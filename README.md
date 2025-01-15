# Conversão de Distâncias

## Descrição
Este projeto é uma aplicação simples de conversão de distâncias, desenvolvida em Python e disponibilizada para uso via um contêiner Docker. O objetivo principal é permitir que os usuários convertam diferentes unidades de distância, como metros para quilômetros, de forma rápida e acessível.

![image](https://github.com/user-attachments/assets/16195380-bb3d-46f0-bc13-9b3be1dc537b)


## Tarefa Prática

### 1. Configuração do Ambiente
1. Faça um fork do repositório original e clone o novo repositório da aplicação "Conversão de Distâncias" no GitHub:
   [https://github.com/KubeDev/conversao-distancia](https://github.com/KubeDev/conversao-distancia).
2. Crie um **Dockerfile** que atenda aos requisitos do projeto.

### 2. Criação e Teste do Contêiner
1. Gere uma imagem Docker a partir do Dockerfile criado:
   ```bash
   docker build -t jose2301/conversao-distancia-fakeshop:v1 .
   docker build -t jose2301/conversao-distancia-fakeshop:latest .
   ```
2. Execute o contêiner para garantir que a aplicação esteja acessível na porta 8080:
   ```bash
   sudo docker container run -d -p 8080:5000 jose2301/conversao-distancia-fakeshop:v1
   ```
3. Acesse a aplicação no navegador:
   [http://localhost:8080/](http://localhost:8080/)



### 3. Entrega
1. Suba em um repositório público no GitHub com as alterações realizadas, incluindo o **Dockerfile**.
2. Publique a imagem do contêiner em sua conta no Dockerhub.
3. Adicione o link da imagem publicada no Dockerhub em um arquivo `.md` no seu repositório.

## Dockerfile
Abaixo está o Dockerfile utilizado para criar a imagem:

```dockerfile
FROM python:3.13.0
WORKDIR /app
COPY  requirements.txt .
RUN apt-get update && \
    pip install -r requirements.txt
COPY . /app/
EXPOSE 5000
CMD [ "gunicorn","--bind","0.0.0.0:5000", "app:app" ]
```

## Links Importantes
- Link do repositório no GitHub: [https://github.com/KubeDev/conversao-distancia](https://github.com/KubeDev/conversao-distancia)
- Link do Dockerhub: [https://hub.docker.com/repository/docker/jose2301/conversao-distancia-fakeshop/general](https://hub.docker.com/repository/docker/jose2301/conversao-distancia-fakeshop/general)

### Versões Publicadas
- **v1:** [Dockerhub - v1](https://hub.docker.com/repository/docker/jose2301/conversao-distancia-fakeshop/tags/v1/sha256-aea8954702dff0c2407b64f68763cd5575026259ad3f00391848f55ec66b2b45)
- **latest:** [Dockerhub - latest](https://hub.docker.com/repository/docker/jose2301/conversao-distancia-fakeshop/tags/latest/sha256-aea8954702dff0c2407b64f68763cd5575026259ad3f00391848f55ec66b2b45)

## Observações
- Certifique-se de que a porta **8080** está disponível no host antes de executar o contêiner.
- Utilize o comando abaixo para verificar o log do contêiner, caso necessário:
  ```bash
  sudo docker logs <container_id>
  ```

