# 🚀 API Backend PixelHub - JSON Server

API REST desarrollada con JSON Server para el sistema de gestión de suscripciones digitales de PixelHub. Proporciona endpoints para autenticación de usuarios y gestión completa de suscripciones.

## 🌐 API en Producción

**Base URL**: `https://api-prueba1-eog3.onrender.com`

La API está desplegada y funcionando en Render, lista para ser consumida por aplicaciones frontend.

## 📋 Características

- **API REST completa** con operaciones CRUD
- **Autenticación de usuarios** con validación de credenciales
- **Gestión de suscripciones** digitales
- **Respuestas en formato JSON**
- **CORS habilitado** para peticiones desde cualquier origen
- **Despliegue automático** en Render

## 🛠️ Tecnologías Utilizadas

- **Runtime**: Node.js
- **Framework**: JSON Server
- **Deployment**: Render
- **Base de datos**: JSON (archivo db.json)

## 📊 Endpoints Disponibles

### 🔐 Usuarios
| Método | Endpoint | Descripción |
|--------|----------|-------------|
| `GET` | `/users` | Obtener todos los usuarios |
| `GET` | `/users/:id` | Obtener usuario por ID |
| `POST` | `/users` | Crear nuevo usuario |
| `PUT` | `/users/:id` | Actualizar usuario completo |
| `PATCH` | `/users/:id` | Actualizar usuario parcial |
| `DELETE` | `/users/:id` | Eliminar usuario |

### 📱 Suscripciones
| Método | Endpoint | Descripción |
|--------|----------|-------------|
| `GET` | `/suscripciones` | Obtener todas las suscripciones |
| `GET` | `/suscripciones/:id` | Obtener suscripción por ID |
| `POST` | `/suscripciones` | Crear nueva suscripción |
| `PUT` | `/suscripciones/:id` | Actualizar suscripción completa |
| `PATCH` | `/suscripciones/:id` | Actualizar suscripción parcial |
| `DELETE` | `/suscripciones/:id` | Eliminar suscripción |

## 🔍 Ejemplos de Uso

### Obtener todos los usuarios
```bash
curl -X GET https://api-prueba1-eog3.onrender.com/users
```

### Obtener todas las suscripciones
```bash
curl -X GET https://api-prueba1-eog3.onrender.com/suscripciones
```

### Crear una nueva suscripción
```bash
curl -X POST https://api-prueba1-eog3.onrender.com/suscripciones \
  -H "Content-Type: application/json" \
  -d '{
    "nombre": "Netflix",
    "costo": 15.99,
    "categoria": "Streaming",
    "fechaRenovacion": "2024-01-15",
    "userId": 1
  }'
```

### Actualizar una suscripción
```bash
curl -X PUT https://api-prueba1-eog3.onrender.com/suscripciones/1 \
  -H "Content-Type: application/json" \
  -d '{
    "nombre": "Netflix Premium",
    "costo": 19.99,
    "categoria": "Streaming",
    "fechaRenovacion": "2024-02-15",
    "userId": 1
  }'
```

### Eliminar una suscripción
```bash
curl -X DELETE https://api-prueba1-eog3.onrender.com/suscripciones/1
```

## 📝 Estructura de Datos

### Usuario
```json
{
  "id": 1,
  "email": "admin@pixelhub.com",
  "password": "123456",
  "nombre": "Administrador",
  "fechaCreacion": "2024-01-01"
}
```

### Suscripción
```json
{
  "id": 1,
  "nombre": "Netflix",
  "costo": 15.99,
  "categoria": "Streaming",
  "fechaRenovacion": "2024-01-15",
  "userId": 1,
  "activa": true,
  "fechaCreacion": "2024-01-01"
}
```

## 🔧 Configuración Local

Si deseas ejecutar la API localmente:

### Requisitos Previos
- Node.js (versión 16 o superior)
- npm o yarn

### Instalación
```bash
# Clonar el repositorio
git clone https://github.com/danmalarcon/API-Prueba1.git
cd API-Prueba1

# Instalar dependencias
npm install

# Ejecutar en modo desarrollo
npm start

# La API estará disponible en http://localhost:3000
```

### Estructura del Proyecto
```
API-Prueba1/
├── db.json          # Base de datos JSON
├── package.json     # Dependencias del proyecto
├── server.js        # Configuración del servidor (si existe)
└── README.md        # Documentación
```

## 🌍 Despliegue en Render

La API está configurada para desplegarse automáticamente en Render:

1. **Conectada al repositorio**: `https://github.com/danmalarcon/API-Prueba1.git`
2. **URL de producción**: `https://api-prueba1-eog3.onrender.com`
3. **Despliegue automático**: Cada push al repositorio actualiza la API

### Variables de Entorno (Render)
```bash
NODE_ENV=production
PORT=10000
```

## 🔒 Seguridad y Limitaciones

### Importante
- **Entorno de desarrollo**: Esta API está diseñada para pruebas y desarrollo
- **Sin autenticación JWT**: Las credenciales se validan directamente
- **CORS abierto**: Permite peticiones desde cualquier origen
- **Datos persistentes**: Los datos se mantienen entre reinicios en Render

### Recomendaciones para Producción
- Implementar autenticación JWT
- Configurar CORS específico
- Usar una base de datos real (PostgreSQL, MongoDB)
- Añadir validaciones de entrada
- Implementar rate limiting

## 🔗 Frontend Asociado

Esta API está diseñada para trabajar con el frontend de PixelHub:

- **Repositorio Frontend**: `https://github.com/danmalarcon/front-app-prueba1.git`
- **URL Frontend**: `https://front-app-prueba1.vercel.app`

## 📊 Filtros y Consultas

JSON Server soporta filtros automáticos:

```bash
# Filtrar por usuario
GET /suscripciones?userId=1

# Filtrar por categoría
GET /suscripciones?categoria=Streaming

# Búsqueda parcial en nombre
GET /suscripciones?nombre_like=Net

# Ordenar por costo
GET /suscripciones?_sort=costo&_order=desc

# Paginación
GET /suscripciones?_page=1&_limit=10
```

## 🚀 Estado del Servicio

### Monitoreo
- **Estado**: ✅ Activo
- **Uptime**: Monitoreado por Render
- **Logs**: Disponibles en el dashboard de Render

### Tiempo de Respuesta
- **Primer acceso**: ~30 segundos (cold start)
- **Accesos posteriores**: <2 segundos
- **Nota**: Render puede dormir la aplicación tras 15 minutos de inactividad

## 🤝 Contribuir

1. Fork el proyecto
2. Crea una rama para tu feature (`git checkout -b feature/nueva-funcionalidad`)
3. Commit tus cambios (`git commit -m 'Agrega nueva funcionalidad'`)
4. Push a la rama (`git push origin feature/nueva-funcionalidad`)
5. Abre un Pull Request

## 📞 Soporte

Si encuentras problemas con la API:

1. Verifica que la URL esté correcta
2. Revisa los headers de las peticiones
3. Consulta los logs en Render
4. Crea un issue en el repositorio

## 📄 Licencia

Este proyecto está bajo la Licencia MIT.

## 👨‍💻 Autor

Desarrollado por Daniel Mazo Alarcón como backend para la simulación de una prueba técnica para una empresa ficticia

---

⭐ **API Lista para Usar**: `https://api-prueba1-eog3.onrender.com`

## 📚 Recursos

- [JSON Server Documentation](https://github.com/typicode/json-server)
- [Render Deployment Guide](https://render.com/docs)
- [REST API Best Practices](https://restfulapi.net/)

## 🔄 Actualizaciones

- **v1.0.0**: API inicial con usuarios y suscripciones
- **Deploy**: Configuración automática en Render
- **CORS**: Habilitado para desarrollo frontend
