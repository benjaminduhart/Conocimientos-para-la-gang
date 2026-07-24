---
author: Mindusting
corrected: false
headerFile: false
tags:
  - Programming
  - Python
  - Sort
title: Función sorted en Python
---

# FUNCIÓN SORTED EN PYTHON

> [!fail]- ESTE APARTADO ESTÁ INCOMPLETO
> > [!todo] #TODO

La [función](py_func.md) `sorted` en **Python** sirve para ordenar un [iterable](py_iterable.md); este recibe un el [iterable](py_iterable.md) como primer y obligatorio argumento, luego mediante *key arguments* podemos indicar dos argumentos más: `key` y `reversed`; siendo `key` una función que indica mediante qué criterio se deben ordenar los datos (*esto se explica más afondo de [su propio apartado](#CRITERIO%20DE%20ORDENADO)*) y siendo `reversed` un valor [`bool`](py_bool.md) que indica si el resultado final debe estar ordenado de forma inversa; por último recalcar que el resultado de este proceso se devuelve, no se aplica directamente sobre el [iterable](py_iterable.md).

> [!abstract] SINTAXIS
> sorted(***\[iterator\]***, \*, key=***\[key\]***, reversed=***\[bool\]***)

## CRITERIO DE ORDENADO

