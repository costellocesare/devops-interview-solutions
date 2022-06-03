Prueba 2 - Despliegue de una aplicación Django y React.js
Elaborar el deployment dockerizado de una aplicación en django (backend) con frontend en React.js contenida en el repositorio. Es necesario desplegar todos los servicios en un solo docker-compose.

Se deben entregar los Dockerfiles pertinentes para elaborar el despliegue y justificar la forma en la que elabora el deployment (supervisor, scripts, docker-compose, kubernetes, etc)

Subir todo lo elaborado a un repositorio (github, gitlab, bitbucket, etc). En el repositorio se debe incluir el código de la aplicación y un archivo README.md con instrucciones detalladas para compilar y desplegar la aplicación, tanto en una PC local como en la nube (AWS o GCP).

#### Solucion ####

### Backend ###

En el backend lo primero que realice fue el Dockerfile usando la imagen de python:3.7 usando las variables de entorno luego instalando todas las dependencias, copiamos todo el contenido del dir en el path de la imagen, ypor ultimo ejecutando el comando para que el server arranque.

probe que funcionara con el comando

`` sudo docker build . ``

una vez compilo y corrio ejecute el siguiente comando

`` sudo docker run -p 8000:8000 #hashdelcontenedor ``

y probe que todo estuviera corriendo poniendo en el navegador 

"localhost:8000"

cuando logre ver el contenido del backend di por terminada la parte backend.

### Frontend ###

Para el backend utilice la imagen de node:12.18.2 copiamos todos los archivos   .json en el directorio, instale npm, copie todo el contenido del directorio raiz al directorio del contenedor luego use un npm run y con nginx levante el sitio.

probe que funcionara con el comando:

`` sudo docker build . ``

una vez compilo y corrio ejecute el siguiente comando:

`` sudo docker run -p 3000:3000  #hashdelcontenedor``

y entre desde el navegador al localhost:3000


en este punto puedes ver los dos contenedores andando si utilizas en comando

`` docker ps ``

donde podremos verificar el ID de cada contenedor que levantamos, la imagen que tiene instlada, el comando que se ejecutó al construir el contenedor, el livetime que tiene, su status y los puertos que esta utilizando.

### docker-compose ###

para el Docker compose levantamos el frontend y el backend segun lo configurado en cada Dockerfile con la diferencia que al backend le declare una variable de entorno llamada SECRET_KEY="", y luego levante una base de datos con la imagen de posgres:10.1 con variables de entorno para nombrar la base y las credenciales; todo esto lo enlazamos a travez de una network que declare con nombre network1.

cuando estuvo todo en el docker-compose.yml ejecutamos el siguiente comando para levantar los 3 contenedores:

`` sudo docker-compose up ``

hara un proceso instalando y deplyando todo, y una vez termine ya esta listo para probar el front y el backend de manera local.


### para desplegarlo en AWS ###

para lanzar los contenedores en AWS una vez creado el docker-compose, creamos una instancia EC2 y se realizan las configuraciones de la instancia.

se copian los archivos del proyecto a la instancia EC2

una vez todo configurado y los archivos copiados se corren los comandos 

``  sudo yum update

    sudo yum install docker

    sudo curl -L "https://github.com/docker/compose/releases/download/1.25.5/docker-compose-$(uname-s)-$(uname -m)" -o /usr/local/bin/docker-compose

    sudo chmod +x /usr/local/bin/docker-compose

  sudo ln -s /usr/local/bin/docker-compose /usr/bin/docker-compose ``

para iniciar el servicio de docker 

`` sudo service docker start ``

y luego desplegar los contenedores 

`` sudo docker-compose up --build ``

y probar poniendo en el navegador la ip de la instancia con los puertos 3000 y 8000 los cuales ya configuramos en pasos anteriores.
