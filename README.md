# Cheatsheet + Documentación de NODEJS

¿Este es un cheatsheet mas de NodeJS? No, Este cheatshet tambien contiene un wiki con la documentación mas de NodeJS acá:
[Wiki Documentación NodeJS](https://github.com/fabiansato/nodeJS-cheatsheet/wiki "Documentación de NodeJS")


------------------------------

# 1.  NodeJS

NodeJS, es básicamente un framework para implementar operaciones de entrada y salida, como decíamos anteriormente. Está basado en eventos, streams y construido encima del motor de Javascript V8, que es con el que funciona el Javascript de Google Chrome.


# 2. Instalación de NodeJS

## Bajar siempre la última versión LTS

Windows:
Si estás en Windows, al pulsar sobre Install te descargará el instalador para este sistema, un archivo con extensión "msi" que como ya sabes, te mostrará el típico asistente de instalación de software.

Linux
```linux
sudo apt-get install python-software-properties
sudo add-apt-repository ppa:chris-lea/node.js
sudo apt-get update
sudo apt-get install nodejs npm
```

# 3. Características fundamentales de Node.JS 

# 4. Módulos en NodeJS


# 5. Eventos en NodeJS


------------------------------
## Modulos en NodeJS

#### Enviar funcion como objeto a otro modulo de nodejs
Envia el contenido de una funcion como un objeto
```nodejs
exports.lafuncion=lafuncion; 

```

#### recibe otro modulo de nodejs y lo guarda como como objeto
```nodejs
const objetonuevo=require('./archivo'); /*guarda en un objeto javascript el archivo (archivo.js) externo*/
```

### mostrar objeto con metodo/funcion
```nodejs
console.log('La suma de 2+2='+objetonuevo.sumar(2,2)) 
```
muestra por pantalla el objetonuevo con metodo sumar y manda por parametros 2 y 7

####  modulo de sistema operativo
```nodejs
const os=require('os');
```

### consumir modulo sistema operativo
```nodejs
os.platform(); /* mostrar sistema operativo */
+os.release(); /* version del sistema operativo */
os.totalmem(); /* Memoria total*/
os.freemem(); /* Memoria libre*/
```


####  modulo de archivos
```nodejs
const fs=require('fs');
```

Luego de el pedido de la linea fs, ponemos el writefile con archivos
```nodejs
/*llama al modulo fs y al metodo wirte file, le agrega un el nombre del archivbo y las lienas y llama al error si existe*/
fs.writeFile('./archivo1.txt', 'línea 1\nLínea 2', error => { 
  if (error)
    console.log(error);
  else
    console.log('El archivo fue creado');
});
```

// mas modulos de nodejs
https://nodejs.org/api/fs.html

####  modulo https
```nodejs
const http=require('http');
```
####  Levantar un Servidor web con Node.js
```nodejs
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
