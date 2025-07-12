## Gerar
sudo certbot certonly --standalone -d evolution.infoguia.com.br

## Copiar para pasta data/certs
sudo cp /etc/letsencrypt/live/evolution.infoguia.com.br/fullchain.pem ~/stack/data/certs/evolution.infoguia.com.br.crt
sudo cp /etc/letsencrypt/live/evolution.infoguia.com.br/privkey.pem   ~/stack/data/certs/evolution.infoguia.com.br.key

## acertar o arquivo nginx/default.conf
