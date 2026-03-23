# 🌱 GreenTech Landing — Refactorización Técnica

## 1. Contexto

Refactorización de una landing estática con objetivo de **reducir peso, eliminar dependencias y mejorar rendimiento** manteniendo paridad visual.

---

## 2. Stack (Antes vs Después)

### Antes

* Bootstrap 5 (CSS + JS)
* jQuery
* Moment.js
* Font Awesome

### Después

* HTML5 semántico
* CSS nativo (custom properties)
* JavaScript vanilla (ES6+)

---

## 3. Decisiones Técnicas

### 3.1 Eliminación de dependencias

**Motivo:** evitar coste de red, parsing y ejecución innecesaria.

| Dependencia  | Motivo eliminación          | Sustitución     |
| ------------ | --------------------------- | --------------- |
| Bootstrap    | Overkill para layout simple | CSS nativo      |
| jQuery       | API DOM moderna suficiente  | `querySelector` |
| Moment.js    | Uso trivial (año actual)    | `Date()`        |
| Font Awesome | 1 icono únicamente          | Emoji           |

---

### 3.2 CSS

* Uso de `:root` para variables
* Tipografía fluida con `clamp()`
* Layout basado en Flexbox
* Eliminación de clases utilitarias redundantes

**Objetivo:** reducir CSS footprint y mejorar legibilidad.

---

### 3.3 Imagen (Hero)

* Reducción de resolución (`w=1200`)
* `object-fit: cover`
* Lazy loading:

```html
loading="lazy"
decoding="async"
```

**Impacto:** mejora en LCP y reducción de transferencia inicial.

---

### 3.4 JavaScript

JS reducido a una única responsabilidad:

```js
new Date().getFullYear()
```

* Sin dependencias
* Sin manipulación compleja del DOM

---

### 3.5 Fuentes

* Reducción de pesos:

  * Antes: 100–900
  * Después: 400, 700

**Impacto:** menos requests + menor blocking render.

---

## 4. Performance

### Mejoras clave

* ↓ Requests HTTP
* ↓ JS bundle (eliminado completamente)
* ↓ CSS total
* ↓ Tiempo de render inicial

### Métricas esperadas

* Mejor LCP
* Mejor FCP
* Mejor TTI

---

## 5. Estructura Final

```
index.html
 ├── <head>
 │    ├── meta
 │    ├── font (optimizada)
 │    └── CSS inline
 │
 ├── <body>
 │    ├── hero (imagen + contenido)
 │    └── footer dinámico
 │
 └── script mínimo
```

---

## 6. Trade-offs

| Decisión           | Beneficio     | Coste                   |
| ------------------ | ------------- | ----------------------- |
| Sin framework      | Rendimiento   | Menos abstracción       |
| CSS manual         | Control total | Más responsabilidad dev |
| Emoji vs icon font | 0 requests    | Menos personalización   |

---

## 7. Posibles Iteraciones

### Corto plazo

* WebP + `srcset`
* Preload de fuente
* Critical CSS extraction

### Medio plazo

* Intersection Observer (animaciones)
* Dark mode (prefers-color-scheme)

### Largo plazo

* PWA (service worker)
* SSR/SSG si escala

---

## 8. Conclusión

Se ha pasado de una arquitectura dependiente de librerías a una solución **lean, performante y mantenible**, alineada con buenas prácticas modernas (Core Web Vitals, reducción de JS, CSS eficiente).

---

**Maintainer:** GreenTech Frontend Team
**Año:** 2026
