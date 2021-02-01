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
## para instalar un proyecto limpio ponemos:
`npm init`
`npm install --save express`
abrir `package.json`
agregar `"main": "nombredelindex.js",`
agregar `"start": "node nombredelindex"`
en primer programa agregamos:

```node
// npm start y listo
// correr el programa en localhost:3000
var express = require('express'); 
var app = express();

const path = require("path");
const http = require("http");

console.log('Ejemplo de app corriendo en el servidor 3000!');

//Se crea el servidor http con el cual podras hacer POST y GET
http.createServer(function (req, res) {
    res.writeHead(200, { 'Content-Type': 'text/html' });
    res.write('Hola este es el primer programa de Nodejs Para utn!');
    res.end();
    
}).listen(3000);

//Aquí en medio puede ir tu código.

app.use(express.static(path.join(__dirname, '/')));
npm start

```


PERO!! para instalar un rpoyecto completo ponemos

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

---------------------------------------------
## Express – Direccionamiento
---------------------------------------------

El direccionamiento hace referencia a la determinación de cómo responde una aplicación a una solicitud de cliente en un determinado punto final, que es un URI (o una vía de acceso) y un método de solicitud HTTP específico (GET, POST, etc.).

La definición de ruta tiene la siguiente estructura:

```node
app.METHOD(PATH, HANDLER)
```
Donde:

    app es una instancia de express.
    METHOD es un método de solicitud HTTP.
    PATH es una vía de acceso en el servidor.
    HANDLER es la función que se ejecuta cuando se correlaciona la ruta.

Por ejemplo en el directorio route encontramos el archivo index.js, el mismo tendrá la definición de nuestra ruta por default (es decir cuando accedemos a la home de nuestro sitio “/”)


--------------------
## Vías de acceso de rutas con expresiones regulares
--------------------

Estos son algunos ejemplos de vías de acceso de ruta basadas en patrones de serie.

Esta vía de acceso de ruta coincidirá con acd y abcd.

```node
app.get('/ab?cd', function(req, res) {
  res.send('ab?cd');
});
```
Esta vía de acceso de ruta coincidirá con abcd, abbcd, abbbcd, etc.

```node
app.get('/ab+cd', function(req, res) {
  res.send('ab+cd');
});
```
Esta vía de acceso de ruta coincidirá con abcd, abxcd, abRABDOMcd, ab123cd, etc.

```node
app.get('/ab*cd', function(req, res) {
  res.send('ab*cd');
});
```
Esta vía de acceso de ruta coincidirá con /abe y /abcde.

```node
app.get('/ab(cd)?e', function(req, res) {
 res.send('ab(cd)?e');
});
```
Los caracteres ?, +, * y () son subconjuntos de sus contrapartidas de expresiones regulares. El guión (-) y el punto (.) se interpretan literalmente en las vías de acceso basadas en series.



```node
app.get(/a/, function(req, res) {
  res.send('/a/');
});

```
Esta vía de acceso de ruta coincidirá con butterfly y dragonfly, pero no con butterflyman, dragonfly man, etc.


```node
app.get(/.*fly$/, function(req, res) {
  res.send('/.*fly$/');
});

```



---------------------------------------------
## Express – Funciones de llamadas
---------------------------------------------

Una función de devolución de llamada individual puede manejar una ruta. Por ejemplo:


```node
app.get('/example/a', function (req, res) {
  res.send('Hello from A!');
});

```
Más de una función de devolución de llamada puede manejar una ruta (asegúrese de especificar el objeto next). Por ejemplo:


```node
app.get('/example/b', function (req, res, next) {
  console.log('the response will be sent by the next function ...');
  next();
}, function (req, res) {
  res.send('Hello from B!');
});

```
Una matriz de funciones de devolución de llamada puede manejar una ruta. Por ejemplo:


```node
var cb0 = function (req, res, next) {
  console.log('CB0');
  next();
}

var cb1 = function (req, res, next) {
  console.log('CB1');
  next();
}

var cb2 = function (req, res) {
  res.send('Hello from C!');
}

app.get('/example/c', [cb0, cb1, cb2]);

```
Una combinación de funciones< independientes y matrices de funciones puede manejar una ruta. Por ejemplo:


```node
var cb0 = function (req, res, next) {
  console.log('CB0');
  next();
}

var cb1 = function (req, res, next) {
  console.log('CB1');
  next();
}

app.get('/example/d', [cb0, cb1], function (req, res, next) {
  console.log('the response will be sent by the next function ...');
  next();
}, function (req, res) {
  res.send('Hello from D!');
});

```
## Métodos de respuesta

Los métodos en el objeto de respuesta (res) de la tabla siguiente pueden enviar una respuesta al cliente y terminar el ciclo de solicitud/respuestas. Si ninguno de estos métodos se invoca desde un manejador de rutas, la solicitud de cliente se dejará colgada.
Método | Descripción
------- | ------
res.download() | Solicita un archivo para descargarlo.
res.end() | Finaliza el proceso de respuesta.
res.json() | Envía una respuesta JSON.
res.jsonp() | Envía una respuesta JSON con soporte JSONP.
res.redirect() | Redirecciona una solicitud.
res.render() | Representa una plantilla de vista.
res.send() | Envía una respuesta de varios tipos.
res.sendFile() | Envía un archivo como una secuencia de octetos.
res.sendStatus() | Establece el código de estado de la respuesta y envía su representación de serie como el cuerpo de respuesta.


---------------------------------------------
## Express – Router
---------------------------------------------

## app.route()

Puede crear manejadores de rutas encadenables para una vía de acceso de ruta utilizando app.route(). Como la vía de acceso se especifica en una única ubicación, la creación de rutas modulares es muy útil, al igual que la reducción de redundancia y errores tipográficos. Para obtener más información sobre las rutas, consulte: Documentación de Router().

A continuación, se muestra un ejemplo de manejadores de rutas encadenados que se definen utilizando app.route().

```node
app.route('/book')
  .get(function(req, res) {
    res.send('Get a random book');
  })
  .post(function(req, res) {
    res.send('Add a book');
  })
  .put(function(req, res) {
    res.send('Update the book');
  });
```


## express.Router

Utilice la clase express.Router para crear manejadores de rutas montables y modulares. Una instancia Router es un sistema de middleware y direccionamiento completo; por este motivo, a menudo se conoce como una “miniaplicación”.

El siguiente ejemplo crea un direccionador como un módulo, carga una función de middleware en él, define algunas rutas y monta el módulo de direccionador en una vía de acceso en la aplicación principal.

Cree un archivo de direccionador denominado birds.js en el directorio de la aplicación, con el siguiente contenido:

```node

var express = require('express');
var router = express.Router();

// middleware that is specific to this router
router.use(function timeLog(req, res, next) {
  console.log('Time: ', Date.now());
  next();
});
// define the home page route
router.get('/', function(req, res) {
  res.send('Birds home page');
});
// define the about route
router.get('/about', function(req, res) {
  res.send('About birds');
});

module.exports = router;
```

A continuación, cargue el módulo de direccionador en la aplicación:

```node
var birds = require('./birds');
...
app.use('/birds', birds);
```
La aplicación ahora podrá manejar solicitudes a /birds y /birds/about, así como invocar la función de middleware timeLog que es específica de la ruta.




---------------------------------------------
## Express – Crear una nueva ruta
---------------------------------------------
Debemos crear el archivo correspondiente en la carpeta routes
ejemplo:
```productos.js``` en ```routes```

Debemos incluir el modulo “Express” utilizando require y acceder al método router.
```node
 var express = require('express');
 var router = express.Router();

/* GET home page */
router.get('/:id([0-9]+)', function(req, res,next) {
 console.log(req.query.nombre);
 console.log(req.params.id);
 res.render('catalogo', { title: 'productos'};
});

module.export = router
```

Con el método router podemos acceder a métodos según los verbos del protocolo http


•	Router.get

•	Router.post

•	Router.put

•	Router.delete

## Ruteo
El primer parámetro de los métodos en la URL con la cual se realizara el match. El match lo realiza en base al use de app.js.
Ejemplo App.js
```node
app.use('/productos', productosRouter);
```

Productos.js (dentro de directorio router)
```node
router.get('/',
```

Va a realizar el match con la url **/productos/**.

/productos lo toma del app.js

/ lo toma del archivo productos.js

Si en el archivo productos.js ahora sumamos
```node
router.get('/destacados',
```
En este último caso el match será con **/productos/destacados**

/productos -> app.js

/destacados -> productos.js

## Parámetros por URL
En la declaración de las rutas, podemos indicar la recepción de un parámetro por URL
```node
router.get('/:id([0-9]+)', function(req, res, next){
```

En este caso el dato enviado en la Url se asignara a la variable id.

También se especifica que la misma debe ser solo numérica (expresión regular) Ejemplo si navegamos la siguiente URL
```node
localhost:3000/productos/1
```

Podemos ver la consola y que muestra

Del lado del router tenemos el siguiente código
```node
router.get('/:id([0-9]+)', function(req, res, next){
 console.log(req.params.id);
 res.reder('catalogo', { title: 'productos', subtitl
});
```
Como vemos el objeto req.params tiene la información de las variables mapeadas desde la URL. En este ejemplo id

Si recibimos parámetros por query string
```
localhost:3000/productos/1?nombre=fabian
```

Lo recibimos de la siguiente manera
```node
router.get('/:id([0-9]+), function(req, res, next){
  console.log(req.query.nombre);
  res.render('catalogo', { title: 'productos'. subtitle:'
});
```

El objeto query tiene la información enviada por query string en la URL

En el caso de recibir datos en el body (ejemplo peticiones por POST) los mismos se reciben en req.body
```node
router.post('/', function(req,res,next){
 let producto = new productosModel({
 name: req.body.name,
 description: req.body.description,
 sku: req.body.sku,
 price: req.body.quantity,
 category: req.body.category
})
let data = await producto.save();
res.status(201).json({ "status": "ok", "data": "data"});

```

------------------------------
# MongoDB
------------------------------
Es una base de datos noSQL con colecciones de documentos 
si quiero crear una colección
create y nombre de la colección
podemos, insertar, quitar, actualizar, cualquier objeto.
Si podemos edit sobre un documento podemos editar el documento.
OJO si usamos UPDATE, los documentos se PISAN por completo salvo que nosotros identifiquemos que no lo haga.
ejemplo
```json
//options
{
 "multi" : false, // si esta en true modifica todos los contenidos con la misma data
 "upsert": false. // si el objeto existe lo actualiza, si no existe lo crea
 }
 ```
 
 ## Mongoose
 ----------------------
 para instalarlo a nuestro proyecto
 `npm install mongoose`
 hacemos un archivo de conexión contra esa base de datos de mongoose
  ```nodejs
 var mongoose = require('mongoose');
mongoose.connect('mongodb://localhost/pwa2020', { useNewUrlParser: true }, function (error) {
    if (error) {
        throw error;
    } else {
        console.log('Conectado a MongoDB');
    }
});
module.exports = mongoose; 
  ```
  Podemos crear productos que se conecten con la base de datos de mongoose ejemplo:

  ```nodejs
const mongoose = require("../bin/mongodb")

const productSchema = new mongoose.Schema({
    name:{
        type:String,
        required:[true,"El campo nombre es obligatorio"],
        minlength:1,
        maxlength:10
    },
    sku:{
        type:String,
        unique:true
    },
    description:String,
    price:{
        type:Number,
        get:function(price){
            return price*1.21
        }
    },
    status:{
        type:String,
        enum:["aprobado","inactivo"]
    }
})
productSchema.virtual("price_currency").get(function(){
    return "$ "+this.price
})
productSchema.set("toJSON",{getters:true,virtuals:true})
module.exports=mongoose.model("products",productSchema)
  
   ```
 
