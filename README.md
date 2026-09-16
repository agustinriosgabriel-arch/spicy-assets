# Spicy Marketing — assets públicos

Contiene el logo para firma de email y la **Base de Contenido**, una tabla web para registrar
campañas, creadores, copys y piezas publicadas.

## Base de Contenido (`web/`)

Sitio estático de un solo archivo. No necesita build, servidor ni base de datos.

| Columna | Para qué sirve |
|---|---|
| ✓ Publicado | Marcar cuando la pieza ya está arriba en redes |
| Campaña | Nombre de la campaña |
| Producto promovido | Producto concreto que se muestra |
| URL del producto | Página del producto |
| Marca / URL de la marca | Marca y su sitio |
| Agencia | Agencia que la gestiona |
| Creador | Quién grabó la pieza |
| Plataforma | Selección múltiple: TikTok, Instagram, YouTube, Facebook, Threads, X, Otro |
| Link TikTok / Link Instagram / Otro link | Links de las piezas publicadas |
| Copy | Texto que acompaña la publicación |

Incluye buscador, filtros (estado, marca, creador, plataforma), alta y baja de filas,
descarga a CSV e importación desde CSV.

### Dónde se guardan los datos

En el **navegador de cada persona** (`localStorage`). Es inmediato y no requiere cuentas,
pero implica tres cosas:

- Cada quien ve su propia copia; los cambios **no** se sincronizan entre personas.
- Se pierden si se limpian los datos del navegador o se usa una ventana privada.
- Para compartir o respaldar: **Descargar CSV** y, del otro lado, **Importar CSV**.

El archivo arranca con 29 registros precargados. El botón *Restablecer datos iniciales*
vuelve a ese punto de partida.

Si más adelante quieren una base compartida entre todo el equipo, hay que cambiar el
almacenamiento (Netlify Blobs con una función serverless, o una hoja de cálculo como backend).

## Publicar en Netlify

El repo ya trae `netlify.toml` con `publish = "web"`, así que no hay nada que configurar.

1. Entrar a [app.netlify.com](https://app.netlify.com) e iniciar sesión con GitHub.
2. **Add new site → Import an existing project → GitHub**.
3. Elegir el repositorio `agustinriosgabriel-arch/spicy-assets`.
4. Dejar todo como viene (Netlify lee `netlify.toml`) y dar **Deploy**.
5. Queda en línea en `https://<nombre>.netlify.app`. El nombre se cambia en
   **Site configuration → Change site name**, y un dominio propio se conecta en
   **Domain management**.

Cada push a la rama publicada vuelve a desplegar el sitio automáticamente.

### Alternativa sin repo

Arrastrar la carpeta `web/` a [app.netlify.com/drop](https://app.netlify.com/drop).
Queda en línea igual, pero sin despliegues automáticos.

## Desarrollo local

No hay dependencias. Basta con abrir `web/index.html` en el navegador, o servirlo:

```bash
python3 -m http.server 8000 --directory web
# http://localhost:8000
```
