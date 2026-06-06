# 🚀 Instalación de Ruby y Ruby on Rails en Windows

## 📋 Información General

Este documento describe el proceso de instalación y configuración de Ruby y Ruby on Rails en Windows para el desarrollo de una aplicación web de calculadora utilizando el framework Ruby on Rails.

---

# 🖥️ Requisitos Previos

Antes de comenzar, asegúrese de contar con:

* Sistema Operativo Windows 10 o superior.
* Conexión a Internet.
* Permisos de administrador para instalar software.

---

# 1️⃣ Instalación de Ruby

## 📥 Descargar Ruby

Ingresar al sitio oficial de RubyInstaller:

https://rubyinstaller.org

Descargar la versión recomendada más reciente para Windows.

En este proyecto se instaló:

```text
Ruby 3.4.9
```

---

## ⚙️ Ejecutar el Instalador

Durante la instalación, activar la opción:

```text
Add Ruby executables to your PATH
```

Esto permitirá ejecutar Ruby desde cualquier terminal de Windows.

---

## 🔧 Instalación de MSYS2

Al finalizar la instalación de RubyInstaller aparecerá una ventana similar a la siguiente:

```text
1 - MSYS2 base installation
2 - MSYS2 system update (optional)
3 - MSYS2 and MINGW development toolchain

Which components shall be installed? If unsure press ENTER [1,3]
```

### ✅ Acción realizada

Simplemente presionar:

```text
ENTER
```

Esto instala automáticamente:

* MSYS2 Base Installation
* MINGW Development Toolchain

Estos componentes son necesarios para compilar dependencias nativas utilizadas por Rails y diversas gemas.

---

> ⚠️ IMPORTANTE
>
> No cerrar la ventana durante la instalación de MSYS2.
> Algunas dependencias pueden tardar varios minutos en descargarse e instalarse.

---

## Instalación de Git

Se utilizó el administrador de paquetes Winget para instalar Git:

```powershell
winget install --id Git.Git -e --source winget
```

Posteriormente se verificó la instalación mediante:

```powershell
git --version
```

---

# 2️⃣ Verificar la Instalación de Ruby

Abrir una nueva ventana de CMD o PowerShell y ejecutar:

```bash
ruby -v
```

Resultado obtenido:

```bash
ruby 3.4.9 (2026-03-11 revision 76cca827ab) +PRISM [x64-mingw-ucrt]
```

### ✅ Verificación Exitosa

Esto confirma que Ruby fue instalado correctamente.

---

# 3️⃣ Verificar RubyGems

RubyGems es el gestor de paquetes oficial de Ruby.

Ejecutar:

```bash
gem -v
```

Resultado obtenido:

```bash
3.6.9
```

### ✅ Verificación Exitosa

RubyGems se encuentra funcionando correctamente.

---

# 4️⃣ Verificar Ruby on Rails

Antes de instalar Rails se ejecutó:

```bash
rails -v
```

Resultado:

```text
'rails' is not recognized as an internal or external command,
operable program or batch file.
```

### ⚠️ Interpretación

Este mensaje indica que Ruby on Rails aún no estaba instalado.

---

# 5️⃣ Instalación de Ruby on Rails

Para instalar Rails se ejecutó:

```bash
gem install rails
```

Durante la instalación se descargaron e instalaron múltiples dependencias necesarias para el framework.

Entre las principales:

* activesupport
* activerecord
* actionpack
* actionview
* actionmailer
* actioncable
* railties
* nokogiri
* rails

Instalación finalizada con éxito:

```text
Successfully installed rails-8.1.3
39 gems installed
```

---

> 💡 NOTA
>
> La instalación de Rails puede tardar varios minutos dependiendo del rendimiento del equipo y la velocidad de Internet.

---

# 6️⃣ Verificar la Instalación de Rails

Una vez finalizada la instalación:

```bash
rails -v
```

Resultado obtenido:

```bash
Rails 8.1.3
```

### ✅ Verificación Exitosa

Ruby on Rails fue instalado correctamente y está listo para ser utilizado.

---

# 📊 Versiones Instaladas

| Componente | Versión |
| ---------- | ------- |
| Ruby       | 3.4.9   |
| RubyGems   | 3.6.9   |
| Rails      | 8.1.3   |

---

# 🔄 Actualización Opcional de RubyGems

Durante la instalación apareció la siguiente recomendación:

```text
A new release of RubyGems is available: 3.6.9 → 4.0.13
```

Para actualizar RubyGems:

```bash
gem update --system 4.0.13
```

---

> ⚠️ IMPORTANTE
>
> Esta actualización es opcional.
> El proyecto puede desarrollarse correctamente con la versión instalada actualmente.

---

# 🎯 Resultado Final

Después de completar todos los pasos se dispone de un entorno de desarrollo completamente funcional para trabajar con:

* Ruby
* RubyGems
* Ruby on Rails

Lo que permite crear aplicaciones web utilizando la arquitectura MVC (Model-View-Controller), característica principal del framework Ruby on Rails.

---