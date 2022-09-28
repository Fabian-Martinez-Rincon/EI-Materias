# Busqueda de Metodos en Java
- [Pagina anterior](/OO1/)
- [Method Lookup](#method-lookup)
- [Method Lookup con herencia](#method-lookup-con-herencia)
- [Sobre escribír metodos (overriding)](#sobre-escribír-metodos)
- [Extender Métodos](#extender-métodos)
- [Super](#super)
- [Super y el Method Lookup](#super-y-el-method-lookup)
- [Super() en los constructores](#super-en-los-constructores)


## Method Lookup

Antes de avanzar con super, recordemos primero que ocurre cuando un objeto recibe un mensaje (cuando alguien invoca un metodo de un objeto)

Cuando un objeto recibe un mensaje, todos los objetos son instancias de clases, lo que pasa es que algun objeto va a buscar a la clase de ese objeto (a la clase de esa instancia) un metodo que corresponda con el mensaje que se le envio (un metodo que se llame igual y que tenga los parametros en el mismo orden). 

![image](https://user-images.githubusercontent.com/55964635/192359878-c98013e6-ff36-48eb-b934-488414bec1ec.png)

Cuando tengo un error al querer mandarle mensajes a objetos que no van a entender, porque no hay ningun metodo en su clase que se corresponda con el mensaje, los encuentra el compilador

```java
new Luz().encender();
new Calefaccion().encender();
new Puerta().`enceder`(); 
```

En esta instancia de Puerta, le envio encender y el compilador ya sabe que mi objeto Puerta, no posee el metodo encender (Directamente no nos deja compilar), mientras que con los otros dos ejemplos que tengo, el compilador los va a dejar pasar porque, chequea que los objetos pudieron entender los mensajes recibidos.

## Method Lookup con herencia

| Explicación  | Grafico |
| ------------- | ------------- |
| Cuando un objeto recibe un mensaje, se busca en su clase un método cuya firma se corresponda con el mensaje. Si no lo encuentra, sigue buscando en la superclase de su clase, y en la superclase de esta..  | <img width="1020"   src = 'https://user-images.githubusercontent.com/55964635/192593948-5ef01c06-4db4-461f-819e-7618228fbbfc.png'>  |


```java
new Luz().encender();
new Calefaccion().encender();
```

## Sobre escribír metodos

- La búsqueda en la cadena de superclases termina tan pronto encuentro un método cuya firma coincide con la que busco.
- Si heredaba un método con la misma firma, el mismo queda 'oculto'

<img width="142" align='right'  src = 'https://user-images.githubusercontent.com/55964635/192596770-db030a56-4833-4473-940e-d75160026415.png'>

```java
public void actionOne(){ // Metodo de A
    // Hacer algo como le gusta a A
}

public void actionOne(){ // Metodo de B
    // Hacer algo como le gusta a B
}
```

 

 



```java
new B().actionOne();
```
Aca tengo una instancia de B y esa instancia le digo 'actionOne', va a su clase a buscar el metodo actionOne, lo encuentra y lo ejecuta, FIN. El problema de esto es que nadie sabe que tenemos ese mismo metodo en la clase A, entonces decimos que se sobre Escribe ese metodo o queda oculto (no es muy frecuente usar la sobre escritura de metodos ya que la mayoria de las herencias siguen la logica de 'esUn')


## Extender Métodos
Pensemos en el caso de que B no tiene problemas del comportamiento que hereda, como en el caso anterior que practicamente hacia una cosa totalmente distinta y se perdia información.
En este caso, hace lo que hereda sin perder información pero tambien puede hacer más.

<img width="152" align='left'  src = 'https://user-images.githubusercontent.com/55964635/192596770-db030a56-4833-4473-940e-d75160026415.png'>



```java
public void actionOne(){ // Metodo de A
    // Hacer algo como le gusta a A
}

public void actionOne(){ // Metodo de B
    // Hacer algo como le gusta a B
    // Hacer algo como le gusta a A
    // Hacer algo como le gusta a B
}
```

```java
new B().actionOne();
```


## Super
- **Podemos pensar a super** como una `pseudo-variable` (como this)
    - no puedo asignarle valor
    - Toma valor automáticamente cuando un objeto comienza a ejecutar un método
- En un método, '**super y this**' hacer referencia al objeto que ejecuta (al receptor del mensaje)
- Utilizar super en lugar del this 'solo cambia la forma en la que se hace el method lokup'
- Se utiliza para:
    - Solamente para extender comportamiento heredado (reimplementar un método e incluir el comportamiento que se heredaba para él)

## Super y el Method Lookup

<img width="132" align='left'  src = 'https://user-images.githubusercontent.com/55964635/192617819-bb67dd5b-9a90-47ae-b8aa-f27a7db6d6c8.png'>

Cuando **super** recibe un mensaje, la búsqueda de métodos comienza en la clase **inmediata superior** a aquella donde está definido el método que envía el mensaje(sin importar la clase del receptor)

```java
public void actionOne(){
    this.actionTwo();
    super.actionOne();
    this.actionTwo();
}
```
<br>
<br>
<br>
<br>
<br>
<br>

- new A().actionOne(); 
    - Lo busca, lo encuentra y lo ejecuta 👍
- new B().actionOne();
    - Ejecuta el actionOne de abajo, el actionTwo propio
    - Despues el actionOne
    - Del padre (A) y por ultimo el actionTwo propio otra vez
- new C().actionOne();
    - Como no encuentra el metodo lo busca en el padre (B)
    - Ejecuta actionTwo() de la clase C, por el this
    - Cuando un objeto recibe un mensaje y a este lo referian como super, la busqueda del metodo comienza en la clase superior a aquella en donde esta el metodo que dice 'super'
    - el metodo que dice super esta en B, entonces empieza a buscar en A


## Super() en los constructores
- Los constructores en Java son subrutinas que se ejecutan en la creación de objetos
- No se heredan
- Si quiero reutilizar comportamiento de otro constructor debo imbocarlo explícitamente
    - Uso super(...) para invocar un constructor en la superclase de mi clase
