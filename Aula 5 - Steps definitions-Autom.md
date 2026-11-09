# Steps definitions
## 1. O que são Steps definitions ?
Steps Definitions são códigos (JS) que dizem ao Cypress o que ele deve fazer quando encontra uma instrução escrita em Gherkin

## 2. Como funciona essa ligação ?
Gherkin      JS
- Given    - Given() 
- When     - When()
- Then     - Then()
- And      - Usa a definição correspondente a etapa.

## 3.Transformando nosso cenário em código.

Ex: *Features/login.feature*

```
Feature: Login de usuário

  Scenario: Login com sucesso
    Given que estou na página de login
    When informo meu e-mail válido
    And informo minha senha correta
    And clico no botão entrar
    Then devo visualizar a página inicial
```
Agora vamos criar outro arquivo.
*features/step_definitions/login.js*

```
import { Given, When, Then } from "@badeball/cypress-cucumber-preprocessor";

Given("que estou na página de login", () => {
    cy.visit("/login");
});

When("informo meu e-mail válido", () => {
    cy.get('[data-testid="email"]').type("maria@email.com");
});

When("informo minha senha correta", () => {
    cy.get('[data-testid="senha"]').type("senha123");
});

When("clico no botão entrar", () => {
    cy.get('[data-testid="entrar"]').click();
});

Then("devo visualizar a página inicial", () => {
    cy.url().should("include", "/home");
});
```

## Entenda o que cada um faz:

- **cy.visit()** |     **-	Acessa uma página**
    - cy.get()	 |      Localiza um elemento
    - .type()    |      Digita um conteúdo
    - .click()	 |      Clica em um elemento
    - .should()	 |      Faz uma validação

Observe esta linha:
``` cy.get('[data-testid="email"]').type("maria@email.com"); ```


Ela significa:
1. Localizar o campo de e-mail.
2. Digitar maria@email.com.
   
E nesta:
```
cy.url().should("include", "/home");
```
Verifica se a URL contém /home.

### Exemplo 2
```
Given ("Estou na página iniciar", () => {
  cy.visit ("/login");
  });
  
When ("Informo meu email", () => {
  cy.get ('[data-testing="email"]).type("cris.@teste.com')
});
When ("Informo minha senha",() => {
  cy.get ('[data-testid="senha"]').type("senha123")
});
Then ("clico no botão entrar",() =>{
 cy.get('[data-testid="entrar"]').click();
});
Then("Devo visualizar a página inicial",() => {
  cy.url().should ("include", "/home");
}];
```

- cy.url() captura a URL atual do navegador.
- .should() realiza uma verificação.
- "include" indica que queremos verificar se existe determinado conteúdo.
- "/home" é o trecho esperado na URL.

*Observação, esse trecho de código é didático*

## Curiosidades
*Você pode utilizar And, When e Then várias vezes. A escolha depende da função de cada etapa, não de uma quantidade obrigatória.*

### 1. Qual é a diferença?
- Given: estabelece a condição inicial do teste.
- When: descreve uma ação realizada pelo usuário.
- Then: descreve o resultado esperado.
- And: acrescenta outra etapa, mantendo o sentido da etapa anterior.
  
### 2. Veja um exemplo de login
```
Feature: Login de usuário

  Scenario: Login com sucesso
    Given que estou na página de login
    When informo meu e-mail válido
    And informo minha senha correta
    And clico no botão entrar
    Then devo visualizar a página inicial
    And devo visualizar meu nome de usuário
```
### Observe:
Etapa	Função
- Given	Define onde o teste começa
- When	Primeira ação
- And	Segunda ação
- And	Terceira ação
- Then	Primeiro resultado esperado
- And	Segundo resultado esperado

### 3. E no JavaScript?
Aqui existe um detalhe interessante!
No Step Definition, o And não precisa necessariamente ser implementado usando uma função chamada And().
Por exemplo:  
```When("informo meu e-mail válido", () => {
    cy.get('[data-testid="email"]').type("maria@email.com");
});

When("informo minha senha correta", () => {
    cy.get('[data-testid="senha"]').type("senha123");
});

When("clico no botão entrar", () => {
    cy.get('[data-testid="entrar"]').click();
});
```
Mesmo que no Gherkin você tenha escrito **And**, pode implementar essas etapas com **When()**.
Isso acontece porque o **Cucumber** interpreta o **And** de acordo com a etapa anterior.
- Uma regra importante: não escolha When ou Then apenas para variar o código. Escolha conforme o significado da etapa.
