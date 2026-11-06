# Scenario Outline
Indica que o scenario será executado com diferentes conjuntos de dados.

### Exemples
É a tabela que contêm os dados utilizados em cada execução.

### Variáveis entre sinais de maior e menor.
ex:
```
<email>
<senha>
<resultado>
 ```
Esses campos serão substituídos por palavras chaves.

## Como o cumcumber executará os testes?

*Cada linha da tabela representa uma execução independente.
Execuções esperadas*
## Exemplos##

1. maria@email.com
Senha: senha123
Esperado: Acesso permitido
Sucesso esperado

2. maria@email.com
Senha: errada
Esperado: Senha incorreta
Bloqueio esperado

3. E-mail vazio
Senha: senha123
Esperado: E-mail obrigatório
Bloqueio esperado

5. maria@email.com
Senha: Senha vazia
Esperado: Senha obrigatória
Bloqueio esperado


## Atenção: os quatro resultados são comportamentos esperados. O teste só será aprovado se o sistema apresentar exatamente o resultado esperado.
5. Qual a vantagem para QA?
- Evita repetição de cenários.
- Facilita testes com diferentes combinações de dados.
- Melhora a manutenção dos testes.
- Permite ampliar a cobertura de testes.
Mas cuidado: não devemos colocar tudo em um único Scenario Outline. Use-o quando os cenários compartilham o mesmo comportamento e a mesma sequência de passos.

