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
- Insertar Ordenado
- Agregar Adelante
- Agregar Atras

#### Basicos

<table>
<tr><td>Agregar Adelante</td><td>Agregar Atras</td></tr>
<tr><td>

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
</td><td>

```pascal
procedure AgregarAlFinal2(var pri,ult:lista;x:integer); 
var  
    nue : lista;
begin 
    new (nue);
    nue^.dato:= x;
    nue^.sig := NIL;
    if pri <> Nil then 
        ult^.sig := nue
    else 
        pri := nue;
    ult := nue;
end;
```
</td></tr>
</table>

