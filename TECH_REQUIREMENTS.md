# Requisitos Técnicos Detallados

Especificaciones técnicas y requisitos del sistema para el test de Mid Frontend Developer.

---

## 🖥️ Requisitos del Sistema

### Ambiente de Desarrollo
- **Node.js:** >= 18.0.0
- **npm:** >= 9.0.0 o **yarn:** >= 1.22.0

### Navegadores Soportados

| Navegador | Versión Mínima |
|-----------|----------------|
| Chrome | Últimas 2 versiones |
| Firefox | Últimas 2 versiones |
| Safari | Últimas 2 versiones |
| Edge | Últimas 2 versiones |

### Breakpoints Responsive

- **Desktop:** >= 1024px
- **Tablet:** 768px - 1023px
- **Mobile:** 320px - 767px

---

## 📊 Estructura de Datos

**Nota:** Los ejemplos están en TypeScript. Si usas JavaScript, adapta según necesites (usando PropTypes o JSDoc).

### Post Interface

```typescript
interface Post {
  userId: number;
  id: number;
  title: string;
  body: string;
}
```

### Comment Interface

```typescript
interface Comment {
  postId: number;
  id: number;
  name: string;
  email: string;
  body: string;
}
```

### User Interface

```typescript
interface User {
  id: number;
  name: string;
  username: string;
  email: string;
  address: {
    street: string;
    suite: string;
    city: string;
    zipcode: string;
    geo: {
      lat: string;
      lng: string;
    };
  };
  phone: string;
  website: string;
  company: {
    name: string;
    catchPhrase: string;
    bs: string;
  };
}
```

### Auth State (Frontend)

```typescript
interface AuthState {
  user: User | null;
  isAuthenticated: boolean;
  isLoading: boolean;
  error: string | null;
}
```

---

## 🔌 API Endpoints

**Base URL:** `https://jsonplaceholder.typicode.com`
**Documentación completa:** `https://jsonplaceholder.typicode.com/guide/`

### Posts

```
GET    /posts              Lista todos los posts (100 posts)
GET    /posts/:id          Obtiene un post específico
GET    /posts/:id/comments Obtiene comentarios de un post
POST   /posts              Crea un nuevo post
PUT    /posts/:id          Actualiza un post (reemplazar completo)
PATCH  /posts/:id          Actualiza un post (parcial)
DELETE /posts/:id          Elimina un post
```

### Comments

```
GET    /comments           Lista todos los comentarios (500 comments)
GET    /comments/:id       Obtiene un comentario específico
GET    /comments?postId=1  Filtra comentarios por postId
POST   /comments           Crea un nuevo comentario
```

### Users

```
GET    /users              Lista todos los usuarios (10 users)
GET    /users/:id          Obtiene un usuario específico
GET    /users/:id/posts    Obtiene posts de un usuario
```

### Importante sobre el API

- **JSONPlaceholder es una API fake:** Las operaciones POST/PUT/PATCH/DELETE no persisten datos realmente
- El API devuelve respuestas correctas simuladas
- **Debes implementar persistencia en el frontend** usando state management + localStorage
- El API soporta todos los métodos HTTP estándar

---

## ✅ Reglas de Validación

### Título de Post
- **Requerido:** Sí
- **Min length:** 10 caracteres
- **Max length:** 200 caracteres
- **Restricción:** No puede iniciar ni terminar con espacios

### Cuerpo de Post
- **Requerido:** Sí
- **Min length:** 50 caracteres
- **Max length:** 1000 caracteres

### Email (Login y Comentarios)
- **Requerido:** Sí
- **Validación:** Formato de email válido

### Password (Login)
- **Requerido:** Sí
- **Min length:** 8 caracteres

---

## ⚡ Performance Targets

### Métricas Core Web Vitals

| Métrica | Target | Max Aceptable |
|---------|--------|---------------|
| First Contentful Paint (FCP) | < 1.5s | < 2.5s |
| Largest Contentful Paint (LCP) | < 2.5s | < 4s |
| Time to Interactive (TTI) | < 3s | < 5s |
| Total Blocking Time (TBT) | < 200ms | < 600ms |
| Cumulative Layout Shift (CLS) | < 0.1 | < 0.25 |

### Bundle Size
- **Initial bundle:** < 500KB (gzipped)
- **Total JavaScript:** < 1MB

---

## 🧪 Testing Requirements

### Cobertura Mínima

```
Statements   : 70%
Branches     : 65%
Functions    : 70%
Lines        : 70%
```

### Tipos de Tests Requeridos
- Tests unitarios de componentes (PostCard, PostForm, PostList, UserCard, etc.)
- Tests de custom hooks
- Tests de funciones utilitarias (validators, formatters, etc.)
- Al menos 3 tests de integración (flujo completo de usuario)

---

## 🔒 Seguridad

### Requisitos Mínimos
- Validación y sanitización de inputs
- Protección contra XSS
- Tokens/sesión no expuestos en URLs
- Sin vulnerabilidades críticas en dependencias (`npm audit`)

---

## 🌐 Compatibilidad

### JavaScript Features Permitidos
ES2020+ incluyendo:
- Optional chaining (`?.`)
- Nullish coalescing (`??`)
- Dynamic import
- Promise.allSettled
- Async/await

### CSS Features Permitidos
- CSS Grid
- Flexbox
- CSS Variables
- Modern layout features

---

## 📦 Stack Tecnológico Requerido

### Obligatorios
- React 18+
- TypeScript (strict mode) o JavaScript (con penalización de -4 puntos)
- TailwindCSS 3+
- Gestor de estado (Zustand, Redux Toolkit, Jotai, o Context API)
- Testing: Vitest o Jest + React Testing Library

### Configuración Requerida
- ESLint configurado
- Prettier configurado
- TypeScript en modo strict (si usas TS)
- `.gitignore` apropiado

---

## 💾 Persistencia de Datos

Como el API de JSONPlaceholder no persiste datos, debes:

1. **Guardar en state management:**
   - Posts creados/editados/eliminados
   - Comentarios agregados
   - Sesión del usuario

2. **Sincronizar con localStorage:**
   - Persistir cambios entre reloads
   - Mantener sincronización con datos del API

3. **Estrategia recomendada:**
   ```
   1. Al iniciar: Fetch datos del API → merge con localStorage
   2. Al modificar: Actualizar state → guardar en localStorage
   3. Al reload: Cargar de localStorage → opcionalmente refrescar del API
   ```

---

## 🎨 Sugerencias de UI

Estos son solo sugerencias para mantener consistencia visual:

**Colores para estados:**
- Post del usuario actual: Azul/destacado
- Post de otros: Neutral
- Error: Rojo
- Success: Verde

**Indicadores visuales:**
- Badge de cantidad de comentarios
- Avatar/inicial del autor
- Timestamp simulado (usar ID como referencia)

---

## ❓ Notas Importantes

- El candidato es libre de elegir la arquitectura de carpetas
- El candidato es libre de elegir librerías adicionales (justificando su uso)
- La autenticación debe ser simulada (validar contra usuarios del API)
- Los cambios deben persistir en la sesión del usuario

---

## 📚 Recursos del API

- **API Base:** https://jsonplaceholder.typicode.com
- **Guía completa:** https://jsonplaceholder.typicode.com/guide/
- **Posts de ejemplo:** https://jsonplaceholder.typicode.com/posts
- **Users de ejemplo:** https://jsonplaceholder.typicode.com/users
- **Comments de ejemplo:** https://jsonplaceholder.typicode.com/comments

---

**Para más información, consulta:**
- [README.md](./README.md) - Requisitos principales
- [FAQ.md](./FAQ.md) - Preguntas frecuentes
