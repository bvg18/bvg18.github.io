# Mercurial, la alternativa a Git.

Metodologías Ágiles de Desarrollo de Software, Universidad de Alicante, curso 2020/21. <br>
Página web creada por Brais Valencia García. Github Developer Student Pack y Namecheap.

## Mercurial
El uso de git es casi unánime en el desarrollo de software, pero existen otras opciones igualmente validas como Baazar o Mercurial.
Es el caso de este último sistema de control de versiones del que hablaremos en esta página web. Más concretamente su uso en relación 
a la práctica 4, realizada de forma grupal, de la asignatura Metodologías de Desarrollo de Doftware de la Universidad de Alicante. <br>
Pongámonos manos a la obra, aprendamos sobre el proyecto Mercurial y su potencial.

## Historia
[Mercurial](https://www.mercurial-scm.org/) es un sistema de control de versiones distribuido. Su nombre le viene del termino 
[Hidrargiro](https://es.wikipedia.org/wiki/Mercurio_(elemento)). Termino usado en la literatura antigua para designar al 
Mercurio, elemento químico con el símbolo Hg y número atómico 80. <br>
El creador y desarrollador principal de Mercurial es Matt Mackall, que hizo pública la existencia de Mercurial el 19 de abril de 2005.
Con el objetivo de cubrir la necesidad existente de un sistema de control de versiones de software libre que sustituyera a la versión gratuita de BitKeeper.
Ya que esta iba a ser retirada por sus creadores Bitmover. Se había estado usando BitKeeper debido a los requisitos de control de versiones del proyecto del núcleo Linux. Mackall decidió escribir Mercurial como sustituto para usarlo con el núcleo Linux. El proyecto comenzó aproximadamente al mismo tiempo que otro denominado git, iniciado por el propio Linus Torvalds con objetivos similares. El proyecto Linux decidió usar Git en lugar de Mercurial, y por ello el proyecto de Mackall se quedaría en un segundo plano.
Siendo Git dueño y señor de los sistemas de control de versiones hasta la fecha, enero de 2021. <br>

Por otro lado, el proyecto Mercurial estaba desarrollado usando el lenguaje de programación [Python](https://www.python.org/) como lenguaje principal. Pero también 
hay partes, como la comparación binaria de [diff](https://es.wikipedia.org/wiki/Diff) desarrolladas en C.<br>
Las principales metas del desarrollo de Mercurial incluyen un gran rendimiento y escalabilidad; desarrollo completamente distribuido, sin necesidad de un servidor; gestión robusta de archivos tanto de texto como binarios; y capacidades avanzadas de ramificación e integración, todo ello manteniendo sencillez conceptual.
El código fuente de Mercurial se encuentra disponible bajo los términos de la licencia GNU GPL versión 2. <br>

## Instalación
Mercurial fue escrito originalmente para funcionar sobre GNU/Linux. Pero ha sido adaptado para poderse utilizar en Windows, Mac OS X y la mayoría de sistemas tipo Unix.
Comenzaremos la instalación del sistema de control de versiones descargandolo. Dependiendo del sistema operativo que usemos, lo podremos hacer mediante linea
de comandos o ejecutable.
> [Mercurial para Windows](https://www.mercurial-scm.org/wiki/Download#Windows) <br>
> [Mercurial para Mac OS X](https://www.mercurial-scm.org/downloads) <br>
> [Mercurial para Linux](https://www.mercurial-scm.org/wiki/Download#Linux_.28.deb.29) <br>

Para más detalles sobre la instalación o algún problema que pudiera surgir tenemos la [wikipedia de Mercurial](https://www.mercurial-scm.org/wiki/Download).

## Configuración
Toda la información relativa al control de versiones de un proyecto se guarda en el directorio raíz del proyecto, concretamente
en el subdirectorio ".hg". <br>
La configuración general para cada usuario se guarda en el archivo ".hgrc" y la configuración local para cada proyecto se guarda en
"<repo>/.hg/hgrc". <br>
  
Tendremos que comprobar si existe el archivo ".hgrc":
- En Windows ``` $ ls .hgrc ```.
- En Mac y Linux ``` $ ls ~/.hgrc```.

Si no existe el archivo lo ponemos crear con ``` $ touch ~/.hgrc ```. <br>

Por último, modificaremos el archivo ``` .hgrc ``` añadiendo un nombre de usuario y un correo electrónico. 
```
[ui] <br>
# Nombre que aparecerá en el commit 
username = Emma Paris <eparis@atlassian.com> 
```
Guardamos el archivo y lo cerramos. Estaremos listos para empezar a usar Mercurial.

## Comandos básicos
Vamos ahora a ver las instrucciones básicas de Mercurial. Así pues, la directiva de Mercurial es ```hg``` por el símbolo químico antes mencionado. <br>
**Por tanto, podemos crear un repositorio local:** <br>
```
hg init (directorio del proyecto)
cd (directorio del proyecto)
```

**Añadiremos los archivos iniciales del proyecto y una vez hecho esto ejecutamos el siguiente comando:**
```
hg add (ficheros nuevos) 
O también podemos añadir todos los ficheros nuevos a la vez con:
hg add .
```
**Una vez añadido los ficheros, podemos hacer el primer commit de nuestro repositorio:** <br>
Con el parametro -m podremos añadir un comentario al commit. Es una buena práctica siempre añadir uno o dos de estos en cada commit. <br>
```
hg commit -m "Primer commit"
```
**Podemos ver el estado de nuestro repositorio con el siguiente comando:** <br>
```
hg status
```
**El uso de ramas es algo fundamental dentro de los sistemas de control de versiones.** <br>
Por ello, hg dispone al igual que git de una serie de directivas para hacernos la vida más fácil a la hora de programar. Tanto de forma individual como en grupo.<br>
**Rama por defecto en Mercurial** <br>
Default es el nombre que tiene la rama que crea Mercurial al crear un proyecto desde cero. <br>
**Como podemos crear nuestras propias ramas:**
```
hg branch nombre-de-la-rama
```
**Una vez creadas ramas para trabajar, podemos ver todas ellas en una lista de esta forma:**
```
hg branches
```
**Ádemas, si necesitamos cambiar entre ramas podemos hacerlo con la directiva de hg:**
```
hg update nombre-de-la-rama
```

**Otra directiva de Mercurial muy útil para el día a día es bisect:** <br>
Presente también en git, no es más que una busqueda binaria entre los commits de nuestro proyecto. <br>
¿Qué conseguimos con esta herramienta? Detectar o buscar un posible error en un commit intermedio. <br>
¿Cómo conseguimos utilizar esta herramienta de forma correcta? Es muy sencillo su uso, unicamente debemos decirle a bisect que el commit en el que estamos ahora tiene un error.
```
hg bisect --reset
hg bisect --bad
```
Acto seguido, nos vamos a un commit antiguo, uno que sepamos que funciona a la perfección o que no tiene ningún error.
```
hg update -r 23
hg bisect --good 23
```
Una vez le indicamos ambos commits a bisect, nos cálcula e indica cual es el commit intermedio y por tanto el siguiente a revisar.
Una vez revisado este commit, tenemos tres opciones, o que sea justamente el commit del error, que sea un commit "bueno" o que siga existiendo el error pero no causado por el commit. Seguiremos usando bisect de la misma manera hasta dar con el fallo dentro del código. <br>
Parece una trivialidad de herramienta. Pero cuando existen miles de commits dentro de un poryecto se vuelve una herramienta muy útil.


**Mercurial admite el uso de [extensiones](https://www.mercurial-scm.org/wiki/UsingExtensions) para añadir diversas funcionalidades o mejoras:** <br>
Podemos ver las extensiones disponibles con el siguiente commando:
```
hg help extensions
```
**Ádemas, podemos ver información de una extensión en concreto de la siguiente forma:** <br>
```
hg help nombre-extension
```
**Por último, podemos habilitar y deshabilitar las extensiones:** <br>
Las extensiones se deben **habilitar**, p.e. en ```.hg/hgrc```:
```
[extensions] 
foo =
# Podemos especificar la ruta concretan 
[extensions] 
myfeature = ~/.hgext/myfeature.pyb 
```

También se pueden **deshabilitar** de una en una: 
```
[extensions] 
# disabling extension bar residing in /path/to/extension/bar.py 
bar = !/path/to/extension/bar.py 
# ditto, but no path was supplied for extension baz
baz = ! 
```
**Existen cantidad de extensiones desarrolladas por terceros que podemos incluir en nuestro proyecto Mercurial**
En este [enlace](https://www.mercurial-scm.org/wiki/UsingExtensions#Extensions_provided_by_others) tenemos una lista de algunas de ellas.

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

**Hacer efectivos los cambios locales de nuestro repositorio de forma remota:**
Hasta ahora hemos estado trabajando de forma local. Siendo nosotros solos los desarrolladores del poryecto y guardando todo nuestro proyecto en nuestra máquina.
Para subir los cambios generados disponemos, al igual que en git, de la directiva siguiente:
```
hg push
```
Conseguiremos guardar de forma remota nuestro proyecto, sí lo creamos localmente; como también los cambios que realicemos. <br>
Más adelante veremos una plataforma similar a GitHub para tener nuestro repositorio remoto. Y como configurarlo todo. 

**Descargar los cambios remotos a nuestro poryecto local:**
Es la acción inversa a la vista arriba. Aquí descargaremos los cambios para igualar el proyecto y las posibles ramas, con el objetivo de tener siempre la última versión de los ficheros y mantener el poryecto actualizado. ¿Cómo logramos esto? Utilizando el comando siguiente como siempre:
```
hg pull
```
Al igual que en git y github, debemos tener cuidado y usar dicho comando diariamente en nuestra rama principal. Al igual que si desarrollamos código en una rama que no es nuestra para que las líneas de código esten actualizadas. Con esta buena práctica, conseguiremos reducir al mínimo posibles errores en el desarrollo de código.


**Los conflictos se marcan igual que en otros scv:**
```
<<<<<<< /tmp/conflict/crab.cpp
void function() {
=======
int function() {
>>>>>>> /tmp/crab.cpp
```

## Nuestro proyecto con mercurial
Vistos algunos de los comandos de los que disponemos al usar el proyecto Mercurial, vamos a ver como podemos aplicarlo a la práctica 4 de la asignatura.
Podemos realizar varias configuraciones distintas perfectamente validas para el trabajado y el desarrollo diario.
La forma de trabajar que vamos a ver aquí es una totalmente distinta a la usada en la asignatura, ya aue no usaremos ni Git ni GitHub. 
Al fin y al cabo es el objetivo de esta página web. 

¿Y cómo vamos a funcionar? <br>
Como hemos estado explicando, vamos a usar Mercurial como sistema de control de versiones. Pero de momento solo tenemos un proyecto local. 
meter algo de codigo donde crea un priyecto y le añade los archivos de la practica 4

¿Y cómo guardamos de forma remota nuestro repositorio?
En la práctica hemos usado GitHub como servidor, en donde todos los componentes del grupo subiamos nuestra copia e ibamos guardando lo desarrollado.
Pero GitHub no es único, hay cantidad de servicios que nos permiten trabajar de forma parecida. 
Portales para subir código creados especificamente para Mercurial y para trabajar de forma sencilla con hg. <br>
La propia página oficial de mercurial nos proporciona una lista de ellas. [Mercurial Hosting](https://www.mercurial-scm.org/wiki/MercurialHosting). <br>
Aquí vamos a ver [Heptapod](https://about.heptapod.host/). Necesitamos crearnos una cuenta en Clever Cloud. En este caso, podemos acceder usando nuestra cuenta 
GitHub y darle permisos o bien crearnos una y no depender del sistema de control de versiones. [Enlace](https://api.clever-cloud.com/v2/sessions/signup). 
Autorizamos a la aplicación y aceptamos los terminos y concidiciones. <br>
Una vez hemos creado nuestra cuenta, volvemos [aquí](https://heptapod.host/users/sign_in) y conectamos usando nuestra cuenta de GitHub. Marcaremos las dos casillas que aparecen.
<br>
Dentro de la página principal de Heptapod, podemos crear un nuevo proyecto o ver los proyectos de otras personas. 
Para mayor seguridad, podemos añadir una configuración ssh. Añadiendo un nivel de seguridad extra vinculando mediante una contraseña ssh tu máquina de trabajo habitual 
con la página web Heptapod. Se configura de forma sencilla siguendo los pasos que indica la propia página web. <br>

Tal y como tenemos en GitHub, Heptapod dispone de la creación y gestión de Issues; o de la creación y gestión de Pull Request entre otras funcionalidades.
Dentro de la aplicación, disponemos también de una herramienta [ToDoList](https://heptapod.host/dashboard/todos) muy parecida a la idea original 
de la práctica 4 salvando las distancias. <br>

Crearemos un nuevo proyecto personal. Tenemos tres opciones a escoger: crear un proyecto en blanco, ideal para empezar un proyecto vacío; crear un proyecto usando 
una plantilla con ficheros iniciales ya creados, ideal para guardar una estructura dada por un lenguaje de porgramacion en concreto. La última y la que nos interesa en este caso es poder importar tus repositorios directamente de GitHub o algunos de los sistemas de control de versiones más importantes.  <br>
Escogemos esta última opción, y le damos click a GitHub. Por seguridad necesitamos escribir un token personal que nos proporciona GitHub para este tipo de trámites. Podemos obtener el token desde la página de GitHub de esta sencilla [forma](https://docs.github.com/es/github/authenticating-to-github/creating-a-personal-access-token). Una vez obtenemos el toquen, volvemos a la página de Heptapod en la que estabamos y autenticamos usando el token mencionado. <br>
Se nos listaran todos los repositorios disponibles, en nuestro caso escogemos el repositorio "mads-ua-20-21/todolist-final-equipo-08" y le damos a importar.
Puede ser que el nombre del nuevo repositorio en Heptapod no sea válido, deberemos cambiarlo por otro. <br>

Una vez creado el repositorio, podemos irnos a linea de comandos y escribir:
```
hg clone https://foss.heptapod.net/[nombre-de-usuario]/[nombre-del-repositorio]
```

Podemos comenzar a desarrollar trabajando con diferentes ramas como hemos visto antes. <br>
Mencionar que Heptapod, nos permite también crear grupos de trabajo como los vistos y usados en GitHub. De esta forma el repositorio se compartirá entre los miembros de dicho grupo. <br>

Cabe destacar, que después de haber probado las diferentes formas de crear un repositorio en Heptapod, mi recomendación es la de crear un proyecto vacío y depués añadir los ficheros necesarios uno mismo. Ya que nos evitamos cantidad de permisos y burocracia entre las distintas plataformas. Ádemas, gozaremos de un control total sobre nuestro repositorio. Al contrario de hacerlo de la forma fácil y automatica. Buena para principiantes en el desarrollo de código o personas que no quieran entrar en detalles. <br>

En el uso diario, existen pocas diferencia entre estos servidores de código remoto "adaptados" a Mercurial y el visto en la asignatura, GitHub.

## comentar hggit 
## Conclusión
