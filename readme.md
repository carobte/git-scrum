# Manifiesto ágil

Declaración de valores y principios para el desarrollo de software ágil. Colaboración con el cliente, adaptabilidad al cambio y entregas continuas.

## Doce principios del manifiesto

1. Satisfacción del cliente
2. Adaptación al cambio
3. Entregas frecuentes
4. Trabajo en equipo
5. Personas motivadas
6. Comunicación directa 
7. Software funcional 
8. Continuidad
9. Excelente técnica
10. Simplicidad
11. Equipos auto-organizados
12. Mejora continua

# Metodolodía Scrum

Metodología ágil para trabajar por equipos, guiada por entregas y reuniones constantes para minimizar la posibilidad de errores.

## Sprints

Entregas periódicas con objetivos específicos

## Product ownner:

Dueño, da los requerimientos técnicos del proyecto, se comunica con el cliente directamente. Aprueba diseño, etc.

## Scrum Master 

Verifica las prácticas de la metodología del Scrum, dirige y asigna tareas mediante herramientas como trello, click up, notion, jira, github project. Idealmente es quien fusiona los cambios de dev en main.

## Team member

Miembros del equipo, los que se encargan de las tareas. Desarrolladores.

<br>
<br>
<hr>
<br>
<br>

# Git

## 1. Instalar Git
- https://git-scm.com/

## 2. Comandos git:

- git init -> Genera carpeta oculta.git. Aquí se guarda la configuración de git y registra los cambios. 

- git status -> nos muestra el estado de los archivos del proyecto. Si se le hace seguimiento o no.

- git add .->  añade todos los archivos. Si queremos un archivo específico sería git add < archivo >

- git commit -m "< mensaje >"-> punto de control

El mensaje debe ser descriptivo, y por convención debemos poner si estamos agregando, editando o eliminando algo. (Conventional commits)

Ejs: 

- Creación archivo index.html:

<code> git commit -m "feat: Creación index.html" </code>

- Edición/ arreglar algo:

<code> git commit -m "fix: Modificación title en el html" </code>

- git config --list -> muestra la configuración actual de git

- git log -> muestra el historial de commits del proyecto

### Configuración variables

- git config --global user.name "< github user >"

- git config --global user.email "< github email >"

## 3. Conexión GitHub

- git remote add origin < url > -> origin es el nombre del remoto, url de github

- git clone < url > -> si fue creado en linea, con este comando se descarga

- git pull origin < rama > -> descarga los commits del repositorio en linea

- git push origin < rama > -> sube los commits realizados de manera local

<br>
<br>
<hr>
<br>
<br>

# Git Flow

Modelo de flujo de trabajo que usa Git para control de versiones. Se usa para manejar ramas.

- main: antes llamda master, rama principal. Producto entregable, en línea. Estado de producción (distribución). No se debería hacer push directamente a main.

- hotfix: no debería crearse, pero se usa para solucionar problemas en caliente cuando se está en producción y se van los cambios a main y dev (develop).

- dev: rama de desarrollo, aquí es donde se hacen los cambios. Por eso se haría git pull origin dev, no main.

- feature/idTarea: ramas para las características que se unen en dev. Todos los commits de este feature, deben ser para ese id, si se necesitan más cambios se puede crear otroa tarea y otro feature.

- release: rama de QA. Preparar lanzamientos de nuevas versiones

Se trabaja en ramas para tener un mejor control de quién hace qué.

No es normal que la rama main tenga una feature, debe pasar por dev. Sino, pasa por una hotfix.

- Desde GitHub podemos crear ramas desde la interfaz.

### Proceso:

#### Gestor de tareas (Trello, Jira, etc.)

Se busca la persona y se asigna las tareas.
Cuando se crea la tarea, genera un id. 

- git clone del repositorio donde estamos trabajando. (Si ya lo tenemos, hacer el git pull para tener la versión actual del proyecto)

- git checkout -b < feature/idTarea_AyudaVisual > -> crea la rama y nos posiciona en ella directamente. Puede llevar _PalabraClave para ayudarnos a identificar la tarea, pero siempre debe llevar el id.

- Se desarrolla lo necesario de la tarea específica en la rama creada. 

- Al finalizar, se hace:
<code> git push origin feature/idTarea_AyudaVisual </code>

- Luego, desde GitHub, creamos el pull request. Por defecto, intenta mandarlos a main, debemos modificarlo a la rama develop. Desde GitHub, podemos organizar en reviewers quién va a revisar ese pull request.

- Hasta ahí llegamos con esa tarea normalmente, podemos continuar el proceso con cada tarea.

##### Desde el administrador

- En el repositorio, sale en el menu de pull request la solicitud. Además, sale en qué rama estamos. Y debe salir el aviso de que main no está protegida, normalmente ella siempre está protegida.

- Puede ver todos los cambios que se hicieron, comentar, aprobar, rechazar los cambios.

- Cuando hay conflictos, se hace pull de develop, sino no porque pueden haber más personas trabajando en otras features. 

- Cuando se aprueban los cambios, desde GitHub, se hace el pull request y el merge. Ahí ya se cierra el cierre del ticket (tarea). Cuando vemos la rama develop, aparece en los commits de develop, y sale el pull request y quién lo aprueba.
