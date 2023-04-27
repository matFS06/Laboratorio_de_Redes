Manual de cria��o de container Docker para p�gina web da empresa Help Solu��es em TI

Esse manual tem como objetivo explicar de forma passo a passo como disponibilizar a p�gina web da empresa Help Solu��es em TI em um container Docker no Laborat�rio Elan.
Pr�-requisitos
Antes de come�armos, voc� precisar� ter:
�	Acesso ao servidor web onde o c�digo HTML da p�gina web da empresa Help Solu��es em TI est� dispon�vel.
�	Uma conta no Laborat�rio Elan e acesso remoto.
�	O Docker instalado em sua m�quina local ou no servidor remoto.
Passo 1: Preparar o ambiente Docker
Antes de iniciar o processo de cria��o do container, vamos preparar o ambiente Docker. Para isso, siga os seguintes passos:
1.	Conecte-se ao servidor remoto atrav�s do terminal com o comando:
ssh <SEU_USUARIO>@200.17.141.82 -p 3333
2.	Verifique se o Docker est� instalado no servidor atrav�s do comando:
docker �version

3.	Caso o Docker por algum motivo inesperado n�o esteja instalado, voc� pode seguir as instru��es de instala��o na documenta��o oficial do Docker: https://docs.docker.com/get-docker/.

Passo 2: Cria��o do container
Agora que o ambiente est� configurado, vamos criar o container para a p�gina web da empresa Help Solu��es em TI. Para isso, siga os seguintes passos:
1.	Crie um arquivo chamado Dockerfile na pasta raiz do seu projeto com o seguinte conte�do:
FROM nginx
COPY . /usr/share/nginx/html
2.	No terminal, navegue at� a pasta raiz do seu projeto e execute o seguinte comando para criar a imagem do container:

docker build -t <NOME_DA_IMAGEM> .

3.	Agora que a imagem do container foi criada, vamos criar o container a partir dessa imagem. Execute o seguinte comando:
docker run -d -p <PORTA_EXTERNA>:80 --name <NOME_DO_CONTAINER> <NOME_DA_IMAGEM>
Onde <PORTA_EXTERNA> � a porta que ser� utilizada para acessar a p�gina web da empresa Help Solu��es em TI atrav�s do navegador. Por exemplo, se voc� escolher a porta 8080, a p�gina web estar� dispon�vel em http://localhost:8080.
O <NOME_DO_CONTAINER> � o nome que voc� deseja dar ao container para identifica��o.

O <NOME_DO_CONTAINER> � o nome que voc� deseja dar ao container para identifica��o.
Passo 3: Disponibiliza��o da p�gina web no container
Com o container criado, agora voc� precisa disponibilizar o c�digo HTML da p�gina web da empresa Help Solu��es em TI dentro do container. Para isso, siga os seguintes passos:
1.	Copie o c�digo HTML da p�gina web da empresa Help Solu��es em TI para a pasta raiz do seu projeto.
2.	No terminal, navegue at� a pasta raiz do seu projeto e execute o seguinte comando para acessar o shell do container:
docker exec -it <NOME_DO_CONTAINER> sh
3.	Agora que voc� est� dentro do container, navegue at� a pasta onde o c�digo HTML ser� copiado. No caso da imagem do Nginx, a pasta � /usr/share/nginx/html. Execute o seguinte comando para copiar o c�digo HTML para dentro do container:
cp <NOME_DO_ARQUIVO_HTML> /usr/share/nginx/html
Passo 4: Manuten��o do container
Ap�s a cria��o do container, � importante mant�-lo atualizado e seguro. Para isso, siga as seguintes boas pr�ticas:
1.	Mantenha o sistema operacional do servidor atualizado.
2.	Mantenha o Docker atualizado.
3.	Mantenha o c�digo HTML da p�gina web da empresa Help Solu��es em TI atualizado.
4.	Fa�a backups do container regularmente.
5.	Monitore o container em busca de poss�veis problemas de seguran�a e desempenho.
Com essas boas pr�ticas em mente, voc� funcion�rio poder� manter o container da p�gina web da empresa Help Solu��es em TI seguro e atualizado.



