# instalamos la imagen de python3.7.
FROM python:3.7

# variable de entorno que usamos para un troubleshooting.
ENV PYTHONUNBUFFERED=1


# nos posicionamos en el directorio /backend.
WORKDIR /backend

# copiamos el .txt de las dependencias en el directorio .
COPY requirements.txt /backend/

# se instalan dependencias que va a necesitar el .txt.
RUN apt-get update 
RUN apt-get install -y graphviz-dev 
RUN pip install --upgrade pip 
RUN pip install psycopg2-binary 


# instalamos las dependencias desde el archivo .txt.
RUN pip3 install -r requirements.txt


# copiamos todo el contenido de la carpeta de la app al
# directorio /backend.
COPY . /backend

# exponemos el puerto 8000.
EXPOSE 8000

# ejecutamos el comando para que el server inicie.
CMD [ "python", "manage.py", "runserver",  "0.0.0.0:8000" ]
