## Comandos en acción:
#####  - CONFIGURACIÓN INICIAL GIT:

```
git --version
git config --global user.name "Franco Villagra"
git config --global user.mail fr4nconv@gmail.com
```
- INSTALACIÓN VS-CODE:
```
git config --global core.editor "code --wait"
git config --global -e
git config --global core.autocrlf true
```
- Para indagar aún más en git, usamos:
```
git config -h
```
Este comando nos entrega un listado de todas las configuraciones de todas las opciones que nosotros podemos agregar a nuestra configuración.

##### Comandos básicos de BASH:
- Es un comando básico que nos permite listar todos los archivos y carpetas que se encuentren.
```
ls
```
- En qué carpeta te encontrás.
```
pwd
```
- Escribimos cd seguido el nombre de la carpeta a la que queremos ingresar.
```
cd (más el nombre de la carpeta a la que queremos ingresar )
```
- Si me quiero salir de la carpeta donde ingresé, escribo:
```
cd ..
```
- Para crear un nuevo archivo:
- Luego escribimos ls para verificar que se creo el archivo.
```
mkdir "nombre del archivo"
```
- Para iniciar un repositorio totalmente vacío.
```
git init
```
- Para mostrar todos los archivos ocultos, incluido el .git
```
ls -a
```
- Para acceder a esa carpeta oculta.
```
cd .git
```
- Al acceder a la carpeta oculta, si volvemos a escribir ls -a, nos va a aparecer un detalle de todos los archivos que se utilizan en .git para gestionar todos nuestros proyectos, esto es un detalle de implementacion.
```
ls -a
```
##### Agregando cambios a Stage:

- Abrimos el editor de texto: Code .
- Creamos un archivo, puede ser cualquier extensión, en este caso, creé el archivo1.txt
- Escribimos en el editor de texto, guardamos, volvemos a la terminal y escribimos: 
git status (estado actual de nuestro repositorio)
- En este punto, nuestro archivo aparece en la terminal de color rojo con la siguiente leyenda: UNTRACKED FILES: (use "git add <file>..." to include in what will be commited)
- Tenemos que seleccionar el archivo, para eso, podemos utilizar los siguientes comandos:
git add archivo1.txt (nombre del archivo, más extensión)
git add *.txt (agrega todos los archivos que tengan extension .txt)
git add . (el punto lo que hará, será agregar todos los archivos que aparezcan dentro del listado)
- En este caso, el que utilizamos es git add archivo1.txt
Nuevamente escribimos: git status (Estado actual de nuestro repositorio), en este punto, nuestro archivo aparece en la terminal de color verde con la siguiente leyenda: Changes to be committed (cambios listos para ser comprometidos) new file: archivo1.txt
- Si quisiera agregar mas de un archivo, debo escribir: git add archivo1.txt (espacio) y el nombre del siguiente archivo.

- Cada vez que se modifica el texto dentro del editor de códigos, se escribe en la terminal:
```
git status
git add
git status (para verificar que se aplico las modificaciones)
```
##### Commit en Git

Para comprometer nuestro trabajo, existen dos formas:
```
git commit -m "escribimos el nombre del archivo a comprometer"
git commit (al presionar enter, se nos abre nuestro editor de texto, porque ese es el editor que configuramos al principio)
```
##### Eliminando archivos de nuestro repositorio:
En la terminal, escribimos:

```
ls
```
En este sentido, para realizar un listado de los elementos que se encuentran en las carpetas. En este caso, vamos a eliminar un archivo de los que tenemos:
###### archivo1.txt y archivo2.txt

En la terminal, escribimos:

```
rm archivo2.txt
```
Presionamos enter, luego git status.
Lo que podemos ver, es que no aparece en texto rojo archivo2.txt, esto significa que son cambios que realizamos que no se encuentran en la etapa de staged, asique lo que vamos a hacer es agregar este cambio, para eso escribimos:

```
git add archivo2.txt
```
Presionamos enter, luego git status.
Ahora nos muestra que tenemos la acción de eliminar el archivo2.txt, y que este se encuentra en la etapa de stage, ahora lo que se va a hacer es un commit de este cambio:

```
git commit -m "eliminando archivo 2"
```
Con esto, vemos que el cambio se ha comprometido, luego escribimos git status, veremos que el archivo ya no se encuentra en el listado o en la etapa de stage. 
Escribimos ls, y vemos que el archivo ya no se encuentra en el listado.

##### Volviendo del Staged y descartar cambios:

- Si por alguna razón quisieramos sacar algun cambio que hayamos pasado a la etapa de staged, escribimos el siguiente comando:

```
git restore --staged archivo1.txt
git status
```
##### Mover o renombrar archivos
En nuestra terminal, escribimos:

```
ls
```
y vemos como tenemos nuestro archivo1.txt, asique escribimos:

```
mv archivo1.txt (seguido, el destino que le vamos a dar al archivo, en este caso reemplazamos el nombre por archivo.txt)
```
Luego realizamos la comprobación, escribiendo en nuestra terminal:

```
ls
```
Y podemos ver que ahora solo sale archivo.txt. Escribimos entonces:

```
git status
```
Vemos que ahora solo tenemos dos cambios, el primero fue el de eliminar archivo1.txt, y el segundo, se ha creado un nuevo archivo.txt. Lo que tenemos que hacer ahora es agregar los dos archivos:

```
git add archivo1.txt archivo.txt
git status
```
Y lo que se ve es que nos aparece la accion de renamed: archivo1.txt -> archivo.txt, lo que significa que se ha cambiado el nombre, ahora sí podemos comprometer nuestros cambios:

```
git commit -m "renombrando archivo"
```
Por supuesto que git viene con una herramienta donde nosotros podemos renombrar y agregar a staged nuestros cambios: 

```
git mv archivo.txt archivo1.txt
git status
```
Podemos ver que nuestros cambios estan realizados, asique ahora lo comprometemos:

```
git commit -m "renombrando archivo"
```
##### Ignorando archivos y directorios

- Suponiendo que estamos trabajando en una base de datos, y ese mismo lo vamos a tener instalada en local, los usuarios, las contraseñas, y cualquier otro tipo de acceso va a ser diferente al tipo de producción, en ese caso nosotros queremos tener ese archivo almacenado en nuestra maquina, y no se suba por error a nuestro repositorio. Ya que no queremos que sepan nuestra contraseña, y ademas queremos que sea configurable, de manera que cuando la aplicacion se despliegue a producción, solamente una persona tenga acceso a esas variables de entorno las cuales serviran para configurar la aplicación y que estas se conecten con la base de datos de producción.

#### Vamos a Vs-Code:
- Creamos un nuevo archivo (.env), y dentro del archivo, escribimos:

```
password=123456
user=franco
```
y voy a suponer que mi aplicacion se va a conectar a una base de datos utilizando MySQL.
Volvemos a la terminal y escribimos git status. Vemos que aparece el archivo .env, y yo no quiero, por algun error en el trabajo/proyecto en el que estemos trabajando llegar a comprometer el archivo o comitearlo, y esto sirve para que solamente los desarrolladores tengamos acceso a esas carpetas, para eso, vuelvo a visual studio, y creo un nuevo archivo, que llamamos .gitignore, dentro escribimos los archivos o tambien cuales son las rutas que yo quiero ignorar, en este caso yo le voy a indicar que quiero ignorar el archivo .env, pero tambien queremos indicarle carpetas, por ejemplo, si nosotros estuviesemos trabajando con Node JS, escribiriamos node_modules/.
Volvemos a la terminal, escribimos git status, y vemos que el archivo de .env no aparece, pero si el archivo de .gitignore, vamos a agregar el archivo:

```
git add .gitignore
git commit -m "agregando archivo .gitignore"
```
##### Git Status
- Luego de crear archivo2.txt y escribir dentro de Visual Studio, nos vamos a la terminal, escribimos git status, pero en vez de eso, podemos escribir:

```
git -s
```
- El resultado va a ser parecido a esto:
```
m (en rojo) .gitignore
m (en rojo) .archivo1.txt
?? (en rojo) archivo2.txt
```
- Para ver un cambio, necesitamos agregarlo, entonces:
```
git add .gitignore
git status -s
```
- Y lo que podemos ver es que la M ha cambiado su color a verde, es decir, que este se ha agregado a la etapa de stage.
- Referencia:
```
(M) es para archivos que han sido modificados
(??) No ha sido agregado para que git le dé seguimiento
(A) significa que el archivo ha sido agregado.
```

##### Visualizando cambios
- En el archivo2.txt donde venimos trabajando, escribimos una palabra, en este caso: Felipe. Guardamos y volvemos a la terminal.
Escribimos git status, y vemos que nuestro archivo se encuentra listo para ser agregado a la etapa de stage, pero en lugar de eso, lo que haremos será escribir:
```
git diff
```
- Acá lo que podemos ver es todo el texto de lo que representaría los cambios que estamos dispuestos a agregar, lo que la terminal nos esta queriendo decir, es que se eliminó la linea de (en este caso, y en color rojo) -Ninguna carpeta más, y se agregó (en color verde) .env
- Ahora procedemos a realizar nuestros cambios: 
```
git add archivo2.txt
git diff
```
- Volvemos a ejecutar el comando pero esta vez así:
```
git diff --staged
```
- Es una manera de saber cuales son los cambios que se encuentran en la etapa de stage.
- Nota:
git diff nos va a mostrar todos los cambios que hemos escrito pero que todavia no ha pasado a la etapa de staged, pero si agregamos --staged, nos va a mostrar todos los cambios que se encuentren en la etapa de staged.

##### Historial
- Existe un comando que se escribe:
```
git log
```
- Sirve para ver:
-> el nombre de la persona que realizo un commit.
-> el correo electronico
-> un mensaje de commit

- Pero tambien podemos escribir:
```
git log --oneline
```
- Nos muestra el historial con un pequeño hash el cual sirve como identificador de ese commit, ademas nos va a mostrar el mensaje que nostros agregamos al comienzo, por eso es importante el nombre que nosotros ponemos al comienzo. No solamente para nosotros, sino para otros desarrolladores.

##### Ramas o Branches
- Las ramas pueden identificarse como punteros, para cada uno de los cambios o versiones que queremos armar de nuestros proyectos. 
- Cada rama representa una linea independiente de desarrollo.
- Git cuenta con una rama principal master/main de la cual parten todas las demas ramas que se puedan crear.
- De la manera en que trabajamos, es por default, es decir, de forma lineal.
- Cuando hay mas de un desarrollador trabajando en un mismo proyecto, en este caso, lo que haremos es salirnos del mismo historial para trabajar en nuestro propio código, una vez que hayamos terminado, volveremos a la rama principal, esto se conoce como BRANCH, o rama.

```
git status
git branch (para verificar en que rama nos encontramos)
```
- Para crear una rama, tenemos que escribir el siguiente comando:
```
git checkout -b 'ramab'
```
- Volvemos a escribir git branch, y podemos ver que ahora existen dos ramas: (main) y (ramab).

- Para viajar entre ramas, debemos escribir:
```
git checkout (nombre de la rama)
```
- Para cambiar el nombre de la rama:
```
git branch -m ramab ramita (nombre de la rama actual, y el nombre nuevo)
```
- Algunas empresas utilizan ->features/nombre-de-la-funcionalidad; también hay empresas que colocan el ticket que quieren arreglar, y los tickets tienen el nombre de SS-4515 por ejemplo.

- supongamos que me arrepentí, ya no quiero que exista ramita, hacemos esto:
```
git branch -d ramita
```
(No se puede borrar la rama si estas parada en ella, debes cambiarte primero)

```
git branch (para verificar los cambios)
```
- Podemos ver el historial en el cual nosotros nos encontramos trabajando, para eso, vamos a escribir:
```
git log --oneline
```
- Para mostrar el contenido de nuestro archivo, el siguiente comando es:
```
cat archivo2.txt (cat + nombre del archivo)
```
- Si nosotros estamos trabajando en ramita, y queremos llevar esos cambios a Main, tenemos que tener en cuenta que debemos estar parados en Main. Luego ejecutamos:
```
git merge ramita
```
##### Conectando con nuestro repositorio
- Ingresamos github
- Creamos un nuevo repositorio "nombre del repositorio"
- Copiamos la linea "git remote add origin" y pegamos en la terminal, la ejecutamos.
- Copiamos "git push -a origin main"
