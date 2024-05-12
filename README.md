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

# Clase 4
# Push, Pull & Pull request

## ¿Cuál es la diferencia entre git push y git pull?

### git push

Nos sirve para **empujar** cualquier cambio o modificación del repositorio local al repositorio remoto

- **`git push`**: Este comando se utiliza para subir los cambios locales a un repositorio remoto.
    - **`git push --all`**
- **`git push --force`** se utiliza para forzar el empuje de tus cambios locales hacia el repositorio remoto, incluso si esto resulta en la pérdida de commits o en la reescritura del historial de la rama remota.
    - **`git push -f`**
- **`git push --set-upstream <remoto> <rama>`**. Este comando te permite establecer la relación de seguimiento entre una rama local y una rama remota.
- **`git push --delete <remoto> <rama>`** Se utiliza para eliminar una rama remota en un repositorio Git.
    - **`git push -d origin <rama>`**
- **`git push -u origin <rama>`** se utiliza para enviar tus cambios locales a una rama específica en el repositorio remoto llamado "origin" y al mismo tiempo establecer esa rama remota como el upstream (seguimiento) de la rama local actual.
- **`git push origin <remoto> <rama_local>:<rama_remota>`**: Se utiliza para subir los cambios de una rama específica al repositorio remoto.

### git pull

Nos sirve para **jalar** o **descargar** los cambios o modificaciones del repositorio remoto al repositorio local.

- **`git pull`**: Se utiliza para traer los cambios del repositorio remoto al repositorio local.
- **`git pull origin <remoto> <rama>`**: Trae los cambios de una rama específica del repositorio remoto a la rama local.
- **`git pull --all`**  Se utiliza para recuperar todas las ramas remotas y fusionarlas en las ramas locales correspondientes. Esto es útil cuando se quiere asegurar que se tienen todas las actualizaciones de todas las ramas remotas en el repositorio local.
- **`git pull --set-upstream origin <rama>`** Realiza dos acciones:
    1. Establece la rama remota **`origin/<rama>`** como el "upstream" de la rama local actual.
    2. Realiza un pull para traer los cambios de la rama remota especificada (**`origin/<rama>`**) y fusionarlos automáticamente con la rama local actual.
- **`git pull origin <rama1> <rama2> <ramaN>`** Realiza un pull de múltiples ramas desde el repositorio remoto llamado "origin" y las fusiona automáticamente con las ramas locales correspondientes.

## ¿Qué es una Pull Request?

Una Pull Request o **PR**, es una petición de cambios que se envía al repositorio.

### ¿Cómo se hace una **PR**?

Tenemos que subir nuestra rama con **`git push`** y hay dos maneras diferentes:

1. La rama la subiste recientemente y aparece la opción en GitHub

    `>Code`

2. Irnos al apartado Pull Request

## Hacer una buena PR

1. **Enfoca tu código en una sola cosa**, es mucho mas fácil revisar y aceptar una Pull Request  que hace una sola cosa a revisar una Pull Request que aprovecha a hacer muchas cosas.
2. **Explica tu Pull Request**, y su una imagen vale mas que mil palabras. ¿Qué puede valer un GIF o un video mostrando la funcionalidad?

## Revisar una PR

1. Proporciona siempre feedback positivo
2. concreción y claridad
3. **Entiende el contexto**, es posible que a veces tengamos que poner paños calientes o parches a nuestro código y que, pese a no ser el más bonito, sí que cumpla su cometido.

# Clase 5
# GitFlow

## Que es GitFlow?

Es el flujode trabajo mas antiguo, utiliza las ramas:
1.- main (o master): contener el codigo de produccion.
2.- develop: Código de preproducción que todavía tienen que ser probadas y validadas.
[![5e7444cb6b-1458190973507-jpg.png](https://i.postimg.cc/8zJg1vFj/5e7444cb6b-1458190973507-jpg.png)](https://postimg.cc/87S04jmS)
# Git Flow

1. Feature: caracteristicas nuevas para el proyecto
2. Release: Cambios de ultimo momento
3. Hotfix: Parches o arreglar bugs pequeños

https://github.com/OpherV/gitflow4idea/branches/all

Rama main y cualquier otra rama que quiera ser integrada por medio de una Pull Request

[![Captura-de-pantalla-2024-05-07-212235.png](https://i.postimg.cc/LXyxYywR/Captura-de-pantalla-2024-05-07-212235.png)](https://postimg.cc/JDkNSQRd)

## Trunk Based Development

Solo la *rama main* y ramas auxiliares efímeras que quiera ser integrada por medio de una Pull Request.
Es util si contamos con un buen Sistema CI/CD

[![Captura-de-pantalla-2024-05-07-212529.png](https://i.postimg.cc/dtCgpYgy/Captura-de-pantalla-2024-05-07-212529.png)](https://postimg.cc/RNMPJjSS)

## Ship / Show / Ask

1. Ship: Se fusiona en la rama principal sin revisión
2. Show: Abre una petición de cambios para que sean revisados por CI pero se fusiona inmediatamente
3. Ask: Abre un PR para discutir los cambios antes de fusionarlos

[![Captura-de-pantalla-2024-05-11-221916.png](https://i.postimg.cc/J0kYfNYL/Captura-de-pantalla-2024-05-11-221916.png)](https://postimg.cc/BPJCDKGY)

## Las reglas de Ship / Show / Ask

1. Tenemos un buen sistema de CI/CD
2. Confiamos en el equipo y existen buenas practicas de desarrollo. Pair programming, mob programming, seniority… y, sobre todo, existe responsabilidad. La persona se responsabiliza de decidir la categoría de su cambio.
3. Las revisiones de código no son requerimientos.
4. Las ramas son lo mas pequeñas posibles, tienen un tiempo de vida corto y siempre salen directamente desde la rama principal.
5. EL equipo ha sabido lidiar con el ego individual, las personas confían en el resto del equipo y las pruebas automáticas pasan.

### Show

https://github.com/CodeMasterChefs/Backend-Ruta_del_Programador/pull/3

### Ask

[https://github.com/CodeMasterChefs/Bakend-Ruta_delProgramador/pull/34/commits/1392ca4147fb4d461681f065b90958f09eccb759](https://github.com/CodeMasterChefs/Bakend-Ruta)

# Clase 6
# Buenas prácticas en Git

## ¿Para qué sirven las buenas prácticas?

- Es un estándar manejado en la mayoría de equipos de desarrollo.
- Resolver conflictos o problemas durante el desarrollo es mas fácil
- Tu historial de commits es mas legible

## 1. ¿Cada cuánto debería hacer un commit?

### **A menudo**

Es mejor hacer commits pequeños, agrupando pequeñas mejoras o acciones, que un commit con todo lo que se quiere hacer.

Hacer commit a menudo no significa que debas hacer commits sin sentido.

## Escribir buenos commits

- Usar el verbo imperativo (Add, Change, Fix, Remove)
- No uses punto final ni puntos suspensivos en tus mensajes (a lo más usa la coma)
- Usa como máximo 50 caracteres para tu mensaje de commit
- Añade todo el contexto que se necesario en el cuerpo del commit (con reglas de puntuación)
- Considera usar utilidades para hacer commit
- Usa un prefijo para tus commits para hacerlos mas semánticos.

## Prefijos para commits

- **feat: Para una nueva característica para el usuario.**
- **fix**: para un bug que afecta al usuario.
- **perf**: para cambios que mejoran el rendimiento del sitio
- **build**: para cambios que mejoran el rendimiento del sitio.
- **ci**: para cambios en la integración continua.
- **docs**: para cambios en la documentación.
- **refactor**: para refactorización del código como cambios de nombre de variables o funciones.
- **style**: para cambios de formato, tabulaciones, espacios o puntos y coma, etc; no afectan al usuario.
- **test**: para test o refactorización de uno ya existente.

[![Captura-de-pantalla-2024-05-11-230400.png](https://i.postimg.cc/0jL8d0FK/Captura-de-pantalla-2024-05-11-230400.png)](https://postimg.cc/JH5VRZ1R)
## Escribir un buen nombre de rama

- Sé consistente al nombrar tus ramas
- Usa el nombre de la accion que se realiza en la rama

[![Captura-de-pantalla-2024-05-11-230606.png](https://i.postimg.cc/GpyhtNfw/Captura-de-pantalla-2024-05-11-230606.png)](https://postimg.cc/kV7dhj9f)

- Usa los IDs de JIRA o el sistema de tickets que uses

# Clase 7
# Deshacer cambios

## ¿En qué casos deshacer cambios?

- Dejo de funcionar el proyecto.
- Queremos recuperar una parte del código que eliminamos.
- Queremos recuperar archivos que eliminamos.

## Comandos destructivos y no destructivos

Los comandos destructivos afectan el historial de commits realizado, sin embargo los comandos no destructivos trabajan en base al historial sin afectarlo.

### git reset

posee 2 opciones

- **soft**: Mantiene los cambios que ocurrieron antes de hacer commit desde donde apuntaba.
    - **`git reset --soft`**. Este comando se utiliza para deshacer cambios en el área de preparación (index) mientras se mantienen los cambios en el directorio de trabajo.
    - **`git reset --soft HEAD~<N>`** Deshace los últimos N commits sin borrar los cambios en tus archivos.
    - **`git reset --soft <SHA>`** Deshace cambios hasta un commit específico sin eliminar los cambios en tus archivos, dejándolos listos para ser confirmados nuevamente.
- **hard**: Descartar los cambios
    - **`git reset --hard`** se utiliza para deshacer los cambios en el directorio de trabajo y en el área de preparación (index), restableciendo el árbol de trabajo al estado del último commit. Esto significa que todos los cambios que no hayan sido confirmados se perderán permanentemente.
    - **`git reset --hard HEAD~<N>`** Deshace los últimos N commits y borra los cambios en tus archivos, restaurando el árbol de trabajo al estado en el que estaba antes de esos commits.
    - **`git reset --hard <SHA>`**Borras la historia de tu repositorio hasta un punto específico, como si usaras un borrador para retroceder y eliminar todo lo que ocurrió después de ese punto.

### git revert

Revierte los cambios que un commit introdujo, y crea un nuevo commit con los cambios revertidos.

- **`git revert <hash_del_commit>`** Se utiliza para deshacer cambios específicos realizados en un commit anterior creando un nuevo commit que revierte esos cambios. Es seguro de usar en repositorios compartidos porque no modifica la historia existente; en su lugar, crea un nuevo commit que deshace los cambios.
    - `git revert HEAD~<N>`Deshace los últimos N commits de manera segura, creando nuevos commits que revierten los cambios introducidos en esos commits específicos.
    - `git revert <SHA>` Deshace los cambios introducidos en un commit específico identificado por el hash `<SHA>`, creando un nuevo commit que revierte esos cambios.

### git checkout

Nos permite recuperar código especifico de commits. Te permite cambiar entre diferentes ramas, moverte hacia atrás y hacia adelante en la historia del repositorio, y deshacer cambios en tus archivos.

- `git checkout HEAD~<N>`Te permite volver al estado del proyecto en un commit específico anterior a los últimos N commits.
- `git checkout <SHA>`Te permite moverte a un commit específico identificado por su hash `<SHA>`.

# Clase 8

# Hooks, Alias y Trucos de Git

## ¿Qué es un Hook?

- Un hook, o un punto de enganche, es la posibilidad de ejecutar una acción o script cada vez que ocurre un evento determinado de Git.
- Hooks del lado del cliente
- Hooks del lado del servidor

## Hooks del lado del cliente

Sólo afectan al repositorio local que los contiene.

- **pre-commit**
    - Podrías comprobar si se esta intentando hacer un commit de demasiados archivos.
    - Puede ser un buen sitio para ejecutar el linter sobre los archivos que han sido modificados.
- **prepare-commit-msg**
    - Para modificar el mensaje del commit o añadir cualquier información extra.
- **commit-msg**
    - Es el sitio perfecto para hacer todas las comprobaciones pertinentes del mensaje
- **post-commit**
    - Su uso principal es la de notificar por Slack
- **pre-push**
    - Para ejecutar una bateria de test
- **post-checkout y post-merge**
    - Permite limpiar el directorio de trabajo, tras realizar un checkout, o el de limpiar las ramas que ya no se usan tras realizar un merge.

## Hooks del lado del servidor

- **pre-receive**
    - Para comprobar que los commits que se quiere guardar estan bien formados.
    - Verificar que el usuario que intenta grabar los commits tiene los permisos necesarios para hacerlo
- **update**
    - Puedes evitar de una forma granular cada actualizacion
- **post-receive**
    - Enviar un correo a todos los usuarios del repositorio que se han grabado nuevos cambios en el repositorio remoto
    - Reflejar un una UI las nuevas referencias, ramas o commits disponibles.

## Creando un hook

Para crear un propio hook solo se tiene que crear un archivo nuevo nombre-del-hook en la carpeta .git/hooks y en el poner el código que quieras que se ejecute

Puedes usar todo tipo de interpretes de lenguaje de programación como bash, node, python, perl, etc.

## ¿Qué es un Alias?

- Los alias permiten definir una serie de comandos que pueden ser usados en lugar de los nombre completos.

[![Captura-de-pantalla-2024-05-11-235015.png](https://i.postimg.cc/B64FFyVy/Captura-de-pantalla-2024-05-11-235015.png)](https://postimg.cc/LqQhKyRB)

## Creando mi primer alias

Git te permite crear tu propio alias facilmente para comandos que usas habitualmente en tu proyecto con este sistema de control de versiones.

`git  config --global alias.[nombre-del-alias] "comando a ejecutar"`