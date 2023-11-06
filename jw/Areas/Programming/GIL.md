---
aliases:
  - Global Interpreter Lock
tags:
  - CS
---

In CPython, the global interpreter lock, or GIL, is a __a mutex that protects access to Python objects, preventing multiple threads from executing Python bytecodes at once__. This lock is necessary because CPython's memory management is not thread-safe.

## Resource
- https://it-eldorado.tistory.com/160