# Mercurial, la alternativa a Git.

Metodologías Ágiles de Desarrollo de Software, Universidad de Alicante, curso 2020/21. <br>
Brais Valencia García

## Mercurial
El uso de git es casi unanime en el desarrollo de software, pero existen otras opciones igualmente validas como Baazar o Mercurial.
Es el caso de este ultimo sistema de control de versiones del que hablaremos en esta pagina web. Mas concretamente su uso en relación 
a la práctica 4 (grupal) de la asignatura Metodologias de desarrollo de software de la universidad de alicante. <br>
Pongamonos manos a la obra y aprendamos un poco sobre el proyecto Mercurial.

## Historia
[Mercurial](https://www.mercurial-scm.org/) es un sistema de control de versiones distribuído. Su nombre le viene del termino 
[Hidrargiro](https://es.wikipedia.org/wiki/Mercurio_(elemento)). Termino usado en la literatura antigua para designar al 
Mercurio, elemento quimico con el símbolo Hg. <br>
El creador y desarrollador principal de Mercurial es Matt Mackall, que hizo pública la existencia de Mercurial el 19 de abril de 2005.
Para cubrir la necesidad de un sistema de control de versiones de software libre que sustituyera a BitKeeper.
El código fuente de Mercurial se encuentra disponible bajo los términos de la licencia GNU GPL versión 2. <br>

El lenguaje de programación que predomina en el proyecto es [Python](https://www.python.org/) pero tambien hay partes escritas en C.<br>
# Añadir más aquí, hay un monton de información

## Instalación
Mercurial fue escrito originalmente para funcionar sobre GNU/Linux. Pero ha sido adaptado para poderse utilizar en Windows, Mac OS X y la mayoría de sistemas tipo Unix.
Comenzaremos la instalación del sistema de control de versiones descargandolo. Dependiendo del sistema operativo que usemos, lo podremos hacer mediante linea
de comandos o ejecutable.
> [Mercurial para Windows](https://www.mercurial-scm.org/wiki/Download#Windows)
> [Mercurial para Mac OS X](https://www.mercurial-scm.org/downloads)
> [Mercurial para Linux](https://www.mercurial-scm.org/wiki/Download#Linux_.28.deb.29)

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
> [ui]
> \# Nombre que aparecerá en el commit
> username = Emma Paris <eparis@atlassian.com>

Guardamos el archivo y lo cerramos. Estaremos listos para empezar a usar Mercurial.

## Comandos básicos
Vamos ahora a ver las instrucciones básicas de Mercurial. Así pues, la directiva de Mercurial es ```hg``` por el simbolo quimico antes mencionado.
Por tanto, podemos crear un repositorio local:
> hg init (directorio del proyecto)
> cd (directorio del proyecto)
<br>

Añadiremos los archivos iniciales del proyecto y una vez hecho esto ejecutamos el siguiente comando:
> hg add (ficheros nuevos)
Una vez añadido los ficheros, podemos hacer el primer commit de nuestro repositorio: <br>
Con el parametro -m podremos añadir un comentario al commit. Es una buena práctica siempre añadir uno o dos de estos en cada commit.
> hg commit -m "Primer commit"
<br>

Mercurial admite el uso de [extensiones](https://www.mercurial-scm.org/wiki/UsingExtensions) para añadir diversas funcionalidades o mejoras: <br>
Podemos ver las extensiones disponibles con el siguinte commando
> hg help extensions
Ádemas, podemos ver información de una extensión en concreto de la siguiente forma:
> hg help nombre-extension
Por último, podemos habilitar y deshabilitar las extensiones:
> Las extensiones se deben habilitar, p.e. en .hg/hgrc:
> [extensions]
> foo =
> \# Podemos especificar la ruta concreta
> [extensions]
> myfeature = ~/.hgext/myfeature.py
<br>
> También se pueden deshabilitar de una en una:
> [extensions]
> \# disabling extension bar residing in /path/to/extension/bar.py
> bar = !/path/to/extension/bar.py
> \# ditto, but no path was supplied for extension baz
> baz = !
<br>

falta por meter: añadir una url de repositorio y cosas como crear ramas y push

## Nuestro proyecto con mercurial
## Subir a Github ?
## Alternativas Hg a Github ?
## Conclusión

