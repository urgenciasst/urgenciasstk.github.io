# ⚡️Instalación
Para comenzar a utilizar la consola batch y los comandos de git se debe instalar, para ello ingresar a:
[https://gitforwindows.org/](https://gitforwindows.org/)
Descargar e instalar el software.
Una vez hecho ya podes empezar a usar git.
# 📂Crear un repositorio nuevo
Crea un directorio nuevo, abrilo y ejecutá:

    git init
para inicializar un nuevo repositorio.
Una vez hecho, se creará una carpeta **“oculta”** llamada `.git`

# 📥Hacer checkout a un repositorio (Clonar)
### Crea una copia de un repositorio local utilizando:

    git clone /path/to/repository
Ejemplo:

    git clone /d/repositorios/proyecto_test.git
### Si utilizas un servidor remoto, ejecuta:

    git clone username@host:/path/to/repository
Ejemplo:

    git clone https://github.com/urgenciasstk/urgenciasstk.github.io.git
# 〰️Flujo de trabajo
### Los repositorios locales estan compuestos por tres "árboles" administrados por git.
 - Directorio de trabajo
 Contiene los archivos del proyecto.
 - Index
 Actua como una zona intermedia
 - Head
 Apunta al último commit realizado.
 Esto es lo que Git utiliza cuando se hace un "add" y un "commit".
En el siguiente gráfico se puede comprender mejor:
![Commit process](https://i.imgur.com/BPqmK3W.png)
# ✔️Add & Commit
### Registrar cambios (añadirlos al Index)
Este es el primer paso en el flujo de trabajo básico.
##### Para agregar un archivo especifico

    git add <filename>

##### Para agregar todos los archivos

    git add .
Ahora el archivo esta incluído en el **INDEX**.
### Hacer commit de los cambios (añadirlo al Head)
##### Para hacer un commit con un mensaje

    git commit -m "URG GDS-999999 STK REC2 - Descripción de cambios"
Ahora el archivo esta incluído en el **HEAD**, pero aún no en el repositorio remoto.

# 🚀Envío de cambios
Luego de realizar los dos pasos del flujo básico (Add & Commit), los cambios están ahora en el **HEAD** de tu copia local. Para enviar estos cambios a tu repositorio remoto ejecuta:

    git push origin master
Reemplaza ***master*** por la rama(branch) a la que quieres enviar tus cambios.

❗️ Si no clonaste previamente un repositorio ya existente y queres conectar tu repositorio local a un repositorio remoto, usa:

    git remote add origin <url_repositorio>
Una vez hecho esto, podrás subir tus cambios al repositorio remoto agregado.

# 〽️Ramas (branch's)
Las ramas son utilizadas para desarrollar funcionalidades aisladas unas de otras. La rama master es la rama ***"por defecto"*** cuando creas un repositorio y actua como rama ***"principal"*** del repositorio, una especie de ***Trunk*** si lo comparamos con *svn*.
![Ramas](https://i.imgur.com/1FIXCe6.png)
#### Crea una nueva rama y cámbiarse a ella

    git checkout -b ejemplo_nuevo_branch
#### Volver a la rama principal

    git checkout master
❗️ Cuando se crea una rama nueva, esta no estará disponible para los demás a menos que subas (push) la rama al repositorio remoto, para ello ejecuta:

    git push origin <ejemplo_nuevo_branch>

# 🔄Actualizar & Fusionar
### Actualizar cambios (Update)
Para actualizar tu repositorio local al commit más nuevo *(Update de svn)*, ejecuta:

    git pull
en tu directorio de trabajo para bajar y fusionar los cambios remotos.
`git pull` se encarga de hacer `git fetch`*(descarga de cambios)* seguido de `git merge`*(fusión de cambios)*.
### Fusionar cambios (Merge)
Para fusionar otra rama a tu rama activa (por ejemplo master), utilizá:

    git merge <branch>
en ambos casos git intentará fusionar automáticamente los cambios. 
### Conflictos
Como es de esperarse, no siempre se podran fusionar los cambios automaticamente, y se produciran conflitos.
Nosotros somos responsable de solucionar esos conflictos manualmente. Para ello se deberán editar los archivos marcados por git.
Después de modificarlos, debemos marcarlos como **"fusionados"**, para ello ejecuta:

    git add <filename>
Antes de fusionar los cambios, podes revisarlos usando:

    git diff <source_branch> <target_branch>

# 🔰Etiquetas (Tag's)
Tal como se utilizaba en SVN, en Git tambien se usa el concepto de etiquetas para cada nueva versión publicada de un software
Para crear una nueva etiqueta llamada ***1.0.1***, ejecutá:

    git tag 1.0.0 1b2e1d63ff
Como podrás observar, usamos ***1b2e1d63ff***, este *"código"* se refiere a los ***10 caracteres*** del **commit id** al cual queres referirte con tu etiqueta.
Para obtener los **commit id** podes ejecutar:

    git log
también podes usar menos caracteres que el commit id, pero debe ser un valor único.


# 📝Reemplaza cambios locales
En caso de que hagas algo mal se pueden reemplazar los cambios locales utilizando:

    git checkout -- <filename>
Este comando reemplaza los cambios en tu directorio de trabajo con el último contenido de **HEAD**.
 Los cambios que ya han sido agregados al **Index**, así como también los nuevos archivos, se mantendrán sin cambio.
Por otro lado, si queres deshacer todos los cambios locales y commits, podes traer la última versión del servidor y apuntar a tu copia local principal de esta forma:

    git fetch origin
    git reset --hard origin/master

# ⚡️Datos útiles
Datos o comandos de utilidad.
#### Interfaz gráfica por defecto

    gitk

#### Colores especiales para la consola

    git config color.ui true

#### Mostrar sólo una línea por cada commit en la traza

    git config format.pretty oneline

#### Agregar archivos de forma interactiva

    git add -i

