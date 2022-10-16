---
layout: default
---

# Service Scanning

Un servicio es una aplicación que se ejecuta en un equipo y que realiza alguna función útil para otros usuarios o equipos. Llamamos a estas máquinas especializadas que almacenan estos servicios útiles "servidores" en lugar de equipos, lo que permite a los usuarios interactuar y consumir estos servicios. Lo que nos interesa son los servicios que han sido mal configurados o tienen una vulnerabilidad. En lugar de realizar las acciones esperadas como parte del servicio, estamos interesados ​​en ver si podemos obligar al servicio a realizar alguna acción no deseada que respalde nuestros objetivos, como ejecutar un comando de nuestra elección.

## Realiza un escaneo con NMAP. ¿Cual es la version del servicio que esta corriendo en el puerto 8080?

En este primer ejercicio nos hacen ejecutar un escaneo con nmap para poder averiguar que version esta corriendo el servicio en el puerto 8080.

![comando nmap!](/assets/images/ServiceScanning/1_01.png "Escaneo basico de un puerto en especifico con NMAP.")

>Estructura del comando y desglose:
>
>``nmap -sC -p [Puerto] [IP]``
>
>- -sC Flag para indicarle a nmap que puede usar scripts para conseguir mas informacion de cada puerto escaneado.
>- -p [Puerto] Flag para escanear un puerto en especifico.

>En este ejercicio podemos sustituir la flag -sC por -sV usando -sV para que solo nos enseñe la version del servicio.

![comando nmap!](/assets/images/ServiceScanning/1_02.png "Escaneo basico de un puerto en especifico con NMAP.")

Como podemos ver con el escaneo nmap efectuado, como salida nos da de output el servicio, el estado del puerto que hemos escaneado y la version.

## Realiza un escaneo con NMAP e identifica el puerto no predeterminado donde esta corriendo el servicio telnet.

En el segundo ejercicio nos hacen ejecutar tambien un escaneo con nmap para averiguar en este caso en que puerto esta corriendo el servicio telnet.

![comando nmap!](/assets/images/ServiceScanning/2_01.png "Escaneo completo de todos los puertos para averiguar en que puerto esta ejecutandose el servicio telnet.")

>Estructura del comando y desglose:
>
>``nmap -sV -p- [IP]``
>
>- -sV Flag para que nos muestre la version del servicio utilizado en el puerto como output.
>- -p- Flag para escanear todos los puertos disponibles y averiguar los servicios que estan corriendo en ellos.

![comando nmap!](/assets/images/ServiceScanning/2_02.png "Resultado del escaneo anterior.")

Una vez terminado el escaneo podemos observar entre otras cosas el puerto en el que se esta corriendo el servicio telnet.

## Enumera los recursos compartidos de SMB disponibles en el host de destino. Conéctate al recurso compartido disponible como usuario bob. Una vez conectado, accede a la carpeta llamada 'flag' y envía el contenido del archivo flag.txt.

En este ultimo ejercicio nos piden que investiguemos en los recursos compartidos disponibles en un host y que consigamos el archivo llamado ''flag.txt'' para resolverlo.

Como primer paso intentaremos hacer una lista de los recursos compartidos para ver si encontramos algo que nos pueda interesar.

![comando smb recursos!](/assets/images/ServiceScanning/3_01.png "Listado de recursos compartidos.")

>Estructura del comando y desglose:
>
>``smbclient -N -L \\\\[IP]``
>
>- -N Flag utilizada para omitir el login con password.
>- -L Flag usada para mostrar los recursos compartidos de host destino.

Vemos que hay una carpeta compartida llamada ''users'', vamos a intentar visualizar lo que tenemos dentro.

![comando smb login!](/assets/images/ServiceScanning/3_02.png "Login sin usuario en un recurso compartido en especifico.")

>Estructura del comando y desglose:
>
>``smbclient \\\\[IP]\\[RecursoCompartido]``

Al intentar visualizar el contenido del recurso nos deniega el acceso, vamos a probar a visualizarlo con el usuario que nos han proporcionado en el enunciado del ejercicio.

![comando smb login!](/assets/images/ServiceScanning/3_03.png "Login a un recurso con un usuario en especifico.")

>Estructura del comando y desglose:
>
>``smbclient -U [User] \\\\[IP]\\[RecursoCompartido]`
>
>- -U Flag para especificar que quieres logearte con un usuario en especifico a un recurso.

Al intentar visualizar el contenido de esta carpeta con las credenciales bob:Welcome1 podemos ver que nos permite ver el interior de este recurso.

>Comandos de interes:
>
>- ls Comando para listar recursos.
>- cd Comando para navegar entre carpetas.
>- get Comando para descargar recursos.

![exploracion de recursos!](/assets/images/ServiceScanning/3_04.png "Exploracion de un recurso y descarga de archivos.")

Conseguimos localizar nuestro archivo de interes flag.txt navegando un poco por el recurso compartido.

![flag obtenida!](/assets/images/ServiceScanning/3_05.png "Visualizacion de flag para resolver el ejercicio.")

Una vez descargado miramos el interior con la herramienta para visualizar archivos de txt que queramos y ya tendriamos nuestra flag para reoslver el ejercicio.

[Ir a la seleccion de ejercicios](../GettingStarted.md)
