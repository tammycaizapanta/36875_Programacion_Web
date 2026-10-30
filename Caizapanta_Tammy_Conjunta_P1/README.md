# Portal web «Innova ESPE 2026»

Examen práctico P1. Portal informativo y responsivo hecho **solo con HTML5 y CSS3** (sin frameworks, sin plantillas y sin JavaScript).

**Estudiante:** Tammy Amarilis Caizapanta Muela

## Estructura

```
CAIZAPANTA_TAMMY_P1/
├── index.html
├── css/styles.css
├── assets/
│   ├── imagenes/
│   └── video/
├── evidencias/
│   ├── dockerDesktop.png
│   ├── dockerHub.png
│   ├── escritorio.png
│   └── movil.jpeg
├── Dockerfile
└── README.md
```

## Cómo ejecutarlo

- **Navegador:** abrir `index.html` con doble clic.
- **Docker (construcción local):**

```bash
docker build -t caizapanta_tammy_p1 .
docker run --rm -p 8080:80 caizapanta_tammy_p1
```

Luego abrir <http://localhost:8080>. El mapa (iframe de OpenStreetMap) necesita internet.

## Imagen Docker (Docker Hub)

La imagen está publicada de forma pública en Docker Hub:

- **Repositorio:** <https://hub.docker.com/r/tammycaizapanta/caizapanta_tammy_p1> en la parte de tags
- **Imagen:** `tammycaizapanta/caizapanta_tammy_p1:latest`
- **Base:** `nginx:alpine`, que sirve `index.html`, `css/` y `assets/` en el puerto 80.

### Ejecutar desde Docker Hub (sin clonar el proyecto)

1. Descargar la imagen:

```bash
docker pull tammycaizapanta/caizapanta_tammy_p1:latest
```

2. Ejecutar el contenedor:

```bash
docker run --rm -p 8080:80 tammycaizapanta/caizapanta_tammy_p1:latest
```

3. Abrir <http://localhost:8080> en el navegador.
4. Para detener el contenedor, presionar `Ctrl + C`.

### Probar desde el celular

Con el contenedor corriendo y el celular en la misma red WiFi, abrir `http://IP_DE_LA_PC:8080`. La IP se obtiene con `ipconfig` en Windows (Dirección IPv4 del adaptador Wi-Fi).

### Construir y publicar la imagen (referencia)

```bash
docker build -t caizapanta_tammy_p1 .
docker login
docker tag caizapanta_tammy_p1 tammycaizapanta/caizapanta_tammy_p1:latest
docker push tammycaizapanta/caizapanta_tammy_p1:latest
```

### Evidencias de Docker

- `evidencias/dockerDesktop.png`: imagen `caizapanta_tammy_p1` construida en Docker Desktop.
- `evidencias/dockerHub.png`: repositorio público `tammycaizapanta/caizapanta_tammy_p1` en Docker Hub.

## Decisiones de maquetación

| Tema | Decisión |
|------|----------|
| HTML semántico | `header`, `nav`, `main`, `section`, `article`, `table`, `form`, `fieldset`, `footer`. |
| Mobile First | Los estilos base son del móvil (una columna). Un solo `@media (min-width: 768px)` adapta a escritorio. |
| Flexbox | Menú de navegación y encabezado (`.main-header`, `.nav-menu`); también la sección de bienvenida y el formulario. |
| CSS Grid | Proyectos destacados (`.projects-grid`): 1 columna en móvil y 3 en escritorio. También el bloque multimedia (video y mapa). |
| Modelo de caja | `box-sizing: border-box` global, más `margin`, `padding`, `border` y `width` en tarjetas y formulario. |
| Posicionamiento | `position: sticky` en el encabezado (`.main-header`), que queda fijo al hacer scroll. |
| Pseudoclases | `:hover` y `:focus` en el menú, los botones, las tarjetas y los campos del formulario. |
| Selectores | De elemento (`body`, `section`, `form`), de clase (`.project-card`, `.btn-primary`) y de id (`#inscripcion`). |
| Sin scroll horizontal | Imágenes con `width: 100%` o `flex` con `min-width: 0`; video e iframe al 100% del contenedor. |

## Formulario (validaciones nativas)

- Nombres: `required`, `minlength`, `maxlength`.
- Correo: `type="email"` y `required`.
- Teléfono: `type="tel"`, `required`, `maxlength="10"` y `pattern="[0-9]{10}"`.
- Carrera: `select` con `required`.
- Modalidad: botones `radio` con `required`.
- Áreas de interés: casillas `checkbox`.
- Comentarios: `textarea` con `maxlength`.
- Condiciones: `checkbox` con `required`.

## Evidencias

Capturas completas de la página en `evidencias/escritorio.png` (1440 px) y `evidencias/movil.jpeg` (móvil).

## Recursos

- `assets/imagenes/logo-innovativa.png`: logotipo ESPE Innovativa, usado en el encabezado y como favicon.
- `banner-espe.jpg`, `proyecto-*.jpg` y `video-poster.jpg`: imágenes de la portada, proyectos y póster del video.
- `assets/video/innova-espe-promo.mp4`: video promocional del evento.