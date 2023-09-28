# Configuración y Ejecución de Servicios con Consul, Express y HAProxy

## Paso 1: Iniciar el Agente de Consul en Modo Desarrollo

```bash
consul agent -dev -bind=192.168.192.1 -data-dir=.
```
consul agent: Inicia el agente de Consul.

-dev: Habilita el modo de desarrollo.

-bind=192.168.192.1: Configura la dirección IP a la que se enlazará el agente de Consul.

-data-dir=.: Establece el directorio de datos del agente de Consul en el directorio actual.

## Paso 2: Instalar las Bibliotecas Node.js

```bash
npm install express consul
```

## Paso 3: Ejecutar un Contenedor Docker con HAProxy

```bash
docker run -d --name my-running-haproxy -p 8080:80 -v ./haproxy.cfg:/usr/local/etc/haproxy/haproxy.cfg haproxy:lts-alpine
```

docker run: Inicia un contenedor Docker.

-d: Ejecuta el contenedor en segundo plano.

--name my-running-haproxy: Asigna un nombre al contenedor, en este caso, "my-running-haproxy".

-p 8080:80: Mapea el puerto 8080 de tu máquina host al puerto 80 del contenedor, lo que permite acceder a HAProxy desde tu máquina en el puerto 8080.

-v ./haproxy.cfg:/usr/local/etc/haproxy/haproxy.cfg: Monta el archivo "haproxy.cfg" desde tu directorio actual en el directorio "/usr/local/etc/haproxy/haproxy.cfg" dentro del contenedor. Esto proporciona una configuración personalizada para HAProxy.

haproxy:lts-alpine: Utiliza la imagen "haproxy:lts-alpine" de Docker, que es una versión de HAProxy basada en Alpine Linux.
