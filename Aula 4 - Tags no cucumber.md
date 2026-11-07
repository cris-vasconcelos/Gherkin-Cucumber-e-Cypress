# Tags no cucumber
As tags servem para organizar, identificar e selecionar cenários de teste.

### Exemplo
Feature com 10 cenários: Alguns testan login, outros cadastros e outros recuperação de senha.
Como identificar os testes de regressão ? Ou quais os testes críticos?
*Aí que entram as tags.*

### 1. Como utilizar as tags?
- As tags começam com um **@** e são colocadas antes de uma feature ou de um scenario.

  Exemplo prático.
  ```
  Feature login de usuário

  @lgin @regressão
  Scenario: Login com credenciais válidas
  - Given que estou na página de login
  - When informo meu e-mail válido
  - And informo minha senha correta
  - And clico no botão entrar
  - Then devo visualizar a página inicial

  @login @negativo
  Scenario: login com senha incorreta
  - Given que estou na página de login
  - When informo meu e-mail válido 
  - And informo minha senha incorreta
  - And clico no botão entrar
  - Then devo visualizar a mensagem "Senha incorreta"
  ```
  **Observe**
  - @login: indetifica os testes relacionados ao login
  - @regressão: identifica um testes que faz parte da regressão
  - #negativo: identifica um cenário de testes negativos.

  ## Posso utilizar várias tags?
  SIM, um cenário pode ter várias tags.

     *Exemplo*
```
@login @regressao @critico
Scenario: Login com credenciais válidas
```
Nesse caso, o cenário pertence aos três grupos.
Também podemos colocar uma Tag antes da Feature:

  ```
@regressao
Feature: Login de usuário

```
Nesse caso, todos os cenários da Feature herdam essa Tag, além das tags individuais.
## 2. Para que serve na Automação?
Imagine se seu projeto possui 500 cenários automatizados.
Você pode organizar a execução para selecionar apenas os cenários com determinada TAG.

## Exemplos

**Tag**        **Finalidade**
- @smoke	        Testes básicos para verificar se o sistema funciona
- @regressao	    Testes de regressão
- @login	        Testes relacionados ao login
- @critico	      Funcionalidades críticas
- @negativo	      Testes de comportamento inválido

### Exercício prático
Loja virtual com três cenários:
- Login com sucesso.
- Login com senha incorreta.
- Cadastro de um novo usuário.

  ```
  @smoketest @critico
  Feature: Login de usuário

  @positive 
  Scenario:Login com sucesso
  - Given que estou na página de login
  - When informo meu e-mail válido
  - And informo minha senha correta
  - And clico no botão entrar
  - Then devo visualizar a página inicial


  @negative
  scenario:Login com senha incorreta
  - Given que estou na página de login
  - When informo meu e-mail válido 
  - And informo minha senha incorreta
  - And clico no botão entrar
  - Then devo visualizar a mensagem "Senha incorreta"

 @smoketest @critico @positivo 
 Feature: Cadastro de usuários
 
   scenario:Cadastro de novo usuário
  - Given que estou na página de cadastro
  - When preencho todos os campos obrigatórios
  - And clico no botão cadastrar
  - Then devo visualizar a mensagem "Usuário cadastrado"
   ```
  ### Para fixar
- @positivo: verifica comportamentos esperados com dados válidos.
- @negativo: verifica como o sistema reage a dados ou situações inválidas.
- @smoketest: identifica testes básicos para verificar se as funcionalidades principais estão operacionais.
- @regressao: identifica testes para verificar se alterações não prejudicaram funcionalidades existentes.
