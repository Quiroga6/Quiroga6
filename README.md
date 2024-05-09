# Clase 1

Estado: Sin empezar

# Introducción a Git

## ¿Qué es un control de verificaciones?

Un control de verificaciones es un sistema que registra cada cambio que realiza en el código fuente de un proyecto.
Esto te permite tener un historial de todos los cambios producidos en sus ficheros, saber quien lo hizo y cuando.

## ¿Por que es importante un control de versiones?

- Rendimiento, solo se guarda lo necesario
- Seguridad, conserva toda acción
- Flexibilidad, no es necesario un desarrollo lineal

# ¿Qué es Git?

Git al ser un sistema distribuido, aloja una copia completa del repositorio en cada maquina local que esta trabajando en el código. Además, puedes tener uno o varios repositorios remotas para sincronizarlos.

![Concept image representing network, networking, connection, social networks, communications.jpeg](Clase%201%207bdc9b86e69f41cd8966d400f19ddc11/e48d1253-bed3-4e73-a438-594432b704d5.png)

## ¿Qué es un Repositorio?

Un pilar de Git son los repositorios
Un repositorio es una carpeta en la que se almacenan las diferentes versiones de los ficheros de un proyecto y el histórico de los cambios que se han realizado en ellos.
Los repositorios pueden ser locales.

### Comandos mencionados

Comandos de Git de la clase 1 varios comandos de Git, entre ellos:

- `git init`: Para inicializar un proyecto en Git.
- `git status`: Para ver el estado de los archivos en el repositorio.
- `git add <archivo>`: Para pasar un archivo al área de staging.
- `git commit -m "mensaje"`: Para realizar un commit con un mensaje descriptivo.
- `git log`: Para ver el historial de commits realizados.
- `git config --global [user.name](http://user.name) "Your name"` configurar nombre de usuario
- `git config --global user.email "email@example.com"` Configurar un email