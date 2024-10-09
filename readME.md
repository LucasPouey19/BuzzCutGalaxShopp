# API de Gerenciamento de Usuários e Produtos com Node.js e MySQL

## Descrição

Esta API permite gerenciar usuários e produtos utilizando um banco de dados MySQL. O servidor é construído com Node.js, Express e faz consultas ao banco de dados MySQL. A API suporta operações de criação, leitura, atualização e exclusão (CRUD) para usuários e produtos.

## Requisitos

- **Node.js** (v12 ou superior)
- **MySQL** (v5.7 ou superior)

## Instalação

### 1. Clone o repositório

```bash
git clone https://github.com/LucasPouey19/BuzzCutGalaxShopp.git
cd backend

##instale as dependências do Node.js utilizando o comando:
npm install

##Certifique-se de que o MySQL esteja instalado e rodando
##Acesse o MySQL a partir da linha de comando:
mysql -u root -p

##Execute o script SQL localizado em src/bancoDados.sql para criar o banco de dados e as tabelas necessárias. Certifique-se de estar no diretório correto e execute o comando abaixo:
source src/bancoDados.sql;
##Esse script criará as tabelas users e products no banco de dados api_db, conforme definido no arquivo.

##Abra o arquivo src/db_config.js e edite a configuração do banco de dados com suas próprias credenciais de MySQL, caso necessário:
const connection = mysql.createConnection({
    host: 'localhost',
    user: 'root',
    password: 'sua_senha',
    database: 'api_db',
});

##Com todas as dependências instaladas e o banco de dados configurado, inicie o servidor rodando o seguinte comando no terminal:
node src/server.js

##Se tudo estiver correto, o servidor será iniciado na porta 3003 e você verá a mensagem:
Rodando na porta 3003

##Teste as rotas da API
##Use um cliente HTTP como Postman ou Insomnia para testar as seguintes rotas:

##Usuários
##POST /usuario/cadastrar - Cadastrar um novo usuário.

##Body: { "name": "Nome", "email": "email@exemplo.com", "password": "senha123" }
##GET /usuario/listar - Listar todos os usuários.

##PUT /usuario/editar/:id - Editar informações de um usuário.

##Body: { "name": "Nome Atualizado", "email": "email@exemplo.com", "password": "novaSenha123" }
##DELETE /usuario/deletar/:id - Deletar um usuário pelo ID.

##Produtos
##POST /produto/cadastrar - Cadastrar um novo produto.

##Body: { "titulo": "Produto", "descricao": "Descrição do produto", "preco": 100 }
##GET /produto/listar - Listar todos os produtos.

##PUT /produto/editar/:id - Editar informações de um produto.

##Body: { "titulo": "Novo Título", "descricao": "Nova descrição", "preco": 150 }
##DELETE /produto/deletar/:id - Deletar um produto pelo ID.

##Descrição dos Arquivos
##src/db_config.js: Contém a configuração da conexão com o banco de dados MySQL. As credenciais de acesso ao banco estão configuradas neste arquivo.

##src/server.js: Ponto de entrada do servidor Node.js. Este arquivo define as rotas das APIs, inicia o servidor na porta 3003 e realiza as operações de CRUD para usuários e produtos.

##src/bancoDados.sql: Script SQL que cria o banco de dados api_db, as tabelas users e products, e qualquer dado inicial necessário para teste.

##Nesta nova atualização do site foi inserido algumas novas funções como a de login e autenticação de usuarios, cada usuario insere seu nome, email e senha, a rota faz com que seja cadastrado no bd, e sempre que um usuario tentar fazer login a rota /login é buscada e recupera os dados do cadastro e com o js confere se eles coincidem com o inserido no formulario...

##Temos 2 tipos de usuarios, usuarios com o nome de "usuario" que são clientes de compra, que apenas tem permissão para comprar e olhar o site, já o outro tipo de usuário, tem o nome de "admin" ele que possui outras funções também desenvolvidas nessa última entrega do site, sendo elas, cadastro de produto e edição de produto.

##O cadastro de produto pela rota interligada com js, cria um array que usa um request para pegar os valores do formulario de input para o novo produto, e quando é clicado no botão de inserir, a função pega os valores e poem numa div com os mesmos nomes do css para ficar com o mesmo estilo.

##Um detalhe utilizado no meio do processo é a API multer que serve para fazer com que as imagens que são variaveis tenham nomes qualificados para que o js e outras API's consigam ler e identificar o endereço

##A função de editar o produto é usada também com uma rota de método PUT (/produto/:id) que serve para ver os valores que já estão cadastrados e usa uma função do mySql chamada "update" que atualiza os valores antigos cadastrados pelos novos, que são recolhidos também por inputs dentro do modal que abre pela opção de editar liberada para admins
