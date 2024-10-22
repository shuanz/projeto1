
# README.md

## Descrição do Projeto

Este projeto consiste em um sistema baseado em contêineres, com uma arquitetura multi-serviços. Ele utiliza Docker Compose para orquestrar os serviços frontend, backend e um proxy reverso Nginx, que também é responsável pelo balanceamento de carga.

## Estrutura do Projeto

- **frontend/**: Diretório com a aplicação de frontend
- **backend/**: Contém o backend da aplicação
- **nginx.conf**: Arquivo de configuração para o Nginx, que faz o balanceamento de carga e atua como proxy reverso.
- **docker-compose.yml**: Arquivo principal do Docker Compose que define os serviços, redes, volumes e configurações.

## Opções de Design

### Escolha de Serviços

- **Frontend**: O serviço de frontend lida com a interface de usuário. Ele se comunica com o backend por meio do Nginx.
- **Backend**: O backend é o serviço responsável por fornecer a lógica de negócio para o frontend.
- **Nginx**: Atua como proxy reverso e balanceador de carga, roteando as requisições entre o frontend e o backend, garantindo alta disponibilidade e escalabilidade.

### Volumes

Volumes são usados para persistir dados dos serviços, permitindo que as informações não sejam perdidas quando os contêineres são reiniciados.

### Redes

Uma rede Docker interna é usada para facilitar a comunicação entre os contêineres, garantindo isolamento de outros serviços externos.

### Estratégia de Balanceamento de Carga

O Nginx é configurado para balancear a carga entre os serviços de backend, roteando requisições o algoritmo do tipo round-robin, melhorando a distribuição de tráfego.

## Instruções de Instalação

### Pré-requisitos

- Docker 27+ instalado
- Docker Compose v2 instalado

### Passos para Instalação

1. Clone o repositório:
   ```bash
   git clone https://github.com/shuanz/projeto1.git
   ```
   
2. Navegue até o diretório do projeto:
   ```bash
   cd pratica1
   ```

3. Suba os contêineres usando o Docker Compose:
   ```bash
   docker-compose up --build
   ```

### Acesso aos Serviços

- **Frontend**: Acesse o serviço frontend em `http://localhost:3000`.
- **Backend**: O backend está acessível internamente para o frontend, e pode ser configurado para expor portas adicionais, se necessário.

## Atualizações de Componentes

### Atualizando a Versão de uma Imagem Docker

Para atualizar qualquer componente (frontend, backend, ou nginx), siga estes passos:

1. Abra o arquivo `dockerfile`.
2. Localize o serviço que deseja atualizar, por exemplo:
   ```yaml
   FROM python:3.8
   ```
3. Troque a versão da imagem para a versão desejada:
   ```yaml
   FROM python:3.13
   ```
4. Rode o comando para reconstruir e atualizar o serviço:
   ```bash
   docker-compose up --build
   ```

Isso irá baixar a nova versão da imagem e rodar os serviços com a versão atualizada.
