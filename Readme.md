<h1 align="center">
  MIDDLEWARE NODE JS - IGNITE ROCKETSEAT
</h1>

<h4 align="center"> 
	Desafio de implementação de middleware do curso Ignite Node.JS da RocketSeat 
</h4>

<p align="center">
  <img alt="Repository size" src="https://img.shields.io/static/v1?label=Last%20commit&message=September&color=yellowgreen&style=for-the-badge&logo=Slack">
</p>

## 💻 Sobre o Projeto

O desafio consiste em implementar os middleware que a aplicação principal necessita para funcionar corretamente.
  * checksExistsUserAccount
  * checksCreateTodosUserAvailability
  * checksTodoExists
  * findUserById
Esses são os middlewares que a aplicação irá chamar para que todos os testes passem

## 🛠 Tecnologias

As seguintes ferramentas foram usadas na construção do projeto:

- [Node.js][nodejs]
- [Express][express]
- [UUID][uuid]
- [Vscode][vscode]

## 💡 Como executar o projeto

Nesse repositório está a aplicação é necessário clonar o repositório para a sua máquina e seguir as informações abaixo:

TESTES:

```bash

  Para rodar os testes execute o comando "yarn test" ou "npm run test"

```

BACKEND:

```bash

01 - Acessar a pasta do projeto no terminal e rodar o comando -  npm install

02 – Rodar o comando " yarn dev " ou " npm run dev " para startar a aplicação

```

## Especificação dos testes dos testes middlewares

- **Should be able to find user by username in header and pass it to request.user**

    Para que esse teste passe, você deve permitir que o middleware **checksExistsUserAccount** receba um username pelo header do request e caso um usuário com o mesmo username exista, ele deve ser colocado dentro de `request.user` e, ao final, retorne a chamada da função `next`.

    Atente-se bem para o nome da propriedade que armazenará o objeto `user` no request.

- **Should not be able to find a non existing user by username in header**

    Para que esse teste passe, no middleware **checksExistsUserAccount** você deve retornar uma resposta com status `404` caso o username passado pelo header da requisição não pertença a nenhum usuário. Você pode também retornar uma mensagem de erro mas isso é opcional.

- **Should be able to let user create a new todo when is in free plan and have less than ten todos**

    Para que esse teste passe, você deve permitir que o middleware **checksCreateTodosUserAvailability** receba o objeto `user` (considere sempre que o objeto existe) da `request` e chame a função `next` somente no caso do usuário estar no **plano grátis e ainda não possuir 10 *todos* cadastrados** ou se ele **já estiver com o plano Pro ativado**.

    Você pode verificar se o usuário possui um plano Pro ou não a partir da propriedade `user.pro`. Caso seja `true` significa que o plano Pro está em uso.

- **Should not be able to let user create a new todo when is not Pro and already have ten todos**

    Para que esse teste passe, no middleware **checksCreateTodosUserAvailability** você deve retornar uma resposta com status `403` caso o usuário recebido pela requisição esteja no **plano grátis** e **já tenha 10 *todos* cadastrados**. Você pode também retornar uma mensagem de erro mas isso é opcional.

- **Should be able to let user create infinite new todos when is in Pro plan**

    Para que esse teste passe, você deve permitir que o middleware **checksCreateTodosUserAvailability** receba o objeto `user` (considere sempre que o objeto existe) da `request` e chame a função `next` caso o usuário já esteja com o plano Pro. 

    Se você satisfez os dois testes anteriores antes desse, ele já deve passar também.

- **Should be able to put user and todo in request when both exits**

    Para que esse teste passe, o middleware **checksTodoExists** deve receber o `username` de dentro do header e o `id` de um *todo* de dentro de `request.params`. Você deve validar que o usuário exista, validar que o `id` seja um uuid e também validar que esse `id` pertence a um *todo* do usuário informado.

    Com todas as validações passando, o *todo* encontrado deve ser passado para o `request` assim como o usuário encontrado também e a função next deve ser chamada.

    É importante que você coloque dentro de `request.user` o usuário encontrado e dentro de `request.todo` o *todo* encontrado.

- **Should not be able to put user and todo in request when user does not exists**

    Para que esse teste passe, no middleware **checksTodoExists** você deve retornar uma resposta com status `404` caso não exista um usuário com o `username` passado pelo header da requisição.

- **Should not be able to put user and todo in request when todo id is not uuid**

    Para que esse teste passe, no middleware **checksTodoExists** você deve retornar uma resposta com status `400` caso o `id` do *todo* passado pelos parâmetros da requisição não seja um UUID válido (por exemplo `1234abcd`).

- **Should not be able to put user and todo in request when todo does not exists**

    Para que esse teste passe, no middleware **checksTodoExists** você deve retornar uma resposta com status `404` caso o `id` do *todo* passado pelos parâmetros da requisição não pertença a nenhum *todo* do usuário encontrado.

- **Should be able to find user by id route param and pass it to request.user**

    Para que esse teste passe, o middleware **findUserById** deve receber o `id` de um usuário de dentro do `request.params`. Você deve validar que o usuário exista, repassar ele para `request.user` e retornar a chamada da função next.

- **Should not be able to pass user to request.user when it does not exists**

    Para que esse teste passe, no middleware **findUserById** você deve retornar uma resposta com status `404` caso o `id` do usuário **passado pelos parâmetros da requisição não pertença a nenhum usuário cadastrado.

## 📝 Feito por Jeandson Tenorio 

👋🏽👋🏽👋🏽👋🏽 [contato!](https://www.linkedin.com/in/jeandson/)

[nodejs]: https://nodejs.org/
[express]: https://expressjs.com/pt-br/
[uuid]: https://www.npmjs.com/package/uuid
[Vscode]: https://code.visualstudio.com/