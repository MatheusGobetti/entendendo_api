# ETag

- Até agora vimos como prevenir requisições usando o header Cache-Control, mas infelizmente na maior parte das APIs web isso é raramente possível.

- Uma outra forma de ganhar tempo e largura de banda é usando o header ETag.

- ETag vem de __Entity Tag__ e destina-se a assegurar um token de validação identificando uma versão específica de uma resposta.

- Em um primeiro momento um cliente faz a requisição de um recurso ```(/users/jackson)```, na resposta o servidor inclui o token atual ```(“12345”)``` na header ETag.

Exemplo:

```
curl http://www.example.com/users/jackson
HTTP/1.1 200 OK
Content-Length: 2048
ETag: "12345"
[DATA]
```

- Em um segundo momento o cliente envia uma nova requisição para ```/users/jackson ``` e inclui o token ETag recebido no header __If-None-Match__.

- Quando a requisição é recebida pelo servidor, ele checa o valor do header __If-None-Match__ e compara com o ETag atual.

- Se forem iguais, não houve mudança e ele pode retornar um status code __304 Not Modified__, do contrário pode retornar um __202 OK__ com a nova representação.

```
curl http://www.example.com/users/jackson \
-H 'If-None-Match: "12345"'
HTTP/1.1 304 Not Modified
ETag: "12345"
```

```
curl http://www.example.com/users/jackson \
-H 'If-None-Match: "12345"'
HTTP/1.1 200 OK
Content-Length: 2048
ETag: "6789"
[DATA]
```

- É importante lembrar que o token ETag pode ter uma representação de letras e números, como por exemplo um __HASH__.

- Por outro lado, um hash ao ser calculado tem um custo computacional considerável, então, caso o recurso seja atualizado diversas vezes, talvez ele não seja a melhor solução.

- Contrapondo ao hash, é possível usar a data da última atualização __(timestamp)__ do recurso para verificar se o mesmo encontra-se desatualizado.

- Para esses casos o melhor é usar a header __Last-Modified__ associado à header __If-Modified-Since__, seguindo a mesma lógica do ETag.

Exemplo:

```
curl http://www.example.com/users/jackson
HTTP/1.1 200 OK
Content-Length: 2048
Last-Modified: Sun, 29 Apr 1998 05:00:00 GMT
[DATA]
```

```
curl http://www.example.com/users/jackson \
-H 'If-Modified-Since: Sun, 29 Apr 1998 05:00:00 GMT'
HTTP/1.1 304 Not Modified
Last-Modified: Sun, 29 Apr 1998 05:00:00 GMT
```

```
curl http://www.example.com/users/jackson \
-H 'If-Modified-Since: Sun, 29 Apr 1998 05:00:00 GMT'
HTTP/1.1 200 OK
Content-Length: 2050
Last-Modified: Mon, 30 Apr 1998 06:00:00 GMT
[DATA]
```

- ETag
```
https://developer.mozilla.org/en-US/docs/Web/HTTP/Headers/ETag
```
- If-None-Match
```
https://developer.mozilla.org/en-US/docs/Web/HTTP/Headers/If-None-Match
```

- Deve-se lembrar ainda que existem outros headers que podem ser usados para criar requisições HTTP __condicionais__.

```
https://developer.mozilla.org/en-US/docs/Web/HTTP/Conditional_requests
```
