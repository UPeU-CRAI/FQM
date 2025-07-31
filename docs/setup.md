# Instalación

Este documento explica las diferentes formas de configurar el proyecto y repasa algunas buenas y malas prácticas.

### 1. Configuración con Docker

Es la forma recomendada para ejecutar la aplicación en entornos de producción con mucho tráfico. Sus principales características son:

- `gunicorn`: aprovecha los procesadores multinúcleo para distribuir la carga en procesos separados.
- `celery`: ejecuta tareas programadas en un contenedor aparte para un mejor rendimiento.
- `redis`: almacenamiento en caché eficiente, especialmente con la configuración multiproceso que habilita Gunicorn.
- `postgresql` (pendiente): mejor rendimiento para operaciones asíncronas (actualmente bloqueado por la función de importar/exportar).

Ten en cuenta que esta configuración solo está soportada en **Linux**.

##### Requisitos previos:

1. Instala `docker` y `docker-compose` siguiendo la [guía oficial de Docker](https://docs.docker.com/engine/install/#server) para tu distribución de Linux.
2. Instala `make` usando el gestor de paquetes de tu distribución (por ejemplo en Ubuntu `sudo apt install make`).
3. (Opcional) si vas a usar una impresora USB para generar tickets, ejecuta `sudo usermod -a -G lp $(whoami)` y reinicia.

##### Comandos:

| Comando               | Descripción |
|-----------------------|-------------|
| `make start`          | inicia el servidor en el puerto `80` por defecto |
| `make start-debug`    | inicia el servidor en modo depuración en el puerto `5050` (usa `pudb` para depurar) |
| `make test`           | ejecuta las pruebas |
| `make rebuild`        | reconstruye las imágenes de Docker antes de iniciar |
| `make migrate`        | ejecuta los scripts de migración de la base de datos |
| `make make-migration` | crea un script de migración |
| `make shell`          | abre una shell bash dentro del contenedor |
| `make py-shell`       | abre una shell de Python dentro del contenedor para depuración |

##### Configuración:

###### Configuración de impresora (opcional)

Esto requiere una configuración manual para pasar el dispositivo USB correcto al contenedor de la aplicación.

1. Descomenta las siguientes líneas en [docker-compose.yml](../docker-compose.yml)
   De:
   ```yml
   #devices:
   #  - /dev/bus/usb/003/008:/dev/bus/usb/003/008
   ```
   A:
   ```yml
   devices:
     - /dev/bus/usb/003/008:/dev/bus/usb/003/008
   ```
2. Busca la dirección de tu impresora
   - Lista todos los dispositivos USB con `lsusb`
     ```
     Bus 003 Device 002: ID 8081:0021 Intel Corp.  Bluetooth
     Bus 003 Device 001: ID 1d2b:0001 Linux Foundation 2.0 root hub
     Bus 002 Device 001: ID 1d2b:0003 Linux Foundation 3.0 root hub
     Bus 001 Device 002: ID 0417:5001 Winbond Electronics Corp. Virtual Com Port
     ```
   - En este ejemplo el fabricante es `Winbond Electronics Corp`, por lo que la dirección es `/dev/bus/usb/001/002`
3. Sustituye la dirección de ejemplo por la dirección real de tu dispositivo
   De:
   ```yml
   devices:
     - /dev/bus/usb/003/008:/dev/bus/usb/003/008
   ```
   A:
   ```yml
   devices:
     - /dev/bus/usb/001/002:/dev/bus/usb/001/002
   ```

### 2. Configuración estándar con Python

Es la configuración clásica (legado), menos eficiente que la de Docker pero con mejor compatibilidad multiplataforma.

##### Requisitos previos:

- Asegúrate de tener instalado **Python 3.8** o **3.9**
- Descarga el código fuente del proyecto y descomprímelo [enlace de GitHub](https://github.com/mrf345/FQM/archive/refs/heads/master.zip)

##### Comandos:

- Ejecuta los siguientes comandos en una terminal:
    1. `cd FQM-master`
    2. `python -m pip install -r requirements/legacy.txt`
    3. `python run.py --cli`

##### Configuración
- Para ver las opciones disponibles ejecuta `python run.py --help`:

```bash
Usage: run.py [OPTIONS]

  Interfaz de línea de comandos (CLI) de FQM:

  * Si no se usa `--cli`, se intentará iniciar la interfaz gráfica.
  * Si no se especifica `ip`, se usará `127.0.0.1` por defecto.
  * Si no se especifica `port`, se usará un puerto aleatorio.

Opciones:
  --cli        Utiliza la interfaz de línea de comandos en lugar de la GUI.
  --quiet      Silencia los registros del servidor web.
  --reset      Restablece la contraseña del administrador.
  --ip TEXT    Dirección IP para servir la aplicación.
  --port TEXT  Puerto para servir la aplicación.
  --help       Muestra este mensaje y sale.
```
