# Preguntas Frecuentes (FAQ)

Clarificaciones sobre requisitos y logística de la prueba técnica.

---

## 🌟 General

### ¿Cuánto tiempo tengo para completar el test?
**48 horas** desde el momento en que recibes la prueba.

### ¿Puedo entregar antes de las 48 horas?
Sí, puedes entregar en cualquier momento dentro del plazo.

### ¿Qué pasa si no termino todas las features?
Entrega lo que tengas. Documenta en el README qué no alcanzaste a completar y por qué. Es mejor tener pocas features completas que muchas a medias.

### ¿Puedo hacer preguntas durante el test?
Sí, puedes hacer preguntas de clarificación sobre requisitos ambiguos.

### ¿Puedo usar código de proyectos anteriores?
Sí, puedes reutilizar código propio, pero debe estar bien integrado al proyecto.

### ¿Puedo buscar en internet y usar Stack Overflow?
Absolutamente. Buscar información es parte del trabajo real de un desarrollador.

### ¿Puedo utilizar AI?
Sí, pero debes tener un entendimiento completo de lo realizado y poder defenderlo.

---

## 🛠️ Tecnologías y Herramientas

### ¿Es obligatorio usar TypeScript?
No es obligatorio, pero es **altamente recomendado**. Puedes usar JavaScript si no tienes experiencia con TypeScript, pero esto afectará tu puntuación (-4 puntos en la sección de Código y Arquitectura). TypeScript demuestra mejores prácticas y es estándar en la industria.

### ¿Es obligatorio usar Vite?
No. Puedes usar Vite, Create React App, o Next.js.

### ¿Puedo usar librerías de componentes UI como Material-UI, Ant Design o Chakra UI?
**No se recomienda**. El objetivo es evaluar tus habilidades con TailwindCSS. Puedes usar librerías headless (Headless UI, Radix UI) para accesibilidad.

### ¿Qué gestor de estado debo usar?
Puedes elegir: Zustand, Redux Toolkit, Jotai, o Context API + useReducer.

### ¿Puedo usar librerías para formularios como React Hook Form o Formik?
Sí.

### ¿Puedo usar librerías de drag & drop?
Sí, son recomendadas (react-beautiful-dnd, @dnd-kit/core, etc.).

### ¿Puedo usar Axios en lugar de fetch?
Sí.

### ¿Puedo usar librerías de iconos?
Sí (React Icons, Heroicons, etc.).

### ¿Debo usar Storybook?
No es obligatorio, pero suma puntos bonus.

---

## 🎯 Funcionalidades

### ¿Debo implementar un backend real para autenticación?
No. Debes simular la autenticación validando contra los usuarios del API de JSONPlaceholder. Por ejemplo, permitir login con cualquier email de los usuarios del API y una contraseña simulada.

### ¿Cómo manejo que el API de JSONPlaceholder no persiste cambios?
El API devuelve respuestas correctas pero no persiste datos. Debes:
1. Implementar persistencia en el frontend usando state management
2. Guardar cambios en localStorage
3. Al crear/editar/eliminar posts, actualizar tu estado local
4. Los cambios deben persistir durante la sesión del usuario

### ¿Los filtros deben funcionar con AND u OR?
**AND lógico**. Si el usuario filtra por múltiples criterios, debe mostrar solo items que cumplan todos los criterios simultáneamente.

### ¿La paginación debe ser del lado del cliente o servidor?
JSONPlaceholder devuelve todos los datos de una vez. Implementa la paginación en el cliente dividiendo el array de resultados.

### ¿Qué significa "optimistic updates"?
Actualizar la UI inmediatamente antes de que el API responda. Si el request falla, revertir el cambio. Ejemplo: al crear un post, mostrarlo inmediatamente en la lista.

### ¿Qué es "debounce en búsqueda"?
La búsqueda no debe ejecutarse en cada keystroke, sino después de que el usuario deje de escribir por ~300ms.

### ¿Cómo simulo las fechas si el API no las incluye?
Puedes usar el ID del post como referencia (posts con ID mayor = más recientes), o generar timestamps localmente cuando creas posts.

---

## 🧪 Testing

### ¿Qué herramienta de testing debo usar?
Vitest (recomendado) o Jest. Para componentes, usa React Testing Library.

### ¿Debo mockear las llamadas al API?
Sí, en tests unitarios y de integración.

### ¿Qué son tests E2E y debo implementarlos?
Tests End-to-End con herramientas como Cypress o Playwright. Son **opcionales** (bonus).

---

## 🚀 Deployment

### ¿Dónde debo desplegar la aplicación?
Opciones gratuitas: Vercel (recomendado), Netlify, GitHub Pages, Railway, o Render.

### ¿Qué hago si mi deploy falla?
Revisa los logs de deployment. Si no puedes resolver, incluye un video mostrando la app funcionando localmente.

---

## 📊 Evaluación

### ¿Qué es lo más importante en la evaluación?
En orden: (1) Funcionalidad, (2) Código limpio, (3) Testing, (4) UI/UX, (5) Performance.

### ¿Penalizan los errores en consola?
Sí. Errores críticos restan 2 puntos cada uno (máximo -10). Warnings menores no penalizan tanto.

### ¿Se evalúa el diseño visual?
Se evalúa principalmente usabilidad, responsive design, y consistencia. No necesitas ser diseñador.

### ¿Puedo copiar código de internet?
Puedes consultar documentación y adaptar snippets, pero:
- ❌ NO copies proyectos completos
- ❌ NO uses generadores de código para todo
- **El plagio resulta en descalificación**

### ¿Se evalúan los commits?
Sí, pero con poco peso (1-2 puntos). Commits descriptivos demuestran profesionalismo.

### ¿Importa cuánto tiempo me tomó?
No directamente, pero mencionar el tiempo invertido en el README ayuda a contextualizar el alcance.

---

## ⏰ Tiempo y Organización

### ¿Qué features priorizar si me quedo sin tiempo?

**Must-have (obligatorios):**
- Autenticación funcional
- CRUD completo de tareas
- Búsqueda y filtros básicos
- Una vista funcional (Kanban O Lista)
- Responsive design
- Tests básicos (60-70% cobertura)

**Should-have:**
- Drag & Drop
- Undo/Redo
- Dark mode
- Buena cobertura de tests (70%+)

**Nice-to-have (bonus):**
- Animaciones, PWA, features adicionales

### ¿Debo trabajar las 48 horas seguidas?
No. Descansa adecuadamente. Calidad > cantidad de horas.

---

## 🐛 Troubleshooting

### TailwindCSS no está aplicando estilos
Verifica:
1. `tailwind.config.js` tiene los paths correctos
2. Importaste las directivas `@tailwind` en tu CSS
3. El servidor de desarrollo está corriendo

### Los tests fallan con error de imports
Revisa tu configuración de Vitest/Jest y asegúrate de tener el environment correcto (`jsdom`).

### CORS error al llamar el API
El API debe tener CORS habilitado. Si no:
1. Usa un proxy
2. Usa datos mockeados
3. Documenta el problema

---

## 📞 ¿Aún tienes dudas?

Si tu pregunta no está aquí:
1. Revisa el [README.md](./README.md)
2. Revisa [TECH_REQUIREMENTS.md](./TECH_REQUIREMENTS.md)
3. Revisa [EVALUATION_CRITERIA.md](./EVALUATION_CRITERIA.md)
4. Contacta a [email de contacto]

**¡Buena suerte! 🚀**

---

**Última actualización:** Noviembre 2024
