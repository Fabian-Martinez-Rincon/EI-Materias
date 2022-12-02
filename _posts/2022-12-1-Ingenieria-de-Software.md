---
layout: post
title: 🛠 Ingenieria de software Resumen 📋
subtitle: Parciales resueltos de la cursada
cover-img: /assets/img/PortadasEditadas/Ingenieria2.jpg
thumbnail-img: /assets/img/logos/Ingenieria.png
share-img: /assets/img/PortadasEditadas/Ingenieria2.jpg
tags: [Ingenieria de software 1, Historias de usuario, Casos de Uso]
---

## Ingenieria de Software 1 

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



