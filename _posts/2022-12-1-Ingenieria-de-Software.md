---
layout: post
title: 🛠 Ingenieria de software Parciales 📋
cover-img: /assets/img/PortadasEditadas/IngenieriaNueva.png
thumbnail-img: /assets/img/logos/Portada.png
share-img: /assets/img/PortadasEditadas/IngenieriaNueva.png
tags: [Ingenieria de software 1, Historias de usuario, Casos de Uso]
---

- Tenemos que poner el cuadrado
- Las cosas que interactuan directamente con el sistema
- Si tengo el `actor 2` debajo del `actor 1` significa que el `actor 2` puede hacer todo lo que hace el `actor 1`, mas las cosas que puede hacer el `actor 2`
- **Flecha Normal** Significa que el actor ejecuta el caso de uso
- **\<uses>** El CU 1 utiliza al CU 5 (que seria el apuntado) se utiliza cuando tenemos mas de un CU que utilizan un CU
- **\<Extend>** en caso de que sea una simple extensión
- **Linea sin flecha** el actor interactua en el CU
- Usar gerarquias para los casos de uso que lo ocasionan dos actores distintos
- Siempre empieza el actor, a no ser de que tengamos algun extend con el sistema
- Mostramos como interactua el actor con el sistema
- Podemos poner como precondicion que el usuario tenga una sesion iniciada sin haberla graficado.
- En los casos en los que mi CU tenga un CU que lo extiende, tenemos que agregar en los pasos del sistema. El sistema ejecuta el caso de uso "Pagar con tarjeta" por ejemplo
 

# La Start Historias de Usuario

## Parcial Primera Fecha

Ingeniería de Software 2022 - Parcial primera fecha - Sábado 22/10/2022

### 1. Historias de usuario

Realice las tarjetas completas de las historias de usuario identificadas en el siguiente dominio.
Se desea modelar un sistema web para un portal de noticias.

Cualquier persona puede acceder a ver las noticias publicadas en el sitio. Para
mostrar el listado de noticias el sistema se conecta con un servidor proveedor
para lo cual, solicita conexión y envía un token de seguridad, si el token es
correcto el server retorna un conjunto de noticias en formato json el cual es
recibido porel sistema, convertido a formato html y mostrado en pantalla.
Aquellos usuarios registrados en el sistema, además podrán acceder a un detalle de cada noticia
publicada. Solo podrán registrarse mayores de 18 años y el registro no tiene costo. Para el registro
se necesita nombre, apellido, edad y mall (debe ser único y es utilizado como nombre de usuario). El -
sistema deberá generar una contraseña de manera aleatoria y enviarla al correo ingresado. Sólo se
permite acceder al detalle de 5 noticias por día

Para acceder al detalle de una noticia se debe estar autenticado previamente, para lo cual cada
usuario tiene 3 intentos. Si falla 3 veces al intentar autenticarse el sistema deberá bloquear la
cuenta.

### 2. Casos de uso
Realice los escenarios y el diagrama completo de los casos de uso identificados en el dominio
anterior.


---

## Parcial Segunda Fecha

### Historias de Usuario

Realice las tarjetas completas de las historias de usuario identificadas en el siguiente dominio (Salvo iniciar y cerrar sesión)

Se desea modelar un sistema para el manejo de alquiler de car
pas para fiestas. Cualquier persona puede pedi
presupuesto. Para esto deber seleccionar el tipo de capa a presupuestar, cantidad de personas, y fecha del evento
(debe ser dentro del año actual). Si hay disponibilidad se genera un código, se imprime el presupuesto y se reserva la
carpa por 48hs (validez del presupuesto). Pasadas las 48hs si la reserva no se hizo efectiva otro sistema se encarga de liberarla.

Los clientes deben loguearse para poder alqullar o hacer pagos. Esto requiere una registración. Para registrarse, el
sistema solicita nombre, apellido, fecha de nacimiento, dni (único y utlizado como nombre de usuario), dirección de
correo electrónico y contraseña (debe ser de 6 caracteres o más). Una vez que se completa el registro el sistema
envía un mensaje de bienvenida al correo ingresado. Sólo se permite el registro de personas mayores de 21 años.

Para alquilar una carpa, el cliente deberá ingresar el código de presupuesto la dirección y la seña a pagar (no menor
al 50% y hasta el 100% del monto presupuestado). La seña se debe abonar a través de tarjeta de crédito (Unico
medio de pago) para lo cual es necesario conectarse con un servidor externo. El cliente debe ingresar el número de
Tarjeta, la fecha de vencimiento y el código de seguridad de la tarjeta. Una vez abonada la seña el sistema envía un
comprobante con el número de alquiler y el monto restante a pagar al correo del cliente.

 

En cualquier momento, el cliente podrá pagar el resto del alquiler ingresando el número de alquiler, El pogo también
se realizará a través de la tarjeta de crédito (tener en cuenta que podria haber abonado el 100%))

### Casos de Uso

![1](https://user-images.githubusercontent.com/55964635/205096308-5808f9f7-99d8-40d8-82ba-c6a0f3b686e0.jpeg)
