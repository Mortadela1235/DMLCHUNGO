-- 1. Lista el nombre de todos los productos que hay en la tabla producto.
SELECT nombre FROM producto;

-- 2. Lista los nombres y los precios de todos los productos de la tabla producto.
SELECT nombre, precio FROM producto;

-- 3. Lista todas las columnas de la tabla producto.
SELECT * FROM producto;

-- 4. Lista el nombre de los productos, el precio en euros y el precio en dólares (USD).
SELECT nombre, precio AS euros, ROUND(precio * 1.08, 2) AS dólares FROM producto;

-- 5. Mismo que el anterior con alias específicos.
SELECT nombre AS 'nombre de producto', precio AS euros, ROUND(precio * 1.08, 2) AS dólares FROM producto;

-- 6. Nombres en mayúsculas y precios.
SELECT UPPER(nombre) AS nombre, precio FROM producto;

-- 7. Nombres en minúsculas y precios.
SELECT LOWER(nombre) AS nombre, precio FROM producto;

-- 8. Nombre del fabricante y dos primeros caracteres en mayúsculas.
SELECT nombre, UPPER(LEFT(nombre, 2)) AS iniciales FROM fabricante;

-- 9. Nombres y precios redondeados.
SELECT nombre, ROUND(precio) AS precio_redondeado FROM producto;

-- 10. Nombres y precios truncados sin decimales.
SELECT nombre, TRUNCATE(precio, 0) AS precio_truncado FROM producto;

-- 11. Identificadores de fabricantes con productos (con repeticiones).
SELECT id_fabricante FROM producto;

-- 12. Identificadores de fabricantes con productos (sin repeticiones).
SELECT DISTINCT id_fabricante FROM producto;

-- 13. Nombres de fabricantes ordenados ascendentemente.
SELECT nombre FROM fabricante ORDER BY nombre ASC;

-- 14. Nombres de fabricantes ordenados descendentemente.
SELECT nombre FROM fabricante ORDER BY nombre DESC;

-- 15. Productos ordenados por nombre (asc) y precio (desc).
SELECT nombre, precio FROM producto ORDER BY nombre ASC, precio DESC;

-- 16. Primeras 5 filas de fabricante.
SELECT * FROM fabricante LIMIT 5;

-- 17. 2 filas a partir de la cuarta (incluyéndola).
SELECT * FROM fabricante LIMIT 3, 2; -- Offset 3 (cuarta fila), 2 filas.

-- 18. Producto más barato.
SELECT nombre, precio FROM producto ORDER BY precio ASC LIMIT 1;

-- 19. Producto más caro.
SELECT nombre, precio FROM producto ORDER BY precio DESC LIMIT 1;

-- 20. Productos del fabricante con id 2.
SELECT nombre FROM producto WHERE id_fabricante = 2;

-- 21. Productos con precio ≤120€.
SELECT nombre FROM producto WHERE precio <= 120;

-- 22. Productos con precio ≥400€.
SELECT nombre FROM producto WHERE precio >= 400;

-- 23. Productos que NO tienen precio ≥400€.
SELECT nombre FROM producto WHERE precio < 400;

-- 24. Productos con precio entre 80€ y 300€ (sin BETWEEN).
SELECT nombre FROM producto WHERE precio >= 80 AND precio <= 300;

-- 25. Productos con precio entre 60€ y 200€ (con BETWEEN).
SELECT nombre FROM producto WHERE precio BETWEEN 60 AND 200;

-- 26. Productos con precio >200€ y fabricante 6.
SELECT nombre FROM producto WHERE precio > 200 AND id_fabricante = 6;

-- 27. Productos de fabricantes 1, 3 o 5 (sin IN).
SELECT nombre FROM producto WHERE id_fabricante = 1 OR id_fabricante = 3 OR id_fabricante = 5;

-- 28. Productos de fabricantes 1, 3 o 5 (con IN).
SELECT nombre FROM producto WHERE id_fabricante IN (1, 3, 5);

-- 29. Precios en céntimos.
SELECT nombre, precio * 100 AS centimos FROM producto;

-- 30. Fabricantes cuyo nombre empieza por 'S'.
SELECT nombre FROM fabricante WHERE nombre LIKE 'S%';

-- 31. Fabricantes cuyo nombre termina en 'e'.
SELECT nombre FROM fabricante WHERE nombre LIKE '%e';

-- 32. Fabricantes con 'w' en el nombre.
SELECT nombre FROM fabricante WHERE nombre LIKE '%w%';

-- 33. Fabricantes con nombres de 4 caracteres.
SELECT nombre FROM fabricante WHERE LENGTH(nombre) = 4;

-- 34. Productos con 'Portátil' en el nombre.
SELECT nombre FROM producto WHERE nombre LIKE '%Portátil%';

-- 35. Monitores con precio <215€.
SELECT nombre FROM producto WHERE nombre LIKE '%Monitor%' AND precio < 215;

-- 36. Productos ≥180€ ordenados por precio (desc) y nombre (asc).
SELECT nombre, precio FROM producto 
WHERE precio >= 180 
ORDER BY precio DESC, nombre ASC;