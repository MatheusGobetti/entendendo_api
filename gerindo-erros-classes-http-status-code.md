# Gerindo Erros

- “Naturalmente, quando fazemos requisições RESTful, __receberemos como retorno um possível erro__, seja por falha no formato da requisição, seja por causas internas referentes ao servidor.”

- “Isso não significa que o retorno apresentado seja uma __mensagem clara__, que não deixa dúvidas sobre o que aconteceu de fato.”

- “Pois bem, o intuito da gerência de erros em APIs Restful é __informar ao requisitante__ uma __mensagem que retrate o que de fato ocorreu__. Mais do que isso, um __status code__ que não seja genérico e sim, __útil__.”

<br><br>

# Classes dos HTTP Status Code

### Existem 5 classes de HTTP Status Code. 
### São elas:

- __1xx Informacional__: Códigos começados com 1 são conhecidos como códigos informacionais. A maioria deles não são usados nos dias atuais.

- __2xx Success__: Esses códigos indicam que ouve sucesso no intercâmbio entre o servidor e o cliente.

- __3xx Redirection__: Os códigos 3xx indicam que cliente deve fazer uma ação adicional antes da requisição estar completa.

- __4xx Client Error__: Nesse caso, o código indica que existe algo errado com a requisição do cliente.

- __5xx Server Error__: O cliente enviou uma requisição válida, mas o servidor não foi capaz de processá-la com sucesso.

Veja detalhes de cada um dos possíveis Status Code:
```
https://httpstatuses.com/
```

<br>

## Exemplos
<br>

### Exemplo 01

- Uma API possui um recurso chamado __“users”__ que só tem disponível o verbo __GET__. Assim, fazemos a seguinte requisição e obtemos a resposta:

```
curl -i -X PUT http://example.com/users
HTTP/1.1 404 Not Found
```

- Apesar do status code retornar algo que é verdade __“404 Not Found”__, essa resposta não é a mais indicada, visto que existe o código __405 Method Not Allowed__, que nesse caso se encaixa perfeitamente.

```
curl -i -X PUT http://example.com/users
HTTP/1.1 405 Method Not Allowed
```

### Exemplo 02

- O cliente solicita uma representação (XML por exemplo) que não está disponível no servidor. O código que devemos usar para uma representação não disponível deve ser o __406 Not Acceptable__.

```
curl -i http://example.com/users -H "Accept: xyz/abc"
HTTP/1.1 406 Not Acceptable
```

### Exemplo 03

- O cliente envia uma requisição __POST__ com um __Content-Type__ não suportado pelo servidor, o mesmo deve retornar o código __415 Unsupported Media Type__.

```
curl -X POST -i http://example.com/users \
-H "Content-Type: application/fake" \
-d 'Weirdly Formatted Data'

HTTP/1.1 415 Unsupported Media Type
```

### Exemplo 04

- Uma requisição __POST__ é enviada ao servidor com um __JSON__ mal formatado. O retorno do servidor deve conter o status code __400 Bad Request__ e uma mensagem no corpo da resposta detalhando o erro.

- O código __400 Bad Request__ tem o propósito de indicar que o servidor não conseguiu entender a requisição por algum erro na sua sintaxe.

```
curl -X POST -i http://example.com/users \
-H "Content-Type: application/json" \
-d '{“name”: “Jhon”'

HTTP/1.1 400 Bad Request
{"message":"757: unexpected token at '{\"name\":\"Jhon\"'"}
```

### Exemplo 05

- Imagine uma requisição POST para criar um usuário em um site, mas, esse usuário já existe no BD. O que fazer?

- O servidor deve retornar um código __409 Conflict__, que tem a finalidade de indicar ao cliente que ele pode resolver um conflito e tentar uma nova requisição.

```
curl -X POST -i http://example.com/users \
-H "Content-Type: application/json" \
-d '{“email”: “jhon@example.com”}'

HTTP/1.1 409 Conflict
{"message":"Email jhon@example.com already exists on DB"}
```

### Exemplo 06

- Imagine uma requisição GET que tem o intuito de mostrar os dados de um determinado usuário, mas esse usuário não existe no BD, qual código devemos retornar?

- Um código que tem esse propósito é o __404 Not Found__. Ele informa que nada foi encontrado em uma URI específica, ou seja, nesse caso, não existe retorno para a pesquisa.

```
curl -i http://example.com/users/jhon
HTTP/1.1 404 Not Found
```

### Exemplo 07

- Uma requisição DELETE é enviada ao servidor para excluir um usuário, qual código devemos retornar? __204 No Content__.

- O código 204 No Content indica que a requisição foi completada com sucesso, mas que não existe nenhum conteúdo adicional para ser enviado para o cliente.

```
curl -i -X DELETE http://example.com/users/jhon
HTTP/1.1 204 No Content
```

### Exemplo 08

- Após apagar um usuário, o cliente volta a requisitar o mesmo com uma requisição GET. Nesse caso, o mesmo não existe mais, qual código devemos retornar?

- Inicialmente podemos usar o código __404 Not Found__, mas ele é muito genérico e caso a aplicação, do lado do servidor, consiga identificar quem aquele usuário solicitado já existiu no BD, podemos então retornar o código __410 Gone__.

- O código 410 Gone trás a ideia de que aquele recurso já existia e agora não existe mais.

```
curl -i -X DELETE http://example.com/users/jhon
HTTP/1.1 204 No Content
curl -i http://example.com/users/jhon
HTTP/1.1 410 Gone
```

