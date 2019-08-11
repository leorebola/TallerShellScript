# Ayuda

## ¿Dónde escribir un archivo de shell script?

Podemos utilizar cualquier editor de texto plano. Ejemplo:

- nano
- vi
- gedit
- bloc de notas
- visual studio code
- atom
- sublime text
- etc

## Declarar el interprete del shell script

En la primer linea de su archivo de script, debe indicar que interprete de shell utilizará. Usaremos:

#!/bin/bash

## Ejecutar un shell script

```console
# 1) dar permiso de ejecucion:

chmod +x myscript.sh

# 2) ejecutar:

./myscript.sh
# ó
sh myscript.sh
```

## Comparación

### Comparaciones de cadenas alfanuméricas

```console
Operador		Verdad (TRUE) si:
------------------------------------------
cadena1 = cadena2	cadena1 es igual a cadena2
cadena1 != cadena2	cadena1 no es igual a cadena2
cadena1 < cadena2	cadena1 es menor que cadena2
cadena1 > cadena 2	cadena1 es mayor que cadena 2
-n cadena1		cadena1 no es igual al valor nulo (longitud mayorque 0)
-z cadena1		cadena1 tiene un valor nulo (longitud 0)
```

### Comparación de valores numéricos

```console
Operador		Verdad (TRUE) si:
------------------------------------------
x -lt y			x menor que y
x -le y			x menor o igual que y
x -eq y			x igual que y
x -ge y			x mayor o igual que y
x -gt y			x mayor que y
x -ne y			x no igual que y
```

### Comprobación de atributos de fichero

```console
Operador		Verdad (TRUE) si:
------------------------------------------
-d fichero		fichero existe y es un directorio
-e fichero		fichero existe
-f fichero		fichero existe y es un fichero regular (no un
			directorio, u otro tipo de fichero especial)

-r fichero		Tienes permiso de lectura en fichero
-s fichero		fichero existe y no esta vacio
-w fichero		Tienes permiso de escritura en fichero
-x fichero		Tienes permiso de ejecucion en fichero (o de busqueda
			si es un directorio)

-O fichero		Eres el dueño del fichero
-G fichero		El grupo del fichero es igual al tuyo.

fichero1 -nt fichero2	fichero1 es mas reciente que fichero2
fichero1 -ot fichero2	fichero1 es mas antiguo que fichero2
```