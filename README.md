# chatwoot-all-in-one

 
Pre requisitos
ubuntu server 20.04
--------------------------
#instalar o docker com o comando

sudo curl -L https://get.docker.com | sh

adicionar seu usuario no grupo docker * após adicionar o usuario entre no seu ssh novamente

sudo usermod -aG docker $USER

---------------------
#clonar repositorio

git clone https://github.com/edcarlosm/chatwoot-all-in-one.git

entre na pasta chatwoot

edite os sequintes arquivos.

config.json coloque um token nesse campo aqui secretKey": "TOKEN"

edite o docker-compose 

Coloque uma senha pessoal nesse campo aqui - POSTGRES_PASSWORD=password

se for utilizar um dominio no seu chatwoot coloque a informação aqui - FRONTEND_URL=https://chatwoot.dominio.com.br

-------

#prepare o docker * vai demorar um pouco dependendo da sua internet

docker compose up --build --no-start

Prepare o banco de dados

docker compose run --rm rails bundle exec rails db:chatwoot_prepare

inicie o docker

docker compose up -d

-------------
#passos para instalação no ip local(sem dominio)

acesse o ip vm( http://ip-vm:3000

acesse o super_admin

crie um bot, pegue o token do bot, edite o bot cliado para adicionar o Outgoing url

coloque as seguintes informações 

http://bridge:3000/chatwoot/webhook?botpress_bot_id=bot&chatwoot_bot_token=token-do-agente-bot *obs se alterar o id do bot lembrar de alterar nesse link tb.

-----------
#edite novamente o docker-compose 


Coloque o token do seu bot aqui  - CHATWOOT_BOT_TOKEN=TOKEN-BOT-CHATWOOT

se for criar um bot com id diferente de 'bot' faça a alteração aqui - BOTPRESS_BOT_ID=bot *obs esse bot é criado no botpress

-------------------

no chatwoot crie uma caixa de entrada do tipo api

coloque o nome preferido e coloque esse link aqui como api http://wppconnect-server:21465/api/minhasala/chatwoot

nesse mesma caixa adicione o bot criado no chatwoot.

adicione um contato com o numero +5511999999999 esse contato vai ser responsavel para dar o start no wppc

----------------------------------
acesse o n8n importe o flow que está nesse git, altere o token do usuario do chatwoot e token do wppc.

vá no contato criado e de um /start minhasala

agora é só esperar que vai aparecer o qrcode.

para mais informações segue os links de fontes utilizadas.

link referente ao integrador do bot

https://www.linkedin.com/pulse/subindo-um-ambiente-de-desenvolvimento-chatbot-poderoso-douglas-lara/

link referente a os videos de instalação e configuração o chatwoot+n8n+wppconnect

https://www.youtube.com/watch?v=A4QsJvJMWIA&list=WL

https://www.youtube.com/watch?v=00616mTid-M

--------------------------------------------

Deu muito trabalho consegui todas essas informações, assim que tiver um tempo coloco melhoro essa cocumentação


se quiser me ajudar com pix minha chave é edcarlos@kabaweb.in
