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

![comando gobuster!](/assets/images/WebEnnumeration/01.png "Comando usado en gobuster para hacer fuerza bruta y sacar la estructura de directorios que tiene el servicio web usando un diccionario.")

Una vez el escaneo termina tendremos listados los directorios que tenemos disponibles en el servidor web. Echándole un vistazo por encima vemos que el servidor tiene un archivo robots.txt que puede contener información relevante en nuestro proceso de enumeración.

Procedemos a mirar el contenido del archivo robots.txt y vemos que tenemos un archivo PHP llamado admin-login-page.php que podría hacer referencia al panel de inicio de sesión de un usuario administrador del sistema.

![contenido del archivo robots.txt!](/assets/images/WebEnnumeration/02.png "Visualización del contenido del archivo robots.txt")

![panel de administrador!](/assets/images/WebEnnumeration/04.png "Panel de administrador")

Al cargar la página vemos un panel de inicio de sesión de administrador que a simple vista no podríamos hacer nada con él, pero si echamos un vistazo al código fuente de la página podemos ver que el que la ha programado se ha dejado en los comentarios unas credenciales de acceso de administrador que podríamos probar de usar para acceder en el panel anteriormente mencionado.

![código fuente de la página admin-login-page.php!](/assets/images/WebEnnumeration/03.png "Visualización del código fuente de panel de acceso que hemos encontrado en el archivo robots.txt")

Y efectivamente al probar las credenciales encontradas en el código fuente de la página nos inicia sesión como usuario de administrador y así obtendríamos nuestra flag en este ejercicio de enumeración web.

![flag del ejercicio!](/assets/images/WebEnnumeration/05.png "Flag del ejercicio")

[Ir a la selección de ejercicios](../GettingStarted.md)
