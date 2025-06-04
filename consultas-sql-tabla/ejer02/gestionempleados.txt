-- 1. Lista el primer apellido de todos los empleados.
SELECT apellido1 FROM empleado;

-- 2. Lista el primer apellido de los empleados eliminando los apellidos que estén repetidos.
SELECT DISTINCT apellido1 FROM empleado;

-- 3. Lista todas las columnas de la tabla empleado.
SELECT * FROM empleado;

-- 4. Lista el nombre y los apellidos de todos los empleados.
SELECT nombre, apellido1, apellido2 FROM empleado;

-- 5. Lista el identificador de los departamentos de los empleados que aparecen en la tabla empleado.
SELECT id_departamento FROM empleado;

-- 6. Lista el identificador de los departamentos de los empleados que aparecen en la tabla empleado, eliminando los identificadores que aparecen repetidos.
SELECT DISTINCT id_departamento FROM empleado;

-- 7. Lista el nombre y apellidos de los empleados en una única columna.
SELECT CONCAT_WS(' ', nombre, apellido1, apellido2) AS nombre_completo FROM empleado;

-- 8. Lista el nombre y apellidos en mayúsculas.
SELECT UPPER(CONCAT_WS(' ', nombre, apellido1, apellido2)) AS nombre_completo FROM empleado;

-- 9. Lista el nombre y apellidos en minúsculas.
SELECT LOWER(CONCAT_WS(' ', nombre, apellido1, apellido2)) AS nombre_completo FROM empleado;

-- 10. Lista el id de empleados y NIF separado en dígitos y letra.
SELECT id, LEFT(nif, 8) AS digitos_nif, RIGHT(nif, 1) AS letra_nif FROM empleado;

-- 11. Lista el nombre del departamento y presupuesto actual (presupuesto - gastos).
SELECT nombre, (presupuesto - gastos) AS presupuesto_actual FROM departamento;

-- 12. Lista departamentos y presupuesto actual ordenado ascendentemente.
SELECT nombre, (presupuesto - gastos) AS presupuesto_actual 
FROM departamento 
ORDER BY presupuesto_actual ASC;

-- 13. Lista nombres de departamentos ordenados ascendentemente.
SELECT nombre FROM departamento ORDER BY nombre ASC;

-- 14. Lista nombres de departamentos ordenados descendentemente.
SELECT nombre FROM departamento ORDER BY nombre DESC;

-- 15. Lista apellidos y nombre de empleados ordenados por apellidos y nombre.
SELECT apellido1, apellido2, nombre 
FROM empleado 
ORDER BY apellido1, apellido2, nombre;

-- 16. Top 3 departamentos con mayor presupuesto.
SELECT nombre, presupuesto 
FROM departamento 
ORDER BY presupuesto DESC 
LIMIT 3;

-- 17. Top 3 departamentos con menor presupuesto.
SELECT nombre, presupuesto 
FROM departamento 
ORDER BY presupuesto ASC 
LIMIT 3;

-- 18. Top 2 departamentos con mayor gasto.
SELECT nombre, gastos 
FROM departamento 
ORDER BY gastos DESC 
LIMIT 2;

-- 19. Top 2 departamentos con menor gasto.
SELECT nombre, gastos 
FROM departamento 
ORDER BY gastos ASC 
LIMIT 2;

-- 20. 5 filas a partir de la tercera (incluyéndola).
SELECT * FROM empleado LIMIT 2, 5;

-- 21. Departamentos con presupuesto >= 150000.
SELECT nombre, presupuesto 
FROM departamento 
WHERE presupuesto >= 150000;

-- 22. Departamentos con gastos < 5000.
SELECT nombre, gastos 
FROM departamento 
WHERE gastos < 5000;

-- 23. Presupuesto entre 100k y 200k (sin BETWEEN).
SELECT nombre, presupuesto 
FROM departamento 
WHERE presupuesto >= 100000 AND presupuesto <= 200000;

-- 24. Presupuesto no entre 100k y 200k (sin BETWEEN).
SELECT nombre, presupuesto 
FROM departamento 
WHERE presupuesto < 100000 OR presupuesto > 200000;

-- 25. Presupuesto entre 100k y 200k (con BETWEEN).
SELECT nombre, presupuesto 
FROM departamento 
WHERE presupuesto BETWEEN 100000 AND 200000;

-- 26. Presupuesto no entre 100k y 200k (con NOT BETWEEN).
SELECT nombre, presupuesto 
FROM departamento 
WHERE presupuesto NOT BETWEEN 100000 AND 200000;

-- 27. Departamentos donde gastos > presupuesto.
SELECT nombre, gastos, presupuesto 
FROM departamento 
WHERE gastos > presupuesto;

-- 28. Departamentos donde gastos < presupuesto.
SELECT nombre, gastos, presupuesto 
FROM departamento 
WHERE gastos < presupuesto;

-- 29. Departamentos donde gastos = presupuesto.
SELECT nombre, gastos, presupuesto 
FROM departamento 
WHERE gastos = presupuesto;

-- 30. Empleados con segundo apellido NULL.
SELECT * FROM empleado WHERE apellido2 IS NULL;

-- 31. Empleados con segundo apellido NO NULL.
SELECT * FROM empleado WHERE apellido2 IS NOT NULL;

-- 32. Empleados con apellido2 'López'.
SELECT * FROM empleado WHERE apellido2 = 'López';

-- 33. Empleados con apellido2 Díaz o Moreno (sin IN).
SELECT * FROM empleado 
WHERE apellido2 = 'Díaz' OR apellido2 = 'Moreno';

-- 34. Empleados con apellido2 Díaz o Moreno (con IN).
SELECT * FROM empleado 
WHERE apellido2 IN ('Díaz', 'Moreno');

-- 35. Empleados del departamento 3.
SELECT nombre, apellido1, apellido2, nif 
FROM empleado 
WHERE id_departamento = 3;

-- 36. Empleados de los departamentos 2, 4 o 5.
SELECT nombre, apellido1, apellido2, nif 
FROM empleado 
WHERE id_departamento IN (2, 4, 5);