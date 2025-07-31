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

---