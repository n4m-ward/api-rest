# API de Games
Api de games feita com base em um curso de node.js
## Endpoints
### GET /games
Endpoint responsavel por retornar todos os games cadastrados no banco de dados.
#### Parametros
Nenhum
#### Respostas
#### OK! 200
Requisição bem sucedida, caso aconteça, a api ira retornar todos os games.
Exemplo de resposta:

```
[
    {
        "id": 23,
        "title": "Call of duty MW",
        "year": 2019,
        "price": 60
    },
    {
        "id": 65,
        "title": "Sea of thieves",
        "year": 2018,
        "price": 40
    },
    {
        "id": 2,
        "title": "Minecraft",
        "year": 2012,
        "price": 20
    }
]
```

#### Falha na autenticação! 401
significa que ocorreu uma falha no processo de autenticação da requisição
Motivos: Token invalido ou expirado!

```
{
    "err": "token invalido!"
}
```
### POST /auth
Endpoint responsavel por realizar o login
#### Parametros
```
{
    "email": "example@gmail.com",
    "password": "password"
}
```
#### Respostas
#### OK! 200
Requisição bem sucedida, caso aconteça, a api ira retornar o token de autenticação

Resposta: 

```
{
	"Token": "eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJpZCI6MSwiZW1haWwiOiJnYWJyaWVscGhwMDBAZ21haWwuY29tIiwiaWF0IjoxNjA1MDQwNjg1LCJleHAiOjE2MDUyMTM0ODV9.6racKLtrm8u-ntILE1zU99bO9GOc9LfwxKboe6QM-"
}
```


#### Falha na autenticação! 401
significa que ocorreu uma falha no processo de autenticação da requisição
Motivos: Email ou Senha incorretos

Ex:

```
{
	err: "Credenciais inválidas!"
}
```

#### Erro Interno do Servidor! 500
significa que ocorreu uma falha recorrente de um problema no servidor
Motivos: Timeout, erro na criação do token.

Ex:

```
{
	err:"Falha interna"
}
```

### GET /game/:id
Endpoint responsavel por realizar buscar um game em especifico
#### Parametros
Id

#### Respostas
#### OK! 200
Requisição bem sucedida, caso aconteça, a api ira retornar o game buscado

Resposta: 

```
{
        "id": 23,
        "title": "Call of duty MW",
        "year": 2019,
        "price": 60
    }
```


#### Not Found! 404
game nao encontrado
Motivo : id incorreto


#### Requisição invalida! 400
Motivos: id passado não é um numero


### PUT /game/:id
Endpoint responsavel por editar games
#### Parametros
Id

#### Respostas
#### OK! 200
Requisição bem sucedida, caso aconteça, a edição dos dados do game foi um sucesso


#### Not Found! 404
game nao encontrado
Motivo : id incorreto

#### Falha na autenticação! 401
significa que ocorreu uma falha no processo de autenticação da requisição
Motivos: Email ou Senha incorretos

Ex:

```
{
	err: "Credenciais inválidas!"
}
```


#### Requisição invalida! 400
Motivos: id passado não é um numero


### DELETE /game/:id
Endpoint responsavel por editar
#### Parametros
Id

#### Respostas
#### OK! 200
Requisição bem sucedida, caso aconteça, a deleção dos dados do game foi um sucesso

#### Falha na autenticação! 401
significa que ocorreu uma falha no processo de autenticação da requisição
Motivos: Email ou Senha incorretos

Ex:

```
{
	err: "Credenciais inválidas!"
}
```

#### Not Found! 404
game nao encontrado
Motivo : id incorreto


#### Requisição invalida! 400
Motivos: id passado não é um numero