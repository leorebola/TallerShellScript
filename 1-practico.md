# Ejercicios Prácticos 1

Los siguientes ejercicios le ayudaran a comprender como escribir shell scripts.

### Antes de comenzar:

En su directorio personal de linux (/home/username) haga un nuevo directorio llamado "curso-sh".

Y dentro de este directorio, cree las siguientes carpetas:

curso-sh/<br>
├── sh/<br>
│   ├── practico-1/<br>
│   ├── practico-2/<br>
│   └── practico-3/<br>
├── logs/<br>
└── datos/

Por cada práctico deberá utilizar la correspondiente carpeta. Siendo las carpetas _logs_ y _datos_ comunes para todos los prácticos y ejercicios.

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


#### Ejercicio 1

Realice un script (01-constantes.sh) que defina e inicialice las siguientes variables como si fueran constantes de configuración:

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

#### Ejercicio 2

Hacer un script (02-variables.sh) con las siguientes variables inicializadas con el valor de texto NONE:
- nombre
- edad
- ciudad

A continuación, deberá imprimir el mensaje (note el salto de línea vacío):

```console
Inicializando variables...

```

Para luego de ese mensaje modificar el valor de las tres variables con sus correspondientes datos (nombre, edad y ciudad). El resultado del script en pantalla deberá ser el siguiente:

```console
Inicializando variables...

Mi nombre es VALOR_NOMBRE, tengo VALOR_EDAD años y vivo en a ciudad de VALOR_CIUDAD.
```

_Ayuda: Para realizar un salto de línea puede utilizar \n en el comando echo_

## Parámetros/Argumentos

```console
#!/bin/sh

NOMBRE=$1
APELLIDO=$2

echo "Hola, $NOMBRE $APELLIDO!"

# Ejecución: ./03-param-saludar.sh Chuck Norris
```

```console
#!/bin/sh

# Modo interactivo de solicitar un parámetro

echo "¿Cual es tu nombre?"
read NOMBRE
echo "Hola, $NOMBRE!"
```

#### Ejercicio 3 y 4

Escriba los dos scripts (03-param-saludar.sh y 04-param-saludar-interactivo.sh) de ejemplo que se encuentran acá arriba y ejecútelos para comprobar su funcionamiento.

#### Ejercicio 5

Realizar un script (05-param-edad.sh) que le solicite ingresar su edad y le sume 10 años.

```console
Por favor ingrese su edad:
```

El resultado de la operación debe ser impresa por pantalla con el siguiente texto de ejemplo:

```console
"Tu edad en diez años será: RESULTADO"
```

_Ayuda: Para realizar operaciones aritméticas debe usar esta notación: $(( a + b ))_

#### Ejercicio 6

Un script (06-param-sumar.sh) que sume dos números enteros pasados como argumentos al momento de la ejecución. No deberá solicitar ninguna acción al usuario.

## Condicionales y Bucles

### if

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
**Nota:** _Si necesita consulte en [4-ayuda.md](4-ayuda.md) las formas de comparación con valores numéricos y cadenas alfanuméricas._

##### Ejercicio 7

Implemente un script (07-if-param-validar.sh) que valide la cantidad de argumentos ingresados sea la correcta. Ni más, ni menos.

La cantidad esperada de argumentos será de dos.

```console
./07-if-param-validar.sh uno dos
OK

./07-if-param-validar.sh uno dos tres
ERROR: La cantidad de parametros requeridos son dos y usted ingreso X_VALOR.
```
Donde X_VALOR es la cantidad de argumentos que ingresó el usuario.

_Ayuda: Para conocer la cantidad de argumentos con la cual fue ejecutado el script, debe usar la variable especial: $#_

##### Ejercicio 8

Un script (08-if-edad.sh) que ingresando la edad, diga si es mayor o menor de edad (18 años).

### for

```console
for (( counter=0; counter<10; counter++ ))
do
    echo "$counter"
done
```

##### Ejercicio 9

Hacer un script (09-for-5holas.sh) que imprima 5 veces el nombre pasado por parámetro, enumerando cada uno de ellos de la siguiente manera:

```
# ejemplo:

./09-for-5holas.sh Lisa
1) Hola Lisa
2) Hola Lisa
3) Hola Lisa
4) Hola Lisa
5) Hola Lisa
```

### case

```
case $NUM in
    0)
        echo "El número ingresado es cero"
        ;;
    1)
        echo "El número ingresado es uno"
        ;;
    2)
        echo "El número ingresado es dos"
        ;;
    3)
        echo "El número ingresado es tres"
        ;;
    *)
        echo "El número ingresado es mayor a 3 y menor a 10"
        ;;
esac
```

##### Ejercicio 10

Realizar un script (10-case-traductor.sh) que pida ingresar uno de los 5 días hábiles de la semana (en minúsculas y sin acentos) y devuelva su traducción en inglés.

|Español|Ingles|
|---|---|
|lunes|monday|
|martes|tuesday|
|miercoles|wednesday|
|jueves|thursday|
|viernes|friday|

```console
./10-case-traductor.sh
Por favor ingrese un dia de lunes a viernes
Traduccion a ingles: lunes -> monday
```
Si se introduce otro día, o una palabra que no corresponde a un día se debe imprimir un mensaje de error:

```console
Palabra no soportada.
```

## Funciones

```console
function function1
{
    echo "Esta es la function1 con parámetro: $1"
}

function2()
{
    echo "Esta es la function2 con parámetro: $1"
}

function1 "param1"
function2 "param2"
```

##### Ejercicio 11

Realizar un script (11-funcion-log.sh) que tenga una función llamada "escribirLog" y que reciba dos parámetros: Tipo de log (TRACE, INFO, ERROR) y un mensaje. La función cada vez que sea llamada deberá imprimir por pantalla la fecha, hora, tipo de log y el mensaje. Ejemplo:

```console
lun ago 12 22:25:50 -03 2019 - INFO - Este es un mensaje desde la función.
lun ago 12 22:25:50 -03 2019 - ERROR- Este es otro mensaje indicando un error.
```

La función dentro del script deberá ser llamada tres veces, una por cada tipo de log.
