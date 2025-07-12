https://desktop.github.com/download/
https://code.visualstudio.com/download

Meu diretorio no Github: https://github.com/CabosEtc/

1- Criar repositório, escolher nome e se é público ou privado.
2- Adicionar o README.md
3- Clonar o repositório pelo terminal:
git clone https://github.com/CabosEtc/help.git
cd site-gerenciamento
4- Faça o upload dos seus arquivos:commit
git add .

git commit -m "Primeiro commit - Adicionando site inicial"
git push origin main
5- Para ignorar um diretório:
Criar um arquivo .gitignore no VSCode com as pastas a serem ignoradas:git 
/apk
/teste
6- Remover as pastas do rastreamento:
git rm -r --cached apk/
7- Confirmar as alterações e enviar:
git add .gitignoregit 
git commit -m "Adicionando .gitignore para ignorar apk/"
git push origin main  # Ou o nome da sua branch principal
8- Subir os arquivos:
git add . (adiciona todos os arquivos no stage)
git add arquivo.txt (somente um arquivo)
git add pasta/ (um diretório)
git commit -m "Primeiro commit - Adicionando site inicial"
git push origin main

9- Baixar os arquivos do repositório (sincronizar pasta já existente)
git pull origin master

10- Comandos importantes:
git status (verifica os arquivos que estão no stage)
git restore --staged . (limpa todos os arquivos do stage)gitrest

*Ver a parte 4. Configurar um fluxo de trabalho com versões


para compilar aqui.

.gitignore
/apk
/downloads
/separar
/tt
/drivers



