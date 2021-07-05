# RESTful
## O que é RESTful?

- No momento em que você estiver falando de uma __implementação__ que usa as mesmas características do REST, você deve usar RESTful.

- REST nada mais é que um conjunto de melhores práticas denominadas __constraints__.

- Ou seja, se temos uma API que não segue os princípios REST, teremos apenas uma API HTTP.

- Portanto, a API __RESTful__ é uma API que IMPLEMENTA os princípios REST.

## Representações

- ### As representações são o formato do qual a informação será devolvida para o cliente

- JSON / XML 

- #### Exemplo 1:

Requisição (para o servidor):
```
GET/cliente/1 HTTP/1.1
Accept: application/json
```
Resposta (para o cliente):

```
{"nome": "João da Silva"}
```
- #### Exemplo 2:
Requisição:
```
GET/cliente/1 HTTP/1.1
Accept: image/jpeg
```
Resposta:

```
{(imagem qualquer)}
```

