# Ejercicio 1 - Trabajo con imágenes
> Realizado por Pablo R.

| Contenido | URL |
| -- | --|
| Docker PHP | https://hub.docker.com/_/php |
| Docker Port | https://docs.docker.com/config/containers/container-networking/ |

## Servidor web
- **Arranca un contenedor que ejecute una instancia de la imagen php:7.4-apache , que se
llame web y que sea accesible desde un navegador en el puerto 8000.**

    Consultamos la documentacion de Docker php-apache para verificar el comando a ejecutar.

    ```sh
        docker run -d --name web -p 8000:80 php:7.4-apache
    ```

    ![](./assets/Punto1.PNG)

    Creamos la imagen de docker php.

    ![](./assets/inpect.PNG)
    
    Con docker inspect obtenemos la URL del contenedor.

    ![](./assets/webfunciona.PNG)
    
    Observamos que la web funciona. http://localhost:8000/


- **Colocar en el directorio raíz del servicio web ( /var/www/html ) un sitio web donde figure el nombre de los componentes del grupo.**

    ```sh
        docker start <id_contenedor>
        docker exec -it web <id_contenedor>
    ```

    ![](./assets/index.PNG)

    ![](./assets/indexcreate.PNG)

    ![](./assets/webindex.PNG)

    Entramos en el contenedor y creamos el fichero index.

- **Colocar en ese mismo directorio raíz un archivo llamado mes.php que muestre el nombre del mes actual. Ver la salida del script en el navegador.**

    ```sh
        nano /var/www/html/mes.php
    ```

    ```php
    <?php
        echo date('F');
    ?>
    ```

    ![](./assets/mes.PNG)

    ![](./assets/mesphpview.PNG)

    Creamos el fichero de mes.php y lo visualizamos

- **Borrar el contenedor.**
