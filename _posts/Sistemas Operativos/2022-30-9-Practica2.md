# 📓 Practica 2

El objetivo de esta práctica es que el alumno comprenda los aspectos principales acerca de la estructura del sistema Operativo GNU/Linux en lo que respecta a procesos, usuarios, filesystems,
permisos, etc


- [1) Editor de textos](#1-editor-de-textos)
- [2) Proceso de Arranque SystemV](#2-proceso-de-arranque-systemv)
- [3) Usuarios](#3-usuarios)
- [4) FileSystem](#4-filesystem)
- [5) Procesos](#5-procesos)
- [6) Otros comandos de Linux](#6-otros-comandos-de-linux-indique-funcionalidad-y-parámetros)
- [7) Indique qué acción realiza cada uno de los comandos...](#7-ejercicio)
- [8) Indique qué comando sería necesario ejecutar para realizar cada una de las siguientes acciones](#8-indique-qué-comando-sería-necesario-ejecutar-para-realizar-cada-una-de-las-siguientes-acciones)
- [9) Indique qué comando sería necesario ejecutar para realizar cada una de las siguientes acciones](#9-indique-qué-comando-sería-necesario-ejecutar-para-realizar-cada-una-de-las-siguientes-acciones)
- [10) Indique qué comando sería necesario ejecutar para realizar cada una de las siguientes acciones](#10-indique-qué-comando-sería-necesario-ejecutar-para-realizar-cada-una-de-las-siguientes-acciones)
- [11) Indique qué acción realiza cada uno de los comandos indicados a continuación....](#11-ejercicio)
- [12) Cree una estructura desde el directorio /home que incluya varios directorios....](#12-ejercicio)
- [13) Indique qué comando/s es necesario para realizar cada una de las acciones de la siguiente secuencia de paso](#13-indique-qué-comandos-es-necesario-para-realizar-cada-una-de-las-acciones-de-la-siguiente-secuencia-de-pasos-considerando-su-orden-de-aparición)

## `1)` Editor de textos:
`(a)` Nombre al menos 3 editores de texto que puede utilizar desde la línea de comandos.

-  **Vim:** Es un editor de texto que rompe las bolas pero aprendes
- **GNU Emacs:** La misma basura que vim pero con calculadora y administrador de archivos
- **mcedit:** Te permite navegar entre los ficheros con una interfaz.

`(b)` ¿En qué se diferencia un editor de texto de los comandos cat, more o less? Enumere los modos de operación que posee el editor de textos vi.\
Estos comandos si bien son muy utiles y simples, carecen de algunas funcionalidades, como por ejemplo, abrir un archivo en modo lectura asi no nos tenemos que preocupar de modificarlo.

- [Fuente](https://victorhckinthefreeworld.com/2020/01/02/ni-cat-ni-more-ni-less-usa-vim-para-ver-el-contenido-de-un-archivo-de-texto-en-la-consola/)

`(c)` Nombre los comandos más comunes que se le pueden enviar al editor de textos vi
- [Comandos basicos](https://docs.oracle.com/cd/E19620-01/805-7644/6j76klopr/index.html)

## `2)` Proceso de Arranque SystemV:
`(a)` Enumere los pasos del proceso de inicio de un sistema GNU/Linux, desde que se prende la PC hasta que se logra obtener el login en el sistema.

- Se empieza a ejecutar el código del BIOS
- El BIOS ejecuta el POST
- El BIOS lee el sector de arranque (MBR)
- Se carga el gestor de arranque (MBC)
- El bootloader carga el kernel y el initrd
- Se monta el initrd como sistema de archivos raíz y se inicializan componentes esenciales (ej.: scheduler)
- El Kernel ejecuta el proceso init y se desmonta el initrd
- Se lee el /etc/inittab
- Se ejecutan los scripts apuntados por el runlevel 1
- El final del runlevel 1 le indica que vaya al runlevel por defecto
- Se ejecutan los scripts apuntados por el runlevel por defecto
- El sistema est´a listo para usarse

`(b)` Proceso INIT. ¿Quién lo ejecuta? ¿Cuál es su objetivo?
- Su función es cargar todos los subprocesos necesarios para el correcto funcionamiento del SO
- El proceso init posee el PID 1 y se encuentra en /sbin/init
- En SysV se lo configura a traves del archivo /etc/inittab
- No tiene padre y es el padre de todos los procesos (pstree)
- Es el encargado de montar los filesystems y de hacer
disponible los dem´as dispositivos

`(c)` Ejecute el comando pstree. ¿Qué es lo que se puede observar a partir de la ejecución de este comando?\
El programa pstree facilita información sobre la finalización de una serie de procesos relacionados entre sí, esto es, todos los descendientes de un proceso particular. El programa deja claro desde un principio que proceso es el primario y cuales son los secundarios.

`(d)` RunLevels. ¿Qué son? ¿Cuál es su objetivo?
- Es el modo en que arranca Linux (3 en Redhat, 2 en Debian)
- El proceso de arranque lo dividimos en niveles
- Cada uno es responsable de levantar (iniciar) o bajar (parar)
una serie de servicios

`(e)` ¿A qué hace referencia cada nivel de ejecución según el estándar? ¿Dónde se define qué Runlevel ejecutar al iniciar el sistema operativo? ¿Todas las distribuciones respetan estos estándares? [Fuente](https://www.factor.mx/portal/base-de-conocimiento/niveles-de-ejecucion/)

- **0** Indica halt o apagado de la máquina.
- **1** Indica monousuario.
- **2** Indica modo multiusuario sin soporte de red.
- **3** Indica modo multiusuario completo con soporte de red.
- **4** No usado, con esta opción el administrador puede personalizar el inicio para cargar algún servicio.
- **5** Indica multiusuario completo con inicio gráfico (X11)
- **6** Indica shutdown y reboot: Se apaga inmediatamente la máquina para reinicio.

Un administrador (root) puede editar el archivo /etc/inittab como mejor convenga al usuario, sin embargo también tiene el poder de establecerlo en 0 o en 6. Si se establece en 6, algo que hice como experimento en mi Mandriva, la próxima vez que la máquina se encienda, se leerá el modo 6, shutdown y reboot, y se hará exactamente eso. 

`(f)` Archivo /etc/inittab. ¿Cuál es su finalidad? ¿Qué tipo de información se almacena en el? ¿Cuál es la estructura de la información que en él se almacena?\
Este programa es el encargado de lanzar los scripts de inicialización del sistema y de modificar el sistema operativo de su estado inicial de arranque al estado estándar multiusuario. También define los intérpretes de órdenes login: de todos los dispositivos tty del sistema y especifica otras características del arranque y apagado.

- [Fuente](https://www.ibiblio.org/pub/linux/docs/LuCaS/Manuales-LuCAS/LIPP2/lipp-2.0-beta-html/node285.html)

`(g)` Suponga que se encuentra en el runlevel \<X>. Indique qué comando(s) ejecutaría para cambiar al runlevel \<Y>. ¿Este cambio es permanente? ¿Por qué?\
No es permanente ya que cuando reinicias el dispositivo, vulven a ejecutarse las runlevels de forma normal. [telinit](https://baulderasec.wordpress.com/analisis-software/linux/5-comenzar-con-linux-y-editar-ficheros/5-7-1-comprobar-el-modo-de-ejecucion/5-7-2-saber-el-modo-de-ejecucion-actual/5-7-2-1-cambiar-los-modos-de-ejecucion-con-init-o-telinit/)

```powershell
ls /etc/rc0.d
sudo runlevel
sudo telinit 2
```


`(h)` Scripts RC. ¿Cuál es su finalidad? ¿Dónde se almacenan? Cuando un sistema GNU/Linux arranca o se detiene se ejecutan scripts, indique cómo determina qué script ejecutar ante cada acción. ¿Existe un orden para llamarlos? Justifique.\
Cuando init ingresa a un nivel de ejecución, llama al script rc con un argumento numérico que especifica el nivel de ejecución al que ir. rc luego inicia y detiene los servicios en el sistema según sea necesario para llevar el sistema a ese nivel de ejecución

- [Fuente](https://geekpeach.net/es/comprender-los-scripts-rc-en-linux)

`(i)` ¿Qué es insserv? ¿Para qué se utiliza? ¿Qué ventajas provee respecto de un arranque tradicional?\
El programa insserv es utilizado por el sistema de inicio «init» estándar basado en SysV. Actualiza el orden de los enlaces simbólicos en /etc/rc?.d/ basándose en las dependencias especificadas por las cabeceras LSB en los propios scripts init.d.

Estas relaciones declaradas entre scripts permiten optimizar la secuencia de arranque para el conjunto de paquetes instalado actualmente, a la vez que detectan y rechazan los bucles de dependencia.
- [Fuente](https://packages.debian.org/sid/insserv)

`(j)` ¿Cómo maneja Upstart el proceso de arranque del sistema?\
Upstart es un reemplazo basado en eventos para el daemon /sbin/init que maneja el inicio de tareas y servicios durante el arranque, los detiene durante el apagado y los supervisa mientras el sistema se está ejecutando.

No entiendo una mrd, despues lo reviso.

- [Fuente](https://esgeeks.com/systemv-upstart-systemd-linux/#:~:text=Qu%C3%A9%20es%20Upstart%3F-,Upstart%20es%20un%20reemplazo%20basado%20en%20eventos%20para%20el%20daemon,el%20sistema%20se%20est%C3%A1%20ejecutando.)

`(k)` Cite las principales diferencias entre SystemV y Upstart.
[Fuente](https://esgeeks.com/systemv-upstart-systemd-linux/#:~:text=Upstart%20%3A%20Upstart%20es%20un%20reemplazo,los%20sistemas%20init%20tradicionales%20SysV.) Que paja escribir

`(l)` Qué reemplaza a los scripts rc de SystemV en Upstart? ¿En que ubicación del filesystem se encuentran?\
Los scripts son reemplazados con jobs. Cada job es definido en el /etc/init (.conf)

`(m)` Dado el siguiente job de upstart perteneciente al servicio de base de datos del mysql indique a qué hace referencia cada línea del mismo:

```powershell
# MySQL Servise
description "MySQL Server " {Descripcion}
autor "info autor" {Autor}
start on ( net − device − up {Iniciar base de datos}
        and local −filesystems   {}
        and runlevel [2345])
stop on runlevel [016]
[...]
exec / usr / sbin /mysqld
[...]
```

`(n)` ¿Qué es sytemd?\
SystemD es el administrador de servicios y sistemas en Linux, y la estandarización de la mayoría de distribuciones de Debian y Red Hat. SystemD fue desarrollado con el objetivo de encargarse de arrancar todo lo que está por debajo del Kernel, permitiendo ejecutar varios procesos de manera simultánea. Además, permite un seguimiento de procesos a través del uso de grupos de control del sistema operativo Linux.

- Es un sistema que centraliza la administracion de demonios y librerias del sistema
- Mejora el paralelismo de booteo
- Puede ser controlado por systemctl
- Compatible con SysV → si es llamado como init
- El demonio systemd reemplaza al proceso init → este pasa a terner PID 1
- Los runlevels son reemplazados por targets
- Al igual que con Upstart el archivo /etc/inittab no existe m´as

- [Fuente](https://keepcoding.io/blog/que-es-systemd/)

`(ñ)` ¿A qué hace referencia el concepto de activación de socket en systemd?\
Es un mecanismo de iniciación bajo demanda → podemos ofrecer una variedad de servicios sin que realmente esten iniciados
- Cuando el sockect recibe una conexión spawnea el servicio y le
pasa el socket
- No hay necesidad de definir dependencias entre servicios → se
inician todos los sockets en primer medida

`(o)` ¿A qué hace referencia el concepto de cgroup?\
Los cgroups o grupos de control, son una característica del kernel Linux que permite que los procesos se organicen en grupos jerárquicos con el fin de limitar y monitorear el uso de varios tipos de recursos. Con cgroups cada proceso corre en su propio espacio del kernel y de la memoria. Cuando se tienen la necesidad, un administrador puede configurar fácilmente un cgroup para limitar los recursos que puede utilizar un proceso.

- [Fuente](https://clibre.io/blog/por-secciones/hardening/item/425-cgroups-grupos-de-control-en-gnu-linux)


## `3)` Usuarios
`(a)` ¿Qué archivos son utilizados en un sistema GNU/Linux para guardar la información de los usuarios?\
Sistema de archivos Ext2, ext3 y ext4: Así como Apple y Microsoft tienen sus propios sistemas, estos tres (cada uno evolución del anterior) son los utilizados por las distribuciones GNU/Linux

`(b)` ¿A qué hacen referencia las siglas UID y GID? ¿Pueden coexistir UIDs iguales en un sistema GNU/Linux? Justifique.\
Los sistemas operativos Linux y Unix utilizan el UID (User ID o ID de usuario) para identificar al usuario particular. El GID (Group ID o ID de grupo) se utiliza para identificar a un grupo. Supongo que no podrian existir dos iguales ya que no los podrias distinguir.

- [Fuente](https://techlandia.com/13112435/como-encontrar-el-uid-y-el-gid)

`(c)` ¿Qué es el usuario root? ¿Puede existir más de un usuario con este perfil en GNU/Linux? ¿Cuál es la UID del root?.\
En Linux el usuario root es aquel que tiene todos los permisos en el sistema operativo, es decir, es el súper administrador. Puede acceder a cualquier archivo y también ejecutar cualquier comando, incluidos los que nunca deberías ejecutar.
Si, podes tenes los usuarios root que quieras. [Fuente](https://www.xn--linuxenespaol-skb.com/tutoriales/crear-usuario-con-privilegios-de-root-en-linux/)

- En Linux, la cuenta de superusuario es root , que siempre tiene el UID 0

`(d)` Agregue un nuevo usuario llamado iso2017 a su instalación de GNU/Linux, especifique que su home sea creada en /home/iso_2017, y hágalo miembro del grupo catedra (si no existe, deberá crearlo). Luego, sin iniciar sesión como este usuario cree un archivo en su home personal que le pertenezca. Luego de todo esto, borre el usuario y verifique que no queden registros de él en los archivos de información de los usuarios y grupos.

- `sudo adduser iso2022` creo un usuario y en home le agrego /home/ (contra = nombre para pruebas)
- `sudo gropadd catedra` creo un grupo 
- `sudo usermod -a -G catedra iso2022`
- `id -nG iso2022` menciona los grupos a los que pertenece mi usuario
- `sudo login iso2022` entro como el usuario
- `cd ..` para ir a la home personal y crear un archivo (creo)
- `sudo userdel iso2022` lo elimina pero aun tenemos todos los archivos creados por este

`(e)` Investigue la funcionalidad y parámetros de los siguientes comandos:
- **useradd nombre ó adduser nombre:** Crea un nuevo usuario
- **usermod nombre:** nos permite modificar todos los parámetros de la cuenta de un usuario creado con anterioridad.
- **userdel nombre:** Elimina un usuario
- **su:** entrar al super usuario (tenes los permisos de TODO)
- **groupadd nombre:** te deja crear un grupo
- **who:** Verifiqua los usuarios conectado al sistema
- **groupdel nombre:** elimina un grupo
- **passwd:** de deja cambiar la constraseña del usuario actual

## `4)` FileSystem:
`(a)` ¿Cómo son definidos los permisos sobre archivos en un sistema GNU/Linux?\
**Los permisos están divididos en tres tipos: lectura, escritura y ejecución**
. Estos permisos pueden ser fijados para tres clases de usuarios: el propietario del archivo o directorio, los integrantes del grupo al que pertenece y todos los demás usuarios.

`(b)` Investigue la funcionalidad y parámetros de los siguientes comandos relacionados con los permisos en GNU/Linux:
- **chmod:** nos permite gestionar permisos
- **chown:** permite cambiar el propietario de un archivo o directorio en sistemas
- **chgrp:** nos permite cambiar el grupo al que pertenece un archivo

`(c)` Al utilizar el comando chmod generalmente se utiliza una notación octal asociada para definir permisos. ¿Qué significa esto? ¿A qué hace referencia cada valor?\
Existen 3 tipos de permisos y se basan en una notacion octal para referenciar a cada uno:

| Permiso  | Valor | Octal |
| ------------- | ------------- | ------------- |
| Lectura  | R  | 4 |
| Escritura  | W  | 2 |
| Ejecucion  | X  | 1 |

`(d)` ¿Existe la posibilidad de que algún usuario del sistema pueda acceder a determinado archivo para el cual no posee permisos? Nombrelo, y realice las pruebas correspondientes.\
El usuario root puede acceder a determinados archivos sin necesidad de poseer permisos o con manejo de interrupciones.

`(e)` Explique los conceptos de “full path name” y “relative path name”. De ejemplos claros de cada uno de ellos.\
full path name es la ruta completa a ese archivo o carpeta desde el directorio / del sistema de archivos. ejemplo `/home/your_username/my_script`

relative path name : Rastrea la ruta desde el directorio actual a través de su padre o sus subdirectorios y archivos. ..\Documents

`(f)` ¿Con qué comando puede determinar en qué directorio se encuentra actualmente? ¿Existe alguna forma de ingresar a su directorio personal sin necesidad de escribir todo el path completo? ¿Podría utilizar la misma idea para acceder a otros directorios? ¿Cómo? Explique con un ejemplo.\
Con el comando pwd podemos saber el directorio actual.

con cd /user volvemos al directorio personal, aunque con solo poner `cd`o `cd ~` ya cumplimos esa función.

Se podría acceder a diferentes directorios gracias la ubicación relativa o atajos ya prestablecidos como `cd ..` para volver al directorio anterior sin necesidad de poner ningún atajo


`(g)` Investigue la funcionalidad y parámetros de los siguientes comandos relacionados con el uso del FileSystem:

- **cd:** Nos permite meternos en un directorio interno
- **umount:** permite eliminar un sistema de archivos remoto que esté montando en la actualidad (no usar xd)
- **mkdir:** Cree una carpeta
- **du:** para ver el tamaño de ficheros y carpetas
- **rmdir:** El comando linux rmdir sirve para borrar directorios
- **df:** Informa la cantidad de espacio libre en disco
- **mount:** Se utiliza para montar dispositivos y particiones para su uso por el sistema operativo (se instala con **sudo apt install nfs-common**)
- **ln:** crear un enlace simbólico al fichero o directorio (como un acceso directo)
- **ls:** Lista el contenido del directorio actual
- **pwd:** Visualiza la ruta donde estoy situado
- **cp:** sirve para copiar archivos y directorios dentro del sistema de archivos
- **mv:** se utiliza para mover o renombrar los archivos y directorios

## `5)` Procesos

`(a)` ¿Qué es un proceso? ¿A que hacen referencia las siglas PID y PPID? ¿Todos los procesos tienen estos atributos en GNU/Linux? Justifique. Indique qué otros atributos tiene un proceso.\
Es un programa en ejecución Para nosotros serán sinónimos: tarea,
job y proceso.

PID significa ID de proceso, que significa Número de identificación para el proceso que se está ejecutando actualmente en la memoria. 2. PPID son las siglas de Parent Process ID, lo que significa que Parent Process es el responsable de crear el proceso actual (Child Process). A través del proceso principal, se creará el proceso secundario.

`(b)` Indique qué comandos se podrían utilizar para ver qué procesos están en ejecución en un sistema GNU/Linux.\
El comando `ps` posee algunas opciones para mostrar los procesos en ejecucion

Algunas opciones:

- e o : muestra todos los procesos ax
- u (o  o ) *usuario*: muestra los procesos de un usuario U
    - -user
- u: salida en formato usuario
- j: salida en formato *job* (muestra PID, PPID, etc.)
- f o : salida en formato largo l
- f: muestra un árbol con la jerarquía de procesos
- k (o ) *campo*: ordena la salida por algún campo (p.e. )
    - -sort
    
    ps uxak rss
    
- o (o  o ) *formato*: permite definir el formato de salida
    
    o -format
    
    ps -o ruser,pid,comm=Comando

`(c)` ¿Qué significa que un proceso se está ejecutando en Background? ¿Y en Foreground?\
Si se ejecuta en background hace referencia a **todos aquellos procesos o rutinas de ejecución que se realizan en segundo plano**

**Si se muestra la ejecución del comando dentro de la terminal** se dice que está en el foreground (primer plano).

`(d)` ¿Cómo puedo hacer para ejecutar un proceso en Background? ¿Como puedo hacer para pasar un proceso de background a foreground y viceversa?\
Para colocar un proceso en segundo plano durante su ejecución, se debe utilizar la combinación teclas: Ctrl + Z. Para volver a colocar un proceso en primer plano, se debe ingresar el comando “fg”. Comando para ver procesos que se estén ejecutando: “ps” o con modificador para ver tambien procesos del sistema: “ps ax”.

`(e)` Pipe ( | ). ¿Cuál es su finalidad? Cite ejemplos de su utilización.\
Linux Pipes **te permiten procesar secuencialmente una serie de comandos referentes a un conjunto de datos, o mover eficazmente los datos de un lado a otro entre comandos**, por ejemplo 

ls | more
• Se ejecuta el comando ls y la salida del mismo, es enviada
como entrada del comanda more

`(f)` Redirección. ¿Qué tipo de redirecciones existen? ¿Cuál es su finalidad? Cite ejemplos de utilización.\
Las **redirecciones** consisten en trasladar información de un tipo a otro

Hay 2 tipos de redirecciones 

- Al utilizar redirecciones mediante > (destructiva):
    - Si el archivo de destino no existe, se lo crea
    - Si el archivo existe, se lo trunca y se escribe el nuevo contenido
- Al utilizar redirecciones mediante >> (no destructiva):
    - Si el archivo de destino no existe, se lo crea
    - Si el archivo existe, se agrega la información al final

EJEMPLOS

>  Redirecciona **stdout** hacía un archivo. Lo crea si no existe, si existe lo sobreescribe.
```
ls -l > lista.txt
```

>> (La salida del comando se envía a un archivo en vez de la terminal.)

Redirecciona **stdout** hacía un archivo. Lo crea si no existe, si existe concatena la salida al final de este.

```
ps -ef >> processos.txt
```
(Concatena al archivo procesos.txt la salida del comando.)

`(g)` Comando kill. ¿Cuál es su funcionalidad? Cite ejemplos.\
Sirve para cancelar procesos
kill es un **comando utilizado para enviar mensajes sencillos a los  ejecutándose en el sistema** . Por defecto el mensaje que se envía es la señal de terminación (SIGTERM), que solicita al proceso limpiar su estado y salir.

`kill -l`

Este comando mostrará una página con las diferentes señales del comando kill, con sus nombres y números correspondientes. Si bien hay varias señales disponibles, en la mayoría de los casos se usa SIGKILL (9) y SIGTERM (15).

ejemplo 

`kill 63772` elimina el proceso con id 63772


`(h)` Investigue la funcionalidad y parámetros de los siguientes comandos relacionados con el manejo de procesos en GNU/Linux. Además, compárelos entre ellos:
- **ps:** Muestra información de los procesos activos.
- **kill:** Sirve para cancelar procesos
- **pstree:** muestra un árbol de procesos.
- **killall:** nos permite matar un proceso escribiendo su nombre
- **top:** Sirve para ver los procesos de ejecución del sistema (y más cosas) en tiempo real
- **nice:** Ejecuta un comando con una prioridad determinada, o modifica la prioridad a de un proceso

## `6)` Otros comandos de Linux (Indique funcionalidad y parámetros)

`(a)` ¿A qué hace referencia el concepto de empaquetar archivos en GNU/Linux?\
`(b)` Seleccione 4 archivos dentro de algún directorio al que tenga permiso y sume el tamaño de cada uno de estos archivos. Cree un archivo empaquetado conteniendo estos 4 archivos y compare los tamaños de los mismos. ¿Qué característica nota?\
`(c)` ¿Qué acciones debe llevar a cabo para comprimir 4 archivos en uno solo? Indique la secuencia de comandos ejecutados.\
`(d)` ¿Pueden comprimirse un conjunto de archivos utilizando un único comando?\
`(e)` Investigue la funcionalidad de los siguientes comandos:
- **tar:**
- **grep:**
- **gzip:**
- **zgrep:**
- **wc:**

## `7)` Ejercicio

Enunciado: Indique qué acción realiza cada uno de los comandos indicados a continuación considerando
su orden. Suponga que se ejecutan desde un usuario que no es root ni pertenece al grupo
de root. (Asuma que se encuentra posicionado en el directorio de trabajo del usuario con el
que se logueó). En caso de no poder ejecutarse el comando, indique la razón

```powershell
l s −l > prueba {No se puede acceder a pruebas pq no existe el fichero}                         
ps > PRUEBA   {crea el archivo prueba con lo obtenido de ps}
chmod 710 prueba  {no existe el archivo prueba dado que se creo en mayusculas}
chown root : root PRUEBA {No poseo los permisos para modificar eso}
chmod 777 PRUEBA  {Concedo todos los permisos tanto al dueño,al grupo y al usuario}
chmod 700 / etc / passwd {No poseo los permisos para modificar eso}
passwd root {No se puede ver la contraseña del root}
rm PRUEBA {elimina el archivo PRUEBA}
man / etc / shadow {nos muestra la documentacion del comando shadow}
find / −name ∗ .conf {Orden no encontrada}
usermod root −d /home/ newroot −L {Orden no encontrada}
cd / root {permiso denegado}
rm ∗ {No se pueden borrar los directorios}
cd / etc {Nos direcciona a la carpeta /etc }
cp ∗ /home −R {no se pueden copiar los directorios}
shutdown {apaga el sistema}
```

## `8)` Indique qué comando sería necesario ejecutar para realizar cada una de las siguientes acciones:

`(a)` Terminar el proceso con PID 23.\
`kill 23`

`(b)` Terminar el proceso llamado init. ¿Qué resultados obtuvo?\
No esta permitido

`(c)` Buscar todos los archivos de usuarios en los que su nombre contiene la cadena “.conf”\
`grep -iRl .conf /home/user`

`(d)` Guardar una lista de procesos en ejecución el archivo /home/\<su nombre de usuario>/procesos\
`ps > /home/user/procesos`

`(e)` Cambiar los permisos del archivo /home/\<su nombre de usuario>/xxxx a:
- **Usuario:** Lectura, escritura, ejecución
- **Grupo:** Lectura, ejecución
- **Otros:** ejecución
`chmod 751 /home/nomUsuario/xxxx`

`(f)` Cambiar los permisos del archivo /home/<su nombre de usuario>/yyyy a:
- **Usuario:** Lectura, escritura.
- **Grupo:** Lectura, ejecución
- **Otros:** Ninguno

`chmod 650 /home/user/yyyy`

`(g)` Borrar todos los archivos del directorio /tmp\
```powershell
cd /tmp
rm *
```

`(h)` Cambiar el propietario del archivo /opt/isodata al usuario iso2010\
`chown iso2010 /opt/isodata`

`(i)` Guardar en el archivo /home/\<su nombre de usuario>/donde el directorio donde me encuentro en este momento, en caso de que el archivo exista no se debe eliminar su contenido anterior.\
`pwd >> /home/user/donde`

## `9)` Indique qué comando sería necesario ejecutar para realizar cada una de las siguientes acciones

`(a)` Ingrese al sistema como usuario “root”\
`(b)` Cree un usuario. Elija como nombre, por convención, la primer letra de su nombre seguida de su apellido. Asígnele una contraseña de acceso.\
`(c)` ¿Qué archivos fueron modificados luego de crear el usuario y qué directorios se crearon?\
`(d)` Crear un directorio en /tmp llamado cursada2017\
`(e)` Copiar todos los archivos de /var/log al directorio antes creado.\
`(f)` Para el directorio antes creado (y los archivos y subdirectorios contenidos en él) cambiar el propietario y grupo al usuario creado y grupo users.\
`(g)` Agregue permiso total al dueño, de escritura al grupo y escritura y ejecución a todos los demás usuarios para todos los archivos dentro de un directorio en forma recursiva.\
`(h)` Acceda a otra terminal virtual para loguearse con el usuario antes creado.\
`(i)` Una vez logueado con el usuario antes creado, averigüe cuál es el nombre de su terminal.\
`(j)` Verifique la cantidad de procesos activos que hay en el sistema.\
`(k)` Verifiqué la cantidad de usuarios conectados al sistema.\
`(l)` Vuelva a la terminal del usuario root, y envíele un mensaje al usuario anteriormente creado, avisándole que el sistema va a ser apagado.\
`(m)` Apague el sistema

## `10)` Indique qué comando sería necesario ejecutar para realizar cada una de las siguientes acciones

`(a)` Cree un directorio cuyo nombre sea su número de legajo e ingrese a él.\
`(b)` Cree un archivo utilizando el editor de textos vi, e introduzca su información personal:\
Nombre, Apellido, Número de alumno y dirección de correo electrónico. El archivo debe llamarse "LEAME".\
`(c)` Cambie los permisos del archivo LEAME, de manera que se puedan ver reflejados los siguientes permisos:
- **Dueño:** ningún permiso
- **Grupo:** permiso de ejecución
- **Otros:** todos los permisos

`(d)` Vaya al directorio /etc y verifique su contenido. Cree un archivo dentro de su directorio personal cuyo nombre sea leame donde el contenido del mismo sea el listado de todos los archivos y directorios contenidos en /etc. ¿Cuál es la razón por la cuál puede crear este archivo si ya existe un archivo llamado "LEAME.en este directorio?.\
`(e)` ¿Qué comando utilizaría y de qué manera si tuviera que localizar un archivo dentro del filesystem? ¿Y si tuviera que localizar varios archivos con características similares? Explique el concepto teórico y ejemplifique.\
`(f)` Utilizando los conceptos aprendidos en el punto e), busque todos los archivos cuya extensión sea .so y almacene el resultado de esta búsqueda en un archivo dentro del directorio creado en a). El archivo deberá llamarse .ejercicio_f".

## `11)` Ejercicio

Indique qué acción realiza cada uno de los comandos indicados a continuación considerando su orden. Suponga que se ejecutan desde un usuario que no es root ni pertenece al grupo de root. (Asuma que se encuentra posicionado en el directorio de trabajo del usuario con el que se logueó). En caso de no poder ejecutarse el comando indique la razón:

```
mkdir iso
cd . / iso; ps > f0
ls > f1
cd /
echo $HOME
ls −l $> $HOME/ iso / l s
cd $HOME; mkdir f2
ls −ld f2
chmod 341 f2
touch dir
cd f2
cd ~/ iso
pwd > f3
ps | grep ' ps ' | wc −l >> ../f2/f3
chmod 700 . . / f 2 ; cd . .
find . −name e t c / passwd
find / −name e t c / passwd
mkdir ejercicio5
...................................
.............................................
```

`(a)` Inicie 2 sesiones utilizando su nombre de usuario y contraseña. En una sesión vaya siguiendo paso a paso las órdenes que se encuentran escritas en el cuadro superior. En la otra sesión, cree utilizando algún editor de textos un archivo que se llame. ejercicio10_explicacion"dentro del directorio creado en el ejercicio 9.a) y, para cada una de las órdenes que ejecute en la otra sesión, realice una breve explicación de los resultados obtenidos.\
`(b)` Complete en el cuadro superior los comandos 19 y 20, de manera tal que realicen la siguiente acción:
- `19:` Copiar el directorio iso y todo su contenido al directorio creado en el inciso 9.a).
- `20:` Copiar el resto de los archivos y directorios que se crearon en este ejercicio al directorio creado en el ejercicio 9.a).

`(c)` Ejecute las órdenes 19 y 20 y comentelas en el archivo creado en el inciso a).

![image](https://user-images.githubusercontent.com/55964635/189272687-459c381d-b44c-4a8d-b3d0-aa3acc44e1ae.png)

## `12)` Ejercicio

**Enunciado:** Cree una estructura desde el directorio /home que incluya varios directorios, subdirectorios y archivos, según el esquema siguiente. Asuma que “usuario” indica cuál es su nombre de usuario. Además deberá tener en cuenta que dirX hace referencia a directorios y fX hace
referencia a archivos:

`(a)` Utilizando la estructura de directorios anteriormente creada, indique que comandos son necesarios para realizar las siguientes acciones:
- Mueva el archivo "f3.al directorio de trabajo /home/usuario.
- Copie el archivo "f4.en el directorio "dir11".
- Haga los mismo que en el inciso anterior pero el archivo de destino, se debe llamar "f7".
- Cree el directorio copia dentro del directorio usuario y copie en él, el contenido de "dir1".
- Renombre el archivo "f1"por el nombre archivo y vea los permisos del mismo.
- Cambie los permisos del archivo llamado archivo de manera de reflejar lo siguiente:
  - **Usuario:** Permisos de lectura y escritura
  - **Grupo:** Permisos de ejecución
  - **Otros:** Todos los permisos
- Renombre los archivos "f3 2 "f4"de manera que se llamen "f3.exe 2 "f4.exerespectivamente.
- Utilizando un único comando cambie los permisos de los dos archivos renombrados en el inciso anterior, de manera de reflejar lo siguiente:
  - **Usuario:** Ningún permiso
  - **Grupo:** Permisos de escritura
  - **Otros:** Permisos de escritura y ejecución


## `13)` Indique qué comando/s es necesario para realizar cada una de las acciones de la siguiente secuencia de pasos (considerando su orden de aparición):
`(a)` Cree un directorio llamado logs en el directorio /tmp.\
`(b)` Copie todo el contenido del directorio /var/log en el directorio creado en el punto anterior.\
`(c)` Empaquete el directorio creado en 1, el archivo resultante se debe llamar "misLogs.tar".\
`(d)` Empaquete y comprima el directorio creado en 1, el archivo resultante se debe llamar "misLogs.tar.gz".\
`(e)` Copie los archivos creados en 3 y 4 al directorio de trabajo de su usuario.