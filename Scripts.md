#Crea un script para cada uno de los siguientes problemas en ubuntu:
 
Crea un script que añada un puerto de escucha en el fichero de configuración de Apache. El puerto se recibirá como parámetro en la llamada y se comprobará que no esté ya presente en el fichero de configuración.

1. Creamos el script:

`nano script1.php`.

 ![Paso 1](images/paso1.PNG)

2. Copiamos el contenido del script

```bash
add_apache_port() {
    PORT=$1
    CONFIG_FILE="/etc/apache2/ports.conf"

    if [ -z "$PORT" ]; then
        echo "Por favor, proporciona un puerto como argumento."
        exit 1
    fi

    if grep -q "^Listen $PORT" "$CONFIG_FILE"; then
        echo "El puerto $PORT ya está presente en $CONFIG_FILE."
    else
        echo "Añadiendo el puerto $PORT al fichero de configuración..."
        echo "Listen $PORT" | sudo tee -a "$CONFIG_FILE"
        echo "Puerto $PORT añadido con éxito."
    fi
}
```

 ![Paso 2](images/paso2.PNG)

 Guardamos y Salimos

 Damos permisos de ejecución

 `chmod +x script.sh`

 Si quisieramos probar el script

 `sudo ./script.sh add_apache_port 8080`


Crea un script que añada un nombre de dominio y una ip al fichero hosts. Debemos comprobar que no existe dicho dominio en el fichero hosts

Lo mismo

Crea un script que nos permita crear una página web con un título, una cabecera y un mensaje
