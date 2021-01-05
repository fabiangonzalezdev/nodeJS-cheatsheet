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
# Características fundamentales de Node.JS
------------------------------

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

------------------------------

