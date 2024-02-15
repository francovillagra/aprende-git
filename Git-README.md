# Aprende GIT :tw-1f4da:

<p>
Algunos de los temas aprendidos:
</p>

- Configuración inicial.
- Comandos básicos de BASH.
- Agregando cambios a stage.
- Commit en Git.
- Eliminando archivos de nuestro repositorio.
- Volviendo del Staged y descartar cambios.
- Mover o renombrar archivos.
- Ignorando archivos y directorios.
- Git status.
- Visualizando cambios.
- Viendo el historial.
- Ramas en Git o Branches.
- Conectando con Git Hub.

**Entre otros comandos**

## Comandos en acción :tw-1f680:
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
:tw-1f50e: Para indagar aún más en git, usamos:
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

```
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
```

:tw-1f4e2: Cada vez que se modifica el texto dentro del editor de códigos, se escribe en la terminal:
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
