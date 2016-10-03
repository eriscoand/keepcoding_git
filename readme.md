**- ¿Qué comando utilizaste en el paso 11? ¿Por qué?**

En el paso 11 he utilizado el siguiente comando:

git reset --hard HEAD~1

Con el comando reset puedo moverme a cualquier commit, con HEAD~1 le indico que quiero el anterior
al que me encuentro actualmente, y con --hard le obligo a eliminar cualquier fichero o modificacion
realizada.

  
**- ¿Qué comando o comandos utilizaste en el paso 12? ¿Por qué?**

En el paso 12 he utilizado los dos comandos siguientes:

- git reflog
- git reset --hard NUMERO_COMMIT 

Con el comando reflog he podido averiguar el commit donde tenia realizada la modificacion al fichero.
Me he guardado el GUID, y posteriormente he utilizado el comando reset pero esta vez poniendo el 
identificador del commit al que queria volver. Con --hard me he asegurado que se realize las modificaciones
al fichero.


**- El merge del paso 13, ¿Causó algún conflicto? ¿Por qué?**

Al realizar el comando "git merge master" estando en la rama styled me ha mostrado el siguiente mensaje:

“Already up-to-date”

Este mensaje significa que todos los canvios de la rama que estamos intentando hacer el merge ya esta incluida
en la rama en la cual estamos actualmente. 
Esto quiere decir que la rama la cual estamos intentando absorver es padre de la rama actual, y no tiene sentido
absorverla.


**- El merge del paso 19, ¿Causó algún conflicto? ¿Por qué?**

Si, el merge del paso 19 causó un conflicto. Al intentar que la rama styled absorba la rama htmlify se encuentra 
que el fichero git-nuestro.md es diferente en cada una de las ramas. Como no puede decidir que texto guardar,
ha modificado el fichero git-nuestro.md con el contenido de las dos ramas.


**- El merge del paso 21, ¿Causó algún conflicto? ¿Por qué?**

En este caso no se podria llamar que causó un conflicto. Cuando se intenta fusionar un commit con otro commit
accesible upstream, git simplifica el merge avanzando el puntero ya que no hay ninguna otra rama divergente
de trabajo. En otras palabras, ahora en la rama master, que se supone que es la principal, esta todo el trabajo
realizado en la rama styled.


**- ¿Qué comando o comandos utilizaste en el paso 25?**

Para dibujar el diagrama se usa el comango log. Este comando se puede hacer que dibuje el diagrama con algunas
opciones.

Para facilitar el trabajo he creado un alias con el comando siguente:

git config alias.graph "log --graph --decorate --pretty=oneline"

De esta forma siempre que utilize "git graph" me mostrarà el diagrama sin tener que escribir todas las opciones.


**- El merge del paso 26, ¿Podría ser fast forward? ¿Por qué?**

Si, el merge del paso 26 podria ser fast forward ya que la rama master es padre de la rama title. Con el merge se quiere
conseguir que la rama master tenga los mismos commits que la rama title. Con fast-forward, git simplemente moveria el
puntero a la rama title, ya que la rama master es padre de la rama title. Sin el fast-forward lo que hemos
conseguido es que se cree otro commit con dos padres, master y title. El nuevo commit tendra todo el trabajo
hecho en el commit title, sin perder el trabajo del commit master.


**- ¿Qué comando o comandos utilizaste en el paso 27?**

En el paso 27, para deshacer el cambio he utilizado el comando siguiente:

git reset HEAD~1

Como el merge del paso 26 era sin fast forward, se ha creado un commit que tiene como padre el commit master i el commit title.
Desaciendo el último commit volveriamos al estado anterior. Como no he puesto --hard los cambios no se han perdido 


**- ¿Qué comando o comandos utilizaste en el paso 28?**

En el paso 28 he utilizado el siguiente comando:

git reset --hard HEAD~0

Con este comando lo que consigo es moverme al commit actual forzando la modificacion del working copy. Es decir, en el paso
27 con el reset al commit anterior sin modificar el working copy, el fichero se quedaba con la modificacion del commit de la
rama title. Reseteando al commit actual, que es al que nos queremos quedar, y forzando la modificación, se descartaran los 
cambios sobre el fichero.


**- ¿Qué comando o comandos utilizaste en el paso 29?**

Para el paso 29, eliminar la rama title he utilizado estos dos comandos:

git branch -d title

Después de este comando git me avisa que la rama no esta merged. Para asegurar el
delete se tiene que poner el siguiente comando:

git branch -D title

**- ¿Qué comando o comandos utilizaste en el paso 30?**

Para rehacer el merge que hemos deshecho he utilizado los siguientes comandos:

- git reflog
- git reset --hard NUMERO_COMMIT

Con "reflog" encuentro el numero de commit donde esta el merge creado a partir
del merge sin fast forward.
Me guardo el GUID del commit y con "reset --hard" y el número del commit 
vuelvo al commit donde esta el merge sin fast forward. 

En este caso, la rama title no se vuelve a crear con el reset. Se tendria que crear manualmente.

**- ¿Qué comando o comandos usaste en el paso 32?**

Para volver al commit inicial he utilizado los siguientes comandos:

git reflog
git checkout NUMERO_COMMIT

Con "reflog" encuentro el numero de commit inicial. Es el último de la lista de commits.
Me guardo el GUID del commit y con "checkout" y el número del commit
vuelvo al commit inicial.


**- ¿Qué comando o comandos usaste en el punto 33?**

Para volver al commit final he utilizado los siguientes comandos:

- git reflog
- git checkout NUMERO_COMMIT

Con "reflog" encuentro el numero de commit final, donde se hace el merge de title a master.
Me guardo el GUID del commit y con "checkout" y el número del commit
vuelvo al commit final.
