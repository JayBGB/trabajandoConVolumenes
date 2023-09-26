# Trabajando con volúmenes

## 1. Descargar la imagen 'httpd'

<details>
<summary>Explicación del primer paso.</summary>

Utilizamos el comando `docker pull httpd:2.4` y comprobamos que se haya descargado correctamente con `docker images`.

```bash
docker pull httpd:2.4

docker images
```
</details>

## 2. Crear un contenedor con el nombre 'dam_web1'

<details>
<summary>Explicación del segundo paso.</summary>

Con `docker run --name dam_web1 -d httpd:2.4` creamos el contenedor.

```bash

docker run --name dam_web1 -d httpd:2.4
```

</details>

## 3. ¿Cómo acceder desde el navegador?

<details>
<summary>Explicación del tercer paso.</summary>

Para acceder al contenedor desde el navegador de tu equipo, se necesita mapear el puerto del contenedor al puerto de nuestra máquina local, lo cual se llevó a cabo en el anterior paso en la creación del contenedor.

</details>

## 4. Utilizar bind mount para que el directorio 'htdocs' se sitúe en el directorio elegido.

<details>
<summary>Explicación del cuarto paso.</summary>

Tras borrar el anterior contenedor para poder crearlo de nuevo con el mismo nombre, usamos el comando `docker run --name dam_web1 -d -p 80:80 -v "$PWD"/htdocs:/usr/local/apache2/htdocs/ httpd:2.4`.

```bash

docker run --name dam_web1 -d -p 80:80 -v "$PWD"/htdocs:/usr/local/apache2/htdocs/ httpd:2.4
```

</details>
