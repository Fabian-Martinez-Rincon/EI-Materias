# 📒 Practica 1

<p><img width="280" align='right' src="../Img/1.png"></p>



El objetivo de esta práctica es que el alumno se familiarice con los conceptos básicos del sistema
operativo GNU/Linux, así como con su entorno y comandos principales.
- [Preguntas/Dudas]()
- [1) Características de GNU/Linux](#1-características-de-gnulinux)
- [2) Distribuciones de GNU/Linux](#2-distribuciones-de-gnulinux)
- [3) Estructura de GNU/Linux](#3-estructura-de-gnulinux)
- [4) Kernel](#4-kernel)
- [5) Intérprete de comandos (Shell)](#5-intérprete-de-comandos-shell)
- [6) Sistema de Archivos (File System)](#6-sistema-de-archivos-file-system)
- [7) Particiones](#7-particiones)
- [8) Arranque (bootstrap) de un Sistema Operativo](#8-arranque-bootstrap-de-un-sistema-operativo)
- [9) Archivos](#9-archivos)
- [10) Indique qué comando es necesario utilizar para realizar cada una de las siguientes acciones.](#10-indique-qué-comando-es-necesario-utilizar-para-realizar-cada-una-de-las-siguientes-acciones-investigue-su-funcionamiento-y-parámetros-más-importantes)
- [11) Investigue su funcionamiento y parámetros más importantes](#11-nvestigue-su-funcionamiento-y-parámetros-más-importantes)
- [12) Investigue su funcionamiento y parámetros más importantes](#12-nvestigue-su-funcionamiento-y-parámetros-más-importantes)


## Preguntas/Dudas

- No entendi muy bien el concepto de partición logica ya que es completamente igual que la primaria, pero no tiene el gestor de arranque. Entonces, que ventaja tiene? 
- Que funcionalidad tiene el locate, porque no funca
- Falta el ultimo punto (12)

---

## `1)` Características de **GNU/Linux**:

`a)` Mencione y explique las características más relevantes de **GNU/Linux**.\
Linux es un sistema operativo completamente libre y gratuito.
- **Gratuito:** Además de ser completamente gratuito, cuenta con múltiples distribuciones, cada una con distintas funcionalidades.
- **Código abierto e independiente:** Cualquiera puede desarrollar y distribuir nuevas funciones, sin necesidad de permisos ni protocolos previos.
- **Muy estable:** Es muy estable :D
- **Altamente seguro:** Como se trata de un software libre, los "hackers" informáticos no tienen mucho interés en desarrollar virus para Linux. 
- **Multitarea y multiusuario:** La potencia de este sistema permite ejecutar a la vez numerosos programas y aplicaciones.

`b)` Mencione otros sistemas operativos y compárelos con GNU/Linux en cuanto a los puntos mencionados en el inciso a.
- A diferencia de Windows y Mac, Linux no pertenece a ninguna compañía, sino que su desarrollo depende de la colaboración de un gran número de empresas y profesionales.
- Su uso esta mas enfocado a programadores dado que sus interfaces son menos amigables.
- Los demás sistemas suelen ser en su mayoría pagos y enfocados mas a lo comercial
- El manejo de permisos de Linux vuelve mas difícil la creación de un virus para dicho sistema mientras que en Windows es mas común.

`c)` ¿Qué es **GNU**?\
GNU es un sistema operativo de software libre

`d)` Indique una breve historia sobre la evolución del proyecto *GNU*\
- El proyecto GNU fue iniciado por Richard M. Stallman con el propósito de crear un sistema operativo completo y libre: el sistema GNU.
- Se baso principalmente en 4 libertades
    - **Libertad 1:** la libertad para ejecutar el programa con cualquier fin.
    - **Libertad 2:** La libertad de estudiar cómo trabaja el programa y de adecuarlo para que haga lo que usuario desee
    - **Libertad 3:** la libertad de redistribuir el programa de manera de colaborar con el resto de la sociedad.
    - **Libertad 4:** la libertad de hacer pública y distribuir a terceros la versión mejorada.

Pondria más pero a nadie le importa la historia de linux salu2.

`e)` Explique qué es la multitarea, e indique si *GNU/Linux* hace uso de ella.\
**Multitarea:** Que permite la ejecución concurrente o simultánea de diversas tareas y procesos.\
LINUX utiliza la llamada multitarea preventiva, la cual **asegura que todos los programas que se están utilizando en un momento dado serán ejecutados**, siendo el sistema operativo el encargado de ceder tiempo de microprocesador a cada programa.

`f)` ¿Qué es **POSIX**?\
Es una norma escrita por la IEEE, que define una interfaz estándar del sistema operativo y el entorno, incluyendo un intérprete de comandos (o "shell")

---

## `2)` Distribuciones de **GNU/Linux**:

`a)` ¿Qué es una distribución de GNU/Linux? Nombre al menos 4 distribuciones de GNU/- Linux y cite diferencias básicas entre ellas.\
Una distribución GNU/Linux es un conjunto de aplicaciones reunidas que permiten brindar mejoras para instalar fácilmente un sistema operativo.

Algunas distribuciones:
- [Debian](http://www.debian.org/)
- [Gentoo](http://www.gentoo.org/)
- [Red Hat Linux](http://www.redhat.com/)
- [Slackware](http://www.slackware.com/)

`b)` ¿En qué se diferencia una distribución de otra?\
Aunque en la mayoría de los casos la principal diferencia es la GUI, o los programas y herramientas que vienen incluidos. Cada distribución Linux tiene un objetivo, que justifica su existencia. Por ejemplo, distribuciones como Ubuntu se centran en ser lo más amigables posible a la hora de instalarse o descargar programas.

`c)` ¿Qué es Debian? Acceda al sitio 1 e indique cuáles son los objetivos del proyecto y una breve cronología del mismo.\
Debian es un sistema operativo libre, desarrollado por un monton de comunistas :D

---

## `3)` Estructura de GNU/Linux:

`a)` Nombre cuales son los 3 componentes fundamentales de GNU/Linux.\

- **El kernel (núcleo)** es el encargado de que el software y el hardware de una computadora puedan trabajar juntos.
- **El Shell (interprete de comandos)** Un intérprete de comandos es un programa que lee las entradas del usuario y las traduce a instrucciones que el sistema es capaz de entender y utilizar.
- **El FileSystem (sistema de archivos)** permite que dentro de un SO se organicen y administren archivos.

`b)` Mencione y explique la estructura básica del Sistema Operativo GNU/Linux.
- **Bootloader (gestor de arranque):** es un sutil software cuya tarea es cargar el sistema operativo de un ordenador en la memoria.
- **Servidor grafico:** es responsable de la activación de la tarjeta de vídeo, ratón y teclado, lo que permite al usuario el uso de interfaces gráficas que son llamadas de Gestores de Ventanas y Entornos de Escritorio
- **Entornos de escritorio:** Estos Entornos de Escritorio proporcionan el fondo de la pantalla, los paneles, las barras de título de las ventanas y mucho más.


---

## `4)` Kernel: 

`a)` ¿Qué es? Indique una breve reseña histórica acerca de la evolución del Kernel de GNU/Linux.\
Se explica arriba y la historia no me importa :D

`b)` ¿Cuáles son sus funciones principales?
- **Gestión de la memoria:** supervisa cuánta memoria se utiliza para almacenar qué tipo de elementos, así como el lugar en que los guarda.
- **Gestión de los procesos:** determina qué procesos pueden usar la unidad central de procesamiento (CPU), cuándo y durante cuánto tiempo.
- **Controladores de dispositivos:** actúa como mediador o intérprete entre el hardware y los procesos.
- **Seguridad y llamadas al sistema:** recibe solicitudes de servicio por parte de los procesos.

`c)` ¿Cuál es la versión actual? ¿Cómo se definía el esquema de versionado del Kernel en versiones anteriores a la 2.4? ¿Qué cambió en el versionado se impuso a partir de la versión 2.6?\
La versión del kernel actual es 5.16. Lo demas a nadie le importa 

`d)` ¿Es posible tener más de un Kernel de GNU/Linux instalado en la misma máquina?\
No, solo puede haber uno.

`e)` ¿Dónde se encuentra ubicado dentro del File System?\
Se encuentra justo en el medio que reside en la memoria e indica qué debe hacer la CPU.  En el directorio boot

`f)` ¿El Kernel de GNU/Linux es monolítico? Justifique.\
El kernel de GNU/Linux es monolítico hibrido, esto se refiere a que el núcleo usa mecanismos de arquitectura tando de diseño **monolítico** como **micronúcleo**

---

## `5)` Intérprete de comandos (Shell):

`a)` ¿Qué es?\
El Shell (intérprete de comandos) es el programa que recibe lo que se escribe en la terminal y lo convierte en instrucciones para el sistema operativo.

`b)` ¿Cuáles son sus funciones?\
Una de sus funciones es leer las entradas del usuario y traducirlas a instrucciones que el sistema es capaz de entender y utilizar.

`c)` Mencione al menos 3 intérpretes de comandos que posee GNU/Linux y compárelos entre ellos.
- **Korn-Shell (ksh):**
- **Bourne-Shell (sh):**
- **C-Shell (csh):**

Estas se diferencian entre sí básicamente en la sintaxis de sus comandos y en la interacción con el usuario.

`d)` ¿Dónde se ubican (path) los comandos propios y externos al Shell?
- **Propios:** Son basicamente los comandos
- **Externos:** Es cualquier ejecutable

`e)` ¿Por qué considera que el Shell no es parte del Kernel de GNU/Linux?\
La principal razon es que es muy remplazable, en caso de que falle, se puede reiniciar y todo tendria que seguir andando.

`f)` ¿Es posible definir un intérprete de comandos distinto para cada usuario? ¿Desde dónde se define? ¿Cualquier usuario puede realizar dicha tarea?\
Cada usuario posee una shell por defecto , la cual puede definirse por un usuario con derechos privilegiados.

---

## `6)` Sistema de Archivos (File System):

`a)` ¿Qué es?\
Es la forma en que dentro de un SO se organizan y se administran los archivos.
- **Métodos de acceso:** cómo se acceden los datos contenidos en el archivo.
- **Manejo de archivos:** cómo actúan los mecanismos para almacenar, referenciar, compartir y proteger los archivos.
- **Manejo de la memoria secundaria:** Cómo se administra el espacio para los archivos en memoria secundaria.
- **Mecanismos de integridad:** con qué métodos se garantiza la incorruptibilidad del archivo.

`b)` Mencione sistemas de archivos soportados por GNU/Linux.\
A continuación veremos una lista con algunos filesystem utilizados hoy en día:
- ext2
- ext3
- ReiserFS
- XFS

`c)` ¿Es posible visualizar particiones del tipo FAT y NTFS en GNU/Linux?\
SI\
`d)`  ¿Cuál es la estructura básica de los File System en GNU/Linux? Mencione los directorios más importantes e indique qué tipo de información se encuentra en ellos. ¿A qué hace referencia la sigla FHS?\
La estructura basica en la que se organizan es **jerarquica de tipo arbol**. El nivel más alto del sistema de ficheros es / o directorio raíz. Todos los demás ficheros y directorios están bajo el directorio raíz. Por ejemplo, /home/jebediah/cheeses.

FHS define los directorios principales y sus contenidos en el sistema operativo LinuxGNU/Linux 

---

## `7)` Particiones:

`a)`  Definición. Tipos de particiones. Ventajas y Desventajas.\
Particionar un disco duro es realizar una división en él de modo que, a efectos prácticos, el sistema operativo crea que tienes varios discos duros, cuando en realidad sólo hay un único disco físico dividido en varias partes. De este modo, se pueden modificar o borrar particiones sin afectar a los demás datos del disco.\
Tipos de particiones:

- **Primarias:** puede ser reconocida como una partición de arranque y puede contener un sistema operativo que realice el arranque del equipo.
- **Extendidas/secundaria** : actúa como una partición primaria; sirve para contener múltiples unidades lógicas en su interior. Fue ideada para romper la limitación de 4 particiones primarias en un solo disco físico
- **Lógicas:** son aquellas particiones que creamos dentro de las particiones extendidas. Al igual que en las particiones primarias, las particiones lógicas pueden utilizarse para instalar Windows y cualquier otro tipo de archivos. Aunque podemos instalar sistemas operativos en las unidades lógicas, no se les puede dar el estado activo y, por lo tanto, no sirven para arrancar el ordenador desde cero por si mismas. Eso sí, podemos utilizar un gestor de arranque en una partición primaria para arrancar las particiones lógicas.
- `Ventajas`
    - **Instalar dos o más sistemas operativos**
    - **Mejor organización**
    - **Más seguridad**
    - **Copias de seguridad**
    - **Facilidad de reinstalación**
- ``Desventajas``
    - **Innecesario para el usuario medio**
    - **Desorden en los volúmenes**
    - **Posibilidad de errores**
    - **Experiencia más lenta**

`b)` ¿Cómo se identifican las particiones en GNU/Linux? (Considere discos **IDE**, **SCSI** y **SATA**).\
Las particiones en cada disco son representadas añadiendo un número decimal al nombre del disco: sda1 y sda2 representan a la primera y segunda partición en la primera unidad de disco SCSI en el sistema.

`c)` ¿Cuántas particiones son necesarias como mínimo para instalar GNU/Linux? Nómbrelas indicando tipo de partición, identificación, tipo de File System y punto de montaje.\
Como mınimo es necesario una particion (para el /)\
La respuesta rápida y fácil es: **recomendable al menos dos, una para el sistema/datos(Primaria) y otra para Swap**. Usualmente se suelen tener tres, una para el sistema/programas (/)(Secundaria), otra para los datos (/home) y otra para swap.

- **Swap:** Una partición SWAP en Linux es un espacio del disco duro utilizado por el sistema operativo como memoria virtual o almacenamiento temporal. Es utilizado cuando no hay espacio suficiente en la memoria RAM para guardar datos de aplicaciones, por lo que la parición SWAP cumple la función de emular RAM en disco

`d)` Ejemplifique diversos casos de particionamiento dependiendo del tipo de tarea que se deba realizar en su sistema operativo.\
Son las primarias y secundarias, que para mas detalle se encuentra en la pregunta `a)`

`e)`  ¿Qué tipo de software para particionar existe? Menciónelos y compare\

Existen 2 tipos:
- **Destructivos:** permiten crear y eliminar particiones (fdisk)
- **No destructivo:** permiten crear, eliminar y modificar particiones

---

## `8)` Arranque (bootstrap) de un Sistema Operativo:

`a)` ¿Qué es el BIOS? ¿Qué tarea realiza?\
BIOS es el responsable de iniciar la carga del SO a través del MBC, el cual es un pequeño código para el arranque del sistema operativo

`b)` ¿Qué es UEFI? ¿Cuál es su función?\
UEFI  es el código del firmware(sirve para comunicarse con los dispositivos de hardware de un sistema) de un chip en la placa base que proporciona funciones adicionales a las del sistema de entrada/salida básico (BIOS). UEFI ofrece una manera de hacer cosas con el equipo antes de que se cargue un sistema operativo.

`c)` ¿Qué es el MBR? ¿Que es el MBC?\
MBC, es un pequeño código para el arranque del sistema operativo.

El MBR o **master boot recordes** el primer sector físico de un portador de datos (por ejemplo, un disco duro, una memoria USB) que se utiliza para arrancar (iniciar) los ordenadores. Para esto, el ordenador debe disponer de un BIOS y un sistema operativo x86

`d)` ¿A qué hacen referencia las siglas GPT? ¿Qué sustituye? Indique cuál es su formato.\
GPT(GUID partition table) especifica la ubicación y formato de la tabla de
particiones en un disco duro. Sustituye al MBR

**GPT lo hace mediante LBA o dirección de bloque lógica** para referirse a la región en donde se encuentran los datos físicamente almacenados en nuestra unidad de almacenamiento

`e)` ¿Cuál es la funcionalidad de un “Gestor de Arranque”? ¿Qué tipos existen? ¿Dónde se instalan? Cite gestores de arranque conocidos.\
La finalidad del bootloader o gestor de arranque es la de cargar una imagen de
Kernel (sistema operativo) de alguna partición para su ejecución

- Se ejecuta luego del código del BIOS
- Existen 2 modos de instalación:
    - En el MBR (puede llegar a utilizar MBR gap)
    - En el sector de arranque de la partición raíz o activa (Volume
    Boot Record)
- Tipos GRUB, LILO, NTLDR, GAG, YaST, etc
- GRand Unified Bootloader: gestor de arranque múltiple más
utilizado

`f)` ¿Cuáles son los pasos que se suceden desde que se prende una computadora hasta que el Sistema Operativo es cargado (proceso de bootstrap)?

- El BIOS se ejecuta, realizando el **POST**, que incluye rutinas que, fijan valores de las señales internas, y ejecutan test internos (RAM, el teclado, etc).
- Se lee el primer sector del disco de inicio llamado **MBR**.
- Se carga en memoria y se ejecuta

`g)`  Analice el proceso de arranque en GNU/Linux y describa sus principales pasos.\
Ell flujo de control durante el arranque es desde el **[BIOS]()**, al **[gestor de arranque]()** y al núcleo (**[kernel]())**). 

- **Kernel:** Este inicia el planificador (para permitir la **[multitarea]()**) y ejecuta el primer **[espacio de usuario]()** (fuera del espacio del núcleo) y el programa de inicialización (que establece el entorno de usuario y permite la interacción del usuario y el **[inicio de sesión]())**, momento en el que el núcleo se inactiva hasta que sea llamado externamente.

- La etapa del **[cargador de arranque]()** no es totalmente necesaria. Determinadas BIOS pueden cargar y pasar el control a Linux sin hacer uso del cargador. Cada proceso de arranque será diferente dependiendo de la arquitectura del **[procesador]()** y el *BIOS*.

- En el apagado, Init es llamado a cerrar toda las funcionalidades del espacio de usuario de una manera controlada, de nuevo a través de secuencias de comandos, tras lo cual el Init termina y el núcleo ejecuta el apagado.

`h)` ¿Cuáles son los pasos que se suceden en el proceso de parada (shutdown) de GNU/Linux?
- Se notifica a los usuarios este hecho.
- Se bloquea el sistema para que nadie más pueda acceder exceptuando el **root**.
- Se envía la señal **SIGTERM** (señal de terminación) a todos los procesos no definidos en **inittab**(contiene un registro para cada proceso que define los niveles de ejecución para ese proceso) para el siguiente run level, provocando que terminen su ejecución de modo ordenado.

`i)` ¿Es posible tener en una PC GNU/Linux y otro Sistema Operativo instalado? Justifique\
Si es posible ya lo vimos anteriormente gracias a las particiones de disco instalar múltiples sistema operativos o a través de maquinas virtuales.

---

## `9)` Archivos

`a)` ¿Cómo se identifican los archivos en GNU/Linux?\
Un nombre de archivo puede tener entre 1 y 255 caracteres. recomendable emplear los caracteres con significado especial en Linux, que son los siguientes: **= \ ^ ~ ' " ` * ; - ? ( )! & ~ < >**

`b)` Investigue el funcionamiento de los editores vi y mcedit, y los comandos cat y more.

- **VI**
Es el editor de texto clásico en UNIX. Puede usarse en cualquier tipo de terminal con un mínimo de teclas.

**MODOS DE VI:**
Existen tres modos o estados de vi:

- **Modo comando:** Este es el modo en el que se encuentra el editor cada vez que se inicia.
Las teclas ejecutan acciones (comandos) que permiten mover el cursor, ejecutar comandos de edición de texto, salir de **vi**, guardar cambios, etc.
- **Modo inserción o texto:** Este es el modo que se usa para insertar el texto. Existen varios
comandos que se pueden utilizar para ingresar a este modo.
- **Modo línea o ex:** Se escriben comandos en la última línea al final de la pantalla.

- **MCEDIT**

Al igual que Vi funciona como gestor de archivos

- **cat**
Es la abreviatura de concatenar. Esto se refiere al hecho de que cat puede ser utilizado para combinar múltiples archivos en un archivo, también se puede utilizar para crear nuevos archivos y para mostrar el contenido de los archivos existentes.

- **more**
Es un comando para ver (pero no modificar) el contenido de un archivo o comando y visualizarlo por páginas.


`c)` Cree un archivo llamado “prueba.exe” en su directorio personal usando el vi. El mismo debe contener su número de alumno y su nombre.\
- Utilice el siguiente comando para crear un archivo (en este ejemplo, .htaccess). También puede editar un archivo existente con el mismo comando. 

```
vi .htaccess
```

- Pulse la tecla de la letra i para cambiar al modo de entrada.
- Inserte el contenido deseado o realice las modificaciones deseadas.
- Pulse la tecla ESC para salir del modo de entrada.
- Guarde el nuevo archivo o los cambios realizados con el siguiente comando:

```
:wq
```

`d)` Investigue el funcionamiento del comando file. Pruébelo con diferentes archivos. ¿Qué diferencia nota?\
Permite detectar el tipo y formato de un archivo

```
file nombreArchivo
```

---

## `10)` Indique qué comando es necesario utilizar para realizar cada una de las siguientes acciones. Investigue su funcionamiento y parámetros más importantes:

`a)` Cree la carpeta ISO2017
```
mkdir "ISO 2022"
```
`b)` Acceda a la carpeta (cd)
```
cd 'ISO 2022'
```
`c)` Cree dos archivos con los nombres iso2017-1 e iso2017-2 (touch)
```
touch ISO2022-1 ISO2022-2
```
`d)` Liste el contenido del directorio actual (ls)
```
ls
```
`e)` Visualizar la ruta donde estoy situado (pwd)
```
pwd
```
`f)` Busque todos los archivos en los que su nombre contiene la cadena “iso*” (find)
```
find ./'ISO 2022' -name "ISO*"
```
`g)` Informar la cantidad de espacio libre en disco (df)
```
df
```
`h)` Verifique los usuarios conectado al sistema (who)
```
who
```
`i)` Acceder a el archivo iso2017-1 e ingresar Nombre y Apellido
```
vi ISO2022-1
```
`j)` Mostrar en pantalla las últimas líneas de un archivo (tail).
```
tail ISO2022-1
```

---

## `11)` Investigue su funcionamiento y parámetros más importantes:

`a)` shutdown\
El comando de apagado (Shutdown) te permite apagar, reiniciar y detener tu sistema


```
sudo shutdown
sudo shutdown now
sudo shutdown [time]
sudo shutdown 11:50
sudo shutdown +5
sudo shutdown +2 "System update"
sudo shutdown -r
sudo shutdown +3 –r "Update System"
sudo shutdown -c
```

| Options  | Description |
| ------------- | ------------- |
| -a  | To control access to the “shutdown” command, it employs the control access file “/etc/shutdown.allow.”  |
| -k  | Instead of shutting down, deliver warning messages as though the shutdown is actual.  |
| -P  | Tells the system to power down before shutting down.  |
| -f  | It skips fsck after reboot.  |
| -F  | After reboot it forces fsck.  |
| -H  | This option orders the system to descend into the boot the monitor on computers which provide support to it if -h is also supplied.  |

`b)` reboot\
Sirve para reiniciar el equipo
```
sudo reboot
```


`c)` halt\
El comando halt detiene la CPU del ordenador
```
sudo halt
```



`d)` locate\
El comando locate es una alternativa útil, ya que es más rápido que find para realizar búsquedas. Eso se debe a que sólo escanea tu base de datos de Linux en lugar de todo el sistema. Además, la sintaxis es más fácil de escribir
```
sudo apt install locate
```
`e)` uname\
Se usa para verificar la información del sistema
```
uname -s
uname -r
uname -v
uname -n
uname -m
uname -p
uname -i
uname -o
uname -a
```

`f)` gmesg (No entiendo porque esta diferente)
El comando `dmesg` es una utilidad de Linux que muestra mensajes relacionados con el kernel recuperados del búfer de anillo del kernel.
```
dmesg
```

`g)` lspci
El comando lspci lista todos los componentes tipo pci como son las tarjetas de red, tarjetas de sonido o tarjetas de televisión. 
```
lspci
```

`h)` at
Ejecuta comandos a la hora especificada.

`i)` netstat
Los administradores de sistemas utilizan netstat el comando de Linux para ver información sobre las conexiones de red
```
sudo apt install net-tools
```

`j)` mount\
Se utiliza para montar dispositivos y particiones para su uso por el sistema operativo
```
sudo apt install nfs-common
sudo mkdir -p /mnt/client_ shareddirectory
sudo mount [nfs_server]:/[nfs_shareddirectory] [client_mountpoint]
```

`k)` umount\
El comando umount le permite eliminar un sistema de archivos remoto que esté montando en la actualidad\
Ejemplo:
```
umount --all
```

`l)` head\
Este comando sirve principalmente para mostrar al principio de un archivo (de texto) o para reducir a lo especificado los datos mostrados por un comando de Linux


`m)` losetup\
losetup de comandos de Linux se utiliza para fijar el dispositivo de bucle.

**parámetros:**

- -d dispositivo extraíble.
- -e <cifrado> Iniciar cifrado codificación.
- -o <número de traducción> Establecer el número de conversión de datos.

`n)` write\
sirve para enviar un mensaje a otro usuario del sistema.

write usuario
Escribo aquí lo que
quiera que le llegue y luego cierro.
Control-D

`ñ)` mkfs\
Se utiliza para dar formato a un dispositivo de almacenamiento de bloque con un determinado sistema de archivos

`o)` fdisk (con cuidado) \
Permite al usuario crear particiones en el disco duro de la misma manera que su contraparte de MS-DOS

---

# `12)` Investigue su funcionamiento y parámetros más importantes:

- `a)`  Indique en qué directorios se almacenan los comandos mencionados en el ejercicio anterior.

Preguntale a dios.