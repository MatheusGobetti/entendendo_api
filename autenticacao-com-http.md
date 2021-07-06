# Autenticação com HTTP

- Os mecanismos padrões de autenticação com HTTP são definidos como __Basic__ (básica) e __Digest__ (resumida).

- Esses dois mecanismos foram projetados seguindo as constraints REST, ou seja, eles são stateless.

- Nesses dois mecanismos o conjunto usuário/senha é incluído em cada requisição, codificado em __Base64__ para a autenticação __Basic__ e com um __hash MD5__ para a autenticação __Digest__.

- A definição do funcionamento da autenticação
em HTTP pode ser encontrada em:

```
https://datatracker.ietf.org/doc/html/rfc2617
```

- A documentação informa que para uma autenticação o cliente deve enviar o header __Authorization__ no seguinte formato:

```
Authorization: auth-scheme hashed-credentials
```

- Sendo assim, uma autenticação básica seria por exemplo:

```
Authorization: Basic am9objpwYXNz
```
```
https://en.wikipedia.org/wiki/Basic_access_authentication
```

- Para fazer uma requisição de autenticação básica HTTP via cURL teríamos:

```
curl -u jack:pass http://www.example.com
```

Já para autenticação HTTP do tipo Digest, teríamos: 

```
curl --digest -u jack:pass 
http://www.example.com
```

- Em retorno à requisição feita com o header Authorization, caso as credenciais não sejam autorizadas, o servidor deve retornar o status code __401 Unauthorized__ e setar o header __WWW-Authenticate__ com o __tipo de autenticação__ que deve ser usado e __qual o domínio__ (realm). 

```
WWW-Authenticate: Basic realm="Perfil"
```

- A diretiva de domínio __“realm”__ é opcional e
indica a proteção de um determinado espaço,
pois uma mesma aplicação pode-se ter
diferentes áreas protegidas usando diferente
esquemas de autenticação.

