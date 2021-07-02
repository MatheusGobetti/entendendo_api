# REST
### O que é REST?
> "O termo transferência de estado representacional - REST foi introduzido e definido no ano de 2000 através de uma tese de PH.D do cientista Roy Fielding, um dos principais autores da especificação do protocolo HTTP"

 - O intuito geral desta tese era a __formalização de um conjunto de melhores práticas__ denominadas __constraints__" . 

 - Essas __constraints__ tinham como objetivo determinar __a forma na qual padrões como HTTP e URI deveriam ser modelados__, aproveitando de fato todos os recursos oferecidos pelos mesmos.
---
### Constraints

- #### Cliente-Servidor

    - A principal característica dessa constraint é __separar as responsabilidades__ de diferentes partes de um sistema.
    
    <br>

    - Essa divisão pode se dar de diversas formas, iniciando por exemplo com uma separação entre mecanismos de __interface do usuário__ e o __back-end__ de uma aplicação.
    
    <br>

    - Isso permite a evolução e __escalabilidade__ destas responsabilidades de __forma independente__.

- #### Stateless

    - Essa caracteríistica propõe que __cada requisição__ ao servidor __não deve ter ligação com requisições anteriores ou futuras__, ou seja, cada requisição deve conter todas as informações necessárias para que ela seja tratada com sucesso pelo servidor.

- #### Cache

    - Para uma melhor performance, um sistema REST deve __permitir__ que suas respostas sejam passíveis de __cache__.

- #### Interface Uniforme

    - Bastante esforço deve ser feito para que o sistema possua uma __interface modelada__ seguindo alguns padrões importantes.

    <br>

    - Quando se fala sobre uma interface, os elementos abaixo devem ser considerados:
        - Recursos
        - Mensagens autodescritivas
        - Hypermedia 

    <br>

    - Devemos pensar em criar uma interface que permita a __manipulação__ desses conceitos. Ex:

            ---- Cliente (Entidade) ----
                        |
                    (Operações)
                    - Criar
                    - Pesquisar
                    - Editar
                    - Deletar
              
- #### Sistema em Camadas

    - Com o intuito de permitir a escalabilidade necessária para grandes sistemas distribuídos, um sistema REST deve ter a capacidade de adicionar elementos intermediários e que sejam __totalmente transparentes__ para seus clientes.
        - Ex: Balanceador de Carga

- #### Código sob demanda

    - Código sob demanda é a única constraint REST __opcional__.

    <br>

    - A ideia é aumentar a __flexibilidade dos clientes__, como por exemplo um código Javascript que só é baixado quando uma determinada página é carregada.

    <br>

    - Apesar de ser algo interessante, essa prática __reduz a visibilidade__, por isso é uma prática opcional.