---
layout: default
---

# Web Enumeration
---
Los servidores web alojan aplicaciones web (a veces más de 1) que a menudo proporcionan una superficie de ataque considerable y un objetivo de gran valor durante una prueba de penetración.

## Intenta ejecutar algunas de las técnicas de enumeración web que has aprendido en esta sección en el servidor objetivo y usa la información que consigas obtener para conseguir la flag.
---
En este ejercicio tendremos que usar las técnicas que hemos ido aprendiendo sobre enumeración web. Para empezar analizando la información que nos han dado en el ejercicio sabemos que es un servidor web por lo tanto no hará falta un escaneo con nmap, ya que sabemos que tipo de servicio atacaremos.

Usamos la herramienta gobuster con un diccionario con los nombres de directorios más típicos para ejecutar un escaneo de fuerza bruta de directorios.

![comando gobuster!](/assets/images/GettingStarter/WebEnnumeration/01.png "Comando usado en gobuster para hacer fuerza bruta y sacar la estructura de directorios que tiene el servicio web usando un diccionario.")

Una vez el escaneo termina tendremos listados los directorios que tenemos disponibles en el servidor web. Echándole un vistazo por encima vemos que el servidor tiene un archivo robots.txt que puede contener información relevante en nuestro proceso de enumeración.

>El estándar de exclusión de robots, también conocido como el protocolo de la exclusión de robots o protocolo de robots.txt, es un método para evitar que ciertos bots que analizan los sitios web u otros robots que investigan todo o una parte del acceso de un sitio Web, público o privado, agreguen información innecesaria a los resultados de búsqueda. Los robots son de uso frecuente por los motores de búsqueda para categorizar archivos de los sitios Webs, o por los webmasters para corregir o filtrar el código fuente.
>
>[Fuente](https://es.wikipedia.org/wiki/Est%C3%A1ndar_de_exclusi%C3%B3n_de_robots)

Procedemos a mirar el contenido del archivo robots.txt y vemos que tenemos un archivo PHP llamado admin-login-page.php que podría hacer referencia al panel de inicio de sesión de un usuario administrador del sistema.

![contenido del archivo robots.txt!](/assets/images/GettingStarter/WebEnnumeration/02.png "Visualización del contenido del archivo robots.txt")

Al cargar la página vemos un panel de inicio de sesión de administrador que a simple vista no podríamos hacer nada con él, ya que no tenemos ningún tipo de credenciales para probar.

![panel de administrador!](/assets/images/GettingStarter/WebEnnumeration/04.png "Panel de administrador")

Si echamos un vistazo al código fuente de la página podemos ver que el que la ha programado se ha dejado en los comentarios unas credenciales de acceso de administrador que podríamos probar de usar para acceder en el panel anteriormente mencionado.

>Para ver el código fuente de una página podemos usar la combinación de teclas CTRL + U.

![código fuente de la página admin-login-page.php!](/assets/images/GettingStarter/WebEnnumeration/03.png "Visualización del código fuente de panel de acceso que hemos encontrado en el archivo robots.txt")

Y efectivamente al probar las credenciales encontradas en el código fuente de la página nos inicia sesión como usuario de administrador y así obtendríamos nuestra flag en este ejercicio de enumeración web.

![flag del ejercicio!](/assets/images/GettingStarter/WebEnnumeration/05.png "Flag del ejercicio")

[Ir a la selección de ejercicios](../GettingStarted.md)
