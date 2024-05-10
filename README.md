# Clase 1

# Introducción a Git

## ¿Qué es un control de verificaciones?

Un control de verificaciones es un sistema que registra cada cambio que realiza en el código fuente de un proyecto.
Esto te permite tener un historial de todos los cambios producidos en sus ficheros, saber quien lo hizo y cuando.

## ¿Por que es importante un control de versiones?

- Rendimiento, solo se guarda lo necesario
- Seguridad, conserva toda acción
- Flexibilidad, no es necesario un desarrollo lineal
El control de versiones es crucial para el desarrollo de software, ya que permite guardar cambios de forma segura y flexible, conservando todo el historial de acciones realizadas.

# ¿Qué es Git?

Git al ser un sistema distribuido, aloja una copia completa del repositorio en cada maquina local que esta trabajando en el código. Además, puedes tener uno o varios repositorios remotas para sincronizarlos.
[![imagen.jpg](https://i.postimg.cc/6QX2nn3s/imagen.jpg)](https://postimg.cc/yDL8zJcn)

## Iniciar un proyecto en Git

Para crear un repositorio Local se puede usar el comando `git init` e indicar el nombre del proyecto. Creara una carpeta configurada y vacia con el nombre que le has indicado.
- `git init nuevo-proyecto`
- `cd nuevo-proyecto`

Para repositorios ya existentes, es necesario usar el comando `git init` dentro de la raíz del directorio del proyecto.
- `cd <directorio del proyecto>`
- `git init`
# States y commits

## Los 3 estados de Git

[![states-git.png](https://i.postimg.cc/85N68H3d/states-git.png)](https://postimg.cc/PLVxYmdN)

### Modified

El archivo ha sido creado, eliminado o contiene cambios que no han sido marcados como confirmados.

- `git status`: Para ver el estado de los archivos en el repositorio.

### Staged

El archivo ha sido marcado como preparado para ser confirmado en el repositorio local.

- `git add <archivo>`: Para pasar un archivo al área de staging.

### Commited

El archivo se encuentra grabado en el repositorio local. Esta acción recibe el nombre de *commit*

- `git commit -m "mensaje"`: Para realizar un commit con un mensaje descriptivo.

Un commit en Git es como guardar una partida en un videojuego, permitiendo restaurar cambios anteriores. Es fundamental para registrar cambios en un repositorio y se realiza con 'git commit'.
El mensaje de un commit es crucial para documentar los cambios realizados y se puede realizar a través de 'git commit' en Git.

- `git restore --staged <archivo>` Se usa para quitar los cambios que has agregado al área de preparación, pero manteniendo esos cambios en tu directorio de trabajo.

## ¿Qué es un commit?

Es como guardar partida en un videojuego, tienes tu punto de restauración si te equivocas.

### ¿Cómo hago un commit?

Para guardar los cambios en el área de staging, puedes hacer un commit con el siguiente comando

- `git commit`

Creará un nuevo commit en tu repositorio y añadirá una referencia al commit en la rama en la que estas trabajando.
Para añadir directamente un mensaje sin abrir el editor, se usa el parámetro `-m` o `--message:` 

- `git commit -m "mensaje"`

El mensaje especifico se usará como titulo del commit para describir los cambios realizados.

### Hacer commits con múltiples líneas de mensajes

`git commit -m "mensaje" -m "mas mensaje"`  

- El primer  **`-m "mensaje"`** se usa para proporcionar el mensaje principal del commit.
- El segundo  **`-m "mas mensaje"`** se usa para proporcionar un mensaje adicional, que puede ser una explicación más detallada del cambio realizado.

### git commit —ammend

Se usa para modificar el commit más reciente en tu historial de Git, para corregir el mensaje del commit o agregar cambios olvidados al último commit sin crear uno nuevo.

- `git commit --ammend - m "nuevo mensaje"`

## ¿Qué es el HEAD?

 "HEAD" en Git es simplemente un puntero que apunta al commit actual en el que te encuentras. Es como tu posición actual en la historia de tu proyecto. "HEAD" es un punto de referencia que indica dónde te encuentras en la historia de tu proyecto en cualquier momento dado.


### Comandos mencionados

Comandos de Git de la clase 1 varios comandos de Git, entre ellos:

- `git init`: Para inicializar un proyecto en Git.
- `git status`: Para ver el estado de los archivos en el repositorio.
- `git add <archivo>`: Para pasar un archivo al área de staging.
- `git commit -m "mensaje"`: Para realizar un commit con un mensaje descriptivo.
- `git log`: Para ver el historial de commits realizados.
- `git config --global user.name "Your name"` Configurar nombre de usuario
- `git config --global user.email "email@example.com"` Configurar un email
- `git restore --staged <archivo>` Se usa para quitar los cambios que has agregado al área de preparación, pero manteniendo esos cambios en tu directorio de trabajo.


# Clase 2
# Ramas, merge y conflictos

## ¿Qué es una rama?

Una rama en Git es una línea independiente de desarrollo. Te permite trabajar en diferentes versiones de tu proyecto simultáneamente, sin interferir con el trabajo en otras ramas. Es como trabajar en diferentes tareas de tu proyecto al mismo tiempo, manteniendo cada tarea separada hasta que estén listas para combinarse.

### ¿Para qué sirven las ramas?

Permiten realizar un desarrollo no lineal y colaborativo.
[![R.png](https://i.postimg.cc/RZJfwqKt/R.png)](https://postimg.cc/21mVDkHj)
## Creando nuestra primera rama

El comando `git Branch` nos permite crear, listar eliminar y renombrar ramas. Para movernos a ella, tendremos que usar el comando `git switch`

```git
# Creamos la rama
git branch mi-primera-rama

# Cambiamos a la rama mi-primera-rama
git switch mi-primera-rama
`````
