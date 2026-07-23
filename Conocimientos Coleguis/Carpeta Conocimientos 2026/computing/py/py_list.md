---
author: Mindusting
corrected: false
tags:
  - Programming
  - Python
  - DataStructure
title: Listas en Python
---

# LISTAS EN PYTHON

> [!fail]- ESTE APARTADO ESTÁ INCOMPLETO
> > [!todo] #TODO
> > - [ ] Explicar como declarar de forma literal una lista con elementos.
> > - [ ] Explicar como declarar una lista rellena de forma eficiente (`[None] * 128`).
> > - [ ] Explicar la compresión de listas (`[2 ** i for i in range(8)]`).
> > - [ ] Documentar las funciones:
> >     - [x] append
> >     - [ ] clear
> >     - [ ] copy
> >     - [ ] count
> >     - [ ] extend
> >     - [ ] index
> >     - [x] insert
> >     - [x] pop
> >     - [ ] remove
> >     - [ ] reverse
> >     - [ ] sort

> [!help]- REFERENCIAS WEB
> - [Python](https://docs.python.org/3/tutorial/datastructures.html) #WWW/Python
> - [W3 Schools](https://www.w3schools.com/python/python_lists.asp) #WWW/W3Schools

> [!faq]- FAQ
> - [¿Qué es una lista en programación?](../pc/pc_list.md)

Para declarar una **lista** en Python se puede hacer de dos forma, de forma *literal* o a través de la [clase](py_class.md) `list`.

## DECLARACIÓN LITERAL

```python
# Se declara la lista de forma literal.
#               V
my_list: list = []
```

---

Para crear una **lista** en Python se puede hacer de las siguientes formas:

```python
list1 = []
list2 = list()

list3: list = []
list4: list = list()
```

La [clase](py_class.md) `list` únicamente puede recibir un argumento, este no es necesario y debe ser un *iterable*, en el caso en el que no se especifique ningún valor para el argumento, devolverá una **lista** bacía, en el caso de crear un *iterable* ([`tuple`](py_tuple.md), [`set`](py_set.md), [`dict`](py_dict.md)) creará una **lista** a partir del *iterable* indicado.

Las **listas** 

```python
l0: list = [0] * 3
l1: list = list(range(3)) # [range(3)]
l2: list = [i for i in range(3)]
```

## AÑADIR ELEMENTO

Para añadir elementos a una **lista** se usa el [método](class/py_methods.md) `append`, este recive un único argumento con el valor que queramos introducir.

> [!abstract] SINTAXIS
> ***\[listName\]***.append(***\[value\]***)

```python
my_list: list = [3]

my_list.append(2)
my_list.append(5)

print(my_list)
# SALIDA:
# [3, 2, 5]
```

Como se puede ver en el ejemplo, los nuevos elementos se añaden al final de la lista.

## ELIMINAR ELEMENTO POR ÍNDICE

Para eliminar un elemento por índice se usa el [método](py_methods.md) `pop`, este tiene un único argumento opcional, el cual por defecto tiene el valor de `-1`, con este se indica el índice del elemento a sacar de la lista, pudiendo dar un índice tanto positivo como negativo, siendo el `-1` el último valor de la lista, a su vez, cuando este devuelve el valor que se extrae de la lista.

> [!abstract] SINTAXIS
> ***\[listName\]***.pop(***\{index\}***)

```python
my_list: list = [3, 2, 5]

print(my_list.pop())
print(my_list.pop(0))
print(my_list)
# SALIDA:
# 5
# 3
# [2]
```

Como se puede ver en el ejemplo cuando usamos el [método](py_methods.md) `pop` sin arguentos extraemos el último valor, en este caso el `5`; cuando usamos el `pop` con un argument (*en este caso el `0`*) obtenemos el elemento del índice indicado (*en este caso el `3`*); finalmente se imprime la lista para poder ver que efectivamente se han extraido los elementos de la lista.

## INSERTAR ELEMENTO

Para insertar un elemento en un índice en concreto se usa el [método](py_methods.md) `insert`, este recive dos parámetros, siendo el primero el índice de la posición en donde queremos introducir el elemento y el segundo el valor del elemento a introducir.

> [!abstract] SINTAXIS
> ***\[listName\]***.insert(***\[index\]***, ***\[value\]***)

```python
my_list: list = [3, 2, 5]

my_list.insert(0, 7)
print(my_list)
# SALIDA:
# [7, 3, 2, 5]

my_list.insert(2, 8)
print(my_list)
# SALIDA:
# [7, 3, 8, 2, 5]
```

Como se puede ver en el ejemplo, cada vez que se inserta un nuevo valor se desplaza tanto el elemento situado en el índice como los que estén a la derecha hacia la derecha, en la primera inserción el índice es el cero, por lo que todos los elementos se desplazan hacia la derecha para dejar hueco en el primer espacio y es ahí en donde se introduce el valor siete.
