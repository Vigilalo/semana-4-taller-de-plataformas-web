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
## Instalación y ejecución

### Requisitos

- Node.js instalado.
- npm disponible en la terminal.
- Archivo `.env` configurado a partir de `.env.example`.

### Instalación

Desde la carpeta raíz del proyecto, ejecutar:

```bash
npm install
```

### Configuración

Crear un archivo `.env` y definir una clave secreta para JWT:

```env
JWT_SECRET=clave_local_de_prueba
NODE_ENV=development
PORT=3010
```

El archivo `.env` no debe subirse al repositorio porque puede contener
información sensible.

### Inicio del servidor

Ejecutar:

```bash
npm start
```

El servidor estará disponible en:

```text
http://localhost:3010
```
## Endpoints de autenticación

### POST /login

Permite autenticar a un usuario.

Ejemplo de solicitud:

```json
{
  "username": "matias",
  "password": "aiep2026"
}
```

Cuando las credenciales son correctas, el servidor genera un JWT y lo almacena
en la cookie `token`.

### GET /privada

Permite acceder a información protegida. La solicitud requiere una cookie
`token` válida.

### POST /logout

Cierra la sesión del usuario y elimina la cookie `token`.

## Respuestas esperadas

- Login correcto: `200 OK`.
- Credenciales incorrectas: `401 Unauthorized`.
- Usuario inexistente: respuesta de error según la validación implementada.
- Acceso sin token: `401 Unauthorized`.
- Acceso con token válido: `200 OK`.
## Casos de prueba

| Nº | Caso | Solicitud | Resultado esperado |
|---:|---|---|---|
| 1 | Login válido | `POST /login` | `200 OK` y cookie `token` |
| 2 | Usuario inexistente | `POST /login` | Respuesta de error |
| 3 | Contraseña incorrecta | `POST /login` | `401 Unauthorized` |
| 4 | Acceso autorizado | `GET /privada` con cookie | `200 OK` |
| 5 | Acceso sin token | `GET /privada` sin cookie | `401 Unauthorized` |
| 6 | Cierre de sesión | `POST /logout` | Cookie eliminada |
| 7 | Acceso posterior al logout | `GET /privada` | `401 Unauthorized` |

Las pruebas deben ejecutarse mediante Postman o una herramienta equivalente.
Cada resultado debe respaldarse con una captura de pantalla.

## Colaboración del equipo

El trabajo se organizó mediante ramas independientes y commits específicos
para cada integrante.

| Integrante | Rama | Responsabilidad |
|---|---|---|
| Yilber Yañez | Rama de autenticación | Validación de usuarios y credenciales |
| Víctor Aizpurua | Rama de seguridad | JWT, cookies, middleware y logout |
| Matías Aquea | `feature/matias-aquea` | Documentación técnica, pruebas y organización del trabajo |

Cada integrante desarrolló sus cambios en una rama separada. Posteriormente,
los aportes fueron integrados mediante Pull Requests hacia la rama principal.

La revisión del historial de GitHub permite identificar el autor, el mensaje y
los archivos modificados en cada commit.