# Estudos docker

Lista de comandos uteis vistos durante curso de docker.

---
## Docker <img src="https://cdn4.iconfinder.com/data/icons/logos-and-brands/512/97_Docker_logo_logos-512.png" alt="drawing" width="80"/>

## Introdução ao docker
- Construir, rodar e transferir imagens
- Containers

## Diferenças entre VM e Container

## Como funcionar o docker
- Dockerfile
    - Imagem -> Container -> Servidor

## Docker Hub
 [DockerHub WebSite](https://hub.docker.com/)
- Transferir imagens
- Guardar imagens

## Criando a primeira imagem
- Dockerfile
    - FROM node: alpine
    - docker build -t hi-docker
- Rodando no container
    - docker run hi-docker

[Dockerfile](https://github.com/joaomanoel-dev/docker-study/blob/main/Docker/Dockerfile)

## Distribuições Linux
- Ubuntu
- Debian
- Centos
- Fedora
- Alpine

## Comandos Linux
Para subir container com imagem do ubuntu

`docker pull ubuntu`

`docker run -it ubuntu`

---
### Comandos
`whoami` - Usuario atual

`echo $0` - Path atual

`history` - historico de comandos

`apt` - instalar packages

### Diretorios
`mkdir` - cria pasta

`rm` - remover arquivos

`rm -r` - remover pasta

`touch` - cria arquivo

`mv` - move ou renomeia pasta

`cat` - visualiza conteudo do arquivo

`more` - visualiza conteudo paginado

`less` - visualiza conteudo paginado começando pelo final

`>` - redirecionamento de conteudo

`grep` - procura dentro do arquivo

`find` - localiza arquivos e diretorios

Concatenando comandos

-> `mkdir teste; cd teste; echo ok`

-> `mkdir teste && cd teste && echo ok`

### Processos
`ps` -  mostra processos

`kill` -  mata processos

### Usuarios
`useradd` -  cria usuario

`groupadd` - cria grupo

`groups "user"` - lista grupo do usuario

`usermod -g "grupo" "user"` - adiciona usuario ao grupo

### Permissões
-RW-R--R--

R - READ

W - WRITE

X - Execute

`chmod` - Altera permissão

## Criando imagens docker
FROM node:12-alpine

WORKDIR /app

COPY/ADD . .

RUN - executa comandos linux

ENV - Variaveis de ambiente

EXPOSE - Porta que vai ser exposta

USER - usuario a logar na aplicação

CMD - executa comandos depois que a imagem é criada

## Tags
`docker build -t app:v1.0.0 .`

`docker image tag app:latest app:v1.0.0`

## Compartilhar imagem
- docker push joaomanoeldev/app:v1
- docker image save -o appv1.tar
- docker image load -i appv1.tar

## Containers
- docker run - inicia container
- docker run -d - inicia container com linha de comando liberada
- docker run -d --"nome" - da nome ao container

### Logs
- docker logs "id container" - logs
- docker logs -f "id container" - logs em tempo real
- docker logs -t "id container" - logs com timestamp
- docker logs -n 10 "id container" - ultimas 10 linhas do log

## Portas de acesso
- docker run -dp 80:3000 --"name" - define porta 80:3000

## Comandos container
- docker exec - executa comandos container
- docker ps - lista containers
- docker start - continua container parado
- docker rm - remove container
- docker rm -f - remove container a força

## Volumes
- docker volume create app-dados
- docker run -dp 3000:3000 --name kiwi -v app-dados:/app/dados app:v2

## Copiando arquivos
- docker cp kiwi2:/app/teste.txt . 
- docker cp joao.txt kiwi2:/app

## Docker compose
- docker-compose up - starta imagem e container
- docker-compose down - baixa container

## Docker Network
- DNS Resolver
- Ping de um container para o outro
- Rede virtual dentro dos container
- Comunicação entre containers

## Logs docker compose
- docker-compose logs

## Docker on Cloud

- Google Cloud Run

App foi instanciada em cloud pelo serviço Google Cloud Run e está disponivel no link [App Docker](https://app-docker-study-urmzgmw2ya-rj.a.run.app/)

### Comandos utilizados no cloud shell da google
`docker pull docker.io/joaomanoeldev/app:v2`

`docker tag d180054895bf us.gcr.io/optimum-lodge-406223/app`

`sudo usermod -a -G docker jaumnetto`

`gcloud auth configure-docker`


`docker push us.gcr.io/optimum-lodge-406223/app`
