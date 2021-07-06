# Versionamento

- “Versionamento em APIs são amados por uns e odiados por outros”

- “Versionamento não faz parte das constraints REST, nem também do Modelo de Maturidade Richardson, mas é __indispensável__ para criar APIs que sofrem mudanças ao longo do tempo”

- Dessa forma, qual a melhor forma de versionar uma API?

- Existem algumas. São elas:

1. Subdomínio: api1.example.com/users
2. URL: example.com/v1/users
3. URL com paramâmetros: example.com/users?v=1
4. HTTP Header customizado: ```X-API-Version: 1```
5. Accept Header com Media Type customizado:
```Accept: application/vnd.myapi.v2+json```
6. Accept Header com opção de versão:
```Accept:application/vnd.myapi+json;version=2.0```

- Atualmente, __uma das mais usadas__ é o versionamento através de __URL__, por ser de fácil implementação, evitar erros por parte de programadores novatos, e permitir compartilhar URLs facilmente.

### Exemplos:

- Pagseguro
```
https://dev.pagseguro.uol.com.br/documentacao/pagamentos/pagamento-padrao
```

- Paypal
```
https://developer.paypal.com/docs/api/overview/
```

