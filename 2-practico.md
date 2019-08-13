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
