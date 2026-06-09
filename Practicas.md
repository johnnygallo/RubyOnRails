# 🚀 Prácticas de Laboratorio – Ruby on Rails

## 🎯 Objetivo

Aplicar los conceptos fundamentales de **Ruby on Rails** mediante el desarrollo de aplicaciones web que utilicen:

* 🏗️ Arquitectura MVC
* 🗄️ Bases de datos relacionales
* 🔄 Operaciones CRUD
* 🔗 Relaciones entre modelos
* ✅ Validaciones

---
# 🛒 Práctica 1: Sistema de Mini Súper

## 📝 Descripción

Desarrollar una aplicación web para administrar un mini súper.

El sistema deberá permitir:

* 📦 Gestionar productos.
* 🏷️ Clasificar productos por categorías y subcategorías.
* 🧾 Registrar facturas de venta.
* 💰 Calcular el total de cada factura.
* 📈 Llevar un control básico de ingresos generados por las ventas.

Toda la interfaz debe desarrollarse utilizando **Ruby on Rails + Tailwind CSS**.

---
## 🗄️ Esquema de Base de Datos

```text
🏷️ Categoría
- nombre:string

📂 Subcategoría
- nombre:string
- categoria_id:integer

📦 Producto
- nombre:string
- precio:decimal
- stock:integer
- subcategoria_id:integer

🧾 Factura
- fecha:datetime
- total:decimal

🛒 DetalleFactura
- factura_id:integer
- producto_id:integer
- cantidad:integer
- subtotal:decimal
```
---

## ✅ Requerimientos

### 📦 Gestión de Productos

* Crear CRUD completo de productos.
* Crear CRUD completo de categorías.
* Crear CRUD completo de subcategorías.
* Mostrar:

  * Nombre del producto.
  * Categoría.
  * Subcategoría.
  * Precio.
  * Stock disponible.

---

### 🧾 Gestión de Facturas

* Crear una factura.

* Agregar múltiples productos a una factura.

* Seleccionar cantidad de cada producto.

* Calcular automáticamente:

  * Subtotal por línea.
  * Total de la factura.

* Mostrar el detalle completo de la compra.

---

### 📈 Reporte de Ingresos

Crear una página que muestre:

* Total de facturas registradas.
* Total de ingresos generados.
* Cantidad de productos vendidos.

---

## ✅ Validaciones

### Categorías

* Nombre obligatorio.

### Subcategorías

* Nombre obligatorio.

### Productos

* Nombre obligatorio.
* Precio mayor que cero.
* Stock mayor o igual a cero.

### Facturas

* Deben contener al menos un producto.

### Detalle Factura

* Cantidad mayor que cero.

---

# 🔐 Práctica 2: Autenticación con JWT para el Sistema de Mini Súper

## 🎯 Objetivo

Extender la aplicación desarrollada en la Práctica 1 implementando autenticación mediante **JSON Web Tokens (JWT)** para proteger los recursos del sistema.

Los usuarios deberán autenticarse para poder acceder a las funcionalidades del Mini Súper.

---

# 📝 Descripción

Utilizando la aplicación desarrollada en la práctica anterior:

* 🛒 Sistema de Mini Súper
* 📦 Gestión de productos
* 🏷️ Categorías y subcategorías
* 🧾 Facturación
* 📈 Reporte de ingresos

Agregar un sistema de autenticación basado en **JWT** que permita:

* Registrar usuarios.
* Iniciar sesión.
* Generar tokens.
* Validar tokens.
* Restringir el acceso a los endpoints protegidos.

---

# 🗄️ Nueva Tabla: Usuarios

```text
👤 Usuario
- nombre:string
- email:string
- password_digest:string
```

> Utilizar `has_secure_password` para el manejo seguro de contraseñas.

---

# 🔗 Flujo de Autenticación

```text
👤 Usuario
      │
      ▼
🔑 Login
      │
      ▼
🎟️ JWT Token
      │
      ▼
🔒 Endpoints Protegidos
```

---

# ✅ Requerimientos

## 👤 Gestión de Usuarios

Implementar:

* Registro de usuarios.
* Inicio de sesión.
* Cierre de sesión (opcional).
* Validación de credenciales.

---

## 🔑 Generación de JWT

Al iniciar sesión correctamente:

* Generar un JWT.
* Retornar el token al usuario.
* Incluir información básica del usuario dentro del payload.

---

## 🔒 Protección de Rutas

Los siguientes módulos deberán requerir autenticación:

* 📦 Productos
* 🏷️ Categorías
* 📂 Subcategorías
* 🧾 Facturas
* 📈 Reporte de ingresos

Si no se envía un token válido:

```json
{
  "error": "No autorizado"
}
```
# 📄 Práctica 3: Generación de Facturas en PDF

## 🎯 Objetivo

Extender la aplicación desarrollada en las prácticas anteriores para generar automáticamente una factura en formato PDF después de completar una venta.

El sistema deberá permitir descargar la factura generada desde la interfaz web.

---

# 📝 Descripción

Partiendo del sistema desarrollado previamente:

* 🛒 Gestión de productos.
* 🧾 Facturación.
* 🔐 Autenticación con JWT.

Implementar la generación de facturas en formato PDF cuando una venta sea finalizada.

---

# 🚀 Flujo de Funcionamiento

```text
🛒 Agregar Productos
          │
          ▼
🧾 Crear Factura
          │
          ▼
💳 Pagar Factura
          │
          ▼
📄 Generar PDF
          │
          ▼
🪟 Modal de Confirmación
          │
          ▼
⬇️ Descargar Factura
```

---

# ✅ Requerimientos

## 📄 Generación de PDF

Al presionar el botón:

```text
💳 Pagar Factura
```

El sistema deberá:

1. Registrar la venta.
2. Calcular el total.
3. Generar un archivo PDF.
4. Asociar el PDF a la factura.
5. Mostrar una ventana modal.

---

## 🪟 Modal de Confirmación

Después de completar el pago deberá mostrarse un modal similar a:

```text
✅ Factura generada correctamente

La compra ha sido registrada.

[⬇️ Descargar Factura]
[❌ Cerrar]
```

---

## 📋 Información del PDF

El documento debe incluir:

### Encabezado

* Nombre del Mini Súper.
* Fecha de emisión.
* Número de factura.

### Información de la compra

| Producto | Cantidad | Precio | Subtotal |
| -------- | -------- | ------ | -------- |

### Resumen

* Total de productos.
* Monto total pagado.

### Pie de página

```text
Gracias por su compra.
```

---
