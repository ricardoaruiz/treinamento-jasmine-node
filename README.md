[![Build Status](https://travis-ci.org/ricardoaruiz/treinamento-jasmine-node.svg?branch=master)](https://travis-ci.org/ricardoaruiz/treinamento-jasmine-node)

## Instalando o Jasmine no projeto

```javascript
npm install --save-dev jasmine
npm install -g jasmine
```

## Inicializando o Jasmine no projeto
```javascript
jasmine init
```

## Criando o primeiro teste

* Criamos um arquivo de teste "spec/exemplo/exemploSpec.js" que faz um  teste simples para demonstrar  que o funcionamento do Jasmine está OK.

    Para executar o teste rodamos o comando:

    ```javascript
    jasmine
    ```

## Executando os testes no NodeJS

* Alteramos o arquivo "package.json" inserindo o comando "jasmine" no nó "scripts => test".

    Para executar os testes rodamos o comando:

    ```javascript
    npm run test
    ```
	
## Adicionando testes de exemplo do Jasmine no projeto

Para adicionar os exemplos utilizamos o comando:

```javascript
jasmine example
```
Após rodar o comando são criados:
- pasta **"lib/jasmine_examples"** com uma implementação de exemplo
- pasta **"spec/jasmine_examples"** com testes da implementação exemplo
- pasta **"spec/helper"** com um comparador customizado como exemplo

## Instalando o Karma no projeto

```javascript
npm install --save-dev karma

npm install --save-dev karma-jamine

npm install --save-dev karma-firefox-launcher

npm install -g install karma-cli
```

## Configurando o Karma no projeto

```javascript
karma init karma.conf.js
```
Responder as perguntas com os seguintes valores:
- jasmine
- no
- Firefox
- spec/**/*Spec.js
- yes

No final será gerado o arquivo karma.conf.js na raiz do projeto com todas as configurações definidas.

## Inicializando o Karma no projeto

```javascript
karma start
```

Os testes vão rodar e o karma ficará em modo de escuta.

Ocorrerá um erro nos testes, pois em um dos testes de exemplo do Jasmine é utilizado o "Require.js" que não é suportado pelos browsers, mas que será resolvido quando
instalarmos o Browserify.

## Executando o Karma com o NodeJS

* Alteramos o arquivo "package.json" no nó scripts da seguinte forma:
    
    ```javascript
    "scripts": {
        "test-dev": "karma start",
        "test": "karma start --single-run"
    },
    ```

    Para executar os testes rodamos o comando:

    ```javascript
    npm run test

    npm run test-dev
    ```

## Browserify

É um framework que converte as chamadas "require" utilizadas no NodeJS para um formato compreensivel pelo navegador

```javascript
npm install --save-dev browserify
npm install --save-dev watchify
npm install --save-dev karma-browserify
```

Alterar o arquivo "karma.conf.js" conforme os trechos abaixo:

```javascript
frameworks: ['jasmine', 'browserify'],
```

```javascript
files: [
    'spec/**/*Spec.js',
    'spec/helpers/**/SpecHelper.js'
],
```

```javascript
preprocessors: {
    'spec/**/*Spec.js': ['browserify']
}
```

## Integrando o Travis CI no projeto

Criar o arquivo .travis.yml na raiz do projeto com o seguinte conteúdo:

```
language: node_js
before_install:
  - "export DISPLAY=:99.0"
  - "sh -e /etc/init.d/xvfb start"
node_js:
  - 'node'
```

## Adicionando o repositório Github no Travis CI

- Ir até o site https://travis-ci.org/
- No lado esquerdo "My Repositories", clicar no "+"
- Encontrar na lista o repositório a ser adicionado e ligar
- Acessar o repositório adicionado no lado esquerdo "My Repositories"
- Clicar na imagem "build/unknown" no canto superior direito
- Será aberta uma tela onde devemos selecionar "Markdown" no segundo combo e copiar o texto
que será apresentado no campo logo abaixo.
- Inserir o texto copiado no topo do arquivo README.md do projeto e fazer o commit