**Instalando o Jasmine no projeto**
```javascript
npm install --save-dev jasmine
```

**Inicializando o Jasmine no projeto**
```javascript
jasmine init
```

**Criando o primeiro teste**

* Criamos um arquivo de teste "spec/exemplo/exemploSpec.js" que faz um  teste simples para demonstrar  que o funcionamento do Jasmine está OK.

    Para executar o teste rodamos o comando:

    ```javascript
    jasmine
    ```

**Executando os testes no NodeJS**

* Alteramos o arquivo "package.json" inserindo o comando "jasmine" no nó "scripts => test".

    Para executar os testes rodamos o comando:

    ```javascript
    npm run test
    ```
	
**Adicionando testes de exemplo do Jasmine no projeto**

Para adicionar os exemplos utilizamos o comando:

   ```javascript
    jasmine example
    ```
Após rodar o comando são criados:
- pasta **"lib/jasmine_examples"** com uma implementação de exemplo
- pasta **"spec/jasmine_examples"** com testes da implementação exemplo
- pasta **"spec/helper"** com um comparador customizado como exemplo