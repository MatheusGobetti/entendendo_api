# Stateless Authentication

## __OAuth__ e __JWT__

<br>

### OAuth
   
```
https://oauth.net/
```

User to Server:

- Quero me cadastrar!
(Login/Senha)

Server to User:
- Tome esse token
(z627asie) e vá ao
facebook me autorizar!

User to Facebook:
- Quero autorizar o Mania de
Concurseiro com esse
token (z627asie)!

Facebook to User
- Ok! Autenticado! Devolva esse token (kad98y) ao Mania de Concurseiro!

User to Server:
- 'Mania de Concurseiro', consegui a autorização do facebook! Ele me passou esse token (kad98y), posso entrar no site?

Server to Facebook:
- Foi você quem gerou esse token (kad98y)?

Facebook to Server:
- Foi sim! Foi eu quem gerei o token!

Facebook to User:
- Ok! Você está autorizado a entrar no site!

## Benefício:
- É escalável!
- É Stateless mesmo?

## Leituras Extras:

```
https://scotch.io/tutorials/the-ins-and-outsof-token-based-authentication
```
```
http://www.kaleidos.net/blog/295/stateless-authentication-with-api-rest/
```

### JWT
   
```
https://jwt.io/
```

> JSON Web Token (JWT) is an open standard (RFC 7519) that defines a compact and self-contained way for securely transmitting information between parties as a JSON object.

<br>

- JWT Structure

    header | payload | signature
    <br>
    aaaaaaa.bbbbbbb.ccccccc
<br>
<br>

- Base64

```
http://www.motobit.com/util/base64-decoder-encoder.asp
```

- JWT
```
https://blog.imaginea.com/stateless-authentication-implementation-using-jwt-nginxlua-and-memcached/
```