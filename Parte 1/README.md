**Prueba 1 - Diagrama de Red**
Produzca un diagrama de red (puede utilizar lucidchart) de una aplicación web en GCP o AWS y escriba una descripción de texto de 1/2 a 1 página de sus elecciones y arquitectura.

El diseño debe soportar:

- Cargas variables
- Contar con HA (alta disponibilidad)
- Frontend en Js
- Backend con una base de datos relacional y una no relacional
- La aplicación backend consume 2 microservicios externos

El diagrama debe hacer un mejor uso de las soluciones distribuidas.


**Resolucion**

* Para correr el front y el backend elegimos maquinas EC2 "Elastic Compute Cloud" que corren dentro de un Elastic Beanstalk para automatizar el balanceo y el auto escalamiento.


* Para las bases de datos utilizaremos "Amazon DynamoDB" que son bases de datos no relacionales y que son facilmente escalables estan diseñadas para soportar aplicaciones de cualquier escala; y tambien; "Amason RDS "Amazon Relational Database Service"" para las bases de datos Relacionales.
