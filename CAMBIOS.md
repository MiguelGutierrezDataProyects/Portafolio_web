# Cambios aplicados al portafolio

Trabajo hecho sobre el repositorio clonado, validado localmente antes de entregar.
**No se hizo push:** eso requiere tus credenciales de GitHub y esas no las manejo.

---

## Cómo aplicarlo

1. Descomprime `portafolio-actualizado.zip` sobre la raíz de tu repositorio, sobrescribiendo.
2. **Borra a mano estos archivos**, que ya no se usan (el zip no puede borrar):

```
images/Imagen1.png
images/proyecto estadisticas de educacion.bin
images/dashboard - resultados icfes.svg
images/yo.svg
images/python.svg
images/proyecto jovenes en accion.svg
images/proyecto jovenes en accion.jpeg
images/proyecto restaurante.svg
images/proyecto boligrafos.svg
images/proyecto estadisticas de educacion.svg
images/dashboard - accidentes de transito.svg
images/dashboard - analisis de ventas.svg
images/dashboard - estado de producto.svg
images/dashboard - facturacion y proyeccion.svg
images/dashboard - recursos humanos.svg

projects/Python/Machine learning/1. Proyecto machine learning - Reconocimiento de numeros/.ipynb_checkpoints/
projects/Python/Machine learning/2. Proyecto machine learning - Regresion lineal/.ipynb_checkpoints/
```

En una terminal, dentro del repo:

```bash
git rm -r --cached "projects/Python/Machine learning/1. Proyecto machine learning - Reconocimiento de numeros/.ipynb_checkpoints" \
                   "projects/Python/Machine learning/2. Proyecto machine learning - Regresion lineal/.ipynb_checkpoints"
git add -A
git status          # revisa antes de confirmar
git commit -m "Rediseño del portafolio: metadatos, contenido, paleta y optimización de imágenes"
git push
```

3. Espera 1-2 minutos a que GitHub Pages reconstruya y revisa el sitio.

---

## Qué cambió

### Bugs corregidos

| Qué | Antes | Ahora |
| :--- | :--- | :--- |
| Meta description | `<meta name="description", charset="...">` — coma de más y `charset` en vez de `content`. **No funcionaba.** | Etiqueta válida con descripción real |
| Meta robots | Misma coma de más | Corregida |
| Campo de mensaje | `<input type="text">` — una sola línea | `<textarea>` |
| Jerarquía de encabezados | 4 `<h1>` en la portada | 1 `<h1>` + `<h2>`/`<h3>` |
| Texto alternativo | El tablero de RR. HH. decía «Palabra educación»; el de accidentes, «Interior de un restaurante»; el de ventas, «Puntas de bolígrafo» | Alt correcto en cada imagen |
| Footer | © 2025 | © 2026 |
| Menú | «Proyectos en python», «Proyectos en power bi» | «Python», «Power BI», con estado activo |
| Erratas | «lso cuales», indentación rota en una sección | Corregidas |

### Nuevo en el `<head>`

- **Open Graph y Twitter Cards** completos, con imagen `images/og-portada.png` (1200×630, generada).
  Esto es lo que desbloquea poder añadir el sitio a **Destacado en LinkedIn**.
- `canonical`, `author` y `theme-color` acorde a la paleta nueva.
- `defer` en el script de contacto.

### Contenido

- **Titular:** fuera «Analista y científico de datos | Administrador financiero | Diseñador de productos».
  Ahora: *Analytics Engineer & Data Analyst — construyo la infraestructura que va del dato crudo al KPI.*
  Debajo, una línea con el stack.
- **`<title>`:** ya no dice «Data Analyst / Science».
- **Sobre mí:** reescrito con el framework ETL, los 20+ pipelines, las pruebas en 24 de 25 proyectos
  y la carga incremental. Antes solo mencionaba dashboards en Power BI y Excel.
- **Tres proyectos destacados en la portada**, con el hallazgo real de cada uno. Antes había que dar
  tres clics para ver un análisis.
- **Descripciones cerradas.** Las nueve terminaban en «. . . .». Ahora cada una dice qué se encontró.
  Las conclusiones salieron de tus propios notebooks, no las inventé.
- **Los dos proyectos de Machine Learning** ahora están enlazados desde la página de Python.
  Antes estaban en el repo y eran invisibles desde el sitio.
- **Los cinco tableros de Power BI** tienen botón «Abrir en vivo» a su enlace público de app.powerbi.com,
  que ya tenías en los `Readme.txt` y no estaba expuesto.

### Diseño

- Paleta unificada en variables CSS: base `#0F172A`, superficie `#1E293B`, acento `#38BDF8`.
  Se fue el amarillo saturado a sangre completa y el azul suelto de los botones.
- Tipografía con `clamp()`: deja de encogerse en móvil y de agrandarse en pantallas grandes.
- Tarjetas de proyecto en grid, con imagen, hallazgo y stack.
- Formulario moderno: bordes de 1 px, radio 6 px, estado de foco con el acento.
- Separadores de 1 px en vez de la franja blanca de 0,8 vw.
- Media query nueva: por debajo de 820 px las secciones de proyecto pasan a una columna.
- `body { height: 100vh }` → `min-height`, que era un bug latente.

### Peso

| | Antes | Ahora |
| :--- | ---: | ---: |
| Carpeta `images/` | 9,34 MB | **1,41 MB** |

Los «SVG» eran en realidad imágenes rasterizadas en base64 dentro de un envoltorio SVG —por eso uno
pesaba 3,2 MB—. Se extrajeron y se guardaron como JPEG progresivo. `power bi.svg` era vectorial de
verdad y se conservó tal cual. La foto de Jóvenes en Acción se aclaró un 35 %: sobre fondo oscuro se
veía como un recuadro vacío.

### Repositorio

- `.gitignore` nuevo (checkpoints de Jupyter, `__pycache__`, archivos de sistema y de editor).
- Eliminadas las carpetas `.ipynb_checkpoints`, que incluían material de curso
  («13.- Aprendizaje de Máquina-checkpoint.ipynb»).
- `README.md` reescrito: qué es el sitio, qué contiene, estructura y stack.

---

## Verificaciones hechas

- Los 13 archivos HTML: **0 enlaces internos rotos**.
- Etiquetas balanceadas en las tres páginas principales.
- Renderizado en Chromium a 1280 px y a 390 px (móvil).
- Ninguna etiqueta meta con la coma defectuosa.

---

## Lo que queda pendiente y es tuyo

1. **Renombrar el repositorio** a `MiguelGutierrezDataProyects.github.io` para que la URL pierda el
   `/Portafolio_web/`. Es gratis, pero cambia la URL: habría que actualizar el enlace en LinkedIn y
   las etiquetas Open Graph.
2. **Reemplazar las ilustraciones por capturas reales** de cada dashboard. Las actuales son de stock
   y se nota.
3. **Renombrar las rutas de `projects/`** para quitar espacios, tildes y numeración.
4. **El proyecto de referencia** con dbt, orquestación y CI. Es lo único que cierra la distancia entre
   lo que tu perfil afirma (Analytics Engineer) y lo que tu portafolio prueba hoy (análisis).
