---
id: subscript-syntax
title: Subscript syntax
sidebar_label: Subscript contract syntax
---

## Syntax of subscript contract

Subscript is built on top of AssemblyScript and follow all AssemblyScript syntax.

Subscript compiles a strict variant of TypeScript (a typed superset of JavaScript) to WebAssembly using Binaryen, like:

```
function fib(n: i32): i32 {
  var a = 0, b = 1
  if (n > 0) {
    while (--n) {
      let t = a + b
      a = b
      b = t
    }
    return b
  }
  return a
}
```

## Strictness

Unlike TypeScript, which targets a JavaScript environment with all of its dynamic features,
subscript targets WebAssembly with all of its static guarantees, hence intentionally avoids the dynamicness of JavaScript
where it cannot be compiled ahead of time efficiently.

Limiting ourselves to where WebAssembly excels, for example by assigning or inferring definite types,
eliminates the need to ship a JIT doing the heavy lifting at runtime,
yielding predictable performance right from the start of execution while
guaranteeing that the resulting WebAssembly modules are small.

```
// Need type
function foo(a?) {
  var b = a + 1
  return b
}

// specify the ideal type in advance
function foo(a: i32 = 0): i32 {
  var b = a + 1
  return b
}
```

## Nullability checks

Like TypeScript, the subscript can propagate whether a value is nullable or not after a check:

```
function doSomething(something: string | null): void {
  if (something) {
    something.length // works for checking
  }
}
```
