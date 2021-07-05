# Safe Methods

- Safe Methods são métodos que são considerados __“salvos”__. Eles não fazem nenhum efeito de qualquer um dos lados (cliente/servidor).

- Você até pode implementar algo para quando um safe method for chamado, como por exemplo atualizar o contador de um usuário, mas, o cliente não pode ser o responsável por essa alteração.

- Os safe methods são: GET e HEAD
<br><br>

# Métodos Idempotentes

- Idempotência é uma propriedade de algumas operações matemáticas e da ciência da computação, que quando “rodadas” múltiplas vezes o resultado não será alterado depois da primeira vez.

- Ou seja, o impacto de enviar 10 requisições HTTP para um método idempotente será o mesmo de se enviar apenas uma única requisição.

- Os métodos idempotentes são: __GET, HEAD, PUT, DELETE, OPTIONS e TRACE__.