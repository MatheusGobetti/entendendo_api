# Caching no Cliente

- Os objetivos do caching HTTP são __eliminar o envio de requisições__ o __máximo possível__, e caso uma requisição precise ser feita, __reduzir os dados de resposta__.

- O primeiro objetivo pode ser alcançado usando-se um mecanismo de expiração conhecido como __Cache-Control__, e o segundo é através do mecanismo de validação __ETag__ ou __Last-Modified__.

    - Mínimo de requisições: __Cache-Control__
    - Mínimo de dados nas respostas: __ETag__

## Prevenindo Requisições Inteiras

- A maneira mais rápida de fazer uma requisição HTTP é não enviá-la inteiramente.

- O header Cache-Control pode ser usado para definir uma política de cache para um recurso.

Exemplos:

    Cache-Control: max-age=3600
    Cache-Control: no-cache
    Cache-Control: private, max-age=86400

- __max-age__: Especifica em segundos quanto tempo o recurso pode ser cacheado. É interessante notar que esse cache também pode ser feito por intermediários, não só o browser em si.

- __private/public__: Define quem pode fazer o cache. __Public__ significa que qualquer um pode fazer o cache. __Private__ por sua vez indica que o cache só pode ser feito pelo browser, ou seja, os intermediários como os CDNs não podem fazer cache.

- __no-cache/no-store__: Essas duas diretivas se confundem mas, a __no-store__ informa a resposta não deve ser armazenada seja no browser ou em seus intermediários, já o __no-cache__ significa que a resposta pode ser cacheada mas não pode ser reusada sem antes checar o servidor. Ela pode ser combinada com um __ETag__ a que veremos a seguir.

Existem outras diretivas que podem ser
usadas, as mesmas podem ser encontradas em:
```
https://developer.mozilla.org/en-US/docs/Web/HTTP/Headers/Cache-Control
```

### Exemplo:

    curl -I http://g1.globo.com/
    curl -I http://www.uol.com.br/
    curl -I http://www.submarino.com.br/

