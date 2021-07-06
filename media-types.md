# Media Types

- “Media Type é uma string que define qual o formato do dado e como ele deve ser lido pela máquina. Isso permite um computador diferenciar entre JSON e XML, por exemplo.”

- “Alguns exemplos de Media Types são:”
   - application/json
   - application/xml
   - multipart/form-data
   - text/html

## application/xml 

- “Um media type é composto por duas partes separada por uma barra. A primeira parte refere-se ao tipo e a segunda ao subtipo. Também é possível especificar alguns parâmetros adicionais, como por exemplo o __charset=UTF-8.__”

- “A primeira parte contém um tipo registrado
de alto nível, que pode ser:”
    - application 
    - audio
    - example 
    - image
    - message
    - model 
    - multipart
    - text 
    - video

```
https://www.iana.org/assignments/media-types/media-types.xhtml
```

- “Para informar o media type, usamos o header field __Accept__ no momento da requisição”

```
mockbin.org

curl mockbin.org/request -H "Accept: application/json"
curl mockbin.org/request -H "Accept: application/xml"
```

- “O header field Accept não se limita apenas a um valor, pode-se também encadear outros tipos em uma mesma requisição, bastando para isso separá-las por vírgula.

```
curl mockbin.org/request -H "Accept: application/json;q=0.5,application/yaml;q=0.1"
```

- “O parâmetro __q__ define __quality factor__, que informa a ordem preferida de retorno da requisição. Esse parâmetro deve estar no intervalo de __0__ a __1__, sendo 1 o de maior prioridade”

```
curl mockbin.org/request -H "Accept: application/json;q=0.5, application/yaml;q=0.1"
```

## Media Type vs MIME Types

```
https://developer.mozilla.org/en-US/docs/Glossary/MIME_type
```

## Content-Type vs Accept

- É comum a confusão entre os campos Content-Type e o Accept, mas devemos saber que o Content-Type é o campo que identifica o conteúdo da requisição, ou seja, em uma requisição __POST__, o formato dos dados envidados deve ser indicado no __Content-Type__, já o __Accept__, informa o tipo de retorno do servidor.