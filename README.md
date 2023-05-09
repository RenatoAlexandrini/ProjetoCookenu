<h1 align="center" >
<img src="https://user-images.githubusercontent.com/102265620/232607819-1b497b9c-d4d5-413c-ae58-4eb31b6e2386.png" width="40" height="40"/>
Projeto Cookenu
<img src="https://user-images.githubusercontent.com/102265620/232608087-df71270b-199a-4b11-8af0-962ef4ce5e86.png" width="40" height="40"/>
</h1>

 ![Badge Finalizado](http://img.shields.io/static/v1?label=STATUS&message=FINALIZADO&color=GREEN&style=for-the-badge)

 <hr>
 <h4>
<img src="https://user-images.githubusercontent.com/102265620/232635961-16b32592-2838-428c-ad15-012aa7a357a5.png" width="20" height="20"/>
O projeto Cookenu, tem como principal objetivo, reforçar o que foi aprendido sobre o conteúdo de Backend, ao longo do curso da Labenu.
Utilizando uma arquitetura em três camadas(Data, Controller e Business), os conceitos de Herança, Arquitetura limpa, Criptografia e principalmente reforçando ainda mais o conceito de Programação Orientada a Objeto, com criação de classes para todas as funções e na maioria das DTOs utilizadas no projeto, também aprofundando o conceito de autenticação, inserindo a parte de "Role" da conta, existindo um tipo de conta Normal com funções restritas e uma conta de Administrador.
</h4>
<h4>
<img src="https://user-images.githubusercontent.com/102265620/232636107-ab8c585f-47db-439f-ab33-0b112fc128a4.png" width="22" height="22"/>
O projeto simula uma rede social de receitas contendo as entidades, Usuários, Receitas e Seguidores, composta pelas ações mais comuns em redes sociais, como criar um usuário, criar uma receita, verificar uma receita postada, seguir um usuário, receber um feed com as receitas postadas por todos os usuários seguidos, verificar o profile, atualizar posts e até deletar contas.
</h4>
<hr>
<h3>
 
<img src="https://user-images.githubusercontent.com/102265620/232636680-10501fe8-3b86-416c-b615-c9983bbe850c.png" width="35" height="35"/>
Como Testar
</h3>
<h4>
<img src="https://user-images.githubusercontent.com/102265620/231886670-84bbf853-61da-4e86-9e84-ed339e0869bb.png" width="20" height="20"/> Link da Documentação via Postman:
<br></br>
https://documenter.getpostman.com/view/24755055/2s93CHuFMw
<br></br>
- Com o Postman instalado em seu computador, basta abrir a documentação e clicar no botão <img src="https://github.com/RenatoAlexandrini/LabenuSystem/assets/102265620/b4329b29-60d4-4ed4-8f94-0ca08cc866a9" width="170" height="50" align="center"/>  para testar diretamente no Postman.
<br></br>
</h4>
<h4>
<img src="https://github.com/RenatoAlexandrini/ProjetoCookenu/assets/102265620/ea3f9c49-cd5e-4026-ace1-81ce8fdb7bd3" width="30" height="30" align="center"/> Para testar localmente:
</h4>


```
- inicie o Git Bash em uma pasta e digite:
- git clone https://github.com/RenatoAlexandrini/ProjetoCookenu
- npm install
- npm run migrations
- npm run start
- Em cada endpoint, substitua o "https://projeto-jemison-cookenu3.onrender.com" por "http://localhost:3003"
```
<hr>

<h2>
<img src="https://user-images.githubusercontent.com/102265620/232643560-015f8d46-4ebb-4780-85ec-ada1d05253e4.png" width="40" height="40"/> Endpoints:
<br></br>
</h2>

<h3>
<img src="https://user-images.githubusercontent.com/102265620/232646417-9dc71130-9b80-4fc4-9f48-62517f79b372.png" width="30" height="30"/> Criar um Usuário/SignUp:
</h3>
<h5>
Este Endpoint cria um novo usuário a partir dos dados recebidos através do "body".

O nome não possui nenhuma restrição

O email passa por duas verificações, primeiramente é verificado se o dado possúi formato padrão de email com "nome@conta.com" e então é verificado se o email já foi cadastrado anteriormente.

A senha precisa conter no mínimo 8 caracteres, entre eles deve existir pelo menos uma letra maiúscula, uma minúscula, um número e um caracter especial(!@#$%).

A "Role" da conta, precisa ser uma opção entre admin ou normal, sendo que, no caso de não ser adicionada nenhuma role, por padrão a conta é criada como normal.

O retorno deste endpoint é composto por: uma mensagem de sucesso, as informações do usuário criado, para facilitar a visualização e o token de validação, que será utilizado no restante dos endpoints.
</h5>

<h3>
<img src="https://user-images.githubusercontent.com/102265620/232647261-94482392-bdc9-4ab1-91b7-d5946947ea5b.png" width="30" height="30"/> Login :
</h3>
<h5>
Este endpoint cria um token de autenticação através de um email e uma senha recebidos através do "body".

Primeiramente é feita uma verificação para saber se o email existe no banco de dados e então uma verificação para saber se a senha combina com a criada pelo usuário.

O retorno deste endpojnt é apenas o token de autenticação que deverá ser utilizado no restante dos endpoints.
</h5>

<h3>
<img src="https://user-images.githubusercontent.com/102265620/232647856-5f53ca35-04b9-4993-9f1f-b65258582000.png" width="30" height="30"/> Buscar o perfil do Usuário:
</h3>
<h5>
Este endpoint retorna o perfil do usuário que está logado no momento, portanto ele precisa apenas do token de autenticação do usuário passado através do "headers"

O retorno deste endpoint são os dados da conta do usuário sem a senha.
</h5>

<h3>
<img src="https://user-images.githubusercontent.com/102265620/232647745-6860e5e3-d823-4819-88cb-3bf801929b03.png" width="30" height="30"/> Buscar o perfil de outors Usuários:
</h3>
<h5>
Este endpoint retorna o profile de qualquer outro usuário, onde o ID deste usuário deverá ser recebido através do "params"

É obrigatório o envio de um ID e não é possível receber o perfil do próprio usuário que esta validado através do token.

O retorno deste endpoint são as informações da conta de um usuário, sem a senha.
</h5>

<h3>
<img src="https://user-images.githubusercontent.com/102265620/232648758-1e93732a-fdf4-4a14-beb2-974bd4028b3a.png" width="30" height="30"/> Criar um Post de Receita :
</h3>
<h5>
Este endpoint cria uma nova receita tendo o usuário autenticado como autor.

Ele recebe um token de autenticação através do "headers" e deverá receber o restante dos dados através do "body"

Um título, que será verificado se já existe uma receita com o mesmo nome

E um Modo de preparo, que não possuí nenhum tipo de restição.

O retorno deste endpoint é composto por uma mensagem de sucesso e os dados da receita para facilitar a vizualização.
</h5>

<h3>
<img src="https://user-images.githubusercontent.com/102265620/232648820-59f7fc0d-7889-4d84-99da-d3736b96fc6c.png" width="30" height="30"/> Buscar um Post de Receita:
</h3>
<h5>
Este endpoint retorna os dados de uma receita, onde o ID deverá ser recebido através do "params" e um token de autenticação deverá ser recebido através do "headers"

Este endpoint retorna os dados da receita junto com o nome o ID do autor da receita.
</h5>

<h3>
<img src="https://user-images.githubusercontent.com/102265620/232648962-717c8bd6-f56d-4678-8f38-bb9a9777608c.png" width="30" height="30"/> Atualizar um Post de Receita:
</h3>
<h5>
Este endpoint atualiza os dados de uma receita, sendo necessários para essa alteração:

Um token de autenticação que deverá ser recebido através do "headers"

O ID de uma receita que deverá ser recebido através do "params"

Um novo título para a receita e/ou um novo modo de preparo para a receita, recebidos através do "body". Sendo obrigatório pelo menos uma, entre esseas duas opções e no caso do novo título, mesmo se houver apenas ele para atualizar ou ele estiver junto com uma nova descrição, ele passará por uma verificação se há uma receita com mesmo nome.

As contas de Administrador, podem alterar qualquer receita, enquanto as contas Normais, podem alterar apenas as receitas de própria autoria.

O retorno deste endpoint é composto por uma mensagem contendo a descriçao de tudo que foi alterado.
</h5>

<h3>
<img src="https://user-images.githubusercontent.com/102265620/232649356-d38bb05e-347e-4f22-9830-67c4f7a03bb0.png" width="30" height="30"/> Deletar um Post de Receita:
</h3>
<h5>
Este endpoint deleta uma receita recebendo seu ID através do "params"

Uma conta de Administrador, poderá deletar qualquer receita, enquanto uma conta Normal só poderá deletar uma receita de autoria própria.

O retorno deste endpoint é uma mensagem indicando o nome da receita deletada.
</h5>

<h3>
<img src="https://user-images.githubusercontent.com/102265620/232649828-a09604c3-1b66-4375-a07c-9f7184327850.png" width="30" height="30"/> Buscar o Feed de um usuário:
</h3>
<h5>
Este endpoint utiliza o ID retirado do token de autenticação, recebido através do "headers", para criar um feed com as receitas postados pelos usuários que a conta segue, ordenado por ordem de criação das receita.
</h5>

<h3>
<img src="https://user-images.githubusercontent.com/102265620/232650136-3358df91-9878-4c36-8b31-7de3d21402fc.png" width="30" height="30"/> Seguir um usuário:
</h3>
<h5>
Este endpoint cria uma relação de seguir um outro usuário.

Recebendo através do "headers" um token de autenticação, de onde será retirado o ID do usuário.

E também o ID do usuário a ser seguido, recebido através do "body", onde serão feitas as verificação:

Se existe um usuário com este ID,

Se o ID recebido pelo "body" não é igual ao ID retirado do token

E se a conta já segue o usuário da solicitação.

este endpoint retorna uma mensagem de sucesso com a relação criada para facilitar a vizualização.
</h5>

<h3>
<img src="https://user-images.githubusercontent.com/102265620/232650198-d0910f0c-8541-4179-a7a7-2cc926280816.png" width="30" height="30"/> Deixar de seguir um usuário:
</h3>
<h5>
Este endpoint deleta uma relação de seguir um outro usuário.

Recebendo através do "headers" um token de autenticação, de onde será retirado o ID do usuário.

E também o ID do usuário que deseja deixar de seguir, recebido através do "body", onde serão feitas as verificação:

Se existe um usuário com este ID,

Se o ID recebido pelo "body" não é igual ao ID retirado do token

E se a conta realmente segue o usuário da solicitação.

este endpoint retorna uma mensagem de sucesso da remoção desta relação.
</h5>

<h3>
<img src="https://user-images.githubusercontent.com/102265620/232650447-65b161a6-7a6f-4b42-acab-6cef96c012e0.png" width="30" height="30"/> Deletar uma conta:
</h3>
<h5>
Este endpoint deleta a conta de um usuário e todas as relações que ele possui no banco de dados.

Ele deve receber um token de autenticação através do "headers" e o ID do usuário a ter a conta deletada, através do "params", então haverá uma verificação se o usuário existe no banco de dados.

Uma conta Administradora, poderá deletar qualquer outra conta de usuário, enqunato uma conta Normal poderá apenas excluir sua própria conta.

Este endpoint retorna uma mensagem de sucesso da remoção da conta com o nome e o ID da conta deletada, para facilitar a vizualização.
</h5>

<h3>
<img src="https://user-images.githubusercontent.com/102265620/232650828-ecf267c3-1b57-40ca-afba-6b936ea72e81.png" width="30" height="30"/> Esqueci minha senha:
</h3>
<h5>
Este endpoint para funcionar corretamente, deveria enviar um link com uma página feita em frontend que levaria ao endpoint de trocar a senha do usuário, sem precisar de nenhum tipo de autenticação, desta forma, ao usuário entrar na conta de email enviada, estaria provando que a conta realmente é sua e poderia trocar a senha.

Porém para conseguirmos testar este endpoint, a senha é trocada automaticamente e enviada para o email recebido através do "body".

Desta forma é possível ao menos testar este recurso do Projeto, porém não seria funcional em um ambiente real, tendo em vista que qualquer usuário conseguiria trocar a senha de outro usuário apenas sabendo o email cadastrado. Mesmo não tendo acesso ao email, poderia gerar trocas de senhas sem a solicitação do próprio dono da conta.

Este endpoint retorna uma mensagem confirmando o envio do email e a partir deste momento, o usuário precisa entrar em seu email e pegar a nova senha para realizar o login.
</h5>


<hr>
<h3>
<img src="https://user-images.githubusercontent.com/102265620/232651622-0bd6e78e-623d-4a62-af0e-2a589b0deda1.png" width="40" height="40"/> Técnicas e tecnologias utilizadas
<br></br>

- ``Typescript`` <img src="https://user-images.githubusercontent.com/102265620/230519766-2b4903ad-94f7-48e7-b949-4fc981ee519d.png" width="19" height="19"/>
- ``SQL`` <img src="https://user-images.githubusercontent.com/102265620/230519864-6ee2f9d0-1377-4528-a6a1-2b19b5b75d5e.jpg" width="22" height="22"/>

</h3>
<hr>
<h3>
<img src="https://user-images.githubusercontent.com/102265620/232651717-cb1347d1-7e7a-4c02-af16-93b83f8d4d33.png" width="35" height="35"/>Autores:
</h3>

| [<img src="https://avatars.githubusercontent.com/u/99742656?v=4" width=115><br><sub>Leonardo Mizuki Koga</sub>](https://github.com/leokoga) | [<img src="https://avatars.githubusercontent.com/u/102482348?v=4" width=115><br><sub>Rhuan Victor</sub>](https://github.com/rhuanvictor1)  | [<img src="https://avatars.githubusercontent.com/u/102265620?v=4" width=115><br><sub>Renato Alexandrini</sub>](https://github.com/RenatoAlexandrini) |
| :---: | :---: | :---: 
