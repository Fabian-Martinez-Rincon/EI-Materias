---
layout: post
title: ⌨️ Diseño de Base de Datos Resumen
cover-img: /assets/img/portadaObjetos.jpg
thumbnail-img: /assets/img/sql.jpg
share-img: /assets/img/portadaObjetos.jpg
tags: [sql, visual studio, sql server]
---


# Conceptual

#### Enunciado
Diseño de Bases De Datos- Examen práctico- Primer Fecha- Tema 1- 8/11/2022

Importante: Consignar en primer hoja: nombre, apellido, legajo, tema de examen, turno de práctica, temas rendidos y cantidad de hojas entregadas, En restantes hojas poner legajo y nro hoja/total hojas

¿Modelado conceptual - (Tema 1)

Se debe modelar mediante modelo conceptual la información necesaria para un sistema encargado
de las ventas de una papelera.

La papelera cuenta con varios puntos de venta de los cuales se conoce: número único de punto de
venta, dirección detallada, teléfonos y empleados que trabajan en el punto de venta. Un empleado
puede ser repositor, vendedor o administrativo. De todos los empleados se conoce: D.N.I, apellidos,
nombres y C.U.LT. De los repositores se conoce además la edad; de los vendedores se conocen los
títulos, en caso de que posean y de los administrativos se registra el número de pasaporte. Un empleado trabaja en un único punto de venta en un momento determinado pero puede rotar entre los diferentes puntos de venta a lo largo del tiempo. Es necesario conocer el historial de rotaciones
de cada empleado en los diferentes puntos de venta de manera cronológica.

Cada punto de venta tiene información de los productos que comercializa, de cada producto se
registra: precio actual [precio de compra] código de producto (puede repetirse para diferentes puntos
de ventas pero no en el mismo punto de venta)| stock actual] stock mínimo, descripción y ubicación.


Para las ventas es necesario almacenar: nro ticket fiscal, precio total de la venta, fecha de la venta,
iproductos comprados, vendedor que realizó la venta, cliente involucrado y una descripción de la
forma de pago. Si la venta es con tarjeta de crédito es necesario además, guardar la cantidad de
¡cuotas en que se realiza el pago y el interés aplicado. Tenga en cuenta que es posible que en un
futuro se consulte a cuánto se vendió un determinado producto en una venta determinada.

En cambio, para las compras se debe almacenar código único de comprá, fecha, productos
involucrados, precio total y proveedor. Tenga en cuenta que es posible que en un futuro se consulte
a cuánto se compró un determinado producto en una compra X. 
De cada proveedor se conoce: razón social, C.U.I.T, posición frente a la afip, nombre de fantasía (puede no tener), dirección
detallada, teléfono y mail.


Por último de los clientes se conoce D.N.I, apellidos, nombres y C.U.1,T. Los empleados de la papelera pueden ser clientes.

---

- **Punto de venta**
    - número unico (Identificador)
    - dirección detallada
    - (0,n) teléfonos
    - 1,n \<trabaja> empleados
    - 1,n \<tiene> productos 
- **Persona**
    - D.N.I 
    - apellidos
    - nombres
    - C.U.I.T
- **Cliente**
- **Empleado** 
    - +repositor
        - edad
    - +vendedor
        - (0,n) titulos
    - +administrativo
        - nroPasaporte
    - \<trabaja> 1,1 punto de venta
- **\<trabaja>**
    - FechaInicio
    - (0,1) FechaFin
- **Producto**
    - precio actual
    - precio de compra
    - código de producto (puede repetirse para diferentes puntos de ventas pero no en el mismo punto de venta) \<idExterno>
    - stock actual 
    - stock mínimo
    - descripción
    - ubicación.
- **Venta**
    - nro ticket fiscal (Identificador)
    - precio total de la venta
    - fecha de la venta
    - <tiene> 1,n productos comprados
    - <tiene> 1,1 vendedor que realizó la venta
        - Fecha
    - <tiene> 1,1 cliente involucrado 
    - descripción forma de pago
    - (0, 1) cantidad de cuotas
    - (0, 1) interés aplicado
- **Compra**
    - código único de comprá
    - fecha
    - \<compro> productos involucrados
        - Precio Compra
    - precio total
    - (1, 1) <tiene> proveedor
- **proveedor** 
    - razón social (identificador)
    - C.U.I.T (identificador)
    - posición frente a la afip
    - (0, 1) nombre de fantasía (puede no tener)
    - dirección detallada
    - teléfono 
    - mail

![3](https://user-images.githubusercontent.com/55964635/204157808-2491b5e1-bade-4d07-b87b-9817a4fe1f8a.jpg)


# Logico-Fisico

![image](https://user-images.githubusercontent.com/55964635/204159760-6a40c834-60c0-4443-8681-6c90018fcf82.png)

## Sql
- [Insertar](#insertar)
- [Eliminar](#eliminar)
- [Actualizar](#actualizar)

### Insertar
### Eliminar
### Actualizar

