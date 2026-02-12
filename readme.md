Clínica – Containerização com Docker
1. Introdução

Este projeto consiste em uma aplicação web estática desenvolvida em HTML.
O presente trabalho tem como objetivo realizar a containerização da aplicação utilizando Docker, permitindo sua execução em ambiente isolado e padronizado.

A utilização de containers garante portabilidade, reprodutibilidade e independência de configuração manual de servidor web.

2. Tecnologias Utilizadas

HTML5

Docker

Nginx (imagem oficial Alpine)

3. Estrutura do Projeto
Clinica/
│── Index.html
│── UML.png
│── Atividade renato.pdf
│── Dockerfile
│── docker-compose.yml (opcional)
│── README.md

4. Processo de Containerização

A aplicação é composta apenas por arquivos estáticos. Para disponibilizá-la via navegador, foi utilizada a imagem oficial do Nginx como servidor web.

4.1 Dockerfile
FROM nginx:alpine

COPY . /usr/share/nginx/html

EXPOSE 80

CMD ["nginx", "-g", "daemon off;"]

4.2 Descrição dos Comandos

FROM nginx:alpine
Utiliza uma imagem leve do Nginx baseada em Alpine Linux.

COPY . /usr/share/nginx/html
Copia os arquivos do projeto para o diretório padrão de hospedagem do Nginx.

EXPOSE 80
Expõe a porta padrão HTTP do container.

CMD
Mantém o servidor Nginx em execução no container.

5. Execução do Projeto
5.1 Construção da Imagem
docker build -t clinica-site .

5.2 Execução do Container
docker run -p 8080:80 clinica-site


A aplicação ficará disponível em:

http://localhost:8080

6. Execução com Docker Compose (Opcional)
docker-compose.yml
version: "3.9"

services:
  web:
    build: .
    ports:
      - "8080:80"


Para executar:

docker-compose up --build

7. Conclusão

A containerização da aplicação permite sua execução em ambiente isolado, garantindo portabilidade e padronização. O uso do Docker elimina a necessidade de instalação manual de servidor web, simplificando o processo de implantação e distribuição do sistema.
