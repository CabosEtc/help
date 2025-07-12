# Comandos Linux
## 📁 Manipulação de Diretórios e Arquivos
> ls -la	Lista arquivos, inclusive ocultos, com detalhes
> cd nome_da_pasta	Entra em um diretório
> pwd	Mostra o caminho atual
> mkdir nova_pasta	Cria nova pasta
> rm arquivo.txt	Remove arquivo
> rm -r pasta/	Remove pasta recursivamente
> cp origem destino	Copia arquivos ou pastas
> mv origem destino	Move ou renomeia arquivos/pastas
> touch nome.txt	Cria arquivo vazio

## 🔍 Busca e Leitura
> cat arquivo.txt	Exibe conteúdo
> less arquivo.txt	Exibe conteúdo paginado
> grep 'termo' arquivo.txt	Busca por termo dentro de arquivo
> find . -name "*.conf"	Encontra arquivos com padrão no nome

## ⚙️ Permissões e Propriedades
> chmod +x script.sh	Torna executável
> chown user:grupo arquivo	Muda dono e grupo
> ls -lh	Lista com permissões e tamanhos legíveis

## 🧠 Gerenciamento de Processos
> ps aux	Lista todos os processos
> top ou htop	Monitora processos em tempo real
> kill PID	Encerra processo por PID
> killall nome_processo	Encerra todos os com mesmo nome

## 🌐 Rede
> ping google.com	Testa conexão
> curl http://localhost	Faz requisição HTTP
> netstat -tulpn	Mostra portas abertas e serviços
> lsof -i :443	Mostra processo usando a porta 443

## 🛠️ Sistema e Utilitários
> df -h	Mostra uso de disco
> du -sh pasta/	Tamanho da pasta
> uptime	Tempo ligado e carga do sistema
> history	Mostra comandos usados recentemente
> reboot	Reinicia sistema