# Guía para editar el sitio de Lesly Suarez

Sitio publicado: **https://leslysuarez.github.io**
Repositorio: **https://github.com/leslysuarez/leslysuarez.github.io**

Todo se edita **desde el navegador, en github.com**. No hace falta instalar nada ni guardar archivos en el computador.

---

## Índice

1. [Cómo funciona el sitio](#1-cómo-funciona-el-sitio)
2. [Cómo editar cualquier archivo (paso a paso)](#2-cómo-editar-cualquier-archivo-paso-a-paso)
3. [Cambiar los textos de una página](#3-cambiar-los-textos-de-una-página)
4. [Agregar una charla](#4-agregar-una-charla)
5. [Agregar un curso o seminario](#5-agregar-un-curso-o-seminario)
6. [Agregar un evento organizado](#6-agregar-un-evento-organizado)
7. [Subir PDFs (apuntes, slides, CV)](#7-subir-pdfs-apuntes-slides-cv)
8. [Agregar una sección nueva al sitio](#8-agregar-una-sección-nueva-al-sitio)
9. [Cambiar el menú superior](#9-cambiar-el-menú-superior)
10. [Cambiar los colores](#10-cambiar-los-colores)
11. [Cambiar la fuente (tipografía)](#11-cambiar-la-fuente-tipografía)
12. [Cambiar la barra lateral (nombre, foto, enlaces)](#12-cambiar-la-barra-lateral-nombre-foto-enlaces)
13. [Si algo se rompe](#13-si-algo-se-rompe)
14. [Configuración inicial (se hace una sola vez)](#14-configuración-inicial-se-hace-una-sola-vez)
15. [Notas sobre el traslado desde Google Sites](#15-notas-sobre-el-traslado-desde-google-sites)

---

## 1. Cómo funciona el sitio

El sitio usa la plantilla **Academic Pages** (Jekyll). Cada vez que se guarda un cambio en el repositorio, GitHub reconstruye el sitio solo y lo publica en 1 a 3 minutos.

Dónde está cada cosa:

| Quiero cambiar…                         | Archivo o carpeta                        |
|-----------------------------------------|------------------------------------------|
| Página de inicio (About me)             | `_pages/about.md`                        |
| Overview                                | `_pages/overview.md`                     |
| Research / Projects                     | `_pages/research.md`                     |
| Organization of Events                  | `_pages/events.md`                       |
| Talks (una charla = un archivo)         | carpeta `_talks/`                        |
| Teaching (un curso = un archivo)        | carpeta `_teaching/`                     |
| My Notes                                | `_pages/my-notes.md`                     |
| Menú superior                           | `_data/navigation.yml`                   |
| Nombre, foto y enlaces de la barra lateral | `_config.yml` (sección `author:`)     |
| Colores                                 | `_sass/theme/_lesly_light.scss`          |
| Colores del modo oscuro                 | `_sass/theme/_lesly_dark.scss`           |
| Fuente                                  | `_includes/head/custom.html` y `_sass/_personalizado.scss` |
| Estilo (barra negra, bloques blancos, botones) | `_sass/_personalizado.scss`       |
| PDFs                                    | carpeta `files/`                         |
| Imágenes                                | carpeta `images/`                        |

> No es necesario tocar las carpetas `_layouts`, `_includes` (salvo `head/custom.html`), `assets` ni el resto de `_sass`.

---

## 2. Cómo editar cualquier archivo (paso a paso)

1. Entra a https://github.com/leslysuarez/leslysuarez.github.io con la cuenta **leslysuarez**.
2. Haz clic en la carpeta y luego en el archivo que quieres cambiar.
3. Haz clic en el **lápiz** ✏️ (arriba a la derecha del archivo, "Edit this file").
4. Haz los cambios.
5. Haz clic en el botón verde **Commit changes…**, escribe una descripción corta (por ejemplo "Agrego charla en Lima") y vuelve a hacer clic en **Commit changes**.
6. Espera 1 a 3 minutos y recarga https://leslysuarez.github.io (si no ves el cambio, recarga con `Ctrl + Shift + R`, o `Cmd + Shift + R` en Mac).

Para ver si la publicación terminó: pestaña **Actions** del repositorio.
- 🟡 amarillo = publicando
- ✅ verde = publicado
- ❌ rojo = hubo un error (ver sección 13)

**Crear un archivo nuevo:** entra a la carpeta → botón **Add file** → **Create new file**.
**Subir un archivo (PDF, imagen):** entra a la carpeta → **Add file** → **Upload files** → arrastra el archivo → **Commit changes**.

---

## 3. Cambiar los textos de una página

Las páginas están escritas en **Markdown**, un formato de texto simple. Lo más útil:

| Escribo                              | Se ve como                  |
|--------------------------------------|-----------------------------|
| `## Título de sección`               | Título grande (con línea lavanda) |
| `### Subtítulo`                      | Subtítulo                   |
| `**negrita**`                        | **negrita**                 |
| `*cursiva*`                          | *cursiva*                   |
| `[texto del enlace](https://...)`    | enlace                      |
| `- elemento`                         | lista con viñetas           |
| una línea en blanco                  | nuevo párrafo               |
| `$$x^2 + y^2$$`                      | fórmula matemática (LaTeX)  |

La parte de arriba de cada archivo, entre las dos líneas `---`, es la **ficha** de la página (título, dirección). Cambia el `title:` si quieres otro título, pero **no cambies** `permalink:` a menos que quieras cambiar la dirección de la página.

**Botones lavanda** (como los de la página de inicio):

```html
<a class="btn--lesly" href="{{ '/talks/' | relative_url }}">Talks</a>
```

---

## 4. Agregar una charla

Cada charla es un archivo dentro de la carpeta `_talks`. La página **Talks** se arma sola, agrupada por año y ordenada de la más nueva a la más antigua.

1. Entra a la carpeta `_talks` → **Add file** → **Create new file**.
2. Nombre del archivo: `AAAA-MM-DD-nombre-corto.md`, por ejemplo `2026-03-01-charla-en-lima.md` (sin espacios ni tildes).
3. Pega esto y completa:

```yaml
---
title: "Título de la charla"
type: "Talk"
venue: "Nombre del congreso o seminario"
location: "Chile"
date: 2026-03-01
# Opcionales (borra el # para usarlos):
# slides: "/files/nombre-del-archivo.pdf"
# link: "https://..."
---
```

4. **Commit changes**.

Notas:
- `date`: siempre en formato `AAAA-MM-DD`. Si solo sabes el mes, usa el día `01`. En el sitio se muestra solo mes y año.
- `type`: si es `"Talk"` no se muestra etiqueta; con cualquier otro valor (`"Round table"`, `"Poster"`, `"Invited talk"`, `"Workshop"`…) aparece una etiqueta lavanda delante del título.
- Siempre usa **comillas** en los textos (`title`, `venue`, etc.), sobre todo si llevan dos puntos `:`.
- Para enlazar las diapositivas: sube el PDF a la carpeta `files` (sección 7) y pon `slides: "/files/nombre.pdf"` (borra el `#`).
- Si quieres agregar una descripción, escríbela **debajo** de la segunda línea `---`.

**Corregir o borrar una charla:** abre su archivo en `_talks` y edítalo con el lápiz, o bórralo con el menú `…` → **Delete file**.

---

## 5. Agregar un curso o seminario

Igual que las charlas, pero en la carpeta `_teaching`:

```yaml
---
title: "Nombre del curso o seminario"
type: "Seminar"
role: "Organizers: Nombre 1, Nombre 2"
location: "Chile"
date: 2026-03-01
link: "https://..."
---
```

- `type` puede ser `"Course"`, `"Seminar"`, `"Teaching assistant"`, etc.
- `link` y `role` son opcionales (si no los usas, borra esas líneas).
- Nombre del archivo, por ejemplo: `2026-curso-algebra.md`.

---

## 6. Agregar un evento organizado

Los eventos están en un solo archivo: `_pages/events.md`. Ábrelo con el lápiz y copia un bloque como este **arriba de los demás** (los más recientes van primero):

```markdown
### Nombre del evento

Member of the Organizing Committee ∥ Institución ∥ Ciudad, mes año.
```

---

## 7. Subir PDFs (apuntes, slides, CV)

1. Entra a la carpeta `files` → **Add file** → **Upload files** → arrastra el PDF → **Commit changes**.
   Usa nombres simples, sin espacios ni tildes: `apuntes-algebra-2026.pdf`.
2. El PDF queda disponible en `https://leslysuarez.github.io/files/apuntes-algebra-2026.pdf`.
3. Para enlazarlo desde una página:

```markdown
- [Apuntes de Álgebra]({{ '/files/apuntes-algebra-2026.pdf' | relative_url }})
```

**My Notes:** abre `_pages/my-notes.md`, borra la línea `*Coming soon.*` y agrega una línea por cada apunte como la de arriba.

**CV:** hoy el botón "CV" del menú enlaza al PDF en Google Drive. Para usar un PDF propio del sitio, súbelo a `files` (por ejemplo `cv-lesly-suarez.pdf`) y en `_data/navigation.yml` cambia el `url` del CV por `/files/cv-lesly-suarez.pdf`. Haz lo mismo con el enlace "My CV" de `_pages/overview.md`.

> Límite: GitHub acepta archivos de hasta 25 MB subidos desde la web.

---

## 8. Agregar una sección nueva al sitio

Ejemplo: una página "Publications".

1. Entra a `_pages` → **Add file** → **Create new file** → nombre `publications.md`.
2. Pega y completa:

```markdown
---
permalink: /publications/
title: "Publications"
author_profile: true
---

## 2026

- Autor, *Título del artículo*, Revista (2026). [arXiv](https://arxiv.org/abs/...)
```

3. **Commit changes**.
4. Para que aparezca en el menú, agrégala en `_data/navigation.yml` (sección 9).

---

## 9. Cambiar el menú superior

Abre `_data/navigation.yml`. Cada bloque es un botón del menú:

```yaml
  - title: "Publications"
    url: /publications/
```

- **Agregar:** copia un bloque, cambia `title` y `url`.
- **Quitar:** borra el bloque (la página sigue existiendo, solo sale del menú).
- **Ordenar:** mueve los bloques.
- Respeta **exactamente** los espacios al inicio de cada línea (2 espacios antes del `-`, 4 antes de `url`).

---

## 10. Cambiar los colores

Abre `_sass/theme/_lesly_light.scss` y cambia solo la sección **COLORES PRINCIPALES**:

```scss
$lesly-acento       : #A68AB5;   // lavanda: botones, subrayados, etiquetas
$lesly-enlace       : #7B5A8F;   // enlaces
$lesly-barra        : #000000;   // fondo de la barra superior
$lesly-barra-texto  : #FFFFFF;   // texto de la barra superior
$lesly-fondo        : #EDEDED;   // fondo gris de la página
$lesly-tarjeta      : #FFFFFF;   // fondo de los bloques de contenido
$lesly-texto        : #212121;   // texto
```

- Los colores van en formato `#RRGGBB`. Puedes elegirlos en https://htmlcolorcodes.com/es/
- Los enlaces conviene que sean un tono **más oscuro** que el acento, para que se lean bien sobre blanco.
- Los colores del **modo oscuro** (botón ☀️/🌙 de la barra) están en `_sass/theme/_lesly_dark.scss`.

Ideas de paletas:
| Estilo            | acento    | enlace    | barra     |
|-------------------|-----------|-----------|-----------|
| Actual (lavanda)  | `#A68AB5` | `#7B5A8F` | `#000000` |
| Azul académico    | `#4A7BB7` | `#2C5A8C` | `#1B2A41` |
| Verde             | `#5E9C76` | `#3B6E50` | `#1F2D24` |
| Burdeo            | `#A0525E` | `#7A2E3A` | `#2B1418` |

---

## 11. Cambiar la fuente (tipografía)

Son dos pasos:

**Paso 1.** En `_includes/head/custom.html` busca esta línea y cambia `Roboto` por la fuente nueva (elígela en https://fonts.google.com; los espacios del nombre se escriben con `+`):

```html
<link href="https://fonts.googleapis.com/css2?family=Roboto:wght@300;400;500;700&display=swap" rel="stylesheet">
```

Por ejemplo, para **Lato**: `family=Lato:wght@300;400;700`.

**Paso 2.** En `_sass/_personalizado.scss`, cambia el nombre en la primera línea de `--lesly-fuente`:

```scss
--lesly-fuente: "Lato", -apple-system, "Segoe UI", "Helvetica Neue", Arial, sans-serif;
```

Fuentes que se ven bien en sitios académicos: **Roboto** (actual), **Lato**, **Source Sans 3**, **Open Sans**, **Merriweather** (con serifa), **EB Garamond** (con serifa, clásica).

---

## 12. Cambiar la barra lateral (nombre, foto, enlaces)

Abre `_config.yml` y busca la sección `author:`:

```yaml
author:
  avatar           : "avatar-ls.svg"
  name             : "Lesly Camila Suarez Diaz"
  bio              : "M.Sc. in Mathematics. Number Theory, Algebra and Geometry."
  location         : "Santiago, Chile"
  employer         : "Universidad de Santiago de Chile"
  email            : "lesly.suarez@usach.cl"
```

- **Foto:** hoy hay un círculo lavanda con las iniciales "LS". Para poner una foto, súbela a la carpeta `images` (idealmente **cuadrada**, por ejemplo `foto-lesly.jpg`) y cambia `avatar: "foto-lesly.jpg"`.
- **Enlaces académicos:** más abajo, en la misma sección, hay líneas para `googlescholar`, `orcid`, `arxiv`, `researchgate`, `linkedin`, `github`, etc. Para activar uno, reemplaza `# URL` por el enlace entre comillas, por ejemplo:
  `orcid            : "https://orcid.org/0000-0000-0000-0000"`
  Para ocultarlo, déjalo vacío.
- El **título** que aparece arriba a la izquierda de la barra es `title:` (al principio de `_config.yml`).

> Ojo: `_config.yml` es delicado con los espacios y los dos puntos. Cambia solo lo que está entre comillas.

---

## 13. Si algo se rompe

**El sitio no se actualiza o la pestaña Actions muestra ❌ rojo:**

1. Entra a **Actions** → haz clic en la ejecución roja → **build** → mira el texto en rojo. Normalmente indica el archivo y la línea con el problema.
2. Errores típicos:
   - Faltan las **comillas** en un texto con dos puntos (`title: Ring: theorem` ✗ → `title: "Ring: theorem"` ✓).
   - Espacios mal puestos en `_config.yml` o `navigation.yml`.
   - Fecha mal escrita (debe ser `2026-03-01`).
   - Falta una de las dos líneas `---` de la ficha.
3. Corrige el archivo y guarda de nuevo. GitHub vuelve a publicar solo.

**Volver a una versión anterior de un archivo:** abre el archivo → botón **History** (arriba a la derecha) → elige la versión buena → **View file** (icono `<>`) → botón **Raw** → copia todo el texto → vuelve al archivo actual, edítalo con el lápiz, pega el texto antiguo y guarda.

**Mientras haya un error, el sitio sigue mostrando la última versión que funcionó**, así que nunca queda "caído".

---

## 14. Configuración inicial (se hace una sola vez)

Para que GitHub publique el sitio con esta plantilla:

1. En el repositorio, entra a **Settings** → **Pages** (menú izquierdo).
2. En **Build and deployment** → **Source**, elige **GitHub Actions**.
3. Ve a la pestaña **Actions**, elige **Deploy Academic Pages template site to Pages** → **Run workflow** → **Run workflow**.
4. Cuando quede en ✅ verde, el sitio está en https://leslysuarez.github.io

---

## 15. Notas sobre el traslado desde Google Sites

- Origen: https://sites.google.com/usach.cl/leslysuarez/home (noviembre de 2026). Se trasladaron las 7 secciones: Home, Overview, Research, Organization of Events, Talks, Teaching y My Notes.
- El **Google Site sigue existiendo**: no redirige solo al sitio nuevo. Conviene agregarle un aviso con el enlace a https://leslysuarez.github.io o despublicarlo.
- Las direcciones cambiaron: "Organiz Events" ahora es `/events/` (la dirección `/organiz-events/` también funciona y redirige).
- El **CV** sigue alojado en Google Drive (ver sección 7 para traerlo al sitio).
- La foto de la página Overview se copió como `images/lesly-charla.jpg`.
- Se corrigieron algunas erratas del sitio original: "activel" → "actively", "wored" → "worked", "Organizating"/"Committe" → "Organizing"/"Committee", "Interuniverstaria" → "Interuniversitaria", "Villareal" → "Villarreal", "Barera" → "Barrera", "CO FUNDER" → "Co-founder".
- **Derechos de autor:** todo el contenido (textos, imágenes, fotos, PDF) es © Lesly Camila Suarez Diaz, con todos los derechos reservados. Así lo dicen el aviso al inicio de `LICENSE`, el `README.md` y el pie de página del sitio. La licencia MIT de `LICENSE` cubre solo el código de la plantilla. Para cambiar el texto del pie de página, edita `_includes/footer.html`.
- La plantilla original es [Academic Pages](https://github.com/academicpages/academicpages.github.io) (licencia MIT). En `AGENTS.md` hay notas técnicas en inglés de la plantilla.
