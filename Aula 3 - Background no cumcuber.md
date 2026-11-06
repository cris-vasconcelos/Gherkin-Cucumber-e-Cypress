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
    Then devo visualizar minhas movimentações ```

*Observe que repetimos a etapa*
GIVEN que estou logado no sistema.

*Podemos evitar essa repetição usando o Background*

## Como fica com o Background
