# Guía de Docker Desktop y Docker Hub

Proyecto: **Visita Seúl** (sitio estático con HTML5 y CSS3)
Usuario de Docker Hub: `tammycaizapanta`
Repositorio: `tammycaizapanta/visita-seul`
Enlace: https://hub.docker.com/r/tammycaizapanta/visita-seul

Enlace: https://github.com/tammycaizapanta/36875_Programacion_Web.git
---


## 1. Preparar Docker Desktop

1. Instala Docker Desktop desde docker.com. En Windows acepta activar **WSL 2**.
2. Ábrelo y espera a que abajo a la izquierda diga **Engine running**.
3. Inicia sesión con tu cuenta (botón **Sign in** o tu avatar arriba a la derecha).
4. Comprueba la instalación en PowerShell:

```powershell
docker --version
```

---

## 2. Estructura del proyecto

La carpeta del proyecto debe tener el `Dockerfile` junto a `index.html`:

```
Caizapanta_Tammy_Proyecto_P1/
├── css/styles.css
├── docs/propuesta.md
├── img/*.svg
├── gracias.html
├── index.html
├── Dockerfile
└── README.md
```

### Dockerfile

```dockerfile
FROM nginx:alpine
COPY . /usr/share/nginx/html
EXPOSE 80
```

FROM nginx:alpine
COPY index.html gracias.html /usr/share/nginx/html/
COPY css/ /usr/share/nginx/html/css/
COPY img/ /usr/share/nginx/html/img/
EXPOSE 80

Las rutas de destino terminan en `/` para que Docker cree la carpeta.

## 3. Construir la imagen

1. Entra a la carpeta del proyecto (la que tiene el `Dockerfile`):

```powershell
cd .\Caizapanta_Tammy_Pro
dir
```

Con `dir` debes ver `Dockerfile`, `index.html`, `css` e `img`.

2. Construye con el **punto final**:

```powershell
docker build -t tammycaizapanta/visita-seul:1.0 -t tammycaizapanta/visita-seul:latest .
```

3. Comprueba que existe:

```powershell
docker images
```

En Docker Desktop aparece en **Images**.

---

## 5. Probar el contenedor

```powershell
docker run -d -p 8080:80 --name seul-test tammycaizapanta/visita-seul:1.0
```

Abre **http://localhost:8080** 

Para ver los archivos dentro del contenedor:

```powershell
docker exec seul-test ls /usr/share/nginx/html /usr/share/nginx/html/css /usr/share/nginx/html/img
```

Para detenerlo y borrarlo:

```powershell
docker stop seul-test
docker rm seul-test
```

En Docker Desktop, la pestaña **Containers** permite hacer lo mismo con los botones de parar y la papelera.

---

## 6. Subir a Docker Hub

1. Inicia sesión:

```powershell
docker login
```

2. Sube las dos etiquetas:

```powershell
docker push tammycaizapanta/visita-seul:1.0
docker push tammycaizapanta/visita-seul:latest
```

3. Verifica en hub.docker.com, en **Repositories**. Deben aparecer `1.0` y `latest`.

Desde Docker Desktop: en **Images**, abre los tres puntos (⋮) de la imagen y elige **Push to Docker Hub**. Para que funcione, la imagen debe llamarse `tammycaizapanta/visita-seul`.

---

## 7. Descargar y ejecutar desde Docker Hub

https://hub.docker.com/r/tammycaizapanta/visita-seul  en tags

```powershell
docker pull tammycaizapanta/visita-seul:1.0
docker run -d -p 8080:80 tammycaizapanta/visita-seul:1.0
```