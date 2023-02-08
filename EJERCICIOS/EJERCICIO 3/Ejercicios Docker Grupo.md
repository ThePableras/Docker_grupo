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
docker run -d --name mariadb --network redbd -v mariadb:/home/mariadb -e -e MYSQL_DATABASE=adminer -e MYSQL_ROOT_PASSWORD=root -e MYSQL_USER=adminer -e MYSQL_PASSWORD=adminer -p 3306:3306 mariadb
~~~
![](assets/CP3.2.PNG)

- Crear un contenedor con Adminer que se pueda conectar al contenedor de la BD
~~~
docker run --network redbd --link mariadb: -p 8080:8080 adminer
~~~
![](assets/CP3.3.PNG)
- Comprobar que el contenedor Adminer puede conectar con el contenedor mysql abriendo un navegador web y accediendo a la URL: http://localhost:8080
![](assets/CP3.4.PNG)