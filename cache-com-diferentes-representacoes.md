# Cache com diferentes tipos de representação

- Pelo que vimos até agora, podemos fazer requisições para diferentes tipos de representação usando para isso o header __Accept__.

- Mas o que ainda não sabemos é que nosso browser, por padrão, usa o __método HTTP e a URI__ como chave para registrar respostas cacheadas, ou seja, mesmo que tenhamos várias representações diferentes, por se tratar do mesmo verbo HTTP e mesma URI, o browser ficará confuso de qual resposta deve fazer cache.

Exemplo:

```
curl http://www.mysite.com/users \
 -H "Accept: application/json"
```

```
curl http://www.mysite.com/users \
 -H "Accept: application/xml"
```

- Para resolver esse problema existe o header __Vary__, que permite indicarmos outros itens para a composição da chave do cache.

Exemplo:

```
curl http://www.mysite.com/users \
 -H "Accept: application/json"
```

```
HTTP/1.1 200 OK
Vary: Accept
Cache-Control: max-age=86400
Content-Type: application/json
Content-Length: 128
```

- Assim, nossa atual chave será: 
```
GET/users application/json
```
E isso permitirá que o browser faça o cache de todas as representações.

- A header Vary também pode informar mais de uma chave, por exemplo:

```
curl http://www.mysite.com/users \
 -H "Accept: application/json" \
 -H "Accept-Language: br" \
 -H "Accept-Encoding: gzip"
```

```
HTTP/1.1 200 OK
Vary: Accept, Accept-Language, Accept-Encoding
Cache-Control: max-age=86400
Content-Type: application/xml
Content-Language: br
Content-Encoding: gzip
Content-Length: 1024
```

Nesse caso, nossa chave seria:
```
GET/users application/xml:br:gzip
```

- Vary:

```
https://developer.mozilla.org/en-US/docs/Web/HTTP/Headers/Vary
```