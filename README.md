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
## Ramas, merge y conflictos

## ¿Qué es una rama?

Una rama en Git es una línea independiente de desarrollo. Te permite trabajar en diferentes versiones de tu proyecto simultáneamente, sin interferir con el trabajo en otras ramas. Es como trabajar en diferentes tareas de tu proyecto al mismo tiempo, manteniendo cada tarea separada hasta que estén listas para combinarse.

### ¿Para qué sirven las ramas?

Permiten realizar un desarrollo no lineal y colaborativo.
[![R.png](https://i.postimg.cc/RZJfwqKt/R.png)](https://postimg.cc/21mVDkHj)
## Creando nuestra primera rama

El comando `git Branch` nos permite crear, listar eliminar y renombrar ramas. Para movernos a ella, tendremos que usar el comando `git switch`

```bash
# Creamos la rama
git branch mi-primera-rama

# Cambiamos a la rama mi-primera-rama
git switch mi-primera-rama
`````
Es posible hacer los dos pasos en uno usando el comando:

- `git switch -c mi-primera-rama` Esto creara la rama y te llevara a ella con un solo comando.
- `git checkout -b mi-primera-rama` Esto tambien creara la rama y te llevara a ella con un solo comando.

## Fusionar ramas

Las bifurcaciones de código que hemos creado en forma de ramas tendrán dos destinos: acabar en el olvido para no terminar en ningún lado o ser fusionada en otra rama

Cuando hablamos de fusión nos referimos que los cambios que hemos realizado en la rama se integran en otra rama, de forma que el código que habíamos generado en la nueva rama se asimila en otra.

### Fusinando ramas

Empleamos el comando `git merge` para incorporar los cambios de una rama a la rama en la que nos encontramos en ese momento.
[![R.jpg](https://i.postimg.cc/tJ0gmTPM/R.jpg)](https://postimg.cc/zbj5yqxC)
```bash
# Abrir el editor antes de hacer el commit
git merge --edit

# Evitar commit automaticamente
git merge --no-commit
`````
Al ejecutar el comando `git merge`, se creara un nuevo commit que incluye todos los cambios de la rama origen a la rama en la que nos encontramos ahora.

## Eliminar ramas ¿por qué?

Por que es una buena practica, además que las ramas tiene un propósito único y corto de periodo.

despues d efusionar una rama en otra, es posible querer eliminarla para no dejarla suelta. Para ello puedes usar el comando `git branch` con el parametro `--delete` o, de forma corta `-d`
```bash
# borramos la rama llamada "mi-primera-rama"
git branch --delete mi-primera-rama
`````
Si hay el caso de querer borrar una rama que no ha sido fusionada previamente, se debe usar el parámetro `-D` . Este parámetro le indica a Git que borrara la rama sin importar si ha sido fusionada o no.
```bash
#borramos la rama llamada "mi-primera-rama"
git branch -D mi-primera-rama
`````
## Conflictos en Git

¿Qué pasa si al querer fusionar dos ramas, la de destino ha realizado cambios en las mismas líneas de un fichero que los que queremos fusionar?

Generan conflictos

### Resolviendo conflictos

Al resolver, deberemos decidir entre:

- Nos quedamos con los cambios de la *rama main.*
- Nos quedamos con los cambios que vienen de la *rama changes*.
- Modificamos los cambios para hacer una fusión personalizada.
[![Captura-de-pantalla-2024-05-11-185126.png](https://i.postimg.cc/s26mSFSX/Captura-de-pantalla-2024-05-11-185126.png)](https://postimg.cc/cK3fybFy)
### Comandos

En el video de la clase 2 se mencionaron los siguientes comandos de Git:

- `git Branch`: Permite crear, listar, eliminar y renombrar ramas.
    - `git branch <nombre de rama>`
    - `git branch -a`
    - `git brach -d <nombre de rama>`
- `git switch`: Se utiliza para cambiar de rama.
    - `git switch <nombre de rama>`
- `git checkout`: También se utiliza para cambiar de rama.
    - `git checkout <nombre de rama>`
- `git merge`: Para incorporar los cambios de una rama a la rama en la que nos encontramos.
    - `git merge <nombre de rama>`
    - `git merge <nombre de rama> --no-f`
- `git push`: Para enviar los cambios confirmados a un repositorio remoto.
- `git log`: Para ver el historial de confirmaciones.
- `git log --oneline`: Para ver el historial de confirmaciones de forma resumida.
- `git log --graph`: Para visualizar el historial de confirmaciones en forma de grafo.
- `git log --graph --oneline`: Para visualizar el historial de confirmaciones en forma de grafo de una línea.

# Clase 3
# Git y Github

## Enlazar un repositorio local con un repositorio remoto

como alias podemos usar cualquier nombre, por defecto es **origin** para indicar que el repositorio remoto que estamos sincronizando es el principal.

Github utiliza las direcciones SSH por defecto. Por ello debemos utilizar estas, para añadir un repositorio local, se ejecuta el siguiente comando:

`git Remote add origin <URL>`

### Generar Key SSH

- Listamos las llaves SSH que ya tenemos
    - `ls -al ~/.ssh`
- Crear key SSH
    - ssh-keygen -t rsa -b 4096 -C “tu.email@gmail.com”
    - press enter
    - passphrase
- Poner en marcha la key SSH
    - `eval "$(ssh-agent -s)"`
- Añadir key SSH
    - `ssh-add ~/.ssh/id_rsa`
- Copia en portapapeles
    - `clip < ~/.ssh/id_rsa.pub`
- Pegar en la sección “key”
    - **https://github.com/settings/ssh/new**

## Como forzar un push

El comando **`git push -f`** (o **`git push --force`**) se utiliza para forzar el empuje de tus cambios locales hacia un repositorio remoto, incluso si esto resulta en la pérdida de commits o la reescritura del historial de la rama remota.

- **`git push -f origin main`**
## Clonando repositorio

Para clonar un repositorio remoto necesitamos saber su dirección, que puede ser una dirección HTTPS o SSH.
[![Captura-de-pantalla-2024-05-11-194341.png](https://i.postimg.cc/FRNBjf9x/Captura-de-pantalla-2024-05-11-194341.png)](https://postimg.cc/p9cCvL59)

Para clonar un repositorio remoto con la dirección SSH

`git clone git@github.com:midudev/libro-javascript.git` 

Para clonar un repositorio remoto con la dirección HTTPS

`git clone https://github.com/midudev/libro-javascript.git` 

## Escribiendo en el repositorio remoto

Para enviar *commits* al repositorio remoto *origin* y la rama *main,* deberíamos ejecutar lo siguiente:

`git push origin oigin main` 

subirá los cambios del repositorio local al repositorio remoto con alias origin a la rama main
## Creando una rama remota

```bash
#Creando una rama en el repositorio local
git switch -c website

#Enviar la rama a nuestro repositorio remoto para ello usamos git push:
#git push <alias-repositorio> <rama>
git push origin website
```

Ahora podemos empezara crear commits en nuestro repositorio local y enviarlos al repositorio remoto de la rama que hemos creado
## Eliminar ramas de mi repositorio local

El comando **`git remote prune origin`** se utiliza para eliminar referencias locales a ramas remotas que ya no existen en el repositorio remoto **`origin`**.

```bash
#ejecutamos el comando
git remote prune origin
```

### Comandos

Se mencionaron varios comandos de Git en la clase3:

1. `git remote add origin <URL>`: Para enlazar un repositorio remoto con un repositorio local.
2. `git push origin <nombre_rama>`: Para sincronizar los cambios del repositorio local con el repositorio remoto.
3. `git branch -d <nombre_rama>`: Para eliminar una rama local.
    1. `git branch -a`: Extiende la salida para incluir todas las ramas, tanto locales como remotas. Esto incluye las ramas locales y todas las ramas remotas que tu repositorio local conoce, aunque estas últimas no estén en tu sistema local.
4. `git fetch`: Para actualizar la información entre el repositorio remoto y el repositorio local.
5. `git switch <nombre_rama>`: Para cambiar a una rama específica.
6. `git tag <nombre_tag>`: Para etiquetar ciertos commits importantes.
7. `git remote remove <nombre_alias>`: Para eliminar un repositorio remoto conectado.
8. **`git remote prune origin`** Se utiliza para eliminar referencias locales a ramas remotas que ya no existen en el repositorio remoto.
9. `git clone <URL_Repositorio>`: Para clonar un repositorio remoto
10. **`git remote -v`**: Se utiliza para mostrar las URL de los repositorios remotos configurados en tu repositorio local