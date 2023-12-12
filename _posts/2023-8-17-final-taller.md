---
layout: post
title: 💀 Final Taller de Programación 
cover-img: /assets/img/PortadasEditadas/taller-portada.jpg
thumbnail-img: /assets/img/logos/taller-logo2.gif
share-img: /assets/img/PortadasEditadas/taller-portada.jpg
tags: [Taller, Programacion, Final, Pascal, Arboles, Merge, MergeAcumulador]
---

En esta página voy a tratar de explicar todo lo que se necesita para aprobar el final independientemente del tema. Hay muchas cosas que uno lo puede deducir, pero en esta cátedra el más mínimo error es motivo para un 2(dos).

# 💀 Final Taller de Programación


## Final Pascal

Si te toca este final, tenes 2 opciones nada más. 
- Merge acumulador
- Arboles

Para ambos temas te tenes que saber si o si:
- Agregar Adelante
- Agregar Atras
- Insertar Ordenado

#### Agregar Adelante

```pascal
Procedure AgregarAdelante (var L:lista; x:integer);
Var 
    nue:Lista;
Begin  
    New(nue);  
    nue^.datos:=x;  
    nue^.sig:=L;  
    L:=nue;
End;    
```

#### Agregar Atras

```pascal
procedure AgregarAlFinal(var l,ult:lista;x:integer); 
var  
    nue : lista;
begin 
    new (nue);
    nue^.dato:= x;
    nue^.sig := NIL;
    if l <> Nil then 
        ult^.sig := nue
    else 
        l := nue;
    ult := nue;
end;
```

#### Insertar Ordenado

```pascal
Procedure InsertarElemento ( var pri: lista; x: Integer);
var 
    ant, nue, act: lista;
begin
    new (nue);
    nue^.dato := x;
    act := pri;
    ant := pri;
    while (act<>NIL) and (act^.dato < x) do 
    begin
        ant := act;
        act := act^.sig ;
    end;
    if (ant = act)  then 
        pri := nue   
    else  
        ant^.sig  := nue; 
    nue^.sig := act ;
end;
```

Mira, para probar los codigos yo lo que hago es hacer una lista de numeros enteros y, insertando lo que quiera probar y despues imprimo la lista para ver si esta bien. 

```pascal
procedure ImprimirLista (L:lista);
begin
    while (L <> nil) do 
    begin
        writeln (L^.dato);
        L:= L^.sig;
    end;
end;
```

> IMPORTANTE: Yo no avanzaria hasta saber bien estos codigos, ya que si tenes algun error en estos es causa de desaprobar :,(

Y con esto nos aseguramos de tener todo en orden.


Bien, una vez que sabemos que funcionan los codigos, vamos a resolver el siguiente final.

### Final Merge Acumulador

> En este final no me acordaba el insertar ordenado y el modulo recursivo del punto c, lo habia hecho mal

![image](https://github.com/Fabian-Martinez-Rincon/Fabian-Martinez-Rincon/assets/55964635/fa8d3aea-b55f-4814-b3bc-3afb4082798e)

Tenemos los datos relevantes con colores que seria **denuncia** que contiene lo siguiente:

- Categoria de denuncia 1..6
- DNI
- Direccion
    - Numero de calle
    - Numero de altura
- Mes
- Dia
- Hora

Bien una vez que tenemos estos datos, podemos empezar a ver los puntos dados.

#### Punto A
- Al decirnos que estan agrupadas por categoria nos indica que es un vector de listas (un vector de 6 agrupa las denuncias por categoria).
- Tambien nos dice que estan ordenadas por numero de calle, por lo que usaremos el proceso de **InsertarOrdenado**

#### Punto B

- Al decir que recibe un vector de listas y devuelve una sola lista nos indica que tenemos que usar un **merge** y por defecto usamos un **agregarAtras** en el modulo de minimo.
- Cuando nos dice que para cada nro de calle en especifica, ya sabemos que es un **merge acumulador** (un merge normal pero con un corte de control)
- Para los merges acumuladores es recomendable crear una estructura de datos aparte, que tenga los datos solicidatos, en este caso, **nro de calle**, **cantidad total de denuncias** y **cantidad de denuncias realizadas en el mes de julio**

#### Punto C
Bien, en este caso, yo lo que hago siempre es hacer el module en forma iterativa, para probar y despues lo paso a recursivo. Basicamente cambias el **while** por el **if** y despues llavas cambias en donde se incrementa la variable, por una llamada a la funcion con el incremento o modificación correspondiente.


### Codigo Completo (No lo probe)

```pascal
program imperativo;
const
    DIMF = 6;
type
    categoria = 1..DIMF;
    direccion = record
        nroCalle:integer;
        nroAltura:integer;
    end;
    denuncia = record
        cat:categoria;
        DNI:integer;
        dir:direccion;
        mes:integer;
        dia:integer;
        hora:integer;
    end;
    lista = ^nodo;
    nodo = record
        dato:denuncia;
        sig:lista;
    end;
    vectorContador = array [1..DIMF] of lista;

    datoNuevo = record
        nroCalle:integer;
        denunciasTotales:integer;
        denunciasJulio:integer;
    end;
    listaNueva = ^nodoNuevo;
    nodoNuevo = record
        dato:datoNuevo;
        sig:listaNueva;
    end;

procedure insertarOrdenado(var l:lista;d:denuncia);
var
    act,ant,nue:lista;
begin
    new(nue);
    nue^.dato:=d;
    act:=l;
    ant:=l;
    while (act <> nil) and (act^.dato.DNI < d.DNI) do
    begin
        ant:=act;
        act:=act^.sig;
    end;
    if (act = ant) then
        l:=nue
    else
        ant^.sig:=nue;
    nue^.sig:=act;
end;

procedure imprimirLista(l:lista);
begin
    while l <> nil do
    begin
        WriteLn(l^.dato.DNI);
        l:=l^.sig;
    end;
end;

procedure agregarAtras(var l,ult:listaNueva; nro:datoNuevo);
var
    nue:listaNueva;
begin
    new(nue);
    nue^.dato:=nro;
    nue^.sig:=nil;
    if (l = nil) then
        l:=nue
    else
        ult^.sig:=nue;
    ult:=nue;    
end;

procedure leerDenuncia(var d:denuncia);
begin
    
    writeln('Ingresar dni: '); ReadLn(d.DNI);

    if (d.DNI <> 0) then
    begin
        writeln('Ingresar categoria: '); ReadLn(d.cat);
        writeln('Ingresar nroCalle: '); ReadLn(d.dir.nroCalle);
        writeln('Ingresar nroAltura: '); ReadLn(d.dir.nroAltura);
        writeln('Ingresar mes: '); ReadLn(d.mes);
        writeln('Ingresar dias: '); ReadLn(d.dia);
        writeln('Ingresar hora: '); ReadLn(d.hora);
    end;
end;

procedure cargarDenuncias(var vc:vectorContador);
var
    d:denuncia;
begin
    leerDenuncia(d);
    while (d.DNI <> 0) do
    begin
        insertarOrdenado(vc[d.cat],d);
        leerDenuncia(d);
    end;
end;
procedure inicializarVector (var vc:vectorContador);
var
    i:integer;
begin
    for i:=1 to DIMF do
    begin
        vc[i]:=nil;
    end;
end;

procedure minimo(vc:vectorContador; var min:denuncia);
var
    posMin:integer;
    i:integer;
begin
    posMin:=-1;
    min.DNI:=9999;
    for i:=1 to DIMF do
    begin
        if (vc[i] <> nil) and (vc[i]^.dato.DNI < min.DNI) then
        begin
            min.DNI:=vc[i]^.dato.DNI;
            posMin:=i;
        end;
    end;
    if (posMin <> -1) then
    begin
        min:=vc[posMin]^.dato;
        vc[posMin]:=vc[posMin]^.sig;
    end;
end;
procedure mergeAcumulador(vc:vectorContador;var ln:listaNueva);
var
    min:denuncia;
    actual:datoNuevo;
    ult:listaNueva;
begin
    ult:=nil;
    minimo(vc,min);
    while (min.DNI <> 9999) do
    begin
        actual.nroCalle:=min.DNI;
        actual.denunciasTotales:=0;
        actual.denunciasJulio:=0;
        while (min.DNI <> 9999) and (actual.nroCalle = min.DNI)  do
        begin
            actual.denunciasTotales:=actual.denunciasTotales + 1;
            if (min.mes = 6) then
                actual.denunciasJulio:=actual.denunciasJulio + 1;
            minimo(vc,min);  
        end;
        agregarAtras(ln,ult,actual);
    end;
end;
procedure calleDenuncias(l:listaNueva;var nroCalle:integer;calleMax:integer);
begin
    if l <> nil then
    begin
        if (calleMax < l^.dato.denunciasTotales) then
        begin
            calleMax:=l^.dato.denunciasTotales;
            nroCalle:=l^.dato.nroCalle;
        end;
        calleDenuncias(l^.sig,nroCalle,calleMax)
    end;
end;
var
    vc:vectorContador;
    l:listaNueva;
    calleDenuncias:integer;
    calleMaxima:integer;
begin
    inicializarVector(vc);
    cargarDenuncias(vc);
    mergeAcumulador(vc,l);
    calleDenuncias:=0;
    calleMaxima:=-1;
    calleMasDenuncias(l,calleDenuncias,calleMaxima);
    writeln('La calle con mas denuncias es: ', calleDenuncias);
end.
```


---

### Final Arboles

> En este final tenia mal el recorrido del arbol, lo puse dos condicionales en la condicion base. (Y siempre va <> nil en la condicion base)

![image](https://github.com/Fabian-Martinez-Rincon/Fabian-Martinez-Rincon/assets/55964635/749e071a-179f-4db5-97f3-1c2ede2e5fb8)

> IMPORTANTE: Primero te diria que resuelvas este parcial con full enteros y despues le agregues los datos compuestos, ya que es mas facil/rapido de testear

Tenemos **recital** con los siguientes datos

- Nombre de la Banda
- Fecha del recital
- Cantidad de canciones tocadas
- Monto recaudado por la venta de entradas

Bien, una vez que tenemos estos datos, podemos empezar a ver los puntos dados.

#### Punto A
- En el momento que nos dice que tienen que estar en **una estructura que permite el recorrido optimo** por **monto recaudado**, usamos un **arbol**

#### Punto B

- Mira, esta parte puede ser la menos intuitiva, ya que NO tenemos que recorrer el arbol completo, tenemos que recorrer las ramas, hasta estar en el rango de numeros
- Tenemos que usar un **agregarAtras**, ya que el arbol al estar ordenado, mantenemos el orden.

#### Punto C

- Aca simplemente hacemos el modulo iterativo, cambiamos el while por el if y despues cambiamos el incremento de la variable, por la llamada al proceso con el incremento como parametro.

---

## Final Objetos

En todos los finales de objetos son mas o menos lo mismo, con resolver bien este final creo que abarcas todos los temas de objetos.

> Cuando rendi este final me dijieron que tenia un 10 en el practico, pero me fue mal en las preguntas teoricas.

![Objetos](https://github.com/Fabian-Martinez-Rincon/Fabian-Martinez-Rincon/assets/55964635/45f4d6a1-edba-4c42-9dfa-eb40fa405f33)

> IMPORTANTE en este tipo de finales NO tenes collecciones, nos manejamos siempre con arrays

Lo mas importante es identificar los objetos con sus atributos y herencias que tenemos.

- Tenista
    - Nombre
    - Cantidad de Partidos Ganados
    - Premios obtenidos en toda su carrera (un array de reales)
- Partido
    - Fecha (string)
    - Lugar
    - Resultado
        - SetsEquipo1
        - SetsEquipo2
- Partido Single (Heredan de Partido) 
    - 2 tenistas
- Partido Doble (Heredan de Partido)
    - 4 tenistas

Una vez que definimos todos los tipos de datos. Empezamos a ver los puntos y definimos los metodos segun el objeto.
- Cuando decimos que debe instanciarse con todos sus datos, nos referimos al constructor.


### Final Concurrente
![concurrente](https://github.com/Fabian-Martinez-Rincon/Fabian-Martinez-Rincon/assets/55964635/3bca1075-53a7-4524-955d-bc41ca1af59a)
