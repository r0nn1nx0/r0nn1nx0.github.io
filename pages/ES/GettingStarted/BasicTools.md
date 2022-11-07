---
layout: default
---

# Basic Tools
---
Herramientas como SSH, NetCat, Tmux y Vim son esenciales y usadas para la mayoria de profesionales en el sector de la seguridad de la informacion. Aun que estas herramientas no estan pensadas como herramientas de penetracion, son muy importantes en el proceso de penetrar un sistemas, por ello tenemos que masterizarlas.

En este ejercicio nos piden extraer la bandera usando las herramientas que nos han enseñado en esta seccion, en este caso usaremos la herramienta NetCat para extraer la flag para resolver el ejercicio.

![comando NetCat!](/assets/images/GettingStarter/BasicTools/01.png "Comando NetCat para extraer la version del servicio del puerto indicado.")

>Estructura del comando:
>
>``netcat [IPObjetivo] [Puerto]``

Como podemos ver en la captura usamos la herramienta NetCat poniendo la IP que queremos atacar conjunto con el puerto al que queremos acceder para que nos de como salida la version y el servicio que esta usando.

[Ir a la seleccion de ejercicios](../GettingStarted.md)
