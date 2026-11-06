# Conhcendo o GIVEN, THAN E WHEN

## Essas três palavras são estruturas básica de muitos cenários GHERKIN.
- **GIVEN (dado):** Apresenta a condição inicial.
- **When  (Quando):** Descreve a ação executada.
- **Then (Então):** Descreve o resultado esperado.


## Exemplo

```Feature login
  Scenario: Login com sucesso
   Given que estou na página de login
   When informo meu usuário e senha válida
   And clico no botão entrar
   Then devo visualizar a página inicial
```
  ### Também temos:
  - And: acrescenta outro condição ou ação.
  - But acrescenta uma condição de contraste.

## Exemplo 2 sucesso
* O sistema deve permitir que um usuário acesse sua conta quando informar e-mail e senha válidos.*

  ## Feature Acessar conta do email
```Scenario: credenciais válidos
   Given estou na página de login
   When informo meu usuário e senha válida
   And clico no botão entrar
   Then devo visualizar a página inicial
   And visualizar meu nome de usuário
```
## Exemplo 3 unhappy
**Requisito:** o sistema deve impedir o acesso quando a senha estiver incorreta e apresentar uma mensagem de erro.
  
```Scenario: credenciais inválidos
   Given estou na página de login
   When informo meu email válido
   And informo minha senha incorreta
   And clico no botão entrar
   Then o sistema não permitir o login
   And devo visualizar a mensagem de senha incorreta
```
## Exemplo 4 unhappy
**Requisito:** O usuário tenta entrar no sistema sem preencher o campo de e-mail.
```Scenario: Campo de email não informado
   Given estou na página de login
   When deixo o campo email vazio
   And informo minha senha correta
   And clico no botão entrar
   Then o sistema não permitir o login
   And devo visualizar a mensagem "email obrigatório"
```
