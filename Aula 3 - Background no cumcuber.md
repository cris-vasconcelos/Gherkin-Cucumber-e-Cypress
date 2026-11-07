## O que é o background
O background serve para definir etapas que são comuns a todos os cenários de uma mesma funcionalidade.
Imagine que estamos testando um sistema bancário. Para acessar as funcionalidades, todos os cenários precisam começar com o usuário autenticado.

## Exemplo: Sem background precisaríamos repetir:
```
Feature: Operações bancárias

  Scenario: Consultar saldo
    Given que estou logada no sistema
    When acesso minha conta
    Then devo visualizar meu saldo

  Scenario: Consultar extrato
    Given que estou logada no sistema
    When acesso a opção de extrato
    Then devo visualizar minhas movimentações
```

*Observe que repetimos a etapa*
GIVEN que estou logado no sistema.

*Podemos evitar essa repetição usando o Background*

## Como fica com o Background

``` Feature: Operações bancárias

  Background:
    Given que estou logada no sistema

  Scenario: Consultar saldo
    When acesso minha conta
    Then devo visualizar meu saldo

  Scenario: Consultar extrato
    When acesso a opção de extrato
    Then devo visualizar minhas movimentações
```
### O que acontece ?
- O background é executado antes de cada cenário.
- O cenário de consultar saldo começa com o usuário logado.
- O cenário de consultar extrato também começa com o usuário logado.
- Não precisamos repetir a mesma etapa com todos os cenários.

## Atenção
*O background não substitui o GIVEN de cada cenário. Ele complementa os cenários com condições iniciais que são compartilhados.*

### Exemplos
Todos os cenários abaixo precisam começar com o usuário na página inicial da loja.

Temos dois cenários:
1. Pesquisar um produto.
2. Adicionar um produto ao carrinho.

```
*Feature: Operação de compras*

Background
Given estou na página inicial da loja

Scenario: Pesquisar produto
When digito o nome do produto no campo pesquisar
Then  o sistema exibe os resultados

Scenario: Adicionar o produto no carrinho
When adiciono o produto no carrinho
Then o sistema exibe a confirmação com a mensagem "Produto adicionado"
```

Scenarios 2
- Login com sucesso
- Login com senha incorreta

 ```
  *Feature: Acesso ao login*

Background
Given estou na tela de login

Scenario: Login com sucesso
When digito o email válido
And digito a senha válida
Then o sistema realiza o login e exibe a mensagem de sucesso.

Scenario: Login com senha incorreta
When digito o email válido
And digito a senha inválida
Then o sistema realiza não realiza o login e exibe a mensagem de credenciais inválidas.
```


