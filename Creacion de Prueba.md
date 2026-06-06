# 📚 Sistema de Gestión de Tareas Académicas con Ruby on Rails

## 🚀 Crear el Proyecto

```bash
rails new tareas_academicas
cd tareas_academicas
```

---

## 📖 Crear el Controller y Modelo de Materias

La tabla **materia** almacenará las materias o cursos donde se asignan las tareas.

```bash
rails generate controller Materias
rails generate model Materia name:string active:boolean
```

---

## 📝 Crear el Scaffold de Tareas

La tabla **tareas** almacenará las actividades pendientes de cada materia.

```bash
rails generate scaffold Tarea title:string description:text fecha:date priority:integer completed:boolean materia:references
```

---

## ⚙️ Configurar Valores por Defecto

Editar la migración de **Materia**:

```ruby
    t.string :name, null: false
    t.boolean :active, default: true, null: false
```

Editar la migración de **Tarea**:

```ruby
    t.string :title, null: false
    t.text :description, null: false
    t.date :fecha, null: false
    t.integer :priority, default: 1, null: false
    t.boolean :completed, default: false, null: false
    t.references :materia, null: false, foreign_key: true
```

---

## 🗄️ Ejecutar las Migraciones

```bash
rails db:migrate
```

---

## 🔗 Configurar Relaciones

### Modelo Materia

```ruby
class Materia < ApplicationRecord
    has_many :tareas, dependent: :destroy
    validates :name, presence: { message: "El nombre de la materia es obligatorio" }
end

```

### Modelo Tarea

```ruby
class Tarea < ApplicationRecord
  belongs_to :materia
end
```

---

## 🛣️ Verificar las Rutas

```bash
rails routes
```

### En config/routes.rb
#### Cambiar el root del proyecto

```bash
Rails.application.routes.draw do
  resources :tareas
  resources :materias
  
  root "materias#index"
end

```


Deberías tener rutas similares a:

```bash
materia_path
materia_index_path

tareas_path
tarea_path
```

---

## ▶️ Ejecutar la Aplicación

```bash
bin/dev
```

o

```bash
rails server
```

Abrir en:

```text
http://localhost:3000
```

---


## 📊 Resultado Esperado del Schema
## 🎨 Instalar Tailwind CSS


### MacOS - Linux
```bash
bundle add tailwindcss-rails
bin/rails tailwindcss:install
bin/rails tailwindcss:watch
```

### Windows
```bash
bundle add tailwindcss-rails
rails tailwindcss:install
rails tailwindcss:watch
```


### Modeificar archivo app/assets/tailwind/application.css
```bash
@import "tailwindcss";

/* ========================================
   BOTONES
======================================== */

.btn {
    @apply inline-flex items-center rounded-lg px-4 py-2 font-medium transition;
}

.btn-primary {
    @apply bg-blue-600 text-white hover:bg-blue-700;
}

.btn-success {
    @apply bg-green-600 text-white hover:bg-green-700;
}

.btn-danger {
    @apply bg-red-600 text-white hover:bg-red-700;
}

.btn-warning {
    @apply bg-yellow-500 text-white hover:bg-yellow-600;
}

/* ========================================
   LAYOUT
======================================== */

.page-container {
    @apply mx-auto max-w-7xl px-6 py-8;
}

.actions {
    @apply flex flex-wrap gap-3 mt-6;
}

/* ========================================
   CARDS
======================================== */

.card {
    @apply bg-white rounded-xl shadow-md border border-gray-200 p-6;
}

.card-header {
    @apply text-xl font-bold text-gray-800 mb-4;
}

.card-section {
    @apply space-y-3;
}

/* ========================================
   TABLAS
======================================== */

.table-custom {
    @apply w-full border-collapse bg-white rounded-xl overflow-hidden shadow;
}

.table-custom th {
    @apply bg-gray-100 text-left px-4 py-3 font-semibold;
}

.table-custom td {
    @apply px-4 py-3 border-t;
}

/* ========================================
   ALERTAS
======================================== */

.alert-success {
    @apply bg-green-100 border border-green-300 text-green-800 px-4 py-3 rounded-lg;
}

.alert-danger {
    @apply bg-red-100 border border-red-300 text-red-800 px-4 py-3 rounded-lg;
}

/* ========================================
   BADGES
======================================== */

.badge-success {
    @apply inline-flex items-center rounded-full bg-green-100 px-3 py-1 text-sm font-medium text-green-800;
}

.badge-danger {
    @apply inline-flex items-center rounded-full bg-red-100 px-3 py-1 text-sm font-medium text-red-800;
}

/* ========================================
   TIPOGRAFÍA
======================================== */

.titulo {
    @apply text-2xl font-bold text-gray-800;
}

.item-label {
    @apply text-sm font-semibold text-gray-500;
}

.item-value {
    @apply text-gray-800;
}

.link-primary {
    @apply text-blue-600 hover:text-blue-800 font-medium;
}

/* ========================================
   FORMULARIOS
======================================== */
.form-card {
    @apply bg-white rounded-xl shadow-md border border-gray-200 p-6;
}

.form-group {
    @apply mb-5;
}

.form-label {
    @apply block text-sm font-semibold text-gray-700 mb-2;
}

.input-field {
    @apply w-full rounded-lg border border-gray-300 px-4 py-2
           focus:border-blue-500 focus:outline-none
           focus:ring-2 focus:ring-blue-200;
}

.checkbox-field {
    @apply h-4 w-4 rounded border-gray-300
           text-blue-600 focus:ring-blue-500;
}
.section-title {
    @apply text-3xl font-bold text-gray-800;
}

.empty-state {
    @apply text-center text-gray-500 py-10;
}

.card-grid {
    @apply grid gap-6 md:grid-cols-2 lg:grid-cols-3;
}
```

## Build TailwindCSS

```bash
rails tailwindcss:build
rails tailwindcss:watch

```

---

## Editar archivos app/views/tareas


### _form

```bash
<%= form_with(model: tarea) do |form| %>

  <% if tarea.errors.any? %>
    <div class="alert-danger mb-6">
      <h2 class="font-bold mb-2">
        <%= pluralize(tarea.errors.count, "error") %> impidieron guardar la tarea:
      </h2>

      <ul class="list-disc list-inside">
        <% tarea.errors.each do |error| %>
          <li><%= error.full_message %></li>
        <% end %>
      </ul>
    </div>
  <% end %>

  <div class="form-card">

    <div class="form-group">
      <%= form.label :title, class: "form-label" %>
      <%= form.text_field :title, class: "input-field" %>
    </div>

    <div class="form-group">
      <%= form.label :description, class: "form-label" %>
      <%= form.textarea :description, rows: 4, class: "input-field" %>
    </div>

    <div class="form-group">
      <%= form.label :fecha, class: "form-label" %>
      <%= form.date_field :fecha, class: "input-field" %>
    </div>

    <div class="form-group">
      <%= form.label :priority, class: "form-label" %>
      <%= form.number_field :priority, in: 1..10, class: "input-field" %>
    </div>

    <div class="form-group">
      <%= form.label :materia_id, "Materia", class: "form-label" %>
      <%= form.collection_select :materia_id,
          Materia.all,
          :id,
          :name,
          { prompt: "Selecciona una materia" },
          { class: "input-field" } %>
    </div>

    <div class="form-group flex items-center gap-3">
      <%= form.check_box :completed, class: "checkbox-field" %>
      <%= form.label :completed, class: "text-sm text-gray-700" %>
    </div>

    <div class="mt-6">
      <%= form.submit "Guardar tarea", class: "btn btn-success" %>
    </div>

  </div>

<% end %>
```


### _tarea

```bash
<div id="<%= dom_id tarea %>" class="card">

  <h2 class="titulo mb-4">
    <%= tarea.title %>
  </h2>

  <div class="card-section">

    <div>
      <p class="item-label">Descripción</p>
      <p class="item-value"><%= tarea.description %></p>
    </div>

    <div>
      <p class="item-label">Fecha</p>
      <p class="item-value"><%= tarea.fecha %></p>
    </div>

    <div>
      <p class="item-label">Estado</p>

      <% if tarea.completed? %>
        <span class="badge-success">Completada</span>
      <% else %>
        <span class="badge-danger">Pendiente</span>
      <% end %>
    </div>

    <div>
      <p class="item-label">Prioridad</p>
      <p class="item-value"><%= tarea.priority %></p>
    </div>

    <div>
      <p class="item-label">Materia</p>

      <%= link_to tarea.materia.name,
          materia_path(tarea.materia),
          class: "link-primary" %>
    </div>

  </div>

</div>
```

### edit


```bash
<% content_for :title, "Editar tarea" %>

<div class="page-container">

  <h1 class="titulo mb-6">
    Editar tarea
  </h1>

  <%= render "form", tarea: @tarea %>

  <div class="actions">
    <%= link_to "Ver tarea", @tarea, class: "btn btn-success" %>

    <%= link_to "Volver a tareas", tareas_path, class: "btn btn-primary" %>
  </div>

</div>
```

### index


```bash
<% content_for :title, "Tareas" %>

<div class="page-container">

  <% if notice.present? %>
    <div class="alert-success mb-6">
      <%= notice %>
    </div>
  <% end %>

  <div class="flex items-center justify-between mb-8">
    <h1 class="text-3xl font-bold text-gray-800">
      Tareas
    </h1>

    <%= link_to "Nueva tarea", new_tarea_path, class: "btn btn-success" %>
  </div>

  <div id="tareas" class="grid gap-6 md:grid-cols-2 lg:grid-cols-3">
    <% @tareas.each do |tarea| %>

      <div class="card">
        <%= render tarea %>

        <div class="mt-4 flex justify-end">
          <%= link_to "Ver detalle", tarea, class: "btn btn-primary" %>
        </div>
      </div>

    <% end %>
  </div>

</div>
```

### new

```bash
<% content_for :title, "Nueva tarea" %>

<div class="page-container">

  <h1 class="titulo mb-6">
    Nueva tarea
  </h1>

  <%= render "form", tarea: @tarea %>

  <div class="actions">
    <%= link_to "Volver a tareas", tareas_path, class: "btn btn-primary" %>
  </div>

</div>
```

### show

```bash
<div class="page-container">

  <% if notice.present? %>
    <div class="alert-success mb-6">
      <%= notice %>
    </div>
  <% end %>

  <%= render @tarea %>

  <div class="actions">
    <%= link_to "Editar", edit_tarea_path(@tarea), class: "btn btn-warning" %>

    <%= link_to "Volver", tareas_path, class: "btn btn-primary" %>

    <%= button_to "Eliminar",
        @tarea,
        method: :delete,
        class: "btn btn-danger" %>
  </div>

</div>
```

## Editar archivos app/views/materias

### _form


```bash
<%= form_with model: materia,
      url: materia.persisted? ? materia_path(materia) : materias_path do |f| %>

    <% if materia.errors.any? %>
        <div class="alert-danger mb-6">
            <h2 class="font-bold mb-2">
                <%= pluralize(materia.errors.count, "error") %> impidieron guardar la materia:
            </h2>

            <ul class="list-disc list-inside">
                <% materia.errors.full_messages.each do |message| %>
                    <li><%= message %></li>
                <% end %>
            </ul>
        </div>
    <% end %>

    <div class="form-card">

        <div class="form-group">
            <%= f.label :name, "Nombre", class: "form-label" %>

            <%= f.text_field :name,
                class: "input-field",
                placeholder: "Ingrese el nombre de la materia" %>
        </div>

        <div class="actions">
            <%= f.submit "Guardar materia", class: "btn btn-success" %>
        </div>

    </div>

<% end %>
```

### edit

```bash 
<% content_for :title, "Editar materia" %>

<div class="page-container">

    <h1 class="titulo mb-6">
        Editar materia
    </h1>

    <%= render "form", materia: @materia %>

    <div class="actions">
        <%= link_to "Ver materia",
            materia_path(@materia),
            class: "btn btn-success" %>

        <%= link_to "Volver a materias",
            materias_path,
            class: "btn btn-primary" %>
    </div>

</div>
```

### index

```bash 
<% content_for :title, "Materias" %>

<div class="page-container">

    <div class="flex items-center justify-between mb-8">
        <h1 class="titulo">
            Materias
        </h1>

        <%= link_to "Nueva materia",
            new_materia_path,
            class: "btn btn-success" %>
    </div>

    <% if @materias.any? %>

        <div class="card">
            <ul class="divide-y divide-gray-200">

                <% @materias.each do |materia| %>
                    <li class="py-4 flex items-center justify-between">

                        <span class="item-value">
                            <%= materia.name %>
                        </span>

                        <%= link_to "Ver",
                            materia_path(materia),
                            class: "link-primary" %>

                    </li>
                <% end %>

            </ul>
        </div>

    <% else %>

        <div class="card text-center">
            <p class="text-gray-500">
                No hay materias registradas.
            </p>
        </div>

    <% end %>

</div>
```

### new

```bash 
<% content_for :title, "Nueva materia" %>

<div class="page-container">

    <h1 class="titulo mb-6">
        Nueva materia
    </h1>

    <%= render "form", materia: @materia %>

    <div class="actions">
        <%= link_to "Volver a materias",
            materias_path,
            class: "btn btn-primary" %>
    </div>

</div>
```

### show

```bash 
<% content_for :title, @materia.name %>

<div class="page-container">

    <div class="card">

        <h1 class="titulo mb-2">
            <%= @materia.name %>
        </h1>

        <p class="text-gray-500 mb-6">
            Detalle de la materia y sus tareas asociadas.
        </p>

        <h2 class="card-header">
            Tareas
        </h2>

        <% if @materia.tareas.any? %>

            <ul class="divide-y divide-gray-200">

                <% @materia.tareas.each do |tarea| %>

                    <li class="py-4 flex items-center justify-between">

                        <%= link_to tarea.title,
                            tarea_path(tarea),
                            class: "link-primary" %>

                        <% if tarea.completed %>
                            <span class="badge-success">
                                Completada
                            </span>
                        <% else %>
                            <span class="badge-danger">
                                Pendiente
                            </span>
                        <% end %>

                    </li>

                <% end %>

            </ul>

        <% else %>

            <p class="text-gray-500">
                Esta materia no tiene tareas registradas.
            </p>

        <% end %>

    </div>

    <div class="actions">

        <%= button_to "Eliminar",
            materia_path(@materia),
            method: :delete,
            class: "btn btn-danger" %>

        <%= link_to "Volver a materias",
            materias_path,
            class: "btn btn-primary" %>
                
    <%= link_to "Nueva tarea", new_tarea_path, class: "btn btn-success" %>

    </div>

</div>
```

---


## 🛠️ Tecnologías Utilizadas

* 💎 Ruby
* 🚂 Ruby on Rails
* 🎨 Tailwind CSS
* 🗄️ SQLite3
* ⚡ Hotwire (Turbo + Stimulus)

---

## 📚 Autor: Grupo 6

Proyecto desarrollado como práctica de Ruby on Rails para la gestión académica de tareas y materias.

## 🎥 Tutorial de Referencia

Durante el desarrollo de este proyecto se utilizó como guía el siguiente tutorial de Ruby on Rails:

> 🚂 **Ruby on Rails Full Course**
>
> Aprende los fundamentos de Ruby on Rails mediante la construcción de una aplicación completa paso a paso.

🔗 **Video:**
https://www.youtube.com/watch?v=gkEeSEPyFiY