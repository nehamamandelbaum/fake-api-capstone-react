## URL base da fake API: https://fake-api-isaude.herokuapp.com/

## Endpoints

### POST /register -> Cria um novo usuário.

#### Corpo da requisição:

```
{
      "name": "Nehama",
      "email": "email@email.com",
      "password": "123456",
      "dateOfBirth": "20/10/1989",
      "gender": "masculino",
      "cpf": "94743482982",
      "city": "Belo Horizonte",
      "state": "MG"
    }
```

#### Formato da resposta:

```
{
	"accessToken": "eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJlbWFpbCI6ImVtYWlsQGVtYWlsLmNvbSIsImlhdCI6MTY0NzQzNTc2OCwiZXhwIjoxNjQ3NDM5MzY4LCJzdWIiOiIzIn0.WwR93HlxKHAMoc7EjJU1AKFP6lnNuNE4y_bFsuXE1V8",
	"user": {
		"email": "email@email.com",
		"name": "Nehama",
		"dateOfBirth": "20/10/1989",
		"gender": "masculino",
		"cpf": "94743482982",
		"city": "Belo Horizonte",
		"state": "MG",
		"id": 3
	}
}
```

Possíveis erros: <br>

1. O email já existe
2. Está faltando email ou senha.

### POST /login

#### Corpo da requisição:

```
{
  "email": "olivier@mail.com",
  "password": "bestPassw0rd"
}
```

#### Formato da Resposta:

```
{
	"accessToken": "eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJlbWFpbCI6ImVtYWlsQGVtYWlsLmNvbSIsImlhdCI6MTY0NzQzNjY5MywiZXhwIjoxNjQ3NDQwMjkzLCJzdWIiOiIzIn0.YHRgcYf2JYK__h3CuQP3ILSYWep75ZoCEKJeF6rQVCM",
	"user": {
		"email": "email@email.com",
		"name": "Nehama",
		"dateOfBirth": "20/10/1989",
		"gender": "masculino",
		"cpf": "94743482982",
		"city": "Belo Horizonte",
		"state": "MG",
		"id": 3
	}
}
```

### POST /vaccines

Corpo da requisição:

Obs: é preciso passar o ID do usuário na requisição, assim como o token no header.

```
{
	"userId": 2,
	"name": "Covid-19",
	"manufacturer": "Osford",
	"lote": "2337593279",
	"applicationDate": "19/01/2022",
	"shot": 2,
	"location": "Araguari",
	"totalShots": 2,
	"nextShot": "20/04/2022"

}
```

Possíveis erros:
Pode estar faltando a propriedade userId ou o token no header.

### GET /vaccines

Deve-se passar o token no header e a resposta irá retornar um array com as vacinas daquele usuário.

### GET /vaccines/:id

Deve-se passar o id como parâmetro da URL, assim como o token no header e a resposta irá retornar a vacina buscada.

### PATCH /vaccines/:id

formato da requisição:

Obs: Deve-se passar no corpo da requisição as propriedades que deseja mudar, assim como o token no header.

```
{
	"manufacturer": "Pfizer"
}
```

Formato da resposta:

Retorna o objeto vacina com a alteração feita.

```
{
	"userId": 2,
	"name": "Covid-19",
	"manufacturer": "Pfizer",
	"lote": "2337593279",
	"applicationDate": "19/01/2022",
	"shot": 2,
	"location": "Araguari",
	"totalShots": 2,
	"nextShot": "20/04/2022",
	"id": 2
}
```

### DELETE /vaccines/:id

Deve-se passar o id da vacina que deseja deletar como parâmetro da url, assim como o token no header.

Caso dê certo não retorna nenhuma resposta, apenas status 200.
