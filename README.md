# Trabajo final de grado (TFG)
<b>Autor: Alexander Álvarez Marques</b>

## Descripción del proyecto
Este proyecto trata de una aplicación web para la gestión de reservas en centros o instalaciónes deportivas.

## Instalación del proyecto
En este repositorio se encuentra solo y exclusivamente los archivos docker necesarios para realizar la correcta instalación del proyecto. Las instrucciónes restantes para su instalación se pueden encontrar en sus correspondientes repositorios.

[Aplicación de backend](https://github.com/AlexanderAlvarezMarques/TFG-Backend.git)
[Aplicación de frontend](https://github.com/AlexanderAlvarezMarques/TFG-Frontend.git)

Para la instalación de docker, debe situarse dentro de la carpeta docker y ejecutar los siguientes comandos:

 - docker network add tfg
 - docker compose build
 - docker compose up -d

Con esto la aplicación debería de quedar en ejecución en segundo plano.
Para comprobar que todo esta en orden podemos ejecutar el siguiente comando
 - docker ps

Deberemos observas varias lineas de código donde nos tendremos que fijar en el nombre del contenedor, para ello deben existir los siguientes nombres:
 - TFG-nginx
 - TFG-php
 - TFG-database
 - TFG-mail_catcher (este es opcional, solo para envio de correos)

De aquí en adelante, seguiremos con las instrucciónes facilitadas en cada respositorio.
