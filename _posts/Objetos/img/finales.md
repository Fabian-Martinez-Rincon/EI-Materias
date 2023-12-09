## Final 04/08/2023

La municipalidad de la ciudad de La Plata necesita un sistema que le permita recolectar las denuncias realizadas por los ciudadanos. La denuncia la hace cualquier ciudadano y al hacerlo debe proporcionar la categoria de denuncia (1: corte de luz en la via publica; 2: auto mal estacionado; 3: recolección de reciduos; 4: Ruidos molestos; 5: Semáforo en malfuncionamiento; 6: bache en la calle), su DNI, la dirección  (número de calle y número de altura) y el mes, dia y hora.

Implemente en pascal:
- **a)** Un módulo que genere el alta de todas las denuncias almacenando toda la información en una estructura agrupada por categoría y ordenada por número de calle. La carga finaliza hasta leer el DNI igual a cero.
- **b)** Un módulo que reciba la estructura generada en a) y devuelva una lista de denuncias donde para cada nro de calle se contabilice cantidad de denuncias totales y cantidad de denuncias realizadas en el mes de julio.
- **c)** Un módulo recursivo que reciba la estructura generada en b) y devuelva el número de calle con mayor cantidad de denuncias

## Final 12/10/2023 Imperativo

Un lugar nos ofrece sus instalaciones para que las bandas de música puedan dar sus recitales. De cada recital se conoce: El nombre de la banda, la fecha del recital, la cantidad de canciones tocadas y el monto recaudado por la venta de entradas.

- **a)** Implemente un módulo que lea registros de recitales de manera sucesiva hasta que se `ingrese ZZZ` como nombre de banda. Los recitales se pueden leer en cualquier orden. Todos los recitales leídos deben almacenarse en una estructura que permita el recorrido óptimo por monto recaudado.
- **b)** Implemente un módulo que reciba la estructura cargada y dos valores (ej 200 y 500) y devuelva una lista con todos los recitales cuyo monto recaudado se encuentra entre esos dos valores leidos (ambos inclusive). La lista resultante debe estar ordenada por monto de mayor a menor.
- **c)** Implemente un **módulo recursivo** que reciba la lista creada en b) y devuelva la cantidad de recitales que tocaron más de 12 canciones.
