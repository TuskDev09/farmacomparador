# FarmaComparador

Plataforma web para comparar precios de medicamentos entre farmacias en Chile. Permite a los usuarios buscar medicamentos, ver precios por farmacia y acceder a ofertas disponibles.

## Tecnologías

- **Backend:** Python 3 / Django 5.2
- **Base de datos:** PostgreSQL
- **Frontend:** Django Templates, HTML, CSS, JavaScript (vanilla)

## Funcionalidades

### Usuarios
- Registro e inicio de sesión
- Búsqueda de medicamentos por nombre o descripción
- Comparación de precios entre farmacias
- Visualización de ofertas y descuentos

### Administración
- Panel CRUD para gestión de usuarios
- Roles diferenciados (usuario regular / administrador)
- Acceso al panel de administración de Django

## Estructura del proyecto

```
APT_Test-APT/
├── manage.py
├── requirements.txt
├── farmacomparador/          # Configuración del proyecto Django
│   ├── settings.py
│   ├── urls.py
│   ├── wsgi.py
│   └── asgi.py
└── comparador/               # Aplicación principal
    ├── models.py
    ├── views.py
    ├── urls.py
    ├── admin.py
    ├── migrations/
    ├── templates/
    │   ├── base.html
    │   ├── index.html
    │   ├── login.html
    │   ├── signup.html
    │   └── admin_dashboard.html
    └── static/
        ├── css/
        └── js/
```

## Modelos de base de datos

| Modelo | Descripción |
|---|---|
| `Usuario` | Cuentas de usuario |
| `Medicamento` | Registro de medicamentos |
| `Presentacion` | Presentaciones y dosis de cada medicamento |
| `PrecioFarmacia` | Precios por presentación y farmacia |
| `Farmacia` | Datos de farmacias |
| `Laboratorio` | Fabricantes de medicamentos |
| `MarcaComercial` | Marcas comerciales |

## Instalación y configuración

### Requisitos previos
- Python 3.10+
- PostgreSQL

### Pasos

1. Clonar el repositorio:
   ```bash
   git clone https://github.com/TuskDev09/farmacomparador
   cd farmacomparador
   ```

2. Crear y activar un entorno virtual:
   ```bash
   python -m venv venv
   # Windows
   venv\Scripts\activate
   # Linux/macOS
   source venv/bin/activate
   ```

3. Instalar dependencias:
   ```bash
   pip install -r requirements.txt
   ```

4. Configurar la base de datos en `farmacomparador/settings.py`:
   ```python
   DATABASES = {
       'default': {
           'ENGINE': 'django.db.backends.postgresql',
           'NAME': 'nombre_de_tu_bd',
           'USER': 'tu_usuario',
           'PASSWORD': 'tu_contraseña',
           'HOST': 'localhost',
           'PORT': '5432',
       }
   }
   ```

5. Aplicar migraciones:
   ```bash
   python manage.py migrate
   ```

6. Crear un superusuario (opcional):
   ```bash
   python manage.py createsuperuser
   ```

7. Iniciar el servidor de desarrollo:
   ```bash
   python manage.py runserver
   ```

La aplicación estará disponible en `http://127.0.0.1:8000/`.

## Rutas principales

| Ruta | Descripción |
|---|---|
| `/` | Página principal con búsqueda y resultados |
| `/login/` | Inicio de sesión |
| `/signup/` | Registro de usuario |
| `/logout/` | Cierre de sesión |
| `/dashboard/` | Panel de administración |
| `/admin/` | Panel de administración de Django |

## Dependencias

```
Django==5.2.7
asgiref==3.10.0
psycopg2-binary==2.9.11
sqlparse==0.5.3
tzdata==2025.2
```

## Notas para producción

- Cambiar `DEBUG = False` en `settings.py`
- Reemplazar `SECRET_KEY` por un valor seguro (usar variables de entorno)
- Configurar `ALLOWED_HOSTS` con el dominio real
- Ejecutar `python manage.py collectstatic` para archivos estáticos
