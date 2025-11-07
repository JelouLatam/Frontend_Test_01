# Prueba Técnica - Mid Frontend Developer (React + TailwindCSS)

## 📋 Descripción General

Bienvenido a la prueba técnica para la posición de **Frontend Developer**.

El objetivo es construir un **Blog Dashboard / Social Media Platform** completo y funcional que demuestre tus habilidades en React, TypeScript (o JavaScript), TailwindCSS y mejores prácticas de desarrollo frontend moderno.

**Tiempo disponible:** 48 horas
**Nivel:** Intermedio
**Stack requerido:** React 18+, TypeScript (o JavaScript), TailwindCSS

---

## 🎯 Objetivos de Evaluación

Esta prueba evalúa:
- ✅ Arquitectura de componentes y código limpio
- ✅ Manejo de estado complejo (local y global)
- ✅ TypeScript/JavaScript y código de calidad
- ✅ Diseño responsive y UX
- ✅ Performance y optimización
- ✅ Testing y calidad de código
- ✅ Integración con APIs REST
- ✅ Mejores prácticas de seguridad
- ✅ Accesibilidad (a11y)

---

## 🚀 El Proyecto: Blog Dashboard & Social Media Platform

### Descripción

Crear una aplicación SPA (Single Page Application) para gestionar posts, comentarios y usuarios, similar a una plataforma de blog o red social simplificada.

### Funcionalidades Requeridas

#### 1. **Sistema de Autenticación** 🔐

- Login con email y contraseña
- Validación de formularios (email válido, contraseña mínimo 8 caracteres)
- Persistencia de sesión (localStorage/sessionStorage)
- Protección de rutas (redirect a login si no está autenticado)
- Logout con limpieza de sesión
- Estados de carga durante autenticación

**Notas:**
- Simular autenticación (puedes validar contra los usuarios del API)
- Implementar manejo de errores (credenciales inválidas, timeout, etc.)

---

#### 2. **Dashboard Principal** 📊

Vista principal después del login con:

**Header:**
- Logo/nombre de la aplicación
- Información del usuario logueado
- Botón de logout
- Toggle para modo oscuro/claro
- Menú de navegación responsive

**Panel de Estadísticas (Cards):**
- Total de posts
- Total de usuarios
- Total de comentarios
- Posts del usuario actual (filtrado por userId)
- Gráfico visual simple (puede ser con CSS, no requiere librería)

**Filtros y Búsqueda:**
- Barra de búsqueda por título de post (búsqueda en tiempo real con debounce)
- Filtros múltiples:
  - Por usuario/autor
  - Posts con más comentarios
  - Posts recientes (simulado por ID)
- Los filtros deben ser combinables
- Botón "Limpiar filtros"

**Vistas de Posts:**
- Vista de cards/grid
- Vista de lista
- Guardar preferencia de vista en localStorage

---

#### 3. **Gestión de Posts** ✏️

**Lista de Posts:**
- Grid/List de cards de posts
- Paginación (10, 25, 50 posts por página)
- Acciones rápidas en cada card:
  - Ver detalles
  - Editar post (si es del usuario actual)
  - Eliminar (con confirmación)
  - Ver comentarios

**Card de Post debe mostrar:**
- Título
- Cuerpo (truncado)
- Autor (nombre del usuario)
- Cantidad de comentarios
- Indicador visual si es post del usuario actual

---

#### 4. **Vista de Detalle de Post** 📝

Al hacer click en un post, mostrar vista detallada con:

**Información del Post:**
- Título completo
- Cuerpo completo
- Información del autor (nombre, email, empresa)
- Fecha simulada (puedes usar el ID como referencia)

**Sección de Comentarios:**
- Lista de todos los comentarios del post
- Cada comentario muestra:
  - Nombre/título del comentario
  - Email del autor
  - Cuerpo del comentario
- Paginación de comentarios si son muchos
- Botón para agregar nuevo comentario (simular)

**Acciones:**
- Editar post (si es del usuario actual)
- Eliminar post (si es del usuario actual)
- Volver a la lista

---

#### 5. **Modal de Creación/Edición de Post** 📝

**Campos del Formulario:**

1. **Título** (obligatorio)
   - Mínimo 10 caracteres
   - Máximo 200 caracteres
   - No puede iniciar/terminar con espacios

2. **Contenido/Body** (obligatorio)
   - Mínimo 50 caracteres
   - Máximo 1000 caracteres
   - Textarea con contador de caracteres

3. **Usuario/Autor** (automático)
   - Pre-seleccionado con el usuario logueado
   - No editable en modo edición

**Validaciones:**
- Validación en tiempo real
- Mensajes de error claros y específicos
- Deshabilitar botón "Guardar" si hay errores
- Confirmación antes de cerrar modal si hay cambios sin guardar

---

#### 6. **Gestión de Usuarios** 👥

**Lista de Usuarios:**
- Grid de cards con información de usuarios
- Cada card muestra:
  - Nombre y username
  - Email
  - Empresa
  - Ciudad
  - Cantidad de posts del usuario
- Click en usuario para ver sus posts

**Vista de Perfil de Usuario:**
- Información completa del usuario
- Lista de posts del usuario
- Estadísticas (total de posts, total de comentarios en sus posts)

---

#### 7. **Características Avanzadas** ⚡

**Búsqueda Global:**
- Buscar en posts por título y contenido
- Buscar usuarios por nombre, username o email
- Resultados en tiempo real con debounce (300ms)
- Highlight de términos encontrados

**Notificaciones/Toast:**
- Feedback visual para todas las acciones:
  - Post creado/actualizado/eliminado
  - Errores de API
  - Comentario agregado
- Auto-dismiss después de 3-5 segundos
- Posibilidad de cerrar manualmente

**Estados de Carga:**
- Skeletons para carga inicial
- Spinners para acciones individuales
- Disable de botones durante operaciones
- Indicadores de progreso

**Manejo de Errores:**
- Error boundaries para errores de React
- Fallback UI cuando falla la carga de datos
- Retry para operaciones fallidas
- Mensajes de error amigables

**Optimistic Updates:**
- Al crear/editar/eliminar posts, actualizar UI inmediatamente
- Revertir si la operación falla

---

## 📦 API de JSONPlaceholder

**Base URL:** `https://jsonplaceholder.typicode.com`
**Documentación:** [JSONPlaceholder Guide](https://jsonplaceholder.typicode.com/guide/)

### Endpoints principales:

```
GET    /posts              - Obtener todos los posts
GET    /posts/:id          - Obtener un post específico
GET    /posts/:id/comments - Obtener comentarios de un post
GET    /comments?postId=1  - Obtener comentarios por postId
POST   /posts              - Crear nuevo post
PUT    /posts/:id          - Actualizar post completo
PATCH  /posts/:id          - Actualizar post parcialmente
DELETE /posts/:id          - Eliminar post

GET    /users              - Obtener todos los usuarios
GET    /users/:id          - Obtener un usuario específico
GET    /users/:id/posts    - Obtener posts de un usuario

GET    /comments           - Obtener todos los comentarios
GET    /comments/:id       - Obtener un comentario específico
```

**Nota:**
- JSONPlaceholder es una API fake. Las operaciones POST/PUT/PATCH/DELETE no persisten datos realmente, pero devuelven respuestas correctas.
- Debes simular la persistencia en el frontend (state management + localStorage).

---

## 🛠️ Requisitos Técnicos

### 1. **Setup del Proyecto**

- **Vite** o **Next.js** (preferiblemente Vite para SPA)
- **React 18+** con TypeScript (o JavaScript si no manejas TS)
- **TailwindCSS** para estilos
- **ESLint** y **Prettier** configurados
- `.gitignore` apropiado
- `README.md` con instrucciones de instalación y ejecución

### 2. **Gestión de Estado**

Elegir e implementar UNA de las siguientes opciones:
- **Zustand** (recomendado por simplicidad)
- **Redux Toolkit**
- **Jotai**
- **Context API + useReducer** (bien estructurado)

**Requisitos:**
- Persistencia del estado en localStorage (posts, usuarios, sesión)
- Estado separado por dominio (auth, posts, users, comments, ui)
- Acciones tipadas (si usas TypeScript)
- Sincronización con API

### 3. **TypeScript (Preferido) o JavaScript**

**Si usas TypeScript:**
- ✅ Tipado estricto (`strict: true` en tsconfig)
- ✅ Interfaces para todas las entidades (Post, User, Comment, etc.)
- ✅ Props tipados en todos los componentes
- ✅ Evitar `any` (usar `unknown` si es necesario)
- ✅ Tipos genéricos donde aplique

**Si usas JavaScript:**
- ✅ PropTypes o documentación JSDoc donde sea posible
- ✅ Código limpio y bien documentado
- ⚠️ **Nota:** Usar JavaScript en lugar de TypeScript afectará la puntuación en la sección "Código y Arquitectura" (-4 puntos del total)

### 4. **Estilos con TailwindCSS**

- ✅ Configuración personalizada (colores, spacing, etc.)
- ✅ Componentes reutilizables con clases compuestas
- ✅ Uso de plugins (forms, typography, etc.) si es necesario
- ✅ Dark mode implementado
- ✅ Responsive design (mobile-first)
- ❌ No usar CSS modules o styled-components (solo Tailwind)

### 5. **Performance y Optimización**

Implementar al menos 5 de las siguientes técnicas:
- ✅ `React.memo` en componentes pesados
- ✅ `useMemo` y `useCallback` donde sea apropiado
- ✅ Lazy loading de componentes (`React.lazy`)
- ✅ Virtualización de listas largas (opcional, bonus)
- ✅ Debounce en búsqueda
- ✅ Optimistic updates en mutaciones
- ✅ Code splitting por rutas
- ✅ Imágenes optimizadas (lazy loading, placeholders si aplica)
- ✅ Cache de datos del API

### 6. **Testing**

**Requerimientos mínimos:**
- ✅ **Cobertura mínima: 70%**
- ✅ Tests unitarios con **Vitest** o **Jest**
- ✅ Tests de componentes con **React Testing Library**
- ✅ Al menos 3 tests de integración

**Qué testear:**
- Componentes críticos (PostCard, PostForm, PostList, UserCard)
- Custom hooks
- Utilidades y helpers (formatters, validators)
- Integración de formularios y validaciones
- Flujos de usuario principales

### 7. **Accesibilidad (a11y)**

- ✅ Navegación por teclado funcional
- ✅ ARIA labels apropiados
- ✅ Contraste de colores (WCAG AA)
- ✅ Focus visible
- ✅ Mensajes de error asociados a inputs (aria-describedby)
- ✅ Roles semánticos apropiados

### 8. **Seguridad**

- ✅ Sanitización de inputs
- ✅ Protección contra XSS
- ✅ Validación en cliente
- ✅ No exponer tokens en URLs
- ✅ Headers de seguridad apropiados (si usas Next.js)

### 9. **Git y Versionamiento**

- ✅ Commits atómicos y descriptivos
- ✅ Conventional Commits (feat:, fix:, refactor:, etc.)
- ✅ Branch principal: `main` o `master`
- ✅ `.gitignore` apropiado
- ✅ No commitear `node_modules`, `.env`, etc.

---

## 🎁 Features Bonus (Opcionales)

Estos features NO son obligatorios pero suman puntos extra:

1. **Animaciones y Transiciones** (+5 puntos)
   - Framer Motion o TailwindCSS animations
   - Transiciones suaves entre vistas
   - Animaciones en hover/interactions

2. **PWA (Progressive Web App)** (+10 puntos)
   - Funciona offline
   - Installable
   - Service worker configurado

3. **Internacionalización (i18n)** (+8 puntos)
   - Soporte para español e inglés
   - Cambio de idioma dinámico

4. **Tests E2E** (+10 puntos)
   - Cypress o Playwright
   - Al menos 2 flujos completos

5. **Virtualización de Listas** (+7 puntos)
   - react-window o similar
   - Optimización para 1000+ posts

6. **Vista de Álbumes y Fotos** (+8 puntos)
   - Integrar endpoints de /albums y /photos
   - Gallery view con lightbox

7. **Exportar Posts** (+5 puntos)
   - Exportar a JSON, CSV o Markdown

8. **Modo Offline** (+10 puntos)
   - Funcionalidad básica sin conexión
   - Sync cuando recupera conexión
   - Service Worker + IndexedDB

9. **Búsqueda Avanzada** (+6 puntos)
   - Búsqueda por múltiples campos
   - Filtros avanzados
   - Operadores lógicos

10. **Storybook** (+7 puntos)
    - Documentación de componentes
    - Al menos 5 stories

**Puntuación máxima bonus:** 75 puntos adicionales

---

## 📤 Entrega

### Qué entregar:

1. **Repositorio de GitHub/GitLab**
   - Código fuente completo
   - README.md con instrucciones claras
   - Commits descriptivos

2. **Aplicación Desplegada**
   - Vercel, Netlify, o similar
   - URL funcional y accesible

3. **Documentación** (en README.md)
   - Instrucciones de instalación
   - Instrucciones para correr el proyecto
   - Instrucciones para correr tests
   - Decisiones técnicas importantes
   - Features implementados y no implementados
   - Tiempo invertido aproximado por sección

4. **Video Demo** (opcional pero recomendado)
   - 3-5 minutos mostrando la aplicación
   - Loom, YouTube, o similar

### Tu README debe incluir:
- Link a la aplicación desplegada
- Instrucciones de instalación y ejecución
- Cómo correr los tests
- Stack técnico utilizado
- Features implementados (y no implementados con razón)
- Decisiones técnicas importantes
- Tiempo invertido aproximado

---

## ⚖️ Criterios de Evaluación

Ver archivo [`TECH_REQUIREMENTS.md`](./TECH_REQUIREMENTS.md) para especificaciones técnicas detalladas.

**Distribución general:**
- Funcionalidad: 30%
- Código y Arquitectura: 25%
- UI/UX y Diseño: 15%
- Testing: 15%
- Performance: 10%
- Documentación: 5%

**Puntuación mínima para aprobar:** 70/100

---

## 📚 Recursos Recomendados

- [React Docs (oficial)](https://react.dev/)
- [TailwindCSS Docs](https://tailwindcss.com/docs)
- [TypeScript Handbook](https://www.typescriptlang.org/docs/)
- [React Testing Library](https://testing-library.com/react)
- [Vitest](https://vitest.dev/)
- [JSONPlaceholder Guide](https://jsonplaceholder.typicode.com/guide/)

---

## ❓ FAQ

**¿Es obligatorio usar TypeScript?**
No es obligatorio, pero es altamente recomendado. Puedes usar JavaScript si no tienes experiencia con TypeScript, pero esto afectará tu puntuación (-4 puntos). Ver [FAQ.md](./FAQ.md) para más detalles.

**¿Puedo usar librerías adicionales?**
Sí, pero justifica su uso. Evita librerías que hagan todo el trabajo por ti.

**¿Qué hago si no termino todas las features?**
Prioriza las funcionalidades core. Es mejor tener menos features bien implementadas que muchas a medias.

**¿Cómo manejo que el API no persiste cambios?**
Debes simular la persistencia en el frontend usando state management + localStorage. Los cambios deben persistir durante la sesión del usuario.

**¿Puedo modificar el diseño?**
Sí, eres libre de diseñar como prefieras siempre que cumpla los requisitos funcionales.

**¿Qué navegadores debo soportar?**
Chrome, Firefox, Safari y Edge (últimas 2 versiones).

---

## 📞 Contacto

Si tienes dudas técnicas o ambigüedades en los requisitos, no dudes en contactarnos.

**¡Mucha suerte! 🚀**

---

**Última actualización:** Noviembre 2025
