# Post Formateo de PC:

 En este caso simularemos un formateo y cambio de sistema operativo en nuestro Pc, para ello debemos recordar todas las dependencias que vamos a necesitar en cualquier proyecto que realizemos con Ruby on Rails. En por ello que a continuación se explicará en detalle que debemos hacer, paso a paso.

 Configuracion e instalacion de git:

 `git remoto:`

- Para actualizar los repositorios:

 `$ sudo apt update`

 `sudo:` esto les da el super usuario para las actualizaciones o descargas de programas.

 Descarga de Git en Ubuntu:

 `$ sudo apt install git`

 Enter


### Cómo crear una clave .ssh para mi Pc Ubuntu y utilizarla en github:

***PRIMERO:***

Para verificar si tengo mis llaves creadas en mi pc, usar el siguiente comando:

`:~$ ls -al ~/.ssh`

Configuracion con email usuario:

`$ git config --global user.name 'nombre'`

Enter

`$ git config --global user.email email@email.com`

Enter

`$ ssh-keygen -t rsa -b 4096 -C "email@algo.com"`

Enter

Enter

Enter

 `$ +---[RSA numero]----+`
*****************************************************************************************************************************************************

### Añadir la clave privada al ssh:

`$ eval "$(ssh-agent -s)"`

(debiera entregar un numero pid)

***************************************************************************************************************************************************

#### Añadir la llave al achivo:

`$ ssh-add ~/.ssh/id_rsa`

Enter

(nos debiera aparecer el email del usuario)

* Copiar la llave pública a GitHub:

` $ sudo apt install xclip` (te pedira la clave del equipo)

***NOTA: Este comando genera un archivo para ser copiada la llave pública en GitHub:***

`$ xclip -sel clip < ~/.ssh/id_rsa.pub`

* Luego abrir la página GitHub, ir a Settings...ssh and gpg keys:

(añadir nueva llave pública)


* Para verificar que se creo la llave:

`$ ssh -v`

`$ ls .ssh`

`$ ssh-keygen`

`$ ls .ssh`

`$ cd .ssh`

`$ ls`

`$ cat id_rsa.pub `


***En esta parte copio la llave y la pego en repositorio git, setting, SSH and GPG keys, New SSH key... title... key(pegar llave)...Add SSH key...y esta lista la configuración.***


Para ver las credenciales que están creadas:

`$ git config --list`

***NOTA: "NO OLVIDAR CREAR EL REPOSITORIO EN GITHUB"***

* Crear 

`$ git init`: (este comando inicializa el proyecto en el que estas trabajando)

`$ git add .` : (este comando prepara los cambios para que sean subidos)

`$ git git commit -m"commit"`: (aca se añade un titulo relacionado al o los cambios que realizaste, no olvidar que van entre comillas dobles)

`$ git push origin master`: (aca finalmente se suben todos los cambios a tu repositorio)

### Instalación y configuración de Postgresql:

Este será nuestro motor de Base de Datos, nos servirá para que los datos que necesitemos almacenar perduren en el tiempo hasta que decidamos eliminarlos. Cómo hacemos esta maravilla?

Lo primero es: En la terminal debes introducir el siguiente comando para la inslación:

`$ sudo apt install postgresql`

Enter

¿Desea continuar? [S/n] s (Obviamente necesitamos continuar, por lo que pondrás que si ó s).

Este comando lo que hará es llamar a la base de datos postgres para su previa configuración:

`$ sudo -i -u postgres`

Damos el siguiente comando que es `$ psql`, esto nos permitirá crear la base de datos y dar un nuevo usuario.

`postgres@nombreDeTuPc:~$ psql`

Creamos la db con el mismo nombre del equipo: 

ejemplo: si mi equipo se llama @juanito, la db se llamará juanito. 

```
postgres=# CREATE DATABASE nombreUsuario;
CREATE DATABASE
```


Creamos el usuario con los roles que necesitemos, en este caso crearemos al usuario eva el cual será nuestra madre(SUPERUSER) de todos los procesos, desde crear más roles hasta admnistrar db o destruirlas.


```
postgres=# CREATE USER eva WITH SUPERUSER CREATEDB;
CREATE ROLE
```


Para listar todos los usuarios creados y sus roles, pon el siguiente comando:

`postgres=# \du`

***NOTA: Puedes hacer el backslash con Alt Gr + la tecla que tiene el signo de pregunta y la barra invertida.***

Puedes modificar al superuser con:

`postgres=# ALTER USER eva [roles a editar]`

Con esto ya tenemos configurada la base de datos con la cual trabajaremos pero de manera dinámica.(esto es el tras bambalinas de la app con su framework, por tanto debes saber de todas manera como opera).

*****************************************************************************************************************************************************

### Para instalar Ruby on Rails:

Antes que todo; necesitaremos un gestor de versiones, esto es para ordenarnos en las versiones que trabajaremos con Ruby, podemos tener cuantas versiones queramos pero, se recomienda trabajar con versiones estables, ya que existe mucha documentación formal al respecto.

Primero instalaremos rvm, gestor de dependencias:

`$ sudo apt-get install -y git-core subversion`


`$ gpg --keyserver hkp://keys.gnupg.net --recv-keys 409B6B1796C275462A1703113804BB82D39DC0E3 7D2BAF1CF37B13E2069D6956105BD0E739499BDB`

`$ \curl -sSL https://get.rvm.io | bash -s stable --rails --ruby`

`$ type rvm | head -n 1`


*****************************************************************************************************************************
### Instalar Rails:



Es aquí donde podemos instalar la versión que más nos guste trabajar, por lo general recomiendo instalar la versión que más te acomode.

`$ rvm install -v 2.5.3`


Para Rails, recomiendo instalar la versión que más te guste (rails 7) y si quieres probar varias versiones, puedes pasarle el comando $ gem install rails [la_version_que_gustes].

`$ gem install rails -v 5.2.5`

Crear gemset:

¿Para qué es importante instalar rvm?

rvm será nuestro gestor de versiones de Ruby y Rails, en las cuales podemos crear varias versiones de trabajo, solo debemos contar con versiones de Ruby y Rails previamente instaladas.

¿Cómo crear un gemset:

`$ rvm gemset create rails525`

***NOTA: Lo ideal es darle un nombre que haga referencia a la versión de Rails la cual voy a utilizar.***

********************************************************************************************************************************************

### Hacer un Proyecto de cero:

Para ello, vamos a generar de manera dinámica lo siguiente:

Crear una carpeta vacía en nuestro escritorio a la cual llamaremos 'prueba', abrirla en la terminal, revisar versiones de Ruby y Rails, cómo hacemos esto? 

```
$ rails -v 
$ 5.2.5
$ ruby -v 
$ 2.5.3
```

***Ahora creamos el proyecto con el siguiente comando:***

`$ rails new post -d postgresql`

Esto hará que de manera automática se configure nuestra base de datos, en este caso incluirá la `gem pg`, y en nuestro archivo .yml este configurada desde el inicio del proyecto.



****************************************************************************

### rvm problem

```shell
rvm use 3.0.0
```

```shell
RVM is not a function, selecting rubies with 'rvm use ...' will not work.

You need to change your terminal emulator preferences to allow login shell.
Sometimes it is required to use `/bin/bash --login` as the command.
Please visit https://rvm.io/integration/gnome-terminal/ for an example.
```

***Solutions:***

```shell
$ source $HOME/.rvm/scripts/rvm
$ rvm use 3.0.0
```
