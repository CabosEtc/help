# Versão 04Jun25 - Incluiu profile infra/automacao, retirou a linha version: 3.8 (obsoleta) 
# version: "3.8"

services:

  nginx:
    #profiles: ["infra"]
    image: nginx:stable
    container_name: nginx
    ports:
      - "80:80"
      - "443:443"
    volumes:
      - ./nginx/default.conf:/etc/nginx/conf.d/default.conf:ro
      - ./frontend/public:/usr/share/nginx/html:ro
      - ./data/certs:/etc/letsencrypt:ro
    # depends_on:
      #- n8n # retirado para evitar erro, o n8n está no profile automacao agora
    restart: always
    networks:
      - app-network

  redis:
    #profiles: ["infra"]
    image: redis:7.2.4-alpine
    container_name: redis
    ports:
      - "6379:6379"
    volumes:
      - ./data/redis:/data
    restart: always
    networks:
      - app-network

  postgres:
    image: postgres:15
    #profiles: ["infra"]
    container_name: postgres
    restart: always
    environment:
      POSTGRES_USER: userinfoguia
      POSTGRES_PASSWORD: Fgl159753
      POSTGRES_DB: infoguia
    volumes:
      - ./data/postgres:/var/lib/postgresql/data
    ports:
      - "5432:5432"
    networks:
      - app-network
  n8n:
    image: n8nio/n8n:1.93.0
    #profiles: ["automacao"]
    container_name: n8n
    restart: always
    env_file:
      - .env
    ports:
      - "5678:5678"
    environment:
      - N8N_HOST=${N8N_HOST}
      - N8N_PORT=${N8N_PORT}
      - N8N_PROTOCOL=${N8N_PROTOCOL}  # Adicionado 27Mai25 .env
      - N8N_EDITOR_BASE_URL=${N8N_EDITOR_BASE_URL}
      - WEBHOOK_URL=${WEBHOOK_URL}
      - N8N_BASIC_AUTH_ACTIVE=${N8N_BASIC_AUTH_ACTIVE}
      - N8N_BASIC_AUTH_USER=${N8N_BASIC_AUTH_USER} # Adicionado 27Mai25 .env
      - N8N_BASIC_AUTH_PASSWORD=${N8N_BASIC_AUTH_PASSWORD}  # Adicionado 27Mai25 .env
#      - NODE_ENV=production
#      - REDIS_HOST=redis
#      - N8N_PATH=${N8N_PATH}
    volumes:
      - ./data/n8n:/home/node/.n8n
#    depends_on:
#      - redis # retirado, o redis está no profile infra
    networks:
      - app-network

  evolution-api:
    image: atendai/evolution-api:v2.2.2
    #profiles: ["automacao"]
    container_name: evolution_api
    restart: "always"
    ports:
      - "8080:8080"
    environment:
      - DATABASE_PROVIDER=postgresql
      - DATABASE_URL=postgres://userinfoguia:Fgl159753@postgres:5432/infoguia
    volumes:
      - ./data/evolution:/evolution/instances
    depends_on:
      - postgres
    networks:
      - app-network

networks:
  app-network:
    driver: bridge


