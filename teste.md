# README

## Visão Geral

Este projeto configura um ambiente de desenvolvimento usando Docker Compose. Inclui vários serviços como Traefik, Jaeger, Prometheus, Grafana, Nginx, PHP, MySQL, phpMyAdmin, Redis, MongoDB, Adminer, Jenkins, Gitea e Portainer.

## Pré-requisitos

- Docker
- Docker Compose

## Configuração

1. Clone o repositório.
2. Navegue até o diretório do projeto.
3. Execute `docker-compose up -d` para iniciar todos os serviços.

## Serviços

### Traefik

Traefik é um proxy reverso e balanceador de carga.

- **Acessar Dashboard**: `http://localhost:8080`
- **Configuração**:
    - `--api.insecure=true`: Habilita o dashboard do Traefik.
    - `--providers.docker=true`: Habilita o provedor Docker.
    - `--entrypoints.web.address=:80`: Define o ponto de entrada web.
    - `--tracing.jaeger=true`: Habilita o rastreamento Jaeger.
    - `--metrics.prometheus=true`: Habilita métricas Prometheus.
    - `--accesslog=true`: Habilita logs de acesso.

### Jaeger

Jaeger é usado para rastreamento.

- **Acessar UI**: `http://localhost:16686`

### Prometheus

Prometheus é usado para monitoramento e alertas.

- **Acessar UI**: `http://localhost:9090`
- **Configuração**: Monte `prometheus.yaml` em `/etc/prometheus/prometheus.yaml`.

### Grafana

Grafana é usado para visualização de dados.

- **Acessar UI**: `http://grafana.local`
- **Porta Padrão**: 3000

### Nginx

Nginx é um servidor web.

- **Acessar UI**: `http://nginx.local`
- **Configuração**: Monte `nginx.conf` em `/etc/nginx/nginx.conf`.

### PHP

PHP é usado para scripts do lado do servidor.

- **Configuração**: Monte o diretório `app` em `/var/www/html`.

### MySQL

MySQL é um banco de dados relacional.

- **Acessar UI**: `http://mysql.local`
- **Variáveis de Ambiente**:
    - `MYSQL_ROOT_PASSWORD`: root
    - `MYSQL_DATABASE`: app_db
    - `MYSQL_USER`: user
    - `MYSQL_PASSWORD`: password

### phpMyAdmin

phpMyAdmin é uma interface web para MySQL.

- **Acessar UI**: `http://phpmyadmin.local`
- **Variáveis de Ambiente**:
    - `PMA_HOST`: mysql
    - `PMA_USER`: root
    - `PMA_PASSWORD`: root

### Redis

Redis é um armazenamento de estrutura de dados em memória.

- **Acessar UI**: `http://redis.local`

### MongoDB

MongoDB é um banco de dados NoSQL.

- **Acessar UI**: `http://mongodb.local`

### Adminer

Adminer é uma ferramenta de gerenciamento de banco de dados.

- **Acessar UI**: `http://adminer.local`

### Jenkins

Jenkins é uma ferramenta de CI/CD.

- **Acessar UI**: `http://jenkins.local`

### Gitea

Gitea é um serviço Git auto-hospedado.

- **Acessar UI**: `http://gitea.local`

### Portainer

Portainer é uma ferramenta de gerenciamento Docker.

- **Acessar UI**: `http://portainer.local`

## Redes

- `app_network`: Uma rede bridge para todos os serviços.

## Volumes

- `mysql_data`: Armazenamento persistente para MySQL.
- `mongo_data`: Armazenamento persistente para MongoDB.
- `jenkins_home`: Armazenamento persistente para Jenkins.
- `gitea_data`: Armazenamento persistente para Gitea.
- `portainer_data`: Armazenamento persistente para Portainer.
- `grafana_data`: Armazenamento persistente para Grafana.

## Uso

1. Iniciar todos os serviços: `docker-compose up -d`
2. Parar todos os serviços: `docker-compose down`
3. Ver logs: `docker-compose logs -f`

## Conclusão

Esta configuração fornece um ambiente de desenvolvimento abrangente com várias ferramentas e serviços. Personalize os arquivos de configuração conforme necessário para seu caso específico.