# 🚀 Semana 4 - Taller de Plataformas Web

Proyecto grupal correspondiente a la **Actividad Práctica Formativa de la Semana 4** de la asignatura **Taller de Plataformas Web**.

El objetivo es implementar un servidor backend con **Node.js y Express.js**, incorporando autenticación mediante **JWT**,
almacenamiento del token en **cookies httpOnly**, protección de rutas mediante **middleware** y cierre de sesión.

#################################################################################

## 🎯 Objetivos del proyecto

- ✅ Crear un servidor con Express.js.
- ✅ Implementar una ruta de login.
- ✅ Validar credenciales contra usuarios ficticios.
- ✅ Generar un token JWT.
- ✅ Almacenar el JWT en una cookie segura.
- ✅ Proteger rutas privadas mediante middleware.
- ✅ Validar tokens inválidos o expirados.
- ✅ Implementar cierre de sesión.
- ✅ Utilizar variables de entorno para gestionar secretos.
- ✅ Documentar el trabajo colaborativo mediante Git y GitHub.

#################################################################################

## 🛠️ Tecnologías utilizadas

- 🟢 Node.js
- ⚡ Express.js
- 🔐 JSON Web Token
- 🍪 Cookies
- 🌱 dotenv
- 🟨 JavaScript
- 🌿 Git
- 🐙 GitHub

#################################################################################

## 📁 Estructura general

```text
semana-4-taller-de-plataformas-web/
├── server.js
├── package.json
├── package-lock.json
├── .gitignore
├── .env.example
└── README.md
```
## ⚙️ Instalación y ejecución

### Requisitos

- Node.js instalado.
- npm disponible en la terminal.
- Archivo `.env` configurado a partir de `.env.example`.

### Instalación

```bash
npm install
```

### Configuración

Crear un archivo `.env` con el siguiente contenido:

```env
JWT_SECRET=clave_local_de_prueba
NODE_ENV=development
PORT=3010
```

> [!IMPORTANT]
> El archivo `.env` no debe subirse al repositorio, ya que puede contener información sensible.

### Iniciar servidor

```bash
npm start
```

Servidor disponible en:

```text
http://localhost:3010
```

## 🔐 Endpoints de autenticación

### `POST /login`

Autentica a un usuario con credenciales válidas.

**Ejemplo de solicitud:**

```json
{
  "username": "matias",
  "password": "aiep2026"
}
```

**Resultado esperado:**
- Generación de JWT.
- Almacenamiento del token en la cookie `token`.

### `GET /privada`

Permite acceder a una ruta protegida.  
Requiere una cookie `token` válida.

### `POST /logout`

Cierra la sesión y elimina la cookie `token`.

## 📬 Respuestas esperadas

- `200 OK` para login exitoso.
- `401 Unauthorized` para credenciales incorrectas.
- Error de validación para usuario inexistente.
- `401 Unauthorized` si no existe token.
- `200 OK` si el token es válido.

## 🧪 Casos de prueba

| Nº | Caso | Solicitud | Resultado esperado |
|---:|---|---|---|
| 1 | Login válido | `POST /login` | `200 OK` y cookie `token` |
| 2 | Usuario inexistente | `POST /login` | Respuesta de error |
| 3 | Contraseña incorrecta | `POST /login` | `401 Unauthorized` |
| 4 | Acceso autorizado | `GET /privada` con cookie | `200 OK` |
| 5 | Acceso sin token | `GET /privada` sin cookie | `401 Unauthorized` |
| 6 | Cierre de sesión | `POST /logout` | Cookie eliminada |
| 7 | Acceso posterior al logout | `GET /privada` | `401 Unauthorized` |

> [!NOTE]
> Las pruebas deben ejecutarse con **Postman** o una herramienta equivalente, y cada resultado debe respaldarse con una captura de pantalla.

## 👥 Trabajo colaborativo

El equipo trabajó mediante ramas independientes y commits específicos por integrante.

| Integrante | Rama | Responsabilidad |
|---|---|---|
| Yilber Yañez | Rama de autenticación | Validación de usuarios y credenciales |
| Víctor Aizpurua | `feature/victor-auth-security` | JWT, cookies, middleware y logout |
| Matías Aquea | `feature/matias-aquea` | Documentación técnica, pruebas y organización |

Cada integrante desarrolló sus cambios en una rama separada. Luego, los aportes se integraron mediante **Pull Requests** hacia la rama principal.

La revisión del historial en GitHub permite identificar el autor, el mensaje y los archivos modificados en cada commit.

## ✅ Aprendizajes logrados

- Implementación de autenticación basada en JWT.
- Uso de cookies seguras con `httpOnly`.
- Protección de rutas privadas con middleware.
- Gestión de variables de entorno con `dotenv`.
- Trabajo colaborativo usando ramas, commits y Pull Requests.
