# 📚 NextRead

Una plataforma moderna y social para descubrir, compartir y conectar a través de libros. NextRead permite a los usuarios explorar un extenso catálogo de obras, dejar reseñas, dar likes, seguir a otros lectores y recibir notificaciones en tiempo real.

---

## ✨ Características Principales

### 📖 Gestión de Libros
- Catálogo extenso de libros con autores y géneros variados
- Búsqueda avanzada por título, autor, género y década
- Clasificación por tendencias y recomendaciones personalizadas
- Visualización de detalles completos del libro (sinopsis, portada, autor, etc.)

### 👤 Perfil de Usuario
- Creación y edición de perfiles personalizados
- Avatar e ícono personalizado
- Banner de perfil customizable
- Gestión de géneros y autores preferidos
- Sistema de logros y gamificación

### 📝 Reseñas y Calificaciones
- Crear y compartir reseñas de libros
- Sistema de calificación de 1 a 5 estrellas
- Dar "likes" a reseñas de otros usuarios
- Visualización ordenada de reseñas (por likes, fecha, calidad del comentario)

### 🤝 Red Social
- Seguir y dejar de seguir a otros usuarios
- Ver seguidores y seguidos
- Sistema de notificaciones en tiempo real
- Notificaciones de nuevos followers y likes en reseñas
- Modal de notificaciones con avatar e información del usuario

### 📚 Listas Personalizadas
- Crear listas personalizadas de libros
- Organizar libros por estado: leídos, en lectura, para leer, favoritos
- Agregar libros a listas personalizadas

### 🔐 Seguridad y Autenticación
- Registro e inicio de sesión con JWT
- Encriptación de contraseñas con bcrypt
- Recuperación de contraseña por correo electrónico
- Cambio de email con confirmación
- Eliminación de cuenta con confirmación por email

### ⚙️ Administración
- Panel de administrador para gestionar usuarios
- Banear usuarios infractores
- Eliminar reseñas inapropiadas con descargo registrado
- Suspensión automática de usuarios por reseñas eliminadas

---

## 🛠️ Stack Tecnológico

### Backend
- **Node.js** + **Express.js** - Servidor web
- **Sequelize** - ORM para gestión de base de datos
- **MySQL** - Base de datos relacional
- **JWT** - Autenticación y autorización
- **bcrypt** - Encriptación de contraseñas
- **Nodemailer** - Envío de emails

### Frontend
- **React 19** - Librería de interfaz de usuario
- **Vite** - Build tool y dev server
- **React Router 7** - Enrutamiento
- **Axios** - Cliente HTTP
- **Framer Motion** - Animaciones
- **Lucide React** - Iconos
- **CSS3** - Estilos personalizados

---

## 🚀 Instalación y Setup

### Requisitos Previos
- Node.js (v16 o superior)
- MySQL Server
- Git

### Pasos de Instalación

#### 1. Clonar el Repositorio
```bash
git clone https://github.com/AlejoGuerraa/nextRead.git
cd nextRead
```

#### 2. Configurar Backend
```bash
cd api
npm install
```

Crear archivo `.env` o configurar conexión a MySQL en `config/db.js`

```bash
npm start
```

El servidor correrá en `http://localhost:3000`

#### 3. Configurar Frontend
```bash
cd ../client
npm install
npm run dev
```

La aplicación estará disponible en `http://localhost:5173`

---

## 📁 Estructura del Proyecto

```
nextRead/
├── api/                          # Backend Express.js
│   ├── config/
│   │   └── db.js                # Configuración de base de datos
│   ├── controller/              # Lógica de negocio
│   │   ├── peticionesUsuario.js
│   │   ├── peticionesLibros.js
│   │   ├── busqueda.js
│   │   ├── peticionesAdmin.js
│   │   └── ...
│   ├── middlewares/             # Middlewares de autenticación
│   │   ├── isAuth.js
│   │   └── isAdmin.js
│   ├── models/                  # Modelos Sequelize
│   │   ├── Usuario.js
│   │   ├── Libro.js
│   │   ├── Resena.js
│   │   ├── ResenaLike.js
│   │   └── ...
│   ├── data/                    # Datos iniciales y seeders
│   └── index.js                 # Punto de entrada
│
├── client/                       # Frontend React
│   ├── public/
│   │   ├── portadasLibros/     # Portadas de libros por autor
│   │   ├── iconos/             # Avatares de usuarios
│   │   └── banners/            # Banners de perfil
│   ├── src/
│   │   ├── components/         # Componentes React
│   │   │   ├── acceso/         # Login/Register
│   │   │   ├── notificaciones/ # Modal de notificaciones
│   │   │   ├── perfil/         # Componentes de perfil
│   │   │   ├── settings/       # Configuración
│   │   │   ├── header.jsx      # Encabezado
│   │   │   └── ...
│   │   ├── pages/              # Páginas principales
│   │   ├── pagescss/           # Estilos CSS
│   │   ├── assets/             # Imágenes y assets
│   │   ├── App.jsx
│   │   └── main.jsx
│   ├── index.html
│   ├── vite.config.js
│   └── package.json
│
└── README.md
```

---

## 🔌 API Endpoints Principales

### Autenticación
- `POST /nextread/register` - Registro de usuario
- `POST /nextread/login` - Inicio de sesión
- `POST /nextread/user/change-password` - Cambiar contraseña

### Usuarios
- `GET /nextread/user` - Obtener datos del usuario (requiere auth)
- `GET /nextread/user/:id/seguidores` - Listar seguidores
- `GET /nextread/user/:id/seguidos` - Listar seguidos
- `POST /nextread/seguir/:targetId` - Seguir usuario
- `POST /nextread/dejar-seguir/:targetId` - Dejar de seguir

### Libros y Reseñas
- `GET /nextread/libros` - Obtener todos los libros
- `GET /nextread/libro/:id` - Obtener detalles de libro
- `GET /nextread/resenas/:idLibro` - Obtener reseñas de un libro
- `POST /nextread/resena/:idLibro` - Crear reseña
- `POST /nextread/resena/:id/like` - Dar like a una reseña
- `DELETE /nextread/resena/:id/like` - Remover like

### Notificaciones
- `POST /nextread/notificaciones/marcar-leidas` - Marcar notificaciones como leídas
- `GET /nextread/user/public/:id` - Obtener datos públicos de usuario

### Búsqueda
- `GET /nextread/buscar` - Búsqueda general
- `GET /nextread/tendencias` - Libros en tendencia
- `GET /nextread/libros/por-decada` - Libros por década

---

## 🔐 Autenticación y Autorización

La aplicación utiliza **JWT (JSON Web Tokens)** para autenticación:

1. Usuario se registra/loguea y recibe un token JWT
2. El token se almacena en `localStorage`
3. Cada petición autenticada incluye: `Authorization: Bearer <token>`
4. El middleware `isAuth` valida el token
5. El middleware `isAdmin` verifica permisos de administrador

---

## 📊 Modelo de Base de Datos

### Tablas Principales

**Usuario**
- id, nombre, apellido, correo, usuario, contrasena
- rol (Admin/Usuario), fecha_nacimiento, activo
- Géneros y autores preferidos
- Listas de libros (leídos, favoritos, en lectura, para leer)
- Notificaciones, logros, iconos, banners

**Libro**
- id, titulo, autor_id, sinopsis, portada
- Géneros y décadas

**Resena**
- id, usuario_id, libro_id, puntuacion, comentario
- likes, fecha, activo

**ResenaLike**
- id, resena_id, usuario_id (único por resena)

**Seguidos_Seguidores**
- id, remitente_id, destinatario_id, estado

**Logro**
- id, nombre, descripcion, icono

---

## 🎨 Características de UX/UI

- **Responsive Design** - Funciona en desktop, tablet y móvil
- **Dark/Light Mode Compatible** - Diseño adaptable
- **Animaciones Suaves** - Transiciones con Framer Motion
- **Interfaz Intuitiva** - Fácil de navegar
- **Notificaciones en Tiempo Real** - Modal con información actualizada
- **Iconografía Clara** - Iconos de Lucide React
- **Colores Coherentes** - Paleta de colores profesional

---

## 🚦 Variables de Entorno (Backend)

Crear archivo `.env` en la carpeta `api/`:

```env
DB_HOST=localhost
DB_PORT=3306
DB_USER=root
DB_PASSWORD=tu_contraseña
DB_NAME=nextread
JWT_SECRET=tu_clave_secreta_jwt
MAIL_USER=tu_email@gmail.com
MAIL_PASSWORD=tu_contraseña_app
```

---

## 📈 Roadmap Futuro

- [ ] Recomendaciones basadas en IA
- [ ] Chat directo entre usuarios
- [ ] Clubs de lectura
- [ ] Integración con APIs de libros (Google Books, OpenLibrary)
- [ ] Sistema de puntos y premios
- [ ] Reportes de usuario
- [ ] Dark mode toggle
- [ ] Exportación de listas

---

## 👥 Equipo

Desarrollado por **Agustin Rivera, Alejo Guerra, Renata Gallucci, Sofia Power, Carolina Mendez**

---

## 📧 Contacto

Para preguntas, sugerencias o reportar bugs:
- Email: [tu_nextreadoficial@gmail.com](mailto:nextreadoficial@gmail.com)
- GitHub: [@AlejoGuerraa](https://github.com/AlejoGuerraa)

---

**¡Gracias por usar NextRead! Esperamos que disfrutes la experiencia de descubrir nuevos libros y conectar con otros lectores apasionados.** 📚✨
