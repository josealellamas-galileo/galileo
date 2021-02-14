# Acerca de Git
#### Por José Alejandro Llamas


## Introducción


Hoy más que nunca vivimos en una época donde el **trabajo colaborativo** es *clave* para cualquier industria. Conforme avanza la globalización, cada vez es más común la contratación de personal "alrededor del mundo", y la industria *tech* no es la excepción.

Con ello también se presenta una serie de desafíos tales como la buena administración de proyectos de código, mantener un seguimiento en el historial de cambios y sobre todo cuidar la efectividad del producto final.

Es aquí donde aparece **Git**, un software de control de versiones (VCS) que permite llevar un control sobre los cambios realizados en un proyecto de código o de otra índole.

A lo largo de esta investigación se hablará un poco acerca de la historia de Git, el modelo estructural de datos, terminología clave y **los comandos más utilizados** para empezar a trabajar con este software de versiones.





¿Qué es Git?
---
***

### Breve reseña histórica

Allá en el 2005, Linus Torvalds había desarrollado el **mayor proyecto** de su carrera hasta el momento: Linux. Este lo había desarrollado en un software de control de versiones llamado BitKeeper, sin embargo dejó de ser una opción gratis, por lo que Torvalds no le agradó para nada. 

Fue gracias a ello que y su pasión por el código que Torvalds se propuso desarrollar su propio sistema de versiones. La herramienta que hoy conocemos como **Git**.

![Git_logo](https://julioecheverri.files.wordpress.com/2016/07/git-logo.png)

Hoy en día, gracias a Internet, es posible contactarnos con usuarios que se encuentran a cientos de kilómetros de nosotros. Esto permite que el trabajo colaborativo no se limite a un trabajo de oficina, sino más bien de conectar con otros puntos alrededor del mundo.

Git es una respuesta a ello. Es lo que en la industria del desarrollo se denomina un **Version Control System (VCS)** o bien un sistema de control de versiones. La función de estas herramientas es **dar un seguimiento** al historial de versiones que se genera en un proyecto de código o de otro tipo de archivos.

Cada versión (o snapshots) generado es un conjunto de archivos que describen a la versión en un momento dado y que necesariamente **debe ser distinto** a los demás. Adicionalmente también se almacena cierta *metadata* que describe algunos atributos de utilidad para el usuario, tales como el autor, fecha de cambios, descripciones, etc.

Si bien existen otras herramientas VCS, Git ha sido el éxito comercial más utilizado hoy en día.

### Modelo de datos de Git

El modelo de datos empleado por Git es el siguiente:

- Los fólderes son denominados *árboles (trees)*;
- Los archivos son denominados *blobs*;

Si bien este es un modelo básico de datos, Git lo lleva a otro nivel. En vez de utilizar un modelo lineal, emplea algo llamado **directed acyclic graph** (DAG).

![DAG](https://i.stack.imgur.com/8Nt1U.png)


La imagen anterior es un digno ejemplo de DAG. Lo que caracteriza a un modelo de este tipo es: 1) posee una dirección o sentido; 2) existen *ramificaciones* (branches) que pueden conectarse en cualquier punto con el "ciclo maestro". Tal es el caso de los snapshots impares (1, 3, 5, 7).

**¿Y para qué nos sirve?** 

![thinking_emoji](http://s3.amazonaws.com/pix.iemoji.com/images/emoji/apple/ios-12/256/thinking-face.png)


En la vida real es posible querer llevar un producto final mientras que paralelamente se haga un testeo de un nuevo feature. Y para no afectar el código maestro, se puede trabajar con una copia del repositorio **sin afectar** al producto final.

Términos como repositorio, branches y código maestro se verá a continuación.

Terminología
---
***


1. **Objects.** El modelo de Git está basado en una colección de objetos, identificados con un ID único (Sha-1 code). Un [objeto](https://git-scm.com/book/en/v2/Git-Internals-Git-Objects) puede ser un blob, un tree o incluso un commit.


2. **References.** Git utiliza funciones de referencia para traducir códigos del tipo Sha-1 (40 caracteres) a nombres entendibles y significativos para el usuario. Una referencia es la forma en cómo se conectan los objetos, teniendo así una *dirección o sentido* (flecha).


3. **Master.** Es la rama principal de development. Si bien se genera por default, es donde el proyecto final se va construyendo. Una buena práctica es agregar las versiones definitivas **una vez se hayan verificado** para evitar estropear el proyecto.


4. **HEAD.** Similar a un puntero (mouse), indica dónde el usuario se encuentra posicionado en el tree.


5. **Staging Area.** Al momento de realizar cambios en un archivo, el usuario deberá cargar el mismo en un proceso "antesala" al proyecto final. Este se llama *staging Area*. El objetivo de esto es decirle a Git **qué cambios deberán incluirse** en el siguiente snapshot. 


6. **Commits.** Una vez se está seguro que el archivo está correcto, el usuario lo integrará al repositorio. Con ello se crea una versión o *commit*. Es importante mencionar que con cada versión se genera metadata útil como el hash number, el repositorio añadido y alguna descripción generada para la versión.


Comandos de Git
---
***

### Comandos generales

| Comando | Descripción |
| :---: | :--- |
| `git init` | Significa *initialize* y la acción que ejecuta es comenzar un repositorio en Git. | 
| `git help` | Brinda información acerca del comando referenciado. La estructura es git *help* + comando. | 
| `git status` |Nos brinda información acerca del estado del repositorio.|
| `git add` |Permite agregar una nueva versión del blob al staging area.|
| `git commit` |Agregará finalmente la nueva versión del blob al repositorio. El resultado es generar una versión del archivo. Adicionalmente el user podrá ingresar algún mensaje referente al cambio realizado.|
| `git log` |Permite ver el historial de cambios.|
| `git log --all --graph --decorate` |Al igual que el comando log permite ver el histórico solamente que de una forma más gráfica. La versión más reciente aparecerá de primero.|
| `git **log --all --graph --oneline` |Permite ver el histórico de versiones de una manera visual, pero más compacta. Los datos mostrados son el Sha-1, la versión y la información sobre el cambio.|
| `git cat-file` |Imprime en pantalla el contenido de un commit.|
| `git checkout` |Permite movilizarse dentro del historial de versiones y/o oramas así como realizar cambios brindando el hash commit code.|
| `git checkout -b papd` |Además de movilizar el cursor HEAD, aprovecha para crear una nueva referencia. En este caso con nombre "papd".|
|`git diff`| Muestra en pantalla lo que cambió en un snapshot respecto a la última. Si se ingresan parámetros como el hash commit code un snapshot en específico, mostrará los cambios respecto a la versión especificada.|
|Colores mostrados | Texto en **<font color=green>verde</font>**. Texto agregado a la referencia pasada. \| Texto en **<font color=red>rojo</font>**. Texto eliminado a la referencia pasada. \| Texto en **<font color=gray>gris</font>**. Texto que se mantuvo a la referencia pasada.|

    
### Comandos de ramificación (branch)

| Comando | Descripción |
| :---: | :--- |
|`git branch`| Permite acceder a funcionalidades específicas de branches. Si se emplea el comando sin algo más, enlistará las ramas que existen asociadas al repositorio local.|
|`git branch -vv`| Permite acceder a funcionalidades específicas de branches. Si se emplea el comando sin algo más, enlistará las ramas que existen asociadas al repositorio local.|
|`git branch galileo`| Crea una nueva branch con el nombre asignado. En este caso, galileo.|


### Comandos de unificación (merge)

| Comando | Descripción |
| :---: | :--- |
| `git merge papd`| Este comando permite unificar dos o más referencias. En caso exista incopatibilidad entre las mismas, Git imprimirá en pantalla un texto referente al conflicto.|
|Fast-forward | Este mensaje aparecerá en pantalla cuando se desea hacer un merge entre dos ramas, donde el commit actual (HEAD) es predecesor del que se desea unir. Lo que hará Git nada más será unificar ambos branches sin crear un nuevo snapshot|
|`git mergetool`| A través de este comando será posible acceder al programa `vimdiff` el cual es una herramienta para resolver conflictos de unificación (merge).|


### Comandos remotos (remote)

| Comando | Descripción |
| :---: | :--- |
| `git remote`| Enlista todas las instancias que existen del mismo repositorio. Estos pueden ser de los colaboradores del proyecto, en un repositorio como Github.|
|`git remote add (nombre) ../(link)`| A través del copiado del repositorio, este comando permite dos cosas: 1) indicar que existe una copia del repositorio y asignarle un nombre; 2) colocar  un link de referencia (p. ej. el link a Github).
|`git push <nombre del remoto> <local branch>:<remote branch>`| Permite enviar los cambios realizados en la computadora local hacia el remoto. Los parámetros ingresados son: 1) nombre del repositorio remoto; 2) El nombre de la rama local; 3) nombre de la rama remota|
|`git clone <URL> <carpeta destino>`| Hace una copia local de un repositorio existente. Los parámetros que recibe son: 1) la URL u origen de dónde será copiado; 2) la carpeta donde se creará la copia local.|
|`git fetch`| Recupera los cambios de un repositorio remoto en mi máquina local. Una vez recibidos los cambios se puede hacer un *merge* para actualizar los cambios y apuntar hacia el mismo lugar donde la rama remota apunta.|
|`git pull`| Realiza la misma acción que *fetch* agregando *merge* al mismo tiempo.|


### Comandos de configuración (config)

| Comando | Descripción |
| :---: | :--- |
| `git config` | Permite acceder a los formatos de configuración de Git.|
| `git clone --shallow`| Al igual que el comando *clone* permite hacer una copia local, no obstante mediante este argumento **únicamente** copiará el último snapshot. El objetivo de esto será ahorrar tiempo de descarga.|
| `git add -p` | Es una forma interactiva para manejar el área staging. En base a los cambios, crea ambientes independientes para aceptar o rechazar los cambios. |
| `git blame` | Permite conocer el usuario responsable de realizar alguna modificación en una línea de código.|
| `git show <Sha-1 code>`| Muestra información detallada de un commit en particular.|
| `git stash` | Permite revertir el directorio de trabajo hacia el último commit. El comando para revertirlo es **stash pop**.|
| `gitignore`| Ignora archivos que no son de interés para el usuario. |

Conclusiones
---
***

- Es un hecho que el trabajo colaborativo alrededor del mundo es más fuerte que nunca. Especialmente en la industria tech y en proyectos de código. Si bien es posible trabajar con perfiles muy capacitados y altamente competentes, también nos enfrentamos a una serie de desafíos como lo es el trabajo simultáneo y la buena administración de ello. Por ende es sumanente útil trabajar con herramientas que nos ayuden a hacer un seguimiento de los cambios creados en un proyecto de código u otra índole.

- Git es una herramienta perfecta para ello. A través de este software es posible administrar la carga de versiones que pueden generarse para elaborar un proyecto con varias fases. Adicionalmente es flexible en cuanto a la creación de diversas versiones y la conexión de estas en algún punto. Asímismo otorga a los usuarios el control que necesitan al momento de implementar cambios, dándoles la oportunidad de escoger qué integrar y qué no.

- Si bien la interfaz de Git no es la más atractiva --una terminal--, la clave para trabajar bien con ella es comprender su modelo de datos. Admito que mi primer acercamiento con esta fue bastante abrumadora, no obstante indagar la forma en cómo funciona y los comandos que utiliza, puedo decir que mi percepción de Git es más favorable que negativa.

- En lo que resta del curso y lo que depara mi futuro profesional estoy seguro que la herramienta será una fuerte aliada a la hora de trabajar proyectos de código. Considero que la práctica será la herramienta que me ayudará a pulir el uso de Git y llevar a cabo proyectos efectivos.


Referencias
---
***

- [EDTeam - ¿Qué es Git y cómo funciona?](https://www.youtube.com/watch?v=jGehuhFhtnE)
- [Github - Organizar información en tablas](https://docs.github.com/es/github/writing-on-github/organizing-information-with-tables)
- [Medium - Markdonw for Jupyter Notebooks cheatsheet](https://docs.github.com/es/github/writing-on-github/organizing-information-with-tables)
- [MIT - Version Control](https://docs.github.com/es/github/writing-on-github/organizing-information-with-tables)
- [SQLBak - Jupyter Notebook Markdown cheatsheet](https://docs.github.com/es/github/writing-on-github/organizing-information-with-tables)




```python

```
