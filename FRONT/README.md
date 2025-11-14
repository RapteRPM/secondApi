# API de Productos - Frontend y Backend

Sistema completo de gestión de productos con autenticación JWT que incluye un backend Flask desplegado en Railway y un frontend web moderno.

## Arquitectura del Sistema

### Backend (API Flask)
- **Despliegue**: Railway (https://apiflask-production.up.railway.app/)
- **Base de Datos**: PostgreSQL
- **Autenticación**: JWT (JSON Web Tokens)
- **Framework**: Flask con Flask-JWT-Extended
- **CORS**: Configurado para GitHub Codespaces y localhost

### Frontend (Cliente Web)
- **Tecnología**: HTML5, CSS3, JavaScript vanilla
- **Framework CSS**: Bootstrap 5.3.0
- **Iconos**: Font Awesome 6.4.0
- **Diseño**: Tema azul oceánico responsive

## Características del Sistema

### Backend API
- Autenticación de usuarios con registro y login
- Gestión completa de productos (CRUD)
- Gestión de categorías de productos
- Validación de datos con esquemas JSON
- Manejo de errores HTTP estándar
- Protección de rutas con JWT
- Configuración CORS para desarrollo

### Frontend Web
- Sistema de login y registro de usuarios
- Dashboard con estadísticas de productos
- Gestión completa de productos con interfaz visual
- Selección y gestión de categorías
- Diseño responsivo para móviles y tablets
- Interfaz moderna con efectos visuales
- Manejo automático de sesiones JWT

## Estructura del Proyecto

```
secondApi/
├── FRONT/                          # Frontend del sistema
│   ├── index.html                  # Página de autenticación
│   ├── dashb.html                  # Dashboard principal
│   ├── frontend_integration.js     # Cliente API y lógica
│   ├── style.css                   # Estilos con tema oceánico
│   └── README.md                   # Documentación
└── (Backend desplegado en Railway)
```

## Endpoints de la API

### Autenticación
- `POST /registry` - Registro de nuevos usuarios
- `POST /login` - Inicio de sesión y obtención de JWT

### Productos
- `GET /products` - Obtener todos los productos (requiere JWT)
- `POST /products` - Crear nuevo producto (requiere JWT)
- `PUT /products/<id>` - Actualizar producto (requiere JWT)
- `DELETE /products/<id>` - Eliminar producto (requiere JWT)

### Categorías
- `GET /categories` - Obtener todas las categorías (requiere JWT)
- `POST /categories` - Crear nueva categoría (requiere JWT)

## Configuración y Uso

### Acceso al Sistema
1. Abrir el frontend en un servidor local:
   ```bash
   cd FRONT
   python3 -m http.server 8081
   ```

2. Navegar a: http://localhost:8081/index.html

3. Registrarse o iniciar sesión con credenciales existentes

### Flujo de Autenticación
1. **Registro**: Crear cuenta con username y password
2. **Login**: Obtener token JWT válido
3. **Navegación**: Acceso automático al dashboard
4. **Sesión**: Token almacenado localmente para futuras requests

### Gestión de Productos
- **Ver productos**: Lista completa con categorías e inventario
- **Crear producto**: Formulario con validación de datos
- **Editar producto**: Modificación inline con guardar/cancelar
- **Eliminar producto**: Confirmación antes de borrado
- **Estadísticas**: Resumen visual del inventario total

## Tecnologías y Dependencias

### Backend
- Python 3.8+
- Flask 2.3.0
- Flask-JWT-Extended
- Flask-CORS
- SQLAlchemy
- PostgreSQL
- Railway (hosting)

### Frontend
- HTML5 semántico
- CSS3 con variables y animaciones
- JavaScript ES6+ vanilla
- Bootstrap 5.3.0 (CDN)
- Font Awesome 6.4.0 (CDN)

## Variables de Configuración

### Frontend
```javascript
// URL base de la API
const API_CONFIG = {
    baseURL: 'https://apiflask-production.up.railway.app'
};
```

### Backend (Railway)
- `DATABASE_URL` - Conexión PostgreSQL
- `JWT_SECRET_KEY` - Clave secreta para JWT
- `FLASK_ENV` - Entorno de ejecución

## Seguridad

### Autenticación JWT
- Tokens con expiración automática
- Almacenamiento seguro en localStorage
- Validación automática en cada request
- Renovación automática de sesiones

### CORS
- Configurado para dominios específicos
- Headers permitidos para autenticación
- Métodos HTTP restringidos según endpoint

### Validación
- Validación de entrada en backend
- Sanitización de datos en frontend
- Manejo de errores específicos por endpoint

## Desarrollo

### Estructura de Archivos Frontend
- `index.html` - Página de autenticación con formularios
- `dashb.html` - Dashboard principal con gestión de productos
- `frontend_integration.js` - Cliente API y funciones de integración
- `style.css` - Estilos personalizados con tema visual

### Flujo de Desarrollo
1. Modificar archivos según necesidades
2. Probar localmente con servidor de desarrollo
3. Validar conexión con API en Railway
4. Verificar funcionalidades de autenticación y CRUD

## Troubleshooting

### Problemas Comunes
- **CORS errors**: Verificar configuración del servidor
- **Login fallido**: Comprobar credenciales y conexión API
- **Token expirado**: Renovar sesión desde login
- **Productos no cargan**: Verificar token JWT válido

### Logs y Debug
- Console del navegador para errores JavaScript
- Network tab para monitorear requests HTTP
- Respuestas de error específicas desde la API

## Contacto y Soporte

Para problemas técnicos o mejoras, revisar:
- Logs del servidor Railway
- Console del navegador para errores frontend
- Documentación de la API en Railway dashboard
start index.html
```

### 2. **Servidor Local (Opcional)**

Para una mejor experiencia, puedes usar un servidor HTTP local:

```bash
# Con Python
python -m http.server 8000

# Con Node.js (si tienes npx instalado)
npx serve .

# Luego visita http://localhost:8000
```

## 📋 Guía de Uso

### **1. Registro de Usuario**

1. Abre `index.html` en tu navegador
2. Haz clic en "Regístrate" si no tienes cuenta
3. Completa el formulario con:
   - **Usuario**: Nombre de usuario único
   - **Contraseña**: Mínimo 6 caracteres
4. Haz clic en "Registrarse"

### **2. Iniciar Sesión**

1. En la página principal (`index.html`)
2. Introduce tus credenciales:
   - **Usuario**: Tu nombre de usuario  
   - **Contraseña**: Tu contraseña
3. Haz clic en "Ingresar"
4. Serás redirigido al dashboard automáticamente

### **3. Dashboard de Productos**

Una vez autenticado, accederás al dashboard principal (`dashb.html`) donde puedes:

#### **📊 Visualizar Estadísticas**
- **Total de Productos**: Cantidad total en el inventario
- **Total de Categorías**: Categorías disponibles
- **Inventario Total**: Suma de todas las unidades

#### **➕ Agregar Productos**
1. Haz clic en "Agregar Producto"
2. Completa el formulario:
   - **Nombre**: Descripción del producto
   - **Inventario**: Cantidad en stock
   - **Categoría**: Selecciona de la lista disponible
3. Haz clic en "Guardar"

#### **✏️ Editar Productos**
1. En cualquier tarjeta de producto, haz clic en "Editar"
2. Modifica los campos necesarios
3. Haz clic en "Guardar"

#### **👁️ Ver Detalles**
1. Haz clic en "Ver" en cualquier producto
2. Se abrirá un modal con información completa

#### **🗑️ Eliminar Productos**
1. Haz clic en "Eliminar" en cualquier producto
2. Confirma la acción en el diálogo de confirmación

## 🔧 Configuración de la API

La aplicación está configurada para conectarse automáticamente a tu API en Railway:

```javascript
// En frontend_integration.js
const API_CONFIG = {
    baseURL: 'https://apiflask-production.up.railway.app',
    headers: {
        'Content-Type': 'application/json',
    }
};
```

### **Endpoints Utilizados:**

- `POST /registry` - Registro de usuarios
- `POST /login` - Autenticación de usuarios
- `GET /products` - Obtener lista de productos
- `POST /products` - Crear nuevo producto
- `PUT /products/{id}` - Actualizar producto
- `DELETE /products/{id}` - Eliminar producto
- `GET /categories` - Obtener categorías

## 🔐 Autenticación

La aplicación utiliza JWT (JSON Web Tokens) para la autenticación:

1. **Login**: Al iniciar sesión exitosamente, recibes un token JWT
2. **Almacenamiento**: El token se guarda en `localStorage` del navegador
3. **Autorización**: Cada petición incluye el token en el header `Authorization: Bearer {token}`
4. **Expiración**: Si el token expira, serás redirigido al login automáticamente

## 🎨 Personalización

### **Cambiar Colores**

Edita las variables CSS en `style.css`:

```css
:root {
    --primary-color: #667eea;
    --secondary-color: #764ba2;
    --success-color: #10b981;
    --danger-color: #ef4444;
    /* Modifica estos valores según tu preferencia */
}
```

### **Modificar la URL de la API**

Si necesitas cambiar la URL de la API, edita `frontend_integration.js`:

```javascript
const API_CONFIG = {
    baseURL: 'https://tu-nueva-api-url.com', // Cambia esta URL
    headers: {
        'Content-Type': 'application/json',
    }
};
```

## 🐛 Solución de Problemas

### **Error de Conexión con la API**

**Problema**: "Error al cargar los datos. Verifica la conexión con el servidor."

**Solución**: 
1. Verifica que la API esté en línea: https://apiflask-production.up.railway.app/
2. Revisa la consola del navegador (F12) para más detalles
3. Confirma que no hay problemas de CORS

### **Sesión Expirada**

**Problema**: "Sesión expirada. Por favor inicia sesión nuevamente."

**Solución**:
1. Los tokens JWT tienen tiempo de expiración limitado
2. Vuelve a iniciar sesión para obtener un nuevo token
3. La aplicación te redirigirá automáticamente al login

### **Formulario No Guarda**

**Problema**: Error al guardar productos

**Solución**:
1. Verifica que todos los campos obligatorios estén completados
2. Asegúrate de que el inventario sea un número válido
3. Confirma que hayas seleccionado una categoría

## 📱 Compatibilidad

- ✅ **Chrome** 80+
- ✅ **Firefox** 75+
- ✅ **Safari** 13+
- ✅ **Edge** 80+
- ✅ **Dispositivos móviles** (iOS Safari, Android Chrome)

## 🚀 ¡Listo para Usar!

Tu frontend está completamente configurado y listo para conectarse con tu API de Railway. 

**Pasos rápidos:**
1. Abre `index.html`
2. Regístrate o inicia sesión  
3. ¡Comienza a gestionar tus productos! 🎉

---

**URL de la API**: https://apiflask-production.up.railway.app/  
**Estado**: ✅ Activa y funcionando  
**Última actualización**: Noviembre 2024
