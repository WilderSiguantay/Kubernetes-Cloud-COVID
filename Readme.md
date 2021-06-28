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
