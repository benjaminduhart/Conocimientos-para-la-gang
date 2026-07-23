---
author: Mindusting
corrected: false
tags:
  - Programming
  - Python
  - Class
title: Encapsulación en Python
---

# ENCAPSULACIÓN EN PYTHON

> [!fail]- ESTE APARTADO ESTÁ INCOMPLETO
> > [!todo] #TODO

%%
```python
class a:
    x = 10
    _y = 20
    __z = 30

    @property
    def readonly(self):
        return self.__z

    def write(self, value):
        self.__z += value
```
%%

### ENCAPSULACIÓN 💊

[Curso de Python. POO IV. Vídeo 27](https://youtu.be/x5CY8fVyYLo?list=PLU8oAlHdN5BlvPxziopYZRd55pdqFwkeS)

[Curso de Python. POO V. Vídeo 28](https://youtu.be/OU-e2uhoGxE?list=PLU8oAlHdN5BlvPxziopYZRd55pdqFwkeS)

La encapsulación de [variables](https://docs.google.com/document/d/1bfVIpraB3qlcHawNTioFMllMpYmXXwx_zfCFDvGoWDY/edit#heading=h.1b13qrr2gfco), [colecciones](https://docs.google.com/document/d/1bfVIpraB3qlcHawNTioFMllMpYmXXwx_zfCFDvGoWDY/edit#heading=h.yxtkjlvtgt8z) o [métodos](https://docs.google.com/document/d/1bfVIpraB3qlcHawNTioFMllMpYmXXwx_zfCFDvGoWDY/edit#heading=h.i8fkhpmgzfk) permite que no se pueda acceder a ninguno de estos elementos desde el exterior del objeto, para ello es tan simple como poner dos barras bajas al inicio de cualquiera de los tres elementos anteriormente mencionados.

|   |
|---|
|Ej:|
|# Creación de la clase "user"<br><br>class user():<br><br>    # Constructor de la clase<br><br>    def __init__(self, name: str = "", age: int = 0):<br><br>        self.__name = name<br><br>        self.__age  = age<br><br>  <br><br>  <br><br># Instanciación de la clase "user"<br><br>mi_usuario = user("Mindusting", 18)<br><br>  <br><br># Intento de acceder a una<br><br># variable encapsulada<br><br>print(mi_usuario.__name)|

Sí ejecutamos este código veréis que ocurre una [excepción](https://docs.google.com/document/d/1bfVIpraB3qlcHawNTioFMllMpYmXXwx_zfCFDvGoWDY/edit#heading=h.omlil79ujtzf) en la última línea, esto es debido a que estamos intentado acceder a una variable encapsulada, y por tanto no se puede hacer, esto nos sirve si queremos que desde el exterior de un objeto se puede ver el contenido de por ejemplo, una [variable](https://docs.google.com/document/d/1bfVIpraB3qlcHawNTioFMllMpYmXXwx_zfCFDvGoWDY/edit#heading=h.1b13qrr2gfco), pero queremos que no se pueda modificar desde el exterior, para ello podemos seguir la lógica del siguiente ejemplo.

|   |
|---|
|Ej:|
|# Creación de la clase "user"<br><br>class user():<br><br>    # Constructor de la clase<br><br>    def __init__(self, name: str = "", age: int = 0):<br><br>        self.__name = name<br><br>        self.__age  = age<br><br>  <br><br>    def get_name(self):<br><br>        return self.__name<br><br>  <br><br>  <br><br># Instanciación de la clase "user"<br><br>mi_usuario = user("Mindusting", 18)<br><br>  <br><br># Intento de acceder a una<br><br># variable encapsulada a través<br><br># de un método<br><br>print(mi_usuario.get_name())|

Como se puede ver en este nuevo ejemplo, ahora si puedes acceder al valor de la [variable](https://docs.google.com/document/d/1bfVIpraB3qlcHawNTioFMllMpYmXXwx_zfCFDvGoWDY/edit#heading=h.1b13qrr2gfco) a través del [método](https://docs.google.com/document/d/1bfVIpraB3qlcHawNTioFMllMpYmXXwx_zfCFDvGoWDY/edit#heading=h.i8fkhpmgzfk), pero no podemos modificar el valor de la [variable](https://docs.google.com/document/d/1bfVIpraB3qlcHawNTioFMllMpYmXXwx_zfCFDvGoWDY/edit#heading=h.1b13qrr2gfco), ya que sigue estando encapsulada, de igual forma, podríamos hacerlo al revés, haciendo un [método](https://docs.google.com/document/d/1bfVIpraB3qlcHawNTioFMllMpYmXXwx_zfCFDvGoWDY/edit#heading=h.i8fkhpmgzfk) que cambie el valor de la variable pero que no se pueda acceder a ella.

En el caso de los [métodos](https://docs.google.com/document/d/1bfVIpraB3qlcHawNTioFMllMpYmXXwx_zfCFDvGoWDY/edit#heading=h.i8fkhpmgzfk) se hace de la misma forma (Poniendo dos barras bajas al inicio del nombre), esto provocará que ese [método](https://docs.google.com/document/d/1bfVIpraB3qlcHawNTioFMllMpYmXXwx_zfCFDvGoWDY/edit#heading=h.i8fkhpmgzfk) solo se le pueda llamar desde el interior del propio objeto.

|   |
|---|
|Ej:|
|# Creación de la clase "user"<br><br>class user():<br><br>    # Constructor de la clase<br><br>    def __init__(self, name: str = "", age: int = 0):<br><br>        self.__name = name<br><br>        self.__age  = age<br><br>        self.__edad_minima()<br><br>  <br><br>  <br><br>    # Método encapsulado para<br><br>    # comprobar si la edad es<br><br>    # menor que 0<br><br>    def __edad_minima(self):<br><br>        if self.__age < 0:<br><br>            self.__age = 0<br><br>  <br><br>  <br><br># Instanciación de la clase "user"<br><br>mi_usuario = user("Mindusting", 18)|

Este ejemplo de uso de un [método](https://docs.google.com/document/d/1bfVIpraB3qlcHawNTioFMllMpYmXXwx_zfCFDvGoWDY/edit#heading=h.i8fkhpmgzfk) encapsulado no tiene mucho sentido ya que podríamos poner el [condicional](https://docs.google.com/document/d/1bfVIpraB3qlcHawNTioFMllMpYmXXwx_zfCFDvGoWDY/edit#heading=h.6ct1vi8j9me0) dentro del [constructor](https://docs.google.com/document/d/1bfVIpraB3qlcHawNTioFMllMpYmXXwx_zfCFDvGoWDY/edit#heading=h.9s3d3f1sd07), pero hay que tener en cuenta que este ejemplo es simplemente para poder entender el concepto de [método](https://docs.google.com/document/d/1bfVIpraB3qlcHawNTioFMllMpYmXXwx_zfCFDvGoWDY/edit#heading=h.i8fkhpmgzfk) encapsulado, ya que si intentamos acceder a él desde el exterior de la clase, ocurrirá una [excepción](https://docs.google.com/document/d/1bfVIpraB3qlcHawNTioFMllMpYmXXwx_zfCFDvGoWDY/edit#heading=h.omlil79ujtzf).