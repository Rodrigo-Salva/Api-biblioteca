<p align="center">
  <img src="https://raw.githubusercontent.com/laravel/art/master/logo-lockup/5%20SVG/2%20CMYK/1%20Full%20Color/laravel-logolockup-cmyk-red.svg" width="350" alt="Laravel Logo">
</p>

<h1 align="center">📚 API Biblioteca - Laravel RESTful</h1>
<p align="center">
  <b>Una API moderna, robusta y elegante para gestionar tu biblioteca digital</b><br>
  <i>¡Controla libros, autores, categorías, préstamos y favoritos, todo desde una API segura y fácil de usar!</i>
</p>

<p align="center">
  <a href="https://github.com/laravel/framework/actions"><img src="https://github.com/laravel/framework/workflows/tests/badge.svg" alt="Build Status"></a>
  <a href="https://packagist.org/packages/laravel/framework"><img src="https://img.shields.io/packagist/dt/laravel/framework" alt="Total Downloads"></a>
  <a href="https://packagist.org/packages/laravel/framework"><img src="https://img.shields.io/packagist/v/laravel/framework" alt="Latest Stable Version"></a>
  <a href="https://packagist.org/packages/laravel/framework"><img src="https://img.shields.io/packagist/l/laravel/framework" alt="License"></a>
</p>

---

## ✨ ¿Qué es esta API?

La **API Biblioteca** es una solución RESTful desarrollada en Laravel para la gestión integral de bibliotecas físicas o digitales. Permite registrar usuarios, administrar libros, autores y categorías, gestionar préstamos y mucho más, todo con seguridad y control de roles (admin/usuario).

---

## 🏛️ Arquitectura de la API

Esta API sigue una arquitectura limpia y desacoplada, inspirada en los principios de Laravel y buenas prácticas de diseño:

```
📁 app/
├── 📁 Http/
│   ├── 📁 Controllers/      # Controladores REST principales (Books, Authors, Categories, Loans, Users, Favorites, Auth)
│   ├── 📁 Middleware/       # Middleware personalizados (IsAdmin, etc)
│   └── 📁 Service/          # Servicios de lógica de dominio (ej: LoanService)
├── 📁 Models/               # Modelos Eloquent (User, Book, Author, Category, Loan, Favorite)
├── 📁 Requests/             # Validaciones de request personalizadas
├── 📁 Providers/            # Providers de Laravel
📁 config/
├── 📄 cors.php              # Configuración de CORS
├── 📄 l5-swagger.php        # Configuración de documentación Swagger
📁 routes/
├── 📄 api.php               # Definición de rutas REST (públicas, autenticadas y admin)
📁 database/
├── 📁 migrations/           # Migraciones de base de datos
```

**Principios clave:**
- Separación de responsabilidades: lógica de negocio en servicios, acceso HTTP en controladores.
- Uso de middleware para autorización y autenticación.
- Documentación automática con Swagger.
- Código listo para escalar y fácil de mantener.

---

## 🚀 Características Principales

- **🔐 Autenticación y Roles**
  - Registro y login de usuarios.
  - Autenticación mediante tokens Laravel Sanctum.
  - Rutas protegidas y middleware para admins.

- **📖 Gestión de Libros**
  - Listado público de libros con stock disponible.
  - CRUD completo para libros (solo admins).
  - Control automático de stock y préstamos.

- **👥 Usuarios y Permisos**
  - Administra usuarios (listar, editar, eliminar) solo con perfil admin.

- **🖋️ Autores y Categorías**
  - CRUD de autores y categorías (solo admins).
  - Consulta pública para usuarios autenticados.

- **📚 Préstamos Inteligentes**
  - Solicitud y devolución de libros.
  - Un usuario no puede solicitar un nuevo préstamo hasta devolver el anterior.
  - Admins pueden ver, editar y eliminar todos los préstamos.

- **⭐ Favoritos**
  - Agrega o elimina libros favoritos para cada usuario.

- **📝 Documentación Swagger/OpenAPI**
  - Anotaciones listas para generar documentación interactiva.

---

## 🔥 ¿Para quién es útil?

- Bibliotecas físicas o virtuales
- Plataformas educativas/universidades
- Apps móviles/web de gestión de libros
- Proyectos de integración o aprendizaje de APIs REST

---

## 🛤️ Endpoints destacados

- `POST /api/register` - Registro de usuario
- `POST /api/login` - Login y obtención de token
- `GET /api/books/available` - Libros con stock disponible (público)
- `GET /api/books` - Listar todos los libros (requiere autenticación)
- `POST /api/loans` - Solicitar préstamo (requiere autenticación)
- `POST /api/loans/{loan}/mark-returned` - Marcar devolución
- `GET /api/favorites` - Listar favoritos del usuario
- **CRUD completo para libros, autores, categorías, préstamos y usuarios** (solo admin)

---

## ⚡ Instalación rápida

```bash
git clone https://github.com/Rodrigo-Salva/Api-biblioteca.git
cd Api-biblioteca
composer install
cp .env.example .env
# Configura la base de datos en .env
php artisan key:generate
php artisan migrate --seed
php artisan serve
```

> **¡Listo!** La API estará disponible en `http://localhost:8000`

---

## 🧩 Ejemplo de autenticación

1. **Regístrate:**  
   `POST /api/register`  
   _Body:_ { "name": "Juan", "email": "juan@email.com", "password": "123456" }

2. **Login:**  
   `POST /api/login`  
   _Body:_ { "email": "juan@email.com", "password": "123456" }

3. **Usa el token:**  
   Añade el token que recibes en la cabecera `Authorization: Bearer <token>` para acceder a rutas protegidas.

---

## 🎨 Tecnologías usadas

- [Laravel](https://laravel.com/) (Framework PHP)
- [Sanctum](https://laravel.com/docs/10.x/sanctum) (Autenticación)
- [Swagger/OpenAPI](https://swagger.io/) (Documentación API)
- MySQL/PostgreSQL (Base de datos)

---

## 💡 Personalízala y extiéndela

¿Quieres agregar notificaciones, reservas anticipadas, reportes de uso u otros módulos?  
¡El código es limpio, modular y fácil de adaptar a tus necesidades!

---

## 📝 Licencia

Este proyecto está bajo licencia MIT.

---

<p align="center">
  <b>Hecho con ❤ por Rodrigo Salva</b>
</p>
