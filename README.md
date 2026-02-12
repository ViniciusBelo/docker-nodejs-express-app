# docker-nodejs-express-app

Exemplo de aplicação Node.js com Express preparada para ser distribuída utilizando Docker.

Projeto demonstrando o conceito:

Develop • Ship • Run 🚀

---

## 📌 Sobre o Projeto

Esta é uma aplicação simples em Node.js utilizando Express, containerizada com Docker.

Ao acessar a aplicação no navegador, será exibida a mensagem:

Geek Hunter!

O foco principal deste projeto é demonstrar como criar, buildar e executar containers Docker.

---

## 🧱 Estrutura do Projeto

- app.js
- package.json
- Dockerfile

---

## 📄 Código da Aplicação (app.js)

```js
const express = require('express');
const app = express();

app.get('/', function (req, res) {
  res.send('Geek Hunter!');
});

app.listen(3000, function () {
  console.log('Servidor Geek Hunter rodando na porta 3000!');
});
```

## 🐳 Dockerfile

Exemplo de Dockerfile utilizado no projeto:

```FROM node:18-alpine
RUN mkdir -p /home/node/app/node_modules && chown -R node:node /home/node/app

WORKDIR /home/node/app

# Copia arquivos de dependências
COPY package*.json ./

USER node

# Instala dependências
RUN npm install

# Copia o restante da aplicação
COPY --chown=node:node . .

EXPOSE 3000

CMD ["node", "app.js"]
```

## 🚀 Build da Imagem Docker

Para criar a imagem Docker, execute:

```bash
docker build -t docker-nodejs-express-app .
```

A opção -t define a tag da imagem.

## ▶️ Executando o Container

Após criar a imagem, execute:

```bash
docker run -it -p 3000:3000 --rm --name docker-nodejs-express-app docker-nodejs-express-app:latest
```

## 🌐 Acessando a Aplicação

Abra o navegador e acesse:

```bash
http://localhost:3000
```

Você verá a mensagem:
Geek Hunter!


## ⚙️ Criando uma Aplicação Express Completa (Opcional)

Caso deseje criar uma aplicação mais estruturada utilizando o express-generator:

Instale o gerador globalmente:

```bash
npm install express-generator -g
```

Crie uma nova aplicação:

```bash
express minhaAplicacao
cd minhaAplicacao
npm install
npm start
```

Depois acesse:

```bash
http://localhost:3000
```

## 📚 Tecnologias Utilizadas

* Node.js
* Express
* Docker

## 🎯 Objetivo
Demonstrar como:

* Criar uma aplicação Node.js
* Criar um Dockerfile
* Gerar uma imagem Docker
* Executar um container
* Publicar uma aplicação containerizada

## 👨‍💻 Autor

Vinícius Belo

---
