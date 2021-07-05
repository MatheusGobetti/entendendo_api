# Métodos HTTP
- Existem __9 métodos__ os quais podemos utilizar
para a criação de uma API RESTful. Esse
conjunto de métodos possui a semântica de
operações possíveis de serem efetuadas sob um
determinado __recurso__.

- Na especificação original do HTTP existiam
apenas 3 métodos __(GET, POST, HEAD)__. Na
revisão 1.1 foram adicionados mais 5 verbos
__(OPTIONS, PUT, DELETE, TRACE e CONNECT)__. A
RFC 5789 estendeu o HTTP com um novo método
__PATCH__.

## GET

- O método GET é utilizado quando existe a
necessidade de se obter um recurso. Ele é
considerado __idempotente__, ou seja,
independente da quantidade de vezes que é
executado sob um recurso, o resultado sempre
será o mesmo.

Ex:
```
curl www.exemplo.com/cliente/1
curl -X GET www.exemplo.com/cliente/1
```

## POST

- Utilizado para a criação de um recurso a
partir do uso de uma representação.

Ex:

```
curl -X POST www.exemplo.com/cliente \
-H "Content-Type: application/json" \
-d '{"nome":"João"}'
```

## PUT

- O método PUT é utilizado como forma de
atualizar um determinado recurso.

Ex:

```
curl -X PUT www.exemplo.com/cliente \
-H "Content-Type: application/json" \
-d '{"nome":"João da Silva"}
```

## DELETE

- O DELETE tem como finalidade a remoção de um
determinado recurso.

Ex:

```
curl -X DELETE www.exemplo.com/cliente/1
```

## Resumindo:

- É tipo um CRUD:
    
    - POST - Create
    - GET - Read
    - PUT - Update
    - DELETE - Delete

## Métodos Extras

### HEAD

- O método __HEAD__ é muito parecido com o método __GET__, a única diferença é que o servidor não retornará o __“body”__ depois de receber a requisição.

Ex:

```
curl -I -v http://www.example.com/users
```

### PATCH

- O método PATCH faz __“modificações parciais nos recursos”__, ou seja, fazer a alteração de valores específicos de um recurso, ao invés de enviar todos os dados novamente.

- Enquanto o método PUT só permite a __“substituição”__ inteira do recurso, o PATCH permite __modificações parciais__.

Ex:

```
curl -X PATCH -v http://www.example.com/users/1 \
-H "Content-Type: application/json" \
-d '{"age":26}'
```

### OPTIONS

- O método OPTIONS é a forma que o cliente possui de perguntar ao servidor quais os requisitos para um determinado recurso.

- Por exemplo, o OPTIONS pode ser usado para saber quais métodos podem ser aplicados a um determinado recurso, ou qual a URL permitida para se comunicar com um determinado recurso.

```
curl -i -X OPTIONS http://www.example.com/users/1
```

### Access-Control-Allow-Methods

```
https://developer.mozilla.org/en-US/docs/Web/HTTP/Access_control_CORS#Access-Control-Allow-Methods
```

### OPTIONS Method

```
http://zacstewart.com/2012/04/14/http-options-method.html
```

### TRACE

- Ecoa de volta a requisição recebida para que o cliente veja se houveram mudanças e adições feitas por servidores intermediários.

### TRACE Vulnerabilidade

```
http://www.cgisecurity.com/questions/httptrace.shtml
```

### CONNECT

- Converte a requisição de conexão para um túnel TCP/IP transparente, usualmente para facilitar comunicação criptografada com SSL (HTTPS) através de um proxy HTTP não criptografado.