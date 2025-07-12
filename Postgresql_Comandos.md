## Autenticar via linha de comando
docker exec -it postgres psql -U userinfoguia -d infoguia

## Listar bancos de dados
\l

## Sair
exit ou \q 

## Verificar permissões do usuario
\du userinfoguia

## Exibir variaveis do container postgres
docker exec -it postgres env


