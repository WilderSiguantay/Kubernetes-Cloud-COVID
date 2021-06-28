# Proyecto realizado en Sistemas Operativos 1

_El proyecto consiste en crear un sitio web que muestre los datos enviados en tiempo real con_
_ayuda de dos balanceador de carga, Docker Compose, kubernetes y las bases de datos de_
_Mongodb y Redis._

_La aplicación utiliza el concepto de colas para el manejo de la concurrencia. Transmite _
_la información mediante diferentes nodos, cada uno con implementado con _
_tecnología diferente._

## Parte 1
### Envío de Datos
La primera parte consta en realizar un programa en Go el cual debe enviar los datos de un 
archivo de entrada a los balanceadores de carga, los balanceadores de carga serán
implementados en: 
- Contour
- Nginx
El archivo con los datos tendrá el siguiente formato:
<img src="https://github.com/WilderSiguantay/Kubernetes-Cloud-COVID/blob/main/Imágenes/P1Formato.PNG" alt="My cool logo"/>

_Enlace a repositorio Git de la parte 1_
https://github.com/WilderSiguantay/SO1P2-EnvioDatosGo


## Segunda Parte (Balanceadores de carga)

_Nota: De esta parte en adelante será en la nube._

La segunda parte empieza por instalar kubernetes la cual será la base de las aplicaciones.
Balanceadores de carga (Nginx y Contour):
Será el mismo trabajo con dos balanceadores de carga distintos, se deben de instalar los
balanceadores de carga de forma local, los balanceadores de carga apuntará a dos 
contenedores que tendrán cada uno un servidor web corriendo sobre go, entonces los 
balanceadores de carga recibirán los datos de la aplicación local y los distribuirá entre los dos 
contenedores

Esta segunda parte la pueden encontrar en la carpeta Manuales/Manual_Tecnico
En donde se está todo el proceso de instalacion y configuracion de Kubernetes y los balanceadores de carga.

## Tercera Parte (Mensajería entre aplicaciones)

La tercera parte se necesita obtener la información que se envió y mandarla por medio de 
por medio de dos herramientas:

- RabbitMQ: Es un software de corretaje de mensajes de código abierto. Acepta 
mensajes de los productores y los entrega a los consumidores. Actúa como un 
intermediario que puede usarse para reducir las cargas y los tiempos de entrega que 
toman los servidores de aplicaciones web.
- gRPC: Es un framework moderno de llamada a procedimiento remoto (RPC) de 
código abierto que puede ejecutarse en cualquier lugar. Permite que las aplicaciones 
cliente y servidor se comuniquen de manera transparente y facilita la creación de 
sistemas conectados.
La información será enviada a dos contenedores que correrán una aplicación en Python, 
estas aplicaciones se encargarán de almacenar los datos finalmente en las dos bases de 
datos que se estarán manejando.

_Enlace a repositorio de tercera parte:_ https://github.com/WilderSiguantay/api-nats

## Cuarta parte (Bases de datos)
Se necesita que se implementen bases de datos no relaciones para mejorar la velocidad y 
rendimiento de la aplicación, las bases de datos a manejar serán:
- MongoDB: Es un sistema de base de datos NoSQL, orientado a documentos y de 
código abierto. En lugar de guardar los datos en tablas, tal y como se hace en las 
bases de datos relacionales, MongoDB guarda estructuras de datos BSON (una 
especificación similar a JSON) con un esquema dinámico, haciendo que la integración 
de los datos en ciertas aplicaciones sea más fácil y rápida.
- Redis: Es un almacén de datos en memoria de código abierto (con licencia BSD), 
utilizado como base de datos, caché y agente de mensajes. Admite estructuras de 
datos como cadenas, hashes, listas, conjuntos, conjuntos ordenados con consultas 
de rango, mapas de bits, hiperloglogs, índices geoespaciales con consultas y flujos de 
radio.
Estas bases de datos deberán de ser instaladas en máquinas virtuales en la nube.

## Quinta parte (Pagina Web)
Por último, se debe de crear una página web corriendo sobre un servidor de node js, dentro 
de la página la cual tendrá una temática de coronavirus debe de tener lo siguiente:
Apartados:
- Deberá mostrar una tabla con todos los datos 
(MongoDB).
- Deberá mostrar el top tres de departamentos con 
más casos(MongoDB).
- Gráfica de Pie con todos los departamentos 
afectados (MongoDB).
- El último caso agregado (el último del archivo)
(Redis).
- Una gráfica de barras que muestra la cantidad de 
afectados por rango de edades, ej. 0-10 años 5 casos (Redis)
_Esta ultima parte está en este repositorio, en la carpeta AppNode_

## Arquitectura Final


<img src="https://github.com/WilderSiguantay/Kubernetes-Cloud-COVID/blob/main/Imágenes/ArquitecturaFinal.PNG" alt="My cool logo"/>
