---
author: Mindusting
corrected: false
tags:
  - Programming
  - Python
title: Variables en Python
---

# FLOAT EN PYTHON

> [!fail]- ESTE APARTADO ESTÁ INCOMPLETO
> > [!todo] #TODO

> [!help]- REFERENCIAS WEB
> - [Python](https://docs.python.org/3/library/functions.html#float) #WWW/Python
>
> YouTube:
> - [Indently](https://youtu.be/NQSVF9WB_ds) #WWW/YT/Indently

```python
print(float(3))
print(float("3.14"))
'''
Combierte un int o str e un valor float, siempre que se pueda.
'''

print(float.is_integer(3.14))
'''
Devuelve `True` si el resto es igual a cero.
'''

print(float.fromhex("ff.f"))
print(float.fromhex("0xff.f"))
'''
Combierte un valor hex a float.
'''
```