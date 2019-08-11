# Ejercicios Prácticos 1

## Variables

|Código|Descripción|
|---|---|
|VAR="" <br> VAR=|Definición.|
|VAR=valor|Definición, inicialización o modificación.|
|$VAR <br> "$VAR" <br> ${VAR}|Formas de acceso a su valor.|
|unset VAR |Eliminar una variable.|

Nombrado de variables:
- my_variable_name: Nombres de variables.
- MY_CONSTANT: Constantes y nombres de variables de entorno.


### Ejercicio 1

Realice un script que defina e inicialice las siguientes variables como si fueran constantes de configuración:

- BASE_PATH
- EMAIL_TEAM
- UMBRAL_ERROR

Al ejecutar el script, debe imprimir por pantalla los valores asignados de la siguiente manera:

```console
La configuración del script es la siguiente:
--------------------------------------------
BASE_PATH: valor
EMAIL_TEAM: valor
UMBRAL_ERROR: valor
--------------------------------------------
```

### Ejercicio 2

Hacer un script con las siguientes variables inicializadas con el valor de texto NONE:
- nombre
- edad
- ciudad

A continuación, deberá imprimir el mensaje (note el salto de linea vacio):

```console
Inicializando variables...

```

Para luego de ese mensaje modificar el valor de las tres variables con su correspondientes datos (nombre, edad y ciudad). El resultado del script en pantalla deberá ser el siguiente:

```console
Inicializando variables...

Mi nombre es VALOR_NOMBRE, tengo VALOR_EDAD años y vivo en a ciudad de VALOR_CIUDAD.
```

_Ayuda: Para realizar un salto de linea puede utilizar \n en el comando echo_

## Parámetros

```console
#!/bin/sh

NOMBRE=$1
APELLIDO=$2

echo "Hola, $NOMBRE $APELLIDO!"

# Ejecución: ./saludar.sh Chuck Norris
```

```console
#!/bin/sh

# Modo interactivo de solicitar un parametro

echo "¿Cual es tu nombre?"
read NOMBRE
echo "Hola, $NOMBRE!"
```

### Ejercicio 1

Realizar un script que le consulte su edad y le sume 10 años.

El resultado de la operación debe ser impresa por pantalla con el siguiente texto de ejemplo:

```console
"Mi edad en diez años será: RESULTADO"
```

_Ayuda: Para realizar operaciones aritmeticas debe usar esta notación: $(( a + b ))_

### Ejercicio 2

### Ejercicio 3

### Ejercicio 4

## Condicionales y Bucles

#### if

```console
if [[ $num = 1 ]]
then
    echo 'El número es UNO.'
elif [[ $num = 2 ]]
    echo 'El número es DOS.'
else
    echo "El número no es UNO ni DOS." 
fi
```
**Nota:** _Si lo necesita consulte en [4-ayuda.md](4-ayuda.md) las formas de comparación con valores numéricos y cadenas alfanuméricas._

### Ejercicio 1

### Ejercicio 2

### Ejercicio 3

### Ejercicio 4

#### for


#### case