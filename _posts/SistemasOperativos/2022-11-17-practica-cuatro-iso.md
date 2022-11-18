---
layout: post
title: 📝 Practica 4
thumbnail-img: /assets/img/iso.png
tags: [iso, sistemas operativos, practica 4, linux]
---

##  Objetivo
El objetivo de esta práctica es que el alumno comprenda los aspectos base acerca de la planificación de procesos en un Sistema Operativo (tipos de planificadores, algoritmos y sus variantes, etc.).

### Indice
- [Ejercicio 1](#ejercicio-1)
- [Ejercicio 2](#ejercicio-2)
- [Ejercicio 3](#ejercicio-3)
- [Ejercicio 4](#ejercicio-4)
- [Ejercicio 5](#ejercicio-5)
- [Ejercicio 6](#ejercicio-6)
- [Ejercicio 7](#ejercicio-7)
- [Ejercicio 8](#ejercicio-8)
- [Ejercicio 9](#ejercicio-9)
- [Ejercicio 10](#ejercicio-10)
- [Ejercicio 11](#ejercicio-11)
- [Ejercicio 12](#ejercicio-12)
- [Ejercicio 13](#ejercicio-13)
- [Ejercicio 14](#ejercicio-14)
- [Ejercicio 15](#ejercicio-15)
- [Ejercicio 16](#ejercicio-16)
- [Ejercicio 17](#ejercicio-17)
- [Ejercicio 18](#ejercicio-18)
- [Ejercicio 19](#ejercicio-19)
- [Ejercicio 20](#ejercicio-20)
- [Ejercicio 21](#ejercicio-21)
- [Ejercicio 22](#ejercicio-22)
- [Ejercicio 23](#ejercicio-23)
- [Ejercicio 24](#ejercicio-24)
- [Ejercicio 25](#ejercicio-25)




### `Ejercicio 1)` 
Responda en forma sintética sobre los siguientes conceptos:
- `(a)` Programa y Proceso
- `(b)` Defina Tiempo de retorno (**TR**) y Tiempo de espera (**TE**) para un Job.
- `(c)` Defina Tiempo Promedio de Retorno (**TPR**) y Tiempo promedio de espera (**TPE**) para un lote de JOBS.
- `(d)` ¿Qué es el Quantum?
- `(e)` ¿Qué significa que un algoritmo de scheduling sea apropiativo o no apropiativo (Preemptive o Non-Preemptive)?
- `(f)` ¿Qué tareas realizan?:
    - `i.` Short Term Scheduler
    - `ii.` Long Term Scheduler
    - `iii.` Medium Term Scheduler
- `(g)` ¿Qué tareas realiza el Dispatcher?

### `Ejercicio 2)`
2. Procesos:
- (a) Investigue y detalle para que sirve cada uno de los siguientes comandos. (Puede que
algún comando no venga por defecto en su distribución por lo que deberá instalarlo):
    - `i`. **top**
    - `ii`. **htop**
    - `iii`. **ps**
    - `iv`. **pstree**
    - `v`. **kill**
    - `vi`. **pgreppkillkillall**
    - `vii`. **killall**
    - `viii`. **renice**
    - `ix`. **xkill**
    - `x`. **atop**
- `(b)` Observe detenidamente el siguiente código. Intente entender lo que hace sin necesidad
de ejecutarlo.
    ```c
    #include <stdio.h>
    #include <sys/types.h>
    #include <unistd.h>
    int main(void) {
        int c;
        pid_t pid;
        printf(" Comienzo. : \n " );
        for (c=0;c<3;c++){
            pid = fork();
        }
        printf( "Proceso \n ");
        return 0;
    }
    ```
    - `i.` ¿Cuántas líneas con la palabra `Proces` aparecen al final de la ejecución de este programa?.
    - `ii.` ¿El número de líneas es el número de procesos que han estado en ejecución?. Ejecute el programa y compruebe si su respuesta es correcta, Modifique el valor del bucle for y compruebe los nuevos resultados.
- `(c)` Vamos a tomar una variante del programa anterior. Ahora, además de un mensaje,
vamos a añadir una variable y, al final del programa vamos a mostrar su valor. El
nuevo código del programa se muestra a continuación
    ```c
    #include <stdio.h>
    #include <sys/types.h>
    #include <unistd.h>
    int main( void ) {
        int c ;
        int p=0;
        pid_t pid ;
        for( c = 0; c<3 ;c++){
            pid = fork() ;
        }
        p++;
        printf( "Proceso %d\n ", p) ;
        return 0;
    }
    ```
    - `i.` ¿Qué valores se muestran por consola?.
    - `ii.` ¿Todas las líneas tendrán el mismo valor o algunas líneas tendrán valores distintos?.
    - `iii.` ¿Cuál es el valor (o valores) que aparece?. Ejecute el programa y compruebe si su respuesta es correcta, Modifique el valor del bucle for y el lugar dónde se incrementa la variable p y compruebe los nuevos resultados.
- `(d)` Comunicación entre procesos:
    - `i.` Investigue la forma de comunicación entre procesos a través de pipes.
    - `ii.` ¿Cómo se crea un pipe en C?.
    - `iii.` ¿Qué parametro es necesario para la creación de un pipe?. Explique para que se utiliza.
    - `iv.` ¿Qué tipo de comunicación es posible con pipes?
- `(e)` ¿Cuál es la información mínima que el SO debe tener sobre un proceso?¿En que estructura de datos asociada almacena dicha información? 
- `(f)` ¿Qué significa que un proceso sea “CPU Bound” y “I/O Bound”?
- `(g)` ¿Cuáles son los estados posibles por los que puede atravesar un proceso?
- `(h)` Explique mediante un diagrama las posibles transiciones entre los estados.
- `(i)` ¿Que scheduler de los mencionados en 1 f se encarga de las transiciones?

### `Ejercicio 3)`
### `Ejercicio 4)`
### `Ejercicio 5)`
### `Ejercicio 6)`
### `Ejercicio 7)`
### `Ejercicio 8)`
### `Ejercicio 9)`
### `Ejercicio 10)`
### `Ejercicio 11)`
### `Ejercicio 12)`
### `Ejercicio 13)`
### `Ejercicio 14)`
### `Ejercicio 15)`
### `Ejercicio 16)`
### `Ejercicio 17)`
### `Ejercicio 18)`
### `Ejercicio 19)`
### `Ejercicio 20)`
### `Ejercicio 21)`
### `Ejercicio 22)`
### `Ejercicio 23)`
### `Ejercicio 24)`
### `Ejercicio 25)`