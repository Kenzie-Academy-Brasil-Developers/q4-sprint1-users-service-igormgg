# <b> Users Service API </b>

## <b> 🌐 URL base da API </b>

Essa API foi feita apenas para rodar localmente na porta 3000. Você pode mudar essa porta manualmente no código. <br>
URL base: http://localhost:3000

## <b> 🛠 Tecnologias utilizadas </b>

#### Framework

- Express.js

#### Libraries

- bcrypt <br>
- dotenv <br>
- jsonwebtoken <br>
- uuid <br>
- yup <br>
- nodemon

<br>

## 🛠 Instalação

<p>Caso queira instalar a API para rodar os testes localmente em sua máquina, siga os seguintes passos:</p>

1 - Rode o comando yarn install na raíz do projeto

```sh
$ yarn intall
```

2 - Em seguida, ainda no terminal, inicie a aplicação nodemon:

```
$ yarn dev
```

<br>

## <b> 🌄 Inicialização da API </b>

Para começar a utilizar a API, copie a URL base da aplicação e use-a na sua ferramenta cliente de API de preferência (recomendo o Insomnia), complementando a URL com os endopints da aplicação, explicados a seguir.

<br>
<hr>
<br>

<br>

## <b> 🔚 Endpoints </b>

Existem 4 endpoints nessa aplicação: 3 para gerenciamento de usuários, e 1 para login.

<br>

<br>

## <b> > Usuário </b>

<br>

### <b> Registro </b>

<i> POST /signup </i>

Essa rota serve para registrar um novo usuário no banco de dados, sendo obrigatório passar no corpo da requisição o username, email, age e password do usuário a registrar. <br>
Exemplo de requisição:

```json
{
  "age": 18,
  "username": "daniel",
  "email": "daniel@kenzie.com",
  "password": "abcd"
}
```

Dessa requisição é esperado um retorno com os dados do usuário cadastrado, como mostrado a seguir:

```json
{
  "uuid": "5f6fd342-3f7e-45d4-a836-3a2838f1b3e9",
  "createdOn": "2022-03-16T02:18:53.029Z",
  "email": "daniel@kenzie.com",
  "age": 18,
  "username": "daniel"
}
```

<br>

### <b> Listagem </b>

<i> GET /user </i>

Essa rota é usada para obter um array com todos os usuários cadastrados no banco de dados. <br>
Aqui não é necessário passar nenhum dado no corpo da requisição, apenas uma autorização do tipo bearer token no header, obtida no login do usuário. <br>
Exemplo de resposta dessa rota:

```json
[
  {
    "uuid": "5f6fd342-3f7e-45d4-a836-3a2838f1b3e9",
    "createdOn": "2022-03-16T02:18:53.029Z",
    "email": "daniel@kenzie.com",
    "age": 18,
    "username": "daniel"
  }
]
```

<br>

### <b> Atualização de senha </b>

<i> PUT /user/:uuid/password </i>

Já essa rota pode ser usada para atualizar a senha do usuário que está logado, bastando passar no corpo da requisição a senha a ser atualizada, passar na URL a UUID do usuário logado, e passar no header uma autorização o bearer token do usuário logado, obtido no login. <br>
A requisição bem sucedida retorna a resposta 204, sem conteúdo. <br>
Exemplo de requisição:

```json
{
  "password": "abcde"
}
```

<br>

## <b> > Login </b>

<br>

### <b> Fazer login </b>

<i> POST /login </i>

Essa rota serve para fazer login de um usuário já cadastrado no banco de dados, sendo obrigatório passar no corpo da requisição o username, e senha do usuário. <br>
Exemplo de requisição:

```json
{
  "username": "daniel",
  "password": "abcd"
}
```

Dessa requisição é esperado um retorno com o token de acesso do usuário, como mostrado a seguir:

```json
{
  "token": "eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJ1c2VybmFtZSI6ImRhbmllbCIsInBhc3N3b3JkIjoiJDJhJDEwJDRtTEpwb3BPUi9xQkcwUlplQmRFWi41NFlmVEF4MnRDMjBYQXVLUGF4c3ZvcVFEWUQ3djk2IiwiaWF0IjoxNjQ3Mzk3MjE1LCJleHAiOjE2NDc0MDA4MTV9.k4j0iLFjSzH0LVeBVo9grtUmYy4vFafm9zOpvJauvys"
}
```
