---
title: "Golang Struct"
date: 2019-09-22T14:33:41+08:00
draft: false
tags: ["Golang"]
---
在Golang中，统一以驼峰式命名变量，首字母大写为公有变量（public），小写则为私有变量（private）。

```go
package demo

type A struct {
  C string
  d string
}

type b struct {
  C string
  d string
}

func (a *A) getC() string {
    return a.C
}

func (a *A) GetD() string {
    return a.d
}
```

如上所示为demo.go，在demo包中有两个struct：A和b。其成员变量均为C和d。

```go
package main

import "${project_path}/demo"

func main() {
  a := demo.A{C: "C", d: "d"} // init struct A
  b := demo.b{C: "C", d: "d"} // error

  println(a.C) // output: C
  println(a.d) // error

  println(a.getC()) // error
  println(a.GetD()) // output: d
}
```

由于struct b为私有类，只能在所处package中调用，在其他package中无法调用其他package中的私有成员。同理，在struct中的成员变量只有公有变量才能在struct外部调用。struct中的函数与成员变量同理。

```java
class A {
  public String C;
  private String d;
  
  private String getC() {
    return C;
  }
  
  public String GetD() {
    return d;
  }
}
```

通过Java语言中的public以及private修饰器可以更快的理解Golang中通过驼峰式命名法管理成员的public和private属性。
