# Plan nutricional – sitio estático

## Qué es esto

Un sitio de una sola página que sirve como plan de alimentación personal, consultado desde el celular y desde la laptop. No es un producto, no tiene usuarios, no lleva analítica. Se publica en GitHub Pages.

El contenido vive en `content/`. La fuente de verdad de los datos es `content/nutricion.md`; el porqué de cada decisión está en `content/contexto.md`.

## Qué construir

Un `index.html` autocontenido: HTML, CSS y JS en el mismo archivo. Sin build step, sin framework, sin dependencias que se instalen. Fuentes desde Google Fonts si hacen falta.

La razón de ser autocontenido es que GitHub Pages sirve el archivo tal cual y el sitio tiene que funcionar también abierto desde el disco, sin servidor.

### Secciones

1. **Día al azar** – botón que arma una combinación (un almuerzo, una merienda, una cena) mostrando ingredientes, gramos y el total de macros del día. Estado solo en memoria, sin `localStorage` ni persistencia de ningún tipo. Debe respetar la restricción de combinación descrita en `nutricion.md`.
2. **Almuerzo** – 6 opciones
3. **Merienda** – 4 opciones
4. **Cena** – 3 opciones
5. **Intercambios** – tablas de reemplazo directo
6. **Cómo usarlo** – reglas de uso, horarios, registro

Cada opción de comida muestra: nombre, lista de ingredientes con gramos, y sus macros (kcal, proteína, carbohidrato, grasa).

### Requisitos técnicos

- **Mobile primero.** El uso principal es el celular, de pie en la cocina o antes de salir. Legibilidad por encima de densidad.
- **Instalable como acceso directo:** incluir `manifest.json`, `theme-color`, `apple-mobile-web-app-capable` y un ícono, para que "Agregar a pantalla de inicio" abra sin barra del navegador.
- Navegación por pestañas o anclas, con la sección activa siempre visible.
- Accesible: foco visible por teclado, contraste suficiente, `prefers-reduced-motion` respetado, roles correctos en las pestañas.
- Sin dependencias externas más allá de las fuentes.

## Dirección de diseño

Usa la skill de diseño frontend. Antes de escribir código, define paleta, tipografías y un elemento distintivo, y valida que no sea el default genérico.

Restricciones concretas para este proyecto:

- **Evita los tres clichés de IA**: fondo crema con serif de alto contraste y acento terracota; fondo casi negro con un acento verde ácido o bermellón; y el layout tipo periódico con filetes finos y radio cero.
- Las cantidades en gramos son el dato que más se lee. Una face monoespaciada para números y unidades ayuda de verdad, no es decoración.
- Nada de ilustraciones de comida, iconos de manzanitas ni fotos de stock. El contenido es una tabla de gramos, no una revista de recetas.
- El tono es de instrumento, no de app de bienestar. Sin frases motivacionales, sin emojis, sin barras de progreso hacia una meta de peso.

## Lo que NO va en el sitio

- **Nada de la rutina de entrenamiento.** Los horarios de entreno solo aparecen como referencia de a qué hora toca cada comida. Los ejercicios, cargas y lesiones quedan fuera de este repo por ahora.
- Nada de seguimiento de peso, medidas corporales ni historial de progreso. Eso vive en una hoja de cálculo aparte.
- Sin login, sin backend, sin base de datos.

## Privacidad

El repo es público si se usa GitHub Pages en plan gratuito. No incluir en el sitio ni en el código: peso, medidas corporales, historial médico, nombre completo ni datos de contacto. Los datos en `content/` ya están filtrados con ese criterio – mantenlo así al editarlos.

Si en algún momento hace falta publicar métricas personales, migrar a Cloudflare Pages con Access, que permite proteger el sitio en el plan gratuito.

## Deploy

GitHub Pages sirve desde la raíz. `index.html` en la raíz del repo, rama principal.

## Al iterar

Los cambios de contenido (una receta nueva, un ajuste de gramos) se hacen primero en `content/nutricion.md` y después se reflejan en `index.html`. Los dos deben quedar consistentes.
