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

El archivo `src/api/client.ts` configura Axios con interceptores:

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
│   ├── api/                        # Servicios de API
│   │   ├── authService.ts          # Autenticación (login, register, logout)
│   │   ├── bookService.ts          # CRUD de libros
│   │   ├── categoryService.ts      # CRUD de categorías
│   │   ├── client.ts               # Cliente Axios configurado
│   │   └── loanService.ts          # Gestión de préstamos
│   │
│   ├── assets/                     # Recursos estáticos
│   │   ├── services/
│   │   │   └── api.js              # Configuración alternativa API
│   │   └── react.svg               # Logo React
│   │
│   ├── components/                 # Componentes reutilizables
│   │   ├── layout/
│   │   │   └── DashboardLayout.tsx # Layout principal con sidebar
│   │   ├── ui/                     # Componentes UI base
│   │   │   ├── avatar.tsx          # Avatar de usuario
│   │   │   ├── button.tsx          # Botones personalizados
│   │   │   ├── card.tsx            # Tarjetas de contenido
│   │   │   ├── dropdown-menu.tsx   # Menús desplegables
│   │   │   ├── input.tsx           # Inputs de formulario
│   │   │   └── label.tsx           # Etiquetas de formulario
│   │   └── ProtectedRoute.tsx      # HOC para rutas protegidas
│   │
│   ├── context/                    # Context API
│   │   └── AuthContext.tsx         # Estado global de autenticación
│   │
│   ├── lib/                        # Utilidades
│   │   └── utils.tsx               # Funciones helper
│   │
│   ├── pages/                      # Páginas principales
│   │   ├── Books.tsx               # Gestión de libros
│   │   ├── Categories.tsx          # Gestión de categorías
│   │   ├── Loans.tsx               # Gestión de préstamos
│   │   ├── Stats.tsx               # Estadísticas y gráficos
│   │   ├── login.tsx               # Página de inicio de sesión
│   │   ├── Logout.tsx              # Página de cierre de sesión
│   │   └── Register.tsx            # Página de registro
│   │
│   ├── router/                     # Configuración de rutas
│   │
│   ├── App.css                     # Estilos globales CSS
│   ├── App.jsx                     # Componente raíz (JSX)
│   ├── App.tsx                     # Componente raíz (TypeScript)
│   ├── index.css                   # Estilos base + Tailwind
│   ├── main.jsx                    # Punto de entrada (JSX)
│   └── main.tsx                    # Punto de entrada (TypeScript)
│
├── public/                         # Archivos públicos
│
├── vendor/                         # Dependencias PHP (si aplica)
│
├── .env                            # Variables de entorno
├── .gitignore                      # Archivos ignorados por Git
├── composer.json                   # Dependencias PHP
├── composer.lock                   # Lock de dependencias PHP
├── eslint.config.js                # Configuración ESLint
├── index.html                      # HTML principal
├── package-lock.json               # Lock de dependencias NPM
├── package.json                    # Dependencias y scripts NPM
├── postcss.config.js               # Configuración PostCSS
├── README.md                       # Documentación del proyecto
├── tailwind.config.js              # Configuración TailwindCSS
└── vite.config.ts                  # Configuración Vite
```

---

## 🎨 Componentes Principales

### DashboardLayout

Layout principal con sidebar y navegación:

```typescript
import { Link, useNavigate } from "react-router-dom";
import { BookOpen, Tag, Users, BarChart, LogOut } from "lucide-react";

export default function DashboardLayout({ children }: { children: React.ReactNode }) {
  const navigate = useNavigate();
  
  const handleLogout = () => {
    localStorage.removeItem("token");
    localStorage.removeItem("user");
    navigate("/login");
  };

  return (
    
      {/* Sidebar */}
      
        
          📚 Biblioteca
        
        
          
            
            Libros
          
          
            
            Categorías
          
          
            
            Préstamos
          
          
            
            Estadísticas
          
        
      

      {/* Main Content */}
      
        {/* Header */}
        
          
            Dashboard
            
              
              Cerrar sesión
            
          
        

        {/* Page Content */}
        
          {children}
        
      
    
  );
}
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






































































































































































































































































































































































