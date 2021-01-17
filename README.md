# Cheatsheet + Documentación de NODEJS

¿Este es un cheatsheet mas de NodeJS? No, Este cheatshet tambien contiene un wiki con la documentación mas de NodeJS acá:
[Wiki Documentación NodeJS](https://github.com/fabiansato/nodeJS-cheatsheet/wiki "Documentación de NodeJS")


------------------------------

# NodeJS
------------------------------
NodeJS, es básicamente un framework para implementar operaciones de entrada y salida, como decíamos anteriormente. Está basado en eventos, streams y construido encima del motor de Javascript V8, que es con el que funciona el Javascript de Google Chrome.


------------------------------
# Instalación de NodeJS
------------------------------
## Bajar siempre la última versión LTS

Windows:
Si estás en Windows, al pulsar sobre Install te descargará el instalador para este sistema, un archivo con extensión "msi" que como ya sabes, te mostrará el típico asistente de instalación de software.

Linux:
```linux
sudo apt-get install python-software-properties
sudo add-apt-repository ppa:chris-lea/node.js
sudo apt-get update
sudo apt-get install nodejs npm
```
Mac:
```terminal
brew install nodejs
```
y
```terminal
brew update
```


------------------------------
#  Módulos en NodeJS
------------------------------

#### Enviar funcion como objeto a otro modulo de nodejs
Envia el contenido de una funcion como un objeto
```node
exports.lafuncion=lafuncion; 

```

#### recibe otro modulo de nodejs y lo guarda como como objeto
```node
const objetonuevo=require('./archivo'); /*guarda en un objeto javascript el archivo (archivo.js) externo*/
```

### mostrar objeto con metodo/funcion
```node
console.log('La suma de 2+2='+objetonuevo.sumar(2,2)) 
```
muestra por pantalla el objetonuevo con metodo sumar y manda por parametros 2 y 7

####  modulo de sistema operativo
```node
const os=require('os');
```

### consumir modulo sistema operativo
```node
os.platform(); /* mostrar sistema operativo */
+os.release(); /* version del sistema operativo */
os.totalmem(); /* Memoria total*/
os.freemem(); /* Memoria libre*/
```


####  modulo de archivos
```node
const fs=require('fs');
```

Luego de el pedido de la linea fs, ponemos el writefile con archivos
```node
/*llama al modulo fs y al metodo wirte file, le agrega un el nombre del archivbo y las lienas y llama al error si existe*/
fs.writeFile('./archivo1.txt', 'línea 1\nLínea 2', error => { 
  if (error)
    console.log(error);
  else
    console.log('El archivo fue creado');
});
```

### mas modulos de nodejs:
https://nodejs.org/api/fs.html

###  modulo https
```node
const http=require('http');
```
### 


Cuando accedemos a un sitio web desde un navegador escribimos entre otras cosas:
```node
http://host[:puerto][/ruta y archivo][?parámetros]
```

•	http (indica el protocolo que utilizamos para conectarnos con un servidor web)

•	host (es el nombre del dominio por ej. google.com.ar)

•	puerto (es un número que generalmente no lo disponemos ya que por defecto el protocolo http utiliza el nro 80, salvo que nuestro servidor escuche peticiones en otro puerto que ya en este caso si debemos indicarlo)

•	[/ruta y archivo] (indica donde se encuentra el archivo en el servidor)

•	?parámetros (datos que se pueden enviar desde el cliente para una mayor identificación del recurso que solicitamos)
###  Levantar un Servidor web con Node.js
```node
const http=require('http');

const servidor=http.createServer((pedido,respuesta) => {
  respuesta.writeHead(200, {'Content-Type': 'text/html'});
  respuesta.write(`<!doctype html><html><head></head>
                   <body><h1>Sitio en desarrollo</h1></body></html>`);
  respuesta.end();
});

servidor.listen(8888);

console.log('Servidor web iniciado');
});
```

El parámetro respuesta es el que tenemos que llamar a los métodos:

•	`writeHead:` es para indicar la cabecera de la petición HTTP (en esta caso indicamos con el código 200 que la petición fue Ok y con el segundo parámetro inicializamos la propiedad Content-Type indicando que retornaremos una corriente de datos de tipo HTML

•	`write:` mediante la función write indicamos todos los datos propiamente dicho del recurso a devolver al cliente (en este caso indicamos en la cabecera de la petición que se trataba de HTML)

•	`end:` finalmente llamando a la función end finalizamos la corriente de datos del recurso (podemos llamar varias veces a la función write previo a llamar por única vez a end)


------------------------------
# 5. Eventos en NodeJS
------------------------------
Los eventos del lado del servidor, no tienen nada que ver con los eventos Javascript que conocemos y utilizamos en las aplicaciones web del lado del cliente
Los eventos se encuentran en un módulo independiente que tenemos que requerir en nuestros programas creados con Node JS con la sentencia "require" que ya hemos visto.
```node
var eventos = require('events');
```


Veamos primero el emisor de eventos, que encuentras en la propiedad EventEmitter.
```node
var EmisorEventos = eventos.EventEmitter;
```
Primero tendremos que "instanciar" un objeto de la clase EventEmitter, que hemos guardado en la variable EmisorEventos.
```node
var ee = new EmisorEventos();
```

Por ejemplo, voy a emitir un evento llamado "datos", con este código.
```node
ee.emit('datos', Date.now());
```


Ahora voy a hacer una función manejadora de eventos que se asocie al evento definido en "datos".

```
ee.on('datos', function(fecha){
console.log(fecha);

});
```
------------------------------


-------------------------------
# API Rest
-------------------------------

•	Protocolo cliente/servidor sin estado: cada petición HTTP contiene toda la información necesaria para ejecutarla,
Las operaciones más importantes relacionadas con los datos en cualquier sistema REST y la especificación HTTP son cuatro: `POST (crear)`, `GET (leer y consultar)`, `PUT (editar)` y `DELETE (eliminar)`.

•	Los objetos en REST siempre se manipulan a partir de la URI.

•	Interfaz uniforme. 

•	Sistema de capas.

•	Uso de hipermedios
Ejemplo

Puedes consultar qué modos de envío tiene habilitado el usuario de la siguiente manera:
```node
GET https://api.mercarolibre.com/users/:user_id?access_token=
```


respuesta:
```node
“shipping_modes”:{

“custom”,
“not_specified”,
“me1”,
“me2”
} 
```
-------------------------------
# Express
-------------------------------
<img src="https://fabiansato.github.io/logos/nodeexpress.png">

## Instalar Express
Instalación
crear directorio:

```node
$ mkdir myapp
$ cd myapp
```

Utilice el mandato npm init

⚠️Importante para inicializar cualquier proyecto
```node
$ npm init
```
Este mandato solicita varios elementos

```node
entry point: (index.js)
```

A continuación, instale Express en el directorio myapp y guárdelo en la lista de dependencias. Por ejemplo:

```node
$ npm install express --save
```
Para instalar Express temporalmente y no añadirlo a la lista de dependencias, omita la opción --save:

```node
$ npm install express
```

----------------------------------------
# Instalar un proyecto rapido
----------------------------------------
para instalar un rpoyecto completo ponemos

```node
express --view=ejs nombredelproyecto
```

luego el mismo proyecto nos va a decir que hagamos
```node
   change directory:
     $ cd nombredelproyecto

   install dependencies:
     $ npm install

   run the app:
     $ DEBUG=nombredelproyecto:* npm start
```

listo!! podremos entrar en nuestro navegador en https://localhost:3000
listooo

⚠️(opcional es mejor hacer un `npm install nodemon -g ` y ejecutamos `nodemon npm start` y es mejor porque se refresca automaticamente!!

## IMPORTANTE 
si se comparte un proyecto no compartir la carpeta "node_modules" la misma se crea simplemente haciendo un `npm install` en la terminal

## Hello world

agregar un archivo app.js

```node
const express = require('express')
const app = express()
const port = 3000

app.get('/', (req, res) => {
  res.send('Hello World!')
})

app.listen(port, () => {
  console.log(`Example app listening at http://localhost:${port}`)
})
```


Ejecute la aplicación con el siguiente mandato:

```node
$ node app.js
```
## Express Generator
Para instalar esta herramienta debemos ejecutar:
```node
npm install express-generator -g
```

visualizar las opciones que nos brinda esta herramienta;
```node
express –h 
```
##crear nuestra primera aplicación:
```node
express --view=ejs myapp
```
dentro del directorio donde se creó nuestra app:
ejecutamos: `npm install`
ejecutamos (desde windows):
```node
set DEBUG=myapp:* & npm start
```
o desde LINUX o MAC:
```node
DEBUG=myapp:* npm start
```
Cada vez que queramos “levantar” nuestro servidor en el puerto 3000 debemos ejecutar este último comando
Si en la barra de direcciones de nuestro navegador colocamos:

`http://localhost:3000/`

Accederemos al contenido de nuestra aplicación.

---------------------------------------------
## Express - extructura de directorios
---------------------------------------------

Al crear nuestra aplicación en node visualizaremos la siguiente estructura de directorio:

•	**bin**: Directorio propio de express, en el cual podremos visualizar la creación de un servidor en node js

•	**node_modules**: Carpeta propia de node, allí se alojaran todos los modulos instalados con npm install

•	**public**: Se aloja el contenido publico

       o	**Imágenes**

       o	**Javascript**

       o	**CSS**

•	**routes**: Se alojan los archivos que oficiaran de “ruteadores”, es decir que serán visualizados de acuerdo a la URL que accedamos

•	**views**: Se alojan las vistas de nuestra aplicación. En este caso son de tipo ejs. 

app.js --- archivo principal con el primer nivel de ruteo 

## IMPORTANTE 
si se comparte un proyecto no compartir la carpeta "node_modules" la misma se crea simplemente haciendo un `npm install` en la terminal

