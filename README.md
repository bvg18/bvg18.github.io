# Mercurial, la alternativa a Git.

Metodologías Ágiles de Desarrollo de Software, Universidad de Alicante, curso 2020/21. <br>
Página web creada por Brais Valencia García. Github Developer Student Pack y Namecheap.

## Mercurial
El uso de git es casi unanime en el desarrollo de software, pero existen otras opciones igualmente validas como Baazar o Mercurial.
Es el caso de este último sistema de control de versiones del que hablaremos en esta página web. Más concretamente su uso en relación 
a la práctica 4, realizada de forma grupal, de la asignatura Metodologías de Desarrollo de Doftware de la Universidad de Alicante. <br>
Pongámonos manos a la obra, aprendamos sobre el proyecto Mercurial y su potencial.

## Historia
[Mercurial](https://www.mercurial-scm.org/) es un sistema de control de versiones distribuído. Su nombre le viene del termino 
[Hidrargiro](https://es.wikipedia.org/wiki/Mercurio_(elemento)). Termino usado en la literatura antigua para designar al 
Mercurio, elemento quimico con el símbolo Hg y número atómico 80. <br>
El creador y desarrollador principal de Mercurial es Matt Mackall, que hizo pública la existencia de Mercurial el 19 de abril de 2005.
Con el objetivo de cubrir la necesidad existente de un sistema de control de versiones de software libre que sustituyera a la versión gratuita de BitKeeper.
Ya que esta iba a ser retirada por sus creadores Bitmover. Se había estado usando BitKeeper debido a los requisitos de control de versiones del proyecto del núcleo Linux. Mackall decidió escribir Mercurial como sustituto para usarlo con el núcleo Linux. El proyecto comenzó aproximadamente al mismo tiempo que otro denominado git, iniciado por el propio Linus Torvalds con objetivos similares. El proyecto Linux decidió usar Git en lugar de Mercurial, y por ello el proyecto de Mackall se quedaría en un segundo plano.
Siendo Git dueño y señor de los sistemas de control de versiones hasta la fecha, enero de 2021. <br>

Por otro lado, el proyecto Mercurial estaba desarrolado usando el lenguaje de programación [Python](https://www.python.org/) como lenguaje principal. Pero también 
hay partes, como la comparacion binaria de [diff](https://es.wikipedia.org/wiki/Diff) desarrolladas en C.<br>
Las principales metas del desarrollo de Mercurial incluyen un gran rendimiento y escalabilidad; desarrollo completamente distribuido, sin necesidad de un servidor; gestión robusta de archivos tanto de texto como binarios; y capacidades avanzadas de ramificación e integración, todo ello manteniendo sencillez conceptual.
El código fuente de Mercurial se encuentra disponible bajo los términos de la licencia GNU GPL versión 2. <br>

## Instalación
Mercurial fue escrito originalmente para funcionar sobre GNU/Linux. Pero ha sido adaptado para poderse utilizar en Windows, Mac OS X y la mayoría de sistemas tipo Unix.
Comenzaremos la instalación del sistema de control de versiones descargandolo. Dependiendo del sistema operativo que usemos, lo podremos hacer mediante linea
de comandos o ejecutable.
> [Mercurial para Windows](https://www.mercurial-scm.org/wiki/Download#Windows) <br>
> [Mercurial para Mac OS X](https://www.mercurial-scm.org/downloads) <br>
> [Mercurial para Linux](https://www.mercurial-scm.org/wiki/Download#Linux_.28.deb.29) <br>

Para más detalles sobre la instalación o algun problema que pudiera surgir tenemos la [wiki de Mercurial](https://www.mercurial-scm.org/wiki/Download).

## Configuración
Toda la información relativa al control de versiones de un proyecto se guarda en el directorio raíz del proyecto, concretamente
en el subdirectorio ".hg". <br>
La configuración general para cada usuario se guarda en el archivo ".hgrc" y la configuración local para cada proyecto se guarda en
"<repo>/.hg/hgrc". <br>
  
Tendremos que comprobar si existe el archivo ".hgrc":
- En Windows ``` $ ls .hgrc ```.
- En Mac y Linux ``` $ ls ~/.hgrc```.

Si no existe el archivo lo ponemos crear con ``` $ touch ~/.hgrc ```.

Por último, modificaremos el archivo ``` .hgrc ``` añadiendo un nombre de usuario y un correo electrónico. 
```
[ui] <br>
# Nombre que aparecerá en el commit <br>
username = Emma Paris <eparis@atlassian.com> <br>
```

Guardamos el archivo y lo cerramos. Estaremos listos para empezar a usar Mercurial.

## Comandos básicos
Vamos ahora a ver las instrucciones básicas de Mercurial. Así pues, la directiva de Mercurial es ```hg``` por el simbolo quimico antes mencionado.
**Por tanto, podemos crear un repositorio local:**
```
hg init (directorio del proyecto)
cd (directorio del proyecto)
```

**Añadiremos los archivos iniciales del proyecto y una vez hecho esto ejecutamos el siguiente comando:**
> hg add (ficheros nuevos) <br>
O también podemos añadir todos los ficheros nuevos a la vez con:
> hg add .
**Una vez añadido los ficheros, podemos hacer el primer commit de nuestro repositorio:** <br>
Con el parametro -m podremos añadir un comentario al commit. Es una buena práctica siempre añadir uno o dos de estos en cada commit. <br>
> hg commit -m "Primer commit" <br>
<br>
**Podemos ver el estado de nuestro repositorio con el siguiente comando:** <br>
> hg status
<br>

**Mercurial admite el uso de [extensiones](https://www.mercurial-scm.org/wiki/UsingExtensions) para añadir diversas funcionalidades o mejoras:** <br>
Podemos ver las extensiones disponibles con el siguinte commando
> hg help extensions <br>
**Ádemas, podemos ver información de una extensión en concreto de la siguiente forma:** <br>
> hg help nombre-extension <br>
**Por último, podemos habilitar y deshabilitar las extensiones:** <br>
> Las extensiones se deben **habilitar**, p.e. en .hg/hgrc:<br>
> [extensions] <br>
> foo = <br>
> \# Podemos especificar la ruta concretan <br>
> [extensions] <br>
> myfeature = ~/.hgext/myfeature.pyb <br>

<br>

> También se pueden **deshabilitar** de una en una: <br>
> [extensions] <br>
> \# disabling extension bar residing in /path/to/extension/bar.py <br>
> bar = !/path/to/extension/bar.py <br>
> \# ditto, but no path was supplied for extension baz <br>
> baz = ! <br>
<br>

**Para dar de alta un nuevo repositorio en un proyecto, edita su ```\<proyecto>/.hg/hgrc``` y añade una nueva entrada en
paths así:**
```
[paths]
default = http://www.hgrepos.net/r1   -> Es especial, se usa como valor por defecto cuando no especificamos la URL.
default-push = ssh://mads@hgrepos.net/r1  ->  Idem pero cuando hacemos un push.
...
alias1 = URL1
alias2 = URL2
```

**Los conflictos se marcan igual que en otros scv:**
```
<<<<<<< /tmp/conflict/crab.cpp
void function() {
=======
int function() {
>>>>>>> /tmp/crab.cpp
```

falta por meter: añadir una url de repositorio y cosas como crear ramas y push

## Nuestro proyecto con mercurial
## Subir a Github ?
## Alternativas Hg a Github ?
## Conclusión

