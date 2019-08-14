# Ejercicios Prácticos 3

#### Ejercicio 1

Crear un script de alarma (01-alarm.sh) que detectará cuando se escriba un log de error.

Este script se ejecutará cada un minuto, mediante un cron de Linux. _El objetivo de este ejercicio es enseñar las posibilidades y existencia del crontab pero no profundizaremos en el tema._

Deberá monitorear los archivos con extensión .log que se escriban dentro de una determinada carpeta. Cuando se detecte un archivo de log que tenga la palabra "Error" en su contenido se tendrá que generar una alarma.

Como no tenemos configurado un servicio de mail, la alarma se escribirá en un archivo ALARMA-[fecha-hora].log dentro del directorio de usuario con el siguiente texto:

```text
[fecha-hora] Se encontró un error en el archivo: filename.log
```

Configuración del cron

Una vez desarrollado el script, los pasos para configurarlo al crontab de Linux son los siguientes:

1) Con un editor de texto crear un archivo llamado "cronfile.cfg" en el directorio home del usuario.

```console
$ nano cronfile.cfg
```

2) Pegar la siguiente línea de texto en su contenido:

```
*/1 * * * * $HOME/curso-sh/sh/practico-3/01-alarm.sh
```

3) Guardar.

4) Ejecutar el siguiente comando:

```console
$ crontab cronfile.cfg
```

Listo, el script se ejecutará una vez por cada minuto.

Notas adicionales:

```
*/1 * * * * $HOME/curso-sh/sh/practico-3/01-alarm.sh
  | | | | |
  | | | | └── día de la semana (0 - 6)
  | | | └──── mes (1 - 12)
  | | └────── día del mes (1 - 31)
  | └──────── hora (0 - 23)
  └────────── minuto (0 - 59)

*	any value
,	value list separator
-	range of values
/	step values
```

Un editor rápido y simple para expresiones cron: https://crontab.guru
