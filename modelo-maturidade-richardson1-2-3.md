# Nível 1 - Recursos

- “No nível 1, passamos a usar recursos como forma de modelar e organizar a API. Neste nível não precisaremos conhecer a funcionalidade de cada método e sim apenas o recurso ao qual temos acesso.”

- “Modelando corretamente os recursos, precisamos usar os métodos HTTP da forma certa, para que a gente possa criar todas as interações necessárias sob um recurso.”

> No nível 1 dizemos que agora temos recursos!

<br><br>

# Nível 2 - Verbos HTTP

- “Nesse nível, o HTTP deixa de exercer um papel apenas de transporte e passa a exercer um papel semântico na API, ou seja, seus verbos passam a ser utilizados com o propósito no qual foram criados.”

- “A utilização do métodos mais conhecidos (GET, POST, PUT e DELETE), bem como a tratativa correta dos códigos de resposta, permitem a modelagem e interação com os recursos presentes em uma API.”

Enviando:
```HTML
POST /cliente
<Cliente>
<Nome>Manoel da Silva</Nome>
...
</Cliente>
```
Recebendo:
```
201 Created
Location: /cliente/1
```

- É importante notar 2 aspectos nessa resposta: O primeiro é a utilização correta da resposta “201 Created”. Como foi solicitado a criação de um recurso, nada mais adequado que uma resposta que informe que o recurso foi criado com sucesso.

- Além disso, um importante aspecto é a presença do header
“Location”. Esse header informa em qual endereço o recurso
criado se encontra disponível.

> No nível 2 dizemos que agora usamos os verbos HTTP de forma correta!

<br>

## Código de Status HTTP

```
https://developer.mozilla.org/en-US/docs/Web/HTTP/Status
```

<br><br>

# Nível 3 - HATEOAS

- HATEOAS (Hypermedia as the Engine of Application State)

- “Em seu blog pessoal, Fielding deixa muito claro que APIs que não utilizam HATEOAS não podem ser consideradas RESTful, mesmo assim, você vai encontrar muitos conteúdos sobre REST que nem ao menos cita essa característica.”

- “Apesar de aparentemente ser algo não muito familiar, HATEOAS é um conceito presente no dia a dia de todos os usuários da Web. Ele tem como elemento principal uma representação hypermedia, que permite um documento descrever seu estado atual e quais os seus relacionamentos com outros futuros estados.”

```HTML
GET /cliente/1
HTTP/1.1 200 OK
<Cliente>
    <Id>1</Id>
    <Nome>Manoel da Silva</Nome>
    <link rel="deletar" href="/cliente/1" />
    <link rel="notificar" href="/cliente/1/notificacao" />
</Cliente>
```

- “No exemplo, o cliente da API deverá entender o significado dos relacionamentos “deletar” e “notificar” para que ele consiga de fato consumir de forma adequada esses links.”

> No nível 3 dizemos que temos controles de hipermídia!

<br>

## RESUMO

- Nível 0 - Você não sabe nem mesmo usar o HTTP corretamente.
- Nível 1 - Agora você tem recursos.
- Nível 2 - Agora você saber usar os verbos HTTP corretamente.
- Nível 3 - Agora você usa controles de hipermídia.