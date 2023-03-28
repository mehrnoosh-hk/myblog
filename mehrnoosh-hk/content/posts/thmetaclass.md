---
title: "Python Metaclass"
date: 2023-03-23
type: "post"
tags: ["Python"]
---
A metaclass is a class whose instances are classes. Metaclass is used to define how a class should behave. In Python, all classes are derived from either `object` or `type` which are themselves classes.
Below is a well-known example of how metaclass is used to implement the singleton pattern. Basically, the singleton pattern prevents a class from having more than one instance.

```python
class SingletonMeta(type):
    _instances = {}

    def __call__(cls, *args, **kwargs):
        if cls not in cls._instances:
            instance = super().__call__(*args, **kwargs)
            cls._instances[cls] = instance
        return cls._instances[cls]


class Singleton(metaclass=SingletonMeta):
    def some_logic(self):
        pass
```
