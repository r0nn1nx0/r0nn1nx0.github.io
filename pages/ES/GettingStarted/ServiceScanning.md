---
layout: default
---

# Service Scanning
---
Un servicio es una aplicación que se ejecuta en un equipo y que realiza alguna función útil para otros usuarios o equipos. Llamamos a estas máquinas especializadas que almacenan estos servicios útiles "servidores" en lugar de equipos, lo que permite a los usuarios interactuar y consumir estos servicios. Lo que nos interesa son los servicios que han sido mal configurados o tienen una vulnerabilidad. En lugar de realizar las acciones esperadas como parte del servicio, estamos interesados ​​en ver si podemos obligar al servicio a realizar alguna acción no deseada que respalde nuestros objetivos, como ejecutar un comando de nuestra elección.

## Realiza un escaneo con NMAP. ¿Cuál es la versión del servicio que está corriendo en el puerto 8080?
---
En este primer ejercicio nos hacen ejecutar un escaneo con nmap para poder averiguar que versión está corriendo el servicio en el puerto 8080.

![comando nmap!](/assets/images/ServiceScanning/1_01.png "Escaneo básico de un puerto en específico con NMAP.")

En este ejercicio podemos sustituir la flag -sC por -sV usando -sV para que solo nos enseñe la versión del servicio.

![comando nmap!](/assets/images/ServiceScanning/1_02.png "Escaneo básico de un puerto en específico con NMAP.")

Como podemos ver con el escaneo nmap efectuado, como salida nos da de output el servicio, el estado del puerto que hemos escaneado y la versión.

## Realiza un escaneo con NMAP e identifica el puerto no predeterminado donde está corriendo el servicio telnet.
---
En el segundo ejercicio nos hacen ejecutar también un escaneo con nmap para averiguar en este caso en que puerto está corriendo el servicio telnet.

![comando nmap!](/assets/images/ServiceScanning/2_01.png "Escaneo completo de todos los puertos para averiguar en que puerto esta ejecutándose el servicio telnet.")

![comando nmap!](/assets/images/ServiceScanning/2_02.png "Resultado del escaneo anterior.")

Una vez terminado el escaneo podemos observar entre otras cosas el puerto en el que se está corriendo el servicio telnet.

## Enumera los recursos compartidos de SMB disponibles en el host de destino. Conéctate al recurso compartido disponible como usuario bob. Una vez conectado, accede a la carpeta llamada 'flag' y envía el contenido del archivo flag.txt.
---
En este último ejercicio nos piden que investiguemos en los recursos compartidos disponibles en un host y que consigamos el archivo llamado ''flag.txt'' para resolverlo.

Como primer paso intentaremos hacer una lista de los recursos compartidos para ver si encontramos algo que nos pueda interesar.

![comando smb recursos!](/assets/images/ServiceScanning/3_01.png "Listado de recursos compartidos.")

Vemos que hay una carpeta compartida llamada ''users'', vamos a intentar visualizar lo que tenemos dentro.

![comando smb login!](/assets/images/ServiceScanning/3_02.png "Inicio de sesión sin usuario en un recurso compartido en específico.")

Al intentar visualizar el contenido del recurso nos deniega el acceso, vamos a probar a visualizarlo con el usuario que nos han proporcionado en el enunciado del ejercicio.

![comando smb login!](/assets/images/ServiceScanning/3_03.png "Inicio de sesión a un recurso con un usuario en específico.")

Al intentar visualizar el contenido de esta carpeta con las credenciales bob:Welcome1 podemos ver que nos permite ver el interior de este recurso.

>Comandos de interés:
>
>- ls: Comando para listar recursos.
>- cd: Comando para navegar entre carpetas.
>- get: Comando para descargar recursos.

![exploración de recursos!](/assets/images/ServiceScanning/3_04.png "Exploración de un recurso y descarga de archivos.")

Conseguimos localizar nuestro archivo de interés flag.txt navegando un poco por el recurso compartido.

![flag obtenida!](/assets/images/ServiceScanning/3_05.png "Visualización de flag para resolver el ejercicio.")

Una vez descargado miramos el interior con la herramienta para visualizar archivos de txt que queramos y ya tendríamos nuestra flag para resolver el ejercicio.

[Ir a la selección de ejercicios](../GettingStarted.md)
