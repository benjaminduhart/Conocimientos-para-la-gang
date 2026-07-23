---
author: Mindusting
corrected: false
tags:
  - Programming
  - Python
  - Module
  - Random
title: Random en Python
---

# RANDOM EN PYTHON

> [!fail]- ESTE APARTADO ESTÁ INCOMPLETO
> > [!todo] #TODO
> > - [ ] Explicar qué son los números pseudoaleatorios.
> > - [ ] Explicar qué son las semillas.
> > - [ ] Explicar por qué no se puede usar este módulo para encriptar.

> [!help]- REFERENCIAS WEB
> - [Python](https://docs.python.org/es/3/library/random.html) #WWW/Python
> - [W3 Schools](https://www.w3schools.com/python/module_random.asp) #WWW/W3Schools

El [módulo](py_module.md) **random** contiene varias [funciones](py_func.md), pero en esta documentación solo veremos la [clase](py_class.md) `Random`, y sus utilidades, pero para ello primero deberemos importarla:

```python
from random import Random
```

Para crear un objeto `Random` tenemos que seguir la siguiente sintaxis, en donde el argumento `seed` es opcional.

> [!abstract] SINTAXIS
> Random(***\[seed]***)

```python
from random import Random

rng: Random = Random()
```

## MÉTODOS DE LA CLASE RANDOM

- `random()`: devuelve un [float](py_float.md) aleatorio dentro del rango de valores [\[0, 1)](../../math/math_range_notation.md).
- `seed([seed])`: establece el valor indicado como nueva semilla del generador de números aleatorios.
- `choice([iterable])`: se el da como argumento un *iterable* y devuelve un *elemento* aleatorio de este.
- `shuffle([iterable])`: desordena el *iterable* que se le pasa como argumento.
