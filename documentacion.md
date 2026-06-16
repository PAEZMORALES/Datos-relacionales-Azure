# Datos-relacionales-Azure
# Introducción a los Datos Relacionales en Microsoft Azure

## ¿Qué son los datos relacionales?

Los datos relacionales son un tipo de información organizada en tablas compuestas por filas y columnas. Cada tabla representa una entidad específica (por ejemplo, clientes, productos o pedidos) y las relaciones entre ellas se establecen mediante claves primarias y claves externas.

Las bases de datos relacionales utilizan el lenguaje **SQL (Structured Query Language)** para almacenar, consultar y administrar los datos.

## Servicios de datos relacionales en Azure

Microsoft Azure ofrece varios servicios para implementar y administrar bases de datos relacionales en la nube. Estos servicios permiten almacenar datos de forma segura, escalable y con alta disponibilidad.

### Azure SQL Database

**Azure SQL Database** es un servicio de base de datos relacional totalmente administrado basado en Microsoft SQL Server. Algunas de sus características principales son:

- Administración automática de copias de seguridad.
- Escalabilidad bajo demanda.
- Alta disponibilidad integrada.
- Seguridad avanzada y protección contra amenazas.
- Actualizaciones automáticas.

### Azure SQL Managed Instance

Este servicio proporciona una compatibilidad casi completa con SQL Server local, facilitando la migración de aplicaciones existentes a la nube con cambios mínimos.

Características:

- Compatibilidad con funcionalidades avanzadas de SQL Server.
- Administración simplificada.
- Alta disponibilidad y recuperación ante desastres.

### SQL Server en Azure Virtual Machines

Permite ejecutar una instalación completa de SQL Server dentro de una máquina virtual de Azure.

Ventajas:

- Control total sobre la configuración.
- Compatibilidad completa con SQL Server.
- Ideal para aplicaciones que requieren personalización específica.

### Azure Database for PostgreSQL

Servicio administrado para ejecutar bases de datos PostgreSQL en Azure.

Beneficios:

- Escalabilidad flexible.
- Seguridad integrada.
- Copias de seguridad automáticas.
- Alto rendimiento.

### Azure Database for MySQL

Servicio administrado para bases de datos MySQL que ofrece:

- Administración simplificada.
- Escalabilidad automática.
- Seguridad y alta disponibilidad.

## Conceptos clave de los datos relacionales

### Tablas

Las tablas almacenan los datos organizados en filas y columnas.

Ejemplo:

| ID Cliente | Nombre | Ciudad |
|------------|---------|---------|
| 1 | Ana | Madrid |
| 2 | Luis | Barcelona |

### Clave primaria (Primary Key)

Identifica de forma única cada fila de una tabla.

Ejemplo:

```sql
CREATE TABLE Clientes (
    ClienteID INT PRIMARY KEY,
    Nombre VARCHAR(100)
);
```

### Clave externa (Foreign Key)

Establece una relación entre dos tablas.

Ejemplo:

```sql
CREATE TABLE Pedidos (
    PedidoID INT PRIMARY KEY,
    ClienteID INT,
    FOREIGN KEY (ClienteID) REFERENCES Clientes(ClienteID)
);
```

### Consultas SQL

Permiten recuperar y manipular datos.

Ejemplo:

```sql
SELECT Nombre
FROM Clientes
WHERE Ciudad = 'Madrid';
```

## Ventajas de utilizar servicios relacionales en Azure

- **Escalabilidad:** aumento o reducción de recursos según la demanda.
- **Alta disponibilidad:** minimiza interrupciones del servicio.
- **Seguridad:** cifrado de datos, autenticación y control de acceso.
- **Administración simplificada:** mantenimiento y actualizaciones automáticas.
- **Integración:** compatibilidad con otros servicios de Azure como Azure Functions, Azure Data Factory y Power BI.

## Casos de uso comunes

- Sistemas de gestión empresarial (ERP).
- Aplicaciones de comercio electrónico.
- Sistemas de gestión de clientes (CRM).
- Aplicaciones financieras.
- Plataformas de reservas y gestión de inventarios.

## Conclusión

Los servicios de datos relacionales de Microsoft Azure permiten almacenar y gestionar información estructurada de manera eficiente y segura. Azure ofrece múltiples opciones, desde bases de datos totalmente administradas hasta máquinas virtuales con control total, adaptándose a diferentes necesidades empresariales y técnicas.
# Introducción a las Bases de Datos Relacionales

Cuando se empezaron a usar los sistemas informáticos, cada aplicación almacenaba los datos en su propia estructura, que era única. Cuando los desarrolladores querían crear aplicaciones para usar esos datos, necesitaban mucha información sobre la estructura de datos en particular para encontrar los que necesitaban.

Estas estructuras de datos eran ineficaces, costosas de mantener y difíciles de optimizar para que la aplicación tuviera un buen rendimiento.

El modelo de base de datos relacional se diseñó para resolver el problema de varias estructuras de datos arbitrarias. El modelo relacional proporciona una forma estándar de representar y consultar datos que cualquier aplicación puede usar.

Una de las principales ventajas del modelo de base de datos relacional es su uso de tablas, que son una manera intuitiva, eficaz y flexible de almacenar y acceder a la información estructurada.

## Importancia del Modelo Relacional

El modelo relacional, sencillo pero eficaz, se usa en organizaciones de todo tipo y tamaño para satisfacer diferentes necesidades de administración de la información.

Las bases de datos relacionales se utilizan para:

- Realizar un seguimiento de los inventarios.
- Procesar transacciones de comercio electrónico.
- Administrar grandes cantidades de información de clientes críticos.
- Gestionar datos empresariales de forma estructurada y eficiente.

Las bases de datos relacionales son útiles para almacenar cualquier información que contenga elementos de datos relacionados que se deban organizar en una estructura coherente y basada en reglas.

## Objetivos del Módulo

En este módulo, obtendrá información sobre:

- Las características clave de las bases de datos relacionales.
- Las estructuras de datos relacionales.
- Los principios fundamentales del modelo relacional.
- La organización y consulta eficiente de los datos.

> **Nota**

> Reconocemos que a diferentes personas les gusta aprender de diferentes maneras. Puede optar por completar este módulo en formato basado en vídeo o puede leer el contenido como texto e imágenes.
>
> El texto contiene más detalle que los vídeos, por lo que, en algunos casos, es posible que desee hacer referencia a él como material complementario para la presentación de vídeo.

# Tablas en una Base de Datos Relacional

En una base de datos relacional, las colecciones de entidades del mundo real se modelan como **tablas**.

Una entidad puede ser cualquier elemento sobre el que se desee almacenar información; normalmente, objetos o eventos importantes para una organización.

Por ejemplo, en un sistema de ventas minoristas, se pueden crear tablas para:

- Clientes
- Productos
- Pedidos
- Artículos de línea dentro de un pedido

## Filas y Entidades

Una tabla contiene **filas**, y cada fila representa una única instancia de una entidad.

En el ejemplo del sistema minorista:

- Cada fila de la tabla **Clientes** contiene los datos de un único cliente.
- Cada fila de la tabla **Productos** define un producto específico.
- Cada fila de la tabla **Pedidos** representa un pedido realizado por un cliente.
- Cada fila de la tabla **Artículos de línea** representa un producto incluido en un pedido.

## Ejemplo de Modelo Relacional

| Tabla | Representa |
|---------|------------|
| Clientes | Información de cada cliente |
| Productos | Catálogo de productos disponibles |
| Pedidos | Pedidos realizados por los clientes |
| Artículos de línea | Productos incluidos en cada pedido |

Este enfoque permite organizar la información de forma estructurada, facilitando el almacenamiento, la consulta y la gestión de los datos.
![Modelo de base de datos relacional](foto_1.png)

## Estructura de las Tablas Relacionales

Las tablas relacionales son un formato para almacenar **datos estructurados**, donde cada fila de una tabla contiene las mismas columnas.

Sin embargo, no es necesario que todas las columnas tengan un valor en cada fila. Por ejemplo, una tabla **Customer** podría incluir una columna denominada **MiddleName**, que puede estar vacía (**NULL**) para los clientes que no tienen segundo nombre o cuyo segundo nombre es desconocido.

## Tipos de Datos en las Columnas

Cada columna almacena datos de un tipo específico. Algunos ejemplos son:

| Tabla | Columna | Tipo de dato |
|---------|---------|-------------|
| Customer | Email | Texto (caracteres) |
| Product | Price | Número decimal |
| Order | Quantity | Número entero |
| Order | OrderDate | Fecha y hora |

### Ejemplos

- La columna **Email** de la tabla **Customer** suele definirse para almacenar datos de texto.
- La columna **Price** de la tabla **Product** se define para almacenar valores numéricos decimales.
- La columna **Quantity** de la tabla **Order** suele restringirse a números enteros.
- La columna **OrderDate** se utiliza para almacenar fechas y horas.

## Compatibilidad de los Tipos de Datos

Los tipos de datos disponibles al definir una tabla dependen del sistema de base de datos utilizado. No obstante, existen tipos de datos estándar definidos por el **American National Standards Institute (ANSI)** que son compatibles con la mayoría de los sistemas de bases de datos relacionales.

> **Nota:** Utilizar tipos de datos adecuados ayuda a garantizar la integridad de la información, optimizar el almacenamiento y mejorar el rendimiento de las consultas.

## Normalización de Bases de Datos

La **normalización** es un término utilizado por los profesionales de bases de datos para describir un proceso de diseño de esquemas que tiene como objetivo minimizar la duplicación de datos y garantizar la integridad de la información.

Aunque existen numerosas reglas complejas que definen el proceso de refactorización de datos en distintos niveles (o formas) de normalización, una definición práctica y simplificada es la siguiente:

### Principios Básicos de la Normalización

1. Separar cada entidad en su propia tabla.
2. Separar cada atributo discreto en su propia columna.
3. Identificar de forma única cada instancia de una entidad (fila) mediante una **clave primaria** (*Primary Key*).
4. Utilizar columnas de **clave externa** (*Foreign Key*) para relacionar entidades vinculadas.

## Objetivos de la Normalización

La normalización ayuda a:

- Reducir la redundancia de datos.
- Evitar inconsistencias en la información.
- Facilitar el mantenimiento de la base de datos.
- Mejorar la integridad y calidad de los datos.
- Optimizar las operaciones de actualización, inserción y eliminación.

## Ejemplo Conceptual

Para comprender los principios básicos de la normalización, supongamos que la siguiente tabla representa una hoja de cálculo utilizada por una empresa para realizar el seguimiento de sus ventas.

> A partir de esta tabla inicial, el proceso de normalización consistirá en identificar las diferentes entidades (clientes, productos, pedidos, etc.), separarlas en tablas independientes y establecer relaciones entre ellas mediante claves primarias y claves externas.

## Principios Básicos de la Normalización

| Nº | Principio | Descripción |
|----|------------|-------------|
| 1 | Separar cada entidad en su propia tabla | Cada entidad (Cliente, Producto, Pedido, etc.) debe almacenarse en una tabla independiente. |
| 2 | Separar cada atributo discreto en su propia columna | Cada dato debe ocupar una columna específica para facilitar su gestión y consulta. |
| 3 | Clave primaria (*Primary Key*) | Cada fila debe identificarse de forma única mediante una clave primaria. |
| 4 | Clave externa (*Foreign Key*) | Las relaciones entre tablas se establecen mediante claves externas. |

## Objetivos de la Normalización

| Objetivo | Beneficio |
|-----------|-----------|
| Reducir la redundancia de datos | Evita almacenar la misma información varias veces. |
| Evitar inconsistencias | Garantiza que los datos sean coherentes y correctos. |
| Facilitar el mantenimiento | Simplifica las actualizaciones y modificaciones. |
| Mejorar la integridad de los datos | Asegura la validez y confiabilidad de la información. |
| Optimizar operaciones | Mejora el rendimiento de inserciones, actualizaciones y eliminaciones. |

# Normalización de Datos en Bases de Datos Relacionales

Observe que los detalles del **cliente** y del **producto** se duplican para cada artículo individual vendido. Además, el nombre del cliente, la dirección postal, el nombre del producto y el precio se combinan en las mismas celdas de la hoja de cálculo.

La normalización cambia la forma en que se almacenan los datos para evitar duplicaciones y mejorar la organización de la información.

## Almacenamiento Normalizado

En un esquema normalizado:

- Cada entidad representada en los datos se almacena en su propia tabla.
- Cada atributo individual de una entidad se almacena en su propia columna.

Ejemplo de entidades separadas:

| Entidad | Tabla |
|---------|-------|
| Cliente | Customer |
| Producto | Product |
| Pedido de venta | Order |
| Elemento de línea | LineItem |

## Eliminación de Duplicación de Datos

Registrar cada instancia de una entidad como una fila dentro de su tabla específica elimina la duplicación de datos.

Ejemplo:

- Si se necesita cambiar la dirección de un cliente, solo es necesario modificar el valor en una única fila de la tabla **Customer**.
- No es necesario actualizar múltiples registros de pedidos o ventas.

## Separación de Atributos en Columnas

La división de los atributos en columnas individuales permite:

- Restringir cada valor a un tipo de dato adecuado.
- Mejorar la calidad y consistencia de la información.
- Facilitar las consultas sobre los datos.

Ejemplos:

| Campo | Tipo de dato esperado |
|-------|------------------------|
| Precio del producto | Número decimal |
| Cantidad de elementos de línea | Número entero |
| Fecha del pedido | Fecha y hora |

Además, disponer de columnas independientes proporciona un nivel de granularidad útil para realizar consultas.

Ejemplo:

- Filtrar clientes que viven en una ciudad específica.
- Buscar productos dentro de un rango de precios.
- Consultar pedidos realizados en una fecha determinada.

## Claves Primarias y Claves Externas

Cada instancia de una entidad se identifica de forma única mediante un identificador conocido como **clave primaria** (*Primary Key*).

Cuando una entidad hace referencia a otra, la clave primaria de la entidad relacionada se almacena como una **clave externa** (*Foreign Key*).

Ejemplo:

| Tabla | Clave |
|-------|-------|
| Customer | CustomerID (Clave primaria) |
| Order | OrderID (Clave primaria) |
| Order | CustomerID (Clave externa) |

Esto permite relacionar un pedido con el cliente correspondiente.

Por ejemplo:

- La dirección de un cliente se almacena una sola vez en la tabla **Customer**.
- La tabla **Order** puede obtener esa información mediante la referencia a la clave del cliente.

## Integridad Referencial

Un sistema de administración de bases de datos relacionales (**RDBMS**) puede aplicar reglas de **integridad referencial** para garantizar que:

- Una clave externa siempre tenga una clave primaria correspondiente.
- No existan registros relacionados con entidades inexistentes.

Ejemplo:

- No se puede crear un pedido asociado a un cliente que no existe en la tabla **Customer**.

## Claves Compuestas

En algunos casos, una clave primaria o externa puede estar formada por la combinación de varias columnas. Esto se conoce como **clave compuesta**.

Ejemplo:

La tabla **LineItem** puede utilizar una combinación única de:

| Columna | Descripción |
|---------|-------------|
| OrderNo | Número del pedido |
| ItemNo | Número del artículo |

La combinación de **OrderNo + ItemNo** permite identificar de forma única cada elemento de línea dentro de un pedido.

# SQL (Structured Query Language)

**SQL** significa **Lenguaje de Consulta Estructurado** (*Structured Query Language*) y se utiliza para comunicarse con una base de datos relacional.

Es el lenguaje estándar utilizado por los sistemas de administración de bases de datos relacionales para realizar tareas como:

- Consultar datos.
- Insertar información.
- Actualizar registros.
- Eliminar datos.
- Crear y modificar estructuras de bases de datos.

Algunos sistemas de administración de bases de datos relacionales que utilizan SQL son:

- Microsoft SQL Server
- Azure SQL Database
- Azure SQL Managed Instance
- SQL Server en Azure Virtual Machines
- MySQL
- PostgreSQL
- Oracle

---

## Historia de SQL

SQL fue normalizado originalmente por:

- **American National Standards Institute (ANSI)** en 1986.
- **Organización Internacional de Normalización (ISO)** en 1987.

Desde entonces, el estándar SQL se ha ampliado varias veces debido a que los proveedores de bases de datos han añadido nuevas funcionalidades.

Además, muchos proveedores incluyen extensiones propias que no forman parte del estándar, creando diferentes **dialectos de SQL**.

---

# Dialectos populares de SQL

| Dialecto | Descripción |
|----------|-------------|
| **Transact-SQL (T-SQL)** | Utilizado por Microsoft SQL Server, Azure SQL Database, Azure SQL Managed Instance y SQL Server en Azure Virtual Machines. |
| **pgSQL** | Dialecto con extensiones utilizado por PostgreSQL. |
| **PL/SQL** | Dialecto utilizado por Oracle. Significa *Procedural Language/SQL*. |

Los usuarios que trabajan con un sistema específico de base de datos deben aprender las características y sintaxis propias de su dialecto SQL.

> **Nota:** Azure SQL Database incluye características de inteligencia artificial que permiten escribir y comprender consultas SQL mediante lenguaje natural.

> **Nota:** Los ejemplos de este módulo utilizan principalmente el dialecto Transact-SQL (T-SQL).

---

# Tipos de instrucciones SQL

Las instrucciones SQL se agrupan en tres categorías principales:

| Grupo | Significado |
|-------|-------------|
| **DDL** | Lenguaje de definición de datos (*Data Definition Language*) |
| **DCL** | Lenguaje de control de datos (*Data Control Language*) |
| **DML** | Lenguaje de manipulación de datos (*Data Manipulation Language*) |

---

# Lenguaje de Definición de Datos (DDL)

Las instrucciones **DDL** se utilizan para crear, modificar y eliminar objetos de una base de datos como:

- Tablas.
- Procedimientos almacenados.
- Vistas.

## Principales instrucciones DDL

| Instrucción | Descripción |
|------------|-------------|
| `CREATE` | Crea un nuevo objeto en la base de datos. |
| `ALTER` | Modifica la estructura de un objeto existente. |
| `DROP` | Elimina un objeto de la base de datos. |
| `RENAME` | Cambia el nombre de un objeto existente. |

> ⚠️ **Advertencia:**  
> La instrucción `DROP` elimina completamente un objeto y todos sus datos. Si no existe una copia de seguridad, la información no podrá recuperarse.

---

## Ejemplo: Crear una tabla

```sql
CREATE TABLE Product
(
    ID INT PRIMARY KEY,
    Name VARCHAR(20) NOT NULL,
    Price DECIMAL NULL
);
```

### Elementos utilizados:

| Elemento | Descripción |
|----------|-------------|
| `PRIMARY KEY` | Identifica de forma única cada fila. |
| `NOT NULL` | Indica que la columna debe tener un valor obligatorio. |
| `NULL` | Permite que una columna no tenga valor. |

---

# Tipos de datos SQL comunes

| Tipo de dato | Uso |
|--------------|-----|
| `INT` | Números enteros. |
| `DECIMAL` | Números decimales. |
| `VARCHAR` | Texto de longitud variable. |

---

# Lenguaje de Control de Datos (DCL)

Las instrucciones **DCL** permiten administrar permisos y accesos a los datos.

## Principales instrucciones DCL

| Instrucción | Descripción |
|------------|-------------|
| `GRANT` | Concede permisos. |
| `DENY` | Niega permisos. |
| `REVOKE` | Quita permisos previamente concedidos. |

Ejemplo:

```sql
GRANT SELECT, INSERT, UPDATE
ON Product
TO user1;
```

Este comando permite al usuario `user1`:

- Leer datos.
- Insertar datos.
- Actualizar datos.

---

# Lenguaje de Manipulación de Datos (DML)

Las instrucciones **DML** permiten trabajar con las filas de las tablas.

Se utilizan para:

- Consultar datos.
- Insertar registros.
- Modificar información.
- Eliminar registros.

## Principales instrucciones DML

| Instrucción | Descripción |
|------------|-------------|
| `SELECT` | Consulta datos. |
| `INSERT` | Inserta nuevas filas. |
| `UPDATE` | Modifica datos existentes. |
| `DELETE` | Elimina filas. |

---

# SELECT

Permite recuperar información de una tabla.

Ejemplo:

```sql
SELECT *
FROM Customer
WHERE City = 'Seattle';
```

Este ejemplo devuelve todos los datos de clientes que viven en Seattle.

---

## Seleccionar columnas específicas

```sql
SELECT FirstName, LastName, Address, City
FROM Customer
WHERE City = 'Seattle';
```

---

# Ordenar resultados con ORDER BY

```sql
SELECT FirstName, LastName, Address, City
FROM Customer
WHERE City = 'Seattle'
ORDER BY LastName;
```

Ordena los resultados por apellido.

---

# JOIN entre tablas

La cláusula `JOIN` permite combinar información de varias tablas relacionadas.

Ejemplo:

```sql
SELECT o.OrderNo, o.OrderDate, c.Address, c.City
FROM Order AS o
JOIN Customer AS c
ON o.Customer = c.ID;
```

En este caso:

- `Order` se relaciona con `Customer`.
- La relación se realiza mediante una clave externa.

---

# UPDATE

Permite modificar registros existentes.

Ejemplo:

```sql
UPDATE Customer
SET Address = '123 High St.'
WHERE ID = 1;
```

Este comando cambia la dirección del cliente con ID igual a 1.

> ⚠️ **Advertencia:**  
> Si se elimina la cláusula `WHERE`, se modificarán todas las filas de la tabla.

---

# DELETE

Permite eliminar registros.

Ejemplo:

```sql
DELETE FROM Product
WHERE ID = 162;
```

Elimina el producto cuyo ID es 162.

> ⚠️ **Advertencia:**  
> Si se omite `WHERE`, se eliminarán todas las filas de la tabla.

---

# INSERT

Permite insertar nuevos registros.

Ejemplo:

```sql
INSERT INTO Product(ID, Name, Price)
VALUES (99, 'Drill', 4.99);
```

Inserta un nuevo producto con:

| Campo | Valor |
|------|-------|
| ID | 99 |
| Nombre | Drill |
| Precio | 4.99 |

---

# Resumen de instrucciones SQL

| Categoría | Instrucciones |
|----------|---------------|
| **DDL** | CREATE, ALTER, DROP, RENAME |
| **DCL** | GRANT, DENY, REVOKE |
| **DML** | SELECT, INSERT, UPDATE, DELETE |

SQL proporciona las herramientas necesarias para crear, administrar, consultar y modificar bases de datos relacionales de forma eficiente.
Descripción de objetos de base de datos
Completado
100 XP
6 minutos
Elección del formato de contenido preferido
Además de las tablas, una base de datos relacional puede contener otras estructuras que ayudan a optimizar la organización de los datos, encapsular acciones mediante programación y mejorar la velocidad de acceso. En esta unidad, obtendrá información sobre tres de estas estructuras con más detalle: vistas, procedimientos almacenados e índices.

¿Qué es una vista?
Una vista es una tabla virtual basada en los resultados de una consulta SELECT . Podría decirse que una vista es como una ventana que muestra unas filas concretas de una o varias tablas subyacentes. Por ejemplo, podría crear una vista en las tablas Order y Customer que recuperan los datos del pedido y del cliente para proporcionar un único objeto que facilita la determinación de las direcciones de entrega de los pedidos:

SQL
CREATE VIEW Deliveries
AS
SELECT o.OrderNo, o.OrderDate,
       c.FirstName, c.LastName, c.Address, c.City
FROM Order AS o JOIN Customer AS c
ON o.Customer = c.ID;
Diagrama que representa el concepto de una vista en una base de datos.

Puede consultar la vista y filtrar los datos de la misma forma que una tabla. La consulta siguiente busca detalles de los pedidos de los clientes que viven en Seattle:

SQL
SELECT OrderNo, OrderDate, LastName, Address
FROM Deliveries
WHERE City = 'Seattle';
¿Qué es un procedimiento almacenado?
Un procedimiento almacenado define instrucciones SQL que se pueden ejecutar a petición. Los procedimientos almacenados se usan para encapsular la lógica de programación en una base de datos para las acciones que las aplicaciones deben realizar al trabajar con datos.

Puede definir un procedimiento almacenado con parámetros a fin de crear una solución flexible para las acciones comunes que podrían tener que aplicarse a los datos en función de una clave o criterios específicos. Por ejemplo, se podría definir el siguiente procedimiento almacenado para cambiar el nombre de un producto en función del identificador de producto especificado.

SQL
CREATE PROCEDURE RenameProduct
	@ProductID INT,
	@NewName VARCHAR(20)
AS
UPDATE Product
SET Name = @NewName
WHERE ID = @ProductID;
Cuando haya que cambiar el nombre de un producto, puede ejecutar el procedimiento almacenado y pasar el identificador del producto y el nuevo nombre que se va a asignar:

SQL
EXEC RenameProduct 201, 'Spanner';
¿Qué es un índice?
Un índice le ayuda a buscar datos en una tabla. Piense en un índice sobre una tabla como en el índice al final de un libro. El índice de un libro contiene un conjunto ordenado de entradas, con las páginas en las que aparece cada una. Cuando quieras encontrar una referencia a un elemento del libro, la buscas en el índice. Puede usar los números de página del índice para ir directamente a las páginas correctas del libro. Sin el índice, es posible que tenga que leer todo el libro para encontrar el contenido que está buscando.

Cuando se crea un índice en una base de datos, se especifica una columna de la tabla; el índice contiene una copia de estos datos con un criterio de ordenación y punteros a las filas correspondientes de la tabla. Cuando el usuario ejecuta una consulta que especifica esta columna en la cláusula WHERE , el sistema de administración de bases de datos puede usar este índice para capturar los datos más rápidamente que si tuviera que examinar toda la fila de tabla por fila.

Por ejemplo, puede usar el código siguiente para crear un índice en la columna Nombre de la tabla Product :

SQL
CREATE INDEX idx_ProductName
ON Product(Name);
El índice crea una estructura basada en árbol que el optimizador de consultas del sistema de base de datos puede usar para buscar rápidamente filas en la tabla Product en función de un nombre especificado.

Captura de pantalla de un índice de ejemplo que crea una estructura basada en árboles.

Para una tabla que contiene pocas filas, el uso del índice probablemente no sea más eficaz que simplemente leer toda la tabla y buscar las filas solicitadas por la consulta (en cuyo caso, el optimizador de consultas omitirá el índice). Pero cuando una tabla tiene muchas filas, los índices pueden mejorar drásticamente el rendimiento de las consultas.

Puede crear muchos índices en una tabla. Por lo tanto, si también desea encontrar productos basados en el precio, crear otro índice en la columna Precio de la tabla Producto podría ser útil. Sin embargo, los índices no son gratuitos. Un índice consume espacio de almacenamiento y, cada vez que inserte datos en una tabla, los actualice o los elimine, tendrá que hacer el mantenimiento de sus índices. Este trabajo adicional puede ralentizar las operaciones de inserción, actualización y eliminación. Debe conseguir un equilibrio entre tener índices que aceleren las consultas y el coste de realizar otras operaciones.

# Evaluación del Módulo

**Puntuación:** 200 XP  
**Duración:** 10 minutos  

Esta evaluación mide la comprensión del módulo.

A diferencia de las actividades anteriores, no se proporcionarán comentarios sobre respuestas individuales; únicamente se indicará si las respuestas son correctas o incorrectas.

Se recomienda revisar los materiales del módulo antes de comenzar.

> **Nota:** Las preguntas y opciones de respuesta de esta evaluación fueron generadas mediante inteligencia artificial y revisadas por un autor humano.

---

# Preguntas

## 1. ¿Cuál de las siguientes indica una infracción del primer formulario normal en un esquema de base de datos?

- [ ] Una tabla tiene columnas con valores NULL.
- [ ] Una tabla contiene grupos o matrices repetidos dentro de una columna.
- [ ] Una tabla tiene una clave principal compuesta por varias columnas.

---

## 2. ¿Cuál es un síntoma común de un esquema de base de datos desnormalizado?

- [ ] Eliminación de todas las restricciones de clave externa.
- [ ] Redundancia de datos y anomalías de actualización.
- [ ] Rendimiento mejorado de las consultas sin inconvenientes.

---

## 3. ¿Cuál es el propósito del tercer formulario normal en la normalización de la base de datos?

- [ ] Permitir varias claves principales en una tabla.
- [ ] Asegurarse de que todos los atributos que no son clave dependan funcionalmente solo de la clave principal.
- [ ] Quitar todas las columnas que aceptan valores NULL de una tabla.

---

## 4. ¿Qué enfoque podría optimizar una consulta que recupera con frecuencia los registros de clientes en función de la columna `LastName`?

- [ ] Crear un índice en la columna `LastName` de la tabla `Customer`.
- [ ] Usar una instrucción `DELETE` para quitar entradas innecesarias de la tabla `Customer`.
- [ ] Agregar una restricción de clave principal en la columna `LastName`.

---

## 5. ¿Cómo mejoran los procedimientos almacenados el rendimiento de la base de datos y la organización en comparación con la ejecución de consultas SQL independientes?

- [ ] Los procedimientos almacenados se pueden indexar automáticamente, lo que acelera significativamente las operaciones de recuperación de datos.
- [ ] Los procedimientos almacenados encapsulan la lógica, lo que reduce el tráfico de red y mejora la eficacia de la ejecución.
- [ ] Los procedimientos almacenados eliminan la necesidad de claves externas, lo que simplifica el diseño de la base de datos y mejora el rendimiento.

---

## 6. ¿Cómo puede asegurarse de que una columna de una tabla recién creada debe contener siempre un valor en SQL?

- [ ] Utilizar una restricción `DEFAULT` con la columna.
- [ ] Especificar la columna como `NOT NULL` durante la creación de la tabla.
- [ ] Crear un índice en la columna.

---

## 7. ¿Qué instrucción SQL usaría para crear una tabla denominada `Books` con las columnas `ISBN` como clave principal y `Title` como NOT NULL?

- [ ] 
```sql
CREATE TABLE Books 
(
    ISBN VARCHAR(255), 
    Title VARCHAR(255)
);
```

- [ ] 
```sql
CREATE TABLE Books 
(
    ISBN INT PRIMARY KEY, 
    Title VARCHAR(255) NOT NULL
);
```

- [ ] 
```sql
CREATE TABLE Books 
(
    ISBN PRIMARY KEY VARCHAR, 
    Title NOT NULL VARCHAR
);


## 8. ¿Qué objeto de base de datos sería más adecuado para encapsular la lógica SQL compleja que debe reutilizarse en varias aplicaciones?

- [ ] Vista
- [ ] Índice
- [ ] Procedimiento almacenado


## 9. ¿Cuál es la principal ventaja de usar índices en una base de datos relacional y cómo afectan al rendimiento?

- [ ] Los índices aceleran la recuperación de datos mediante la creación de una copia ordenada de datos de columna, lo que mejora el rendimiento de las consultas.
- [ ] Los índices ayudan a mantener la integridad de los datos aplicando restricciones de clave principal, lo que acelera las operaciones de modificación de datos.
- [ ] Los índices reducen el espacio de almacenamiento necesario al comprimir los datos de columna, lo que mejora el rendimiento general de la base de datos.


Las **bases de datos relacionales** son una forma común mediante la cual las aplicaciones transaccionales almacenan y administran datos.

Estas bases de datos están formadas por:

- Un esquema de tablas.
- Relaciones entre tablas mediante valores de clave comunes.
- Consultas y operaciones realizadas mediante SQL.

El lenguaje **SQL** permite:

- Consultar datos.
- Insertar información.
- Actualizar registros.
- Eliminar datos.
- Administrar estructuras de bases de datos.

Además, una base de datos relacional puede enriquecerse mediante la creación de objetos como:

- **Vistas**
- **Procedimientos almacenados**
- **Índices**

# En este módulo has aprendido a:

- Identificar las características de los datos relacionales.
- Definir el concepto de normalización.
- Identificar los tipos de instrucciones SQL.
- Identificar objetos comunes de bases de datos relacionales.


# Pasos siguientes

Ahora que has aprendido sobre las **bases de datos relacionales**, puedes continuar aprendiendo sobre las cargas de trabajo relacionadas con datos en **Microsoft Azure** mediante una certificación de Microsoft en:

**Aspectos básicos de datos de Azure**


# Introducción a Azure

Elige la cuenta de Azure adecuada para ti:

- Paga según el uso.
- Prueba Azure gratis durante 30 días.
- Regístrate para comenzar a utilizar los servicios de Azure.

- # Evaluación del Módulo

Esta evaluación mide la comprensión del módulo.

A diferencia de las actividades anteriores, no se proporcionarán comentarios sobre respuestas individuales; únicamente se indicará si las respuestas son correctas o incorrectas.

Se recomienda revisar los materiales del módulo antes de comenzar.

> **Nota:** Las preguntas y opciones de respuesta de esta evaluación fueron generadas mediante inteligencia artificial y revisadas por un autor humano.

---

# Preguntas

## 1. Al crear un esquema de base de datos normalizado, ¿cómo debe controlar atributos opcionales, como un nombre intermedio para los clientes?

- [ ] Incluir el atributo opcional como una columna que acepta valores NULL en la tabla pertinente.
- [ ] Excluir el atributo opcional del esquema de base de datos para simplificar el diseño.
- [ ] Crear una tabla independiente para el atributo opcional y usar una relación de clave externa.

---

## 2. ¿Cómo representarías una relación de muchos a muchos entre dos tablas en un esquema de base de datos normalizado?

- [ ] Mediante la creación de una tabla de unión que incluye claves externas que hacen referencia a las claves principales de ambas tablas.
- [ ] Mediante la combinación de ambas tablas en una sola tabla con todos los atributos.
- [ ] Mediante la adición de varias columnas de clave externa en cada tabla para hacer referencia a la otra tabla.

---

## 3. Para mejorar el rendimiento al consultar con frecuencia una tabla de `ventas` por `SaleDate`, ¿qué debería hacer?

- [ ] Crear un índice en la columna `SaleDate`.
- [ ] Agregar una restricción de clave externa en la columna `SaleDate`.
- [ ] Crear un procedimiento almacenado para realizar consultas mediante `SaleDate`.

---

## 4. ¿Cómo pueden contribuir los procedimientos almacenados a mejorar la seguridad dentro de un entorno de base de datos?

- [ ] Los procedimientos almacenados requieren autenticación de usuario para cada ejecución, lo que garantiza que solo los usuarios autorizados puedan modificar los datos.
- [ ] Los procedimientos almacenados pueden limitar el acceso directo a las tablas mediante la encapsulación de la lógica SQL, reduciendo la exposición a ataques por inyección de código SQL.
- [ ] Los procedimientos almacenados cifran automáticamente todos los datos de la base de datos, garantizando la confidencialidad de los datos.

---

## 5. ¿Qué objeto de base de datos usaría para aplicar la integridad referencial entre dos tablas?

- [ ] Clave foránea (*Foreign Key*).
- [ ] Índice.
- [ ] Procedimiento almacenado.

---

## 6. ¿Cómo puede asegurarse de que una columna de una tabla recién creada debe contener siempre un valor en SQL?

- [ ] Especificar la columna como `NOT NULL` durante la creación de la tabla.
- [ ] Utilizar una restricción `DEFAULT` con la columna.
- [ ] Crear un índice en la columna.

---

## 7. ¿Cuál de las siguientes indica una infracción del primer formulario normal en un esquema de base de datos?

- [ ] Una tabla tiene una clave principal compuesta por varias columnas.
- [ ] Una tabla tiene columnas con valores NULL.
- [ ] Una tabla contiene grupos o matrices repetidos dentro de una columna.

---

## 8. ¿Qué escenario ilustra una desventaja de usar vistas en una base de datos?

- [ ] Las vistas pueden provocar problemas de rendimiento con consultas complejas, ya que no almacenan los datos y dependen de consultar las tablas base cada vez.
- [ ] Las vistas pueden actualizar automáticamente las tablas base cuando los datos se modifican en la vista.
- [ ] Las vistas aumentan los riesgos de seguridad, ya que exponen estructuras de tabla subyacentes a los usuarios.

---

## 9. ¿Cuál es el resultado de ejecutar la siguiente instrucción SQL?

```sql
DELETE FROM Customers
WHERE CustomerID = 15;
```

Opciones:

- [ ] Eliminará todas las filas de la tabla `Customers`.
- [ ] Eliminará la fila de la tabla `Customers` donde `CustomerID` es 15.
- [ ] Se actualizará el ID de cliente a 15 para todas las filas.

- [ ] # Resumen


Las **bases de datos relacionales** son una forma común mediante la cual las aplicaciones transaccionales almacenan y administran datos.

Están compuestas por:

- Un esquema de tablas.
- Relaciones entre tablas mediante valores de clave comunes.
- Consultas y manipulación de datos utilizando SQL.

El lenguaje **SQL** permite consultar y modificar los datos almacenados en las tablas.

Además, una base de datos relacional puede enriquecerse mediante la creación de objetos como:

- **Vistas**
- **Procedimientos almacenados**
- **Índices**

---

# En este módulo has aprendido a:

- Identificar las características de los datos relacionales.
- Definir el concepto de normalización.
- Identificar los tipos de instrucciones SQL.
- Identificar objetos comunes de bases de datos relacionales.

---

# Pasos siguientes

Ahora que has aprendido sobre las **bases de datos relacionales**, considera obtener más información sobre las cargas de trabajo relacionadas con datos en **Microsoft Azure** mediante una certificación de Microsoft en:

**Aspectos básicos de datos de Azure**

---

# Introducción a Azure

Elige la cuenta de Azure adecuada para ti:

- Paga según el uso.
- Prueba Azure gratis durante 30 días.
- Regístrate para comenzar a utilizar Azure.
  # Evaluación del Módulo

**Puntuación:** 200 XP  
**Duración:** 10 minutos  

Esta evaluación mide la comprensión del módulo.

A diferencia de las actividades anteriores, no se proporcionarán comentarios sobre respuestas individuales; únicamente se indicará si las respuestas son correctas o incorrectas.

Se recomienda revisar los materiales del módulo antes de comenzar.

> **Nota:** Las preguntas y opciones de respuesta de esta evaluación fueron generadas mediante inteligencia artificial y revisadas por un autor humano.

---

# Preguntas

## 1. ¿Qué instrucción SQL usaría para crear una tabla denominada `Books` con las columnas `ISBN` como clave principal y `Title` como NOT NULL?

- [ ] 
```sql
CREATE TABLE Books
(
    ISBN INT PRIMARY KEY,
    Title VARCHAR(255) NOT NULL
);
```

- [ ] 
```sql
CREATE TABLE Books
(
    ISBN PRIMARY KEY VARCHAR,
    Title NOT NULL VARCHAR
);
```

- [ ] 
```sql
CREATE TABLE Books
(
    ISBN VARCHAR(255),
    Title VARCHAR(255)
);
```

---

## 2. ¿Qué instrucción SQL recupera correctamente `ProductName` y `Price` de la tabla `Products` para los productos con un precio inferior a 10?

- [ ] 
```sql
SELECT ProductName, Price
FROM Products
WHERE Price < 10;
```

- [ ] 
```sql
SELECT ProductName, Price
WHERE Price < 10
FROM Products;
```

- [ ] 
```sql
SELECT *
FROM Products
WHERE ProductName AND Price < 10;
```

---

## 3. ¿Cuál es el rol de una clave externa en un esquema de base de datos normalizado?

- [ ] Almacenar varios tipos de datos dentro de una sola columna.
- [ ] Crear una relación entre dos tablas haciendo referencia a la clave principal de otra tabla.
- [ ] Identificar de forma única cada fila dentro de una tabla.

---

## 4. Una empresa debe asegurarse de que una consulta compleja que se ejecuta con frecuencia se ejecute rápidamente sin modificar las tablas subyacentes. ¿Qué objeto de base de datos sería la solución más adecuada?

- [ ] Procedimiento almacenado.
- [ ] Vista.
- [ ] Índice.

---

## 5. ¿Cuál es la principal ventaja de usar índices en una base de datos relacional y cómo afectan al rendimiento?

- [ ] Los índices reducen el espacio de almacenamiento necesario al comprimir los datos de columna, lo que mejora el rendimiento general de la base de datos.
- [ ] Los índices aceleran la recuperación de datos mediante la creación de una copia ordenada de datos de columna, lo que mejora el rendimiento de las consultas.
- [ ] Los índices ayudan a mantener la integridad de los datos aplicando restricciones de clave principal, lo que acelera las operaciones de modificación de datos.

---

## 6. Una base de datos experimenta con frecuencia un rendimiento lento de las consultas debido a escaneos de tablas grandes. ¿Qué objeto de base de datos se puede implementar para mitigar este problema de forma eficaz?

- [ ] Procedimiento almacenado.
- [ ] Índice.
- [ ] Vista.

---

## 7. ¿Cómo puede asegurarse de que una columna de una tabla recién creada debe contener siempre un valor en SQL?

- [ ] Especificar la columna como `NOT NULL` durante la creación de la tabla.
- [ ] Utilizar una restricción `DEFAULT` con la columna.
- [ ] Crear un índice en la columna.

---

## 8. ¿Cuál es la principal ventaja de usar una clave compuesta en un esquema de base de datos?

- [ ] Simplifica el esquema reduciendo el número de tablas.
- [ ] Permite almacenar entradas duplicadas en varias tablas.
- [ ] Identifica de forma única una fila mediante una combinación de varias columnas cuando una sola columna no es suficiente.

---

## 9. Al crear un esquema de base de datos normalizado, ¿cómo debe controlar atributos opcionales, como un nombre intermedio para los clientes?

- [ ] Crear una tabla independiente para el atributo opcional y usar una relación de clave externa.
- [ ] Excluir el atributo opcional del esquema de base de datos para simplificar el diseño.
- [ ] Incluir el atributo opcional como una columna que acepta valores NULL en la tabla pertinente.
- [ ] # Resumen

**Completado**  
**100 XP**  
**Duración:** 1 minuto

Las **bases de datos relacionales** son una forma común mediante la cual las aplicaciones transaccionales almacenan y administran datos.

Están compuestas por:

- Un esquema de tablas.
- Relaciones entre tablas mediante valores de clave comunes.
- Consultas y manipulación de datos mediante SQL.

El lenguaje **SQL** permite consultar y modificar los datos almacenados en las tablas.

Además, una base de datos relacional puede enriquecerse mediante la creación de objetos como:

- **Vistas**
- **Procedimientos almacenados**
- **Índices**

---

# En este módulo has aprendido a:

- Identificar las características de los datos relacionales.
- Definir el concepto de normalización.
- Identificar los tipos de instrucciones SQL.
- Identificar objetos comunes de bases de datos relacionales.

---

# Pasos siguientes

Ahora que has aprendido sobre las **bases de datos relacionales**, considera obtener más información sobre las cargas de trabajo relacionadas con datos en **Microsoft Azure** mediante la realización de una certificación de Microsoft en:

**Aspectos básicos de datos de Azure**

# Introducción a Azure

Elige la cuenta de Azure adecuada para ti:

- Paga según el uso.
- Prueba Azure gratis durante 30 días.
- Regístrate para comenzar a utilizar Azure.

  # Exploración de los Servicios de Bases de Datos Relacionales en Azure

  # Resumen

Las **bases de datos relacionales** son una forma común mediante la cual las aplicaciones transaccionales almacenan y administran datos.

Están compuestas por:

- Un esquema de tablas.
- Relaciones entre tablas mediante valores de clave comunes.
- Consultas y manipulación de datos utilizando SQL.

El lenguaje **SQL** permite consultar y modificar los datos almacenados en las tablas.

Además, una base de datos relacional puede enriquecerse mediante la creación de objetos como:

- **Vistas**
- **Procedimientos almacenados**
- **Índices**

---

# En este módulo has aprendido a:

- Identificar las características de los datos relacionales.
- Definir el concepto de normalización.
- Identificar los tipos de instrucciones SQL.
- Identificar objetos comunes de bases de datos relacionales.

---

# Pasos siguientes

Ahora que has aprendido sobre las **bases de datos relacionales**, considera obtener más información sobre las cargas de trabajo relacionadas con datos en **Microsoft Azure** mediante la realización de una certificación de Microsoft en:

**Aspectos básicos de datos de Azure**

---

# Introducción a Azure
# Resumen



Las **bases de datos relacionales** son una forma común mediante la cual las aplicaciones transaccionales almacenan y administran datos.

Están compuestas por:

- Un esquema de tablas.
- Relaciones entre tablas mediante valores de clave comunes.
- Consultas y manipulación de datos utilizando SQL.

El lenguaje **SQL** permite consultar y modificar los datos almacenados en las tablas.

Además, una base de datos relacional puede enriquecerse mediante la creación de objetos como:



---

# En este módulo has aprendido a:

- Identificar las características de los datos relacionales.
- Definir el concepto de normalización.
- Identificar los tipos de instrucciones SQL.
- Identificar objetos comunes de bases de datos relacionales.

---

# Pasos siguientes

Ahora que has aprendido sobre las **bases de datos relacionales**, considera obtener más información sobre las cargas de trabajo relacionadas con datos en **Microsoft Azure** mediante la realización de una certificación de Microsoft en:

**Aspectos básicos de datos de Azure**

---

# Introducción a Azure

Elección del formato de contenido preferido
Azure admite varios servicios de base de datos, lo que permite ejecutar en la nube diversos sistemas de administración de bases de datos relacionales conocidos, por ejemplo, SQL Server, PostgreSQL y MySQL.

La mayoría de Azure servicios de base de datos están totalmente administrados, por lo que no es necesario controlar el mantenimiento de la infraestructura. Incluyen alta disponibilidad integrada y admiten el escalado a la distribución global. Azure los servicios de base de datos también proporcionan características de seguridad como la supervisión automática y la detección de amenazas, así como el ajuste automático del rendimiento.

En este módulo, explorará las opciones disponibles para los servicios de bases de datos relacionales en Azure.

 Nota:

Reconocemos que a diferentes personas les gusta aprender de diferentes maneras. Puede optar por completar este módulo en formato basado en vídeo o puede leer el contenido como texto e imágenes. El texto contiene más detalle que los vídeos, por lo que, en algunos casos, es posible que desee hacer referencia a él como material complementario para la presentación de vídeo.

# Descripción de los servicios y las capacidades de Azure SQL

**Completado**  
**100 XP**  
**Duración:** 10 minutos

Azure SQL es un término colectivo utilizado para referirse a una familia de servicios de bases de datos basados en **Microsoft SQL Server en Azure**.

Los servicios principales de Azure SQL son:

- **SQL Server en Azure Virtual Machines (VMs)**
- **Azure SQL Managed Instance**
- **Azure SQL Database**

---

# Servicios de Azure SQL

## SQL Server en Azure Virtual Machines (VMs)

Es una máquina virtual que se ejecuta en Azure con SQL Server instalado.

Este servicio pertenece al modelo:

**Infraestructura como servicio (IaaS)**

Permite virtualizar:

- Hardware.
- Almacenamiento.
- Redes.
- Procesamiento.

Es una buena opción para migraciones **lift-and-shift** desde instalaciones locales de SQL Server hacia la nube.

---

## Azure SQL Managed Instance

Es un servicio:

**Plataforma como servicio (PaaS)**

Proporciona una compatibilidad casi completa con instancias locales de SQL Server.

Permite abstraer:

- Hardware.
- Sistema operativo.

Incluye administración automatizada de:

- Actualizaciones de software.
- Copias de seguridad.
- Tareas de mantenimiento.

Reduce la carga administrativa necesaria para mantener una instancia de base de datos.

---

## Azure SQL Database

Es un servicio:

**PaaS totalmente administrado**

Diseñado para aplicaciones en la nube.

Incluye capacidades principales de SQL Server y es una buena opción para crear nuevas aplicaciones cloud.

---

# Comparación de servicios Azure SQL

| Característica | SQL Server en Azure VM | Azure SQL Managed Instance | Azure SQL Database |
|---|---|---|---|
| Tipo de servicio | IaaS | PaaS | PaaS |
| Compatibilidad SQL Server | Totalmente compatible con instalaciones locales | Casi completa | Funcionalidades principales |
| Arquitectura | Instancias SQL Server instaladas en máquinas virtuales | Instancias administradas con varias bases de datos | Bases de datos individuales o grupos elásticos |
| Disponibilidad | 99,99 % | 99,99 % | 99,995 % |
| Administración | Administrada por el usuario | Automatizada | Automatizada |
| Caso de uso | Migraciones con control total | Migraciones con mínimos cambios | Nuevas aplicaciones cloud |

---

# SQL Server en Azure Virtual Machines

SQL Server en máquinas virtuales permite utilizar versiones completas de SQL Server en Azure sin administrar hardware físico.

Este enfoque replica una instalación tradicional de SQL Server.

Es adecuado para:

- Migraciones rápidas a la nube.
- Aplicaciones que requieren acceso al sistema operativo.
- Escenarios híbridos.

> Un entorno híbrido combina recursos locales y recursos en la nube.

---

## Ventajas de SQL Server en Azure VM

Permite:

- Crear entornos rápidos de desarrollo y pruebas.
- Migrar aplicaciones existentes con pocos cambios.
- Escalar verticalmente recursos como:
  - Memoria.
  - CPU.
  - Espacio en disco.

---

# Azure SQL Managed Instance

Azure SQL Managed Instance permite ejecutar una instancia administrada de SQL Server en Azure.

Características:

- Compatibilidad con SQL Server local.
- Varias bases de datos por instancia.
- Copias de seguridad automáticas.
- Actualizaciones automáticas.
- Supervisión integrada.
- Seguridad administrada.

---

## Casos de uso

Es recomendable cuando:

- Se desea migrar SQL Server local mediante lift-and-shift.
- Se necesitan pocos cambios en aplicaciones existentes.
- Se requieren características avanzadas de SQL Server.

---

## Ventajas empresariales

Automatiza tareas como:

- Instalación y actualización de software.
- Copias de seguridad.
- Recuperación.
- Alta disponibilidad.
- Supervisión del rendimiento.

También admite:

- Inicios de sesión SQL Server.
- Autenticación mediante Microsoft Entra ID.

---

# Azure SQL Database

Azure SQL Database es una oferta PaaS de Microsoft.

Permite crear bases de datos administradas en la nube.

Un servidor SQL Database es una estructura lógica que administra:

- Bases de datos.
- Inicios de sesión.
- Reglas de firewall.
- Auditoría.
- Detección de amenazas.

---

# Opciones de Azure SQL Database

## Base de datos única

Permite crear una única base de datos SQL administrada.

Características:

- Escalabilidad según necesidad.
- Administración automática.
- Recursos asignados dinámicamente.

---

## Grupo elástico

Permite compartir recursos entre varias bases de datos.

Comparte:

- Memoria.
- Almacenamiento.
- Capacidad de procesamiento.

Es útil cuando las bases de datos tienen cargas variables.

Ejemplo:

- Una base de datos de nóminas puede necesitar muchos recursos al final del mes.
- Una base de datos de informes puede necesitar más recursos durante ciertos periodos.

---

## Hiperescala

El nivel Hiperescala permite:

- Bases de datos muy grandes.
- Hasta 100 TB.
- Escalado rápido.
- Copias de seguridad rápidas.

---

# Casos de uso de Azure SQL Database

Azure SQL Database es ideal para:

- Nuevas aplicaciones cloud.
- Aplicaciones modernas.
- Sistemas que requieren alta disponibilidad.
- Aplicaciones con cargas variables.

---

# Ventajas empresariales de Azure SQL Database

## Administración automática

Azure realiza:

- Actualizaciones.
- Parches de seguridad.
- Mantenimiento.

---

## Escalabilidad

Permite aumentar recursos como:

- Procesamiento.
- Memoria.
- Almacenamiento.

Sin realizar actualizaciones manuales complejas.

---

## Alta disponibilidad

Proporciona:

- Disponibilidad del 99,995 %.
- Restauración a un punto en el tiempo.
- Replicación entre regiones.

---

# Seguridad

Azure SQL Database incluye:

## Advanced Threat Protection

Proporciona:

- Evaluaciones de vulnerabilidad.
- Detección de actividades sospechosas.
- Alertas de seguridad.
- Protección frente a ataques SQL.

---

## Auditoría

Registra eventos de la base de datos y permite:

- Revisar actividad.
- Cumplir normativas.
- Detectar anomalías.

---

## Cifrado

Protege los datos:

- En reposo.
- En tránsito.

---

# Inteligencia artificial en Azure SQL Database

Azure SQL Database incorpora asistencia mediante IA para:

- Optimización de consultas.
- Análisis de rendimiento.
- Resolución de problemas mediante lenguaje natural.

 Descripción de los servicios de Azure para bases de datos de código abierto

Elección del formato de contenido preferido
Además de los servicios de Azure SQL, los servicios de datos de Azure están disponibles para otros sistemas populares de bases de datos relacionales, como MySQL y PostgreSQL. La razón principal de incluir estos servicios es permitir que las organizaciones que los usan en aplicaciones locales migren a Azure rápidamente, sin necesidad de realizar cambios significativos en sus aplicaciones.

¿Qué son MySQL y PostgreSQL?
MySQL y PostgreSQL son sistemas de administración de bases de datos relacionales que se adaptan a diferentes especializaciones.

MySQL comenzó siendo un sistema de administración de bases de datos de código abierto fácil de usar. Es la base de datos relacional de código abierto líder para aplicaciones de pila de Linux, Apache, MySQL y PHP (LAMP). Está disponible en varias ediciones; Community, Estándar y Enterprise. La edición Community está disponible de forma gratuita y se ha usado históricamente como sistema de administración de bases de datos para aplicaciones web que se ejecutan en Linux. También hay versiones disponibles para Windows. La edición Estándar ofrece mayor rendimiento y usa una tecnología diferente para almacenar los datos. La edición Enterprise proporciona un completo conjunto de herramientas y características, entre las que se incluyen seguridad mejorada, disponibilidad y escalabilidad. Las ediciones Estándar y Enterprise son las más usadas por las organizaciones comerciales, aunque estas versiones del software no son gratuitas.

PostgreSQL es una base de datos híbrida de objetos relacionales. Puede almacenar datos en tablas relacionales, pero una base de datos PostgreSQL también le permite almacenar tipos de datos personalizados, con sus propias propiedades no relacionales. El sistema de administración de bases de datos es extensible, es decir, se pueden agregar módulos de código a la base de datos, los cuales pueden ejecutarse mediante consultas. Otra característica clave es su capacidad de almacenar y manipular datos geométricos, como líneas, círculos y polígonos.

PostgreSQL dispone de su propio lenguaje de consulta llamado pgsql. Este lenguaje es una variante del lenguaje de consulta relacional estándar, SQL, y cuenta con características que permiten escribir procedimientos almacenados que se ejecutan en la base de datos.

Azure Database for MySQL
Azure Database for MySQL es una implementación de PaaS de MySQL en la nube de Azure que se basa en la edición Community de MySQL.

El servicio Azure Database for MySQL incluye alta disponibilidad sin costos adicionales y escalabilidad según sea necesario. Solo paga por lo que usa. Se proporcionan copias de seguridad automáticas, con restauración a un momento dado durante un máximo de 35 días (siete días de forma predeterminada).

El servidor ofrece seguridad de conexión para aplicar las reglas de firewall y, opcionalmente, requerir conexiones SSL. Muchos parámetros de servidor permiten configurar opciones del servidor, como los modos de bloqueo, el número máximo de conexiones y los tiempos de espera.

Azure Database for MySQL proporciona un sistema de base de datos global que se puede escalar verticalmente a bases de datos grandes sin necesidad de administrar el hardware, los componentes de red, los servidores virtuales, las revisiones de software y otros componentes subyacentes.

Hay algunas operaciones que no están disponibles con Azure Database for MySQL. Estas funciones están relacionadas principalmente con la seguridad y la administración. Azure administra estos aspectos del propio servidor de bases de datos.

Ventajas de Azure Database for MySQL
Azure Database for MySQL ofrece las siguientes características:

Características de alta disponibilidad integradas.
Rendimiento predecible.
Escalado sencillo que responde rápidamente a la demanda.
Protección de los datos, tanto en reposo como en movimiento.
Copias de seguridad automáticas y restauración a un momento dado, durante un máximo de 35 días (siete días de forma predeterminada).
Seguridad de categoría empresarial y cumplimiento normativo.
El sistema utiliza un modelo de precios de pago por uso, de manera que solo pagas por lo que realmente utilizas.

Los servidores de Azure Database for MySQL proporcionan funcionalidades de supervisión para agregar alertas y para ver las métricas y los registros.

Azure Database for MySQL: servidor flexible
La opción de implementación flexible-servidor es un servicio de base de datos totalmente administrado diseñado para proporcionar un control y flexibilidad más granulares sobre las funciones de administración de bases de datos y las opciones de configuración. Proporciona controles de optimización de costos y es la opción de implementación recomendada para las nuevas cargas de trabajo. Con una cuenta gratuita de Azure, puede usar servidor flexible gratis durante 12 meses.

Base de Datos de Azure para PostgreSQL
Si prefiere PostgreSQL, puede elegir Azure Database for PostgreSQL ejecutar una implementación de PaaS de PostgreSQL en la nube de Azure. Este servicio proporciona las mismas ventajas de disponibilidad, rendimiento, escalado, seguridad y administración que MySQL.

Algunas características de las bases de datos locales de PostgreSQL no están disponibles en Azure Database for PostgreSQL. Estas características están relacionadas principalmente con las extensiones que los usuarios pueden agregar a una base de datos para realizar tareas especializadas, como escribir procedimientos almacenados en varios lenguajes de programación (distintos de pgsql, el cual está disponible) e interactuar directamente con el sistema operativo. Se admite un conjunto básico de las extensiones que se usan con más frecuencia, y la lista de extensiones disponibles se revisa continuamente.

Servidor flexible de base de datos de Azure para PostgreSQL
La opción de implementación de servidor flexible para PostgreSQL es un servicio de base de datos totalmente administrado. Proporciona un elevado nivel de control y personalizaciones de configuración de servidor, así como controles de optimización de costos. Con una cuenta gratuita de Azure, puede usar servidor flexible gratis durante 12 meses.

Ventajas de Azure Database for PostgreSQL
Azure Database for PostgreSQL es un servicio de alta disponibilidad. Integra mecanismos de conmutación por error y de detección de errores.

Los usuarios de PostgreSQL están familiarizados con la herramienta pgAdmin, que puede usar para administrar y supervisar una base de datos de PostgreSQL. Puede seguir usando esta herramienta para conectarse a Azure Database for PostgreSQL, Aun así, algunas funcionalidades centradas en el servidor, como la realización de copias de seguridad y la restauración del servidor, no están disponibles porque Microsoft se encarga de administrar y mantener el servidor.

Azure Database for PostgreSQL registra información de las consultas que se ejecutan en las bases de datos del servidor y las guarda en una base de datos llamada azure_sys. Puede consultar la vista query_store.qs_view para ver esta información y usarla para supervisar las consultas que ejecutan los usuarios. Esta información puede resultar muy valiosa si necesita ajustar las consultas que realizan las aplicaciones. 
# Evaluación del módulo


Esta evaluación comprueba la comprensión del módulo.

A diferencia de actividades anteriores, no se proporcionará información sobre respuestas individuales; únicamente se indicará si las respuestas son correctas o incorrectas.

El objetivo es medir los conocimientos adquiridos. Se recomienda revisar el contenido del módulo antes de comenzar.


## 1. Su empresa necesita una solución de base de datos relacional que proporcione entornos de desarrollo y pruebas rápidos sin invertir en hardware local. ¿Qué servicio de Azure es más adecuado?

- SQL Server en Azure Virtual Machines
- Instancia Gestionada de Azure SQL
- Azure SQL Database

-

## 2. Una empresa requiere un servicio SQL con escalado automático y uso compartido de recursos en varias bases de datos para controlar cargas de trabajo variables. ¿Qué servicio es adecuado?

- Azure SQL Database usando pools elásticos
- SQL Server en Azure Virtual Machines
- Instancia Gestionada de Azure SQL

---

## 3. ¿Qué servicio Azure SQL sería más adecuado para una empresa que busca migrar sus bases de datos de SQL Server locales existentes a la nube con cambios mínimos de código y compatibilidad total?

- Azure SQL Database
- SQL Server en Azure Virtual Machines
- Instancia Gestionada de Azure SQL

---

## 4. Una organización busca una solución de base de datos de código abierto totalmente administrada con alta disponibilidad y seguridad de nivel empresarial para sus aplicaciones web. ¿Qué servicio de Azure deben considerar?

- SQL Server en Azure Virtual Machines
- Base de Datos Azure para MySQL
- Azure SQL Database

---

## 5. ¿Qué servicio Azure SQL sería mejor para un escenario donde la elasticidad de la base de datos y la asignación de recursos deben administrarse entre varias bases de datos?

- Instancia Gestionada de Azure SQL
- SQL Server en Azure Virtual Machines
- Azure SQL Database con Elastic Pool

---

## 6. Su organización está desarrollando una nueva aplicación en la nube que requiere las características más recientes de SQL Server y alta disponibilidad. ¿Qué servicio Azure SQL sería más adecuado?

- Instancia Gestionada de Azure SQL
- Azure SQL Database
- SQL Server en Azure Virtual Machines

---

## 7. ¿Qué afirmación identifica correctamente una diferencia clave entre Azure SQL Database y Azure SQL Managed Instance?

- Azure SQL Database admite bases de datos únicas o grupos elásticos, mientras que Azure SQL Managed Instance admite varias bases de datos en grupos de instancias.
- Azure SQL Database requiere actualizaciones manuales y copias de seguridad, mientras que Azure SQL Managed Instance automatiza estas tareas.
- Azure SQL Database ofrece casi 100 % de compatibilidad con SQL Server, a diferencia de Azure SQL Managed Instance.

---

## 8. Una empresa planea migrar su base de datos MySQL a Azure para mejorar la escalabilidad y las copias de seguridad automatizadas. ¿Qué servicio de Azure debe elegir?

- Azure SQL Database
- Instancia Gestionada de Azure SQL
- Base de Datos Azure para MySQL

---

## 9. Su organización planea implementar una plataforma global de comercio electrónico que requiera alta disponibilidad y recuperación ante desastres en varias regiones. ¿Qué servicio de base de datos de Azure debe elegir?

- Instancia Gestionada de Azure SQL
- SQL Server en Azure Virtual Machines
- Azure SQL Database con replicación geográfica

# Resumen


Azure admite una variedad de **servicios de bases de datos** que pueden utilizarse para:

- Crear nuevas aplicaciones en la nube.
- Migrar aplicaciones existentes hacia la nube.
- Administrar datos con soluciones escalables y seguras.

---

# En este módulo has aprendido a:

- Identificar las opciones disponibles de los **servicios Azure SQL**.
- Identificar las opciones de **bases de datos de código abierto en Azure**.
- Aprovisionar un **servicio de base de datos en Azure**.
