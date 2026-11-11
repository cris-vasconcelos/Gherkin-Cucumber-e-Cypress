## 1. Criando uma pasta
**Abra o terminal**

Execute:
```
mkdir -p ~/Documentos/cypress-cucumber

```
**Entre na pasta**
```
cd ~/Documentos/cypress-cucumber
```
**Abra o projeto**
```
code .
```

## 2.O que fizemos?
- mkdir: criou a pasta.
- -p: criou também a pasta Projetos, caso ainda não exista.
- cd: entrou na pasta.
- code .: abriu a pasta atual no VS Code.

## 3. Inicializando o projeto npm
No terminal do VS Code, confirme que está dentro da pasta cypress-cucumber e execute:
```
npm init -y
```

## O que esse comando faz?

Ele cria o arquivo package.json, que armazena as informações do projeto e suas dependências.

Depois da execução, você deverá encontrar:
```
cypress-cucumber/
└── package.json
```
## 4.Instalar o cypress

No terminal do vscode, dentro da pasta cypress-cucumber, execute:
```
npm install cypress --save-dev
```
O que esse comando faz?
- npm install: instala uma biblioteca.
- cypress: nome da ferramenta.
- --save-dev: registra o Cypress como dependência de desenvolvimento no package.json.
A instalação pode levar alguns minutos.

Depois, execute:
```
npx cypress -v
```
## 5. Abrir o cypress
No terminal, execute:
```
npx cypress open
```

**O que deve acontecer:**
1. O Cypress abrirá uma janela.
2. Você verá a opção E2E Testing.
3. Selecione E2E Testing.
4. O Cypress solicitará a configuração inicial.
5. Selecione o navegador disponível.
