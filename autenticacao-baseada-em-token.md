# Autenticação Baseada em Token

- A autenticação baseada em token consiste em enviar o usuário/senha para o servidor e receber em troca um Token que será informado em cada requisição através da header Authorization.

```
curl http://www.example.com/login \
-i -d '{"email":"jack@jack.com", "password": "supersecret"}'
```

```
HTTP/1.1 200 OK
Content-Type: application/json
Content-Length: 51
Connection: keep-alive
Server: thin
{"access_token":"6afc7f5db9eaaf7eab"}
```

```
curl -i -H 'Authorization: Token 6afc7f5db9eaaf7eab' \ 
http://localhost:4567
```

- Geralmente essa é a escolha para o uso em Web APIs, mas ela não é considerada stateless pois o __servidor precisará armazenar o Token__ e isso caracteriza __“manter o estado”__.

- Mas qual a grande vantagem de ser stateless? Qual o mal de uma conexão stateful?

Assim, podemos enumerar:

1. Será necessário replicar os dados armazenados na medida em que se escala.
2. Quando tiver muitos clientes você precisará gerir muitos tokens.
3. Se cada cliente armazenado tiver mais de um token isso pode dobrar facilmente.

