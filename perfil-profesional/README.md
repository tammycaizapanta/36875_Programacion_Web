# Perfil profesional - Tammy Caizapanta

## Objetivo del proyecto

Implementar los conocimientos de desarrollo web y contenedorización mediante la creación y despliegue de un sitio web de perfil profesional optimizado, estructurado con HTML5 y CSS moderno, y empaquetado utilizando Nginx y Docker para su distribución en Docker Hub.

## Tecnologías utilizadas

* HTML5
* CSS en archivo externo
* Nginx
* Docker y Docker Hub
* Git y GitHub

## Estructura del proyecto

```
perfil-profesional/
├── index.html
├── css/
│   └── styles.css
├── img/
│   ├── foto_perfil.jpg
│   ├── github.png
│   ├── ig.png
│   ├── pageicon.png
│   └── linkedin.png
├── docs/
│   ├── mockup.png
│   ├── Evidencia1.png
│   ├── Evidencia2.png
│   └── Presentación.pdf
├── Dockerfile
└── README.md
```

## Construir y ejecutar la imagen Docker

**Requisito:** Tener Docker instalado y abierto.

**1. Descargar el proyecto:**

```bash
git clone https://github.com/tammycaizapanta/36875_Programacion_Web.git
cd 36875_Programacion_Web
```

**2. Construir la imagen:**

```bash
docker build -t tammycaizapanta/perfil-profesional:1.0 .
```

**3. Ejecutar el contenedor:**

```bash
docker run -d --name perfil --rm -p 8083:80 tammycaizapanta/perfil-profesional:1.0
```

**4. Abrir en el navegador:** [http://localhost:8083](http://localhost:8083)

* Para ver los contenedores activos: `docker ps`
* Para detener y eliminar uno: `docker stop <id>` y `docker rm <id>`

También se puede usar la imagen publicada directamente sin necesidad de construirla:

```bash
docker run -d --name perfil --rm -p 8083:80 tammycaizapanta/perfil-profesional:1.0
```

## Enlace a Docker Hub

[https://hub.docker.com/r/tammycaizapanta/perfil-profesional](https://hub.docker.com/r/tammycaizapanta/perfil-profesional)

## Autora

Tammy Amarilis Caizapanta Muela - Ingeniería de Software, Universidad de las Fuerzas Armadas ESPE