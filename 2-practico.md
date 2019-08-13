# Ejercicios Prácticos 2

En estos ejercicios se trabajará con ficheros, directorios y se integrará el conocimiento aprendido en el practico 1 por lo cual es importante haya completado todos los ejercicios.

Para realizar varias de estas actividades necesitará los dataset en la carpeta "datos".

## Trabajar con ficheros de texto plano

### Leer linea por linea un fichero

#### Ejercicio 1

Imprimir todas las lineas que contiene el fichero datos/en-la-ciudad-de-la-furia.txt

Nombre de este script: 01-lineas.sh

Ayuda:
```console
file="/path/to/txt/file"

while IFS= read -r line
do
  echo "$line"
done < "$file"
```

#### Ejercicio 2

Realizar un script "02-usuarios.sh" que retorne toda la lista de usuarios que figuran en /etc/passwd. Solo los nombres de usuarios y ordenados alfabéticamente.

_Ayuda: Puede usar los comandos cut y sort con pipe |_

_Para saber como usar estos comandos puede recurrir a Google o al manual de Linux "man pages" escribiendo man y el comando. Ejemplo: **man cut**_

### Iterar el contenido de un directorio

#### Ejercicio 3

Imprimir un listado con todos los archivos que se encuentran en la carpeta _datos_.

El listado deberá contener tres datos separados por coma:
- Path absoluto de cada fichero.
- Nombre del fichero (sin path).
- Su tamaño en formato legible por "humano".

```console
/home/username/curso-sh/datos/titanic3.csv,titanic3.csv,105 K
```

Nombre de este script: 03-dir-info.sh

_Ayuda: Le serán útiles los comandos cut, du y basename._

#### Ejercicio 4

Deberá automatizar el renombrado de ficheros. Para este ejercicio es necesario que dentro de la carpeta "curso-sh" cree una carpeta llamada "renombrado".

Una vez creada esta nueva carpeta, ingrese a la misma y ejecute el siguiente comando para crear cuatro archivos:

```console
echo uno > uno.txt;echo dos > dos.txt;echo tres > tres.txt;echo cuatro > cuatro.txt;echo cinco > cinco.csv;
```

El script en cuestion (04-renomnrado.sh) deberá renombrar todos los ficheros **.txt** colocándoles el prefijo _OK__ y cambiando la extensión _.txt_ por _.dat_

Además, deberá dejar registro en un archivo de log llamado _03-renombrado.log_ ubicado en la carpeta logs. La información que debe escribir será fecha, hora, nombre original del archivo y nuevo nombre. Para esto puede reutilizar la función escribirLog del práctico anterior modificándola para que escriba en un archivo.

Compruebe antes y después de renombrar que el contenido de los archivos no fue modificado.

#### Ejercicio 5

Realizar un script llamado 05-password-inseguro.sh que reciba dos argumentos: Una palabra (contraseña) y un fichero de contraseñas más usadas filtradas en la web (darkweb2017-top10000.txt).

1- Deberá validar que sean únicamente  dos los argumentos pasados al script.

2- Validar que el segundo argumento es un fichero que existe.

Si alguna de estas dos condiciones no se cumple, el script deberá abortar su ejecución imprimiendo un mensaje informativo al usuario de porque se canceló.

3- Imprimir PASSWORD INSEGURO si la palabra existe dentro del fichero e indicar en que número del ranking se encontró (nro de línea).

El resultado del script será así:

```console
./05-password-inseguro.sh qwer1234 ../../datos/darkweb2017-top10000.txt
---------------------
| PASSWORD INSEGURO |
---------------------
La contraseña qwer1234 figura en el top 123 de las más usadas en 2017. Se recomienza utilizar otra.
```

_Ayuda: El comando grep tiene una opción que le puede ser útil_


### Crear directorios y ficheros

#### Ejercicio 6

El script 06-deploy.sh al ejecutarse deberá crear un directorio de despliegue (deploy) y un fichero llamado 06-deploy.log en el directorio de logs.

El log contendrá la fecha y hora de ejecución del script junto a un mensaje:

```console
FECHA HORA - Creación exitosa del directorio.
```

Pero en caso que el directorio ya existiera deberá escribir en el log el siguiente mensaje:

```console
FECHA HORA - Se omite la creación del directorio porque ya existe.
```

Luego el script deberá guardar en el mismo archivo de log, el nombre de usuario que ejecutó el script.

_Ayuda: Googlee cómo obtener el nombre del usuario actual._

#### Ejercicio 7

Realizar un script (07-titanic.sh) que busque en el archivo titanic3.csv la cantidad de personas mayores o menores a una determinada edad que viajaban en dicho barco. No todas las personas registran edad, deberá contemplar este caso de error.

Nótese que el archivo titanic3.csv no es necesario pasarlo como argumento.

Realice este script de manera interactiva. Es decir, que solicite al usuario ingresar una edad y que luego solicite si debe ser menor o mayor a esa edad.

Implemente el código usando dos funciones: buscarMenorA y buscarMayorA.

Debe contemplar el caso, si no existen personas que coincidan con el criterio de búsqueda se debe imprimir un mensaje.

#### Ejercicio 8

Consulte por GET el webservice rest: https://httpbin.org/get

El script 08-test-rest.sh debe controlar que el status code retornado sea 200 y en este caso devolver el mensaje "Webservice saludable."

En caso que el status code sea diferente a 200, devolver el mensaje "Alerta: el webservice no respondió status code 200".

_Ayuda: Utilice el comando curl con su opción I. Puede que no tenga instalado curl, pruebe antes en la terminal de comandos._

#### Ejercicio 9

Hacer un script 09-country-info.sh que reciba por parámetro dos argumentos:

- Argumento 1: CODE o NAME
- Argumento 2: Código o Nombre de país

Si en el primer argumento se pasa CODE, entonces el segundo deberá ser el código de país. Ejemplo AR para Argentina.

Si en el primer argumento se pasa NAME, entonces el segundo deberá ser el nombre de país. Ejemplo Argentina.

El script deberá retornar la moneda del país y su código. Ejemplo: Para Argentina, la moneda es el Peso y su código es ARS.

Los datos para el script están en el archivo country-code-to-currency-code-mapping.csv cuyas columnas son:

```console
Country,CountryCode,Currency,Code
```

Utilice para este script: case y funciones.