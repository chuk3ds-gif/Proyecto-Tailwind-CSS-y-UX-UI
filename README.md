# DevX

Portafolio personal de un estudiante de Ingeniería de Software, desarrollado con **HTML5**, **Tailwind CSS 4** y **JavaScript puro**, con apoyo de inteligencia artificial y revisado a mano.

- **Sitio publicado:** https://github.com/chuk3ds-gif/Proyecto-Tailwind-CSS-y-UX-UI 
- **Video:** https://youtu.be/kgbE75Qn-nY

![Vista del sitio en computador](documentacion/capturas/computador-oscuro.png)

## Características
- Diseño **mobile-first** y responsive (prefijos `sm`, `md` y `lg`).
- Distribución: hero con imagen y datos rápidos, intereses en mosaico, habilidades en filas, proyecto destacado a todo el ancho, y preguntas y contacto en dos columnas.
- Navbar fija con enlaces en forma de píldora y **menú hamburguesa** (se cierra con un enlace o con Escape).
- **Modo oscuro / claro** con botón; la preferencia se guarda en el navegador.
- Paleta propia con `@theme` y **regla 60-30-10**: `#0E0B1F` (60 %), `#1C1836` (30 %), `#A3E635` (10 %), más éxito `#22C55E`, error `#EF4444` y advertencia `#F59E0B`.
- Dos fuentes: Space Grotesk (títulos) e Inter (texto).
- **Formulario** con validación (obligatorios, correo válido, mínimo 20 caracteres), errores debajo de cada campo y **toast** de confirmación de 4 segundos. Es una demostración: no envía correos.
- Componentes extra: **acordeón** de preguntas frecuentes y **filtro** de proyectos.
- Accesibilidad: textos alternativos, etiquetas, contraste ≥ 4.5:1 en ambos modos, foco visible, enlace "Saltar al contenido" y `prefers-reduced-motion`.

## Tecnologías
| Tecnología | Uso |
|---|---|
| HTML5 | Estructura semántica (`header`, `nav`, `main`, `section`, `article`, `footer`) |
| Tailwind CSS 4 + Tailwind CLI | Estilos utilitarios y tema propio con `@theme` |
| JavaScript (sin librerías) | Menú, tema, acordeón, filtro, validación y toast |
| Claude (IA) | Generación de la versión inicial y ajustes (ver bitácora) |

## Estructura
```
DevX-Portfolio/
├── index.html            # Página única
├── src/input.css         # Entrada de Tailwind: @import, @theme, modo oscuro
├── dist/output.css       # CSS compilado (se publica; no lo edite a mano)
├── js/script.js          # Interacciones
├── assets/images/        # Ilustraciones SVG propias y favicon
├── documentacion/        # Prompt maestro, bitácora, pruebas, cambios manuales, auditoría, capturas
├── pruebas/              # Scripts de pruebas automáticas (Playwright)
└── package.json
```

## Instalación y ejecución
Requisitos: [Node.js](https://nodejs.org) 20 o superior.

```bash
npm install          # instala tailwindcss y @tailwindcss/cli
npm run dev          # recompila el CSS cada vez que guarda un archivo
npm run build        # genera dist/output.css minificado para publicar
```
Abra `index.html` en el navegador (o use la extensión *Live Server* de VS Code).

> **Importante:** si agrega clases nuevas en el HTML o el JS, ejecute `npm run build` antes de subir los cambios; si no, esas clases no tendrán estilo en el sitio publicado.

## Publicación en GitHub Pages
1. Cree un repositorio **público** llamado `DevX-Portfolio` y suba todo el contenido de esta carpeta (incluida `dist/`).
2. En GitHub: **Settings → Pages → Source: Deploy from a branch → Branch: `main` / `(root)` → Save**.
3. Espere 1–2 minutos y abra `https://TU-USUARIO.github.io/DevX-Portfolio/`. Pruébelo también desde el celular.

Todas las rutas son relativas (`dist/output.css`, `js/script.js`, `assets/...`), así que funcionan dentro de la subcarpeta de GitHub Pages. El archivo `.nojekyll` evita que GitHub procese el sitio con Jekyll.

## Prompt maestro
> Versión resumida del prompt que generó la versión 1 del sitio. Revísela y **reescríbala con sus palabras** antes de mostrarla en el video: la guía pide que el prompt sea de autoría propia.

#### 1. Rol
Actúa como desarrollador frontend senior especializado en HTML5 semántico, Tailwind CSS 4, JavaScript puro, diseño responsive y accesibilidad web (WCAG 2.2).

#### 2. Contexto
Voy a crear **DevX**, el portafolio personal de un estudiante de Ingeniería de Software. Está dirigido a reclutadores tecnológicos, desarrolladores y estudiantes de programación. Su objetivo es presentar mi perfil académico, mis habilidades, mis proyectos (web y videojuegos) y recibir mensajes de contacto. El estilo debe ser moderno, tecnológico y minimalista, sin abusar de sombras, degradados ni animaciones.

#### 3. Tareas
Construye una página única con estas secciones, en este orden:
1. Navbar fija con el logo "DevX" en texto, enlaces a cada sección y botón "Contacto". En celular se convierte en menú hamburguesa que abre y cierra con JavaScript, se cierra al elegir un enlace o al pulsar Escape y actualiza `aria-expanded`.
2. Botón para cambiar entre modo claro y oscuro con la variante `dark:`; el modo oscuro es el predeterminado y la elección se guarda en `localStorage`.
3. Hero con título H1, descripción breve, ilustración de avatar y dos botones: "Ver proyectos" y "Escríbeme".
4. Sección "Sobre mí" con perfil académico e intereses (incluido el desarrollo de videojuegos), marcada como contenido demostrativo.
5. Sección de habilidades en tres tarjetas: Frontend, Backend y datos, Herramientas y videojuegos.
6. Proyectos en tarjetas (imagen, categoría, título, descripción, tecnologías y enlace) con un grid de 1 columna en celular y más columnas en pantallas grandes, efecto hover y un filtro por categoría (Todos, Web, Videojuegos).
7. Preguntas frecuentes en acordeón de 4 preguntas, accesible con teclado.
8. Formulario de contacto con nombre, correo, asunto y mensaje. Valida con JavaScript los campos obligatorios, el formato del correo y un mínimo de 20 caracteres en el mensaje; muestra el error en rojo debajo de cada campo y, al enviar bien, un toast verde que desaparece a los 4 segundos. No simules el envío de correos: no hay servidor.
9. Footer con derechos, enlaces a redes y "Volver arriba".

#### 4. Restricciones
- Solo HTML, Tailwind CSS 4 compilado con **Tailwind CLI** (`@import "tailwindcss"`, sin `tailwind.config.js`) y JavaScript puro, sin Bootstrap ni otras librerías.
- Paleta con `@theme` y regla 60-30-10: fondo `#0E0B1F` índigo casi negro (60 %), superficie `#1C1836` violeta oscuro (30 %), acento `#A3E635` verde lima (10 %); éxito `#22C55E`, error `#EF4444`, advertencia `#F59E0B`. Define también los tokens del modo claro.
- Máximo dos fuentes de Google Fonts: Space Grotesk (títulos) e Inter (texto).
- Mobile-first, con los prefijos `sm`, `md` y `lg` como mínimo.
- Accesibilidad: `lang="es"`, un solo H1, textos alternativos, `<label>` en cada campo, contraste mínimo 4.5:1 en ambos modos, foco visible, enlace "Saltar al contenido" y soporte de `prefers-reduced-motion`.
- No inventes experiencia laboral ni certificaciones: usa contenido demostrativo y marca los campos editables con comentarios.
- Imágenes propias en SVG (sin bancos de imágenes con licencia dudosa).

#### 5. Formato de salida
Entrega los archivos `index.html`, `src/input.css`, `js/script.js` y las imágenes en `assets/images/`, con el código indentado y comentarios en español que separen cada sección. Al final explica cómo compilar (`npm run build`) y qué partes debo personalizar.

## Bitácora de prompts
| # | Prompt de ajuste enviado | Problema que buscaba resolver | Resultado obtenido | ¿Funcionó? |
|---|---|---|---|---|
| 1 | Prompt maestro completo (ver `prompt_maestro.md`) | Generar la versión 1 del sitio | Se crearon `index.html`, `src/input.css`, `js/script.js` y 6 imágenes SVG; 41 de 42 pruebas pasaron en la primera ejecución | Sí, con un fallo por revisar |
| 2 | "No se puede instalar Tailwind con npm en este entorno; compila con otra vía oficial sin cambiar el código" | `npm install` falló (sin acceso al registro de npm) | Se usó el ejecutable oficial *standalone* de Tailwind CLI v4.3.3 descargado de GitHub; `dist/output.css` se generó (27 KB) | Sí |
| 3 | "La prueba 'sin errores en consola' falla; identifica el recurso que no carga" | 1 prueba fallida: `Failed to load resource: net::ERR_FAILED` | La causa era el bloqueo de Google Fonts *dentro del entorno de pruebas*, no un error del sitio. Se ajustó la prueba para registrar la URL del recurso fallido e ignorar solo las fuentes bloqueadas | Sí (42/42) |
| 4 | "Con 4 proyectos y 3 columnas queda una tarjeta sola en la última fila del escritorio; corrige el grid" | Tarjeta huérfana en la fila final a 1280 px (visible en la captura) | El grid pasó de `md:grid-cols-2 lg:grid-cols-3` a `md:grid-cols-2 xl:grid-cols-4` | Sí |
| 5 | "Si se pulsa 'Enviar' varias veces se apilan varios toasts; muestra solo uno" | 4 clics seguidos dejaban 4 toasts en pantalla | Se añadió `contenedorToasts.replaceChildren()` al inicio de `mostrarToast()` | Sí |
| 6 | "Cambia el nombre del sitio a DevX, usa otra paleta (manteniendo la regla 60-30-10 y el contraste) y cambia la distribución de las secciones" | Darle al sitio una identidad propia y distinta | Nombre DevX; paleta índigo `#0E0B1F` / violeta `#1C1836` / lima `#A3E635` (antes azul marino, azul grisáceo y cian); hero con imagen a la izquierda y datos rápidos; intereses en mosaico; habilidades en filas; proyecto destacado a todo el ancho + 3 tarjetas; FAQ y contacto en dos columnas. La tarjeta destacada también resolvió la fila incompleta de la iteración 4 | Sí (45/45) |
| 7 | [Su prompt] | | | |
| 8 | [Su prompt] | | | |

Detalle completo de cada iteración: [`documentacion/bitacora_prompts.md`](documentacion/bitacora_prompts.md).

## Cambios manuales
Tres cambios hechos sin IA: ver [`documentacion/cambios_manuales.md`](documentacion/cambios_manuales.md).

## Pruebas
45/45 pruebas funcionales, HTML sin errores en el validador del W3C y contraste verificado en ambos modos. Detalle en [`documentacion/pruebas.md`](documentacion/pruebas.md). Puntaje de Lighthouse: **___** (complete).

## Créditos
- Ilustraciones SVG creadas para este proyecto.
- Fuentes: [Inter](https://fonts.google.com/specimen/Inter) y [Space Grotesk](https://fonts.google.com/specimen/Space+Grotesk) (SIL Open Font License).
- Desarrollado con apoyo de Claude (Anthropic); todo el código fue revisado y probado.

**Autor:** Tu Nombre · [Programa] · [Universidad] · 2026
