## Comandos básicos

| Comando | Descripción |
|--------|-------------|
| `pwd`   | muestra en qué carpeta estás |
| `cd /etc`   | cambia al directorio /etc |
| `cd ..`  | sube un nivel |
| `ls -l`| lista archivos con detalles |
| `touch archivo1.txt`   | crea un archivo vacío |
| `mkdir carpeta_ejemplo`   | crea una nueva carpeta |
| `cp archivo1.txt carpeta_ejemplo/`   | copia archivo a carpeta |
| `mv archivo1.txt renombrado.txt`   | renombra archivo |
| `rm renombrado.txt`   | elimina archivo |
| `cat archivo.txt`   | muestra el contenido completo |
| `more archivo.txt`   | similar a more, pero más interactivo |
| `head -n 5 archivo.txt`   | muestra las primeras 5 líneas |
| `tail -n 10 archivo.txt`   | muestra las últimas 10 líneas |
| `ls -1 archivo.txt`   | muestra los permisos |
| `chmod 744 archivo.txt`   | da permisos de lectura/escritura/ejecución al dueño |
| `chown ubuntu archivo.txt`   | cambia el propietario del archivo |
| `man ls`   | muestra el manual del comando ls |
| `ls --help`   | muestra ayuda rápida |
| `nano archivo.txt`   | editor de texto nano |
| `ps`   | muestra la lista de procesos en ejecución |
| `top`   | muestra en tiempo real los procesos que más consumen recursos |
| `htop`   | versión más interactiva de top |
| `pstree`   | muestra los procesos en forma de árbol jerárquico |
| `kill <PID>`   | termina el proceso por ID |
| `killall sleep`   | termina todos los procesos "sleep" |
| `nice`   |  inicia un proceso con una prioridad específica |
| `renice`   |  cambia la prioridad de un proceso que ya está en ejecución |
| `lscpu`   | muestra información del procesador |
| `mpstat`   | muestra estadísticas del uso de la CPU |
| `free-h`   | muestra el uso de la memoria RAM |
| `df-h`   | muestra el uso del espacio en disco de cada partición |
| `du`   | muestra el uso de espacio de archivos y directorios |
| `ip a`   | muestra las direcciones IP configuradas |
| `ping`   | verifica la conectividad con otro servidor |
| `netstat`   | muestra conexiones de red, tablas de enrutamiento |
| `ss`   | similar a netstat |
| `traceroute`   | muestra la ruta que siguen los paquetes hasta llegar a un servidor |
| `sleep 100 &`   | ejecuta un proceso en segundo plano |
| `ps aux  grep sleep`   | lista los procesos en ejecución que incluyen la palabra "sleep"  |

## Arquitectura cliente/servidor

| Comando | Descripción |
|--------|-------------|
| `sudo apt update`   | actualiza la lista de paquetes disponibles desde los repositorios |
| `sudo apt upgrade -y`   | instala todas las actualizaciones disponibles para los paquetes ya instalados -y responde “sí” automáticamente a todas las confirmaciones |
| `sudo apt install`  | usa el gestor de paquetes APT para instalar uno o varios paquetes en Ubuntu |
| `-y`| lista archivos con detalles |
| `ca-certificates`   | contiene los certificados digitales de autoridades de certificación confiables |
| `curl`   | descarg archivo desde internet |
| `gnupg`   | convierte o valida una clave GPG de Docker  |
| `install`   | crea archivos o directorios y asigna permisos y propietario de forma controlada |
| `-m 0755`   | establece los permisos del directorio creado como 0755 |
| `-d`   | indica que se debe crear un directorio  |
| `/etc/apt/keyrings`   | nueva ubicación recomendada por Debian/Ubuntu para almacenar claves GPG de repositorios externos |
| `-f`   | falla en silencio si la descarga falla |
| `-s`   | silencioso |
| `-S`   | si ocurre un error, sí lo muestra  |
| `-L`   | sigue redirecciones  |
| `simbolo pipe`   | toma la salida de curl y la pasa como entrada a gpg |
| `gpg --dearmor`   | convierte una clave ASCII-armored (texto plano) a formato binario, que es lo que necesita APT |
| `-o /etc/apt/keyrings/docker.gpg`   | guarda la clave convertida en el archivo docker.gpg dentro del directorio /etc/apt/keyrings |
| `nano archivo.txt`   | editor de texto nano |
| `echo "deb [...] ..."`   | está generando una línea de repositorio APT con varios elementos importantes |
| `arch=$(dpkg --print-architecture) `   | detecta automáticamente la arquitectura del sistema para que APT descargue los paquetes correctos |
| `signed-by=/etc/apt/keyrings/docker.gpg `   | le dice a APT que confíe solo en los paquetes firmados con esa clave GPG |
| `$(lsb_release -cs)`   | inserta automáticamente el nombre en clave de tu versión de Ubuntu |
| `stable`   | indica que deseas usar la rama estable |
| `sudo tee /etc/apt/sources.list.d/docker.list`   | toma la salida del echo y la escribe como archivo dentro del sistema |
| `> /dev/null`   |  silencia la salida del tee para que el usuario no vea el contenido generado |
| `sudo docker run hello-world`   |  muestra un mensaje de bienvenida si todo funciona bien |
| `mkdir apache-php-server
cd apache-php-server
mkdir src`   | inicia la estructura base de tu proyecto Docker con Apache y PHP |
| `echo "<?php echo 'Hola desde el servidor Apache con PHP. Fecha: ' . date('Y-m-d H:i:s'); ?>" > src/index.php`   | respuesta del servidor a las solicitudes del cliente |
| `cat src/index.php`   | verifica lo anterior |
| `nano Dockerfile`   | crean el archivo Dockerfile, para que Docker sepa cómo construir tu imagen personalizada con Apache y PHP |
| `FROM php:8.2-apache `   | usa una imagen oficial de PHP con Apache preinstalado |
| `COPY src/ /var/www/html/ `   | copia el contenido del directorio src/ al directorio raíz de Apache dentro del contenedor |
| `EXPOSE 80 `   | informa que el contenedor usará el puerto 80  |
| `sudo docker build -t apache-php .`   | construye una imagen a partir del Dockerfile en este directorio y asigna el nombre apache-php |
| `sudo docker run -d -p 80:80 --name servidor-web apache-php`   | crea y ejecuta un contenedor Docker a partir de la imagen apache-php |
| `sudo docker ps`   | verifica que está corriendo lo anterior |
| `sleep 100 &`   | ejecuta un proceso en segundo plano |
| `ps aux  grep sleep`   | lista los procesos en ejecución que incluyen la palabra "sleep"  |

## Administración de archivos

| Comando | Descripción |
|--------|-------------|
| `echo "Este es un archivo de prueba." > archivo1.txt`   | escribe texto dentro del archivo |
| `schmod g+w archivo1.txt`   | agrega permiso de escritura |
| `chmod o-r archivo1.txt`  | quita permiso de lectura |
| `touch script.sh`| crea un nuevo archivo de script vacío |
| `echo -e '#!/bin/bash\necho "Hola Mundo"' > script.sh`   | escribe un script que imprime un mensaje |
| `chmod 700 script.sh`   | da permisos solo al dueño |
| `ls -l script.sh`   | muestra los permisos del script  |
| `/script.sh`   | ejecuta el script |
| `file archivo1.txt`   | muestra el tipo de archivo que es archivo1.txt |
| `stat archivo1.txt`   | muestra información detallada del archivo  |
| `echo -e "\x7fELF" > binario`   | crea un archivo llamado "binario" |
| `lsblk`   | muestra todos los dispositivos de almacenamiento conectados y su estructura de particiones |
| `mount`   | monta un dispositivo en una carpeta específica del sistema |
| `df -T`   | muestra el tipo de sistema de archivos para cada punto de montaje  |
| `sudo mkfs.ext4 /dev/xvdf`   | crea un sistema de archivos ext4 en un volumen  |
| `sudo mount /dev/xvdf /mnt/disco1`   | monta el volumen en el directorio |
| `sudo nano /etc/fstab`   | abre el archivo de configuración para añadir una entrada de montaje |
| `sudo adduser usuario1`   | crea un nuevo usuario en el sistema |
| `sudo mkdir /home/usuario1/privado`   | crea el directorio privado dentro del home del usuario |
| `sudo chown usuario1:usuario1 /home/usuario1/privado`   | cambia el propietario de la carpeta para que sea el usuario1 |
| `chmod 700 /home/usuario1/privado `   | otorga permisos para que solo el dueño pueda leer, escribir y acceder |








