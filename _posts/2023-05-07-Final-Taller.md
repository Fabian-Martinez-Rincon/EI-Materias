---
layout: post
title: 💻 Taller de Programación Final
cover-img: /assets/img/PortadasEditadas/Taller.png
thumbnail-img: /assets/img/logos/taller2.png
share-img: /assets/img/PortadasEditadas/Taller.png
tags: [Taller De Programación, Java, Pascal, R-INFO]
---

En este resumen voy a poner codigo de R-Info y de Pascal ya que son los temas mas "dificiles" de aprobar sin estudiar. Si necesitas los recursos de la materia, los podes encontrar en este [**repositorio**](https://github.com/Fabian-Martinez-Rincon/Taller-de-Programacion)

Para Para, antes de aprender lo practico tenemos que leer bien las diapositivas que estan en el repositorio de arriba, rendi el final a principios del 2023 y me dijo que el practico es de 10 pero que no pegue una en la teoria y por eso desaprobe esa fecha. MUCHO CUIDADO 

# Imperativo

Primero damos la ordenación de vectores. En este caso, lo vamos a usar cada vez que el enunciado nos solicite retornar un vector ordenado por x campo. Con aprenderse uno de los dos estamos bien (a mi me gusta mas el de selección)

<table><tr><td>Selección</td><td>Inserción</td></tr><tr><td>

{% highlight pascal %}
  Procedure Seleccion (var v:vector; dimL:Integer);
  var 
      i, j, p: Integer;
      item:integer;
  begin
      {busca el mínimo y guarda en p la posición}
      for i:=1 to dimL-1 do 
      begin 
          p := i;
          for j := i+1 to dimL do
              if v[ j ] < v[ p ] then p:=j;
          {intercambia v[i] y v[p]}
          item := v[ p ];   
          v[ p ] := v[ i ];   
          v[ i ] := item;
      end;
  end;
{% endhighlight %}

</td><td>

{% highlight pascal %}
  Procedure Insercion (var v:vector; dimL:Integer);
  var 
      i, j: Integer; 
      actual:integer;
  begin
      actual:=0;
      for i:=2 to dimL do 
      begin 
          actual:= v[i];
          j:= i-1; 
          while (j > 0) and (v[j] > actual) do
          begin
              v[j+1]:= v[j];
              j:=j-1;
          end;  
          v[j+1]:= actual; 
      end;
  end;
{% endhighlight %}
</td></tr>
</table>

En el de **Selección** tenemos dos for anidados, dentro un if para hacer el ordenamiento donde i y j son las posiciones que recorremos y p seria auxiliar para el intercambio. El primer for es de 1 hasta DimL-1 y el segundo for es de i+1 hasta DimL

--- 

Podriamos mandarle a recursión pero eso con una repasada estamos bien, aca lo importante son los **recorridos** del arbol y el **crear** nada más.

### Crear

```pascal
  Procedure crear (var A:arbol; num:integer);
  Begin
    if (A = nil) then
    begin
      new(A);
      A^.dato:= num; 
      A^.HI:= nil; 
      A^.HD:= nil;
    end
    else
      if (num < A^.dato) then 
        crear(A^.HI,num)
      else 
        crear(A^.HD,num)   
  End;
```

Si el arbol esta vacio, agregamos el elemento de forma normal, en caso de que no, preguntamos si el elemento es menor que el dato actual y lo llamamos recursivamente con el **Hijo Izquierdo** en caso contrario, lo mandamos con el **Hijo Derecho**

### Imprimir

Tenemos tres formas de imprimir, con aprender una estamos bien
- **En Orden** El imprimir en el medio
- **Pos Orden** El imprimir al principio
- **Pre Orden** El imprimir al final

```pascal
//Input 1,22,3,44,5,6,7,2,0
Procedure enOrden( a:arbol );
begin 
  if (a <> nil) then begin
    enOrden(a^.HI);
    write(a^.dato,'|');
    enOrden(a^.HD);
  end;
end;
//1,2,3,5,6,7,22,44
```

---

### Merge

En resumen, agarramos n listas/arreglos que esten ordenados por el mismo criterio y los volvemos uno solo. Tenemos dos tipos de merge, el merge común, el mergue acumulador, que es lo mismo que el normal pero con un corte de control.

#### Merge Normal

```pascal
procedure merge(v:vector; var l:lista);
var
   min:string;
   ult:lista;
begin
	minimo(v,min);
	while (min <> 'ZZZ') do 
		begin
			AgregarAlFinal2(l,ult,min);
			minimo(v,min);
		end;
end;
```
Recibimos  un vector de listas y este al estar ordenado, lo agregamos a la lista nueva (Vamos a tener que recordar el agregar de listas)

#### Merge Acumulador

```pascal
procedure merge(var l :lista_nueva;v:vector) ;
var
	ult : lista_nueva;
	min, actual : venta_nueva;
begin
	minimo(v,min);	
	while (min.codigo <> 9999) do	
	begin
		actual.cant := 0;	
		actual.codigo := min.codigo;	
		while (min.codigo <> 9999) and (min.codigo = actual.codigo) do begin
			actual.cant:= actual.cant + min.cant;	
			minimo(v,min);	
		end;
		AgregarAlFinal2(l,ult,actual);	
	end;
end;
```

---

### Los minimos

Tenemos este minimo que es para el merge normal. Inicializamos un minimo, recorremos la primera posición de cada lista en el arreglo para quedarnos con la posición, y al final de todo avanzamos en esa posición

```pascal
procedure minimo(var v : vector; var min : string);
var
   pos, i : integer;
begin
	min := 'ZZZ';
	pos := -1;
	for i:= 1 to dimF do					
		if (v[i] <> nil) and (v[i]^.dato <= min) then begin
			min := v[i]^.dato; 
			pos := i;	
		end;
	if (pos <> -1) then  
		v[pos] := v[pos]^.sig;
end;
```

Este seria el minimo para el acumulador, es basicamente lo mismo pero con mas campos.

```pascal
procedure minimo(var v:vector; var x:venta_nueva);
var 
  i, pos : integer;
begin
	x.codigo := 9999;
	pos := -1;
	for i := 1 to cantidad do 
		if (v[i] <> NIL) and (v[i]^.dato.codigo <= x.codigo) then 
		begin
			pos := i;	
			x.codigo := v[i]^.dato.codigo;
            x.cant:=v[i]^.dato.cantidad_vendida;	
		end;

	if (pos <> -1) then
	begin
      x.codigo := v[pos]^.dato.codigo;
      x.cant := v[pos]^.dato.cantidad_vendida; 
      v[pos] := v[pos]^.sig; 
	end;
end;
```

Y con esto terminamos imperativo

---

# Concurrente

Este lenguaje es horrible pero no queda otra que aprenderlo para el final, igual es una boludes.

La estructura es la siguiente

- programa nombre
- procesos (son las funciones E valor ES referencia)
- robots
