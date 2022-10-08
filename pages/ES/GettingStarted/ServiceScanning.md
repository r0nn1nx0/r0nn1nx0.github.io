---
layout: default
---

# Service Scanning

Un servicio es una aplicación que se ejecuta en un equipo y que realiza alguna función útil para otros usuarios o equipos. Llamamos a estas máquinas especializadas que almacenan estos servicios útiles "servidores" en lugar de equipos, lo que permite a los usuarios interactuar y consumir estos servicios. Lo que nos interesa son los servicios que han sido mal configurados o tienen una vulnerabilidad. En lugar de realizar las acciones esperadas como parte del servicio, estamos interesados ​​en ver si podemos obligar al servicio a realizar alguna acción no deseada que respalde nuestros objetivos, como ejecutar un comando de nuestra elección.

## Realiza un escaneo con NMAP. ¿Cual es la version del servicio que esta corriendo en el puerto 8080?

En este primer ejercicio nos hacen ejecutar un escaneo con nmap para poder averiguar que version esta corriendo el servicio en el puerto 8080.

![commando nmap!](/assets/images/ServiceScanning/1_01.png "Escaneo basico de un puerto en especifico con NMAP.")

>Estructura del comando y desglose:
>
>``nmap -sC -p [Puerto] [IP]
>
>- -sC Flag para indicarle a nmap que puede usar scripts para conseguir mas informacion de cada puerto escaneado.
>- -p [Puerto] Flag para escanear un puerto en especifico.

![commando nmap!](/assets/images/ServiceScanning/1_02.png "Escaneo basico de un puerto en especifico con NMAP.")

Como podemos ver con el escaneo nmap efectuado, como salida nos da de output el servicio, el estado del puerto que hemos escaneado y la version.

## Realiza un escaneo con NMAP e identifica el puerto no predeterminado donde esta corriendo el servicio telnet.

En el segundo ejercicio nos hacen ejecutar tambien un escaneo con nmap para averiguar en este caso en que puerto esta corriendo el servicio telnet.

![commando nmap!](/assets/images/ServiceScanning/2_01.png "Escaneo completo de todos los puertos para averiguar en que puerto esta ejecutandose el servicio telnet.")

>Estructura del comando y desglose:
>
>``nmap -sV -sC -p- [IP]
>
>- -sV Flag para que nos muestre la version del servicio utilizado en el puerto como output.
>- -sC Flag para indicarle a nmap que puede usar scripts para conseguir mas informacion de cada puerto escaneado.
>- -p- Flag para escanear todos los puertos disponibles y averiguar los servicios que estan corriendo en ellos.

![commando nmap!](/assets/images/ServiceScanning/2_02.png "Resultado del escaneo anterior.")

Una vez terminado el escaneo podemos observar entre otras cosas el puerto en el que se esta corriendo el servicio telnet.

[Ir a la seleccion de ejercicios](../GettingStarted.md)
