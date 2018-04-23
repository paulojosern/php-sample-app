# 1. DOCUMENTAÇÃO - FRONTEND

Na raiz do projeto FRONTEND foi criado o arquivo Dockerfile com os comandos para o build da imagem e containers.

### 1. Arquivo Dockerfile

**Imagem PHP**
> FROM php:7.2-apache

**local onde será exposto**
> WORKDIR /var/www/html/

**Copia o conteudo PHP do diretório para a web**
> COPY . /var/www/html/

**Instalar extensão mysqli**
RUN docker-php-ext-install mysqli

## 2. CRIAÇÃO E BUILD DA IMAGEM 

**Inciar a criação da imagem para o build do frontend**
> $ docker build . -t frontend:0.0.1

**Verificar imagem criada**
> $ docker images

**Rodar docker da imagem em backround passando a porta e a tag** 
> $ docker run -d -p 80:80 frontend:0.0.1

**Verificar o container criado**
> $docker ps