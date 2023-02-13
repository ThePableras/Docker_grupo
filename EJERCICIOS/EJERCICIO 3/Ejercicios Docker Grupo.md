# Ejercicios Docker Grupo
> Realizado por: Emilio Taibo

## Ejercicos 3 - Redes

- Crea una red bridge redbd
~~~
docker network create redbd
~~~
![](assets/CP3.1.png)
- Crea un contenedor con una imagen de mariaDB que estará en la red redbd . Este
contenedor se ejecutará en segundo plano, y será accesible a través del puerto 3306. (Es
necesario definir la contraseña del usuario root y un volumen de datos persistente)
~~~
adduser mariadb
docker run -d --name mariadb --network redbd -v mariadb:/home/mariadb -e MYSQL_ROOT_PASSWORD=root -p 3306:3306 mariadb
~~~
![](assets/CP3.2.PNG)

- Crear un contenedor con Adminer que se pueda conectar al contenedor de la BD
~~~
docker run --network redbd --link mariadb:db -p 8080:8080 adminer
~~~
![](assets/CP3.3.PNG)
- Comprobar que el contenedor Adminer puede conectar con el contenedor mysql abriendo un navegador web y accediendo a la URL: http://localhost:8080
![](assets/CP3.4.PNG)

Accedemos con usuario y contraseña root, y nombre de la base de datos adminer.

![](assets/P1.png)
Contenedores creados y en ejecución.

![](assets/P2.png)
Acceso a la BD a través de Adminer.

![](assets/P3.png)
![](assets/P3.1.png)
Creación de BD con Adminer.

![](assets/P4.png)
Observamos que la BD "nuevabd" se ha creado correctamente.


```sh
docker stop mariadb
docker rm adminer
docker rm mariadb
```
![](assets/P5.png)
Borramos el contenido.
