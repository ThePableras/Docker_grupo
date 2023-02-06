## Ejercicio 2 - almacenamiento - Portainer

> Realizado por Patricia Fdez

Descargo la imagen de portainer, la más actualizada es portainer/portainer-ce

```bash
docker pull portainer/portainer-ce
```
![](assets/descargarImagen.png)

Compruebo que se ha descargado la imagen y esta en el repositorio.

```bash 
docker images
```
![](assets/comprobarimagenes.png)

Creo un volumen para portainer y creo un contenedor le añadimos la imagen que descargamos y el volumen que acabo de crear.

```bash
docker volume create portainer_v

sudo docker run -d -p 9000:9000 --name=portainer_c --restart=always -v /var/run/docker.sock:/var/run/docker.sock -v /volume1/docker/portainer:/portaines_v portainer/portainer-ce:latest

```
![](assets/volumenycontenedor.png)

La añadimos un directorio en el contenedor en el que irá el volumen y un puerto, en este caso 9000.

Abrimos el navegador y vemos: 

![](assets/navgador1.png)

Paramos el contenedor:

![](assets/stopcontainer.png)

Comprobamos en el navegador lo que nos muestra el contenedor parado.

![](assets/stopcontainernavegador.png)

Borramos el contenedor

![](assets/rmcontainer1.png)





