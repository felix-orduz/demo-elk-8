# Demo ELK 8

Este proyecto es una demostración de una pila ELK (Elasticsearch, Logstash y Kibana) utilizando Docker y Docker Compose.

## Requisitos

- Docker
- Docker Compose

## Configuración para ARM

Si estás utilizando una máquina con arquitectura ARM, asegúrate de exportar la plataforma Docker adecuada:

```bash
export DOCKER_DEFAULT_PLATFORM=linux/amd64
```

## Preparación

Primero, crea una red Docker para los contenedores:

```bash
docker network create net_test_logs
```

## Despliegue

Levanta los servicios definidos en el `docker-compose.yml`:

```bash
docker-compose -f docker-compose.yml up -d
```

Verifica el estado de los contenedores:

```bash
docker-compose -f docker-compose.yml ps
```

### Logs

Puedes seguir los logs de los diferentes servicios utilizando los siguientes comandos:

- Kibana:

```bash
docker-compose -f docker-compose.yml logs -f kibana
```

- Elasticsearch:

```bash
docker-compose -f docker-compose.yml logs -f elasticsearch
```

- Nginx:

```bash
docker-compose -f docker-compose.yml logs -f nginx
```

## Validación de Conexión a Elasticsearch

Para validar la conexión a Elasticsearch a través de Nginx, usa el siguiente comando `curl`:

```bash
curl -vvvv -u elastic:changeme -X GET "http://localhost:18081/elastic/_license"
```

## Estructura del Proyecto

- `docker-compose.yml`: Define los servicios de Elasticsearch, Kibana y Nginx.
- `nginx.conf`: Configuración de Nginx para redirigir el tráfico a Elasticsearch y Kibana.
- `certs/`: Directorio para almacenar certificados SSL generados.
- `.env`: Archivo para definir las variables de entorno necesarias.

## Notas

- Asegúrate de definir las contraseñas y otras configuraciones sensibles en el archivo `.env` antes de ejecutar los comandos.
- Este proyecto utiliza configuraciones de seguridad básicas para los servicios de Elasticsearch y Kibana. Revisa y ajusta las configuraciones de seguridad para un entorno de producción.
- La configuración actual está optimizada para un entorno de desarrollo. Ajusta los límites de recursos y otras configuraciones según las necesidades de tu entorno.

## Recursos

- [Documentación de Elasticsearch](https://www.elastic.co/guide/en/elasticsearch/reference/current/index.html)
- [Documentación de Kibana](https://www.elastic.co/guide/en/kibana/current/index.html)
- [Documentación de Nginx](https://nginx.org/en/docs/)
- [Docker](https://www.docker.com/)
- [Docker Compose](https://docs.docker.com/compose/)

## Licencia

Este proyecto está licenciado bajo la Licencia MIT. Consulta el archivo LICENSE para más detalles.

## Apóyame
<a href="https://www.buymeacoffee.com/felixorduz" target="_blank"><img src="https://www.buymeacoffee.com/assets/img/custom_images/orange_img.png" alt="Buy Me A Coffee" style="height: 41px !important;width: 174px !important;box-shadow: 0px 3px 2px 0px rgba(190, 190, 190, 0.5) !important;-webkit-box-shadow: 0px 3px 2px 0px rgba(190, 190, 190, 0.5) !important;" ></a>
