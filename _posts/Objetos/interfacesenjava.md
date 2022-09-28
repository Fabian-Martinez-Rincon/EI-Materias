# Interfaces en Java y UML
- [Pagina anterior](/OO1/)

- Tipo = Conjunto de firmas de operaciones/metodos (nombre, tipos de argumentos, tipo de resultado)
- Decimos que un objeto "es de un tipo" su ofrece el conjunto de operaciones definidas por el tipo.
- Con esto en mente:
  - Cada clase en java define "explicitamente" a un tipo (es un conjunto de firmas de operaciones)
  - Cada instancia de una clase A (o de cualquier subclase) "es del tipo" definido por esa clase
  - Pero ...  las clases no son la unica forma de definir tipos.

## Los tipos y el compilador

- Java es un lenguaje fuertemente tipado.
  - Debemos indicar el tipo de todas las variables
- El compilador utiliza informacion de tipos para asegurarse de que no enviamos mensajes a objetos que no los entienden
- Cuando declaramos el tipo de una variable, el compilador controla que solo enviemos a esa variable mensajes acordes a ese tipo.
- Cuando asignamos un objeto a una variable, el compilador controla que el tipo del objeto sea compatible con el de la variable.

