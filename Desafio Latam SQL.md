### **Agrupando valores con GROUP BY**
La cláusula GROUP BY es una poderosa herramienta en SQL que se utiliza para agrupar filas con valores idénticos en una o varias columnas específicas, permitiendo realizar operaciones de agregación en cada grupo.

En este primer ejercicio aprenderemos a utilizar GROUP BY para obtener todos los elementos distintos de una tabla, lo mismo que previamente hicimos con distinct.

Tenemos la siguiente tabla colores:

|**COLOR**|
| :- |
|Rojo|
|Azul|
|Verde|
|Amarillo|
|Naranja|
|Morado|
|Rosa|
|Café|
|Gris|
|Negro|
|Blanco|
|Rojo|
|Azul|
|Verde|
|Amarillo|

Podemos seleccionar los elementos únicos utilizando GROUP BY de la siguiente forma:

SELECT color as color\_unico FROM colores GROUP BY color

Como resultado obtendremos:

|**COLOR**|
| :- |
|Amarillo|
|Azul|
|Blanco|
|Café|
|Gris|
|Morado|
|Naranja|
|Negro|
|Rojo|
|Rosa|
|Verde|
## **Ejercicio**
Dada la siguiente **tabla de usuarios**

|**CORREO**|
| :- |
|<juan.perez@empresa.com>|
|<maria.gonzalez@empresa.com>|
|<carlos.rodriguez@empresa.com>|
|<ana.martinez@empresa.com>|
|<luis.garcia@empresa.com>|
|<carmen.lopez@empresa.com>|
|<jose.hernandez@empresa.com>|
|<francisco.martin@empresa.com>|
|<laura.sanchez@empresa.com>|
|<antonio.diaz@empresa.com>|
|<juan.perez@empresa.com>|
|<maria.gonzalez@empresa.com>|

Crea una consulta que nos muestre cada correo una única vez. La columa mostrada debe llamarse correo\_unico

Select correo as correo\_unico from usuarios group by correo



### Agrupar y contar
GROUP BY es comúnmente utilizada junto con funciones de agregación como COUNT, MAX, MIN, SUM y AVG para obtener información resumida de un conjunto de datos.

En este ejercicio aprenderemos a agrupar y contar.

Tenemos la siguiente tabla colores:

|**COLOR**|
| :- |
|Rojo|
|Azul|
|Verde|
|Amarillo|
|Naranja|
|Morado|
|Rosa|
|Café|
|Gris|
|Negro|
|Blanco|
|Rojo|
|Azul|
|Verde|
|Amarillo|

Queremos saber cuantas veces aparece cada color. Esto lo podemos lograr combinando GROUP BY y la función de agregación COUNT

SELECT color, COUNT(color) as Repeticiones FROM colores GROUP BY color

|**COLOR**|**REPETICIONES**|
| :- | :- |
|Amarillo|2|
|Azul|2|
|Blanco|1|
|Café|1|
|Gris|1|
|Morado|1|
|Naranja|1|
|Negro|1|
|Rojo|2|
|Rosa|1|
|Verde|2|
## **Ejercicio**
Dada la siguiente **tabla de usuarios**

|**CORREO**|
| :- |
|<juan.perez@empresa.com>|
|<maria.gonzalez@empresa.com>|
|<carlos.rodriguez@empresa.com>|
|<ana.martinez@empresa.com>|
|<luis.garcia@empresa.com>|
|<carmen.lopez@empresa.com>|
|<jose.hernandez@empresa.com>|
|<francisco.martin@empresa.com>|
|<laura.sanchez@empresa.com>|
|<antonio.diaz@empresa.com>|
|<juan.perez@empresa.com>|
|<maria.gonzalez@empresa.com>|

Crea una consulta que nos muestre cada correo una única vez junto a la cantidad de repeticiones. Las columnas deben llamarse correo y repeticiones.


select correo, count(\*) as repeticiones from usuarios group by correo


### Ejercitando agrupar y contar
## **Ejercicio**
Dada la siguiente **tabla empleados**

|**NOMBRE**|**APELLIDO**|**SUELDO**|**DEPARTAMENTO**|
| :- | :- | :- | :- |
|Juan|Pérez|3000|Ventas|
|María|González|3500|Marketing|
|Carlos|Rodríguez|4000|Tecnología|
|Ana|Martínez|2800|Recursos Humanos|
|Luis|García|3200|Finanzas|
|Carmen|López|3100|Administración|
|José|Hernández|2900|Operaciones|
|Francisco|Martín|3400|Legal|
|Laura|Sánchez|3300|Compras|
|Antonio|Díaz|3600|Producción|
|Sofía|Ruiz|2750|Ventas|
|Jorge|Vargas|3900|Tecnología|
|Elena|Castro|3050|Marketing|
|Pedro|Ortega|3150|Finanzas|

Se pide contar cuantas personas trabajan en cada departamento. Las columnas resultantes deben llamarse departamento y cantidad\_empleados

select departamento, count(\*) as cantidad\_empleados from empleados group by departamento



### Agrupar y sumar
En este ejercicio agruparemos y sumaremos. La lógica de la consulta es la misma previamente mencionada, solo cambia la funcion de agrupacion a utilizar. Por ejemplo, tenemos la tabla pedidos con los siguientes datos:

|**CLIENTE**|**MONTO**|
| :- | :- |
|Cliente A|1200|
|Cliente A|800|
|Cliente B|150|
|Cliente C|200|
|Cliente B|90|

Si queremos calcular cuanto ha gastado cada cliente, podemos realizar la siguiente consulta

SELECT Cliente, SUM(Monto) AS Monto\_Total FROM pedidos GROUP BY Cliente;
## **Ejercicio**
Utilizando la siguiente **tabla ventas** de una empresa, crea una consulta que muestre cuanto se vendió en total por cada cateogría. Las columnas de la consulta deben llamarse categoria y monto\_total

|**PRODUCTO**|**MONTO**|**CATEGORIA**|
| :- | :- | :- |
|Laptop Pro|1200|Electrónicos|
|Smartphone X|800|Electrónicos|
|Silla Ergo|150|Mobiliario|
|Mesa de Café|90|Mobiliario|
|Reloj Elegante|250|Accesorios|
|Bolso de Viaje|70|Accesorios|
|Zapatillas Run|100|Ropa|
|Camisa Casual|40|Ropa|
|Licuadora Max|60|Electrodomésticos|
|Horno Compacto|110|Electrodomésticos|
|Libro de Cocina|20|Libros|
|Novela Misterio|15|Libros|
|Audífonos Plus|50|Electrónicos|
|Lámpara Moderna|45|Mobiliario|
|Laptop Pro|1200|Electrónicos|
|Silla Ergo|150|Mobiliario|
|Bolso de Viaje|70|Accesorios|
|Zapatillas Run|100|Ropa|


SELECT categoria, SUM(Monto) AS Monto\_Total FROM ventas GROUP BY categoria;



### Agrupar y promediar
Previamente aprendimos que AVG nos permite calcular el promedio de los elementos de una columna en una tabla. En este ejercicio lo utilizaremos para calcular promedios por grupo.

SELECT grupo, AVG(columna) FROM tabla GROUP by grupo
## **Ejercicio**
Dada la siguiente tabla de **estudiantes**

|**NOMBRE\_COMPLETO**|**NOTA**|
| :- | :- |
|Juan Pérez|7|
|Juan Pérez|8|
|Juan Pérez|6|
|María Rodríguez|9|
|María Rodríguez|7|
|María Rodríguez|8|
|Carlos García|6|
|Carlos García|5|
|Carlos García|7|
|Ana Fernández|8|
|Ana Fernández|9|
|Ana Fernández|8|
|Luis Morales|7|
|Luis Morales|6|
|Luis Morales|5|

Encuentra el promedio de notas de cada estudiante. Las columnas deben tener el nombre de Nombre\_Completo y Promedio\_Notas respectivamente.

Este ejercicio tiene un supuesto importante: que no hay dos estudiantes con el mismo nombre y apellido. Discutiremos este tipo de supuestos más adelante cuando revisemos el concepto de integridad.

SELECT nombre\_completo, AVG(nota) as promedio\_notas FROM estudiantes GROUP by nombre\_completo

### Máximo por grupo
En este ejercicio combinaremos la función de agregación MAX() con group by para poder obtener el monto mas alto de cada grupo. La sintaxis de la consulta será igual a las vistas previamente, es decir:

SELECT grupo, MAX(columna) FROM tabla GROUP by grupo
## **Ejercicio**
Dada la siguiente **tabla de ventas**:

|**PRODUCTO**|**MONTO**|**CATEGORIA**|
| :- | :- | :- |
|Laptop Pro|1200|Electrónicos|
|Smartphone X|800|Electrónicos|
|Silla Ergo|150|Mobiliario|
|Mesa de Café|90|Mobiliario|
|Reloj Elegante|250|Accesorios|
|Bolso de Viaje|70|Accesorios|
|Zapatillas Run|100|Ropa|
|Camisa Casual|40|Ropa|
|Licuadora Max|60|Electrodomésticos|
|Horno Compacto|110|Electrodomésticos|
|Libro de Cocina|20|Libros|
|Novela Misterio|15|Libros|
|Audífonos Plus|50|Electrónicos|
|Lámpara Moderna|45|Mobiliario|
|Laptop Pro|1200|Electrónicos|
|Silla Ergo|150|Mobiliario|
|Bolso de Viaje|70|Accesorios|
|Zapatillas Run|100|Ropa|

Crea una consulta para calcular el monto mas alto por cada categoría. La tabla resultante debe tener dos columnas:categoria y monto\_mas\_alto.

SELECT categoria, MAX(monto) as monto\_mas\_alto FROM ventas GROUP by categoria


### Mínimo por grupo
En este ejercicio combinaremos la función MIN() con GROUP BY para poder obtener el monto mas bajo de cada grupo.La sintaxis de la consulta será igual a las vistas previamente, es decir:

SELECT grupo, MIN(columna) FROM tabla GROUP by grupo
## **Ejercicio**
Dada la tabla **ventas**:

|**PRODUCTO**|**MONTO**|**CATEGORIA**|
| :- | :- | :- |
|Laptop Pro|1200|Electrónicos|
|Smartphone X|800|Electrónicos|
|Silla Ergo|150|Mobiliario|
|Mesa de Café|90|Mobiliario|
|Reloj Elegante|250|Accesorios|
|Bolso de Viaje|70|Accesorios|
|Zapatillas Run|100|Ropa|
|Camisa Casual|40|Ropa|
|Licuadora Max|60|Electrodomésticos|
|Horno Compacto|110|Electrodomésticos|
|Libro de Cocina|20|Libros|
|Novela Misterio|15|Libros|
|Audífonos Plus|50|Electrónicos|
|Lámpara Moderna|45|Mobiliario|
|Laptop Pro|1200|Electrónicos|
|Silla Ergo|150|Mobiliario|
|Bolso de Viaje|70|Accesorios|
|Zapatillas Run|100|Ropa|

Crea una consulta para calcular el monto más bajo por cada categoría. La tabla resultante debe tener dos columnas: categoria y monto\_mas\_bajo.

SELECT categoria, MIN(monto) as monto\_mas\_bajo FROM ventas GROUP by categoria


### Funciones de agregación y fechas
A la hora de construir informes, frecuentemente necesitaremos entregar información agrupada en un periodo de tiempo. Para lograr esto utilizaremos una combinación de GROUP BY con la función strftime.

Tenemos la tabla "ventas" con la siguiente información:

|**ID\_VENTA**|**MONTO**|**FECHA\_VENTA**|
| :- | :- | :- |
|1|200|2010-01-15|
|2|150|2011-02-20|
|3|300|2012-03-10|
|4|250|2012-04-05|
|5|100|2014-05-25|
|6|350|2015-06-18|
|7|400|2015-07-22|
|8|180|2015-08-09|
|9|220|2018-09-30|
|10|275|2018-10-11|

Se nos solicita determinar el monto total de ventas por año. Para resolverlo tenemos que agrupar por fecha y sumar los montos de la siguiente forma:

SELECT SUM(monto), strftime("%Y", fecha\_venta) AS año FROM ventas GROUP BY strftime("%Y", fecha\_venta)
## **Ejercicio**
Utilizando esta nueva **tabla de ventas**.

|**ID\_VENTA**|**MONTO**|**FECHA\_VENTA**|
| :- | :- | :- |
|1|200|2010-01-15|
|2|150|2010-02-20|
|3|300|2010-02-10|
|4|250|2010-04-05|
|5|100|2010-04-25|
|6|350|2010-04-18|
|7|400|2010-06-22|
|8|180|2010-06-09|
|9|220|2010-09-30|
|10|275|2010-10-11|

Calcula el total de ventas por mes. El nombre de las columnas resultantes será "suma\_ventas" y "mes" respectivamente.

Pista: utiliza la función strftime con %m.

SELECT SUM(monto) AS suma\_ventas , strftime("%m", fecha\_venta) AS mes FROM ventas GROUP BY strftime("%m", fecha\_venta)



### Ejercitando funciones de agregación con fechas
## **Ejercicio**
Se tiene una tabla llamada inscripciones con distintas fechas de inscripciones de un usuario a un sitio web.

|**FECHA\_INSCRIPCION**|
| :- |
|2022-01-15|
|2022-01-20|
|2022-02-10|
|2022-02-05|
|2022-03-25|
|2022-03-18|
|2022-04-22|
|2022-04-09|
|2022-05-30|
|2022-05-11|
|2022-06-19|
|2022-06-29|
|2022-07-12|
|2022-07-21|
|2022-08-08|
|2022-08-17|
|2022-09-13|
|2022-09-26|
|2022-10-14|
|2022-10-28|

Cuenta cuántos usuarios se registraron cada mes. Las columnas resultantes deben llamarse "mes" y "cantidad\_usuarios".

Tip: Utiliza la función strftime con %m.



SELECT strftime("%m", fecha\_inscripcion) AS mes, count(fecha\_inscripcion) AS cantidad\_usuarios FROM inscripciones GROUP BY strftime("%m", fecha\_inscripcion)


### Agrupando sin indicar el nombre de las columnas
Cuando se trata de agrupar datos en una consulta SQL, existe una forma de evitar la redundancia de la cláusula SELECT. Por ejemplo, considera la siguiente consulta:

SELECT strftime("%Y", fecha\_venta) AS año, SUM(monto) FROM ventas GROUP BY strftime("%Y", fecha\_venta)

Puedes simplificarla de la siguiente manera:

SELECT strftime("%Y", fecha\_venta) AS año, SUM(monto) FROM ventas GROUP BY 1

Esta notación se interpreta como "agrupa por el primer criterio". También es posible aplicar esta sintaxis en la cláusula ORDER BY:

SELECT strftime("%Y", fecha\_venta) AS año, SUM(monto) FROM ventas GROUP BY 1 ORDER BY 1

De esta manera, puedes lograr la misma agrupación y ordenamiento sin repetir la expresión de la cláusula SELECT.
## **Ejercicio**
Dada la siguiente **tabla de usuarios**

|**CORREO**|
| :- |
|<juan.perez@empresa.com>|
|<maria.gonzalez@empresa.com>|
|<carlos.rodriguez@empresa.com>|
|<ana.martinez@empresa.com>|
|<luis.garcia@empresa.com>|
|<carmen.lopez@empresa.com>|
|<jose.hernandez@empresa.com>|
|<juan.perez@empresa.com>|
|<carmen.lopez@empresa.com>|
|<maria.gonzalez@empresa.com>|
|<juan.perez@empresa.com>|
|<maria.gonzalez@empresa.com>|

Crea una consulta que nos muestre cada correo una única vez acompañado del número de veces que se repite. Las columnas deben llevar los nombres "correo" y "repeticiones", respectivamente, y deben estar ordenadas alfabéticamente.

SELECT correo, count(\*) as repeticiones FROM usuarios GROUP BY correo order by 1



### Agrupando por múltiples columnas
En SQL es posible agrupar por múltiples columnas utilizando la siguiente sintaxis:

SELECT columna1, columna2, funcion\_agrupado(columna3) FROM tabla GROUP BY columna1, columna2

Y como aprendimos en el ejercicio anterior, también podemos escribir la consulta de la siguiente manera:

SELECT columna1, columna2, funcion\_agrupado(columna3) FROM tabla GROUP BY 1, 2
## **Ejercicio**
Tenemos la siguiente **tabla estudiantes**

|**CORREO**|**MATERIA**|**NOTA**|
| :- | :- | :- |
|[estudiante1@ejemplo.co](mailto:estudiante1@ejemplo.com)[m](mailto:estudiante1@ejemplo.com)|Matemáticas|8\.5|
|<estudiante2@ejemplo.com>|Matemáticas|9\.0|
|<estudiante3@ejemplo.com>|Matemáticas|7\.5|
|<estudiante1@ejemplo.com>|Ciencias|8\.0|
|<estudiante2@ejemplo.com>|Ciencias|9\.5|
|<estudiante3@ejemplo.com>|Ciencias|7\.0|
|<estudiante1@ejemplo.com>|Historia|8\.7|
|<estudiante2@ejemplo.com>|Historia|9\.2|
|<estudiante3@ejemplo.com>|Historia|7\.8|

Calcula el promedio de cada estudiante en cada materia. Las columnas deben llamarse correo, materia y promedio\_notas

select correo, materia, avg(nota) as promedio\_notas from estudiantes group by 1,2








### Ejercicio
### Ejercitando funciones de agregación con fechas
## **Ejercicio**
Se tiene una tabla llamada inscripciones con distintas fechas de inscripciones de un usuario a un sitio web.

|**FECHA\_INSCRIPCION**|
| :- |
|2022-01-15|
|2022-01-20|
|2022-02-10|
|2022-02-05|
|2022-03-25|
|2022-03-18|
|2022-04-22|
|2022-04-09|
|2022-05-30|
|2022-05-11|
|2022-06-19|
|2022-06-29|
|2022-07-12|
|2022-07-21|
|2022-08-08|
|2022-08-17|
|2022-09-13|
|2022-09-26|
|2022-10-14|
|2022-10-28|

Cuenta cuántos usuarios se registraron cada mes. Las columnas resultantes deben llamarse "mes" y "cantidad\_usuarios".

Tip: Utiliza la función strftime con %m.








###
###
###
###
### Introducción a Having
En SQL, la cláusula GROUP BY nos permite agrupar datos. Si queremos filtrar la información obtenida utilizaremos HAVING.

HAVING se emplea para filtrar los resultados de una consulta que involucra funciones agregadas. En otras palabras, HAVING permite aplicar condiciones de filtrado a los resultados de funciones como COUNT, MAX, MIN, SUM y AVG después de que se han agrupado los datos con la cláusula GROUP BY.

Por ejemplo, si tenemos la siguiente tabla de inscripciones

|**FECHA\_INSCRIPCION**|
| :- |
|2022-01-15|
|2022-01-20|
|2022-02-10|
|2022-02-05|
|2022-03-25|
|2022-03-18|
|2022-04-22|
|2022-04-09|
|2022-05-30|
|2022-05-11|
|2022-06-19|
|2022-06-29|
|2022-07-12|
|2022-07-21|
|2022-08-08|
|2022-08-17|
|2022-09-13|
|2022-09-26|
|2022-10-14|
|2022-10-28|

Nos piden crear un reporte mostrando los meses y la cantidad de inscritos, pero solo donde hayan 2 o más inscritos.

SELECT strftime("%m", Fecha\_Inscripcion) AS mes, COUNT(Fecha\_Inscripcion) cantidad\_usuarios 

FROM inscripciones 

GROUP BY strftime("%m", Fecha\_Inscripcion)

HAVING cantidad\_usuarios >= 2

En esta consulta, primero utilizamos GROUP BY para agrupar por mes. Luego, utilizamos la función de agregación COUNT(Fecha\_Inscripcion) para contar la cantidad de inscritos.Después de haber agrupado los datos y calculado el total de inscritos, aplicamos la cláusula HAVING para filtrar los resultados.

Nos piden crear un reporte mostrando los meses y la cantidad de inscritos, pero solo donde hayan 2 o más inscritos.

SELECT strftime("%m", Fecha\_Inscripcion) AS mes, COUNT(Fecha\_Inscripcion) cantidad\_usuarios 

FROM inscripciones 

GROUP BY strftime("%m", Fecha\_Inscripcion)

HAVING cantidad\_usuarios >= 2

En esta consulta, primero utilizamos GROUP BY para agrupar por mes. Luego, utilizamos la función de agregación COUNT(Fecha\_Inscripcion) para contar la cantidad de inscritos.Después de haber agrupado los datos y calculado el total de inscritos, aplicamos la cláusula HAVING para filtrar los resultados.


Crea un reporte mostrando los meses y la cantidad de inscritos pero solo donde haya 1 inscrito. Las columnas deben llamarse mes y cantidad\_usuarios respectivamente.

SELECT strftime("%m", Fecha\_Inscripcion) AS mes, COUNT(Fecha\_Inscripcion) cantidad\_usuarios 

FROM inscripciones 

GROUP BY strftime("%m", Fecha\_Inscripcion)

HAVING cantidad\_usuarios = 1



Uno de los usos mas recurrentes de HAVING es buscar duplicados. Por ejemplo, dada una tabla de correos ver cuales están más de 1 vez.
## Ejercicio
Se tiene la tabla correos\_corporativos

|**CORREO**|
| :- |
|<juan.perez@empresa.com>|
|<maria.gonzalez@empresa.com>|
|<carlos.rodriguez@empresa.com>|
|<ana.martinez@empresa.com>|
|<luis.garcia@empresa.com>|
|<carmen.lopez@empresa.com>|
|<jose.hernandez@empresa.com>|
|<francisco.martin@empresa.com>|
|<laura.sanchez@empresa.com>|
|<antonio.diaz@empresa.com>|
|<juan.perez@empresa.com>|
|<maria.gonzalez@empresa.com>|

Muestra los correos que aparezcan en más de una ocasión. La tabla resultante debe tener dos columnas: una llamada correo, y otra llamada cuenta\_correos que muestra la cantidad de repeticiones correspondiente a cada correo


SELECT correo, COUNT(correo) cuenta\_correos

FROM correos\_corporativos

GROUP BY  correo

HAVING COUNT(correo) > 1



### Having y cuenta
## **Ejercicio**
Dada la siguiente **tabla empleados**

|**NOMBRE**|**APELLIDO**|**SUELDO**|**DEPARTAMENTO**|
| :- | :- | :- | :- |
|Juan|Pérez|3000|Ventas|
|María|González|3500|Marketing|
|Carlos|Rodríguez|4000|Tecnología|
|Ana|Martínez|2800|Recursos Humanos|
|Luis|García|3200|Finanzas|
|Carmen|López|3100|Administración|
|José|Hernández|2900|Operaciones|
|Francisco|Martín|3400|Legal|
|Laura|Sánchez|3300|Compras|
|Antonio|Díaz|3600|Producción|
|Sofía|Ruiz|2750|Ventas|
|Jorge|Vargas|3900|Tecnología|
|Elena|Castro|3050|Marketing|
|Pedro|Ortega|3150|Finanzas|

Crea una consulta que muestre la cantidad de usuarios y el departamento en donde haya más de un empleado. Las columnas deben llamarse cantidad\_de\_usuarios y departamento, respectivamente.

select count(\*) aS cantidad\_de\_usuarios, departamento from empleados

group by departamento

having count(\*) >1



### Having y promedio
## **Ejercicio**
Se tiene la siguiente **tabla notas**:

|**EMAIL**|**NOTAS**|
| :- | :- |
|<Alumno1@ejemplo.com>|90|
|<Alumno1@ejemplo.com>|50|
|[Alumno1@ejemplo.co](mailto:Alumno1@ejemplo.com)[m](mailto:Alumno1@ejemplo.com)|30|
|<Alumno2@ejemplo.com>|90|
|<Alumno2@ejemplo.com>|20|
|<Alumno3@ejemplo.com>|80|
|<Alumno2@ejemplo.com>|50|
|<Alumno3@ejemplo.com>|30|
|<Alumno3@ejemplo.com>|10|

Crea una consulta para determinar cuales son los estudiantes que aprobaron. El criterio de aprobación es promedio de notas >= 50.

Las columnas a mostrar deben ser email y promedio\_notas.

select email, avg(notas) as promedio\_notas from notas

group by email

having avg(notas) >50




### Having y order
Una vez que hemos agrupado datos utilizando la cláusula GROUP BY, es común que necesitemos ordenar esos grupos según algún criterio específico. Por lo general, queremos ordenar los grupos en función de alguna métrica agregada, como la suma, el conteo, el promedio, etc. Para hacer esto, usamos la cláusula ORDER BY junto con las funciones de agregación.

El orden de las clausulas en una consulta debe ser el siguiente:

|**ORDEN**|**CLAUSULA**|**DESCRIPCIÓN**|
| :- | :- | :- |
|1|SELECT|Especifica las columnas que se deben retornar en el resultado.|
|2|FROM|Especifica las tablas de las cuales se extraerán los datos.|
|3|WHERE|Filtra registros antes de cualquier agregación o agrupación.|
|4|GROUP BY|Agrupa registros por una o más columnas.|
|5|HAVING|Filtra registros después de la agregación.|
|6|ORDER BY|Ordena los registros retornados por una o más columnas.|
|7|LIMIT|Limita el número de registros retornados.|
## **Ejercicio**
Dada la siguiente tabla **ventas**, escribe una consulta SQL para obtener los productos que se han vendido en una cantidad total mayor a 1000, ordenados en orden descendente de cantidad vendida.

|**PRODUCTO**|**CANTIDAD**|
| :- | :- |
|A|500|
|B|2000|
|C|300|
|D|1500|
|E|700|
|A|600|
|B|800|
|C|1200|
|D|400|
|E|300|

La tabla resultante debe tener dos columnas: 'producto' y 'cantidad\_total'.

select producto, sum(cantidad) as cantidad\_total from ventas

group by producto

having sum(cantidad) >1000

order by sum(cantidad) desc



### Having y order 2
## **Ejercicio**
Supongamos que tienes una tabla de empleados con los siguientes datos:

|**ID\_EMPLEADO**|**NOMBRE**|**DEPARTAMENTO**|**SALARIO**|
| :- | :- | :- | :- |
|1|Juan|Ventas|3000|
|2|Maria|Marketing|3500|
|3|Carlos|Ventas|4000|
|4|Ana|Marketing|2800|
|5|Luis|Ventas|3200|

Tu tarea es escribir una consulta SQL que devuelva los departamentos cuyo salario promedio es mayor a 3000, ordenados de mayor a menor salario promedio. Los resultados deben mostrar el nombre del departamento y el salario promedio, con los nombres de las columnas como Departamento y Salario\_Promedio respectivamente.

select departamento, avg(salario) as salario\_promedio from empleados

group by departamento

having avg(salario) >3000

order by avg(salario) desc



### Introduccion a subconsultas
Las subconsultas, también conocidas como "subqueries", nos permiten utilizar los resultados de una consulta dentro de otra consulta.

Veamos un ejemplo práctico.

Dada la siguiente **tabla empleados**

|**NOMBRE**|**APELLIDO**|**SUELDO**|**DEPARTAMENTO**|
| :- | :- | :- | :- |
|Juan|Pérez|3000|Ventas|
|María|González|3500|Marketing|
|Carlos|Rodríguez|4000|Tecnología|
|Ana|Martínez|2800|Recursos Humanos|
|Luis|García|3200|Finanzas|
|Carmen|López|3100|Administración|
|José|Hernández|2900|Operaciones|
|Francisco|Martín|3400|Legal|
|Laura|Sánchez|3300|Compras|
|Antonio|Díaz|3600|Producción|
|Sofía|Ruiz|2750|Ventas|
|Jorge|Vargas|3900|Tecnología|
|Elena|Castro|3050|Marketing|
|Pedro|Ortega|3150|Finanzas|

Se nos pide seleccionar a todas las personas que ganan sobre el promedio.

Este tipo de preguntas podemos contestarlas utilizando subconsultas.

La idea para contestar esto es la siguiente.

1. Calculamos el promedio SELECT avg(sueldo) FROM empleados
1. Seleccionamos todos los empleados cuyo sueldo es mayor a la consulta anterior. SELECT \* FROM empleados WHERE sueldo > (SELECT AVG(sueldo) FROM empleados)
## **Ejercicio**
Utilizando los mismos datos de la tabla empleados, selecciona todos los registros cuyo sueldo sea menor o igual al promedio.

SELECT \* FROM empleados WHERE sueldo <= (SELECT avg(sueldo) FROM empleados)



### Subconsultas y where parte 1
Dentro de las subconsultas, podemos utilizar las mismas cláusulas que hemos aprendido hasta ahora, como la cláusula WHERE. Esto significa que podemos aplicar la cláusula WHERE tanto dentro de la subconsulta como fuera de ella.
## **Ejercicio**
Dada la siguiente **tabla empleados**

|**NOMBRE**|**APELLIDO**|**SUELDO**|**DEPARTAMENTO**|
| :- | :- | :- | :- |
|Juan|Pérez|3000|Ventas|
|María|González|3500|Marketing|
|Carlos|Rodríguez|4000|Tecnología|
|Ana|Martínez|2800|Recursos Humanos|
|Luis|García|3200|Finanzas|
|Carmen|López|3100|Administración|
|José|Hernández|2900|Operaciones|
|Francisco|Martín|3400|Legal|
|Laura|Sánchez|3300|Compras|
|Antonio|Díaz|3600|Producción|
|Sofía|Ruiz|2750|Ventas|
|Jorge|Vargas|3900|Tecnología|
|Elena|Castro|3050|Marketing|
|Pedro|Ortega|3150|Finanzas|

Selecciona toda la información de los registros que sean mayores al promedio del departamento de finanzas.

Tip:

- Se pide el promedio exclusivamente del departamento de finanzas por lo que no hay necesidad de agrupar los datos.
- Para este tipo de problema usualmente hay más de una solución.

SELECT \* FROM empleados WHERE sueldo > (SELECT avg(sueldo) FROM empleados where departamento='Finanzas')




### Sub
### consultas y where parte 2
## **Ejercicio**

|**NOMBRE**|**APELLIDO**|**SUELDO**|**DEPARTAMENTO**|
| :- | :- | :- | :- |
|Juan|Pérez|3000|Ventas|
|María|González|3500|Marketing|
|Carlos|Rodríguez|4000|Tecnología|
|Ana|Martínez|2800|Recursos Humanos|
|Luis|García|3200|Finanzas|
|Carmen|López|3100|Administración|
|José|Hernández|2900|Operaciones|
|Francisco|Martín|3400|Legal|
|Laura|Sánchez|3300|Compras|
|Antonio|Díaz|3600|Producción|
|Sofía|Ruiz|2750|Ventas|
|Jorge|Vargas|3900|Tecnología|
|Elena|Castro|3050|Marketing|
|Pedro|Ortega|3150|Finanzas|

Utilizando los datos de la **tabla empleados**, selecciona todos los empleados cuyo sueldo sea mayor al empleado que tiene el mayor sueldo del departamento de finanzas.

SELECT \* FROM empleados WHERE sueldo > (SELECT max(sueldo) FROM empleados where departamento='Finanzas')


ejercicio


Se tiene la siguiente **tabla notas**:

|**EMAIL**|**NOTAS**|
| :- | :- |
|<Alumno1@ejemplo.com>|90|
|<Alumno1@ejemplo.com>|50|
|<Alumno1@ejemplo.com>|30|
|<Alumno2@ejemplo.com>|90|
|<Alumno2@ejemplo.com>|20|
|<Alumno3@ejemplo.com>|80|
|<Alumno2@ejemplo.com>|50|
|<Alumno3@ejemplo.com>|30|
|<Alumno3@ejemplo.com>|10|

Selecciona todos los registros superiores al promedio de not

select \* from notas where notas > (select avg(notas) from notas)






### Subconsultas con IN
El operador IN es un operador muy útil en subconsultas. Para entenderlo, primero probaremos una consulta sencilla utilizandolo directamente sin subconsultas.

|**PAÍS**|**CÓDIGO TELÉFONO**|
| :- | :- |
|Argentina|+54|
|Brasil|+55|
|Chile|+56|
|Colombia|+57|
|España|+34|
|Estados Unidos|+1|
|México|+52|

Queremos seleccionar todos los códigos de Argentina, Brasil, Chile o Colombia. Una forma de abordar el problema sería combinar todas las opciones con where y múltiples operadores or. Otra opción es utilizando el operador IN de la siguiente manera:

SELECT \* 

FROM paises 

WHERE pais IN ('Argentina', 'Brasil', 'Chile', 'Colombia')

De la misma forma podemos hacer una consulta como la siguiente:

SELECT \*

FROM table

WHERE columna IN (SELECT \* from otra\_tabla)
## **Operador IN con subconsultas**
Se tiene la siguiente tabla de estudiantes

|**ESTUDIANTE\_ID**|**NOMBRE**|
| :- | :- |
|1|Juan|
|2|María|
|3|Pedro|
|4|Ana|

y la tabla de notas

|**ESTUDIANTE\_ID**|**PROMEDIO\_NOTAS**|
| :- | :- |
|1|85|
|2|65|
|3|49|
|4|38|

Se nos pide mostrar los nombres de todas las personas que tengan un promedio de notas menor que 50.

1. Seleccionamos los ids de la tabla notas con promedio\_notas <= 50
1. Seleccionamos los nombres de de la tabla estudiantes cuyo id esté dentro de la subconsulta anterior.

SELECT nombre from estudiantes

WHERE estudiante\_id IN (SELECT estudiante\_id from notas where promedio\_notas <= 50)
## **Ejercicio**
Se tiene una tabla estudiantes con un código y un nombre

|**ESTUDIANTE\_ID**|**NOMBRE**|
| :- | :- |
|1|Juan|
|2|María|
|3|Pedro|
|4|Ana|

Y se tiene una tabla promedios con el código del estudiante y su promedio de notas.

|**ESTUDIANTE\_ID**|**PROMEDIO\_NOTAS**|
| :- | :- |
|1|85|
|2|65|
|3|49|
|4|38|

Muestra los nombres de todos los estudiantes que tengan un promedio de notas sobre 50

Tip 1: No necesitas agrupar ni promediar ni contar Tip 2: Hay más de una forma de resolver este ejercicio, no te adelantes a joins e intenta resolverlo utilizando subqueries

SELECT nombre from estudiantes

WHERE estudiante\_id IN (SELECT estudiante\_id from promedios where promedio\_notas > 50)



## Ejercicio
Se tiene la tabla **libros**

|**LIBRO\_ID**|**NOMBRE**|
| :- | :- |
|1|La Odisea|
|2|Cien Años de Soledad|
|3|El Principito|
|4|Moby Dick|

Y se tiene la tabla **valoraciones**

|**LIBRO\_ID**|**VALORACION\_PROMEDIO**|
| :- | :- |
|1|4\.5|
|2|4\.7|
|3|4\.2|
|4|3\.9|

Crea una consulta que muestre todos los títulos con valoración\_promedio > 4. La columna resultante debe llamarse nombres\_seleccionados.

SELECT nombre from libros as nombres\_seleccionados

WHERE libro\_id IN (SELECT libro\_id from valoraciones where valoracion\_promedio > 4)


### Subconsultas con IN parte 3
## **Ejercicio**
Se tiene una tabla de **pacientes**

|**PACIENTE\_ID**|**NOMBRE**|
| :- | :- |
|1|Roberto|
|2|Carmen|
|3|Luisa|
|4|Esteban|

Se tiene una tabla de **consultas**

|**PACIENTE\_ID**|**FECHA\_CONSULTA**|
| :- | :- |
|1|2023-05-10|
|2|2023-05-15|
|3|2023-05-20|
|4|2023-05-25|

Se pide obtener los nombres de todos los pacientes que tuvieron su última consulta antes del 16 de mayo de 2023. La columna se debe llamar nombres\_pacientes.

select nombre as nombres\_pacientes from pacientes where paciente\_id in (select paciente\_id from consultas where 

date(fecha\_consulta) < '2023-05-16')



### Subconsultas en el FROM
Las subconsultas, también conocidas como "subqueries", nos permiten utilizar los resultados de una consulta dentro de otra consulta. En los ejercicios anteriores utilizamos las subconsultas dentro de la claúsula WHERE, pero también es posible utilizarlas dentro de otras claúsulas. En este ejercicio abordaremos como utilizarla dentro de FROM

Una subconsulta en el FROM tiene la siguiente forma.

SELECT \* 

`    `FROM (

`        `SELECT \* FROM tabla1

)

En este caso no parece tan útil ya que simplemente estamos seleccionando lo mismo, pero veamos un caso donde si sería necesario.

Se tiene la tabla ventas que tiene el código de vendedor y el monto de cada venta realizada. Nos piden saber cuanto es el promedio total vendido.

|**EMPLEADO\_ID**|**MONTO**|
| :- | :- |
|1|100|
|1|150|
|2|200|
|2|250|
|3|300|
|3|350|
|4|400|

Para esto primero necesitamos sumar los montos por vendedor y luego sobre estos resultados sacamos el promedio de las ventas.

SELECT AVG(total\_venta) as promedio\_ventas

FROM (

`    `SELECT empleado\_id, SUM(monto) as total\_venta

`    `FROM ventas

`    `GROUP BY empleado\_id

) 
### **¿Cómo llegamos a esto?**
Si queremos saber los promedios, primero tenemos que saber los totales, para eso necesitamos sumar por empleado.

SELECT empleado\_id, SUM(monto) as total\_venta

FROM ventas

GROUP BY empleado\_id

El código anterior nos generará los siguientes resultados.

|**EMPLEADO\_ID**|**TOTAL\_VENTA**|
| :- | :- |
|1|250|
|2|450|
|3|650|
|4|400|

Luego sacamos el promedio de los montos de esta nueva tabla.

SELECT AVG(total\_venta) as promedio\_ventas

FROM (

`    `SELECT empleado\_id, SUM(monto) as total\_venta

`    `FROM ventas

`    `GROUP BY empleado\_id

) 

Este tipo de ejercicio suele ser un poco mas complejo de pensar y escribir y requiere de cierta práctica dominar, por lo mismo el primer ejercicio consistirá en escribir el mismo query. Intenta hacerlo sin mirar la respuesta.
## **Ejercicio**
Se tiene la tabla ventas que tiene el código de vendedor y el monto de la venta. Nos piden saber cuanto es el promedio total vendido. El resultado debe estar en la columna promedio\_ventas

SELECT AVG(total\_venta) as promedio\_ventas

FROM (

`    `SELECT empleado\_id, SUM(monto) as total\_venta

`    `FROM ventas

`    `GROUP BY empleado\_id

) 


SELECT AVG(goles) as PROMEDIO\_GOLES

FROM (

SELECT jugador\_id, SUM(goles) as total\_goles

FROM goles

GROUP BY jugador\_id

) 



### Subconsultas con IN parte 2
## **Ejercicio**
Se tiene la tabla **libros**

|**LIBRO\_ID**|**NOMBRE**|
| :- | :- |
|1|La Odisea|
|2|Cien Años de Soledad|
|3|El Principito|
|4|Moby Dick|

Y se tiene la tabla **valoraciones**

|**LIBRO\_ID**|**VALORACION\_PROMEDIO**|
| :- | :- |
|1|4\.5|
|2|4\.7|
|3|4\.2|
|4|3\.9|

Crea una consulta que muestre todos los títulos con valoración\_promedio > 4. La columna resultante debe llamarse nombres\_seleccionados.

select nombre as nombres\_seleccionados from libros where libro\_id in (select libro\_id from valoraciones where valoracion\_promedio > 4)






### Introducción a la cláusula unión de SQL
El operador **UNION** en SQL se utiliza para combinar el resultado de dos o más SELECT en un solo conjunto de resultados.

La sintaxis básica de UNION es la siguiente:

SELECT columna1, columna2

FROM tabla1 

UNION SELECT columna1, columna2

FROM tabla2; 

Las columnas que se seleccionan en los SELECT deben tener los mismos nombres de columna, secuencia y tipos de datos.

Veamos un ejemplo:

Supongamos que tenemos dos tablas: 'Estudiantes' y 'Profesores', que contienen una lista de apellidos en cada una. Queremos crear una lista que combine los apellidos de ambas tablas.

Estudiantes

|**ID**|**NOMBRE**|**APELLIDO**|
| :- | :- | :- |
|1|Juan|Rodríguez|
|2|María|Sánchez|
|3|Pedro|Castillo|

Profesores

|**ID**|**NOMBRE**|**APELLIDO**|
| :- | :- | :- |
|1|Alberto|Vargas|
|2|Carla|Garrido|
|3|Diego|Mendoza|

Al hacer la consulta:

SELECT apellido 

FROM Estudiantes 

UNION 

SELECT apellido 

FROM Profesores; 

Nos daría el resultado:

|**APELLIDO**|
| :- |
|Rodríguez|
|Sánchez|
|Castillo|
|Vargas|
|Garrido|
|Mendoza|
## **Ejercicio**
Dadas las tablas **estudiantes**

|**NOMBRE**|
| :- |
|Juan|
|Maria|
|Pedro|

y **profesores**

|**NOMBRE**|
| :- |
|Carlos|
|Ana|
|Luis|

Escribe una consulta SQL que use UNION para combinar los nombres de ambas tablas. La columna resultante debe llamarse 'nombres'.



SELECT nombre as nombres

FROM Estudiantes 

UNION 

SELECT nombre as nombres

FROM Profesores ;


### **Eliminar duplicados con union**
El operador *UNION* se utiliza para combinar los resultados de dos o más consultas SELECT en un solo conjunto de resultados. La principal característica de UNION es que elimina las filas duplicadas del resultado final.
## **Ejercicio**
Se tiene la tabla **usuarios** con la siguiente información:

|**ID**|**NOMBRE**|**APELLIDO**|**EMAIL**|**TELEFONO**|
| :- | :- | :- | :- | :- |
|1|Juan|Pérez|<juanperez@gmail.com>|555-1234|
|2|María|García|<mariagarcia@hotmail.com>|555-5678|
|3|Pedro|López|<pedrolopez@yahoo.com>|555-5678|
|4|Lucía|Sánchez|<luciasanchez@outlook.com>|555-5555|
|5|Jorge|Martínez|<jorgemartinez@gmail.com>|555-5678|

Y la tabla **clientes** con la siguiente información:

|**ID**|**NOMBRE**|**APELLIDO**|**EMAIL**|**TELEFONO**|
| :- | :- | :- | :- | :- |
|1|Juan|Pérez|<juanperez@gmail.com>|555-1234|
|2|María|García|<mariagarcia@hotmail.com>|555-5678|
|3|Pedro|López|<pedrolopez@yahoo.com>|555-5678|
|4|Lucía|Sánchez|<luciasanchez@outlook.com>|555-5555|
|5|Jorge|Martínez|<jorgemartinez@gmail.com>|555-4321|

Crea una consulta que nos muestre cada correo una única vez. La columna mostrada debe llamarse correos\_unicos



select email as correos\_unicos from usuarios

union

select email as correos\_unicos from clientes



### Union vs Union all
En los ejercicios anteriores aprendimos que el operador **UNION** se utiliza para combinar los resultados de dos o más consultas SELECT en un solo conjunto de resultados, eliminando las filas duplicadas.

Si queremos obtener las filas duplicadas en el resultado, utilizaremos el operador UNION ALL.

Por ejemplo, si tenemos dos tablas, 'tabla1' y 'tabla2', con los siguientes datos:

**tabla1**

|**NOMBRE**|**EDAD**|
| :- | :- |
|Juan|30|
|Maria|25|
|Carlos|40|

**tabla2**

|**NOMBRE**|**EDAD**|
| :- | :- |
|Juan|30|
|Luis|30|
|Carmen|25|

Observa que Juan está en ambas tablas.

Podemos combinar ambas tablas utilizando UNION ALL de la siguiente forma:

SELECT \* FROM tabla1 UNION ALL SELECT \* FROM tabla2;

Como resultado obtendremos:

|**NOMBRE**|**EDAD**|
| :- | :- |
|Juan|30|
|Maria|25|
|Carlos|40|
|Juan|30|
|Luis|30|
|Carmen|25|
## **Ejercicio**
Dadas las siguientes tablas **empleados1** y **empleados2**

**empleados1**

|**NOMBRE**|**APELLIDO**|**EDAD**|
| :- | :- | :- |
|Juan|Pérez|30|
|María|González|25|
|Carlos|Rodríguez|40|

**empleados2**

|**NOMBRE**|**APELLIDO**|**EDAD**|
| :- | :- | :- |
|Ana|Martínez|22|
|María|González|25|
|Carmen|López|25|

Crea una consulta que combine ambas tablas incluyendo las filas duplicadas.

SELECT \* FROM empleados1 UNION ALL SELECT \* FROM empleados2;


### Introducción a intersección
El operador **INTERSECT** se utiliza para combinar dos SELECT y devolver los resultados que se encuentran en ambas consultas.

Por ejemplo, si tenemos las siguientes dos tablas, clientes1 y clientes2:

Tabla **clientes1**:

|**NOMBRE**|
| :- |
|Juan|
|Maria|
|Carlos|
|Ana|
|Luis|

Tabla **clientes2**:

|**NOMBRE**|
| :- |
|Ana|
|Luis|
|Pedro|
|Carmen|
|Juan|

Podemos encontrar los clientes en común utilizando INTERSECT de la siguiente forma:

SELECT nombre FROM clientes1 INTERSECT SELECT nombre FROM clientes2

Como resultado obtendremos:

|**NOMBRE**|
| :- |
|Ana|
|Juan|
|Luis|
## **Ejercicio**
Dadas las siguientes tablas, **lista1** y **lista2**, encuentra los clientes que están en ambas listas.

Lista1:

|**CLIENTE**|
| :- |
|Juan|
|Maria|
|Carlos|
|Ana|
|Luis|
|Pedro|
|Carmen|

Lista2:

|**CLIENTE**|
| :- |
|Ana|
|Luis|
|Pedro|
|Carmen|
|Juan|
|Maria|
|Sofia|

SELECT cliente FROM lista1 INTERSECT SELECT cliente FROM lista2


### El operador Except
El operador **EXCEPT** en SQL se utiliza para devolver todas las filas en la primera consulta que no están presentes en la segunda consulta. En otras palabras, EXCEPT devuelve solo las filas, que son parte de la primera consulta pero no de la segunda consulta.

Por ejemplo, si tenemos dos tablas, 'Tabla1' y 'Tabla2', que contienen los siguientes datos:

Tabla1

|**ID**|**NOMBRE**|
| :- | :- |
|1|Juan|
|2|María|
|3|Carlos|

Tabla2

|**ID**|**NOMBRE**|
| :- | :- |
|1|Juan|
|4|Ana|
|5|Luis|

Podemos usar EXCEPT para encontrar los nombres que están en 'Tabla1' pero no en 'Tabla2' con la siguiente consulta:

SELECT nombre FROM Tabla1 EXCEPT SELECT nombre FROM Tabla2;

Esto daría como resultado:

|**NOMBRE**|
| :- |
|María|
|Carlos|
## **Ejercicio**
Dadas las siguientes tablas, 'empleados' y 'gerentes', que contienen los siguientes datos:

empleados

|**ID**|**NOMBRE**|
| :- | :- |
|1|Juan|
|2|María|
|3|Carlos|
|4|Ana|
|5|Luis|

gerentes

|**ID**|**NOMBRE**|
| :- | :- |
|1|Juan|
|2|María|

Crea una consulta que muestre los nombres de los empleados que no son gerentes.

SELECT nombre FROM empleados EXCEPT SELECT nombre FROM gerentes;



### Añadir un registro en una tabla
Con SQL podemos ingresar datos nuevos a tablas existentes. Para lograrlo utilizaremos la instrucción INSERT .

La instrucción INSERT la acompañaremos de las palabra clave INTO para especificar en qué tabla queremos insertar un valor y VALUES para especificar los valores que queremos insertar.

Por ejemplo. Si tenemos una tabla llamada productos con las columnas id, nombre y precio, podemos agregar un nuevo producto a la tabla usando utilizando:

INSERT INTO productos VALUES (1, 'Camiseta', 2000);

Para cada columna en la tabla debemos ingresar los valores correspondientes en el mismo orden en que se definen en la sentencia. Debemos utilizar comillas simples para valores de tipo de datos de texto.
## **Ejercicio**
Dada la **tabla usuarios** con las columnas id, nombre, apellido, email y telefono:

|**COLUMNA**|**TIPO DE DATO**|
| :- | :- |
|id|INTEGER|
|nombre|TEXT|
|apellido|TEXT|
|email|TEXT|
|telefono|TEXT|

Crea un nuevo **usuario** con los siguientes datos:

- id: 7
- nombre: Lucía
- apellido: Sánchez
- email: <luciasanchez@outlook.com>
- telefono: 555-5555

INSERT INTO usuarios VALUES (7, 'Lucía', 'Sánchez', 'luciasanchez@outlook.com','555-5555');


### Añadir un registro en una tabla parte 2
## **Ejercicio**
Se tiene la tabla **productos**:

|**COLUMNA**|**TIPO**|
| :- | :- |
|id|INT|
|nombre|VARCHAR|
|precio|INT|
|stock|INT|

Inserta un nuevo producto con los siguientes datos:

- id: 7
- nombre: Bolso
- Precio: 1000
- Stock: 10

insert into productos values (7,'Bolso',1000,10)

### Especificando valores nulos
A la hora de insertar datos, si hay un valor que no conocemos, o es un valor que no queremos especificar, podemos ingresar un valor nulo.

Ejemplo: Se tiene la tabla productos:

|**COLUMNA**|**TIPO**|
| :- | :- |
|id|INT|
|nombre|VARCHAR|
|precio|INT|
|stock|INT|

Podemos ingresar solo el id y nombre con:

INSERT INTO productos VALUES (1, 'Camiseta', NULL, NULL);
## **Ejercicio**
Se tiene la tabla **productos**:

|**COLUMNA**|**TIPO**|
| :- | :- |
|id|INT|
|nombre|VARCHAR|
|precio|INT|
|stock|INT|

Inserta un nuevo producto con los siguientes datos:

- id: 7
- nombre: Bolso
- Precio: 1000

INSERT INTO productos VALUES (7, 'Bolso', 1000, NULL);


### Añadir un registro especificando columnas
A la hora de insertar datos es posible mencionar específicamente las columnas que se van a insertar, en lugar de mencionar todos los valores en el orden en que se definen en la tabla.

Veamos un ejemplo:

Se tiene la tabla **productos**:

|**COLUMNA**|**TIPO**|
| :- | :- |
|id|INT|
|nombre|VARCHAR|
|precio|INT|
|stock|INT|

Se pide insertar un nuevo producto con los siguientes datos, pero especificando las columnas

- id: 7
- nombre: Bolso
- Precio: 1000
- Stock: 10

INSERT INTO productos (id, precio, nombre, stock) VALUES (7, 1000,'Bolso', 10);

Una ventaja de este método es que no es necesario ingresar los valores en el mismo orden en que se definen en la tabla.
## **Ejercicio**
Se tiene la tabla **usuarios**:

|**COLUMNA**|**TIPO DE DATO**|
| :- | :- |
|id|INTEGER|
|nombre|TEXT|
|apellido|TEXT|
|email|TEXT|
|telefono|TEXT|

Prueba agregando los siguientes datos a la tabla usuarios, puedes notar que tienen el orden alterado en relación a la tabla.

- id: 7
- apellido: Sánchez
- nombre: Lucía
- telefono: 333-3333
- email: <luciasanchez@outlook.com>

INSERT INTO usuarios (id, apellido, nombre, telefono, email) VALUES (7,'Sánchez','Lucía', '333-3333','luciasanchez@outlook.com');


### Añadir un registro especificando solo algunas columnas
Otro beneficio de especificar las columnas al momento de insertar datos es que se insertarán valores nulos en las columnas no mencionadas automáticamente.

Supongamos que tenemos una tabla llamada productos:

|**COLUMNA**|**TIPO**|
| :- | :- |
|nombre|TEXT|
|precio|INT|
|stock|INT|

Podemos ingresar el producto "Gorro" con un precio de 1000 y dejar el stock en nulo de la siguiente manera:

INSERT INTO productos (nombre, precio) VALUES ('Gorro', 1000);

Mas adelante aprenderemos que algunas columnas pueden tener restricciones que no permiten valores nulos.
## **Ejercicio**
Inserta un nuevo item en la tabla productos con los siguientes datos:

- nombre: Bolso
- stock: 10


### **Añadir fecha de hoy a un registro**
Si queremos insertar la fecha actual al momento de crear un registro, podemos utilizar la función CURRENT\_DATE para obtenerla.

Ejemplo: INSERT INTO usuarios (nombre, fecha\_creacion) VALUES ('Gonzalo', CURRENT\_DATE);
## **Ejercicio**

|**COLUMNA**|**TIPO**|
| :- | :- |
|nombre|TEXT|
|precio|INT|
|stock|INT|
|fecha|DATE|

Si tenemos la tabla productos, inserta un nuevo producto con los siguientes datos:

- nombre: Bolso
- stock: 10
- fecha: CURRENT\_DATE


INSERT INTO productos (nombre, stock, fecha) VALUES ('Bolso', 10,CURRENT\_DATE);


### Añadiendo fecha y hora al insertar
Si queremos insertar una fecha cualquiera al momento de crear un registro, simplemente debemos hacerlo especificando la fecha en el formato esperado.

El formato de fecha es: YYYY-MM-DD, o sea año-mes-día, donde el año es de 4 dígitos, el mes es de 2 dígitos y el día es de 2 dígitos.

Ejemplo: INSERT INTO usuarios (nombre, fecha\_creacion) VALUES ('Gonzalo', '2021-01-01');
## **Ejercicio**
Se tiene la tabla **productos**:

|**COLUMNA**|**TIPO**|
| :- | :- |
|nombre|TEXT|
|precio|INT|
|stock|INT|
|fecha|DATE|

Inserta un nuevo producto con los siguientes datos:

- nombre: Bolso
- stock: 10
- fecha: fecha\_con\_formato

La fecha del producto debe ser del primero de enero del 2023.

INSERT INTO productos (nombre, stock,fecha) VALUES ('Bolso', 10, '2023-01-01');


### Añamúltiples valores
Podemos ingresar varios registros en una tabla en una sola sentencia INSERT. Para lograrlo, debemos especificar los valores de cada registro separados por comas.

Por ejemplo, si tenemos una tabla llamada ventas con las columnas producto, cantidad y precio, podemos agregar varios registros a la tabla usando:

INSERT INTO ventas VALUES ('Camiseta', 5, 2000), ('Pantalón', 3, 1500), ('Zapatos', 2, 3000);
## **Ejercicio**
Inserta los siguientes registros en la tabla ventas:

|**PRODUCTO**|**CANTIDAD**|**PRECIO**|
| :- | :- | :- |
|Gorro|5|1000|
|Camiseta|10|500|
|Pantalón|8|1500|

INSERT INTO ventas VALUES ('Gorro', 5, 1000), ('Camiseta', 10, 500), ('Pantalón', 8, 1500);


### Crear un registro con un campo autoincremental
En una base de datos SQL, es posible agilizar el proceso de inserción de datos en una tabla mediante el uso de un campo autoincremental. Este tipo de campo es especialmente útil cuando se trata de gestionar identificadores únicos, como por ejemplo el campo "id" de una tabla. La característica de autoincremento se logra empleando la cláusula AUTOINCREMENT en la definición del campo.

Para ilustrar este proceso, consideremos una tabla llamada "empleados" con tres columnas: "id" (autoincremental), "nombre" y "apellido". Esta es la forma en que se crea la tabla:

CREATE TABLE empleados (id INTEGER PRIMARY KEY AUTOINCREMENT, nombre TEXT,apellido TEXT);

Aquí, hemos definido la columna "id" como un campo autoincremental utilizando la cláusula AUTOINCREMENT, lo que asegura que se generará automáticamente un valor único y creciente para cada nuevo registro.

Supongamos que deseamos insertar un nuevo empleado en esta tabla. Podemos utilizar la siguiente consulta SQL:

INSERT INTO empleados (nombre, apellido) VALUES ('John', 'Doe');

Al ejecutar esta consulta, se creará un nuevo empleado en la tabla "empleados". La columna "id" se incrementará automáticamente, mientras que los valores proporcionados para "nombre" y "apellido" serán almacenados en las columnas correspondientes. Esto garantiza que cada nuevo empleado tendrá un identificador único y que el proceso de inserción sea más eficiente.
## **Ejercicio**
Dada la **tabla empleados** con las columnas id, nombre y apellido, crea un nuevo empleado con el nombre "Jane" y el apellido "Smith".

INSERT INTO empleados (nombre, apellido) VALUES ('Jane', 'Smith');


### Añadir un registro asumiendo un valor por defecto
Al crear una tabla en SQL, puedes asignar valores predeterminados a sus columnas. Esto implica que al insertar nuevos datos, si no se proporciona un valor específico para una columna, se usará automáticamente el valor por defecto asignado.

Supongamos que queremos crear una tabla llamada "Productos" con las siguientes columnas:

- ID (identificador único del producto)
- Nombre (nombre del producto)
- Precio (precio del producto, con un valor por defecto de 10)

CREATE TABLE Productos (ID INTEGER PRIMARY KEY AUTOINCREMENT, Nombre TEXT, Precio INTEGER DEFAULT 10);

Si insertamos un nuevo producto sólo con el nombre, se utilizará automáticamente el valor por defecto del precio:

INSERT INTO Productos (Nombre) VALUES ('Ejemplo Producto');

En este caso, el producto se insertará con el valor 10 en la columna Precio.

Si deseamos insertar un producto con un precio diferente, simplemente proporcionamos el valor correspondiente:

INSERT INTO Productos (Nombre, Precio) VALUES ('Otro Producto', 25);
## **Ejercicio**
Dada la **tabla usuarios** con las columnas id, nombre, apellido, email y telefono, crea un nuevo usuario con los valores:

- nombre: Lucía
- apellido: Sánchez
- email: <luciasanchez@outlook.com>

La columna telefono tendrá el valor por defecto 111-1111

INSERT INTO usuarios (nombre,apellido, email) VALUES ('Lucía', 'Sánchez','luciasanchez@outlook.com');



### **Borrar todos los registros de una tabla**
En SQL, la cláusula DELETE se utiliza para eliminar registros de una tabla. Cuando se ejecuta la instrucción DELETE FROM nombre\_tabla, se eliminan todos los registros de la tabla especificada.

Es importante tener en cuenta que esta operación es irreversible y eliminará permanentemente los datos de la tabla, por lo que debes tener mucho cuidado al usar esta instrucción.
## **Ejercicios**
Borra todos los datos de la tabla 'productos'.

Delete fron productos

### Borrar un registro con where
La sentencia DELETE se utiliza para eliminar datos de una tabla. Si queremos eliminar filas específicas en lugar de todos los datos de la tabla, podemos usar la cláusula WHERE junto con la sentencia DELETE. Esto nos permite especificar una condición para determinar qué filas se eliminarán.

Por ejemplo, si tenemos una tabla de productos y queremos eliminar solo aquellos productos cuyo precio sea igual a 1000, podemos usar la siguiente consulta:

DELETE FROM productos WHERE precio = 1000
## **Ejercicio**
Dada la **tabla usuarios** con los siguientes datos:

|**ID**|**NOMBRE**|**APELLIDO**|**EMAIL**|**TELEFONO**|
| :- | :- | :- | :- | :- |
|1|Juan|Pérez|<juanperez@gmail.com>|555-1234|
|2|María|García|<mariagarcia@hotmail.com>|555-5678|
|3|Pedro|López|<pedrolopez@yahoo.com>|555-9876|
|4|Lucía|Sánchez|<luciasanchez@outlook.com>|555-5555|
|5|Jorge|Martínez|<jorgemartinez@gmail.com>|555-4321|

Borra el usuario cuyo id sea igual a 2.

delete from usuarios where id= 2


### Editar registros
La sentencia UPDATE se utiliza para realizar modificaciones en datos ya existentes de una tabla.

Se utiliza de la siguiente forma

UPDATE nombre\_tabla SET nombre\_columna = nuevo\_valor

Supongamos que tenemos una tabla **ventas** con una columna llamada "total". Si queremos aumentar en un 10% el total de todas las ventas registradas en la tabla, podemos hacerlo de la siguiente manera:

UPDATE ventas SET total = total \* 1.10;

La instrucción UPDATE afecta todas las filas de la tabla, ya que no hemos utilizado la cláusula WHERE para establecer una condición de filtro.
## **Ejercicio**
Se tiene una **tabla usuarios** con los siguientes datos:

|**ID**|**NOMBRE**|**APELLIDO**|**EMAIL**|**REGISTRADO**|
| :- | :- | :- | :- | :- |
|1|Juan|Pérez|<juanperez@gmail.com>|FALSE|
|2|María|García|<mariagarcia@hotmail.com>|FALSE|
|3|Pedro|López|<pedrolopez@yahoo.com>|FALSE|
|4|Lucía|Sánchez|<luciasanchez@outlook.com>|FALSE|
|5|Jorge|Martínez|<jorgemartinez@gmail.com>|FALSE|

Edita la columna "registrado" para que todos los usuarios tengan el valor TRUE
## Ejercicio
Se tiene una **tabla usuarios** con los siguientes datos:

|**ID**|**NOMBRE**|**APELLIDO**|**EMAIL**|**REGISTRADO**|
| :- | :- | :- | :- | :- |
|1|Juan|Pérez|<juanperez@gmail.com>|FALSE|
|2|María|García|<mariagarcia@hotmail.com>|FALSE|
|3|Pedro|López|<pedrolopez@yahoo.com>|FALSE|
|4|Lucía|Sánchez|<luciasanchez@outlook.com>|FALSE|
|5|Jorge|Martínez|<jorgemartinez@gmail.com>|FALSE|

Edita la columna "registrado" para que todos los usuarios tengan el valor TRUE

UPDATE usuarios SET registrado = true;




### Editar todos los registros utilizando where
Si queremos editar solamente algunas filas de nuestra tabla, podemos utilizar UPDATE en conjunto con WHERE. De esta forma solo se modificarán los registros que cumplan con la condición especificada.

UPDATE nombre\_tabla SET nombre\_columna = nuevo\_valor WHERE condicion;

Supongamos que gestionamos una tabla llamada empleados que contiene información sobre los empleados de una empresa. Entre las columnas se encuentran id\_empleado, nombre, salario y departamento. Si deseamos aumentar el salario en un 15% solamente para los empleados que trabajan en el departamento de "Ventas", podríamos emplear la instrucción UPDATE junto con WHERE de la siguiente manera:

UPDATE empleados SET salario = salario \* 1.15 WHERE departamento = 'Ventas';

Es importante ser precavido al elegir la condición de filtrado para tus filas. De esta manera, te aseguras de no alterar accidentalmente datos equivocados.
## **Ejercicio**
Se tiene una **tabla usuarios** con los siguientes datos:

|**ID**|**NOMBRE**|**APELLIDO**|**EMAIL**|**TELEFONO**|
| :- | :- | :- | :- | :- |
|1|Juan|Pérez|<juanperez@gmail.com>|555-1234|
|2|María|García|<mariagarcia@hotmail.com>|555-5678|
|3|Pedro|López|<pedrolopez@yahoo.com>|555-9876|
|4|Lucía|López|<luciasanchez@outlook.com>|555-5555|
|5|Jorge|Martínez|<jorgemartinez@gmail.com>|555-4321|

Asignales el telefono 123-456 al usuario con id 4.


UPDATE usuarios SET telefono='123-456' WHERE id = 4;





### Editar múltiples columnas
En SQL es posible editar múltiples columnas de un registro utilizando la cláusula SET. Para lograrlo, debemos especificar el nombre de cada columna que queremos modificar, seguido del nuevo valor que queremos asignarle.

UPDATE tabla 

`  `SET 

`    `columna1 = 'nuevo\_valor',

`    `columna2 = 'nuevo\_valor',

`    `columna3 = 'nuevo\_valor'

`  `WHERE 

`    `condicion;



UPDATE usuarios 

`  `SET 

`    `nombre = 'Juan', 

`    `apellido = 'Pérez'

`  `WHERE 

`    `id = 1;


También es posible escribir la consulta en una sola línea, pero es recomendable utilizar saltos de línea para mejorar la legibilidad del código.
## Ejercicio
Se tiene una tabla de posts con las siguientes columnas:

|**COLUMNA**|**TIPO DE DATO**|
| :- | :- |
|id|INTEGER|
|titulo|TEXT|
|contenido|TEXT|
|autor|TEXT|
|fecha|TEXT|

Edita el post con id 1 para que tenga el título "Aprendiendo SQL" y el contenido "SQL es un lenguaje de programación para gestionar bases de datos relacionales".

UPDATE posts 

SET 

titulo = 'Aprendiendo SQL', 

contenido = 'SQL es un lenguaje de programación para gestionar bases de datos relacionales'

WHERE 

id = 1;





### Nuestra primera tabla
Hasta este punto, hemos aprendido cómo realizar consultas en tablas predefinidas, e incluso cómo insertar datos a las tablas, pero ¿cómo creamos nuestras propias tablas?

Para crear una tabla en SQL, se utiliza la sentencia CREATE TABLE de la siguiente forma:

CREATE TABLE nombre\_tabla (nombre\_columna1 tipo\_de\_dato) 

Esta sentencia permite definir la estructura de la tabla, incluyendo el nombre de las columnas y sus tipos de datos. Veamos un ejemplo de cómo crear una tabla de productos que incluye diferentes tipos de datos para las columnas:

CREATE TABLE productos (nombre TEXT);

Luego, una vez creada la tabla, podemos insertar datos tal como aprendimos en ejercicios anteriores:

INSERT INTO productos values   ('Ipad Pro 2022'),  ('Iphone 13 Pro Max'),  ('Macbook Pro 2023');
## **Ejercicio**
Crea una tabla llamada **alumnos** que almacene una columan nombre de tipo texto

|**COLUMNA**|**TIPO DE DATO**|
| :- | :- |
|nombre|texto|

Inserta un registro dentro de la tabla creada utilizado los siguientes datos:

- nombre: Lucía

Pista: Para poder ingresar las dos queries requeridas, recuerda añadir punto y coma al final de cada una.

CREATE TABLE alumnos (nombre TEXT);

INSERT INTO alumnos values ('Lucía');



### Una tabla con múltiples columnas
Al momento de crear una tabla podemos especificar múltiples columnas, cada una con su nombre y tipo de dato. Por ejemplo, si queremos crear una tabla de productos que incluya el nombre, descripción y precio de cada producto, podemos hacerlo de la siguiente forma:

CREATE TABLE productos (nombre TEXT, descripcion TEXT, precio INT);
## **Ejercicio**
Crea una tabla llamada **alumnos** con las siguientes columnas:

|**COLUMNA**|**TIPO DE DATO**|
| :- | :- |
|nombre|texto|
|apellido|texto|
|telefono|texto|

Inserta un registro dentro de la tabla creada utilizado los siguientes datos:

- nombre: Lucía
- apellido: Sánchez
- telefono: 12345678

Pista: para poder ingresar las dos queries requeridas, recuerda añadir punto y coma al final de cada una.

CREATE TABLE alumnos (nombre TEXT, apellido TEXT, telefono TEXT);

insert into alumnos values ('Lucía','Sánchez','12345678')



### Tablas con distintos tipos de datos
Adicionalmente a los datos de tipo Texto podemos utilizar otros tipos de datos, en este ejercicio abordaremos los 3 siguientes tipos.

- **INTEGER** para almacenar números enteros
- **BOOLEAN** para almacenar valores de verdadero o falso
- **DATE** para almacenar fechas
## **Ejercicio**
Crea una tabla llamada **usuarios** con las siguientes columnas:

|**COLUMNA**|**TIPO DE DATO**|
| :- | :- |
|nombre|text|
|apellido|text|
|edad|integer|
|activo|boolean|
|nacimiento|date|

Luego inserta un registro dentro de la tabla creada utilizado los siguientes datos:

- nombre: Lucía
- apellido: Sánchez
- edad: 25
- activo: true
- nacimiento: 1996-01-01

Pista: para poder ingresar las dos queries requeridas, recuerda añadir punto y coma al final de cada una.

create table usuarios (nombre TEXT, apellido TEXT, edad int, activo BOOLEAN, nacimiento date);

insert into usuarios (nombre, apellido, edad, activo, nacimiento) values ('Lucía','Sánchez', 25, true, '1996-01-01')



### **Tipos reales**
Hasta el momento hemos visto los siguientes tipos de datos:

- **TEXT** para almacenar texto
- **INTEGER** para almacenar números enteros
- **BOOLEAN** para almacenar valores de verdadero o falso
- **DATE** para almacenar fechas

En este ejercicio veremos el tipo de dato REAL, que permite almacenar números con decimales.
## **Ejercicio**
Crea una tabla llamada **temperaturas** con la columna temperatura\_celsius:

|**COLUMNA**|**TIPO DE DATO**|
| :- | :- |
|temperatura\_celsius|real|

Luego inserta los siguientes registros:

|**TEMPERATURA\_CELSIUS**|
| :- |
|23\.4|
|26\.5|
|27\.1|

**Importante**. Para ingresar la parte decimal de los números, utiliza el punto (.) como separador decimal

CREATE TABLE temperaturas (

temperatura\_celsius real

); 

insert into temperaturas values (23.4);

insert into temperaturas values (26.5);

insert into temperaturas values (27.1);




### Borrar un tabla
En SQL podemos utilizar el comando **DROP TABLE** para eliminar una tabla.

Por ejemplo, si queremos eliminar la tabla **temperaturas** que creamos en el ejercicio anterior, podemos hacerlo con la siguiente query:

DROP TABLE temperaturas;

Si intentamos hacer un SELECT de la tabla **temperaturas** luego de eliminarla, obtendremos un error.
## **Ejercicio**
En este ejercicio tendremos una tabla con datos que no nos interesan, deberemos borrarla, crearla de nuevo y poblarla con los datos pedidos.

Borra la tabla **temperaturas** y vuelve a crearla con las siguientes columnas:

|**COLUMNA**|**TIPO DE DATO**|
| :- | :- |
|ciudad|TEXT|
|temperatura|REAL|
|fecha|Date|

Luego, inserta los siguientes registros:

|**CIUDAD**|**TEMPERATURA**|**FECHA**|
| :- | :- | :- |
|Buenos Aires|20\.0|2024-01-01|
|Buenos Aires|21\.0|2024-01-02|
|Santiago|22\.0|2024-01-01|
|Santiago|23\.0|2024-01-02|

**Importante:** para poder ingresar las queries requeridas, recuerda añadir punto y coma al final de cada una.

drop table temperaturas;

create table temperaturas (ciudad text, temperatura real, fecha date);

insert into temperaturas values ('Buenos Aires',20.0,'2024-01-01');

insert into temperaturas values ('Buenos Aires',21.0,'2024-01-02');

insert into temperaturas values ('Santiago',22.0,'2024-01-01');

insert into temperaturas Values ('Santiago',23.0,'2024-01-02')






### Actualizar una tabla
En este ejercicio aprenderemos a añadir una columna a una tabla existente. Para ello, utilizaremos la sentencia ALTER TABLE, que nos permite modificar la definición de una tabla.

La sintaxis para lograrlo es la siguiente:

ALTER TABLE nombre\_tabla ADD COLUMN nombre\_columna tipo\_dato;

donde tenemos que especificar el nombre de la tabla existente, el nombre de la columna nueva y el tipo de dato que utilizaremos.

Por ejemplo si tenemos la tabla personas con las columnas nombre y apellido, y queremos agregar la columna edad de tipo INTEGER, podemos hacerlo de la siguiente manera:

ALTER TABLE personas ADD COLUMN edad INTEGER;
## **Ejercicio**
En este ejercicio, vamos a modificar la tabla **productos** para agregar la columna **descripcion** de tipo **TEXT**.

Actualmente la tabla **productos** tiene las siguientes columnas:

|**COLUMNA**|**TIPO DE DATO**|
| :- | :- |
|nombre|TEXT|
|precio|REAL|

Luego de crearla deberás insertar los siguientes registros:

|**NOMBRE**|**PRECIO**|**DESCRIPCION**|
| :- | :- | :- |
|Camisa|1000\.00|Camisa de manga corta|
|Pantalón|2000\.00|Pantalón de mezclilla|
|Camisa XL|1000\.00|Camisa de manga larga|

**Importante:** para poder ingresar las queries requeridas, recuerda añadir punto y coma al final de cada una.






ALTER TABLE productos ADD COLUMN descripcion TEXT default null;

insert into productos (nombre, precio, descripcion) values ('Camisa',1000.00, 'Camisa de manga corta');

insert into productos (nombre, precio, descripcion) values ( 'Pantalón',2000.00, 'Pantalón de mezclilla');

insert into productos (nombre, precio, descripcion) values ('Camisa XL', 1000.00,'Camisa de manga larga

')


### **Introducción a restricciones**
#### **Ideas clave**
- Las restricciones o **constraints** en inglés, son reglas que se pueden aplicar a las columnas de una tabla.
- La restricción NOT NULL es un tipo de restricción que impide que se ingresen valores nulos en una columna.
- Si ingresamos un valor nulo en una columna con la restricción NOT NULL, la operación fallará.
#### **Añadir una restricción al crear una tabla**
Al crear tablas, podemos añadir restricciones (en inglés **constraints**) a las columnas para evitar que se ingresen datos que no cumplan ciertas condiciones.

En este ejercicio, aprenderemos a agregar la restricción NOT NULL, que impide agregar valores nulos en una columna. Por ejemplo, al crear una tabla de personas con nombre y apellido, podemos hacer que el nombre sea obligatorio (no nulo) y el apellido opcional.

Para lograrlo, crearemos la tabla y en la columna **nombre** agregaremos la restricción NOT NULL de la siguiente manera:

CREATE TABLE personas (

`    `nombre TEXT NOT NULL,

`    `apellido TEXT

)

Para agregar una restricción, simplemente debemos especificarla junto con la columna.

Para indicar las restricciones al diagramar una tabla, utilizaremos una columna adicional llamada **Constraints**. Ejemplo con la tabla **personas**:

|**COLUMN**|**DATA TYPE**|**CONSTRAINTS**|
| :- | :- | :- |
|nombre|TEXT|NOT NULL|
|apellido|TEXT||
Pongamos a prueba nuestra restricción con distintas consultas y observemos los resultados.

|**QUERY**|**RESULTADO**|
| :- | :- |
|INSERT INTO personas (nombre, apellido) VALUES ('Juan', 'Pérez');|Funciona|
|INSERT INTO personas (nombre, apellido) VALUES (NULL, 'Pérez');|No funciona, error: NOT NULL constraint failed: personas.nombre|
|INSERT INTO personas (apellido) VALUES ('Pérez');|No funciona, error: NOT NULL constraint failed: personas.nombre|

En resumen: en esta tabla que acabamos de crear, podremos hacer un insert de una persona con nombre y sin apellido, pero *no* podremos ingresar una persona sin nombre.
## **Ejercicio**
Crea una nueva tabla llamada *empleados* con las siguientes columnas:

|**COLUMNA**|**TIPO DE DATO**|**RESTRICCIONES**|
| :- | :- | :- |
|nombre|TEXT|NOT NULL|
|apellido|TEXT||
Luego ingresa los siguientes datos

- nombre: Pedro
- apellido: Pérez

Puedes probar un insert sin un nombre para observar el error.




CREATE TABLE empleados (

nombre TEXT NOT NULL,

apellido TEXT

);

INSERT INTO empleados (nombre, apellido) VALUES ('Pedro', 'Pérez');





### Agregar una restricción a una tabla existente
#### **Ideas clave**
- Las restricciones o **constraints** en inglés son reglas que se pueden aplicar a las columnas de una tabla.
- Se puede agregar una restricción al momento de crear una tabla.
- En SQLite no se pueden agregar directamente restricciones a tablas ya creadas.
- Pero podemos lograrlo creando una nueva tabla con la restricción, copiando los datos de la tabla original a la nueva tabla, borrando la tabla original y renombrando la nueva tabla con el nombre de la tabla original.
#### **Agregar una restricción a una tabla existente**
Por ejemplo, si tenemos una tabla **personas** con las columnas **nombre** y **apellido**.

|**COLUMNA**|**TIPO DE DATO**|**RESTRICCIONES**|
| :- | :- | :- |
|nombre|TEXT||
|apellido|TEXT||
y queremos agregarle la restricción **NOT NULL** a la columna **nombre**.

Lo que tenemos que hacer es:

1. Crear una nueva tabla con la restricción.

/\* 1. Creamos la nueva tabla con la restricción \*/

CREATE TABLE personas2 (

`    `nombre TEXT NOT NULL,

`    `apellido TEXT

);

2. Copiar los datos de la tabla original a la nueva tabla.

/\* 2. Copiamos los datos de la tabla original a la nueva tabla \*/

INSERT INTO personas2 (nombre, apellido)

`    `SELECT nombre, apellido

`    `FROM personas;

3. Borrar la tabla original.

/\* 3. Borramos la tabla original \*/

DROP TABLE personas;

4. Renombrar la nueva tabla con el nombre de la tabla original.

/\* 4. Renombramos la nueva tabla con el nombre de la tabla original \*/

ALTER TABLE personas2 RENAME TO personas;

En otros motores de bases de datos como PostgreSQL o MySQL si es posible agregar restricciones a tablas existente sin necesidad de crear una nueva tabla.
## **Ejercicio**
Se tiene una tabla llamada patentes con las siguientes columnas:

|**COLUMNA**|**TIPO DE DATO**|**RESTRICCIONES**|
| :- | :- | :- |
|patente|TEXT||
Con la siguiente información:

|**PATENTE**|
| :- |
|ABC123|
|ABC124|

Se pide agregar una restricción de not null a la columna **patente**.



CREATE TABLE patentes2 (

patente TEXT NOT NULL

);

INSERT INTO patentes2 (patente)

SELECT patente

FROM patentes;

DROP TABLE patentes;

ALTER TABLE patentes2 RENAME TO patentes; 







CREATE TABLE personas2 ( nombre TEXT, apellido TEXT, edad INTEGER )

INSERT INTO personas2 

SELECT nombre, apellido, edad

FROM personas;

DROP TABLE personas; 

ALTER TABLE personas2 RENAME TO personas;



### Restricción unique
#### **Ideas clave**
- Existen distintos tipos de restricciones que se pueden aplicar a las columnas de una tabla.
- La restricción de unicidad, o **UNIQUE**, nos permite evitar duplicados en una columna específica.
#### **Restricción UNIQUE**
La restricción **UNIQUE**, nos permite evitar duplicados en una columna específica. Un caso muy popular de esta restricción es evitar personas con el mismo correo electrónico.

Para agregar una restricción de UNIQUE simplemente tenemos que especificarla al crear la tabla. Por ejemplo, si queremos que el correo electrónico de las personas sea único, podemos crear la tabla de la siguiente manera:

CREATE TABLE personas (

`    `nombre text

`    `apellido text

`    `email text UNIQUE

)

Pongamos a prueba nuestra restricción con distintas consultas y observemos los resultados.

|**QUERY**|**FUNCIONA**|
| :- | :- |
|INSERT INTO personas (nombre, apellido, email) VALUES ('Juan', 'Pérez', 'juan.perez@email.com');|Funciona|
|INSERT INTO personas (nombre, apellido, email) VALUES ('María', 'García', 'juan.perez@email.com');|No funciona, error: UNIQUE constraint failed: personas.email|
|INSERT INTO personas (nombre, apellido, email) VALUES ('Pedro', 'Pérez', 'pedro.perez@email.com');|Funciona|

En resumen: En esta tabla que acabamos de crear, el correo electrónico de cada persona debe ser único; no podremos ingresar dos personas con el mismo correo electrónico.
## **Ejercicio**
En este ejercicio, vamos a crear una tabla llamada **productos** con las siguientes columnas:

|**COLUMNA**|**TIPO DE DATO**|**RESTRICCIONES**|
| :- | :- | :- |
|nombre|TEXT|NOT NULL|
|codigo|TEXT|UNIQUE|
|precio|REAL|NOT NULL|

Luego, vamos a insertar los siguientes registros:

|**NOMBRE**|**PRECIO**|**CODIGO**|
| :- | :- | :- |
|Camisa|1000\.00|CAM-001|
|Pantalón|2000\.00|PAN-001|
|Camisa XL|1000\.00|CAM-002|

Pista: para poder ingresar las dos queries requeridas, recuerda añadir punto y coma al final de cada una.

Si quieres probar un insert para observar el error puedes hacerlo con el código CAM-001.
### **Borrar una restricción**
#### Ideas clave
- Las restricciones o **constraints** en inglés, son reglas que se pueden aplicar a las columnas de una tabla.
- Así como se pueden agregar restricciones a las columnas, también se pueden borrar.
#### Borrar una restricción de una tabla existente
Para borrar una restricción de una tabla existente en SQLite, se debe seguir un procedimiento similar al de agregar una restricción.

1. Crear una nueva tabla sin la restricción.
1. Copiar los datos de la tabla original a la nueva tabla.
1. Borrar la tabla original.
1. Renombrar la nueva tabla con el nombre de la tabla original.

Para el ejemplo tendremos una tabla llamada **temperaturas** con la siguiente estructura:

|**COLUMNA**|**TIPO DE DATO**|**RESTRICCIONES**|
| :- | :- | :- |
|temperatura|REAL|NOT NULL|

/\* 1. Creamos la nueva tabla sin la restricción \*/

CREATE TABLE temperaturas2 (

`    `temperatura REAL 

);

/\* 2. Copiamos los datos de la tabla original a la nueva tabla \*/

INSERT INTO temperaturas2 (temperatura)

`    `SELECT temperatura

`    `FROM temperaturas;

3

/\* 3. Borramos la tabla original \*/

DROP TABLE temperaturas;

4

/\* 4. Renombramos la nueva tabla con el nombre de la tabla original \*/

ALTER TABLE temperaturas2 RENAME TO temperaturas;
## Ejercicio
Se tiene una tabla llamada personas con las siguientes columnas:

|**COLUMNA**|**TIPO DE DATO**|**RESTRICCIONES**|
| :- | :- | :- |
|nombre|TEXT|NOT NULL|
|apellido|TEXT|NOT NULL|
|edad|INTEGER||
Se pide borrar la restricción de not null de las columnas **nombre** y **apellido**.


CREATE TABLE personas2 (

nombre text,

apellido text,

edad integer

);

INSERT INTO personas2 (nombre, apellido, edad)

SELECT nombre, apellido, edad

FROM personas;

DROP TABLE personas;

ALTER TABLE personas2 RENAME TO personas;




### Restricción unique
#### **Ideas clave**
- Existen distintos tipos de restricciones que se pueden aplicar a las columnas de una tabla.
- La restricción de unicidad, o **UNIQUE**, nos permite evitar duplicados en una columna específica.
#### **Restricción UNIQUE**
La restricción **UNIQUE**, nos permite evitar duplicados en una columna específica. Un caso muy popular de esta restricción es evitar personas con el mismo correo electrónico.

Para agregar una restricción de UNIQUE simplemente tenemos que especificarla al crear la tabla. Por ejemplo, si queremos que el correo electrónico de las personas sea único, podemos crear la tabla de la siguiente manera:

CREATE TABLE personas (

`    `nombre text

`    `apellido text

`    `email text UNIQUE

)


Pongamos a prueba nuestra restricción con distintas consultas y observemos los resultados.

|**QUERY**|**FUNCIONA**|
| :- | :- |
|INSERT INTO personas (nombre, apellido, email) VALUES ('Juan', 'Pérez', 'juan.perez@email.com');|Funciona|
|INSERT INTO personas (nombre, apellido, email) VALUES ('María', 'García', 'juan.perez@email.com');|No funciona, error: UNIQUE constraint failed: personas.email|
|INSERT INTO personas (nombre, apellido, email) VALUES ('Pedro', 'Pérez', 'pedro.perez@email.com');|Funciona|

En resumen: En esta tabla que acabamos de crear, el correo electrónico de cada persona debe ser único; no podremos ingresar dos personas con el mismo correo electrónico.
## Ejercicio
En este ejercicio, vamos a crear una tabla llamada **productos** con las siguientes columnas:

|**COLUMNA**|**TIPO DE DATO**|**RESTRICCIONES**|
| :- | :- | :- |
|nombre|TEXT|NOT NULL|
|codigo|TEXT|UNIQUE|
|precio|REAL|NOT NULL|

Luego, vamos a insertar los siguientes registros:

|**NOMBRE**|**PRECIO**|**CODIGO**|
| :- | :- | :- |
|Camisa|1000\.00|CAM-001|
|Pantalón|2000\.00|PAN-001|
|Camisa XL|1000\.00|CAM-002|

Pista: para poder ingresar las dos queries requeridas, recuerda añadir punto y coma al final de cada una.

Si quieres probar un insert para observar el error puedes hacerlo con el código CAM-001.

create table productos(nombre text not null, precio REAL not NULL, codigo text UNIQUE);

insert into productos (nombre, codigo, precio) values('Camisa','CAM-001' , 1000.00);

insert into productos (nombre, codigo, precio) values('Pantalón','PAN-001',2000.00);

insert into productos (nombre, codigo, precio) values('Camisa XL','CAM-002',1000.00);



### Restricciones con check
#### **Ideas clave**
- Existen distintos tipos de restricciones que se pueden aplicar a las columnas de una tabla.
- La restricción de no nulidad, o **NOT NULL**, impide que se ingresen valores nulos en una columna.
- La restricción de unicidad, o **UNIQUE**, nos permite evitar duplicados en una columna específica.
- La restricción **CHECK** nos permite establecer una condición que los valores de una columna deben cumplir.
#### **Restricciones CHECK**
La restricción **CHECK** nos permite establecer una condición que los valores de una columna deben cumplir. Por ejemplo, si queremos que el salario de los empleados sea mayor a cero, podemos agregar una restricción de CHECK a la columna **salario**.

Para agregar una restricción de CHECK simplemente tenemos que especificarlo en la definición de la columna, proporcionando la condición que debe cumplir el valor de la columna. Por ejemplo:

CREATE TABLE empleados (

`    `nombre TEXT,

`    `salario REAL CHECK (salario > 0)

);

|**QUERY**|**FUNCIONA**|
| :- | :- |
|INSERT INTO empleados (nombre, salario) VALUES ('Juan', 3000);|Funciona|
|INSERT INTO empleados (nombre, salario) VALUES ('Ana', -3000);|No funciona, error: CHECK constraint failed: empleados|
|INSERT INTO empleados (nombre, salario) VALUES ('Luis', 3000);|Funciona|
## **Ejercicio**
En este ejercicio, vamos a crear una tabla llamada **productos** con las siguientes columnas:

|**COLUMNA**|**TIPO DE DATO**|**RESTRICCIONES**|
| :- | :- | :- |
|nombre|TEXT|NOT NULL|
|precio|REAL|NOT NULL|
|stock|INTEGER|CHECK (stock >= 0)|

Luego, vamos a insertar los siguientes registros:

|**NOMBRE**|**PRECIO**|**STOCK**|
| :- | :- | :- |
|Camisa|1000\.00|10|
|Pantalón|2000\.00|5|
|Camisa XL|1000\.00|3|




Pista: para poder ingresar las dos queries requeridas, recuerda añadir punto y coma al final de cada una.

Si quieres probar un insert para observar el error puedes hacerlo ingresando un stock negativo.


CREATE TABLE Productos(

nombre TEXT NOT NULL,

precio real NOT NULL, 

stock INTEGER CHECK (stock >= 0));

insert into Productos (nombre, precio, stock) values('Camisa', 1000.00,10);

insert into Productos (nombre, precio, stock) values('Pantalón', 2000.00,5);

insert into Productos (nombre, precio, stock) values('Camisa XL', 1000.00,3);



### Clave primaria
#### **Ideas clave**
- Existen distintos tipos de restricciones que se pueden aplicar a las columnas de una tabla como **NOT NULL**, **UNIQUE** y **CHECK**.
- La restricción **Primary Key** impide que se ingresen valores nulos y asegura que no haya duplicados en una columna específica. Para efectos prácticos, podemos decir que es una combinación de **Unique** y **Not Null**
#### **¿Qué es una clave primaria?**
La clave primaria, o en inglés **PRIMARY KEY** es una restricción que sirve para identificar de forma única cada registro en una tabla. Por ejemplo supongamos que tenemos una tabla llamada **boletas** con los siguientes registros:

|**ID**|**MONTO DE LA BOLETA**|**FECHA DE EMISION**|
| :- | :- | :- |
|1|10\.000|2021-10-01|
|2|12\.000|2021-10-02|
|3|16\.000|2021-10-03|

Y queremos buscar la boleta con id 2. Si no tuvieramos una clave primaria, podríamos tener dos boletas con el mismo id, y no sabríamos cuál de las dos es la que queremos, o podríamos tener boletas con id nulo, y no sabríamos cuál es la boleta que buscamos.

La restricción de primary key nos asegura esto no suceda.

Cuando tenemos una clave primaria, tenemos certeza de que podemos buscar cualquier registro en la base de datos y luego modificarlo o eliminarlo, y no habrá ningún otro registro modificado o eliminado que el seleccionado. Esto nos permite cuidar la **integridad de los datos**.
#### **Agregar una clave primaria a una tabla nueva**
Para agregar una clave primaria a una tabla nueva, simplemente tenemos que especificarlo en la definición de la columna. Por ejemplo:

CREATE TABLE boletas (

`    `id INT PRIMARY KEY,

`    `monto\_de\_la\_boleta REAL,

`    `fecha\_de\_emision DATE

);
## **Ejercicio**
Crea una tabla llamada **posts** con las siguientes columnas:

|**COLUMN NAME**|**DATA TYPE**|**CONSTRAINTS**|
| :- | :- | :- |
|id|INT|PRIMARY KEY|
|title|TEXT||
|content|TEXT||
inserta los siguientes registros:

|**ID**|**TITLE**|**CONTENT**|
| :- | :- | :- |
|1|Introducción|¡Bienvenido al mundo de la programación!|
|2|Primeros Pasos|Sumérgete en los conceptos básicos de la programación.|
|3|Temas Avanzados|Explora conceptos y técnicas avanzadas en programación.|

Pista: para poder ingresar las dos queries requeridas, recuerda añadir punto y coma al final de cada una.

Si quieres poner a prueba la clave primaria puedes intentar insertar un id nulo o un id que ya hayas ingresado.

create table posts (

id int primary key,

title text,

content text

);

insert into posts (id, title, content) values(1,'Introducción', '¡Bienvenido al mundo de la programación!');

insert into posts (id, title, content) values(2,'Primeros Pasos', 'Sumérgete en los conceptos básicos de la programación.');

insert into posts (id, title, content) values(3,'Temas Avanzados', 'Explora conceptos y técnicas avanzadas en programación.');




### Autoincremental
#### **Ideas clave**
- La restricción **Primary Key** impide que se ingresen valores nulos y asegura que no haya duplicados en una columna específica. Para efectos prácticos, podemos decir que es una combinación de **Unique** y **Not Null**.
- Los campos autoincrementales nos permiten generar un valor único de forma automática para cada registro que insertemos en una tabla.
- Si un campo de clave primaria es un número entero, se convierte automáticamente en un campo autoincremental en **SQLITE**.
#### **¿Qué son los campos autoincrementales?**
Los campos autoincrementales son campos que generan un valor único de forma automática para cada registro que insertemos en una tabla. Usualmente, el incremento es de 1 en 1.

Entonces si tenemos una tabla como la siguiente:

|**ID**|**MONTO DE LA BOLETA**|**FECHA DE EMISION**|
| :- | :- | :- |
|1|10\.000|2021-10-01|
|2|12\.000|2021-10-02|
|3|16\.000|2021-10-03|

Y agregamos un nuevo registro sin especificar el valor del campo id, la base de datos se encargará de generar un valor único para ese campo, que para este caso sería 4.
#### **Cómo ingresar un nuevo registro con un campo autoincremental**
Para ingresar un nuevo registro en la tabla, simplemente omitimos el campo id y la base de datos se encargará de asignarle un valor único.

Ejemplo:

INSERT INTO boletas (monto\_de\_la\_boleta, fecha\_de\_emision) VALUES (20.000, '2021-10-04');

Observa que no estamos ingresando el campo id en la query.

Luego, si seleccionamos todos los registros de la tabla de la siguiente forma:

SELECT \* FROM boletas;

Veremos que el campo id del nuevo registro tiene un valor único y mayor al de los registros anteriores.

|**ID**|**MONTO DE LA BOLETA**|**FECHA DE EMISION**|
| :- | :- | :- |
|1|10\.000|2021-10-01|
|2|12\.000|2021-10-02|
|3|16\.000|2021-10-03|
|4|20\.000|2021-10-04|

Un campo definido como INTEGER (o INT) + PRIMARY KEY se convierte automáticamente en un campo autoincremental en **SQLITE**.
## **Ejercicio**
Crea una tabla llamada **usuarios** con las siguientes columnas:

|**COLUMNA**|**TIPO DE DATO**|**RESTRICCIONES**|
| :- | :- | :- |
|id|INTEGER|PRIMARY KEY|
|nombre|TEXT|NOT NULL|
|fecha\_creacion|DATE||
Luego, vamos a insertar los siguientes registros:

|**NOMBRE**|**FECHA\_CREACION**|
| :- | :- |
|Ana|2024-01-01|
|Gonzalo|2024-01-02|
|Juan|2024-01-03|
|María|2024-01-04|

Pista: No ingreses los ids, la base de datos se encargará de generarlos automáticamente.



create table usuarios (id INTEGER PRIMARY KEY, nombre NOT NULL, fecha\_creacion );

INSERT INTO usuarios (nombre, fecha\_creacion) values('Ana', '2024-01-01');

INSERT INTO usuarios (nombre, fecha\_creacion) values('Gonzalo', '2024-01-02');

INSERT INTO usuarios (nombre, fecha\_creacion) values('Juan', '2024-01-03');

INSERT INTO usuarios (nombre, fecha\_creacion) values('María', '2024-01-04');



### **Autoincremental parte 2**
#### **Ideas clave**
- Si un campo de clave primaria es un número entero, se convierte automáticamente en un campo autoincremental en **SQLITE**.
- Si se ingresa un registro con un valor mayor al de la secuencia actual, la base de datos se encarga de actualizar la secuencia para que el siguiente registro tenga un valor mayor al del registro que acabamos de insertar.
#### **Actualización de la secuencia**
Cuando tenemos campos autoincrementales en una tabla e insertamos un nuevo registro con un valor más alto que el de la secuencia actual, la base de datos se encarga de actualizar la secuencia para que el siguiente registro tenga un valor mayor al del registro que acabamos de insertar.

Por ejemplo, si tenemos una tabla con los siguientes registros:

|**ID**|**NOMBRE**|
| :- | :- |
|1|Ana|
|2|Gonzalo|
|3|Juan|

Luego insertamos un nuevo registro con un id mayor al de la secuencia actual:

INSERT INTO usuarios (id, nombre) VALUES (10, 'María');

Y luego insertamos un nuevo registro sin especificar el id:

INSERT INTO usuarios (nombre) VALUES ('Pedro');

Obtendremos la siguiente tabla:

|**ID**|**NOMBRE**|
| :- | :- |
|1|Ana|
|2|Gonzalo|
|3|Juan|
|10|María|
|11|Pedro|
## **Ejercicio**
Crea una tabla llamada **transacciones** con las siguientes columnas:

|**COLUMNA**|**TIPO DE DATO**|**RESTRICCIONES**|
| :- | :- | :- |
|id|INTEGER|PRIMARY KEY|
|monto|REAL|NOT NULL|
|fecha|DATE||
Luego, vamos a insertar los siguientes registros:

|**ID**|**MONTO**|**FECHA**|
| :- | :- | :- |
||1000\.00|2024-01-01|
||2000\.00|2024-01-02|
||3000\.00|2024-01-03|
|10|4000\.00|2024-01-04|
||5000\.00|2024-01-05|

**Importante**: Al único campo que vamos a agregar un id de forma personalizada va a ser al cuarto registro, esto con el fin de observar la relación que se genera entre el campo incremental y cómo aumenta según el valor que insertemos.

CREATE TABLE transacciones (id INTEGER PRIMARY KEY,

monto REAL NOT NULL,

fecha DATE);

INSERT INTO transacciones (monto,fecha) values (1000.00,'2024-01-01');

INSERT INTO transacciones (monto,fecha) values (2000.00,'2024-01-02');

INSERT INTO transacciones (monto,fecha) values (3000.00,'2024-01-03');

INSERT INTO transacciones (id,monto,fecha) values (10,4000.00,'2024-01-04');

INSERT INTO transacciones (monto,fecha) values (5000.00,'2024-01-05');



### **Primary key y texto**
La clave primaria no está limitada exclusivamente a valores numéricos; también se pueden utilizar datos de texto. Tomemos, por ejemplo, una tabla de personas, donde podríamos emplear la dirección de correo electrónico como clave primaria, ya que cada individuo posee una dirección de correo única.

En SQLite, los campos que son de tipo INTEGER y se designan como PRIMARY KEY no pueden contener valores nulos. No obstante, a diferencia de otros sistemas de gestión de bases de datos como MySQL o PostgreSQL, cuando se utiliza PRIMARY KEY con tipos de datos como texto u otros, se permite que el valor sea nulo.

Por lo tanto, si queremos que un campo sea tanto clave primaria como no nulo, debemos especificarlo mediante la combinación de PRIMARY KEY y NOT NULL.

Ejemplo:

CREATE TABLE posts (

`    `title text primary key not null

)
## **Ejercicio**
Crea una tabla llamada **personas** con las siguientes columnas:

|**COLUMN NAME**|**DATA TYPE**|**CONSTRAINTS**|
| :- | :- | :- |
|email|TEXT|PRIMARY KEY NOT NULL|
|nombre|TEXT||
|apellido|TEXT||
Inserta los siguientes registros:

|**EMAIL**|**NOMBRE**|**APELLIDO**|
| :- | :- | :- |
|<example1@example.com>|John|Doe|
|<example2@example.com>|Jane|Smith|
|<example3@example.com>|Mike|Johnson|

Puedes probar usando el mismo email en dos registros diferentes para que observes como se comporta la restricción.
#### **Edi**
#### **tor**
Escribe tu respuesta dentro del editor:

create table personas (email TEXT PRIMARY KEY NOT NULL,

nombre TEXT, 

apellido TEXT );

insert into personas (email, nombre, apellido) values ('example1@example.com', 'John', 'Doe');

insert into personas (email, nombre, apellido) values ('example2@example.com', 'Jane', 'Smith');

insert into personas (email, nombre, apellido) values ('example3@example.com', 'Mike', 'Johnson')



### **Clave Foránea**
En este ejercicio introduciremos el concepto de **clave foránea** o **foreign key**.

La clave foránea es una restricción que se le puede agregar a una columna de una tabla para indicar que los valores que se inserten en esa columna deben existir en otra tabla.

Por ejemplo, si tenemos una tabla de personas y una tabla de autos, podríamos agregar una columna **persona\_id** a la tabla de autos, y agregarle la restricción de clave foránea para indicar que el valor de esa columna debe existir en la tabla de personas. De esta forma nos aseguramos que no se inserten autos de personas que no existen o que se borren personas que tienen autos asignado a su nombre dejando autos sin dueño.

**personas**

|**COLUMNA**|**TIPO DE DATO**|**RESTRICCIONES**|
| :- | :- | :- |
|id|INTEGER|PRIMARY KEY|
|nombre|TEXT||
|apellido|TEXT||
**autos**

|**COLUMNA**|**TIPO DE DATO**|**RESTRICCIONES**|
| :- | :- | :- |
|id|INTEGER|PRIMARY KEY|
|patente|TEXT||
|persona\_id|INTEGER|FOREIGN KEY (persona\_id) REFERENCES personas(id)|

Con los siguientes datos:

**personas**

|**ID**|**NOMBRE**|**APELLIDO**|
| :- | :- | :- |
|1|John|Doe|
|2|Jane|Smith|

**autos**

|**ID**|**PATENTE**|**PERSONA\_ID**|
| :- | :- | :- |
|1|ABC123|1|
|2|DEF456|2|

Podemos ver que el auto con patente ABC123 pertenece a la persona con id 1, y el auto con patente DEF456 pertenece a la persona con id 2. Adicionalmente la clave foránea nos asegura que no podamos borrar la persona con id 1 mientras exista un auto con persona\_id 1. De la misma forma, no podremos insertar un auto con persona\_id 3, ya que no existe una persona con id 3.
## **Agregando la clave foránea**
Para agregar una clave foránea a una tabla existente, debemos especificar la restricción **FOREIGN KEY** seguida del nombre de la columna y la tabla a la que hace referencia, y finalmente la columna de la tabla a la que hace referencia.

La sintaxis es la siguiente:

ALTER TABLE nombre\_tabla ADD COLUMN nombre\_columna tipo\_dato REFERENCES nombre\_tabla\_referencia(nombre\_columna\_referencia);

Se ve complicado, pero veamos un ejemplo con las tablas **personas** y **autos**.

ALTER TABLE autos ADD COLUMN persona\_id INTEGER REFERENCES personas(id);

La clave foránea debe hacer referencia a una columna que tenga una restricción de **clave primaria**
## **Ejercicio**
Se tienen las tablas **articulos** y **categorias** con la siguiente estructura:

**articulos**

|**COLUMNA**|**TIPO DE DATO**|**RESTRICCIONES**|
| :- | :- | :- |
|id|INTEGER|PRIMARY KEY|
|nombre|TEXT||
|precio|REAL||
**categorias**

|**COLUMNA**|**TIPO DE DATO**|**RESTRICCIONES**|
| :- | :- | :- |
|id|INTEGER|PRIMARY KEY|
|nombre|TEXT||
Se pide agregar una clave foránea a la tabla **articulos** para que la columna **categoria\_id** haga referencia a la columna **id** de la tabla **categorias**.

ALTER TABLE articulos ADD COLUMN categoria\_id integer REFERENCES categorias(id);




### Pk y fks
Los conceptos de clave primaria y clave foránea son fundamentales para el diseño de bases de datos y los ocuparemos tan frecuentemente que los abreviare como PK **Primary Key** y FK **Foreign Key** respectivamente.

Con la clave primaria podemos identificar de forma única cada registro de una tabla, y con la clave foránea podemos relacionar dos tablas entre si y evitar que existan registros que no tengan una relación válida.

PK = Primary Key

FK = Foreign Key

A partir de ahora utilizaremos frecuentemente estas abreviaciones. También veremos que casi todas las tablas tendrán una clave primaria (PK). **Esto se debe a que la clave primaria nos ayuda a mantener la integridad de los datos, y nos permite identificar de forma única cada registro de una tabla.**

Una práctica común en el diseño de bases de datos es utilizar una columna llamada **id** como clave primaria. Esta columna es de tipo **INTEGER** y tiene la restricción **PRIMARY KEY**. Además, es común que esta columna sea autoincremental, es decir, que el valor de la columna se incremente automáticamente cada vez que se inserta un nuevo registro. Pero esto no es una obligación. Definir una clave primaria es una decisión de diseño, y en algunos casos puede ser más conveniente utilizar otra columna como clave primaria.
## **Ejercicio**
Se tiene la tabla **transacciones** y la tabla usuarios con la siguiente estructuras:

**transacciones**

|**COLUMNA**|**TIPO DE DATO**|**RESTRICCIONES**|
| :- | :- | :- |
|id|INTEGER|PRIMARY KEY|
|monto|REAL||
|usuario\_id|INTEGER|FOREIGN KEY (usuario\_id) REFERENCES usuarios(id)|

**usuarios**

|**COLUMNA**|**TIPO DE DATO**|**RESTRICCIONES**|
| :- | :- | :- |
|id|INTEGER|PRIMARY KEY|
|nombre|TEXT||
|apellido|TEXT||
Con los siguientes datos:

**transacciones**

|**ID**|**MONTO**|**USUARIO\_ID**|
| :- | :- | :- |
|1|100|1|
|2|200|2|
|3|300|1|

**usuarios**

|**ID**|**NOMBRE**|**APELLIDO**|
| :- | :- | :- |
|1|John|Doe|
|2|Jane|Smith|

1. En este ejercicio primero intentaremos crear una transacción con un usuario que no existe para observar el error.
1. Intentaremos borrar un usuario que tiene transacciones asociadas para observar el error.
1. Luego eliminaremos nuestras consultas anteriores y modificaremos la tabla de transacciones para eliminar la clave foránea. Solo se debe eliminar la clave foránea, no la columna.

TIP: Esto requiere crear una tabla temporal, copiar los datos de la tabla original a la tabla temporal, borrar la tabla original, y renombrar la tabla temporal con el nombre de la tabla original.

4. Finalmente se deben asociar las transacciones al usuario con id 3. El cual no existe y la idea es demostrar que sin la FK podemos insertar transacciones sin usuarios asociados.

Los puntos 1 y 2 son para observar que sucede. Para lograr la respuesta correcta tienes que realizar los puntos 3 y 4 en el editor.

insert into transacciones (monto, usuario\_id) values (10,3);

delete from transacciones where usuario\_id = 2;





### Múltiples tablas
#### **Ideas clave**
- La cláusula JOIN permite combinar datos de varias tablas en una única tabla de resultados.
- Para realizar la unión, es necesario especificar las tablas que se desean unir y la condición de unión correspondiente.
#### **Combinando datos de múltiples tablas con la cláusula JOIN**
Cuando trabajamos con bases de datos relacionales, surge con frecuencia la necesidad de combinar datos de varias tablas.

Veamos un ejemplo:

Tabla **usuarios**

|**EMAIL1**|**NOMBRE**|**EDAD**|
| :- | :- | :- |
|<juan.perez@example.com>|Juan Pérez|30|
|<maria.gonzalez@example.com>|Maria González|25|
|<john.doe@example.com>|John Doe|40|
|<test.user@example.com>|Test User|22|

Tabla **datos\_contacto**

|**EMAIL2**|**TELÉFONO**|
| :- | :- |
|<juan.perez@example.com>|555-123-4567|
|[maria.gonzalez@example.co](mailto:maria.gonzalez@example.com)[m](mailto:maria.gonzalez@example.com)|444-987-6543|
|<john.doe@example.com>|777-555-8888|
|<test.user@example.com>|111-222-3333|
|<juan.perez@example.com>|999-888-7777|
|<maria.gonzalez@example.com>|333-111-0000|

Para obtener todos los email, nombre, edad y teléfono en una **única tabla** utilizaremos la cláusula JOIN.

En nuestro ejemplo, podemos unir las tablas con la siguiente consulta:


SELECT \*

FROM 

`    `usuarios

INNER JOIN 

`    `datos\_contacto

ON 

`    `email1 = email2;

Para unir tablas tenemos que establecer una o más claves de unión. En este caso, lo que tienen en común ambas tablas es el email.

Si aplicáramos la consulta anterior, obtendríamos:

|**EMAIL1**|**NOMBRE**|**EDAD**|**EMAIL2**|**TELÉFONO**|
| :- | :- | :- | :- | :- |
|<juan.perez@example.com>|Juan Pérez|30|<juan.perez@example.com>|555-123-4567|
|<juan.perez@example.com>|Juan Pérez|30|<juan.perez@example.com>|999-888-7777|
|<maria.gonzalez@example.com>|Maria González|25|<maria.gonzalez@example.com>|444-987-6543|
|[maria.gonzalez@example.co](mailto:maria.gonzalez@example.com)[m](mailto:maria.gonzalez@example.com)|Maria González|25|[maria.gonzalez@example.co](mailto:maria.gonzalez@example.com)[m](mailto:maria.gonzalez@example.com)|333-111-0000|
|<john.doe@example.com>|John Doe|40|<john.doe@example.com>|777-555-8888|
|<test.user@example.com>|Test User|22|<test.user@example.com>|111-222-3333|

**Importante**: Observemos que los registros de ambas tablas se han combinado en una única tabla de resultados.
### Ejercicio
Utilizando lo aprendido, selecciona todos los usuarios junto a sus notas. Observa los resultados antes de avanzar.

Tabla **usuarios**:

|**EMAIL1**|**NOMBRE**|**EDAD**|
| :- | :- | :- |
|<juan.perez@example.com>|Juan Pérez|30|
|<maria.gonzalez@example.com>|Maria González|25|
|<john.doe@example.com>|John Doe|40|
|<test.user@example.com>|Test User|22|

Tabla **notas**:

|**EMAIL2**|**NOTAS**|
| :- | :- |
|<juan.perez@example.com>|90|
|<maria.gonzalez@example.com>|100|
|<john.doe@example.com>|80|
|<test.user@example.com>|0|
|<juan.perez@example.com>|100|
|<maria.gonzalez@example.com>|100|


SELECT \*

FROM 

usuarios

INNER JOIN 

notas

ON 

email1 = email2;

### Múltiples tablas: utilizando atributo del mismo nombre
#### **Ideas clave**
- La cláusula JOIN nos permite combinar los datos de varias tablas en una única tabla de resultados.
- Para hacer la unión debemos especificar las tablas que queremos unir y la condición de unión.
- Cuando la columna se llama igual en las dos tablas, tenemos que especificar el nombre de la tabla para evitar ambigüedad.
#### **Múltiples tablas: consecuencia de tener atributos con el mismo nombre**
En el ejercicio anterior realizamos un JOIN entre dos tablas donde una de ellas tenía un atributo llamado email1 y la otra email2. En este ejercicio trabajaremos con un problema del mismo tipo, pero donde en las dos tablas el atributo se llama igual.

Para ejemplificar esto, utilizaremos el nombre email en ambas tablas.

Tabla **usuarios**:

|**EMAIL**|**NOMBRE**|**EDAD**|
| :- | :- | :- |
|<juan.perez@example.com>|Juan Pérez|30|
|<maria.gonzalez@example.com>|Maria González|25|
|<john.doe@example.com>|John Doe|40|
|<test.user@example.com>|Test User|22|

Tabla **datos\_contacto**:

|**EMAIL**|**TELÉFONO**|
| :- | :- |
|<juan.perez@example.com>|555-123-4567|
|<maria.gonzalez@example.com>|444-987-6543|
|<john.doe@example.com>|777-555-8888|
|<test.user@example.com>|111-222-3333|
|<juan.perez@example.com>|999-888-7777|
|<maria.gonzalez@example.com>|333-111-0000|

Si intentamos probar la consulta anterior obtendremos:


SELE

CT \*

FROM 

`    `usuarios

JOIN

`    `datos\_contacto

ON

`    `email = email;

SQLITE\_ERROR: sqlite3 result code 1: ambiguous column name: email

Y esto se debe a que SQL no sabe a cuál email nos referimos en la condición de unión. Para solucionar esto, debemos especificar el nombre de la tabla al que pertenece el atributo.
#### Resolviendo la ambigüedad
Para arreglar esto NO tenemos que cambiarle el nombre a la columna, simplemente tenemos que especificar a qué tabla pertenece el atributo. Por ejemplo, podemos hacer lo siguiente:


SELECT \* 

FROM 

`    `usuarios 

JOIN 

`    `datos\_contacto 

ON 

`    `usuarios.email = datos\_contacto.email

De esta forma, SQL puede entender a cuál email nos referimos en cada situación.
#### Alias
En SQL, podemos utilizar alias para referirnos a las tablas de una forma más corta. Por ejemplo, si queremos referirnos a la tabla usuarios como u y a la tabla datos\_contacto como dc, podemos hacer lo siguiente:

SELECT \* 

FROM 

`    `usuarios u

JOIN 

`    `datos\_contacto dc 

ON 

`    `u.email = dc.email


## Ejercicio
Utilizando lo aprendido, selecciona todos los usuarios junto a sus notas. Recuerda que para especificar la clave de unión debes utilizar el nombre de la tabla para evitar ambigüedad. Observa los resultados antes de avanzar.

Tabla **usuarios**:

|**EMAIL**|**NOMBRE**|**EDAD**|
| :- | :- | :- |
|<juan.perez@example.com>|Juan Pérez|30|
|<maria.gonzalez@example.com>|Maria González|25|
|<john.doe@example.com>|John Doe|40|
|<test.user@example.com>|Test User|22|

Tabla **notas**:

|**EMAIL**|**NOTAS**|
| :- | :- |
|<juan.perez@example.com>|90|
|<maria.gonzalez@example.com>|100|
|<john.doe@example.com>|80|
|<test.user@example.com>|0|
|<juan.perez@example.com>|100|
|<maria.gonzalez@example.com>|100|


select \*

FROM 

usuarios t1

JOIN

notas t2 

ON

t1.email = t2.email;




### Seleccionando algunos atributos
#### **Ideas clave**
- La cláusula JOIN nos permite combinar los datos de varias tablas en una única tabla de resultados.
- Para hacer la unión, debemos especificar las tablas que queremos unir y la condición de unión.
- Podemos seleccionar los datos de cada tabla que deseamos mostrar en la consulta.
#### **Seleccionando algunos atributos**
Al igual que cuando trabajamos con una sola tabla, podemos seleccionar sólo los atributos que deseamos mostrar en la consulta. Cuando tenemos dos tablas, podemos seleccionar todos los atributos de una tabla y sólo algunos de la otra de la siguiente forma:

SELECT tabla1.\*, 

`    `tabla2.atributo1, 

`    `tabla2.atributo2

FROM tabla1

JOIN tabla2 ON tabla1.id = tabla2.id;

Si tenemos dos tablas como en los ejercicios anteriores:

Tabla **usuarios**

|**EMAIL**|**NOMBRE**|**EDAD**|
| :- | :- | :- |
|<juan.perez@example.com>|Juan Pérez|30|
|<maria.gonzalez@example.com>|Maria González|25|
|<john.doe@example.com>|John Doe|40|
|<test.user@example.com>|Test User|22|

Tabla **datos\_contacto**

|**EMAIL**|**TELÉFONO**|
| :- | :- |
|<juan.perez@example.com>|555-123-4567|
|<maria.gonzalez@example.com>|444-987-6543|
|<john.doe@example.com>|777-555-8888|
|<test.user@example.com>|111-222-3333|
|<juan.perez@example.com>|999-888-7777|
|<maria.gonzalez@example.com>|333-111-0000|


SELECT usuarios.\*, datos\_contacto.telefono 

FROM usuarios 

JOIN datos\_contacto 

ON usuarios.email = datos\_contacto.email

De esta forma, seleccionamos todo de la tabla **usuarios** y sólo los teléfonos de la tabla **datos\_contacto**.
## Ejercicio
Dadas las siguientes tablas:

Tabla **usuarios**:

|**EMAIL**|**NOMBRE**|**EDAD**|
| :- | :- | :- |
|<juan.perez@example.com>|Juan Pérez|30|
|<maria.gonzalez@example.com>|Maria González|25|
|<john.doe@example.com>|John Doe|40|
|<test.user@example.com>|Test User|22|

Tabla **notas**:

|**EMAIL**|**NOTAS**|
| :- | :- |
|<juan.perez@example.com>|90|
|<maria.gonzalez@example.com>|100|
|<john.doe@example.com>|80|
|<test.user@example.com>|0|
|<juan.perez@example.com>|100|
|<maria.gonzalez@example.com>|100|

Selecciona de la tabla **usuarios** el email, nombre y edad, y de la tabla **notas** sólo las notas. Une los registros de ambas tablas utilizando el email.

SELECT 

`    `usuarios.email, 

`    `usuarios.nombre, 

`    `usuarios.edad, 

`    `notas.notas 

FROM 

`    `usuarios 

JOIN 

`    `notas 

ON 

`    `usuarios.email = notas.email;


SELECT 

usuarios.email, 

usuarios.nombre, 

usuarios.edad, 

notas.notas 

FROM 

usuarios 

JOIN 

notas 

ON 

usuarios.email = notas.email;



### **Join **n sin resultados**
#### **Ideas clave**
- La cláusula JOIN nos permite combinar los datos de varias tablas en una única tabla de resultados.
- Para hacer la unión, debemos especificar las tablas que queremos unir y la condición de unión.
- La cláusula JOIN solo une los registros que tienen una clave común en ambas tablas. Existen otros tipos de JOIN que revisaremos más adelante.

¿Qué sucedería si los emails presentes en una tabla no se encuentran en la otra tabla al momento de unir los datos?

Tabla **usuarios**

|**EMAIL**|**NOMBRE**|**EDAD**|
| :- | :- | :- |
|<juan.perez@example.com>|Juan Pérez|30|
|<maria.gonzalez@example.com>|Maria González|25|
|<john.doe@example.com>|John Doe|40|
|<test.user@example.com>|Test User|22|

Tabla **datos\_contacto**

|**EMAIL**|**TELÉFONO**|
| :- | :- |
|<alvaro.sanchez@example.com>|555-123-4567|
|<maria.fernandez@example.com>|444-987-6543|
|<francisca.medina@example.com>|777-555-8888|

La respuesta es bien sencilla: si no hay ningún dato común entre ambas tablas, no obtendremos resultados.

Utilizando lo aprendido previamente, selecciona todos los registros de la unión de las tablas **usuarios** y **datos\_contacto**. Observa el resultado.

SELECT 

`    `usuarios.\*, 

`    `datos\_contacto.telefono 

FROM 

`    `usuarios 

JOIN 

`    `datos\_contacto 

ON 

`    `usuarios.email = datos\_contacto.email;

Al ejecutar esta consulta, no obtendremos ningún resultado ya que no hay emails comunes entre las tablas **usuarios** y **datos\_contacto**.

Para confirmar, si ejecutamos la consulta anterior, el resultado sería una tabla vacía, ya que ninguna de las direcciones de correo electrónico en **usuarios** coincide con las direcciones de correo electrónico en **datos\_contacto**.\*\*. Observa el resultado.

SELECT 

usuarios.\*, 

datos\_contacto.telefono 

FROM 

usuarios 

JOIN 

datos\_contacto 

ON 

usuarios.email = datos\_contacto.email;



### Orden de cláusulas
#### **Ideas clave**
- La cláusula JOIN nos permite combinar los datos de varias tablas en una única tabla de resultados.
- Para hacer la unión, debemos especificar las tablas que queremos unir y la condición de unión.
- Las cláusulas tienen un orden específico que debemos seguir para que la consulta funcione correctamente.
#### **Orden de cláusulas**

|**COMANDO**|**SE LEE COMO:**|
| :- | :- |
|SELECT|Selecciona estos datos.|
|FROM|De esta tabla.|
|JOIN|Únelos con esta tabla.|
|WHERE|Filtra los valores que cumplan tal condición.|
|GROUP BY|Agrupa los resultados por este criterio.|
|HAVING|Filtra por estos criterios agrupados.|
|ORDER BY|Ordena los resultados por este otro criterio.|
|LIMIT|Limita los resultados a esta cantidad.|

En el siguiente ejercicio nos enfocaremos en combinar la cláusula JOIN con la cláusula WHERE.
#### **Ejercicio**
Dadas las siguientes tablas, selecciona toda la información del usuario juan.perez@example.com.

Tabla **usuarios**

|**EMAIL**|**NOMBRE**|**EDAD**|
| :- | :- | :- |
|<juan.perez@example.com>|Juan Pérez|30|
|<maria.gonzalez@example.com>|Maria González|25|
|<john.doe@example.com>|John Doe|40|
|<test.user@example.com>|Test User|22|

Tabla **notas**

|**EMAIL**|**NOTAS**|
| :- | :- |
|<juan.perez@example.com>|90|
|<maria.gonzalez@example.com>|100|
|<john.doe@example.com>|80|
|<test.user@example.com>|0|
|<juan.perez@example.com>|100|
|<maria.gonzalez@example.com>|100|

Pista: debes seleccionar todo, unir las tablas y filtrar por el email respectivo.

select t1.email as email ,t1.nombre,t1.edad, t2.email as email ,t2.notas 

from usuarios t1

join notas t2

on

t1.email= t2.email where t1.email='juan.perez@example.com'



### Agrupar por múltiples columnas
#### **Ideas clave**
- La cláusula JOIN nos permite combinar los datos de varias tablas en una única tabla de resultados.
- Para hacer la unión, debemos especificar las tablas que queremos unir y la condición de unión.
- Las cláusulas tienen un orden específico que debemos seguir para que la consulta funcione correctamente.
#### **Orden de cláusulas**

|**COMANDO**|**SE LEE COMO:**|
| :- | :- |
|SELECT|Selecciona estos datos.|
|FROM|De esta tabla.|
|JOIN|Únelos con esta tabla.|
|WHERE|Filtra los valores que cumplan tal condición.|
|GROUP BY|Agrupa los resultados por este criterio.|
|HAVING|Filtra por estos criterios agrupados.|
|ORDER BY|Ordena los resultados por este otro criterio.|
|LIMIT|Limita los resultados a esta cantidad.|

En este ejercicio, nos enfocaremos en combinar la cláusula JOIN con la cláusula GROUP BY.
#### **Utilizando GROUP BY y funciones de agregación en consultas con múltiples tablas**
Al igual que en las consultas sobre una tabla, podemos utilizar funciones de agregación y agrupado en consultas sobre múltiples tablas.

Supongamos que tenemos dos tablas: una tabla llamada **clientes** y otra tabla llamada **pedidos**. Aquí están las estructuras y algunos datos de ejemplo para cada tabla.

Tabla **clientes**:

|**CLIENTE\_ID**|**NOMBRE**|
| :- | :- |
|1|Juan Pérez|
|2|Ana Gómez|
|3|Luis Fernández|

Tabla **pedidos**:

|**PEDIDO\_ID**|**CLIENTE\_ID**|**FECHA**|
| :- | :- | :- |
|101|1|2023-01-15|
|102|2|2023-02-20|
|103|1|2023-03-10|
|104|3|2023-04-22|
|105|2|2023-05-18|
|106|1|2023-06-30|

Para mostrar la cantidad total de pedidos realizados por cada cliente, podemos usar la siguiente consulta SQL:

SELECT nombre, COUNT(p.pedido\_id) AS total\_pedidos

FROM clientes c

JOIN pedidos p ON c.cliente\_id = p.cliente\_id

GROUP BY c.cliente\_id, nombre;

Con esto obtenemos el siguiente resultado:

|**NOMBRE\_CLIENTE**|**TOTAL\_PEDIDOS**|
| :- | :- |
|Juan Pérez|3|
|Ana Gómez|2|
|Luis Fernández|1|

Algunos detalles importantes a tener en cuenta:

- Si hay columnas con el mismo nombre entonces tenemos que especificar el nombre de la tabla antes del nombre de la columna.
- A la hora de agrupar datos debemos tener en cuenta que las columnas que no están en la cláusula GROUP BY deben ser utilizadas con funciones de agregación. Por lo mismo, en este tipo de ejercicios, el SELECT \* no es recomendable, especialmente si la tabla tiene muchas columnas.
#### **Ejercicio**
Tenemos dos tablas: **Productos** y **Ventas**. Realiza una consulta que nos muestre el producto más vendido y la cantidad total de unidades vendidas de ese producto. La columna que muestre el total de unidades vendidas debe llamarse "total\_vendido"

Pista: Recuerda el uso de order by y limit

Tabla Productos

|**NOMBRE**|**PRECIO**|**PRODUCTOID**|
| :- | :- | :- |
|Producto A|10|1|
|Producto B|15|2|
|Producto C|20|3|

Tabla Ventas

|**CANTIDAD**|**FECHAVENTA**|**PRODUCTOID**|
| :- | :- | :- |
|20|'2023-09-01'|1|
|15|'2023-09-02'|1|
|10|'2023-09-03'|2|
|25|'2023-09-04'|3|
|30|'2023-09-05'|3|


select t1.nombre, sum(t2.cantidad) as total\_vendido from productos t1

join

ventas t2

on t1.productoid = t2.productoid

group by t1.productoid

order by cantidad desc

limit 1 





### Relaciones 1 a 1
#### **Ideas clave**
- La cardinalidad de una relación es la cantidad de elementos de una tabla que pueden estar relacionados con los de otra tabla.
- Dependiendo de como se modelen las relaciones entre tablas, se pueden tener relaciones de uno a uno, uno a muchos o muchos a muchos.
- En una relación uno a uno, un registro de una tabla solo puede estar relacionado con un registro de la otra tabla.
#### **¿Qué es la cardinalidad de una relación?**
La cardinalidad de una relación es la cantidad de elementos de una tabla que pueden estar relacionados con los de otra tabla.

Las relaciones entre tablas se pueden clasificar en tres tipos principales según su cardinalidad.

En este ejercicio veremos la relación uno a uno, denotada como 1:1. En esta relación, cada registro de una tabla está relacionado con un único registro de otra tabla. Por ejemplo, cada persona puede tener un único pasaporte y cada pasaporte pertenece a una única persona.

tabla **personas**

|**ID**|**NOMBRE**|
| :- | :- |
|1|Juan|
|2|María|
|3|Carlos|

tabla **pasaportes**

|**ID**|**PERSONA\_ID**|
| :- | :- |
|1|1|
|2|2|
|3|3|

Al hacer un JOIN entre las tablas Personas y Pasaportes, obtendríamos:

|**ID**|**NOMBRE**|**ID**|**PERSONA\_ID**|
| :- | :- | :- | :- |
|1|Juan|1|1|
|2|María|2|2|
|3|Carlos|3|3|

O sea, por cada registro de la tabla Personas hay un único registro en la tabla Pasaportes y viceversa.
#### **Ejercicio**
Dada las siguientes tablas:

tabla **Vehículos**

|**ID**|**MODELO**|
| :- | :- |
|1|Toyota Corolla|
|2|Honda Civic|
|3|Ford Focus|

tabla: **Matrículas**

|**ID**|**VEHICULO\_ID**|**MATRICULA**|
| :- | :- | :- |
|1|1|ABC-123|
|2|2|XYZ-456|
|3|3|DEF-789|

Se pide crear una consulta que muestre toda la información de las matrículas de los vehículos junto a su matrícula correspondiente.

select t1.id, t1.modelo, t2.id,t2.vehiculo\_id, t2.matricula from Vehiculos t1

join

matriculas t2

on t1.id=t2.vehiculo\_id



### **Relaciones 1 a n**
#### **Ideas clave**
- La cardinalidad de una relación es la cantidad de elementos de una tabla que pueden estar relacionados con los de otra tabla.
- Dependiendo de como se modelen las relaciones entre tablas, se pueden tener relaciones de *uno a uno*, *uno a muchos* o *muchos a muchos*.
- En una relación uno a uno, un registro de una tabla solo puede estar relacionado con un registro de la otra tabla.
- En una relación uno a muchos, un registro de una tabla puede estar relacionado con uno o varios registros de otra tabla.
#### **Relaciones 1 a N**
En esta tipo de relación, un registro de una tabla puede estar relacionado con uno o varios registros de otra tabla. Por ejemplo, podriamos tener una tabla de empleados y otra de departamentos. Cada empleado pertenece a un único departamento, pero un departamento puede tener varios empleados.

tabla **departamentos**

|**ID**|**NOMBRE**|
| :- | :- |
|1|Recursos Humanos|
|2|TI|
|3|Marketing|

tabla **empleados**

|**ID**|**NOMBRE**|**DEPARTAMENTO\_ID**|
| :- | :- | :- |
|1|Ana|1|
|2|Pedro|2|
|3|Luis|2|
|4|Marta|3|
|5|Elena|1|

Al hacer un JOIN entre las tablas Empleados y Departamentos, obtendríamos:

|**ID**|**NOMBRE**|**ID**|**NOMBRE**|
| :- | :- | :- | :- |
|1|Ana|1|Recursos Humanos|
|2|Pedro|2|TI|
|3|Luis|2|TI|
|4|Marta|3|Marketing|
|5|Elena|1|Recursos Humanos|

Podemos ver que por cada registro de la tabla Empleados hay un único registro en la tabla Departamentos, pero un registro de la tabla Departamentos puede estar relacionado con varios registros de la tabla Empleados.
#### **Ejercicio**
Dada las siguientes tablas:

Tabla **continentes**

|**CONTINENTE\_ID**|**NOMBRE**|
| :- | :- |
|1|África|
|2|América|
|3|Asia|
|4|Europa|
|5|Oceanía|

Tabla **paises**

|**PAIS\_ID**|**NOMBRE**|**CONTINENTE\_ID**|
| :- | :- | :- |
|1|Nigeria|1|
|2|Brasil|2|
|3|China|3|
|4|Alemania|4|
|5|Australia|5|
|6|Argentina|2|
|7|Japón|3|
|8|Francia|4|
|9|Egipto|1|
|10|Nueva Zelanda|5|

Se pide crear una consulta que muestre toda la información de los países junto a su continente correspondiente. Observa dentro de los resultados que un país pertenece a un único continente, pero un continente puede tener varios países.


### Relaciones 1 a n
#### **Ideas clave**
- La cardinalidad de una relación es la cantidad de elementos de una tabla que pueden estar relacionados con los de otra tabla.
- Dependiendo de como se modelen las relaciones entre tablas, se pueden tener relaciones de uno a uno, uno a muchos o muchos a muchos.
- En una relación uno a uno, un registro de una tabla solo puede estar relacionado con un registro de la otra tabla.
- En una relación uno a muchos, un registro de una tabla puede estar relacionado con uno o varios registros de otra tabla.
#### **Relaciones 1 a N**
En esta tipo de relación, un registro de una tabla puede estar relacionado con uno o varios registros de otra tabla. Por ejemplo, podriamos tener una tabla de empleados y otra de departamentos. Cada empleado pertenece a un único departamento, pero un departamento puede tener varios empleados.

tabla **departamentos**

|**ID**|**NOMBRE**|
| :- | :- |
|1|Recursos Humanos|
|2|TI|
|3|Marketing|

tabla **empleados**

|**ID**|**NOMBRE**|**DEPARTAMENTO\_ID**|
| :- | :- | :- |
|1|Ana|1|
|2|Pedro|2|
|3|Luis|2|
|4|Marta|3|
|5|Elena|1|

Al hacer un JOIN entre las tablas Empleados y Departamentos, obtendríamos:

|**ID**|**NOMBRE**|**ID**|**NOMBRE**|
| :- | :- | :- | :- |
|1|Ana|1|Recursos Humanos|
|2|Pedro|2|TI|
|3|Luis|2|TI|
|4|Marta|3|Marketing|
|5|Elena|1|Recursos Humanos|

Podemos ver que por cada registro de la tabla Empleados hay un único registro en la tabla Departamentos, pero un registro de la tabla Departamentos puede estar relacionado con varios registros de la tabla Empleados.
#### **Ejercicio**
Dada las siguientes tablas:

Tabla **continentes**

|**CONTINENTE\_ID**|**NOMBRE**|
| :- | :- |
|1|África|
|2|América|
|3|Asia|
|4|Europa|
|5|Oceanía|

Tabla **paises**

|**PAIS\_ID**|**NOMBRE**|**CONTINENTE\_ID**|
| :- | :- | :- |
|1|Nigeria|1|
|2|Brasil|2|
|3|China|3|
|4|Alemania|4|
|5|Australia|5|
|6|Argentina|2|
|7|Japón|3|
|8|Francia|4|
|9|Egipto|1|
|10|Nueva Zelanda|5|

Se pide crear una consulta que muestre toda la información de los países junto a su continente correspondiente. Observa dentro de los resultados que un país pertenece a un único continente, pero un continente puede tener varios países.

SELECT t2.pais\_id, t2.nombre, t2.continente\_id, t1.continente\_id, t1.nombre

from continentes t1

inner join paises t2 on t1.CONTINENTE\_ID= t2.CONTINENTE\_ID



### Relaciones n a n
#### **Ideas clave**
- La cardinalidad de una relación es la cantidad de elementos de una tabla que pueden estar relacionados con los de otra tabla.
- Dependiendo de como se modelen las relaciones entre tablas, se pueden tener relaciones de uno a uno, uno a muchos o muchos a muchos.
- En una relación uno a uno, un registro de una tabla solo puede estar relacionado con un registro de la otra tabla.
- En una relación uno a muchos, un registro de una tabla puede estar relacionado con uno o varios registros de otra tabla.
- En una relación muchos a muchos, un registro de una tabla puede estar relacionado con uno o varios registros de otra tabla, y viceversa.
#### **Relaciones N a N**
En bases de datos relaciones, con dos tablas solo podemos lograr relaciones de uno a uno o uno a muchos. Para lograr relaciones muchos a muchos, se necesita una tabla intermedia con ciertas características que estudiaremos más adelante.
#### **Ejercicio resuelto**
Se tiene un sistema que guarda información de profesores y alumnos. Cada profesor puede tener varios alumnos y cada alumno puede tener varios profesores. Para lograr esto se tiene una tabla profesores, una tabla alumnos y una tabla profesores\_alumnos que relaciona a los profesores con los alumnos.

Tabla **profesores**

|**PROFESOR\_ID**|**NOMBRE**|
| :- | :- |
|1|Ana|
|2|Pedro|
|3|Luis|

Tabla **alumnos**

|**ALUMNO\_ID**|**NOMBRE**|
| :- | :- |
|1|Marta|
|2|Elena|
|3|Juan|

Tabla **profesores\_alumnos**

|**PROFESOR\_ID**|**ALUMNO\_ID**|
| :- | :- |
|1|1|
|1|2|
|2|1|

Al unir las tablas profesores y profesores\_alumnos con un JOIN, obtendríamos:

|**PROFESOR\_ID**|**NOMBRE**|**ALUMNO\_ID**|
| :- | :- | :- |
|1|Ana|1|
|1|Ana|2|
|2|Pedro|1|

Al unir las tabla anterior con la tabla alumnos, obtendríamos:

|**PROFESOR\_ID**|**NOMBRE**|**ALUMNO\_ID**|**NOMBRE**|
| :- | :- | :- | :- |
|1|Ana|1|Marta|
|1|Ana|2|Elena|
|2|Pedro|1|Marta|

Donde podemos ver que por cada registro de la tabla profesores hay uno o varios registros en la tabla profesores\_alumnos, y por cada registro de la tabla profesores\_alumnos hay un registro en la tabla alumnos.

Para hacer el join entre más de 2 tablas, se puede hacer un join por cada tabla que se quiera unir.

SELECT \*

FROM profesores

JOIN profesores\_alumnos

ON profesores.profesor\_id = profesores\_alumnos.profesor\_id

JOIN alumnos

ON profesores\_alumnos.alumno\_id = alumnos.alumno\_id;
#### **Ejercicio**
Se tiene una base de datos con un catálogo de objetos y colores. Cada objeto puede tener varios colores y cada color puede estar asociado a varios objetos.

Tabla **objetos**

|**OBJETO\_ID**|**OBJETO**|
| :- | :- |
|1|Mesa|
|2|Silla|
|3|Cama|

Tabla **colores**

|**COLOR\_ID**|**COLOR**|
| :- | :- |
|1|Rojo|
|2|Azul|
|3|Verde|

Tabla **objetos\_colores**

|**OBJETOS\_COLORES\_ID**|**OBJETO\_ID**|**COLOR\_ID**|
| :- | :- | :- |
|1|1|1|
|2|1|2|
|3|2|1|
|4|3|3|

Se pide hacer una consulta que muestre los objetos y sus colores correspondientes.

SELECT T1.OBJETO\_ID, T1.OBJETO, 

T2.OBJETOS\_COLORES\_ID, T2.OBJETO\_ID, T2.COLOR\_ID, 

T3.COLOR\_ID, T3.COLOR 

FROM objetos T1 

JOIN objetos\_colores T2

ON T1.objeto\_id = T2.objeto\_id 

JOIN colores T3 ON T2.color\_id = T3.color\_id; 



### Características de la tabla intermedia
#### **Ideas clave**
- En una relación muchos a muchos, un registro de una tabla puede estar relacionado con uno o varios registros de otra tabla, y viceversa.
- Las bases de datos relacionales no permiten relaciones muchos a muchos directamente, por lo que se necesita una tabla intermedia que relacione a las tablas principales.
- La tabla intermedia debe tener una columna que sea clave foránea de cada una de las tablas principales.
#### **Entendiendo la tabla intermedia**
Si tenemos dos tablas A y B que queremos relacionar de manera muchos a muchos, necesitamos una tabla intermedia C que relacione a ambas tablas.

Intentemos hacerlo con un ejemplo. Supongamos que tenemos una tabla profesores y una tabla alumnos. Cada profesor puede tener varios alumnos y cada alumno puede tener varios profesores. Si agregamos la clave foránea en la tabla de profesores, tendríamos algo como esto:

Tabla **profesores**

|**PROFESOR\_ID**|**NOMBRE**|**ALUMNO\_ID**|
| :- | :- | :- |
|1|Ana|1|
|2|Pedro|1|
|3|Luis|2|

Tabla **alumnos**

|**ALUMNO\_ID**|**NOMBRE**|
| :- | :- |
|1|Marta|
|2|Elena|
|3|Juan|

Al hacer un JOIN entre las tablas profesores y alumnos, obtendríamos:

|**PROFESOR\_ID**|**NOMBRE**|**ALUMNO\_ID**|**NOMBRE**|
| :- | :- | :- | :- |
|1|Ana|1|Marta|
|2|Pedro|1|Marta|
|3|Luis|2|Elena|

O sea que por cada profesor hay uno o varios alumnos pero por cada alumno hay un solo profesor. Esto no es lo que queremos, ya que un alumno puede tener varios profesores.

Si agregamos la clave foránea en la tabla de alumnos, tendríamos algo como esto:

Tabla **profesores**

|**PROFESOR\_ID**|**NOMBRE**|
| :- | :- |
|1|Ana|
|2|Pedro|
|3|Luis|

Tabla **alumnos**

|**ALUMNO\_ID**|**NOMBRE**|**PROFESOR\_ID**|
| :- | :- | :- |
|1|Marta|1|
|2|Elena|1|
|3|Juan|2|

Al hacer un JOIN entre las tablas alumnos y profesores, obtendríamos:

|**ALUMNO\_ID**|**NOMBRE**|**PROFESOR\_ID**|**NOMBRE**|
| :- | :- | :- | :- |
|1|Marta|1|Ana|
|2|Elena|1|Ana|
|3|Juan|2|Pedro|

O sea que por cada alumno hay uno o varios profesores pero por cada profesor hay un solo alumno. Esto tampoco es lo que queremos.

Para lograr una relación muchos a muchos, necesitamos una tabla intermedia que relacione a las tablas profesores y alumnos. Esta tabla intermedia tiene que tener una columna que sea clave foránea de cada una de las tablas principales para poder servir de puente entre ellas.

Tabla **profesores\_alumnos**

|**PROFESOR\_ID**|**ALUMNO\_ID**|
| :- | :- |
|1|1|
|1|2|
|2|1|

Por cada entrada en la tabla profesores\_alumnos, tenemos una relación entre un profesor y un alumno. Si queremos saber qué profesores tienen un alumno, o qué alumnos tienen un profesor, podemos hacer un JOIN entre las tablas profesores\_alumnos y profesores o alumnos, respectivamente.
#### **Ejercicio**
Se tiene un sistema que guarda información de profesores y alumnos. Cada profesor puede tener varios alumnos y cada alumno puede tener varios profesores. Para lograr esto se tiene una tabla profesores, una tabla alumnos y una tabla profesores\_alumnos que relaciona a los profesores con los alumnos.

Tabla **profesores**

|**PROFESOR\_ID**|**NOMBRE**|
| :- | :- |
|1|Julia|
|2|Pedro|
|3|Luis|

Tabla **alumnos**

|**ALUMNO\_ID**|**NOMBRE**|
| :- | :- |
|1|Marta|
|2|Elena|
|3|Juan|

Tabla **profesores\_alumnos**

|**PROFESOR\_ID**|**ALUMNO\_ID**|
| :- | :- |
|1|1|

Se pide agregar registros a la tabla profesores\_alumnos para que Julia tenga a Elena como alumna y Pedro tenga a Juan como alumno. Luego mostrar los profesores con sus respectivos alumnos.

Ingresa los datos en el mismo orden pedido

insert into profesores\_alumnos (PROFESOR\_ID, ALUMNO\_ID) values (1,2);

insert into profesores\_alumnos (PROFESOR\_ID, ALUMNO\_ID) values (2,3);

select T1.PROFESOR\_ID, T1.NOMBRE,

T2.PROFESOR\_ID, T2.ALUMNO\_ID,

T3.ALUMNO\_ID, T3.NOMBRE

from

profesores T1

inner join profesores\_alumnos T2 on T1.PROFESOR\_ID=T2.PROFESOR\_ID

inner JOIN ALUMNOS T3 ON T2.ALUMNO\_ID = T3.ALUMNO\_ID

### **Sin**
### ` `**restricción de unicidad**
#### **Ideas clave**
- La tabla intermedia debe tener una columna que sea clave foránea de cada una de las tablas principales.
- Si hay una restricción de unicidad, se garantiza que no haya registros duplicados en la tabla intermedia. Esto se logra con una clave primaria compuesta de las claves foráneas de las tablas principales.
#### **Restricción de unicidad**
Supongamos que tenemos un sistema de gestión para una biblioteca que incluye tres tablas principales: Libros, Usuarios y Pedidos. La tabla Pedidos actúa como una tabla intermedia para manejar la relación de muchos a muchos entre Libros y Usuarios. En este sistema, un libro puede ser solicitado por múltiples usuarios, y cada usuario puede solicitar varios libros.

LIBROSintidPKstringtitulostringautorUSUARIOSintidPKstringnombrestringemailN to N

Antes de construir la tabla intermedia tenemos que hacernos una pregunta importante: ¿un usuario puede pedir el mismo libro más de una vez?

- Si la respuesta es sí, entonces **no** necesitamos una restricción de unicidad en la tabla intermedia.
- Si la respuesta es no, entonces debemos asegurarnos de que no haya registros duplicados en la tabla intermedia y esto se hace con una restricción de unicidad.

En este ejemplo tiene sentido que un usuario pueda pedir el mismo libro más de una vez, por lo que nuestra tabla intermedia tendría la siguiente estructura:

|**LIBRO\_ID**|**USUARIO\_ID**|
| :- | :- |
|1|1|
|1|1|
|2|2|
|2|2|
|3|1|

Dentro de la tabla podemos ver que el usuario 1 ha pedido el libro 1 dos veces, lo cual no es un problema si no hay una restricción de unicidad.
#### **Ejercicio**
Dada las siguientes tablas:

Tabla **libros**

|**LIBRO\_ID**|**TITULO**|
| :- | :- |
|1|El Quijote|
|2|Don Juan|
|3|Rayuela|

Tabla **usuarios**

|**USUARIO\_ID**|**NOMBRE**|
| :- | :- |
|1|Ana|
|2|Pedro|
|3|Luis|

Tabla **pedidos**

|**LIBRO\_ID**|**USUARIO\_ID**|
| :- | :- |
|1|1|
|1|1|
|2|2|
|2|2|
|3|1|

Selecciona a todos los usuarios que han pedido el mismo libro más de una vez. Las columnas a mostrar son usuario\_id, libro\_id y veces donde veceses el número de veces que el usuario ha pedido el libro.

Pista: Agrupa por libro\_id y usuario\_id y cuenta cuantos registros hay por cada grupo. Reflexiona si debes ocupar where o having para filtrar los resultados.



SELECT T3.USUARIO\_ID,T1.LIBRO\_ID, COUNT(\*) AS VECES

FROM libros T1

INNER JOIN pedidos T2 on T1.LIBRO\_ID=T2.LIBRO\_ID

INNER JOIN USUARIOS T3 on T2.USUARIO\_ID=T3.USUARIO\_ID

GROUP BY T1.libro\_id, T3.usuario\_id 

HAVING VECES > 1



### **Conrestricción de unicidad**
#### **Ideas clave**
- La tabla intermedia debe tener una columna que sea clave foránea de cada una de las tablas principales.
- Si hay una restricción de unicidad, se garantiza que no haya registros duplicados en la tabla intermedia. Esto se logra con una clave primaria compuesta de las claves foráneas de las tablas principales.
#### **Restricción de unicidad**
Supongamos que tenemos un sistema que guarda información de proyectos y empleados. Cada empleado puede trabajar en varios proyectos y cada proyecto puede tener varios empleados trabajando en él. Para manejar esto, tenemos una tabla empleados, una tabla proyectos y una tabla empleados\_proyectos que relaciona a los empleados con los proyectos.

EMPLEADOSintidPKstringnombrestringpuestoPROYECTOSintidPKstringnombrestringdepartamentoN to N

Antes de construir la tabla intermedia tenemos que hacernos una pregunta importante: ¿un empleado puede estar en el mismo proeycto más de una vez?

- Si la respuesta es sí, entonces **no** necesitamos una restricción de unicidad en la tabla intermedia.
- Si la respuesta es no, entonces debemos asegurarnos de que no haya registros duplicados en la tabla intermedia y esto se hace con una restricción de unicidad.

En este caso, un empleado no puede estar asignado al mismo proyecto más de una vez. Para evitar que esto suceda, al crear la tabla agregaremos una clave primaria compuesta de las claves foráneas de las tablas principales.

CREATE TABLE Empleados\_Proyectos (

empleado\_id INT,

proyecto\_id INT,

PRIMARY KEY (empleado\_id, proyecto\_id),

FOREIGN KEY (empleado\_id) REFERENCES Empleados(id),

FOREIGN KEY (proyecto\_id) REFERENCES Proyectos(id)

);

De esta manera, si se intenta agregar un registro con un empleado y un proyecto que ya existen en la tabla, se generará un error, lo que asegura que no haya registros duplicados en la tabla intermedia.
#### **Ejercicio**
Dada las siguientes tablas:

**Tabla Empleados**

|**ID**|**NOMBRE**|**PUESTO**|
| :- | :- | :- |
|1|Juan Pérez|Desarrollador|
|2|María García|Analista|
|3|Carlos López|Gerente|

**Tabla Proyectos**

|**ID**|**NOMBRE**|**DEPARTAMENTO**|
| :- | :- | :- |
|1|Sistema de Gestión|TI|
|2|Desarrollo Web|TI|
|3|Análisis de Datos|Data Science|

**Tabla Empleados\_Proyectos**

|**EMPLEADO\_ID**|**PROYECTO\_ID**|
| :- | :- |
|1|1|
|1|2|
|2|1|
|2|3|
|3|1|
|3|2|
|3|3|

Crea una consulta que seleccione todos los empleados junto con la cantidad de proyectos asignados a cada uno, demostrando que no hay registros duplicados en la tabla intermedia. Las columnas de la consulta deben ser nombre, puesto y cantidad\_proyectos.

SELECT T1.nombre, T1.puesto, COUNT(T2.proyecto\_id) AS cantidad\_proyectos 

FROM empleados AS T1 

INNER JOIN empleados\_proyectos AS T2 ON T1.id = T2.empleado\_id 

INNER JOIN proyectos AS T3 ON T2.proyecto\_id = T3.id 

GROUP BY T1.nombre, T1.puesto;








### Seleccionando caracteres de un string con SUBSTR
La función SUBSTR() se utiliza para seleccionar una determinada cantidad de caracteres de un string:

SUBSTR( string, inicio, largo )

En la sintaxis podemos observar que la función tiene 3 argumentos. 1. String: el nombre de la columna o palabra que será utilizada 2. Inicio: un integer que especifica la posicion de inicio desde la cual se extraerán caracteres al string. 3. Largo: la cantidad de caracteres extraidos

Por ejemplo, si tenemos una tabla de productos con el campo 'nombre' y queremos seleccionar sólo la primera letra de cada nombre, podemos utilizar la siguiente consulta:

SELECT SUBSTR(nombre, 1, 1) AS primera\_letra FROM productos;

En este ejemplo estamos indicando que en la columna nombre, partiendo desde su primera letra, nos devuelva sólo 1 caracter que corresponderá a la primera letra de cada nombre.

Es importante recordar que algunas funciones tienen distintos nombres dependiendo del motor de base de datos. Por ejemplo, para lograr este mismo objetivo en PostgreSQL, deberíamos usar la función LEFT()
## **Ejercicio**
Se tiene una **tabla usuarios** con las columnas id, nombre, apellido, email y teléfono. Utiliza la función SUBSTR para seleccionar las tres primeras letras del apellido de cada usuario en la tabla 'usuarios'. Asigna el nombre 'primeras\_letras' a la columna creada.

select substr(apellido, 1,3) as primeras\_letras from usuarios


### el
### eccionando caracteres
Se tiene una **tabla** de **usuarios** con las columnas nombre y apellido. Utilizando la función SUBSTR(), selecciona 3 caracteres del apellido de María, partiendo desde el segundo caracter. Asigna el alias 'tres\_caracteres\_del\_apellido' a la columna creada.


select substr(apellido,2 ,3) as tres\_caracteres\_del\_apellido from usuarios where nombre ='María'

### Inner Join
#### **Ideas clave**
- La cláusula JOIN nos permite combinar los datos de varias tablas en una única tabla de resultados.
- Existen varios tipos de joins, cuando no se especifica el tipo de join se utiliza INNER JOIN.
- La diferencia entre los tipos de joins radica en cómo se manejan los registros que no tienen una clave común en ambas tablas.
#### **INNER JOIN es la opción por defecto**
Hasta el momento hemos utilizado INNER JOIN, pero no lo hemos especificado. Si no se especifica el tipo de JOIN, por defecto se utiliza INNER JOIN. Esto implica que:

SELECT \* FROM usuarios JOIN datos\_contacto ON usuarios.email = datos\_contacto.email

Es lo mismo que:

SELECT \* FROM usuarios INNER JOIN datos\_contacto ON usuarios.email = datos\_contacto.email
#### **¿Qué hace INNER JOIN?**
INNER JOIN combina los registros de ambas tablas en base a una condición de unión. **Solo se incluyen los registros que tienen una clave común en ambas tablas**. Si no hay una clave común, los registros no se incluyen en el resultado final.
## **Ejercicio**
Une las tablas utilizando JOIN (o INNER JOIN) para obtener todos los registros de ambas tablas. Mira las tablas antes de realizar el ejercicio y pon especial atención en Francisco, quien no tiene ninguna nota en el sistema.

**Tabla usuarios**

|**EMAIL**|**NOMBRE**|**EDAD**|
| :- | :- | :- |
|<juan.perez@example.com>|Juan Pérez|30|
|<maria.gonzalez@example.com>|Maria González|25|
|<john.doe@example.com>|John Doe|40|
|<francisco@example.com>|Test User|22|

**Tabla notas**

|**EMAIL**|**NOTAS**|
| :- | :- |
|<juan.perez@example.com>|90|
|<maria.gonzalez@example.com>|100|
|<john.doe@example.com>|80|
|<juan.perez@example.com>|100|
|<maria.gonzalez@example.com>|100|

Después de ejecutar la consulta, observa el resultado y utilizando únicamente lo aprendido en este ejercicio, explica por qué Francisco no aparece en el resultado.

SELECT t1.email, t1.nombre, t1.edad, t2.email, t2.notas from usuarios t1

inner join

notas t2 on t1.email=t2.email




### **Inner Join con diagrama de venn**
#### **Ideas clave**
- Los diagramas de Venn son una forma visual de representar conjuntos y operaciones entre ellos.
- Podemos utilizar los diagramas de Venn para visualizar lo que sucede con los registros de las tablas al realizar distintos tipos de JOIN.
- En el diagrama de Venn, un INNER JOIN se visualiza como la intersección entre dos círculos.
#### **Diagramas de Venn**
Un diagrama de Venn nos permite visualizar conjuntos y operaciones entre ellos. Estos diagramas se componen de círculos que representan conjuntos de datos. En ellos, los elementos que tienen en común los distintos conjuntos de datos se representan en la intersección de los círculos.

Cuando trabajamos con bases de datos, podemos utilizar estos diagramas para visualizar los registros que se obtendrían al realizar distintos tipos de JOIN. Especialmente, nos serán útiles para visualizar los resultados de una operación de join.

Para hacerlo, pondremos como elementos las claves de unión de las tablas. Los elementos que solo estén en la primera tabla los representaremos en un círculo, los elementos que solo estén en la segunda tabla los representaremos en otro círculo y los elementos que estén en ambas tablas los representaremos en la intersección de ambos círculos.

Por ejemplo, supongamos que tenemos dos tablas: productos y ventas.

**Tabla productos**

|**ID**|**NOMBRE**|**PRECIO**|
| :- | :- | :- |
|1|Producto 1|100|
|2|Producto 2|200|
|3|Producto 3|300|

\*\*Tabla ventas

|**ID**|**ID\_PRODUCTO**|**CANTIDAD**|
| :- | :- | :- |
|1|3|2|
|2|4|2|

Las claves en común entre ambas tablas son id en productos e id\_producto en ventas. Estos los pondremos en los círculos del diagrama de Venn.

Para armar este diagrama, primero identificamos la clave de unión de las tablas. Luego, en un círculo izquierdo que representa a la tabla productos ponemos los registros 1, 2 y 3 asociados a la clave id. En el círculo derecho que representa a la tabla ventas ponemos los registros 3 y 4 asociados a la clave id\_producto. En la intersección de ambos círculos ponemos el registro 3, ya que es el único que se encuentra en ambas tablas.

Mirando el diagrama y con lo que hemos aprendido, podemos decir que un INNER JOIN entre estas dos tablas nos devolvería el registro 3, ya que es el único que se encuentra en ambas tablas. Es decir, **un INNER JOIN nos muestra la intersección de ambos conjuntos**.
#### **Ejercicio**
Dados las siguientes tablas:

**Tabla actores**

|**ACTOR\_ID**|**NOMBRE**|
| :- | :- |
|1|Robert Downey Jr.|
|2|Scarlett Johansson|
|3|Chris Hemsworth|
|4|Mark Ruffalo|
|5|Chris Evans|

**Tabla peliculas**

|**PELICULA\_ID**|**TITULO**|**ACTOR\_ID**|
| :- | :- | :- |
|101|Iron Man|1|
|102|Avengers|1|
|103|Black Widow|2|
|104|Thor|3|
|105|Avengers|3|
|106|Avengers|4|
|107|Avengers|5|
|108|Captain America|5|

En un papel, dibuja un diagrama de Venn que muestre los registros que se obtendrían al realizar un INNER JOIN entre las tablas actores y peliculas.

En el editor de código a continuación, realiza una consulta que muestre el nombre de los actores y los títulos de las películas en las que han actuado.

¿El resultado del código coincide con tu dibujo?




### Inner Join con diagrama de venn
#### **Ideas clave**
- Los diagramas de Venn son una forma visual de representar conjuntos y operaciones entre ellos.
- Podemos utilizar los diagramas de Venn para visualizar lo que sucede con los registros de las tablas al realizar distintos tipos de JOIN.
- En el diagrama de Venn, un INNER JOIN se visualiza como la intersección entre dos círculos.
#### **Diagramas de Venn**
Un diagrama de Venn nos permite visualizar conjuntos y operaciones entre ellos. Estos diagramas se componen de círculos que representan conjuntos de datos. En ellos, los elementos que tienen en común los distintos conjuntos de datos se representan en la intersección de los círculos.

Cuando trabajamos con bases de datos, podemos utilizar estos diagramas para visualizar los registros que se obtendrían al realizar distintos tipos de JOIN. Especialmente, nos serán útiles para visualizar los resultados de una operación de join.

Para hacerlo, pondremos como elementos las claves de unión de las tablas. Los elementos que solo estén en la primera tabla los representaremos en un círculo, los elementos que solo estén en la segunda tabla los representaremos en otro círculo y los elementos que estén en ambas tablas los representaremos en la intersección de ambos círculos.

Por ejemplo, supongamos que tenemos dos tablas: productos y ventas.

**Tabla productos**

|**ID**|**NOMBRE**|**PRECIO**|
| :- | :- | :- |
|1|Producto 1|100|
|2|Producto 2|200|
|3|Producto 3|300|

\*\*Tabla ventas

|**ID**|**ID\_PRODUCTO**|**CANTIDAD**|
| :- | :- | :- |
|1|3|2|
|2|4|2|

Las claves en común entre ambas tablas son id en productos e id\_producto en ventas. Estos los pondremos en los círculos del diagrama de Venn.

Para armar este diagrama, primero identificamos la clave de unión de las tablas. Luego, en un círculo izquierdo que representa a la tabla productos ponemos los registros 1, 2 y 3 asociados a la clave id. En el círculo derecho que representa a la tabla ventas ponemos los registros 3 y 4 asociados a la clave id\_producto. En la intersección de ambos círculos ponemos el registro 3, ya que es el único que se encuentra en ambas tablas.

Mirando el diagrama y con lo que hemos aprendido, podemos decir que un INNER JOIN entre estas dos tablas nos devolvería el registro 3, ya que es el único que se encuentra en ambas tablas. Es decir, **un INNER JOIN nos muestra la intersección de ambos conjuntos**.
#### **Ejercicio**
Dados las siguientes tablas:

**Tabla actores**

|**ACTOR\_ID**|**NOMBRE**|
| :- | :- |
|1|Robert Downey Jr.|
|2|Scarlett Johansson|
|3|Chris Hemsworth|
|4|Mark Ruffalo|
|5|Chris Evans|

**Tabla peliculas**

|**PELICULA\_ID**|**TITULO**|**ACTOR\_ID**|
| :- | :- | :- |
|101|Iron Man|1|
|102|Avengers|1|
|103|Black Widow|2|
|104|Thor|3|
|105|Avengers|3|
|106|Avengers|4|
|107|Avengers|5|
|108|Captain America|5|

En un papel, dibuja un diagrama de Venn que muestre los registros que se obtendrían al realizar un INNER JOIN entre las tablas actores y peliculas.

En el editor de código a continuación, realiza una consulta que muestre el nombre de los actores y los títulos de las películas en las que han actuado.

¿El resultado del código coincide con tu dibujo?

select nombre, titulo

from actores t1

inner join peliculas t2 on t1.actor\_id =t2.actor\_id



### Left Join
#### **Ideas clave**
- La cláusula JOIN nos permite combinar los datos de varias tablas en una única tabla de resultados.
- Existen distintos tipos de JOIN. La diferencia entre los tipos de joins radica en cómo se manejan los registros que no tienen una clave común en ambas tablas.
- Al utilizar un INNER JOIN, si en una de las tablas no está la clave correspondiente, ese registro no aparecerá en el resultado final.
- Al utilizar un LEFT JOIN, si en la tabla izquierda está la clave pero en la tabla derecha no, el registro de la tabla izquierda aparecerá en el resultado final con valores NULL en los campos de la tabla derecha.
#### **Inner join V.S Left join**
Para ilustrar la diferencia trabajaremos con las tablas usuarios y notas.

+-----------------------------+          +-----------------------------+

|         usuarios            |          |           notas             |

+-----------------------------+          +-----------------------------+

| email                       |----------| email                       |

| nombre                      |          | notas                       |

| edad                        |          |                             |

+-----------------------------+          +-----------------------------+

Tabla usuarios

|**EMAIL**|**NOMBRE**|**EDAD**|
| :- | :- | :- |
|<juan.perez@example.com>|Juan Pérez|30|
|<maria.gonzalez@example.com>|Maria González|25|
|<john.doe@example.com>|John Doe|40|
|<francisco@example.com>|Test User|22|

Tabla notas

|**EMAIL**|**NOTAS**|
| :- | :- |
|<juan.perez@example.com>|90|
|<maria.gonzalez@example.com>|100|
|<john.doe@example.com>|80|
|<juan.perez@example.com>|100|
|<maria.gonzalez@example.com>|100|

Si hacemos un INNER JOIN entre las tablas usuarios y notas utilizando el campo email como clave, nos quedaremos con los siguientes registros:

SELECT u.email, u.nombre, u.edad, n.notas

FROM usuarios u

INNER JOIN notas n ON u.email = n.email;

|**EMAIL**|**NOMBRE**|**EDAD**|**NOTAS**|
| :- | :- | :- | :- |
|<juan.perez@example.com>|Juan Pérez|30|90|
|<juan.perez@example.com>|Juan Pérez|30|100|
|<maria.gonzalez@example.com>|Maria González|25|100|
|<maria.gonzalez@example.com>|Maria González|25|100|
|<john.doe@example.com>|John Doe|40|80|

Aquí veremos que <francisco@example.com> no aparece en el resultado final, ya que no tiene ninguna nota en el sistema. Sin embargo, si utilizamos un LEFT JOIN entre las tablas usuarios y notas, como el siguiente:

SELECT u.email, u.nombre, u.edad, n.notas

FROM usuarios u

LEFT JOIN notas n ON u.email = n.email;

Obtendremos los siguientes registros:

|**EMAIL**|**NOMBRE**|**EDAD**|**NOTAS**|
| :- | :- | :- | :- |
|<juan.perez@example.com>|Juan Pérez|30|90|
|<juan.perez@example.com>|Juan Pérez|30|100|
|<maria.gonzalez@example.com>|Maria González|25|100|
|<maria.gonzalez@example.com>|Maria González|25|100|
|<john.doe@example.com>|John Doe|40|80|
|<francisco@example.com>|Test User|22|NULL|

Al hacer un LEFT JOIN, el registro de <francisco@example.com> aparece en el resultado final con valores NULL en los campos de la tabla notas, puesto que Francisco no tiene ninguna nota en el sistema, sin embargo, está en la tabla de usuarios.
#### **Realizando un LEFT JOIN**
La sintaxis para utilizar LEFT JOIN es similar a INNER JOIN:

SELECT \* FROM tabla1 LEFT JOIN tabla2 ON tabla1.atributo = tabla2.atributo
#### **Ejercicio**
Se tiene una tabla llamada **empleados** y otra llamada \*departamentos+. Utilizando lo aprendido, selecciona a todos los empleados junto a sus departamentos correspondientes, incluyendo a los empleados que aún no han sido asignados a ningún departamento. En ambas tablas existe la columna email.

+----------------------------+                   +----------------------------+

|          empleados         |                   |        departamentos       |

+----------------------------+                   +----------------------------+

| email                      |<----------------->| email                      |

| nombre                     |                   | departamento               |

| edad                       |                   +----------------------------+

+----------------------------+


SELECT t1.email, t1.nombre, t1.edad, t2.email, t2.departamento

FROM empleados t1 LEFT JOIN departamentos t2 ON t1.email = t2.email;


### **Left Join en diagrama de venn**
#### **Ideas clave**
- Los diagramas de Venn son una forma visual de representar conjuntos y operaciones entre ellos.
- Podemos utilizar los diagramas de Venn para visualizar lo que sucede con los registros de las tablas al realizar distintos tipos de JOIN.
- En el diagrama de Venn un INNER JOIN se visualiza como la intersección entre dos círculos.
- En el diagrama de Venn un LEFT JOIN se visualiza como el conjunto de la izquierda.
#### **Armemos un diagrama de Venn**
**Tabla productos**

|**ID**|**NOMBRE**|**PRECIO**|
| :- | :- | :- |
|1|Producto 1|100|
|2|Producto 2|200|
|3|Producto 3|300|

**Tabla ventas**

|**ID**|**ID\_PRODUCTO**|**CANTIDAD**|
| :- | :- | :- |
|1|3|2|
|2|4|2|

Para armar este diagrama, repetimos los pasos que aprendimos previamente. Primero, identificamos la clave de unión de las tablas. Luego, en un círculo izquierdo que representa a la tabla productos ponemos los registros 1, 2 y 3 asociados a la clave id. En el círculo derecho que representa a la tabla ventas ponemos los registros 3 y 4 asociados a la clave id\_producto. En la intersección de ambos círculos ponemos el registro 3, ya que es el único que se encuentra en ambas tablas.

Cuando hacemos una operación de Left Join entre la tabla A y la tabla B, en los resultados aparecerán todos los registros de la tabla A, incluso aquellos que no tienen una clave correspondiente en la tabla B. O sea podemos visualizar el Left Join como el conjunto de la izquierda en un diagrama de Venn.
#### **Analizando el resultado**
Adicionalmente viendo el diagrama de Venn podemos observar el resultado de la operación de Left Join entre las tablas productos y ventas. En el podemos ver:

1. Los registros con id 1, 2 y 3 de la tabla productos aparecerán en los resultados del Left Join dado que los 3 están en el conjunto de la izquierda.
1. Los registros con id 4 de la tabla ventas no aparecerán en los resultados del Left Join dado que no están en el conjunto de la izquierda.
1. El registro 1 y 2 no aparecerán con datos de la tabla de venta ya que solo se encuentran en la tabla de la izquierda.
1. El registro 3 aparecerá con los datos de la tabla venta ya que es el único que se encuentra en ambas tablas.
#### **Ejercicio**
Dada las siguientes tablas:

Tabla **Profesion**

|**ID**|**PROFESION**|
| :- | :- |
|1|Ingeniero|
|2|Médico|
|3|Abogado|
|4|Arquitecto|

Tabla **Personas**

|**ID**|**NOMBRE**|**PROFESION\_ID**|
| :- | :- | :- |
|1|Juan|1|
|2|Maria|2|
|3|Ana|3|

Se tiene una tabla llamada **Personas** que contiene el nombre de las personas y el id de la profesión a la que pertenecen. Se quiere obtener un listado de todas las profesiones y las personas que pertenecen a cada una de ellas. Si una profesión no tiene personas asociadas, se debe mostrar el nombre de la profesión y NULL en el campo Nombre. La tabla resultante sólo debe contener dos columnas: Profesion y Nombre.

SELECT profesion, nombre FROM Personas t1

RIGHT JOIN Profesion t2 ON t2.id = t1.profesion\_id;






### Left Join en diagrama de venn
#### **Ideas clave**
- Los diagramas de Venn son una forma visual de representar conjuntos y operaciones entre ellos.
- Podemos utilizar los diagramas de Venn para visualizar lo que sucede con los registros de las tablas al realizar distintos tipos de JOIN.
- En el diagrama de Venn un INNER JOIN se visualiza como la intersección entre dos círculos.
- En el diagrama de Venn un LEFT JOIN se visualiza como el conjunto de la izquierda.
#### **Armemos un diagrama de Venn**
**Tabla productos**

|**ID**|**NOMBRE**|**PRECIO**|
| :- | :- | :- |
|1|Producto 1|100|
|2|Producto 2|200|
|3|Producto 3|300|

**Tabla ventas**

|**ID**|**ID\_PRODUCTO**|**CANTIDAD**|
| :- | :- | :- |
|1|3|2|
|2|4|2|

Para armar este diagrama, repetimos los pasos que aprendimos previamente. Primero, identificamos la clave de unión de las tablas. Luego, en un círculo izquierdo que representa a la tabla productos ponemos los registros 1, 2 y 3 asociados a la clave id. En el círculo derecho que representa a la tabla ventas ponemos los registros 3 y 4 asociados a la clave id\_producto. En la intersección de ambos círculos ponemos el registro 3, ya que es el único que se encuentra en ambas tablas.

Cuando hacemos una operación de Left Join entre la tabla A y la tabla B, en los resultados aparecerán todos los registros de la tabla A, incluso aquellos que no tienen una clave correspondiente en la tabla B. O sea podemos visualizar el Left Join como el conjunto de la izquierda en un diagrama de Venn.
#### **Analizando el resultado**
Adicionalmente viendo el diagrama de Venn podemos observar el resultado de la operación de Left Join entre las tablas productos y ventas. En el podemos ver:

1. Los registros con id 1, 2 y 3 de la tabla productos aparecerán en los resultados del Left Join dado que los 3 están en el conjunto de la izquierda.
1. Los registros con id 4 de la tabla ventas no aparecerán en los resultados del Left Join dado que no están en el conjunto de la izquierda.
1. El registro 1 y 2 no aparecerán con datos de la tabla de venta ya que solo se encuentran en la tabla de la izquierda.
1. El registro 3 aparecerá con los datos de la tabla venta ya que es el único que se encuentra en ambas tablas.
#### **Ejercicio**
Dada las siguientes tablas:

Tabla **Profesion**

|**ID**|**PROFESION**|
| :- | :- |
|1|Ingeniero|
|2|Médico|
|3|Abogado|
|4|Arquitecto|

Tabla **Personas**

|**ID**|**NOMBRE**|**PROFESION\_ID**|
| :- | :- | :- |
|1|Juan|1|
|2|Maria|2|
|3|Ana|3|

Se tiene una tabla llamada **Personas** que contiene el nombre de las personas y el id de la profesión a la que pertenecen. Se quiere obtener un listado de todas las profesiones y las personas que pertenecen a cada una de ellas. Si una profesión no tiene personas asociadas, se debe mostrar el nombre de la profesión y NULL en el campo Nombre. La tabla resultante sólo debe contener dos columnas: Profesion y Nombre.



SELECT T2.PROFESION, T1.NOMBRE

FROM PROFESION T2 

LEFT join Personas t1 ON T1.PROFESION\_ID=T2.ID 




### Right Join
#### **Ideas clave**
- Existen distintos tipos de JOIN.
- Al utilizar un INNER JOIN, si en una de las tablas no está la clave correspondiente, ese registro no aparecerá en el resultado final.
- Al utilizar un LEFT JOIN, si en la tabla izquierda está la clave pero en la tabla derecha no, el registro de la tabla izquierda aparecerá en el resultado final con valores NULL en los campos de la tabla derecha.
- Al utilizar RIGHT JOIN, si en la tabla derecha está la clave pero en la tabla izquierda no, el registro de la tabla derecha aparecerá en el resultado final con valores NULL en los campos de la tabla izquierda.
#### **RIGHT JOIN**
RIGHT JOIN funciona de la misma forma que LEFT JOIN, pero invierte el orden de las tablas. Mientras que el LEFT JOIN devuelve todas las filas de la tabla izquierda y las coincidencias correspondientes de la tabla derecha (rellenando con NULL si no hay coincidencia), el RIGHT JOIN hace lo contrario: devuelve todas las filas de la tabla derecha y las coincidencias correspondientes de la tabla izquierda.

Para hacer un RIGHT JOIN en SQL, se utiliza la siguiente sintaxis:

SELECT \* 

FROM tabla1 

RIGHT JOIN tabla2 

ON tabla1.atributo = tabla2.atributo;

Para ejemplificar la diferencia entre LEFT JOIN y RIGHT JOIN, consideremos las tablas de "usuarios" y "notas". A diferencia de los casos anteriores estudiados aquí, tendremos notas asociadas a correos que no se encuentran en la tabla de usuarios.
#### **Tabla usuarios**

|**EMAIL**|**NOMBRE**|**EDAD**|
| :- | :- | :- |
|<juan.perez@example.com>|Juan Pérez|30|
|<maria.gonzalez@example.com>|Maria González|25|
|<francisco@example.com>|Test User|22|
#### **Tabla notas**

|**EMAIL**|**NOTAS**|
| :- | :- |
|<juan.perez@example.com>|90|
|<maria.gonzalez@example.com>|100|
|<juan.perez@example.com>|100|
|<maria.gonzalez@example.com>|100|
|<emilio@example.com>|90|

Al hacer un RIGHT JOIN entre las tablas usuarios y notas utilizando el campo email como clave de la siguiente forma:

SELECT u.email, nombre, edad, notas

FROM usuarios u

RIGHT JOIN notas n 

ON u.email = n.email;

Obtendremos la siguiente respuesta:

|**EMAIL**|**NOMBRE**|**EDAD**|**NOTAS**|
| :- | :- | :- | :- |
|<juan.perez@example.com>|Juan Pérez|30|90|
|<juan.perez@example.com>|Juan Pérez|30|100|
|<maria.gonzalez@example.com>|Maria González|25|100|
|<maria.gonzalez@example.com>|Maria González|25|100|
|<emilio@example.com>|NULL|NULL|90|

En este ejemplo puntual <emilio@example.com> tiene notas pero no tenemos su registro en la tabla de usuarios. Utilizando RIGHT JOIN podemos mostrar su información.
## **Ejercicio**
Dadas las tablas **empleados** y **departamentos**:

+----------------------------+              +---------------------------+

|          empleados         |              |        departamentos      |

+----------------------------+              +---------------------------+

| email     (PK)             |--------------| email     (FK)            |

| nombre                     |              | departamento              |

| edad                       |              |                           |                 

+----------------------------+              +---------------------------+

Nos solicitan seleccionar todos los registros de los departamentos de todas las oficinas junto con sus correspondientes empleados, incluyendo aquellos departamentos que no tienen empleados asociados. Ambas tablas contienen la columna email.

SELECT e.email, e.nombre, e.edad, d.email, d.departamento FROM empleados e 

RIGHT JOIN departamentos d ON d.email = e.email;





### Left Join y Right Join
#### **Ideas clave**
- Al utilizar un LEFT JOIN, si en la tabla izquierda está la clave pero en la tabla derecha no, el registro de la tabla izquierda aparecerá en el resultado final con valores NULL en los campos de la tabla derecha.
- Al utilizar un RIGHT JOIN, si en la tabla derecha está la clave pero en la tabla izquierda no, el registro de la tabla derecha aparecerá en el resultado final con valores NULL en los campos de la tabla izquierda.
- LEFT JOIN y RIGHT JOIN son un reflejo el uno del otro. Utilizar LEFT JOIN o RIGHT JOIN depende simplemente de qué tabla quieres nombrar primero.
#### **LEFT JOIN o RIGHT JOIN**
Utilizar LEFT JOIN o RIGHT JOIN depende simplemente de qué tabla quieres nombrar primero.

SELECT \* 

FROM tabla1 

LEFT JOIN tabla2 ON tabla1.id = tabla2.id

Es prácticamente lo mismo que:

SELECT \* 

FROM tabla2

RIGHT JOIN tabla1 on tabla2.id = tabla1.id

LEFT JOIN y RIGHT JOIN son un reflejo el uno del otro. Sin embargo, existe una pequeña diferencia cuando los utilizamos en conjunto con SELECT \*, dado que los atributos de los primera tabla se mostrarán primero.

Por ejemplo, si tenemos las siguientes tablas:

Tabla usuarios

|**EMAIL**|**NOMBRE**|**EDAD**|
| :- | :- | :- |
|<juan.perez@example.com>|Juan Pérez|30|
|<maria.gonzalez@example.com>|Maria González|25|
|<francisco@example.com>|Test User|22|

Tabla notas

|**EMAIL**|**NOTAS**|
| :- | :- |
|<juan.perez@example.com>|90|
|<maria.gonzalez@example.com>|100|
|<juan.perez@example.com>|100|
|<maria.gonzalez@example.com>|100|
|<emilio@example.com>|90|

Con SELECT \* FROM usuarios left join notas on usuarios.email = notas.email; obtendríamos lo siguiente:

|**EMAIL**|**NOMBRE**|**EDAD**|**EMAIL**|**NOTAS**|
| :- | :- | :- | :- | :- |
|<juan.perez@example.com>|Juan Pérez|30|<juan.perez@example.com>|90|
|<juan.perez@example.com>|Juan Pérez|30|<juan.perez@example.com>|100|
|<maria.gonzalez@example.com>|Maria González|25|<maria.gonzalez@example.com>|100|
|<maria.gonzalez@example.com>|Maria González|25|<maria.gonzalez@example.com>|100|
|<francisco@example.com>|Test User|22|NULL|NULL|

En cambio, con SELECT \* FROM Notas RIGHT JOIN Usuarios ON Notas.email = Usuarios.email; obtendríamos:

|**EMAIL**|**NOTAS**|**EMAIL**|**NOMBRE**|**EDAD**|
| :- | :- | :- | :- | :- |
|<juan.perez@example.com>|90|<juan.perez@example.com>|Juan Pérez|30|
|<juan.perez@example.com>|100|<juan.perez@example.com>|Juan Pérez|30|
|<maria.gonzalez@example.com>|100|<maria.gonzalez@example.com>|Maria González|25|
|<maria.gonzalez@example.com>|100|<maria.gonzalez@example.com>|Maria González|25|
|NULL|NULL|<francisco@example.com>|Test User|22|

Para obtener los resultados en el mismo orden simplemente podemos especificar el orden que queremos.

SELECT usuarios.\*, notas.\* 

FROM Notas 

RIGHT JOIN Usuarios ON Notas.email = Usuarios.email;` 

A partir de este ejercicio queda a tu discreción como resolver los problemas, ya sea utilizando LEFT JOIN o RIGHT JOIN, pero para que las respuestas sean marcadas correctas los atributos deben aparecer en el orden que las tablas son mencionadas, a menos que se especifique lo contrario.
# **Ejercicio**
Selecciona todos los registros de todos los productos (tabla productos) junto a sus precios (tabla precios), incluyendo a los productos que no tienen precio asignado. Las tablas se relacionan entre si por la columna producto\_id.
### Lef
### t Join y Right Join
#### **Ideas clave**
- Al utilizar un LEFT JOIN, si en la tabla izquierda está la clave pero en la tabla derecha no, el registro de la tabla izquierda aparecerá en el resultado final con valores NULL en los campos de la tabla derecha.
- Al utilizar un RIGHT JOIN, si en la tabla derecha está la clave pero en la tabla izquierda no, el registro de la tabla derecha aparecerá en el resultado final con valores NULL en los campos de la tabla izquierda.
- LEFT JOIN y RIGHT JOIN son un reflejo el uno del otro. Utilizar LEFT JOIN o RIGHT JOIN depende simplemente de qué tabla quieres nombrar primero.
#### **LEFT JOIN o RIGHT JOIN**
Utilizar LEFT JOIN o RIGHT JOIN depende simplemente de qué tabla quieres nombrar primero.

SELECT \* 

FROM tabla1 

LEFT JOIN tabla2 ON tabla1.id = tabla2.id

Es prácticamente lo mismo que:

SELECT \* 

FROM tabla2

RIGHT JOIN tabla1 on tabla2.id = tabla1.id

LEFT JOIN y RIGHT JOIN son un reflejo el uno del otro. Sin embargo, existe una pequeña diferencia cuando los utilizamos en conjunto con SELECT \*, dado que los atributos de los primera tabla se mostrarán primero.

Por ejemplo, si tenemos las siguientes tablas:

Tabla usuarios

|**EMAIL**|**NOMBRE**|**EDAD**|
| :- | :- | :- |
|<juan.perez@example.com>|Juan Pérez|30|
|<maria.gonzalez@example.com>|Maria González|25|
|<francisco@example.com>|Test User|22|

Tabla notas

|**EMAIL**|**NOTAS**|
| :- | :- |
|<juan.perez@example.com>|90|
|<maria.gonzalez@example.com>|100|
|<juan.perez@example.com>|100|
|<maria.gonzalez@example.com>|100|
|<emilio@example.com>|90|

Con SELECT \* FROM usuarios left join notas on usuarios.email = notas.email; obtendríamos lo siguiente:

|**EMAIL**|**NOMBRE**|**EDAD**|**EMAIL**|**NOTAS**|
| :- | :- | :- | :- | :- |
|<juan.perez@example.com>|Juan Pérez|30|<juan.perez@example.com>|90|
|<juan.perez@example.com>|Juan Pérez|30|<juan.perez@example.com>|100|
|<maria.gonzalez@example.com>|Maria González|25|<maria.gonzalez@example.com>|100|
|<maria.gonzalez@example.com>|Maria González|25|<maria.gonzalez@example.com>|100|
|<francisco@example.com>|Test User|22|NULL|NULL|

En cambio, con SELECT \* FROM Notas RIGHT JOIN Usuarios ON Notas.email = Usuarios.email; obtendríamos:

|**EMAIL**|**NOTAS**|**EMAIL**|**NOMBRE**|**EDAD**|
| :- | :- | :- | :- | :- |
|<juan.perez@example.com>|90|<juan.perez@example.com>|Juan Pérez|30|
|<juan.perez@example.com>|100|<juan.perez@example.com>|Juan Pérez|30|
|<maria.gonzalez@example.com>|100|<maria.gonzalez@example.com>|Maria González|25|
|<maria.gonzalez@example.com>|100|<maria.gonzalez@example.com>|Maria González|25|
|NULL|NULL|<francisco@example.com>|Test User|22|

Para obtener los resultados en el mismo orden simplemente podemos especificar el orden que queremos.

SELECT usuarios.\*, notas.\* 

FROM Notas 

RIGHT JOIN Usuarios ON Notas.email = Usuarios.email;` 

A partir de este ejercicio queda a tu discreción como resolver los problemas, ya sea utilizando LEFT JOIN o RIGHT JOIN, pero para que las respuestas sean marcadas correctas los atributos deben aparecer en el orden que las tablas son mencionadas, a menos que se especifique lo contrario.
# **Ejercicio**
Selecciona todos los registros de todos los productos (tabla productos) junto a sus precios (tabla precios), incluyendo a los productos que no tienen precio asignado. Las tablas se relacionan entre si por la columna producto\_id.

SELECT productos.\*, precios.\* 

FROM productos 

LEFT JOIN precios ON productos.producto\_id = precios.producto\_id;




### Identificando tipos de join
#### **Ideas clave:**
- Existen múltiples tipos de JOIN
- Hasta el momento hemos visto INNER JOIN, LEFT JOIN y RIGHT JOIN
- Debemos saber identificar el tipo de JOIN a utilizar en una consulta a partir de la petición
#### **Guía útil para identificar el tipo de join**
1. **INNER JOIN**
   1. **Cuándo usarlo:** Cuando necesitas sólo las filas donde haya coincidencias en ambas tablas.
   1. **Resultado:** Devuelve solo las filas con datos correspondientes en ambas tablas.
1. **LEFT JOIN (o LEFT OUTER JOIN)**
   1. **Cuándo usarlo:** Cuando necesitas todas las filas de la tabla de la izquierda y las filas coincidentes de la tabla de la derecha.
   1. **Resultado:** Devuelve todas las filas de la tabla de la izquierda y las coincidencias de la tabla de la derecha, con NULLs donde no haya coincidencias.
1. **RIGHT JOIN (o RIGHT OUTER JOIN)**
   1. **Cuándo usarlo:** Cuando necesitas todas las filas de la tabla de la derecha y las filas coincidentes de la tabla de la izquierda.
   1. **Resultado:** Devuelve todas las filas de la tabla de la derecha y las coincidencias de la tabla de la izquierda, con NULLs donde no haya coincidencias.
## **Ejercicio**
Se tiene una base de datos con dos tablas principales: autores y libros.

Crea una consulta con el fin de obtener información que muestre el nombre del autor junto con el título del libro que ha escrito. **La consulta debe incluir sólo aquellos libros que tienen autores asignados**

tip: Aparece destacado la pista para identificar el tipo de JOIN a utilizar.

Las columnas de la consulta deben llamarse:

- nombre\_autor
- titulo\_libro
### **Tabla autores:**

|**ID**|**NOMBRE**|
| :- | :- |
|1|Gabriel García Márquez|
|2|Isabel Allende|
|3|J.K. Rowling|
### **Tabla libros:**

|**ID**|**TITULO**|**ID\_AUTOR**|
| :- | :- | :- |
|1|Cien Años de Soledad|1|
|2|La Casa de los Espíritus|2|
|3|Harry Potter y la Piedra Filosofal|3|
|4|Libro sin Autor|NULL|

select nombre nombre\_autor, titulo as titulo\_libro

from autores

INNER join libros on autores.id = libros.id\_autor


### Identificando tipos de join parte 2
#### **Guía útil para identificar el tipo de join**
1. **INNER JOIN**
   1. **Cuándo usarlo:** Cuando necesitas sólo las filas donde haya coincidencias en ambas tablas.
   1. **Resultado:** Devuelve solo las filas con datos correspondientes en ambas tablas.
1. **LEFT JOIN (o LEFT OUTER JOIN)**
   1. **Cuándo usarlo:** Cuando necesitas todas las filas de la tabla de la izquierda y las filas coincidentes de la tabla de la derecha.
   1. **Resultado:** Devuelve todas las filas de la tabla de la izquierda y las coincidencias de la tabla de la derecha, con NULLs donde no haya coincidencias.
1. **RIGHT JOIN (o RIGHT OUTER JOIN)**
   1. **Cuándo usarlo:** Cuando necesitas todas las filas de la tabla de la derecha y las filas coincidentes de la tabla de la izquierda.
   1. **Resultado:** Devuelve todas las filas de la tabla de la derecha y las coincidencias de la tabla de la izquierda, con NULLs donde no haya coincidencias.
## **Ejercicio**
Se tiene una base de datos con dos tablas principales: empleados y proyectos.

Crea una consulta con el fin de obtener información detallada, y que muestre el nombre del empleado junto con el nombre del proyecto en el que participa.
#### **Tabla de empleados**
La tabla de empleados tiene los siguientes campos:

- id (identificador único del empleado)
- nombre (nombre del empleado)
- id\_proyecto (identificador del proyecto en el que participa el empleado)
## **Datos de ejemplo**

|**ID**|**NOMBRE**|**ID\_PROYECTO**|
| :- | :- | :- |
|1|Juan Pérez|1|
|2|María Gonzalez|2|
|3|Pedro López|NULL|
|4|Ana Rodríguez|3|
### **Tabla de proyectos**
La tabla de proyectos tiene los siguientes campos:

- id (identificador único del proyecto)
- nombre\_proyecto (nombre del proyecto)
#### **Datos de ejemplo**

|**ID**|**NOMBRE\_PROYECTO**|
| :- | :- |
|1|Desarrollo Web|
|2|App Móvil|
|3|Sistema de Inventario|
### **Resultado esperado**
El resultado debe tener las columnas con los siguientes nombres e incluir a todos los empleados, aunque no tengan asignado proyecto.

- nombre\_empleado
- nombre\_proyecto



SELECT nombre AS nombre\_empleado, nombre\_proyecto 

FROM empleados left JOIN proyectos ON empleados.id\_proyecto = proyectos.id




### Identificando tipos de join parte 3
#### **Guía útil para identificar el tipo de join**
1. **INNER JOIN**
   1. **Cuándo usarlo:** Cuando necesitas sólo las filas donde haya coincidencias en ambas tablas.
   1. **Resultado:** Devuelve solo las filas con datos correspondientes en ambas tablas.
1. **LEFT JOIN (o LEFT OUTER JOIN)**
   1. **Cuándo usarlo:** Cuando necesitas todas las filas de la tabla de la izquierda y las filas coincidentes de la tabla de la derecha.
   1. **Resultado:** Devuelve todas las filas de la tabla de la izquierda y las coincidencias de la tabla de la derecha, con NULLs donde no haya coincidencias.
1. **RIGHT JOIN (o RIGHT OUTER JOIN)**
   1. **Cuándo usarlo:** Cuando necesitas todas las filas de la tabla de la derecha y las filas coincidentes de la tabla de la izquierda.
   1. **Resultado:** Devuelve todas las filas de la tabla de la derecha y las coincidencias de la tabla de la izquierda, con NULLs donde no haya coincidencias.
### **Ejercicio**
Se tiene una base de datos con dos tablas principales: empleados y proyectos.

Se pide obtener una lista de todos los proyectos junto con los nombres de los empleados asignados a cada proyecto, incluyendo aquellos proyectos que no tienen empleados asignados", se utilizan las siguientes columnas:

El resultado debe estar únicamente compuesto por las columnas nombre\_empleado y nombre\_proyecto que corresponden al nombre del empleado y al nombre del proyecto de sus respectivas tablas, incluso aquellos que no tienen empleados asignados (empleado NULL).
### **Tabla: empleados**

|**ID**|**NOMBRE**|**ID\_PROYECTO**|
| :- | :- | :- |
|1|Juan Pérez|1|
|2|María González|2|
|3|Pedro López|NULL|
|4|Ana Rodríguez|3|
### **Tabla: proyectos**

|**ID**|**NOMBRE\_PROYECTO**|
| :- | :- |
|1|Desarrollo Web|
|2|App Móvil|
|3|Sistema de Inventario|
|4|Marketing Digital|


SELECT nombre AS nombre\_empleado, nombre\_proyecto 

FROM empleados right JOIN proyectos ON empleados.id\_proyecto = proyectos.id



### Full outer join
#### **Ideas clave**
- Existen distintos tipos de JOIN.
- Al utilizar un INNER JOIN, si en una de las tablas no está la clave correspondiente, ese registro no aparecerá en el resultado final.
- Al utilizar un LEFT JOIN, si en la tabla izquierda está la clave pero en la tabla derecha no, el registro de la tabla izquierda aparecerá en el resultado final con valores NULL en los campos de la tabla derecha.
- Al utilizar RIGHT JOIN, si en la tabla derecha está la clave pero en la tabla izquierda no, el registro de la tabla derecha aparecerá en el resultado final con valores NULL en los campos de la tabla izquierda.
- Al utilizar FULL OUTER JOIN, se obtienen todos los registros de ambas tablas, incluyendo los registros no coincidentes.
#### **Full outer join**
Full outer join es una combinación de LEFT JOIN y RIGHT JOIN. Devuelve todos los registros de ambas tablas, incluyendo los registros no coincidentes.

Veamos un ejemplo antes de conocer la sintaxis para entender mejor cómo funciona.

Se tiene dos tablas

**Tabla empleados:**

|**ID\_EMPLEADO**|**NOMBRE**|**ID\_DEPARTAMENTO**|
| :- | :- | :- |
|1|Ana|10|
|2|Juan|20|
|3|María|30|

**Tabla departamentos:**

|**ID\_DEPARTAMENTO**|**DEPARTAMENTO**|
| :- | :- |
|10|Recursos Humanos|
|20|Finanzas|
|40|Marketing|

Una consulta con FULL OUTER JOIN entre las tablas empleados y departamentos, utilizando el campo id\_departamento, daría como resultado:

|**ID\_EMPLEADO**|**NOMBRE**|**ID\_DEPARTAMENTO**|**DEPARTAMENTO**|
| :- | :- | :- | :- |
|1|Ana|10|Recursos Humanos|
|2|Juan|20|Finanzas|
|3|María|30|NULL|
|NULL|NULL|40|Marketing|

Estos datos nos podrían ayudar a identificar empleados que no están asignados a un departamento o departamentos sin empleados en una única vista.
#### **Implementando full outer join en SQLite**
El motor de base de datos SQLite no soporta operaciones de FULL OUTER JOIN. Sin embargo, se puede lograr el mismo efecto con la siguiente sintaxis:

SELECT \*

FROM tableA

LEFT JOIN tableB

`  `ON tableA.column\_name = tableB.column\_name

UNION

SELECT \*

FROM tableA

RIGHT JOIN tableB

`  `ON tableA.column\_name = tableB.column\_name
#### Ejercicio
Dada las tablas empleados y departamentos que vimos previamente, escribe una consulta que devuelva todos los registros coincidentes y no coincidentes entre las tablas empleados y departamentos.


FULL OUTER JOIN








### **Full outer join parte 2**
#### Ideas clave
- Al utilizar un LEFT JOIN, si en la tabla izquierda está la clave pero en la tabla derecha no, el registro de la tabla izquierda aparecerá en el resultado final con valores NULL en los campos de la tabla derecha.
- Al utilizar RIGHT JOIN, si en la tabla derecha está la clave pero en la tabla izquierda no, el registro de la tabla derecha aparecerá en el resultado final con valores NULL en los campos de la tabla izquierda.
- Al utilizar FULL OUTER JOIN, se obtienen todos los registros de ambas tablas, incluyendo los registros no coincidentes.
#### Full outer join
Una operación de full outer join es la únion de un LEFT JOIN y un RIGHT JOIN. Devuelve todos los registros de ambas tablas, incluyendo los registros no coincidentes.

#### Union vs Union all
Si miramos el diagrama detenidamente, nos daremos cuenta que si simplemente unimos los resultados de un LEFT JOIN y un RIGHT JOIN podríamos estar duplicando los registros en el punto de intersección. Aquí es donde debemos recordar la diferencia entre UNION y UNION ALL. UNION elimina los registros duplicados, mientras que UNION ALL no lo hace. Por lo tanto si unimos los resultados de un LEFT JOIN y un RIGHT JOIN debemos utilizar UNION para evitar duplicados.
### Lef
### t excluding join
#### **Ideas clave**
- Al utilizar un LEFT JOIN, si la clave está presente en la tabla izquierda pero ausente en la tabla derecha, el registro de la tabla izquierda se mostrará en el resultado final con valores NULL en los campos de la tabla derecha.
- Un left excluding join es una combinación de left join con una cláusula WHERE para mostrar los registros de la tabla izquierda que no tienen coincidencias en la tabla derecha.
#### **Left excluding join**
Left excluding join es un tipo de join que se utiliza cuando queremos obtener los registros de la tabla izquierda que no tienen coincidencias en la tabla derecha.
#### **Tabla Alumnos**

|**ID**|**NOMBRE**|**APELLIDO**|
| :- | :- | :- |
|1|Juan|Perez|
|2|Maria|Garcia|
|3|Pedro|Lopez|
#### **Tabla Calificaciones**

|**ID**|**ALUMNO\_ID**|**CALIFICACION**|
| :- | :- | :- |
|1|1|8\.5|
|2|1|7\.9|
|3|2|9\.2|
|4|2|8\.8|

En este ejemplo si queremos obtener los alumnos que no tienen calificaciones, podemos hacerlo con un left excluding join.

SELECT \*

FROM alumnos a

LEFT JOIN calificaciones c

ON a.id = c.alumno\_id

WHERE c.calificacion IS NULL;

Y como resultado obtendríamos:

|**ID**|**NOMBRE**|**APELLIDO**|**ID**|**ALUMNO\_ID**|**CALIFICACION**|
| :- | :- | :- | :- | :- | :- |
|3|Pedro|Lopez||||
Dado que Pedro es el único alumno que no tiene calificaciones, es el único que aparece en el resultado final.

En diagrama de Venn, podemos ver la diferencia entre un left join y un left excluding join.

SELECT \*

FROM alumnos a

LEFT JOIN calificaciones c

ON a.id = c.alumno\_id

WHERE c.calificacion IS NULL;

## **Ejercicio Didáctico**
Dada las siguientes tablas:

Tabla **Profesion**

|**ID**|**NOMBRE**|
| :- | :- |
|1|Ingeniero|
|2|Doctor|
|3|Abogado|

Tabla **Personas**

|**ID**|**NOMBRE**|**APELLIDO**|**PROFESION\_ID**|
| :- | :- | :- | :- |
|1|Juan|Perez|1|
|2|Maria|Garcia|2|
|3|Pedro|Lopez|2|

Crea una consulta SQL que muestre todos los datos de las tablas mencionadas de las personas que no tienen profesión.

SELECT \* FROM personas p LEFT JOIN profesion pr ON p.profesion\_id = pr.id WHERE pr.id IS NULL;



### Right excluding join
#### **Ideas clave**
- Al utilizar un LEFT JOIN, si en la tabla izquierda está la clave pero en la tabla derecha no, el registro de la tabla izquierda aparecerá en el resultado final con valores NULL en los campos de la tabla derecha.
- Un left excluding join es una combinación de left join con una cláusula WHERE para mostrar los registros de la tabla izquierda que no tienen coincidencias en la tabla derecha.
- Un right excluding join es una combinación de right join con una cláusula WHERE para mostrar los registros de la tabla derecha que no tienen coincidencias en la tabla izquierda.
#### **¿Cómo funciona un right excluding join?**
Right excluding join es muy similar a Left excluding Join. Una consulta de right excluding join nos entrega los registros que **no tienen coincidencia** con la **tabla izquierda**.

SELECT \*

FROM tableA

RIGHT JOIN tableB

`  `ON tableA.name = tableB.name

WHERE tableA.name IS NULL

Es importante observar que además de cambiar el JOIN hay que cambiar el WHERE y sustituir **tableA** por **tableB**
#### **Caso práctico**
En una base de datos se tienen las tablas de calificaciones y cursos.

Tabla: **calificaciones**

|**ID**|**ALUMNO\_ID**|**CURSO\_ID**|**CALIFICACION**|
| :- | :- | :- | :- |
|1|1|1|8\.5|
|2|1|2|7\.9|
|3|2|1|9\.2|
|4|2|2|8\.8|
|5|3|1|7\.5|
|6|4|2|9\.1|

Tabla: **cursos**

|**ID**|**NOMBRE**|**DOCENTE\_ID**|
| :- | :- | :- |
|1|Matemáticas|1|
|2|Ciencias|1|
|3|Arte|1|

Nos piden obtener toda la información de los cursos que no tienen calificaciones. Para resolver esto con un right excluding join, la consulta sería:

SELECT \*

FROM calificaciones c

RIGHT JOIN cursos cu

ON cu.id = c.curso\_id

WHERE c.id IS NULL;

Como resultado obtendríamos:

|**ID**|**ALUMNO\_ID**|**CURSO\_ID**|**CALIFICACION**|**ID**|**NOMBRE**|**DOCENTE\_ID**|
| :- | :- | :- | :- | :- | :- | :- |
|||||3|Arte|1|
#### **Ejercicio**
Dada la siguientes tablas:

Tabla **docentes**

|**ID**|**NOMBRE**|
| :- | :- |
|1|Benjamin|
|2|Felipe|
|3|Susana|

Tabla: **cursos**

|**ID**|**NOMBRE**|**DOCENTE\_ID**|
| :- | :- | :- |
|1|Matemáticas|1|
|2|Ciencias|1|
|3|Arte|1|

Utiliza un right join para obtener a los docentes que aún no tienen un curso asignado.

SELECT \* FROM cursos c right JOIN docentes d ON d.id = c.docente\_id WHERE c.id IS NULL; 



### Full outer excluding join
#### **Ideas clave**
- Un left excluding join es una combinación de left join con una cláusula WHERE para mostrar los registros de la tabla izquierda que no tienen coincidencias en la tabla derecha.
- Un right excluding join es una combinación de right join con una cláusula WHERE para mostrar los registros de la tabla derecha que no tienen coincidencias en la tabla izquierda.
- Al utilizar FULL OUTER JOIN, se obtienen todos los registros de ambas tablas, incluyendo los registros no coincidentes.
- Full Outer Excluding Join es una combinación de FULL OUTER JOIN con una cláusula WHERE para mostrar los registros que no tienen coincidencias en ambas tablas.
#### **FULL OUTER EXCLUDING JOIN**
FULL OUTER EXCLUDING JOIN nos entrega los registros coincidentes, pero también los no coincidentes de la tabla de la derecha como de la izquierda.

Aunque SQLite no soporta directamente FULL OUTER JOIN, podemos realizar un FULL OUTER EXCLUDING JOIN utilizando una combinación de LEFT EXCLUDING JOIN y RIGHT EXCLUDING JOIN.

SELECT \*

FROM tabla\_A

LEFT JOIN tabla\_B ON tabla\_A.clave = tabla\_B.clave

WHERE tabla\_B.clave IS NULL

UNION

SELECT \*

FROM tabla\_A

RIGHT JOIN tabla\_B ON tabla\_A.clave = tabla\_B.clave

WHERE tabla\_A.clave IS NULL

Esta consulta nos dará todos los registros de tabla\_A que no tienen coincidencia en tabla\_B, y todos los registros de tabla\_B que no tienen coincidencia en tabla\_A.
#### Ejercicio\*\*
Consideremos las siguientes tablas:

Tabla empleados:

|**ID\_EMPLEADO**|**NOMBRE**|**ID\_DEPARTAMENTO**|
| :- | :- | :- |
|1|Ana|10|
|2|Juan|20|
|3|María|30|
|4|Carlos|NULL|

Tabla departamentos:

|**ID\_DEPARTAMENTO**|**DEPARTAMENTO**|
| :- | :- |
|10|Recursos Humanos|
|20|Finanzas|
|40|Marketing|

Escribe una consulta SQL que implemente un FULL OUTER EXCLUDING JOIN entre las tablas empleados y departamentos. Esta consulta debe mostrar tanto a los Empleados que no están asignados a ningún departamento existente como a los departamentos que no tienen empleados asignados.

Una vez que hayas escrito la consulta, ejecútala y analiza los resultados y contesta las siguientes preguntas:

1. ¿Por qué Carlos aparece en el resultado de la consulta?
1. ¿Por qué el departamento de Marketing aparece en el resultado?

   Porque se encuentra en la tabla de departamento pero no en la de empleados. 

1. ¿Cómo se diferencia este resultado de un FULL OUTER JOIN regular?



SELECT tabla\_A.id\_empleado, tabla\_A.nombre, tabla\_A.id\_departamento, departamento 

FROM empleados AS tabla\_A 

LEFT JOIN departamentos AS tabla\_B ON tabla\_A.id\_departamento = tabla\_B.id\_departamento 

WHERE tabla\_B.id\_departamento IS NULL UNION 

SELECT NULL AS id\_empleado, NULL AS nombre, tabla\_B.id\_departamento, tabla\_B.departamento 

FROM empleados AS tabla\_A 

RIGHT JOIN departamentos AS tabla\_B ON tabla\_A.id\_departamento = tabla\_B.id\_departamento 

WHERE tabla\_A.id\_empleado IS NULL;



### Natural Join
#### **Ideas clave**
- Natural Join es un JOIN que adicionalmente asume que las columnas con el mismo nombre son las columnas de unión.
- La ventaja de usar NATURAL JOIN es que simplifica la escritura de la consulta, pero solo es útil cuando las columnas de unión tienen el mismo nombre y tipo de datos en ambas tablas.


#### **Natural Join**
El **NATURAL JOIN** es un tipo de join en SQL que se utiliza para combinar dos tablas utilizando las columnas que tienen el mismo nombre. Su sintaxis es la siguiente:

SELECT columnas

FROM tabla1

NATURAL JOIN tabla2;

Como se espera que las columnas se llamen igual no es necesario especificarlas.
#### **Veamos un ejemplo:**
Supongamos que tenemos dos tablas, clientes y pedidos, con la siguiente estructura:

**Tabla clientes**

|**ID\_CLIENTE**|**NOMBRE**|**EMAIL**|
| :- | :- | :- |
|1|Juan|<juan@example.com>|
|2|María|<maria@example.com>|
|3|Pedro|<pedro@example.com>|

**Tabla pedidos**

|**ID\_PEDIDO**|**ID\_CLIENTE**|**PRODUCTO**|**CANTIDAD**|
| :- | :- | :- | :- |
|1|1|Laptop|1|
|2|2|Tablet|2|
|3|1|Smartphone|1|

En este caso, ambas tablas tienen una columna id\_cliente por lo que, al hacer un Natural Join, esta será la columna utilizada para unir las tablas.

SELECT \*

FROM clientes

NATURAL JOIN pedidos;

|**ID\_CLIENTE**|**NOMBRE**|**EMAIL**|**ID\_PEDIDO**|**PRODUCTO**|**CANTIDAD**|
| :- | :- | :- | :- | :- | :- |
|1|Juan|<juan@example.com>|1|Laptop|1|
|2|María|<maria@example.com>|2|Tablet|2|
|3|Pedro|<pedro@example.com>|3|Smartphone|1|
## **Ejercicio**
Se tiene una base de datos de una tienda en línea con las siguientes tablas:

**Tabla productos:**

|**ID\_PRODUCTO**|**NOMBRE**|**CATEGORÍA**|**PRECIO**|
| :- | :- | :- | :- |
|1|Laptop|Electrónica|800|
|2|Smartphone|Electrónica|500|
|3|Camiseta|Ropa|20|
|4|Zapatos|Calzado|50|

**Tabla ventas:**

|**ID\_VENTA**|**ID\_PRODUCTO**|**CANTIDAD**|**FECHA**|
| :- | :- | :- | :- |
|1|1|2|2024-01-01|
|2|2|1|2024-01-01|
|3|3|3|2024-01-02|
|4|4|1|2024-01-02|

Realiza una consulta utilizando **NATURAL JOIN** que muestre el nombre del producto, la cantidad vendida y la fecha de venta de cada producto vendido. Utiliza los nombres originales de las columnas.

SELECT nombre, cantidad, fecha FROM productos NATURAL JOIN ventas;

### Nat
### ural Left Join
#### **Ideas clave**
- Natural Join es un JOIN que adicionalmente asume que las columnas con el mismo nombre son las columnas de unión.
- La ventaja de usar NATURAL JOIN es que simplifica la escritura de la consulta, pero solo es útil cuando las columnas de unión tienen el mismo nombre y tipo de datos en ambas tablas.
- Así como para JOIN la opción de INNER es implícita, para NATURAL JOIN la opción de INNER también es implícita. y uno puede utilizar NATURAL INNER JOIN, NATURAL LEFT JOIN, NATURAL RIGHT JOIN.
#### **Natural Left Join**
NATURAL LEFT JOIN realiza un LEFT JOIN utilizando las columnas que tienen el mismo nombre en ambas tablas. Su uso es el siguiente:

SELECT columnas

FROM tabla1

NATURAL LEFT JOIN tabla2;
#### **Ejercicio**
Dada las tablas entregadas, crea un reporte que seleccione a todos los estudiantes (sus nombres), cursos inscritos y fecha de inscripciones. Si un estudiante no tiene cursos inscritos, se debe mostrar el estudiante sin los datos de inscripción.

Aquí tienes las tablas estudiantes e inscripciones representadas en Markdown:

**Tabla estudiantes**

| id\_estudiante | nombre | email              |

\|---------------|--------|--------------------|

| 1             | Carlos | carlos@example.com |

| 2             | Laura  | laura@example.com  |

| 3             | Miguel | miguel@example.com |

| 4             | Ana    | ana@example.com    |

**Tabla inscripciones**

| id\_inscripcion | id\_estudiante | curso       | fecha       |

\|----------------|---------------|-------------|-------------|

| 1              | 1             | Matemáticas | 2024-03-01  |

| 2              | 2             | Historia    | 2024-03-02  |

| 3              | 1             | Física      | 2024-03-03  |

| 4              | 3             | Química     | 2024-03-04  |


SELECT nombre, curso,fecha

FROM estudiantes

NATURAL LEFT JOIN inscripciones;



### Self Join
#### **Ideas clave**
- Un self join se utiliza para combinar una tabla consigo misma.
- Self join no es un tipo de join específico, es solo el término utilizado para referirse a la operación de combinar una tabla consigo misma.
- Para lograr el self join se utilizan otros tipos de joins como INNER JOIN o LEFT JOIN.
#### **Self Join**
Un self join es un tipo de join en SQL que se utiliza para combinar una tabla consigo misma. Se usa cuando queremos relacionar filas de una tabla con otras filas de la misma tabla. Aunque el término "self join" se refiere a esta relación consigo misma, en la práctica se utilizan otros tipos de joins como INNER JOIN o LEFT JOIN para realizar esta operación.
#### **Ejemplo**
Supongamos que tenemos una tabla llamada empleados con la siguiente estructura:

|**ID\_EMPLEADO**|**NOMBRE**|**ID\_SUPERVISOR**|
| :- | :- | :- |
|1|Juan|NULL|
|2|María|1|
|3|Pedro|1|
|4|Ana|2|
|5|Luis|2|
#### **Uso del Self Join**
Para obtener el nombre de **todos** los empleados junto con el nombre de su supervisor, podemos usar un self join de la siguiente manera:

SELECT e1.nombre AS nombre\_empleado, e2.nombre AS nombre\_supervisor

FROM empleados e1

LEFT JOIN empleados e2 ON e1.id\_supervisor = e2.id\_empleado;

|**NOMBRE\_EMPLEADO**|**NOMBRE\_SUPERVISOR**|
| :- | :- |
|Juan|NULL|
|María|Juan|
|Pedro|Juan|
|Ana|María|
|Luis|María|

En este ejemplo, estamos obteniendo el nombre de cada empleado (e1.nombre) y el nombre de su supervisor (e2.nombre). El self join se realiza uniendo la tabla empleados consigo misma (empleados e1 LEFT JOIN empleados e2), utilizando la columna id\_supervisor de e1 y la columna id\_empleado de e2.

Se utiliza LEFT JOIN en lugar de INNER JOIN para incluir a los empleados que no tienen supervisor, dado que en la consulta nos pedían los nombres de **todos** los empleados.
#### **Ejercicio**
Se tiene la tabla clientes con los siguientes datos:

|**ID\_CLIENTE**|**NOMBRE**|**ID\_CLIENTE\_REFERENTE**|
| :- | :- | :- |
|1|Juan|NULL|
|2|María|1|
|3|Pedro|1|
|4|Ana|2|
|5|Luis|2|

Utilizando lo aprendido escribe una consulta que muestre el nombre de todos los clientes junto con el nombre de su cliente referente. Las columnas de la tabla resultante deben llamarse nombre\_cliente y nombre\_cliente\_referente.


SELECT e1.nombre AS nombre\_empleado, e2.nombre AS nombre\_supervisor

FROM empleados e1

LEFT JOIN empleados e2 ON e1.id\_supervisor = e2.id\_empleado;


### Self Join
#### **Ideas clave**
- Un self join se utiliza para combinar una tabla consigo misma.
- Self join no es un tipo de join específico, es solo el término utilizado para referirse a la operación de combinar una tabla consigo misma.
- Para lograr el self join se utilizan otros tipos de joins como INNER JOIN o LEFT JOIN.
#### **Self Join**
Un self join es un tipo de join en SQL que se utiliza para combinar una tabla consigo misma. Se usa cuando queremos relacionar filas de una tabla con otras filas de la misma tabla. Aunque el término "self join" se refiere a esta relación consigo misma, en la práctica se utilizan otros tipos de joins como INNER JOIN o LEFT JOIN para realizar esta operación.
#### **Ejemplo**
Supongamos que tenemos una tabla llamada empleados con la siguiente estructura:

|**ID\_EMPLEADO**|**NOMBRE**|**ID\_SUPERVISOR**|
| :- | :- | :- |
|1|Juan|NULL|
|2|María|1|
|3|Pedro|1|
|4|Ana|2|
|5|Luis|2|
#### **Uso del Self Join**
Para obtener el nombre de **todos** los empleados junto con el nombre de su supervisor, podemos usar un self join de la siguiente manera:

SELECT e1.nombre AS nombre\_empleado, e2.nombre AS nombre\_supervisor

FROM empleados e1

LEFT JOIN empleados e2 ON e1.id\_supervisor = e2.id\_empleado;

|**NOMBRE\_EMPLEADO**|**NOMBRE\_SUPERVISOR**|
| :- | :- |
|Juan|NULL|
|María|Juan|
|Pedro|Juan|
|Ana|María|
|Luis|María|

En este ejemplo, estamos obteniendo el nombre de cada empleado (e1.nombre) y el nombre de su supervisor (e2.nombre). El self join se realiza uniendo la tabla empleados consigo misma (empleados e1 LEFT JOIN empleados e2), utilizando la columna id\_supervisor de e1 y la columna id\_empleado de e2.

Se utiliza LEFT JOIN en lugar de INNER JOIN para incluir a los empleados que no tienen supervisor, dado que en la consulta nos pedían los nombres de **todos** los empleados.
#### **Ejercicio**
Se tiene la tabla clientes con los siguientes datos:

|**ID\_CLIENTE**|**NOMBRE**|**ID\_CLIENTE\_REFERENTE**|
| :- | :- | :- |
|1|Juan|NULL|
|2|María|1|
|3|Pedro|1|
|4|Ana|2|
|5|Luis|2|

Utilizando lo aprendido escribe una consulta que muestre el nombre de todos los clientes junto con el nombre de su cliente referente. Las columnas de la tabla resultante deben llamarse nombre\_cliente y nombre\_cliente\_referente.




SELECT e1.nombre AS nombre\_cliente, e2.nombre AS nombre\_cliente\_referente FROM clientes e1 LEFT JOIN clientes e2 ON e1.id\_cliente\_referente = e2.id\_cliente;




### **Self Join parte 2**
#### **Ideas clave**
- Un self join se utiliza para combinar una tabla consigo misma.
- Self join no es un tipo de join específico, es solo el término utilizado para referirse a la operación de combinar una tabla consigo misma.
- Para lograr el self join se utilizan otros tipos de joins como INNER JOIN o LEFT JOIN.
## **Ejercicio**
Se tiene la tabla amigos que contiene la información de amigos conectados en una red social.

|**ID\_AMIGO**|**NOMBRE**|**ID\_AMIGO\_CONECTADO**|
| :- | :- | :- |
|1|Carlos|NULL|
|2|Laura|1|
|3|Miguel|1|
|4|Ana|2|
|5|Luis|3|

Escribe una consulta SQL utilizando self join para obtener el nombre de cada amigo junto con el nombre de su amigo conectado. Solo se deben mostrar los amigos que tienen un amigo conectado. Las columnas de la tabla resultante deben llamarse nombre y nombre\_amigo\_conectado.

Tip 1: ¿Qué tipo de join utilizarías para obtener los amigos conectados? Tip 2: ¿Qué columnas de la tabla amigos se relacionan entre sí?



SELECT e1.nombre , e2.nombre AS nombre\_amigo\_conectado FROM amigos e1 inner JOIN amigos e2 ON e1.id\_amigo\_conectado = e2.id\_amigo;



### **Cross Join**
#### Ideas clave
- Cross Join genera el producto cartesiano de dos tablas.
- Cross Join no requiere una condición de unión, dado que combina todas las filas de la primera tabla con todas las filas de la segunda tabla.
#### Cross Join
El Cross Join, también conocido como producto cartesiano, combina cada fila de la primera tabla con cada fila de la segunda tabla, generando un conjunto de resultados que es el producto cartesiano de ambas tablas. Es útil cuando se desea combinar todas las filas de una tabla con todas las filas de otra tabla.

La sintaxis de Cross Join es la siguiente:

SELECT columnas

FROM tabla1

CROSS JOIN tabla2;
#### Ejemplo
Se tienen dos tablas, una de figuras geométricas y otra de colores. Se pide generar una consulta que muestre todas las figuras junto con todos los colores posibles.

Tabla **figuras**:

|**ID\_FIGURA**|**NOMBRE\_FIGURA**|
| :- | :- |
|1|Círculo|
|2|Cuadrado|
|3|Triángulo|

Tabla colores:

|**ID\_COLOR**|**NOMBRE\_COLOR**|
| :- | :- |
|1|Rojo|
|2|Verde|
|3|Azul|

La consulta SQL necesaria tendrá la siguiente estructura:

SELECT nombre\_figura, nombre\_color

from figuras

cross join colores;

El resultado será una tabla con todas las combinaciones posibles de figuras y colores:

|**NOMBRE\_FIGURA**|**NOMBRE\_COLOR**|
| :- | :- |
|Círculo|Rojo|
|Círculo|Verde|
|Círculo|Azul|
|Cuadrado|Rojo|
|Cuadrado|Verde|
|Cuadrado|Azul|
|Triángulo|Rojo|
|Triángulo|Verde|
|Triángulo|Azul|
#### Ejercicio
Se tiene una tabla de números y una tabla de pintas. Genera una consulta que muestre todos los números junto con todas las pintas posibles simulando una baraja de cartas ordenada por números de menor a mayor y las pintas en orden alfabético. Las columnas de la tabla resultante deben llamarse numero y pinta.

Tabla **numeros**:

|**NUMERO**|
| :- |
|1|
|2|
|3|
|4|
|5|
|6|
|7|
|8|
|9|
|10|
|11|
|12|
|13|

Tabla **pintas**:

|**PINTA**|
| :- |
|Corazones|
|Diamantes|
|Tréboles|
|Picas|



SELECT numero, pinta FROM numeros CROSS JOIN pintas ORDER BY numero, pinta;



### Join con funciones agregadas
#### **Ideas clave:**
- **Combinar datos de varias tablas**: La claúsula JOIN nos permite combinar filas de dos o más tablas.
- **Escoger el tipo de JOIN**: La elección del tipo de JOIN depende de si queremos contabilizar filas sin coincidencias, si es así usamos LEFT JOIN, si no usamos INNER JOIN.
- **Agrupar datos**: El uso de GROUP BY permite agrupar filas que tienen el mismo valor en una o más columnas.
- **Funciones de agregación**: Sobre datos agrupados, podemos utilizar funciones de agregación como SUM(), COUNT(), y AVG().
#### **¿Qué vamos a aprender?**
En estos ejercicios trabajaremos con problemas muy comunes en el análisis de datos, donde necesitamos combinar datos de varias tablas, agruparlos y obtener información de datos agregados. A lo largo de estos de estos ejercicios aprenderemos a identificar qué tipo de JOIN utilizar para cada caso.
#### **Escenario**
Se tiene una tabla de productos y una tabla de ventas. Se desea hacer una consulta que muestre cada producto con la cantidad de ventas realizadas.

tabla **productos**

|**ID**|**NOMBRE**|
| :- | :- |
|1|smartphone|
|2|tablet|
|3|camiseta|
|4|zapatos|

tabla **ventas** Para este primer ejercicio vamos a suponer que la tabla de ventas solo permite registrar la venta de un producto a la vez.

|**ID**|**ID\_PRODUCTO**|
| :- | :- |
|1|1|
|2|1|
|2|2|
|2|2|
|3|1|

Si miramos las ventas, veremos que el producto con id=1 se vendió 3 veces y el producto con id=2 se vendió 2 veces, y el resto no se ha vendido. Es decir, el resultado esperado sería:

|**NOMBRE**|**CANTIDAD\_VENTAS**|
| :- | :- |
|smartphone|3|
|tablet|2|
|camiseta|0|
|zapatos|0|

La solución a este ejercicio requiere de unir las tablas productos y ventas y agrupar los resultados por el nombre del producto para finalmente contar el número de ventas realizadas.

La pregunta importante es: ¿Qué tipo de JOIN deberíamos usar para este caso? ¿INNER JOIN o LEFT JOIN?

Para tomar la decisión, debemos considerar si queremos contabilizar productos sin ventas. Si queremos contabilizarlos, entonces deberíamos usar un LEFT JOIN. Si no queremos contabilizarlos, entonces deberíamos usar un INNER JOIN. En el ejemplo, la tabla del reporte muestra camisetas y zapatos que no han sido vendidos, por lo que deberíamos usar un LEFT JOIN.

SELECT p.nombre, COUNT(v.id) AS cantidad\_ventas

FROM productos p

LEFT JOIN ventas v ON p.id = v.id\_producto

GROUP BY p.nombre;
#### **Ejercicio**
Se tiene una tabla de usuarios y una tabla de notas. Se desea hacer una consulta que muestre la cantidad de notas que ha registrado cada usuario incluso si no ha registrado ninguna nota. Las columnas de las tablas deben ser email y cantidad\_notas.

Tabla **usuarios**

|**EMAIL**|**NOMBRE**|
| :- | :- |
|<juan.perez@example.com>|Juan Pérez|
|<maria.gonzalez@example.com>|Maria González|
|<john.doe@example.com>|John Doe|
|<francisco@example.com>|Test User|

Tabla **notas**

|**EMAIL**|**NOTAS**|
| :- | :- |
|<juan.perez@example.com>|90|
|<maria.gonzalez@example.com>|100|
|<john.doe@example.com>|80|
|<juan.perez@example.com>|100|
|<maria.gonzalez@example.com>|100|

sELECT u.email, COUNT(n.notas) AS cantidad\_notas 

FROM usuarios u LEFT JOIN notas n ON u.email = n.email GROUP BY u.email 

ORDER BY u.nombre asc;




### Introducción a la primera forma normal
#### **Ideas clave**
- La redundancia en una base de datos puede llevar a inconsistencias a la hora de identificar el dato correcto, actualizarlo o eliminarlo.
- La normalización es un proceso de eliminación de redundancia en una base de datos
#### **¿Qué es la normalización?**
La normalización es un proceso de eliminación de redundancia en una base de datos con el objetivo de prevenir inconsistencias. Este proceso consta de diversas etapas que, al aplicarse correctamente, permiten que la base de datos sea más eficiente y fácil de mantener. Cada una de estas etapas recibe el nombre de formas normales.
#### **Primera forma normal**
En la primera forma normal se busca que cada registro sea identificable de forma única en una tabla. Veamos un ejemplo de una tabla que no cumple con la primera forma normal:

|**NOMBRE**|**APELLIDO**|**ESTADO CIVIL**|
| :- | :- | :- |
|Juan|Pérez|Casado|
|María|González|Soltera|
|Pedro|Rodríguez|Casado|
|Juan|Pérez|Soltero|
|María|González|Viuda|
|Pedro|Rodríguez|Soltero|
|Juan|Pérez|Divorciado|
|María|González|Soltera|
|Pedro|Rodríguez|Casado|

En esta tabla, si preguntamos por el estado civil de Juan Pérez, no sabríamos cuál es el correcto. Además, ¿es Juan Pérez una persona o son personas distintas y es una coincidencia que tengan el mismo nombre y apellido? Este es uno de los problemas que se busca solucionar con la primera forma normal.
#### **Ejercicio**
Supongamos que cada combinación de nombre y apellido de la tabla **personas**, previamente descrita, corresponde a una única persona, y el último registro de cada persona es el correcto. Borra los registros incorrectos.

Hay formas de hacerlo automático, pero puedes simplemente borrar los registros incorrectos uno por uno separando las consultas con punto y coma. Es un trabajo tedioso, pero no olvidarás la lección de tener tablas que cumplan con la primera forma normal.

Una forma

delete from personas where nombre = 'Juan' and apellido = 'Pérez' and "ESTADO CIVIL"='Casado';

delete from personas where nombre = 'María' and apellido = 'González' and "ESTADO CIVIL"= 'Soltera';

delete from personas where nombre = 'Pedro' and apellido = 'Rodríguez' and "ESTADO CIVIL"= 'Casado';

delete from personas where nombre = 'Juan' and apellido = 'Pérez' and "ESTADO CIVIL"= 'Soltero';

delete from personas where nombre = 'María' and apellido = 'González' and "ESTADO CIVIL"= 'Viuda';

delete from personas where nombre = 'Pedro' and apellido = 'Rodríguez' and "ESTADO CIVIL"= 'Soltero';

**Todas las personas no repetidas**

DELETE FROM personas WHERE ID NOT IN ( SELECT MAX(ID) FROM personas GROUP BY nombre, apellido );

**solo el último registro de Juan**

DELETE FROM personas WHERE ID NOT IN ( SELECT MAX(ID) FROM personas where nombre = 'Juan' GROUP BY nombre, apellido ) ;




### Conviertiendo a 1fn
#### **Ideas clave**
- La redundancia en una base de datos puede llevar a inconsistencias a la hora de identificar el dato correcto, actualizarlo o eliminarlo.
- La normalización es un proceso de eliminación de redundancia en una base de datos
- En primera forma normal debería haber una clave primaria que identifique de forma única a cada registro en una tabla.
#### **Primera forma normal**
En la primera forma normal, denotada como **1fn**, se busca que cada registro sea identificable de forma única en una tabla. Veamos un ejemplo de una tabla que no cumple con la primera forma normal:

|**NOMBRE**|**APELLIDO**|**ESTADO CIVIL**|
| :- | :- | :- |
|Juan|Pérez|Casado|
|María|González|Soltera|
|Pedro|Rodríguez|Casado|
|Juan|Pérez|Soltero|
|María|González|Viuda|
|Pedro|Rodríguez|Soltero|
|Juan|Pérez|Divorciado|
|María|González|Soltera|
|Pedro|Rodríguez|Casado|

En esta ocasión vamos a suponer que cada combinación de nombre y apellido de la tabla **personas** corresponde a una única persona, por lo tanto Juan Pérez con estado civil Casado, Soltero y Divorciado, son personas distintas. Para convertir esta tabla en primera forma normal agregaremos una clave primaria que identifique de forma única a cada registro.

En SQLite no podemos agregar una clave primaria a una tabla que ya tiene datos, por lo que tendremos que crear una nueva tabla con la clave primaria y luego insertar los datos de la tabla original en la nueva t




CREATE TABLE personas2 (

`  `id INTEGER PRIMARY KEY AUTOINCREMENT,

`  `nombre TEXT NOT NULL,

`  `apellido TEXT NOT NULL,

`  `estado\_civil TEXT NOT NULL

);

/\* Seleccionamos los datos de personas y lo insertamos en personas2 \*/

INSERT INTO personas2 (nombre, apellido, estado\_civil)

SELECT nombre, apellido, estado\_civil

FROM personas;

/\* Borramos la tabla personas \*/

DROP TABLE personas;

/\* Renombramos la tabla personas2 a personas \*/

ALTER TABLE personas2 RENAME TO personas;


Esto dará como resultado la siguiente tabla:

|**ID**|**NOMBRE**|**APELLIDO**|**ESTADO CIVIL**|
| :- | :- | :- | :- |
|1|Juan|Pérez|Soltero|
|2|María|González|Casada|
|3|Pedro|Rodríguez|Divorciado|
|4|Juan|Pérez|Casado|
|5|María|González|Soltera|
|6|Pedro|Rodríguez|Casado|
|7|Juan|Pérez|Soltero|
|8|María|González|Viuda|
|9|Pedro|Rodríguez|Soltero|
|10|Juan|Pérez|Divorciado|
|11|María|González|Soltera|
|12|Pedro|Rodríguez|Casado|




#### Ejercicio
En el ejercicio anterior descubrimos los problemas que puede traer una tabla que no tiene clave primaria, al no poder identificar de forma única a cada registro.

Se tiene la siguiente tabla de **productos**

|**PRODUCTO**|**CATEGORÍA**|**PRECIO**|
| :- | :- | :- |
|Manzana|Fruta|0\.50|
|Pan|Panadería|1\.00|
|Leche|Lácteos|1\.20|
|Manzana|Fruta|0\.55|
|Pan|Panadería|1\.10|
|Queso|Lácteos|2\.50|

Los productos que aperecen en la tabla aunque tengan el mismo nombre, son productos distintos. Se pide agregar una clave primaria a la tabla que identifique de forma única a cada producto.

Ten en cuenta que no puedes agregar una clave primaria a una tabla que ya tiene datos, por lo que tendrás que crear una nueva tabla con la clave primaria y luego insertar los datos de la tabla original en la nueva tabla.


CREATE TABLE productos2 ( ID INTEGER PRIMARY KEY AUTOINCREMENT, PRODUCTO TEXT NOT NULL, "Categoría" TEXT NOT NULL, PRECIO REAL NOT NULL ); 

/\* Inserta los datos desde la tabla original \*/

INSERT INTO productos2 (producto, "Categoría", precio) SELECT producto, "Categoría", precio FROM productos;

/\* Elimina la tabla original \*/ DROP TABLE productos; /\* Renombra la nueva tabla \*/

ALTER TABLE productos2 RENAME TO productos; /\* Consulta para verificar los resultados \*/ 

SELECT id AS "ID", producto AS "PRODUCTO", "Categoría" AS "CATEGORÍA", precio AS "PRECIO" FROM productos;



### Grupos repetitivos
#### **Ideas clave**
- La redundancia en una base de datos puede llevar a inconsistencias a la hora de identificar el dato correcto, actualizarlo o eliminarlo.
- La normalización es un proceso de eliminación de redundancia en una base de datos
- En primera forma normal debería haber una clave primaria que identifique de forma única a cada registro en una tabla.
- Los grupos repetitivos son un indicio de que una tabla no cumple con la primera forma normal.
#### **¿Qué son los grupos repetitivos?**
Los grupos repetitivos son un conjunto de campos que se repiten en una tabla. Por ejemplo, si en una tabla se tienen los campos telefono1, telefono2 y telefono3, se podría considerar que estos campos forman un grupo repetitivo.

|**ID**|**NOMBRE**|**APELLIDO**|**TELEFONO1**|**TELEFONO2**|**TELEFONO3**|
| :- | :- | :- | :- | :- | :- |
|1|Juan|Pérez|12345678|87654321|45678912|
|2|María|González|23456789|98765432|56789123|

Existen diversos problemas asociados a los grupos repetitivos, pero en este caso puntual hay dos problemas evidentes:

1. ¿Qué pasa si una persona tiene más de tres teléfonos? ¿Se debería modificar la tabla para agregar un campo telefono4, telefono5, etc.? ¿Cuál es el límite?
1. Si la mayoría de las personas solo tienen un teléfono, ¿cómo se maneja la información de los campos telefono2 y telefono3? ¿Se dejan en blanco? ¿Se les asigna un valor nulo? Probablemente terminemos con una gran cantidad de campos vacíos.

Resolver el problema de los grupos repetitivos es un paso importante en la normalización de una base de datos. En este caso, se podría crear una tabla telefonos que contenga los teléfonos de las personas y se relacione con la tabla personas, quedando de la siguiente manera:

tabla **personas**:

|**ID**|**NOMBRE**|**APELLIDO**|
| :- | :- | :- |
|1|Juan|Pérez|
|2|María|González|

tabla **telefonos**:

|**ID\_PERSONA**|**TELEFONO**|
| :- | :- |
|1|12345678|
|1|87654321|
|1|45678912|
|2|23456789|
|2|98765432|
|2|56789123|

De esta forma, se puede tener un número arbitrario de teléfonos por persona sin necesidad de modificar la estructura de la tabla personas.
#### **Ejercicio**
Dada la siguiente tabla, identifica los grupos repetitivos y propón una solución para normalizar la tabla.

tabla **empleados\_desnormalizado**:

|**ID**|**NOMBRE**|**APELLIDO**|**PROYECTO1**|**PROYECTO2**|**PROYECTO3**|
| :- | :- | :- | :- | :- | :- |
|1|Juan|Pérez|1|2|3|

1. Identifica los grupos repetitivos en la tabla empleados\_desnormalizado.
1. Crea las tablas **empleados** y **proyectos** en primera forma normal para que permitan almacenar la información de los empleados y los proyectos en una estructura normalizada.
1. Ingresa la información de la tabla empleados\_desnormalizado en las tablas normalizadas.

Crea una consulta que muestre la información de los empleados y los proyectos a los que están asignados en una estructura normalizada. Las columnas de la consulta deben ser nombre, apellido y id\_proyecto.

CREATE TABLE empleados ( id INTEGER PRIMARY KEY AUTOINCREMENT, nombre TEXT, apellido TEXT );

CREATE TABLE proyectos ( id\_proyecto INTEGER, id\_empleado INTEGER, PRIMARY KEY (id\_proyecto, id\_empleado) );

INSERT INTO empleados (nombre, apellido) VALUES ('Juan', 'Pérez'); 

INSERT INTO proyectos (id\_proyecto, id\_empleado) VALUES (1, 1), (2, 1), (3, 1); 

SELECT e.nombre, e.apellido, p.id\_proyecto FROM empleados e 

INNER JOIN proyectos p ON e.id = p.id\_empleado; 




### Grupos repetitivos parte 2
#### **Ideas clave**
- La redundancia en una base de datos puede llevar a inconsistencias a la hora de identificar el dato correcto, actualizarlo o eliminarlo.
- La normalización es un proceso de eliminación de redundancia en una base de datos
- En primera forma normal debería haber una clave primaria que identifique de forma única a cada registro en una tabla.
- Los grupos repetitivos son un indicio de que una tabla no cumple con la primera forma normal.
- Hay más de un forma de tener grupos repetitivos en una tabla
#### **Grupos repetitivos**
Los grupos repetitivos son conjuntos de campos que se repiten dentro de una tabla. Sin embargo, existen varias formas en las que estos grupos repetitivos pueden aparecer en una tabla.

En el ejercicio anterior, se vio un ejemplo de un grupo repetitivo en el que se tenían varios campos con el mismo propósito. Por ejemplo: telefono1, telefono2 y telefono3. Otra forma de tener grupos repetitivos es tener varios valores en un solo campo.

|**ID**|**NOMBRE COMPLETO**|**TELÉFONOS**|
| :- | :- | :- |
|1|Juan Pérez|+56 9 1234 5678, +56 2 2345 6789, +56 9 8765 4321|
|2|Pedro Rodríguez|+56 9 4321 9876, +56 2 6789 5432|
|3|Ana López|+56 9 8765 2345, +56 2 4321 1987, +56 9 6789 5432|

Los problema asociados a esta forma de grupos repetitivos son distintos:

- Al modificar el teléfono de una persona, se debe modificar el campo Teléfonos que tiene varios registros y podríamos olvidar alguno o pasarlo a llevar por error.
- Al tener los datos almacenados de esta forma es difícil saber cuanto teléfonos tiene cada persona.
- Los teléfonos podrían tener distintos formatos y sería difícil establecer una restricción para que todos los teléfonos tengan el mismo formato.
- Verificar si el mismo teléfono está asignado a más de una persona también se vuelve más complicado que al tener la tabla desnormalizada.

Por ejemplo, si quisiéramos contar la cantidad de teléfonos de cada persona, podríamos contar la cantidad de símbolos + en el campo Teléfonos. Para lograr esto, podemos calcular la cantidad total de caracteres en el campo Teléfonos y restarle la cantidad de caracteres en el mismo campo después de eliminar los símbolos +.

SELECT

`    `id,

`    `nombre\_completo,

`    `LENGTH(telefonos) - LENGTH(REPLACE(telefonos, '+', '')) AS cantidad\_telefonos

FROM

`    `personas;

Como se observa, es mucho más complicado que simplemente contar los registros de una tabla.
#### **Ejercicio**
Se tiene la tabla **pedidos** que tiene una columna id y otra columna productos. Se pide que cuentes la cantidad de productos que tiene cada pedido en esta tabla no normalizada.

|**ID**|**PRODUCTOS**|
| :- | :- |
|1|producto1 producto2 producto3|
|2|producto4 producto5|
|3||
|4|producto6 producto7 producto8 producto9 producto10|
|5|producto11|

Para simplificar el problema dentro de la tabla de sql, los productos están separados por un espacio y no hay espacios al principio ni al final de la cadena.

--SELECT id, productos, CASE WHEN TRIM(productos) = '' THEN 0 ELSE LENGTH(TRIM(productos)) - LENGTH(REPLACE(TRIM(productos), ' ', '')) + 1 END AS cantidad\_productos FROM pedidos;




SELECT id, productos, LENGTH(PRODUCTOS) - LENGTH(REPLACE(PRODUCTOS, ' ', '')) + 1 FROM pedidos;



### Grupos repetitivos parte 3
#### **Ideas clave**
- Los grupos repetitivos son un indicio de que una tabla no cumple con la primera forma normal.
- Hay grupos repetitivos cuando tienes columnas que se repiten en una tabla, ejemplo: proyecto1, proyecto2, proyecto3.
- Hay grupos repetitivos cuando tienes dentro de un campo varios valores, ejemplo: producto1 producto2 producto3.
- Finalmente hay grupos repetitivos cuando tienes columnas que se repiten en varias filas, ejemplo: nombre, `apellido

Veamos por ejemplo la tabla departamentos:

|**NOMBRE\_DEPARTAMENTO**|**NOMBRE\_PERSONA**|**APELLIDO\_PERSONA**|
| :- | :- | :- |
|Recursos Humanos|Ana|Pérez|
|TI|Pedro|Rodríguez|
|TI|Luis|González|
|Marketing|Marta|López|
|Marketing|Elena|Pérez|

La tabla anterior, aunque sea un poco más difícil de evidenciar, también tiene grupos repetitivos. Dado que nombre\_departamento se repite en varias filas para distintas personas.

Por ejemplo esto mismo podría estar como

|**NOMBRE\_DEPARTAMENTO**|**PERSONAS**|
| :- | :- |
|Recursos Humanos|Ana Pérez|
|TI|Pedro Rodríguez, Luis González|
|Marketing|Marta López, Elena Pérez|

O como:

|**NOMBRE\_DEPARTAMENTO**|**NOMBRE PERSONA 1**|**NOMBRE PERSONA 2**|**NOMBRE PERSONA 3**|
| :- | :- | :- | :- |
|Recursos Humanos|Ana|||
|TI|Pedro|Luis||
|Marketing|Marta|Elena||
Los problemas asociados a los grupos repetitivos son similares a los que se presentan en los ejercicios anteriores.

- Si se quiere cambiar el nombre de un departamento, se tendría que cambiar en todas las filas que correspondan a ese departamento.
- O un departamento podría quedar escrito de distintas formas, por ejemplo, TI, T.I., Tecnologías de la Información, etc. Y sería difícil establecer una restricción para que todos los departamentos tengan el mismo nombre.

Para eliminar los grupos repetitivos de esta tabla, se debe crear una nueva tabla Personas separada de la tabla Departamentos que relacione a las personas con los departamentos.

Deparamentos:

|**ID**|**NOMBRE\_DEPARTAMENTO**|
| :- | :- |
|1|Recursos Humanos|
|2|TI|
|3|Marketing|

Personas:

|**ID**|**NOMBRE\_PERSONA**|**APELLIDO\_PERSONA**|**DEPARTAMENTO\_ID**|
| :- | :- | :- | :- |
|1|Ana|Pérez|1|
|2|Pedro|Rodríguez|2|
|3|Luis|González|2|
|4|Marta|López|3|
|5|Elena|Pérez|3|
#### **Ejercicio Didáctico**
Con las tablas normalizadas de Departamentos y Personas. Muestra todos los departamentos y cuántas personas trabajan en cada uno. Las columnas deben llamarse nombre\_departamento y cantidad\_personas.

select NOMBRE\_DEPARTAMENTO as nombre\_departamento , count(p.DEPARTAMENTO\_ID) as cantidad\_personas

from departamentos d

inner join personas p on d.id= p.DEPARTAMENTO\_ID

group by p.DEPARTAMENTO\_ID

order by d.nombre\_departamento;



### Dependencias parciales
#### **Ideas clave**
- La redundancia en una base de datos puede llevar a inconsistencias a la hora de identificar el dato correcto, actualizarlo o eliminarlo.
- La normalización es un proceso de eliminación de redundancia en una base de datos
- En primera forma normal debe haber una clave primaria que identifique de forma única a cada registro en una tabla.
- En la segunda forma normal no deben existir dependencias parciales, o sea que cada columna de una tabla debe depender de la clave primaria completa y no de una parte de ella.
#### **Dependencias parciales**
Una dependencia parcial es cuando una columna depende de solo una parte de la clave primaria. Esto por supuesto solo aplica a tablas con claves primarias compuestas.

Veamos un ejemplo de una tabla que tiene dependencias parciales:

Se tiene un sistema de registro de notas guardado en una única tabla llamada **notas**. La tabla tiene la siguiente estructura:

|**ID DE ESTUDIANTE**|**ID DE CURSO**|**NOMBRE DEL ESTUDIANTE**|**NOMBRE DEL CURSO**|**NOTA**|
| :- | :- | :- | :- | :- |
|1|101|Juan|Matemáticas|90|
|1|102|Juan|Historia|85|
|2|101|Ana|Matemáticas|95|
|2|103|Ana|Ciencia|88|

En esta tabla tenemos una clave primaria compuesta por ID de estudiante e ID de curso. Esta combinación de columnas identifica de manera única a cada fila, dado que para este ejemplo un estudiante no puede estar en el mismo curso dos veces.

Las dependencias parciales ocurren cuando un campo como Nombre del estudiante depende solo de ID de estudiante y no de ID de curso. O sea depende de una parte de la clave primaria y no de la clave primaria completa, por lo mismo se le llama dependencia parcial.
#### **¿Por qué es importante eliminar las dependencias parciales?**
Las dependencias parciales pueden causar problemas de actualización y eliminación de datos. Por ejemplo, si se cambia el nombre de un estudiante, se tendría que cambiar en todas las filas que correspondan a ese estudiante. O si se elimina un estudiante, se perdería la información de las notas asociadas a ese estudiante.
#### **Eliminar dependencias parciales**
Para llegar a la segunda forma normal (2FN) se deben identificar todas las dependencias parciales.

- Nombre del estudiante es parcial porque depende solo de ID de estudiante y no de la clave primaria completa
- Nombre del curso es parcial porque depende solo de ID de curso y no de la clave primaria completa

El siguiente paso es separar la tabla **notas** en dos tablas adicionales, una para los estudiantes y otra para los cursos.

Tabla **estudiantes**

|**ID\_DE\_ESTUDIANTE**|**NOMBRE\_DEL\_ESTUDIANTE**|
| :- | :- |
|1|Juan|
|2|Ana|

Tabla **cursos**

|**ID\_DE\_CURSO**|**NOMBRE\_DEL\_CURSO**|
| :- | :- |
|101|Matemáticas|
|102|Historia|
|103|Ciencia|

Luego se debe eliminar las columnas Nombre del estudiante y Nombre del curso de la tabla **notas** y agregar las claves foráneas ID de estudiante e ID de curso respectivamente.

Tabla **notas**

|**ID\_DE\_ESTUDIANTE**|**ID\_DE\_CURSO**|**NOTA**|
| :- | :- | :- |
|1|101|90|
|1|102|85|
|2|101|95|
|2|103|88|
#### **Ejercicio:**
Dada las tablas **estudiantes** y **cursos** y **notas** normalizadas, crea una consulta que muestre el nombre del estudiante, el nombre del curso y la nota que ha obtenido cada estudiante en cada curso. Las columnas deben llamarse nombre\_estudiante, nombre\_curso y nota.


SELECT e.NOMBRE\_DEL\_ESTUDIANTE, c.NOMBRE\_DEL\_CURSO, n.nota 

FROM estudiantes e INNER JOIN notas n ON e.ID\_de\_estudiante = n.ID\_de\_estudiante 

INNER JOIN cursos c ON n.ID\_de\_curso = c.ID\_de\_curso;



### Dependencias transitivas
#### **Ideas clave**
- La redundancia en una base de datos puede llevar a inconsistencias a la hora de identificar el dato correcto, actualizarlo o eliminarlo.
- La normalización es un proceso de eliminación de redundancia en una base de datos
- En primera forma normal debe haber una clave primaria que identifique de forma única a cada registro en una tabla.
- En la segunda forma normal no deben existir dependencias parciales, o sea que cada columna de una tabla debe depender de la clave primaria completa y no de una parte de ella.
- En la tercera forma normal no deben existir dependencias transitivas, o sea que una columna no puede depender de otra que no sea la clave primaria.
### **Qué son las dependencias transitivas**
Las dependencias transitivas ocurren cuando una columna depende de otra que no es la clave primaria de manera indirecta. En otras palabras, si la columna A depende de la columna B y la columna B depende de la clave primaria, entonces la columna A depende transitivamente de la clave primaria.

Por ejemplo, consideremos la siguiente tabla **Peliculas**:

|**ID**|**PELÍCULA**|**DIRECTOR**|**NACIONALIDAD DIRECTOR**|
| :- | :- | :- | :- |
|1|El Padrino|Francis Ford Coppola|Estadounidense|
|2|Ciudad de Dios|Fernando Meirelles|Brasileño|
|3|El Laberinto del Fauno|Guillermo del Toro|Mexicano|
|4|Amélie|Jean-Pierre Jeunet|Francés|
|5|Parasite|Bong Joon-ho|Coreano|

En esta tabla, podemos observar que la columna Nacionalidad Director depende de la columna Director. A su vez, Director depende de la clave primaria ID. Por lo tanto, Nacionalidad Director depende indirectamente de la clave primaria ID, lo que implica que hay una dependencia transitiva.

Este tipo de dependencia es importante de identificar y gestionar, especialmente en el contexto de la normalización de bases de datos, para evitar redundancias y asegurar la integridad de los datos.
### **Ejercicio**
A partir de la siguiente tabla en 2FN, llamada Músicos, identifica las dependencias transitivas y propón una solución para normalizarla:

|**ID**|**PAIS**|**MUSICO**|**EDAD\_MUSICO**|
| :- | :- | :- | :- |
|1|Estados Unidos|Beyoncé|42|
|2|Brasil|Gilberto Gil|81|
|3|Francia|David Guetta|56|
|4|India|A. R. Rahman|57|
|5|Corea del Sur|RM|29|

Las tablas normalizadas deberían ser paises y musicos . Manten los nombres de los músicos y países en la tabla musicos. La claves primarias deben llamarse id en ambas tablas y la clave foránea debe llamarse pais\_id.

Ingresa los datos normalizados en las tablas correspondientes.

CREATE TABLE paises ( id INTEGER PRIMARY KEY AUTOINCREMENT, pais TEXT );

CREATE TABLE musicos ( id INTEGER PRIMARY KEY AUTOINCREMENT, pais\_id INTEGER, musico TEXT, edad\_musico INTEGER, FOREIGN KEY (pais\_id) REFERENCES paises(id) ); 

INSERT INTO paises (id, pais) VALUES (1, 'Estados Unidos'), (2, 'Brasil'), (3, 'Francia'), (4, 'India'), (5, 'Corea del Sur'); 

INSERT INTO musicos (musico, edad\_musico, pais\_id) VALUES ('Beyoncé', 42, 1), ('Gilberto Gil', 81, 2), ('David Guetta', 56, 3), ('A. R. Rahman', 57, 4), ('RM', 29, 5);


\*\*\*\*\*

CREATE TABLE paises (

id INT PRIMARY KEY,

pais TEXT NOT NULL

);

INSERT INTO paises (id, pais) VALUES

(1, 'Estados Unidos'),

(2, 'Brasil'),

(3, 'Francia'),

(4, 'India'),

(5, 'Corea del Sur');

CREATE TABLE musicos (

id INT PRIMARY KEY,

musico TEXT NOT NULL,

edad\_musico INT NOT NULL,

pais\_id INT NOT NULL,

FOREIGN KEY (pais\_id) REFERENCES paises(id)

);

INSERT INTO musicos (id, musico, edad\_musico, pais\_id) VALUES

(1, 'Beyoncé', 42, 1),

(2, 'Gilberto Gil', 81, 2),

(3, 'David Guetta', 56, 3),

(4, 'A. R. Rahman', 57, 4),

(5, 'RM', 29, 5);

SELECT p.id, p.pais

FROM paises p

JOIN musicos m ON p.id = m.pais\_id;


