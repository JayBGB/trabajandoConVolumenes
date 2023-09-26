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