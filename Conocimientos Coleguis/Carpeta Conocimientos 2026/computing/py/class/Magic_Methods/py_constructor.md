---
author: Mindusting
corrected: false
tags:
  - Programming
  - Python
  - Class
  - Method
  - Constructor
title: Constructores en Python 👷
---

### CONSTRUCTORES EN PYTHON

Un constructor es un [método](https://docs.google.com/document/d/1bfVIpraB3qlcHawNTioFMllMpYmXXwx_zfCFDvGoWDY/edit#heading=h.i8fkhpmgzfk) el cual tiene como nombre `__init__`, esto provoca que se ejecute automáticamente al momento de instanciar una clase, dándole así los valores iniciales que tendrán las [variables](https://docs.google.com/document/d/1bfVIpraB3qlcHawNTioFMllMpYmXXwx_zfCFDvGoWDY/edit#heading=h.1b13qrr2gfco) y [colecciones](https://docs.google.com/document/d/1bfVIpraB3qlcHawNTioFMllMpYmXXwx_zfCFDvGoWDY/edit#heading=h.yxtkjlvtgt8z) del objeto, haciendo uso del argumento “self” (El uso de este argumento se explica de forma más extensa en el apartado [métodos](https://docs.google.com/document/d/1bfVIpraB3qlcHawNTioFMllMpYmXXwx_zfCFDvGoWDY/edit#heading=h.i8fkhpmgzfk)) para almacenar los valores en el objeto.

|   |
|---|
|Ej:|
|# Creación de la clase "user"<br><br>class user():<br><br>    # Constructor de la clase<br><br>    def __init__(self, name: str = "", age: int = 0):<br><br>        self.name = name<br><br>        self.age  = age<br><br>  <br><br>  <br><br># Instanciación de la clase "user"<br><br>mi_usuario = user("Mindusting", 18)|

Como se puede ver en el ejemplo, para indicar los valores de los argumentos del constructor, estos se indican en los paréntesis situados tras la palabra “user” de la última línea, ya que es en ese momento en el que se instancia la clase “user”.
