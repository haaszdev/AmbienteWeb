# Ambiente Web

Este repositório contém a configuração de um ambiente WordPress usando Docker Compose, integrando serviços adicionais como MySQL, Redis e Prometheus.

## Requisitos

Antes de iniciar, certifique-se de ter as seguintes ferramentas instaladas:

- [Docker](https://www.docker.com/get-started)
- [Docker Compose](https://docs.docker.com/compose/install/)

## Passo a Passo da Instalação

1. Habilite a coleta de métricas no Docker editando o arquivo `daemon.json`:

    - Linux: `/etc/docker/daemon.json`
    - Windows: `%programdata%\docker\config\daemon.json`
    - macOS: `~/.docker/daemon.json`

    Configure dessa forma:

    ```bash
    {
      "experimental": false,
      "metrics-addr": "127.0.0.1:9323"
    }
    ```

    Reinicie o Docker a fim de aplicar as alterações.

2. Clone este repositório:

    ```bash
    git clone https://github.com/haaszdev/AmbienteWeb.git
    cd AmbienteWeb
    ```

3. Inicie os contêineres:

    ```bash
    docker-compose up
    ```

    Espere até que todos os contêineres estejam em execução.

4. Configure o WordPress:

    - Acesse `http://localhost:8080` em seu navegador.
    - Siga as instruções para finalizar a instalação do WordPress:
        - Selecione o idioma desejado.
        - Complete as informações do site, como título, nome de usuário, senha e email.
        - Clique em "Instalar WordPress".
    - Após a instalação, basta acessar com a conta criada.
    - Na página de plugins do WordPress, ative o plugin Redis Object Cache.
    - Verifique se o Redis está ativo nas configurações do plugin no WordPress.

## Os serviços são expostos nas seguintes portas:

- WordPress: `localhost:8080`
- Redis: `localhost:6379`
- Prometheus: `localhost:9090`
