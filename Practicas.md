# 🚀 Prácticas de Laboratorio – Ruby on Rails

## 🎯 Objetivo

Aplicar los conceptos fundamentales de **Ruby on Rails** mediante el desarrollo de aplicaciones web que utilicen:

* 🏗️ Arquitectura MVC
* 🗄️ Bases de datos relacionales
* 🔄 Operaciones CRUD
* 🔗 Relaciones entre modelos
* ✅ Validaciones

---

# 📚 Práctica 1: Gestión de Materias

## 📝 Descripción

Desarrollar una aplicación que permita registrar y administrar las materias de una institución académica.

## 🗄️ Esquema de Base de Datos

### 📖 Tabla: Materias

| Campo      | Tipo     |
| ---------- | -------- |
| nombre     | string   |
| codigo     | string   |
| creditos   | integer  |

## ✅ Requerimientos

* Crear el modelo **Materia**.
* Generar el scaffold correspondiente.
* Implementar las operaciones CRUD:

  * ➕ Crear materia.
  * 🔍 Consultar materias.
  * ✏️ Editar materia.
  * ❌ Eliminar materia.
* Mostrar una tabla con todas las materias registradas.
* Implementar las siguientes validaciones:

  * 📌 Nombre obligatorio.
  * 🔒 Código único.
  * 📊 Créditos mayores a cero.

## 🎓 Competencias que se evalúan

* Creación de modelos.
* Uso de migraciones.
* Generación de scaffolds.
* Validaciones básicas.

---

# 👨‍🎓 Práctica 2: Gestión de Estudiantes y Materias

## 📝 Descripción

Desarrollar una aplicación para administrar estudiantes y asociarlos a una materia.

## 🗄️ Esquema de Base de Datos

### 📖 Tabla: Materias

| Campo  | Tipo    |
| ------ | ------- |
| id     | integer |
| nombre | string  |
| codigo | string  |

### 👨‍🎓 Tabla: Estudiantes

| Campo      | Tipo    |
| ---------- | ------- |
| id         | integer |
| nombre     | string  |
| apellido   | string  |
| correo     | string  |
| materia_id | integer |

## 🔗 Relación

```text
📖 Materia (1) ────────── (N) 👨‍🎓 Estudiantes
```

Una materia puede tener muchos estudiantes.

## ✅ Requerimientos

* Crear ambos modelos.
* Configurar las relaciones:

  * 📖 Materia tiene muchos estudiantes.
  * 👨‍🎓 Estudiante pertenece a una materia.
* Crear formularios para registrar estudiantes.
* Mostrar en la vista:

  * 👤 Nombre completo.
  * 📧 Correo electrónico.
  * 📚 Materia asignada.
* Implementar validaciones:

  * 📧 Correo obligatorio.
  * 👤 Nombre obligatorio.
* Mostrar la cantidad de estudiantes por materia.

## 🎓 Competencias que se evalúan

* Relaciones 1:N.
* Claves foráneas.
* Consultas mediante asociaciones.
* Formularios en Rails.

---

# 🏛️ Práctica 3: Sistema de Matrícula Académica

## 📝 Descripción

Desarrollar un sistema donde los estudiantes puedan matricular varias materias.

## 🗄️ Esquema de Base de Datos

### 👨‍🎓 Tabla: Estudiantes

| Campo  | Tipo    |
| ------ | ------- |
| id     | integer |
| nombre | string  |
| correo | string  |

### 📖 Tabla: Materias

| Campo  | Tipo    |
| ------ | ------- |
| id     | integer |
| nombre | string  |
| codigo | string  |

### 📋 Tabla: Matrículas

| Campo           | Tipo    |
| --------------- | ------- |
| id              | integer |
| estudiante_id   | integer |
| materia_id      | integer |
| fecha_matricula | date    |

## 🔗 Relación

```text
👨‍🎓 Estudiantes
       │
       │
       ▼
📋 Matrículas
       ▲
       │
       │
📖 Materias
```

Relación **Muchos a Muchos (N:N)**.

## ✅ Requerimientos

* Crear los tres modelos.
* Configurar correctamente las asociaciones.
* Permitir matricular estudiantes en varias materias.
* Mostrar:

  * 👨‍🎓 Estudiante.
  * 📖 Materias matriculadas.
  * 📅 Fecha de matrícula.
* Evitar matrículas duplicadas.
* Crear una página para visualizar todas las matrículas.
* Mostrar cuántas materias tiene matriculado cada estudiante.

## 🎓 Competencias que se evalúan

* Relaciones N:N.
* Tablas intermedias.
* Consultas avanzadas.
* Validaciones personalizadas.

---

# ⭐ Desafío 

Implementar mejoras visuales utilizando:

* 🎨 Tailwind CSS.
* 🃏 Tarjetas (Cards).
* 📱 Diseño responsivo.
* 🔔 Mensajes flash.
* 🧭 Barra de navegación.
* 🌙 Modo oscuro (opcional).

---
