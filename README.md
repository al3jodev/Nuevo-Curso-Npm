# Nuevo-Curso-Npm
Proyecto inicial del Nuevo Curso de NPM: Gestión de paquetes y dependencias en Javascript

## Comandos Basicos

Ver que version tenemos instalada de node:
```sh
node -v
```
Ver que version tenemos instalada de npm:
```sh
npm -v
```
Actualizar a la ultima version de npm:
```sh
npm install -g npm@latest
```

### Inicializar proyecto

El siguiente comando me permite inicializar un proyecto npm, una vez ejecuta me solicitara una cierta informacion necesaria para crear el archivo package.json

```sh
npm init
```
Inicializar parametros globales como autor, email:
```
npm set init.author.email "al3jodev@outlook.com"
npm set init.author.name "Alejandro Jaramillo"
```

Otra forma rapida de crear el package.json con valores globales definidos anteriormente es:
```sh
npm init -y
```

### Instalar dependencias

#### Dependencias para produccion

Para definir dependencias para produccion se utiliza los siguientes flags:

```sh
npm install moment --save
```

Otra forma
```sh
	npm install moment -S
```

#### Dependencias para desarrollo

Para definir dependencias para produccion se utiliza los siguientes flags:

```
npm install moment --save-dev
```
Otra forma
```
npm install date-fns -D
```
		
#### Dependencias Globales

Para instalar dependencias de forma global:
```
sudo npm install -g nodemon		
```

Ver paquetes instalados de forma global
```
npm list -g --depth 0
```
#### Dependencias Opcionales

Instalar paquetes opcionales
```
npm install eslint -O
```
Simulacion de instalacion de paquetes para verificar si existen conflictos:
```
npm install react --dry-run
```
	
Forzar la instalacion de paquetes:
```
npm install webpack -f
```
Para instalar todas las dependencias referenciadas en el archivo package.json	
```
npm install
```

Instalar paquetes con un numero de version especifica:
```
npm install json-server@0.15.0
```
	
Listar paquetes instalados
```
npm list
```

Revisar paquetes instalados con nuevas versiones disponibles:
```
npm outdate
```

Para ver un output más detallado
```
npm outdate --dd
```

Actualizar los paquetes que no están en la ultima versión
```
npm update
```

Actualizar la ultima version de un paquete especifico
```
npm install json-server@latest
```

### Eliminar paquetes

Eliminar un paquete de node_modules y del archivo package.json
```
npm uninstall json-server
```

Desinstalar un paquete de todo node_modules pero no del archivo package.json:
```
npm uninstall webpack --no-save
```
## Informacion adicional

El archivo package-lock.json describe todo el árbol de dependencias de cada paquete instalado. Cuando alguien hace fork de un repositorio no tiene el directorio node_modules.
Con el comando npm install se instalarán las dependencias indicadas en el package.json con la versión indicada. También, se instalarán las sub-dependencias indicadas en package-lock.json con la versión indicada. Pero, ¿qué significan estas diferentes versiones en cada dependencia?
Versionado de paquetes
El versionado de paquetes está conformado por tres valores:

Major: el valor que muestra la versión que contiene los cambios importantes del paquete
Minor: el valor que muestra la versión que contiene los cambios en funcionalidades, pero no representan un cambio significativo
Patch: el valor que muestra la versión que contiene cambios rápidos para solucionar problemas de seguridad o bugs


Símbolos ^ y ~ para actualizar las versiones minor y patch
Existen dos símbolos que acompañan a este versionado, que sirven para actualizar las versiones minor y patch del paquete:

Caret (^): Permite actualizar las versiones minor y patch
Tilde (~): Permite actualizar las versiones patch

Por ejemplo, tenemos la versión “5.2.3”:

Si tiene el carret ^, actualizará la versión minor y patch, por lo que tendrás versiones como “^5.3.3”, “^5.4.3”, “^5.4.4”, etc.
Si tiene la tilde ~, actualizará la versión de patch, por lo que tendrás versiones como “~5.2.4”, “~5.2.5”, “~5.2.6”, etc.

Lo recomendable es quitar estos símbolos y tener la versión exacta para evitar problemas de versionado, principalmente con paquetes que los mantienen pocas personas o no son fiables.

## EJECUTAR TAREAS

El apartado de "scripts" en el package.json es el que indica los comandos a ejecutar del proyecto. Esta sección es la que utilizarás para crear comandos que optimicen el desarrollo de tu aplicación.
Crear un comando en tu proyecto
Para crear un comando en tu proyecto sigue la siguiente estructura, donde <nombre> es el nombre del comando que debería ser muy descriptivo y <comando> es el comando que utilizarías en la terminal:
```
{
    "scripts": {
        "<nombre>": "<comando>"
    }
}
```
Una vez hayas escrito el comando en el archivo package.json, la manera de ejecutarlo será con el comando npm run.
Por ejemplo, creemos tres comandos para iniciar el proyecto (start), crear un archivo para producción (build) y combinarlos (deploy). Que no te preocupe si no entiendes cada comando, solo entiende cómo ejecuta NPM el script.
```
{
    "scripts": {
        "start": "webpack-dev-server --open --mode development",
        "build": "webpack --mode production",
        "deploy": "npm run format && npm run build"
    }
}
```
Y para ejecutarlos, es necesario utilizar el comando pertinente en la terminal:
```
$ npm run start
$ npm run build
$ npm run deploy
```
## Solución de problems en proyectos con NPM

Cuando estés desarrollando un proyecto con NPM, puede que generes errores que no permitan seguir con tu trabajo. Saber manejar los errores es fundamental para solucionarlos y seguir con tus tareas (y no entrar en pánico). Alguno de estos errores pueden ser:

Errores en la configuración del archivo package.json
Errores del sistema operativo
Configuración errónea de Git o GitHub
Errores ortográficos (typos)
O errores que no estén ligados directamente a NPM

Mostrar todos los pasos de un comando de NPM
Para identificar el error que puede existir en tu proyecto, es necesario analizar cada paso que ejecuta un comando, para saber qué o en dónde ocurre el problema.
El flag --dd en un comando de NPM, te mostrará de manera verbosa cada paso que se ejecuta. De esta manera podrás observar si existe un error para solucionarlo.
$ npm [comando] --dd

Otra forma, es ejecutar el comando de NPM. Si existe un error, la terminal te mostrará los diferentes errores que encontró. Al final de este resumen, existirá una ruta con los detalles del error, lo puedes abrir para observar los pasos que ejecutó NPM.

Error de dependencias en node_modules
Existen situaciones en las que instalas una dependencia con una versión que no corresponde a la deseada. En esta situación, puedes utilizar los siguientes comandos, el primero para borrar el caché de NPM y el segundo para verificar si están eliminados correctamente.
```
$ npm cache clean --force
$ npm cache verify
```
Si existen valores corruptos o una instalación incorrecta de una dependencia, deberás eliminar el directorio de node_modules y después ejecutar el comando npm install para instalar correctamente los paquetes.
Contribución creada con aportes de: Andrés Guano.
```
rm -rf node_modules/
```
Borrar carpeta node_modules/
```	
	sudo npm install -g rimraf
```
Se borra la carpeta
```
	rimraf node_modules
```	 
## Gestionar la seguridad en proyectos con NPM
```
npm install --ya hace una verificacion inicial de paquetes
npm audit
npm audit fix
```
Actualizar paquete de uno a uno en caso que audit fix no lo haga
```
npm update eslint-utils --depth 2 
```

## Publicar un paquete en NPM

Antes de publicar un paquete en NPM debes asegurarte de cumplir con los siguientes requisitos:

Asegurar que el programa funcione reduciendo en lo posible los bugs
Revisar que la configuración del archivo package.json sea correcta
Tener un nombre único para el proyecto, usando guiones (-) para separar palabras y evitando números
Crear una cuenta en NPM, ya que aquí estarán tus paquetes a tu nombre. Después, debes utilizar el comando npm adduser para iniciar sesión en la terminal. Si no aparece tu contraseña, no te preocupes, es una forma de seguridad

Una vez hayas cumplido los requisitos, ejecuta el comando npm publish y si no existen errores, tu paquete será publicado. Puedes utilizar el comando npm whoami para visualizar el usuario en el que publicarás el paquete, esto es importante si tienes varias cuentas de NPM.
Si realizas cambios en tu código, deberás cambiar la versión de tu proyecto, puedes utilizar los siguientes comandos:
### Aumenta una version path (1.0.0) -> (1.0.1)
```
$ npm version patch 
```
### Aumenta una version minor (1.0.0) -> (1.1.0)
```
$ npm version minor
```
### Aumenta una version major (1.0.0) -> (2.0.0)
```
$ npm version major
```
### Aumenta una version específica (1.0.0) -> (3.1.1)
```
$ npm version <version>
```

Una vez actualizada la versión de tu proyecto, puedes ejecutar nuevamente el comando npm publish para actualizarlo en los repositorios de NPM.
Publicando el proyecto de mensajes aleatorios
Antes de publicar el proyecto de mensajes aleatorios, debemos asegurarnos de que el programa se ejecute bien en la terminal. Para esto, identifica el directorio en el que te encuentras, debe ser el mismo del proyecto con el comando pwd.
También debes ejecutar el comando sudo npm link que te permitirá hacer una referencia al paquete hacia el directorio global de NPM, similar a cómo se instalaría desde los servidores de NPM.
Otra forma es instalarlo de manera global, como cualquier otra dependencia, pero en lugar del nombre de la dependencia, estará la ruta del proyecto:
```
$ sudo npm install -g /users/tuUsuario/random-messages
```

De esta manera, ya puedes ejecutar el programa con el comando que creamos en "bin", random-msg y funcionará de forma global en el sistema.
Una vez revisado todo, ya puedes ingresar tu usuario con npm adduser y publicarlo con npm publish. En los paquetes de tu usuario de NPM aparecerá algo parecido a esto: