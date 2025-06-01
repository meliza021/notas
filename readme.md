# 🌸🐱 README de MySQL 🐱🌸
## 💻✨ Todo lo que sé de MySQL explicado por mí ✨💻

¡Hola! 🙋‍♀️🌷  
Soy una estudiante súper curiosa 🐰 que ama aprender cosas nuevas, y aquí dejo mi **README más bonito** de **MySQL** para que yo y quien lo lea 📖 pueda entenderlo TODO de forma kawaii y clarita. 💖

---

## 📑✨ Índice ✨📑

1️⃣ [SELECT: Todas sus variantes 🐾](#-select-todas-sus-variantes-)  
2️⃣ [Funciones de MySQL 🎈](#-funciones-de-mysql-)  
  📊 Funciones de Agregación 🐼  
  🔤 Funciones de Texto 🐻  
  🔢 Funciones Numéricas 🦊  
  ⏰ Funciones de Fecha y Hora 🐨  
  ✨ Otras Funciones Útiles 🦄  
3️⃣ [Procedimientos Almacenados 📝](#-procedimientos-almacenados-)  
4️⃣ [Eventos Programados 🕒](#-eventos-programados-)  
5️⃣ [Permisos de Usuarios 🔐](#-permisos-de-usuarios-)  
6️⃣ [Tips Finales 🌟](#-tips-finales-)

---

## ✅ SELECT: Todas sus variantes 🐾

El **SELECT** es mi comando favorito 🌸 porque me deja ver toda la info que quiero 👀✨. Aquí dejo todas sus formas:

- 🐣 **Básico**
  ```sql
  SELECT * FROM tabla;
- 🌈 **Seleccionar columnas específicas**

  ```sql
  SELECT nombre, edad FROM usuarios;
  ```

- 🎯 **WHERE: Filtros**

  ```sql
  SELECT * FROM productos WHERE precio > 50;
  ```

- 🐧 **ORDER BY: Ordenar**

  ```sql
  SELECT * FROM clientes ORDER BY nombre ASC;
  ```

- 🦋 **LIMIT: Limitar resultados**

  ```sql
  SELECT * FROM ventas LIMIT 10;
  ```

- 🐼 **DISTINCT: Sin duplicados**

  ```sql
  SELECT DISTINCT ciudad FROM clientes;
  ```

- 🐙 **GROUP BY + HAVING**

  ```sql
  SELECT categoria, COUNT(*) FROM productos GROUP BY categoria HAVING COUNT(*) > 5;
  ```

- 🦄 **JOIN: Unir tablas**

  ```sql
  SELECT u.nombre, p.producto 
  FROM usuarios u 
  INNER JOIN pedidos p ON u.id = p.usuario_id;
  ```

- 🐰 **Subconsultas**

  ```sql
  SELECT nombre FROM empleados WHERE salario > (SELECT AVG(salario) FROM empleados);
  ```

---

## 🎈 Funciones de MySQL 🎈

Las funciones son mis amigas mágicas 🧚‍♀️✨. Aquí guardo todas por categoría:

### 📊 Funciones de Agregación 🐼

| Función   | Descripción        |
| --------- | ------------------ |
| `COUNT()` | Contar registros 🧮 |
| `SUM()`   | Sumar valores ➕    |
| `AVG()`   | Promedio 📏         |
| `MIN()`   | Mínimo 📉           |
| `MAX()`   | Máximo 📈           |

```sql
SELECT COUNT(*) FROM clientes;
SELECT SUM(precio) FROM ventas;
SELECT AVG(edad) FROM empleados;
```

### 🔤 Funciones de Texto 🐻

| Función       | Descripción       |
| ------------- | ----------------- |
| `UPPER()`     | Mayúsculas ✨      |
| `LOWER()`     | Minúsculas 🐣      |
| `LENGTH()`    | Largo del texto 📏 |
| `CONCAT()`    | Unir textos 🔗     |
| `SUBSTRING()` | Subcadena ✂️       |

```sql
SELECT UPPER(nombre) FROM usuarios;
SELECT CONCAT(nombre, ' ', apellido) FROM usuarios;
```

---

### 🔢 Funciones Numéricas 🦊

| Función   | Descripción        |
| --------- | ------------------ |
| `ROUND()` | Redondear 🔵        |
| `CEIL()`  | Redondear arriba ⬆️ |
| `FLOOR()` | Redondear abajo ⬇️  |
| `ABS()`   | Valor absoluto ♾️   |
| `MOD()`   | Módulo 🧩           |

```sql
SELECT ROUND(3.1416, 2); -- 3.14
SELECT ABS(-15);
```

---

### ⏰ Funciones de Fecha y Hora 🐨

| Función                      | Descripción                  |
| ---------------------------- | ---------------------------- |
| `NOW()`                      | Fecha y hora actual 🕒        |
| `CURDATE()`                  | Solo fecha 📅                 |
| `CURTIME()`                  | Solo hora ⏰                  |
| `YEAR()`, `MONTH()`, `DAY()` | Extraer partes de la fecha 🗓️ |

```sql
SELECT NOW();
SELECT YEAR(fecha_nacimiento) FROM empleados;
```

---

### ✨ Otras Funciones Útiles 🦄

- `IFNULL()`: Devuelve otro valor si es NULL.
- `COALESCE()`: Devuelve el primer valor NO NULL.
- `CASE`: Condiciones dentro de SELECT 🐰

```sql
SELECT IFNULL(telefono, 'No registrado') FROM clientes;

SELECT 
  nombre,
  CASE
    WHEN salario > 1000 THEN 'Alto'
    ELSE 'Bajo'
  END AS nivel_salarial
FROM empleados;
```

---

## 📝 Procedimientos Almacenados 📝

Los **procedimientos almacenados** 🗂️ me ayudan a guardar consultas y lógica que puedo reutilizar.

- 🧵 **Crear procedimiento**

  ```sql
  DELIMITER //
  CREATE PROCEDURE mostrarEmpleados()
  BEGIN
    SELECT * FROM empleados;
  END //
  DELIMITER ;
  ```

- 🎀 **Llamar procedimiento**

  ```sql
  CALL mostrarEmpleados();
  ```

- ✂️ **Eliminar procedimiento**

  ```sql
  DROP PROCEDURE IF EXISTS mostrarEmpleados;
  ```

- ✏️ **Con parámetros**

  ```sql
  DELIMITER //
  CREATE PROCEDURE filtrarPorDepartamento(IN dep VARCHAR(50))
  BEGIN
    SELECT * FROM empleados WHERE departamento = dep;
  END //
  DELIMITER ;
  
  CALL filtrarPorDepartamento('Marketing');
  ```

---

## 🕒 Eventos Programados 🕒

Los **eventos** ⏰ permiten ejecutar tareas cada cierto tiempo o en un momento específico.

- 🔓 **Activar el programador**

  ```sql
  SET GLOBAL event_scheduler = ON;
  ```

- 🧩 **Crear evento**

  ```sql
  CREATE EVENT borrarTemporales
  ON SCHEDULE EVERY 1 DAY
  DO
    DELETE FROM logs WHERE fecha < NOW() - INTERVAL 30 DAY;
  ```

- ❌ **Eliminar evento**

  ```sql
  DROP EVENT IF EXISTS borrarTemporales;
  ```

- 🧵 **Listar eventos**

  ```sql
  SHOW EVENTS;
  ```

---

## 🔐 Permisos de Usuarios 🔐

En MySQL puedo dar permisos para controlar quién hace qué 🛡️✨.

- 🧑‍💻 **Crear usuario**

  ```sql
  CREATE USER 'usuario1'@'localhost' IDENTIFIED BY 'contrasena123';
  ```

- 🎁 **Dar permisos**

  ```sql
  GRANT SELECT, INSERT ON mi_base.* TO 'usuario1'@'localhost';
  ```

- 🧹 **Revocar permisos**

  ```sql
  REVOKE INSERT ON mi_base.* FROM 'usuario1'@'localhost';
  ```

- 🔑 **Ver permisos**

  ```sql
  SHOW GRANTS FOR 'usuario1'@'localhost';
  ```

- 🗑️ **Eliminar usuario**

  ```sql
  DROP USER 'usuario1'@'localhost';
  ```

---

## 🌟 Tips Finales 🌟

✨ Siempre hago **backups** para no perder datos.  
✨ Reviso bien mis `WHERE` para no borrar o actualizar todo sin querer 🫣.  
✨ Uso `EXPLAIN` para entender mis consultas y optimizarlas.  
✨ Organizo mis bases con nombres claros y consistentes 🗂️.

---

## 💖 Gracias por leer mi README 💖

Espero que este README 🌸 sea útil para mí y para ti 🫶.  
Lo hice con mucho amor y con todos mis apuntes 🐰✨.

**¡Sigamos aprendiendo! 🚀**