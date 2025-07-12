# A versão do docker-compose.yml de 04Jun25 agora controla os containers atraves de perfis

## Perfil infra (NGINX e Redis)

docker compose --profile infra up -d
docker compose --profile infra down -v

## Perfil automacao (N8N e Evolution)

docker compose --profile automacao up -d
docker compose --profile automacao down -v

## 🐳 Docker
> docker ps	Lista containers ativos
> docker-compose up -d	Sobe serviços em segundo plano
> docker logs nginx (mostra o log do app nginx, por exemplo)
> modo follow abaixo:
> docker logs -f nome	Acompanha logs do container
> docker exec -it container bash	Entra no container
> docker-compose down	Para e remove os serviços
> docker compose down -d n8n                                   | Remove o n8n 
> docker compose up -d n8n                                     | Sobe somente o n8n
> docker-compose up -d --build                                 | Garante que a imagem será recompilada conforme os arquivos atuais, evitando erros por ambiente desatualizado.

## Verificar os aplicativos que estão rodando na mesma rede
docker network inspect app-network