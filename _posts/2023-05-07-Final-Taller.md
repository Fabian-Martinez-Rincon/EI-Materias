---
layout: post
title: 💻 Taller de Programación Final
subtitle: Resumen para el final
cover-img: /assets/img/PortadasEditadas/Taller.png
thumbnail-img: /assets/img/logos/taller2.png
share-img: /assets/img/PortadasEditadas/Taller.png
tags: [Taller De Programación, Java, Pascal, R-INFO]
---

En este resumen voy a poner codigo de R-Info y de Pascal ya que son los temas mas "dificiles" de aprobar sin estudiar. Si necesitas los recursos de la materia, los podes encontrar en este [**repositorio**](https://github.com/Fabian-Martinez-Rincon/Taller-de-Programacion)

### Imperativo

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

En el de **Selección** tenemos dos for anidados, dentro un if para hacer el ordenamiento donde i y j son las posiciones que recorremos y p seria auxiliar para el intercambio. El primer for de de 1 hasta dimL-1 y el segundo for es de i+1 hasta DimL

