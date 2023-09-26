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


## 5. Realizar un 'Hello World' en HTML y acceder desde el navegador.
<details>
<summary>Explicación del quinto paso.</summary>

Creamos un archivo HTML llamado **index.html** en el directorio **htdocs** que hemos montado en el paso 4. Luego, accedemos a la página desde tu navegador utilizando la siguiente URL:

[http://localhost:80](http://localhost:80)

```html
<html>
    <body>
        <h1>
            Hello World!
        </h1>
    </body>
</html>
```
</details>

## 6. Crear otro contenedor 'dam_web2' con el mismo volumen y a otro puerto.

<details>
<summary>Explicación del sexto paso.</summary>

Utilizamos el siguiente comando para llevar a cabo este paso: `docker run --name dam_web2 -d -p 9080:80 -v "$PWD"/htdocs:/usr/local/apache2/htdocs/ httpd:2.4`

```bash

docker run --name dam_web2 -d -p 9080:80 -v "$PWD"/htdocs:/usr/local/apache2/htdocs/ httpd:2.4
```
## 7. Comprobar que los dos servidores 'sirven' la misma página.

<details>
<summary>Explicación del séptimo paso.</summary>
Para esto simplemente debemos abrir el navegador y acceder a las siguientes URLs:

[http://localhost:80](http://localhost:80)
[http://localhost:9080](http://localhost:9080)
</details>

## 8. Realizar modificaciones en la página y comprobar que los dos servidores 'sirven' la misma página.

<details>
<summary>Explicación del séptimo paso.</summary>

Abrimos el archivo **index.html** en el directorio **htdocs** y realizamos modificaciones en el contenido. 
Al actualizar cualquiera de las dos URLs anteriores en el navegador, vemos las modificaciones reflejadas en ambas páginas. Esto demuestra que ambos servidores están sirviendo la misma página y se mantienen sincronizados gracias al `bind mount`.

```html
<html>
    <body>
        <h1>
            Hello World! How are you getting on?
        </h1>
    </body>
</html>
```
</details>