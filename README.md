# 🎓 Sistema de Gestión Académica

Sistema web completo para la gestión de asistencias, cargas académicas, docentes y materias en instituciones educativas.

[![Laravel](https://img.shields.io/badge/Laravel-12.x-FF2D20?style=flat&logo=laravel)](https://laravel.com)
[![PostgreSQL](https://img.shields.io/badge/PostgreSQL-16-336791?style=flat&logo=postgresql)](https://www.postgresql.org)
[![Bootstrap](https://img.shields.io/badge/Bootstrap-5.3-7952B3?style=flat&logo=bootstrap)](https://getbootstrap.com)
[![License](https://img.shields.io/badge/License-MIT-green.svg)](LICENSE)

## 📋 Características Principales

### 👤 Gestión de Usuarios
- **3 Roles:** Admin, Decano, Docente
- Sistema de permisos con Spatie Permission
- Gestión completa de usuarios y roles

### 👨‍🏫 Gestión de Docentes
- Registro completo de docentes
- Asignación de cargas académicas
- Control de asistencias con habilitaciones

### 📚 Gestión Académica
- Materias y grupos
- Horarios y aulas
- Asignación de cargas por docente
- Prevención de conflictos de horario

### ✅ Control de Asistencia
- Sistema de habilitaciones para marcado
- Marcado con confirmación de contraseña
- Ventana de tiempo configurable (±15 minutos)
- Registro manual por administradores
- Estados: Asistencia, Falta, Tardanza, Justificada

### 📊 Reportes
- Reportes personalizables de docentes
- Exportación a PDF con DomPDF
- Estadísticas de asistencias y habilitaciones
- Filtros por fechas y secciones

## 🚀 Instalación Local

### Requisitos Previos
- PHP >= 8.2
- Composer
- Node.js >= 18.x
- PostgreSQL >= 14
- Git

### Pasos de Instalación

```bash
# 1. Clonar el repositorio
git clone https://github.com/Bryan-ArHe/GestionAcademica.git
cd GestionAcademica

# 2. Instalar dependencias PHP
composer install

# 3. Instalar dependencias Node
npm install

# 4. Copiar archivo de entorno
cp .env.example .env

# 5. Generar clave de aplicación
php artisan key:generate

# 6. Configurar base de datos en .env
# DB_CONNECTION=pgsql
# DB_HOST=127.0.0.1
# DB_PORT=5432
# DB_DATABASE=gestionacademica
# DB_USERNAME=tu_usuario
# DB_PASSWORD=tu_contraseña

# 7. Ejecutar migraciones y seeders
php artisan migrate --seed

# 8. Crear link simbólico de storage
php artisan storage:link

# 9. Compilar assets
npm run build

# 10. Iniciar servidor de desarrollo
php artisan serve
```

Acceder a: `http://localhost:8000`

### Credenciales por Defecto

**Administrador:**
- Email: `admin@admin.com`
- Contraseña: `password`

**Decano:**
- Email: `decano@decano.com`
- Contraseña: `password`

**Docente:**
- Email: `docente@docente.com`
- Contraseña: `password`

## 🐳 Despliegue con Docker

### Construcción de la Imagen

```bash
docker build -t gestion-academica:latest .
```

### Ejecución

```bash
docker run -d \
  -p 8000:8000 \
  -e APP_KEY="base64:tu-key-generada" \
  -e DB_HOST="host.docker.internal" \
  -e DB_PORT="5432" \
  -e DB_DATABASE="gestionacademica" \
  -e DB_USERNAME="postgres" \
  -e DB_PASSWORD="tu-password" \
  -e RUN_SEEDERS="true" \
  --name gestion-academica \
  gestion-academica:latest
```

## ☁️ Despliegue en la Nube

**⚠️ IMPORTANTE: Si la información no se ve reflejada en producción, consulta:**

📖 **[GUÍA COMPLETA DE DESPLIEGUE](DESPLIEGUE.md)**

### Diagnóstico Rápido

```bash
# Ejecutar script de verificación
chmod +x verificar-sistema.sh
./verificar-sistema.sh
```

### Problemas Comunes

| Problema | Solución |
|----------|----------|
| Base de datos vacía | `php artisan db:seed --force` |
| Assets sin cargar | `npm run build` |
| Error de permisos | `chmod -R 775 storage bootstrap/cache` |
| APP_KEY faltante | `php artisan key:generate` |
| PDFs no generan | Instalar fuentes (ver Dockerfile) |

### Plataformas Soportadas

- ✅ Railway
- ✅ Render
- ✅ Heroku
- ✅ AWS (EC2, ECS, Elastic Beanstalk)
- ✅ DigitalOcean
- ✅ VPS (Ubuntu/Debian)

## 🛠️ Tecnologías Utilizadas

### Backend
- **Laravel 12.x** - Framework PHP
- **PostgreSQL** - Base de datos
- **Spatie Laravel Permission** - Roles y permisos
- **DomPDF** - Generación de PDFs

### Frontend
- **Bootstrap 5.3.3** - Framework CSS
- **Vite** - Build tool
- **Font Awesome 6.5** - Iconos
- **SweetAlert2** - Alertas elegantes

### DevOps
- **Docker** - Containerización
- **Nginx** - Servidor web
- **PHP-FPM** - Process manager

## 📁 Estructura del Proyecto

```
GestionAcademica/
├── app/
│   ├── Http/Controllers/
│   │   ├── Admin/              # Controladores de administración
│   │   ├── Docente/            # Controladores de docentes
│   │   └── ReporteDocenteController.php
│   ├── Models/                 # Modelos Eloquent
│   └── Services/               # Servicios de negocio
├── resources/
│   ├── views/
│   │   ├── admin/              # Vistas de administración
│   │   ├── docente/            # Vistas de docentes
│   │   ├── decano/             # Vistas de decano
│   │   └── layouts/            # Layouts maestros
│   ├── css/                    # Estilos personalizados
│   └── js/                     # JavaScript
├── database/
│   ├── migrations/             # Migraciones de BD
│   └── seeders/                # Seeders de datos
├── .docker/                    # Configuración Docker
│   ├── entrypoint.sh
│   └── nginx.conf
├── Dockerfile                  # Imagen Docker
└── DESPLIEGUE.md              # Guía de despliegue
```

## 🧪 Testing

```bash
# Ejecutar tests
php artisan test

# Con coverage
php artisan test --coverage
```

## 📝 Documentación Adicional

- [Guía de Despliegue](DESPLIEGUE.md)
- [Sistema de Asistencia](SISTEMA_ASISTENCIA.md)
- [Configuración de API](API_CONFIGURACION.md)
- [Pruebas de Habilitaciones](PRUEBA_HABILITACIONES.md)

## 🤝 Contribuir

Las contribuciones son bienvenidas. Por favor:

1. Fork el proyecto
2. Crea una rama para tu feature (`git checkout -b feature/AmazingFeature`)
3. Commit tus cambios (`git commit -m 'Add: AmazingFeature'`)
4. Push a la rama (`git push origin feature/AmazingFeature`)
5. Abre un Pull Request

## 📄 Licencia

Este proyecto está bajo la Licencia MIT. Ver el archivo [LICENSE](LICENSE) para más detalles.

## 👥 Autores

- **Desenvolvimento Inicial** - [naixs007](https://github.com/naixs007)

## 🆘 Soporte

¿Problemas al desplegar? ¿La información no se muestra en la nube?

1. Revisa la [Guía de Despliegue](DESPLIEGUE.md)
2. Ejecuta el script de diagnóstico: `./verificar-sistema.sh`
3. Revisa los logs: `tail -f storage/logs/laravel.log`
4. Abre un [Issue](https://github.com/naixs007/GestionAcademica/issues)

---

⭐ Si este proyecto te fue útil, considera darle una estrella en GitHub
