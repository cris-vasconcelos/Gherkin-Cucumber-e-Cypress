## Preparar integração com cucumber
Vamos começar com a integração de gherkin e cypress.

1. No terminal do VS Code, confirme que está na pasta cypress-cucumber e execute:
```
npm install --save-dev @badeball/cypress-cucumber-preprocessor
```
2. Intalação do processador de arquivos JS.

```
npm install --save-dev @bahmutov/cypress-esbuild-preprocessor
```
3. npm

```
npm install --save-dev esbuild
```
**Para que servem?**
- @badeball/cypress-cucumber-preprocessor: permite que o Cypress reconheça arquivos .feature escritos em Gherkin.
- @bahmutov/cypress-esbuild-preprocessor: prepara os arquivos para execução.
- esbuild: realiza a compilação dos arquivos JavaScript.

   
   
