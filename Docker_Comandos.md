# A versão do docker-compose.yml de 04Jun25 agora controla os containers atraves de perfis

## Perfil infra (NGINX e Redis)

docker compose --profile infra up -d
docker compose --profile infra down -v

## Perfil automacao (N8N e Evolution)

docker compose --profile automacao up -d
docker compose --profile automacao down -v

## 🐳 Docker
> docker ps                                                    | Lista containers ativos
> docker logs -f nome	                                       | Acompanha logs do container
> docker logs nginx                                            | mostra o log do app (nginx, neste exemplo)
> 
> docker exec -it container bash	Entra no container
> 
> docker compose down -v                                       | Remove os volumes anônimos associados aos serviços. ⚠️ Remove dados persistentes.
> docker compose down -d n8n                                   | Remove o n8n 
> docker compose down --remove-orphans                         | Remove containers órfãos (que não estão no docker-compose.yml atual).
> docker compose down --rmi                                    | Remove imagens locais

> docker compose up -d                                         | Sobe o container em background (modo daemon)
> docker compose up --build                                    | Força o build das imagens antes de subir os containers
> docker compose up -d n8n                                     | Sobe somente o n8n
> docker compose up -d --build                                 | Garante que a imagem será recompilada conforme os arquivos atuais, evitando erros por ambiente desatualizado.
> docker compose up --force-recreate                           | Recria os containers mesmo que não haja mudanças
> docker compose up --remove-orphans                           | Remove containers órfãos da rede Docker

### Organizar estes com calma, são do docker compose up
-d, --detach	Roda os containers em background (modo daemon)
--build	Força o build das imagens antes de subir os containers
--force-recreate	Recria os containers mesmo que não haja mudanças
--no-deps	Sobe somente o serviço indicado, sem subir seus depends_on
--no-build	Não constrói as imagens, mesmo que elas não existam
--remove-orphans	Remove containers órfãos da rede Docker
--wait	Aguarda até que todos os containers estejam saudáveis (requer healthcheck)
`--pull always	missing
--attach [serviço]	Mostra logs apenas de serviços específicos (funciona com --detach desabilitado)
--exit-code-from [serviço]	Faz o docker compose up retornar o exit code do serviço indicado
--renew-anon-volumes	Recria volumes anônimos (como se fosse um novo container do zero)
--scale [serviço=n]	Sobe múltiplas instâncias de um mesmo serviço (docker compose up --scale worker=3)



## Verificar os aplicativos que estão rodando na mesma rede
docker network inspect app-network