# demo-elk-8
demo-elk-8

Si se tiene ARM
```bash
export DOCKER_DEFAULT_PLATFORM=linux/amd64
```

```bash
docker network create net_test_logs
docker-compose -f docker-compose.yml up -d
docker-compose -f docker-compose-elk.yml ps
docker-compose -f docker-compose-elk.yml logs -f kibana
docker-compose -f docker-compose-elk.yml logs -f elasticsearch
docker-compose -f docker-compose-elk.yml logs -f nginx
```

Validar conexion a elastic por http
```bash
curl -vvvv -u elastic:changeme -X GET "http://localhost:18081/elastic/_license"
