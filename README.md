# 🚀 Blog Informatorio 2025

Proyecto final desarrollado con Django. Un sistema de gestión de contenidos (CMS) tipo Blog con roles escalonados, autenticación y moderación de contenidos.

## 🏗️ Arquitectura y Estructura del Código

El proyecto sigue el patrón **MVT (Modelo-Vista-Template)** y buenas prácticas de desarrollo modular:

* **Organización Modular (`/apps`):** Se desacopló la lógica del proyecto principal creando una carpeta `apps` para contener las aplicaciones (en este caso, `posts`). Esto mantiene la raíz limpia y escalable.
* **Herencia de Plantillas:** Se implementó un archivo maestro `base.html` del cual heredan todas las vistas (`extends`), garantizando consistencia en el Navbar y Footer sin duplicar código.
* **Seguridad:** Uso de decoradores (`@login_required`, `@permission_required`) y validaciones en las vistas para proteger rutas sensibles.
* **Gestión de Media:** Configuración para carga y renderizado de imágenes dinámicas por parte de los usuarios.

## 👥 Gestión de Roles y Permisos

El sistema implementa una lógica de permisos estricta basada en los requerimientos:

1.  **Visitante (Anónimo):**
    * Acceso de lectura a posts y comentarios.
    * Filtrado por categorías.
    * Posibilidad de registrarse.

2.  **Miembro (Usuario Registrado):**
    * Puede comentar en las publicaciones.
    * **Permiso exclusivo:** Solo puede editar y eliminar *sus propios* comentarios.

3.  **Colaborador (Staff):**
    * Gestión de Contenido: Puede Crear, Editar y Eliminar artículos.
    * Moderación: Tiene permisos para eliminar comentarios de *cualquier* usuario.
    * Acceso restringido: No puede acceder a la gestión de usuarios ni configuraciones sensibles del Admin.

4.  **Superusuario (Root):**
    * Control total del sistema y acceso irrestricto al panel de administración (`/admin`).

## 🛠️ Tecnologías Utilizadas

* **Backend:** Python 3, Django 5.x
* **Base de Datos:** SQLite (Entorno local) / Configurable para MySQL.
* **Frontend:** HTML5, CSS3, Bootstrap 5 (Responsive Design).
* **Control de Versiones:** Git & GitHub.

---

## 🔐 Credenciales de Acceso (Testing)

Para facilitar la evaluación del proyecto, se han pre-cargado los siguientes usuarios con sus respectivos roles en la base de datos:

| Rol / Perfil | Usuario | Contraseña | Permisos Clave |
| :--- | :--- | :--- | :--- |
| **👑 Superusuario (Root)** | `root` | `admin12345` | Acceso Total + Panel Admin |
| **🤝 Colaborador** | `colaborador1` | `staff123` | Crear/Editar Posts + Moderar Comentarios |
| **👤 Miembro** | `pepe` | `usuario123` | Comentar + Editar solo *sus* comentarios |



---
*Proyecto realizado para el curso de Desarrollo Web - Informatorio Chaco.*
