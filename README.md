# criando-api

* Tenha o git instalado em sua maquina
* Tenha o node intalado em sua maquina

* Crie uma pasta chamada crud-api-anotação
* Abra a pasta no terminal e Inicialize o projeto utilizando o comando ```npm init -y```
esse comando cria um arquivo chamado package.json, ele nada mais é que um arquivo que grava as informações do projeto como  nome do projeto, versões, dependencias etc...

```
{
  "name": "crud-api-anotacao",
  "version": "1.0.0",
  "description": "",
  "main": "index.js",
  "scripts": {
    "test": "echo \"Error: no test specified\" && exit 1"
},
...
```

* Vamos utilizar o  express.js  framwork, que nos ajuda a construir api no padrao rest(usando protocolo http) . O Express é um framework para aplicativo da web do Node.js mínimo e flexível que fornece um conjunto robusto de recursos para aplicativos web e móvel.
para saber mais  sobre [express.js]( https://expressjs.com/pt-br/)  
* Para usar o express vamos digitar no terminal o comando ``` npm install express --save```  todos os modulos que intalar vai aparecer o uma pasta chamada node-modules, outro arquivo chamado package-lockson na pasta raiz.


* Crie no diretorio raiz um arquivo chamado app.js e vamos copiar o codigo que esta  Dentro do site [express.js](https://expressjs.com/pt-br/starter/hello-world.html) no app.js,  temos a opção Hello World ele mostra o passo a passo para criar uma aplicação. Mas por enquanto só vamos copiar o código que esta nele 
``` const express = require('express')
const app = express()
const port = 3000

app.get('/', (req, res) => {
  res.send('Hello World!')
})

app.listen(port, () => {
  console.log(`Example app listening at http://localhost:${port}`)
})
```

* Agora vamos executar 
* Digite no terminal ```node app.js`` 
esse comando vai dizer ao node que é para ele executar esse script que criamos que é o  app.js 
e vai aparecer  no termial a mensagen A api esta rodando em  http://localhost:3000, clica nele e vai aparecer no navegador a mensagem Hello World! Hello Vanessa! ,  para sair do servidor pressione a tecla ctrl + c
* Para não ficar reiniciando o servidor toda vez que faz alguma atualização,  vamos instalar o modulo [Nodemon](https://www.npmjs.com/package/nodemon).  O nodemon é uma ferramenta que ajuda a desenvolver aplicativos baseados em node.js, reiniciando automaticamente o aplicativo de nó quando mudanças de arquivo no diretório são detectadas. 
* Pare a aplicação que estava rodando e Digite o comando ``` npm install --save-dev nodemon``` para intalar o modulo local. 
* Para usar o nodemon vai no arquivo package.js e na parte do script digite ```"start": nodemon app.js``` porque é esse json que vai executar nossos scripts ficara assim:
``` "scripts": {
    "start": "nodemon app.js",
    "test": "echo \"Error: no test specified\" && exit 1"
  },
  ```
* Agora para executar a aplicação no nodemon é só digitar no terminal ```npm start``` 
que vai aparecer isso no terminal

```
> crud-api-anotacao@1.0.0 start C:\Users\ddd\llllll\crud-api-anotacao
> nodemon app.js

[nodemon] 2.0.13
[nodemon] to restart at any time, enter `rs`
[nodemon] watching path(s): *.*
[nodemon] watching extensions: js,mjs,json
[nodemon] starting `node app.js`
A api esta rodando em  http://localhost:3000
```
Agora sim... Qualquer coisa no codigo que mudar, essa aplicação vai parar e vai subir automaticament 


### Depois de tudo instalado agora vamos construir nossa api/nossas rotas

##### Vamos utilizar alguns métodos [Http](https://developer.mozilla.org/pt-BR/docs/Web/HTTP/Methods)

Como não vamos utilizar o banco de dados
*Dentro do arquivo app.js, depois do ``` const port = 3000 ```de um enter e crie uma variável  chamada rotes que recebe um array vazio 
```const = notes ```

Exemplo: 

```
const express = require('express')
const app = express()
const port = 3000

const notes = []
```
### Iniciando o método Get

* Adicione depois da / notes na rota

Exemplo:
```
app.get('/notes', (req, res) => 

```

* Alterar o send para json, ao invés de  uma string vamos retornar 
  para o frontend um tudo que estiver dentro do const note = [], um array

Exemplo:
  ```
  app.get('/notes', (req, res) => { 
  res.json(notes)
})

 ```

 ### Iniciando o método Post 

Ele serve para criar alguma coisa nova

* Copie o código 

``` 
app.get('/notes', (req, res) => { 
  res.json(notes)  
})

```

* Como nós vamos trabalhar com o body temos que colocar mais um item lá em cima esse código ``` app.use(express.json()) ```  depois desse ``` const port = 3000 ```
isso vai passar uma configuração para o express, para parsear todas as minhas entradas das apis por json. Para saber mais consulte [express](http://expressjs.com/pt-br/4x/api.html#req.body)

Exemplo: 

```
const express = require('express')
const app = express()
const port = 3000

app.use(express.json()) 
``` 

* Para pegar as variaveis que o front esta mandando vamos add ``` console.log(req.body) ``` e faça o teste 

Exemplo:

```
app.post('/notes', (req, res) => { 
  // o req vai pegar as requisições do body assim consigo manipular essas informações
  console.log(req.body)
  res.json(notes) 
})
```

  Sabendo disso agora  a gente vamos conseguir extrair as informações 
* Vamos criar dois campos para para passar o titulo e a descrição 
```const title = req.body.title ``` e  ```const description = req.body.description ```

Exemplo: 

```
app.post('/notes', (req, res) => { 
  const title = req.body.title 
  const description = req.body.description 
  res.json(notes) 
})

```
