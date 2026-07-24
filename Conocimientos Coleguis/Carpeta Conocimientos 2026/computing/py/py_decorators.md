---
author: Mindusting
corrected: false
tags:
  - Programming
  - Python
  - Function
title: Decoradores en Python
---

# DECORADORES EN PYTHON

> [!fail]- ESTE APARTADO ESTÁ INCOMPLETO
> > [!todo] #TODO
> > - [ ] Explicar que un decorador es en esencia una función que envuelve otra función para añadirle nuevo comportamiento.
> > - [ ] Explicar la diferencia entre un decorador simple y un decorador con argumentos.

> [!help]- REFERENCIAS WEB
> - [El libro de Python](https://ellibrodepython.com/decoradores-python) #WWW/ElLibroDePython
> 
> YouTube:
> - [Clear Code](https://youtu.be/nVdF7QT-Ggg) #WWW/YT/ClearCode

```python
def decorator(func):
    def wrapper(*args, **vargs):
        return func(*args, **vargs)
    return wrapper
```

```python
def decorator_factory(*decorator_args, **decorator_vargs):
    def decorator(func):
        def wrapper(*args, **vargs):
            return func(*args, **vargs)
        return wrapper
    return decorator
```

```python
@decorator_factory("arg")
def func1():
    pass

created_decorator = decorator_factory("arg")

@created_decorator
def func2():
    pass
```
