## Git y Github

**¿Que es git?**

Git es un software para llevar un control de versiones de nuestros proyectos desarrollado por Linus Tolvards. 

Fue desarrollado pensando en la eficiencia y la confiabilidad del mantenimiento de versiones de aplicaciones cuando éstas tienen un gran número de archivos de código fuente.

**¿Que ventajas nos ofrece?**

Pues la principal ventaja es poder llevar un historico de los cambios (commits) en el codigo fuente de nuestro proyecto ya sea en los cambios de las diferentes versiones de nuestros software. 

Así como volver a versiones previas de nuestro codigo fuente o detectar los cambios que se han hecho en cada versión en caso de que una versión cuente con un bug poder identificarlo más rapido.

**¿Y que es github?**

Github no es más que una red social basada en git, es la más utilizada pero no es la unica existen varias como Gitlab, bitbucket y otros servicios para Git.

La gran ventaja de Github es que hay miles de librerias para todo tipo de lenguajes (Java, PHP, Swift, etc) o proyectos de ejemplo o ya terminados open source que podemos reutilizar para nuestros propios proyectos.

## Empezando con Git desde consola

Lo primero que hay que tener en cuenta es que cuando se trabaja con Git se almacena de forma local una copia (commits) y otra remota en el servidor que nosotros le indiquemos.

**1. Inizializar un proyecto**

```bash
git init

....
Initialized empty Git repository in /Users/alesanderlopezgil/NetBeansProjects/AplicacionActividades/.git/
```

Este comando se debe ejecutar por primera vez en la carpeta raiz de nuestro proyecto para que genere los ficheros necesarios y la carpeta **.git**.

**.gitignore**

Siempre dentro de nuestro proyecto tendremos carpetas y ficheros que no queramos que se suban a nuestro proyecto ya pueden ser librerias que pueden ser redundantes o ficheros con contraseñas entonces dentro de este fichero debemos indicar su nombre, por ejemplo en un proyecto php.
```bash
/vendor/*
/config/app.php
```

**2. Antes de nuestro primer commit**

Siempre dentro de un proyecto git esta el fichero README.md que se utiliza para la documentación y es mostrado al entrar a un repositorio. Este fichero tiene la estructura en Markdown. 

Un ejemplo de fichero.

```bash
# Proyecto asignatura: Entorno de desarrollo

Proyecto escrito en Java por los alumnos del Roque Amagro de Desarrollo de aplicaciones multiplataforma.

##### REQUISITOS FUNCIONALES:

**1. Usuario se tiene que registrar para operar en la app (alta)**

- Alta, rellenar y editar perfil individual
- Baja usuarios (actividad, grupo o aplicación)
- Consulta actividades
- Alta-baja actividades

**2. Usuario Presidente propone actividades**

- Funciona como gestor de la actividad/grupo
- Crear actividades/grupos
- Crea perfil de participantes
- Veta usuarios
- Guarda contenido multimedia
- Suspender actividad/grupo

**3. El sistema propone actividades de acuerdo al perfil**

- Necesita de formularios para crear perfiles usuarios y de actividad
- Compara perfil, filtra y selecciona posibles usuarios para una actividad
- Listar actividades y usuarios

**4. Administrador**

- Gestión de usuarios, grupos y actividades (elimina usuarios)
- Backups de la base de datos
- Realizar estadísticas


##### REQUISITOS NO FUNCIONALES:
- netbeans
- mysql
- github
- hibernate
- acceso remoto
```

**3. Nuestro primer commit.

Una vez estamos dentro de la carpeta de nuestro proyecto podemos listar los ficheros que no han sido commiteados con el siguiente commando.
```bash
git status 

...
On branch master

Initial commit

Untracked files:
  (use "git add <file>..." to include in what will be committed)

    README.md
    build.xml
    manifest.mf
    nbproject/
    src/
```

Para añadir nuestros ficheros al siguiente commit podemos indicarlos uno a uno o añadirlos todos con el siguiente comando.

```bash
git add --all
```

Ahora tenemos listo nuestros ficheros para generar nuestro primer commit.

```bash
git commit -m "Primer commit, nuestro proyecto se ha generado por primera vez y se le ha añadido el README.md"

...
 9 files changed, 1657 insertions(+)
 create mode 100644 README.md
 create mode 100644 build.xml
 create mode 100644 manifest.mf
 create mode 100644 nbproject/build-impl.xml
 create mode 100644 nbproject/genfiles.properties
 create mode 100644 nbproject/private/private.properties
 create mode 100644 nbproject/project.properties
 create mode 100644 nbproject/project.xml
 create mode 100644 src/aplicacionactividades/AplicacionActividades.java
```

Ahora podemos comprobar que no tenemos ficheros por modificar desde nuestro ultimo cambio.

```bash
git status

...
On branch master
nothing to commit, working tree clean
```

**4. Repositorios remotos**

Ahora que hemos hecho nuestro primer commit tenemos un repositorio local en nuestro equipo pero lo interesante sería tener también una copia reciente en otro repositorio remoto para en caso de que nuestro disco duro se borre o la carpeta se borre poder recuperarlo y que nuestros demás compañeros tengan también los ultimos cambios que hemos realizado en el proyecto entonces llega el comando push (empujar)

```bash
git push origin master

...
fatal: 'origin' does not appear to be a git repository
fatal: Could not read from remote repository.

Please make sure you have the correct access rights
and the repository exists.
```

**Ha fallado ¿Porque?**

Porque antes de hacer el push no hemos indicado cual es nuestro repositorio remoto, primero debemos crear un repositorio en un servicio como github por ejemplo, ya tengo uno creado y la ruta es la siguiente ***https://github.com/alesanderlopez/gitcurso*** y nuestro usuario ***alesanderlopez*** y solo falta indicarlo con el siguiente comando.

```bash
## Si queremos usar https
git remote set-url origin https://github.com/alesanderlopez/gitcurso.git

## Si queremos usar ssh
git remote set-url origin https://github.com/alesanderlopez/gitcurso.git
```

Ahora si podemos hacer push que tenemos el repositorio remoto añadido.

```bash
git push origin master

...
Username for 'https://github.com': alesanderlopez
Password for 'https://alesanderlopez@github.com':

Counting objects: 15, done.
Delta compression using up to 8 threads.
Compressing objects: 100% (13/13), done.
Writing objects: 100% (15/15), 13.84 KiB | 0 bytes/s, done.
Total 15 (delta 0), reused 0 (delta 0)
To https://github.com/alesanderlopez/gitcurso.git
 + d7b2e59...7d5c4c6 master -> master (forced update)
```

Ahora vamos a nuestro repositorio remoto y veremos los ficheros.

> https://github.com/alesanderlopez/gitcurso

**5. Usar nuestro proyecto publico en otro ordenador**

Una de las grandes ventajas de github es que te puedes descargar un proyecto o libreria publicos en tu equipo en cuestión de segundos. 

¿Como? Pues gracias a la función clone vamos a hacer un ejemplo haciendo un clone de nuestro proyecto en otro directorio simulando que es otro equipo, tan solo necesitamos saber la ruta del repositorio.

> La ruta de nuestro repositorio es https://github.com/alesanderlopez/gitcurso.git

```bash
git clone https://github.com/alesanderlopez/gitcurso.git

...
Cloning into 'gitcurso'...
remote: Counting objects: 15, done.
remote: Compressing objects: 100% (13/13), done.
remote: Total 15 (delta 0), reused 15 (delta 0), pack-reused 0
Unpacking objects: 100% (15/15), done.

$ ls gitcurso
README.md   build.xml   manifest.mf nbproject   src
```

**6. Bajando los nuevos cambios**

Simulamos ahora que en nuestro nuevo ordenador hemos hecho cambios y los hemos commiteados y subidos al repositorio con los siguientes comandos.
```bash
$$ git status
On branch master
Your branch is up-to-date with 'origin/master'.
Untracked files:
  (use "git add <file>..." to include in what will be committed)

    src/aplicacionactividades/NuevaClasePrueba.java

nothing added to commit but untracked files present (use "git add" to track)

$$ git add --all

$$ git commit -m "Añadida la clase NuevaClasePrueba"
[master 9e41f2c] Añadida la clase NuevaClasePrueba
 Committer: Alesander López Gil <alesanderlopezgil@MPro.local>
Your name and email address were configured automatically based
on your username and hostname.

 1 file changed, 14 insertions(+)
 create mode 100644 src/aplicacionactividades/NuevaClasePrueba.java

$$ git push origin master
Counting objects: 5, done.
Delta compression using up to 8 threads.
Compressing objects: 100% (4/4), done.
Writing objects: 100% (5/5), 646 bytes | 0 bytes/s, done.
Total 5 (delta 1), reused 0 (delta 0)
remote: Resolving deltas: 100% (1/1), completed with 1 local object.
To https://github.com/alesanderlopez/gitcurso.git
   7d5c4c6..9e41f2c  master -> master

```

Ahora en nuestro ordenador previo no tenemos los nuevos cambios que hemos hecho en el otro para obtenerlos solo basta con hacer un **pull** (arrastrar)

```bash
$$ ll src/aplicacionactividades/
AplicacionActividades.java

$$ git pull origin master
From https://github.com/alesanderlopez/gitcurso
 * branch            master     -> FETCH_HEAD
Updating 7d5c4c6..9e41f2c
Fast-forward
 src/aplicacionactividades/NuevaClasePrueba.java | 14 ++++++++++++++
 1 file changed, 14 insertions(+)
 create mode 100644 src/aplicacionactividades/NuevaClasePrueba.java

$$ ll src/aplicacionactividades/
AplicacionActividades.java 
NuevaClasePrueba.java 

(Vemos como ahora esta la nueva clase)
```

**Fucionando cambios**

En ocasiones hay en los dos ordenadores cambios imaginamos que hemos cambios y en la rama remota hay cambios que no tenemos todavía.

Pues cuando hagamos push puede fallarnos, por lo que siempre antes de hacer un push debemos hacer un pull para tener siempre los ultimos cambios antes de subir los nuestros.

**Las ramas**

Las ramas en git se utilizan para poder dibir el desarrollo de los proyectos, por ejemplo en la rama master (origin master) va el flujo de producción y lo adecuado es programar en la rama dev y cuando nuestros cambios sean estables fucionarlos en la rama master.

Este ultimo termino aveces es complejo de entender y de utilizar ya que las fusiones entre ramas no suelen ser limpias y al fusionar hay que hacer cambios en los ficheros.

Por ejemplo si queremos traer los cambios de la rama dev a la master se utilizan los siguientes comandos.
```bash
git checkout master
git merge dev
```

El checkout se utiliza para saltar entre las distintas ramas y el merge se utiliza para fusionarla.

** Para crear ramas**
```bash
git checkout -b nuevarama
```

**Volver al ultimo commit**

Si por accidente hemos hecho alguna cagada despues de nuestro ultimo commit o pull y queremos restablecer todo solo basta con hacer un:
```bash
git checkout .
```

Este comando nos vuelve el proyecto al ultimo commit.

Y para ir a un commit anterior:
```bash
git checkout IDCOMMIT
```
