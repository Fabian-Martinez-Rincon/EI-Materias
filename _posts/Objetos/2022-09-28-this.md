---
layout: post
title: Un poco más respecto al this
tags: [this, objetos, java]
---


# Un poco más respecto al `this`

- [This](#this)
- [This y el method lookup](#this-y-el-method-lookup)
- [Reutilizar comportamiento repetido](#reutilizar-comportamiento-repetido)
- [Aprovechar comportamiento heredado](#aprovechar-comportamiento-heredado)
- [Descomponer métodos largos](#descomponer-métodos-largos)

## This
- **this** (en algunos lenguajes seft) es una `pseudo-variable`
    - No puedo asignale valor
    - Toma valor automáticamente cuando un objeto comienza a ejecutar un método
- **this** hace referencia al objeto que ejecuta el método (al receptor del mensaje que resultó en la ejecución del método)
- Se utiliza para:
    - Reutilizar comportamiento repetido en varios métodos
    - Aprovechar comportamiento heredado
    - Descomponer métodos largos (top down)
- En algunos lenguajes (p.e java):
    - Puede obviarse (es implíto), aunque en OO1 preferimos no hacerlo
    - Para desambiguar referencia a las variables de instancia del objeto

## This y el method lookup

Cuando **this** recibe un mensaje, la búsqueda de métodos comienza en la clase de la cual **this** es instancia (sin importar donde está el método en el que se le envía el mensaje)

<img align='right' src = 'https://user-images.githubusercontent.com/55964635/193175787-d02aa844-30aa-4e01-a139-e692e6e9ff5c.png'>

```java
new A().actionTwo();
```
En este primer ejemplo, estamos creando una instancia pero lo que no podemos es enviarle el mensaje actionTwo, ya que este metodo no pertenece ni a `A` ni a ninguna super clase de esta.


```Java
new B().actionTwo();
```

Va a su clase a buscar el metodo que corresponda, lo encuenttra y lo ejecuta. Ya está

```java
new C().actionTwo();
```
La instancia de C, recibe el mensaje actionTwo(), va a su clase `C` a buscar el metodo, no lo encuentra, lo encuentra en su super clase `D`, el this que tenemos en el metodo actionTwo(), pasa a apuntar al mentodo actionOne, de la clase `C`, ya que el **this** pasa a ejecutar la instancia que esta ejecutando el metodo

```java
public void actionTwo(){
    this.actionOne();
}
```

Bien, no importa en donde este implementado el metodo, **this** siempre apunta al objeto que recibe el mensaje.

## Reutilizar comportamiento repetido

```java
//Moverse
public void translateBy (Point2D point){
    this.position.translateBy(point);
    this.disableShields();
    this.energy -= 1;
}

// Disparar
public void fireUpon (Ship ship){
    ship.takeFireFrom(this.position)
    this.disableShields();
    this.energy -= 1;
}
```

Lo que noto en estos dos metodos, es que las ultimas dos lineas son repetidas. Entonces lo que hacemos en este caso, es en la parte que es comun, llevarla a otro metodo. Ya que estas lineas solo estan para repetirle constantemente.

```java
private void payThePrice(){
    this.disableShields();
    this.energy -= 1;
}
```
Como resultado tenemos el siguiente codigo.

```java
//Moverse
public void translateBy (Point2D point){
    this.position.translateBy(point);
    this.payThePrice();
}

// Disparar
public void fireUpon (Ship ship){
    ship.takeFireFrom(this.position)
    this.payThePrice();
}
```

## Aprovechar comportamiento heredado
![image](https://user-images.githubusercontent.com/55964635/193178784-15e25248-c011-453f-8c2f-8f984ce1bc39.png)


## Descomponer métodos largos




