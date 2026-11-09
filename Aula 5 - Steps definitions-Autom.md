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

- **cy.visit()**      **-	Acessa uma página**
    - cy.get()	      - Localiza um elemento
    - .type()         - Digita um conteúdo
    - .click()	      - Clica em um elemento
    - .should()	      - Faz uma validação
