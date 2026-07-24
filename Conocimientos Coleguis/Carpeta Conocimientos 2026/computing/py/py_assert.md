---
author: Mindusting
corrected: false
tags:
  - Programming
  - Python
title: Assert en Python
---

# ASSERT EN PYTHON

> [!fail]- ESTE APARTADO ESTÁ INCOMPLETO
> > [!todo] #TODO

> [!help]- REFERENCIAS WEB
> - [W3 Schools](https://www.w3schools.com/python/ref_keyword_assert.asp) #WWW/W3Schools
> 
> YouTube:
> - [Indently](https://youtu.be/96mDQrlceEk) #WWW/YT/Indently
> - [Python for Everyone](https://youtu.be/8bYAD61Gs28) #WWW/YT/PythonForEveryone
> - [Real Python](https://youtu.be/jjUgWvNxHys) #WWW/YT/RealPython

> [!abstract] SINTAXIS
> assert ***\[condition\] \{, \[message\]\}***

```py
x: float = 0.3

assert isinstance(x, float), "x sould by float."
```

---

Si al ejecutar el archivo de Python no queres que se realicen los `assert` (*ya que reduce el rendimiento debido a las comprobaciones extra*), se puede usar el parámetro `-O` (*menos o mayúscula*) para que se ignoren:

```bash
python3 -O main.py
```
