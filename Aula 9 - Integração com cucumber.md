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
3. npm esbuild

```
npm install --save-dev esbuild
```
**Para que servem?**
- @badeball/cypress-cucumber-preprocessor: permite que o Cypress reconheça arquivos .feature escritos em Gherkin.
- @bahmutov/cypress-esbuild-preprocessor: prepara os arquivos para execução.
- esbuild: realiza a compilação dos arquivos JavaScript.

## Configuração do cypress

No vscode, abra o arquivo>> cypress.config.js

substitua o código, pelo o código abaixo:
```

const { defineConfig } = require("cypress");

const createBundler = require("@bahmutov/cypress-esbuild-preprocessor");

const {
  addCucumberPreprocessorPlugin,
} = require("@badeball/cypress-cucumber-preprocessor");

const {
  createEsbuildPlugin,
} = require("@badeball/cypress-cucumber-preprocessor/esbuild");

module.exports = defineConfig({
  e2e: {
    specPattern: "**/*.feature",

    async setupNodeEvents(on, config) {
      await addCucumberPreprocessorPlugin(on, config);

      on(
        "file:preprocessor",
        createBundler({
          plugins: [createEsbuildPlugin(config)],
        })
      );

      return config;
    },
  },
});
```
Essa configuração segue a integração recomendada na documentação do Cucumber Preprocessor, adaptada para CommonJS. 
[GitHub](https://github.com/badeball/cypress-cucumber-preprocessor/blob/master/docs/quick-start.md?utm_source=chatgpt.com)

### O que configuramos?

- require: importa as bibliotecas instaladas.
- defineConfig: organiza as configurações do Cypress.
- specPattern: informa que nossos testes serão arquivos .feature.
- setupNodeEvents: inicializa a integração com Cucumber.
- createEsbuildPlugin: prepara os arquivos Gherkin para execução.
-return config: devolve a configuração atualizada ao Cypress. 
   
