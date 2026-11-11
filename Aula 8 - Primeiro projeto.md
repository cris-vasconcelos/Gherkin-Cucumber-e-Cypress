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
