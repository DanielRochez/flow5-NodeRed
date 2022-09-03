# flow5-NodeRed
Este ejercicio hecho en Node-Red consiste en obtener la información climática por API desde openweathermap.org

# Introducción

El flow 5 representa el cuarto ejercicio a realizar con NodeRed. Este ejercicio consiste en obtener la información climática por una API desde openweathermap.org. 

# Material Necesario
Para realizar este flow necesitas lo siguiente:

1. Ubuntu 20.04
2. NodeJS
* NPM
* NodeRed
* Nodos Dashboard

# Material de referencia
En los siguientes enlaces puedes encontrar cursos en la plataforma de edu.codigoiot.com que te permitirán realiar las configuraciones necesarias

* [Instalación de Virtual Box y Ubuntu 20.04](https://edu.codigoiot.com/course/view.php?id=812)
* [Instalación de NodeRed](https://edu.codigoiot.com/enrol/index.php?id=817)
* [Introducción a NodeRed](https://edu.codigoiot.com/enrol/index.php?id=278)
* [Introducción a MQTT](https://edu.codigoiot.com/course/view.php?id=851)

# Instrucciones
## Requisitos previos
Para que este flow funcione, debes cumplir con los siguientes requisitos previos

1. Instalación de NodeJS. Se recomienda tener instalado NodeJS en alguna versión LTS. Al momento de creación de este documento, se usó la versión 16.17LTS. Esta instalación debe incluir las Build-Tools para hacer uso de NPM

2. Instalación de NodeRed. La instalación se realiza por NPM. Al momento de la creación de este contenido, se usó la versión 3.0.2

3. Cuenta de openweathermap.org la cual es gratuita y nos permitira conocer el clima por una API

4. Gererar un api key que se usara dentro del proyecto en la siguiente pagina https://home.openweathermap.org/api_keys. tomar a consideración que se activa en un lapso de 2 horas

# Instrucciones de preparación del entorno
Para ejecutar este flow, es necesario lo siguiente

1. Arrancar NodeRed con el comando node-red
2. Clonar el flow4
2. Añadir los siguientes nodos:
   * 1 nodo tipo timestamp
   * 1 nodo tipo http request
   * 1 nodo tipo json
   * 2 nodos tipo function
   * 2 nodos tipo gauge
   * 1 nodo tipo chart

nota: para ver las conexiones de los nodos dirigirse al apartado de resultados que se encuentra mas abajo

3. Hacer una petición GET en el nodo http request y agregar el url la dirección obtenida en openweathermap.org/
4. Cambiar la propiedad del nodo tipo json para que siempre convierta a objetos Javascript
5. Cambiar el nombre del 1° nodo function a Temperatura API y añadir el siguiente codigo en la pestaña on message: 
    global.set ("tempAPI",msg.payload.main.temp);
    msg.payload = msg.payload.main.temp;
    msg.topic = "Temperatura";
    return msg;

6. Cambiar el nombre del 2° nodo function a Humedad API y añadir el siguiente codigo en la pestaña on message: 
    msg.payload = msg.payload.main.humidity;
    global.set ("humAPI",msg.payload);
    msg.topic = "Humedad";
    return msg;

7. Agregar una nueva tabla en el dashboard de nombre flow5 y añadir 3 grupos dentro de ella con los nombres de Temperatura, Humedad e Historico, dar clic en los nodos de temperatura API, humedad API e historico API y asociarlos con los grupos creados
8. Modificar los rangos de los nodos de temperatura y humedad de minimo a maximo
9. Hacer clic en el boton Deploy

# Instrucciones de operación
Para observar el resultado de este flow, sólo es necesario abrir en otra pestaña del navegador la direccion http://localhost:1880/ui y seleccionar el flow5, dar clic en timestamp para enviar la información de nuestro http request 

# Resultados
A continuación puede verse una vista previa del resultado de este flow.
Resultados

Diagrama de nodos 
![Cargando](https://github.com/DanielRochez/flow5-NodeRed/blob/main/imagen7.png?raw=true)

Resultado en pantalla
![Cargando](https://github.com/DanielRochez/flow5-NodeRed/blob/main/imagen8.png?raw=true)

# Evidencias


# Créditos
Desarrollado por Daniel Rochez

* [GitHub](https://github.com/DanielRochez)
