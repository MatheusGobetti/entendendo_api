# cURL
## cURL é uma __ferramenta de linha de comando__, utilizada para pegar ou enviar arquivos usando a sintaxe URL.

- Uma requisição cURL é composta da palavra __curl__ a qual você quer acessar, e um __conjunto de opções__ que permitem você modificar qualquer coisa na requisição que será enviada.

## Algumas opções do uso:

- __-H:__ H é um atalho para **H**eader. Essa opção permite adicionar ou substituir campos do cabeçalho HTTP.

Exemplo:

```
-H "Content-Type: application/json"
```

- __-d:__ É um atalho para **d**ata. Com essa opção vamos enviar dados para o servidor.

Exemplo com um payload JSON:

```
-d '{"name": "Matheus Gobetti"}'
```

- __-i__, __-include:__ Quando usamos esta opção, o cURL não mostrará apenas o corpo da resposta enviada do servidor, mas também o cabeçalho/HEADER.

Exemplo:

```
-i https://jsonplaceholder.typicode.com/posts/1
```

- __-I__, __-head:__ Esta opção diz ao cURL para fazer uma requisição do tipo HEAD que irá trazer apenas o cabeçalho do documento sem o corpo.

- __-X__, __-request:__ Esta opção não especifica qual o verbo HTTP que queremos usar. O padrão é o GET mas nós podemos usar também o POST, PUT, PATCH ou DELETE.

