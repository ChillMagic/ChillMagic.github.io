---
layout: post
title: 【CVM】 CMS 的编译（寄存器篇）
categories: [CMS, CVM]
description: 
keywords: CMS, 编译
---

CVM 是采取 AOT 编译方式。
CMS 的每条指令，都会被编译为 `(Runtime::Environment &env) -> void` 类型的函数。

**私有寄存器**

CMS 的寄存器是或静态或动态的。每个函数都会对其使用的寄存器进行声明。
`mov %1, %2` 这样的一条指令，在编译期就能够知道 `%1` 与 `%2` 是动态还是静态的。
假如 `%1` 是动态， `%2` 是静态，那么只需要 `env.get_dynamic(1, e_current)` 和 `env.get_static(2, e_current)` 就能获取 `%1` 和 `%2` 的数据。

```cpp
std::function<void(Runtime::Environment &env)> getPrivateRegisterFunc(const FunctionInfo &funcinfo, const InstStruct::Register &reg)
{
    size_t id = reg.index();
    if (funcinfo.is_dynamic(id)) {
        return [=](Runtime::Environment &env){ env.get_dynamic(id, e_current); };
    }
    else if (funcinfo.is_static(id)) {
        return [=](Runtime::Environment &env){ env.get_static(id, e_current); };
    }
    else {
        funcinfo.putError();
    }
}
```

这样做的好处是不需要在运行期判断，坏处则是编译的代码需要写很多，而且容易错漏。

关于不同环境的编译，因为无法在编译期得到父环境的信息，因此目前全部是 Runtime 期间判断的。

父环境系统的设计只是一个雏形，用于闭包的实现。不过带来许多问题。这方面需要改进一下。（大概会将直接获取父环境寄存器的设计删掉。）
