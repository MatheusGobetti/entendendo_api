# Analisando uma Resposta HTTP

- Primeira requisição feita:

```
curl -i https://jsonplaceholder.typicode.com/posts/1
```

- O que o cURL mostra como resposta de uma requisição HTTP pode ser dividido em 4 partes:

1. __Start-Line__ (Linha de Início / Obrigatória)
2. __Header Fields__ (Cabeçalho de Campos / Pode ter 0 ou mais)
3. __Empty Line__ (Linha em Branco / Obrigatória)
4. __Message-Body__ (Corpo da mensagem / Opcional) 

- Portanto, apesar de todas as requisições terem respostas diferentes, pelo menos a linha inicial e a linha em branco existirão.

## Start-Line

- A Start-Line pode ser dividida em 2 partes: __Request-Line__ e  __Status-Line__, onde, no código abaixo, __HTTP/1.1__ é a __Request-Line__ que indica a versão do HTTP que foi usada, e o __200 OK__ que é a Status-Line representando que houve uma resposta.

```
HTTP/1.1 200 OK
```

## Header Fields

- Os Header Fields representam os __metadados__ da requisição e resposta HTTP. Eles contêm informações sobre como a __transferência dos dados__ deve ser manipulada.

    - __Content-Type:__ Informa como a representação é serializada.
    
    - __Content-Length:__ Informa o tamanho do corpo da mensagem e é indicado em octetos.

    - __X-Powered-By:__ Header Fields __não-oficiais__, por convenção começam com um __X__. No entanto, essa prática está em desuso pois existem diversos Header Fields oficiais, e devemos tentar usá-los antes de criar algum.<br>
    Mesmo assim, ao se criar um novo Header, atualmente, indica-se não começar mais com o __X__.
    ```
    https://developer.mozilla.org/en-US/docs/Web/HTTP/Headers
    ```
    ```
    https://stackoverflow.com/questions/3561381/custom-http-headers-naming-conventions
    ```
    - __Empty-Line__: A linha em branco serve apenas para delimitar o fim dos Header Fields e o início do corpo da mensagem.

    - __Message-Body:__ O corpo da mensagem contém os dados que foram enviados do servidor em resposta à requisição feita. Nesse caso temos hm JSON.

- Uma outra forma de fazer uma requisição é usando a opção __-v__, que faz com que o resultado seja mais verboso, mostrando de fato como ocorreu a requisição.

```
curl -v -i https://jsonplaceholder.typicode.com/posts/1
```
