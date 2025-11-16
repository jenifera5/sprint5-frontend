
🤖 Entrega S5.02 – Desarrollo con IA Generativa
📘 Descripción General

Durante esta entrega se desarrolló una interfaz frontend moderna en React para consumir la API REST creada previamente en Laravel.
El objetivo principal fue experimentar con el uso de Inteligencia Artificial Generativa (ChatGPT) como asistente de desarrollo, optimizando la generación de código, la corrección de errores y el diseño visual del proyecto.

⚙️ 1. Modelo de IA seleccionado y modo de uso

Se utilizó ChatGPT (modelo GPT-5, OpenAI) como herramienta de apoyo en todo el proceso de desarrollo.
El modelo se empleó para:

Generar estructuras base en React con TypeScript y TailwindCSS.

Diseñar componentes funcionales (Books.tsx, Categories.tsx, etc.) conectados a la API Laravel.

Optimizar llamadas fetch y manejo de estados en React con useState y useEffect.

Resolver errores de conexión entre frontend y backend (autenticación Bearer Token, rutas API, CORS).

Proponer mejoras de interfaz (modal de creación, etiquetas dinámicas y sistema de búsqueda).

Tipo de asistencia: diálogo iterativo, corrigiendo y perfeccionando el código en cada iteración.

💬 2. Registro de interacciones con la IA

Durante el desarrollo se realizaron múltiples sesiones con ChatGPT.
Algunos ejemplos relevantes fueron:

Generación inicial del CRUD de libros: el modelo generó un componente Books.tsx completamente funcional para listar, crear, editar y eliminar libros.

Depuración del buscador: se detectó que el endpoint /api/books/search no respondía correctamente; la IA propuso probar rutas alternativas y manejar ambas (/api/books/search y /books/search) automáticamente.

Integración de categorías: el modelo ayudó a añadir la relación Libro → Categorías mediante with('categorias') en Laravel y su renderizado dinámico en el frontend con Tag icons.

Mejoras visuales: ChatGPT sugirió el uso de clases Tailwind para lograr una interfaz limpia, minimalista y coherente con el diseño general del proyecto.

🧩 3. Análisis del código generado

El código generado por la IA fue funcional, aunque requirió revisión manual:

Se corrigieron nombres de rutas y tokens de autorización.

Se adaptó la estructura a TypeScript, mejorando la validación de datos (interface Book, interface Categoria).

Se optimizó la gestión del estado en React para evitar renderizados innecesarios.

Se agregaron controles de error (try/catch, response.ok) y validaciones de formularios.

El resultado final fue un frontend totalmente operativo, conectado a la API Laravel, con una experiencia de usuario fluida y moderna.

🔗 4. Conexión entre Frontend y Backend

La API desarrollada en Laravel maneja los recursos de libros y categorías, protegidos mediante token Bearer.
El frontend React se comunica con ella usando fetch y los endpoints definidos:

Método	Endpoint	Descripción
GET	/api/books	Lista todos los libros
POST	/api/books	Crea un nuevo libro
PUT	/api/books/{id}	Edita un libro existente
DELETE	/api/books/{id}	Elimina un libro
GET	/api/books/search?query=	Busca libros por título o autor

El componente principal Books.tsx incluye:

Modal de creación/edición con selector múltiple de categorías.

Barra de búsqueda dinámica con detección automática del endpoint correcto.

Renderizado de etiquetas de categoría mediante Tag icons.

Todo el flujo CRUD fue probado con la API activa en http://127.0.0.1:8000.

🧠 5. Reflexión sobre el proceso de aprendizaje

Este sprint permitió consolidar conocimientos en:

Comunicación entre frontend y backend mediante API REST.

Comprensión del código generado por IA y adaptación a un entorno real.

Resolución de problemas y depuración de errores con ayuda contextual de la IA.

Mejora del razonamiento lógico al validar cada fragmento propuesto antes de implementarlo.

La IA no sustituyó el aprendizaje, sino que aceleró la comprensión de conceptos complejos y ayudó a estructurar el proyecto con mayor eficiencia.
El proceso de colaboración con ChatGPT fomentó un pensamiento crítico y la capacidad de transformar respuestas automáticas en código mantenible y funcional.

🧾 6. Código y repositorio de GitHub

El código fuente completo está disponible en el siguiente repositorio:

🔗 Repositorio: GitHub – Sprint 5 Laravel API REST

📁 Contiene:

Carpeta backend/ → Proyecto Laravel con controladores, rutas, seeders y autenticación.

Carpeta frontend/ → Proyecto React con los componentes (Books.tsx, Categories.tsx, ModalForm.tsx, etc.).

Documentación en README.md con las secciones de análisis, integración y reflexión.

🧩 Resultado final

El resultado es un sistema completo Biblioteca Universo de Libros, donde:

El backend Laravel gestiona los recursos y la lógica.

El frontend React ofrece una interfaz amigable y moderna.

La IA generativa (ChatGPT) se usó como asistente de desarrollo para optimizar el proceso y mejorar la comprensión del código.

💬 “El verdadero aprendizaje no fue generar código, sino entender cómo razonar junto a la IA para construir software mejor estructurado y funcional.”
— Jenifer Álvarez, Sprint 5
=======
# 📚 Library Management System - Frontend

> Aplicación web con React 18 + TypeScript + Vite

Cliente moderno para el sistema de gestión de biblioteca, desarrollado con React, TypeScript y TailwindCSS, consumiendo la API REST de Laravel.

![React](https://img.shields.io/badge/React-18-61DAFB?style=flat&logo=react&logoColor=black)
![TypeScript](https://img.shields.io/badge/TypeScript-5-3178C6?style=flat&logo=typescript&logoColor=white)
![Vite](https://img.shields.io/badge/Vite-5-646CFF?style=flat&logo=vite&logoColor=white)
![TailwindCSS](https://img.shields.io/badge/Tailwind-3-06B6D4?style=flat&logo=tailwindcss&logoColor=white)

---

## 📋 Tabla de Contenidos

- [Características](#-características)
- [Tecnologías](#️-tecnologías)
- [Requisitos Previos](#-requisitos-previos)
- [Instalación](#-instalación)
- [Configuración](#️-configuración)
- [Estructura del Proyecto](#-estructura-del-proyecto)
- [Uso](#-uso)
- [Licencia](#-licencia)

---

## ✨ Características

- **Arquitectura Moderna**
  - Vite como build tool (desarrollo ultrarrápido)
  - TypeScript para type safety
  - React Router DOM para navegación SPA
  
- **Gestión de Estado**
  - Context API para autenticación global
  - Axios con interceptores automáticos para tokens
  
- **Interfaz de Usuario**
  - Diseño responsive con TailwindCSS
  - Componentes reutilizables con TypeScript
  - Formularios con validación
  - Búsqueda en tiempo real
  - Dashboard interactivo
  
- **Integración con API**
  - Servicios dedicados por recurso (books, categories, loans)
  - Manejo de errores consistente
  - Normalización de respuestas
  - Autenticación JWT automática

---

## 🛠️ Tecnologías

- **React 18** - Librería UI
- **TypeScript 5** - Superset de JavaScript tipado
- **Vite 5** - Build tool moderna
- **TailwindCSS 3** - Framework CSS utility-first
- **React Router DOM 6** - Enrutamiento SPA
- **Axios** - Cliente HTTP con interceptores
- **Lucide React** - Iconos SVG

---

## 📦 Requisitos Previos

Asegúrate de tener instalado:

| Software | Versión Mínima | Verificar |
|----------|----------------|-----------|
| Node.js  | 18.x           | `node -v` |
| NPM      | 9.x            | `npm -v` |
| Git      | 2.x            | `git --version` |

**Backend requerido:**
- API REST Laravel corriendo en `http://127.0.0.1:8000`
- Ver [README del backend](https://github.com/jenifera5/sprint5) para instrucciones

---

## 🚀 Instalación

### Paso 1: Clonar el repositorio

```bash
git clone https://github.com/jenifera5/sprint5-frontend.git
cd sprint5-frontend
```

### Paso 2: Instalar dependencias

```bash
npm install
```

### Paso 3: Configurar variables de entorno

Crea un archivo `.env` en la raíz del proyecto:

```env
VITE_API_BASE_URL=http://127.0.0.1:8000/api
```

### Paso 4: Iniciar servidor de desarrollo

```bash
npm run dev
```

La aplicación estará disponible en: `http://localhost:5173`

---

## ⚙️ Configuración

### Variables de Entorno

```env
# URL base de la API (sin /api al final)
VITE_API_BASE_URL=http://127.0.0.1:8000/api
```

### Cliente API (Axios)

El archivo `src/services/client.ts` configura Axios con interceptores:

```typescript
import axios from "axios";

export const api = axios.create({
  baseURL: "http://127.0.0.1:8000/api",
  headers: {
    'Content-Type': 'application/json',
    'Accept': 'application/json'
  }
});

// Interceptor para añadir token automáticamente
api.interceptors.request.use((config) => {
  const token = localStorage.getItem("token");
  if (token) {
    config.headers["Authorization"] = `Bearer ${token}`;
  }
  return config;
});

// Interceptor para manejar errores
api.interceptors.response.use(
  (res) => res,
  (err) => {
    if (err?.response?.status === 401) {
      localStorage.removeItem("token");
      window.location.href = "/login";
    }
    return Promise.reject(err);
  }
);
```

---

## 📂 Estructura del Proyecto

```
sprint5-frontend/
├── src/
│   ├── components/
│   │   └── layout/
│   │       └── DashboardLayout.tsx
│   ├── pages/
│   │   ├── Books.tsx
│   │   ├── Categories.tsx
│   │   ├── Loans.tsx
│   │   ├── Stats.tsx
│   │   ├── login.tsx
│   │   ├── Register.tsx
│   │   └── Logout.tsx
│   ├── services/
│   │   ├── client.ts
│   │   ├── authService.ts
│   │   ├── bookService.ts
│   │   ├── categoryService.ts
│   │   └── loanService.ts
│   ├── App.tsx
│   ├── main.tsx
│   └── index.css
├── public/
├── .env
├── package.json
├── tsconfig.json
├── tailwind.config.js
└── vite.config.ts
```

---

## 🎨 Componentes Principales

### DashboardLayout

Layout principal con sidebar y navegación:

```typescript

  

```

**Características:**
- Sidebar responsive con menú colapsable
- Header con avatar y dropdown
- Logout integrado
- Navegación con React Router

### Páginas

#### Books (Libros)
- Listado de libros con paginación
- Búsqueda en tiempo real
- Crear/Editar/Eliminar (admin)
- Asignar categorías
- Ver detalles

#### Categories (Categorías)
- CRUD completo de categorías
- Validación de formularios
- Confirmación de eliminación

#### Loans (Préstamos)
- Gestión de préstamos
- Estados: pendiente, activo, devuelto, vencido
- Filtrado por fecha
- Detalles de usuario y libro

#### Stats (Estadísticas)
- Top 5 libros más prestados
- Gráficos de barras interactivos
- Métricas visuales

---

## 💻 Uso

### 1. Registro

Accede a `/register` y crea una cuenta:

```
Nombre: Admin Test
Email: admin@test.com
Password: 123456
Rol: Administrador
```

### 2. Login

Accede a `/login` con las credenciales:

```
Email: admin@test.com
Password: 123456
```

### 3. Navegación

Una vez autenticado, podrás acceder a:

- **`/`** - Gestión de libros
- **`/categories`** - Gestión de categorías
- **`/loans`** - Gestión de préstamos
- **`/stats`** - Estadísticas

### 4. Logout

Click en el avatar → "Cerrar sesión"

---

## 🔧 Scripts Disponibles

```bash
# Desarrollo
npm run dev

# Build para producción
npm run build

# Preview del build
npm run preview

# Lint
npm run lint

# Type checking
npm run type-check
```

---

## 🎯 Servicios API

### authService.ts

```typescript
export async function register(payload: {
  nombre: string;
  email: string;
  password: string;
  rol?: string;
}) {
  const { data } = await api.post("/register", payload);
  return data;
}

export async function login(payload: { 
  email: string; 
  password: string 
}) {
  const { data } = await api.post("/login", payload);
  return data;
}

export async function logout() {
  const { data } = await api.post("/logout");
  return data;
}
```

### bookService.ts

```typescript
export async function listBooks() {
  const { data } = await api.get("/books");
  return data;
}

export async function createBook(payload: BookPayload) {
  const { data } = await api.post("/books", payload);
  return data;
}

export async function updateBook(id: number, payload: BookPayload) {
  const { data } = await api.put(`/books/${id}`, payload);
  return data;
}

export async function deleteBook(id: number) {
  const { data } = await api.delete(`/books/${id}`);
  return data;
}

export async function searchBooks(query: string) {
  const { data } = await api.get("/books/search", { params: { query } });
  return data;
}

export async function popularBooks() {
  const { data } = await api.get("/books/stats/popular");
  return data;
}
```

---

## 🚀 Deployment

### Build para Producción

```bash
npm run build
```

Esto genera la carpeta `dist/` con los archivos estáticos optimizados.

### Deploy en Vercel

```bash
# Instalar Vercel CLI
npm install -g vercel

# Deploy
vercel
```

Configurar variable de entorno en Vercel:
- `VITE_API_BASE_URL=https://tu-api-backend.com/api`

### Deploy en Netlify

```bash
# Build
npm run build

# Deploy
netlify deploy --prod --dir=dist
```

### Variables de Entorno en Producción

Asegúrate de configurar:
```env
VITE_API_BASE_URL=https://tu-api-backend.com/api
```

---

## 📄 Licencia

Este proyecto está bajo la **Licencia MIT**. Ver archivo `LICENSE` para más detalles.

```
MIT License

Copyright (c) 2025 Jenifer Álvarez

Permission is hereby granted, free of charge, to any person obtaining a copy
of this software and associated documentation files (the "Software"), to deal
in the Software without restriction, including without limitation the rights
to use, copy, modify, merge, publish, distribute, sublicense, and/or sell
copies of the Software, and to permit persons to whom the Software is
furnished to do so, subject to the following conditions:

The above copyright notice and this permission notice shall be included in all
copies or substantial portions of the Software.

THE SOFTWARE IS PROVIDED "AS IS", WITHOUT WARRANTY OF ANY KIND, EXPRESS OR
IMPLIED, INCLUDING BUT NOT LIMITED TO THE WARRANTIES OF MERCHANTABILITY,
FITNESS FOR A PARTICULAR PURPOSE AND NONINFRINGEMENT. IN NO EVENT SHALL THE
AUTHORS OR COPYRIGHT HOLDERS BE LIABLE FOR ANY CLAIM, DAMAGES OR OTHER
LIABILITY, WHETHER IN AN ACTION OF CONTRACT, TORT OR OTHERWISE, ARISING FROM,
OUT OF OR IN CONNECTION WITH THE SOFTWARE OR THE USE OR OTHER DEALINGS IN THE
SOFTWARE.
```

---

## 👩‍💻 Autora

**Jenifer Álvarez**

Proyecto desarrollado como parte del **Sprint 5 - API REST con Laravel Passport** del curso **FullStack** de **IT Academy**.

### Contacto

- **GitHub:** [@jenifera5](https://github.com/jenifera5)
- **Proyecto Backend:** [Sprint 5 - Biblioteca REST API](https://github.com/jenifera5/sprint5)
- **Proyecto Frontend:** [Sprint 5 - Frontend](https://github.com/jenifera5/sprint5-frontend)

---

## 🙏 Agradecimientos

- **IT Academy** - Por el programa FullStack y la guía durante el sprint
- **React Team** - Por la librería UI moderna y reactiva
- **Vite Team** - Por la herramienta de build ultrarrápida
- **TailwindCSS** - Por el framework CSS utility-first
- **Claude (Anthropic)** - Por la asistencia con IA generativa durante el desarrollo

---

## 📝 Notas Técnicas

### TypeScript

Este proyecto usa TypeScript estricto. Interfaces principales:

```typescript
interface Book {
  id: number;
  titulo: string;
  autor: string;
  anio: number;
  disponibles: number;
  categorias?: Categoria[];
}

interface Category {
  id: number;
  nombre: string;
  descripcion: string;
}

interface Loan {
  id: number;
  id_usuario: number;
  id_libro: number;
  fecha_prestamo: string;
  fecha_devolucion: string;
  estado: string;
  usuario?: { nombre: string };
  libro?: { titulo: string };
}
```

### Almacenamiento Local

El token JWT se guarda en `localStorage`:

```typescript
// Guardar token
localStorage.setItem("token", data.token);
localStorage.setItem("user", JSON.stringify(data.usuario));

// Leer token
const token = localStorage.getItem("token");

// Eliminar token (logout)
localStorage.removeItem("token");
localStorage.removeItem("user");
```

### Manejo de Errores

```typescript
try {
  const response = await api.get("/books");
  setBooks(response.data);
} catch (error) {
  console.error("Error al obtener libros:", error);
  setBooks([]);
}
```

---

**Última actualización:** Noviembre 2025 | **Versión:** 1.0.0


















































































































































































