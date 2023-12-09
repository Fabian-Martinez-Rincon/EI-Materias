---
layout: post
title: 💀 Final Taller de Programación 
cover-img: /assets/img/PortadasEditadas/taller-portada.jpg
thumbnail-img: /assets/img/logos/taller-logo2.gif
share-img: /assets/img/PortadasEditadas/taller-portada.jpg
tags: [Procesos, Memoria Principal, Memoria Virtual, Sistemas Operativos, Practicas, ISO]
---

## 💀 Final Taller de Programación

En esta página voy a tratar de explicar todo lo que se necesita para aprobar el final independientemente del tema. Hay muchas cosas que uno lo puede deducir, pero en esta cátedra el más mínimo error es motivo para un 2(dos).

### Final Pascal

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

Y con esto nos aseguramos de tener todo en orden.


Bien, una vez que sabemos que funcionan los codigos, vamos a resolver el siguiente final.

![image](https://github.com/Fabian-Martinez-Rincon/Fabian-Martinez-Rincon/assets/55964635/fa8d3aea-b55f-4814-b3bc-3afb4082798e)

![image](https://github.com/Fabian-Martinez-Rincon/Fabian-Martinez-Rincon/assets/55964635/749e071a-179f-4db5-97f3-1c2ede2e5fb8)
