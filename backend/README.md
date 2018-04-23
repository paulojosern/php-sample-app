# 1. DOCUMENTAÇÃO - BACKEND

Na raiz do projeto BACKEND foi criado o arquivo Dockerfile com os comandos para o build da imagem e containers.

Além do arquivo Dockerfile foi adicionado o demo.sql, que são os comandos para nosso banco de dados

### 1. Arquivo Dockerfile

**Imagem base da ultima versão do mysql**
> FROM mysql:5.7

**Copia o conteudo do diretório para a web**
> COPY ./demo.sql /docker-entrypoint-initdb.d/

## 2. Pull do PHP, Apache e MYSQL

**Executar o Pull da imagem do PHP com o Apache**
> $ docker pull php:7.2-apache

**Executar o Pull da imagem do MYSQL em sua última versão**
> $ docker pull mysql:5.7

## 3. CRIAÇÃO E BUILD DA IMAGEM 

**Inciar a criação da imagem para o build do do BACKEND passando a tag com a versão**
> $ docker build . -t db:0.0.1

**Executar o comendo do  MYSQL utilizando usando imagem que foi criada. Passando parametro "-d"  que executa o container em segundo plano, informar o nome e que não tem senha**
> $ docker run -d -e MYSQL_DATABASE=demo  -e MYSQL_ALLOW_EMPTY_PASSWORD=yes --name backend db:0.0.1

**Usando o terminal para bater no container backend e rodar o comando mysql -u root -p para conectar com o banco**
> $ docker exec -ti backend mysql -u root -p

## 4. CONECTANDO FRONTEND COM BACKEND

**Build do Projeto anterior: (para rodar o FRONTEND)**
> $ docker build . -t frontend:0.0.1

**fazer a comunicação entre o backend e o FRONTEND**
> $ docker run -d -p 80:80 --name frontend --link backend frontend:0.0.1
