
Desenvolvimento em Docker 

front  Angularr
back   nodejs
db     mongo




- PASSO 1 Criar imagens primeiro 


# docker build -t clientfront .

# docker build -t serverback .

docker run -d --name container_name image_name

- PASSO 2 

docker-compose build

docker-compose up

Vc vera com docker-compose ps

25b691f548ba        clientfront         "sh -c 'while true ;…"   7 minutes ago       Up 7 minutes        0.0.0.0:4200->4200/tcp   angular_front_1
ba2972b01dd1        serverback          "sh -c 'while true ;…"   7 minutes ago       Up 7 minutes        0.0.0.0:3000->3000/tcp   angular_back_1

- Passo 3

docker exec -it angular_front_1 bash
vc vera dentro do Front container

ao entrarr dentro do container 
pode testar
# $ root@25b691f548ba:/app# ping front 
# $ PING front (172.24.0.3) 56(84) bytes of data.
# $ 64 bytes from 25b691f548ba (172.24.0.3): icmp_seq=1 ttl=64 time=0.034 ms

e executar o comando 

ng serve --host 0.0.0.0

testando no seu navegador
http://localhost:4200/
ira aparecer a aplicacao

# $/app# c
    criar novo projeto
    ng new projectname

- Passo 4
# $/app# 
    configurar backend


- Passo 5 

comentar o comando de container zumbi

colocar o comando de executar o projeto com a porta aberta para 4200

ng serve --host 0.0.0.0