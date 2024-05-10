# Repositorio1
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

### Modified

El archivo ha sido creado, eliminado o contiene cambios que no han sido marcados como confirmados.


### Comandos mencionados

Comandos de Git de la clase 1 varios comandos de Git, entre ellos:

- `git init`: Para inicializar un proyecto en Git.
- `git status`: Para ver el estado de los archivos en el repositorio.
- `git add <archivo>`: Para pasar un archivo al área de staging.
- `git commit -m "mensaje"`: Para realizar un commit con un mensaje descriptivo.
- `git log`: Para ver el historial de commits realizados.
- `git config --global [user.name](http://user.name) "Your name"` configurar nombre de usuario
- `git config --global user.email "email@example.com"` Configurar un email
