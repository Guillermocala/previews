# Visualizador de mocks HTML

Repositorio para previsualizar mocks HTML de varios proyectos desde un único menú.

## Uso

1. Sirve el contenido del repo como sitio estático (no abras `index.html` como `file://`):
   - **Node**: `npx serve .` o `npx serve -p 3000 .`
   - **Python**: `python -m http.server 8080` (desde la raíz del repo)
   - **VS Code / Cursor**: extensión "Live Server" con raíz en esta carpeta

2. Abre en el navegador la URL del servidor (p. ej. `http://localhost:3000/`).

3. En la vista principal elige una previsualización. Se abrirá en una página con barra superior fija y botón "Volver al menú".

## Añadir previsualizaciones

1. Coloca tus archivos HTML en carpetas bajo el repo (por ejemplo `mocks/<proyecto>/`).

2. Edita `previews.json` y añade o modifica entradas con este formato:

```json
{
  "projects": [
    {
      "name": "Nombre del proyecto",
      "previews": [
        { "name": "Nombre visible", "path": "mocks/proyecto/archivo.html" }
      ]
    }
  ]
}
```

- `name`: texto que se muestra en el menú.
- `path`: ruta relativa al HTML del mock desde la raíz del repo.

**GitHub Pages:** Usa nombres de carpeta sin espacios ni caracteres especiales (ñ, tildes) en las rutas (p. ej. `terque-rediseno-landing-wordpress`) para evitar 404. El `name` puede seguir mostrando el texto con tildes.

## Publicar en GitHub Pages

1. Crea un repositorio en GitHub y sube este proyecto (o conéctalo si ya existe):
   ```bash
   git remote add origin https://github.com/TU_USUARIO/TU_REPO.git
   git branch -M main
   git push -u origin main
   ```

2. En GitHub: **Settings** → **Pages** (menú izquierdo).

3. En **Build and deployment**:
   - **Source**: "Deploy from a branch".
   - **Branch**: `main` (o `master`).
   - **Folder**: `/ (root)`.

4. Guarda. En unos minutos el sitio estará en `https://TU_USUARIO.github.io/TU_REPO/`.

Las rutas de `previews.json` son relativas, así que el menú y el viewer funcionan igual que en local.

## Estructura

- `index.html` — Menú principal (lista de proyectos y previsualizaciones).
- `viewer.html` — Página que muestra el mock en un iframe y la barra fija "Volver al menú".
- `previews.json` — Listado de proyectos y previsualizaciones (editar al añadir mocks).
- `mocks/` — Carpeta de ejemplo; puedes usar otras rutas y referenciarlas en `previews.json`.
