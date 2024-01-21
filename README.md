# React-Foundations

Fonte:
https://nextjs.org/learn/react-foundations

## O que é o React e o Next.js ?

O React é uma biblioteca em Javascript para construção de interfaces de usuário (UI). 
Sendo a UI algo que o usuário vê e interage.
Sendo biblioteca um conjunto de funções (APIs) que podem ser utilizadas pelo desenvolvedor no momento oportuno. 
Image de componente: https://nextjs.org/_next/image?url=%2Flearn%2Fdark%2Flearn-react-components.png&w=1920&q=75&dpl=dpl_42Sgxb1DrR4FHfR27frojTCdKMQA

Construir componentes no React leva tempo.

o Next.js é um framework em React que te disponibiliza blocos de código que auxilia construção de aplicações web.
Sendo framework, algo que disponibiliza ao React ferramental e configurações necessárias, estrutura, funcionalidades e otimização para a aplicação.
https://nextjs.org/_next/image?url=%2Flearn%2Fdark%2Flearn-ecosystem.png&w=1920&q=75&dpl=dpl_42Sgxb1DrR4FHfR27frojTCdKMQA

## O que deve-se considerar na implementação de uma aplicação ?

- A interface do usuário.
- Roteamento
- Recuperação de dados
- Renderização
- Integrações 
- Infraestrutura para deploy
- Performance
- Escalabilidade
- Experiência do desenvolvedor

## Renderizando a UI

O Document Object Model (DOM) é a representação da página em código de marcação HTML que o navegador interpreta.
O DOM é um padrão do W3C. O DOM é uma árvore, que contém nós que são objetos que representam partes do documento.
Ele representa a página web que pode ter sua estrutura, conteúdo e estilo alterados através de outras linguagens: Javascript, CSS,..
O nós podem ter `handler events` (event listners) que quando disparados são executados.
O documento é nó do tipo documento.
Todos os elementos Html, são nós do tipo elemento.
Todos os atributos Html, são nós do tipo atributo.
Texto inserido em elementos Html, são nós do tipo texto.
Comentários são nós do tipo comentário.

Navegadores precisam uma engine para transformar o HTML em DOM.

The DOM API provides a set of methods and properties to perform these operations, such as getElementById, createElement, appendChild, and innerHTML

```html
<html>
  <body>
    <div id="app"></div>
    <script type="text/javascript">
      // Select the div element with 'app' id
      const app = document.getElementById('app');
 
      // Create a new H1 element
      const header = document.createElement('h1');
 
      // Create a new text node for the H1 element
      const text = 'Develop. Preview. Ship.';
      const headerContent = document.createTextNode(text);
 
      // Append the text to the H1 element
      header.appendChild(headerContent);
 
      // Place the H1 element inside the div
      app.appendChild(header);
    </script>
  </body>
</html>
```

```h
// Create the root element
var root = document.createElement("root");

// Create a child element
var child = document.createElement("child");

// Add the child element to the root element
root.appendChild(child);

document.getElementById("root").innerHTML = "<child></child>";
```

Exemplos de Eventos do DOM (https://en.wikipedia.org/wiki/DOM_event):
- clicar no mouse (onclick)
- a pagina web foi carregada (onload)
- a imagem foi carregada (onload)
- o mouse move para cima do elemento (onfocus)
- quando o valor de um input muda (onchange)
- quando um formulario é enviado (onsubmit)
- quando o usuário pressiona uma tecla (onkeypress)

O Javascript DOM é uma representação do HTML que age como uma interface entre o Javascript e o documento propriamente. O javascript é capaz de :
- adicionar, mudar e remover qualquer elemento/atributo do HTML
- mudar o estilo CSS
- reagir aos eventos existentes
- criar novos eventos

O jQuery, AngularJS, React, Vue.js são outras bibliotecas capazes de interagir/manipular/criar com o DOM.

Shadow DOM: Web Components are a set of features that provide a standard component model for the web allowing for encapsulation and interoperability of individual HTML elements. Web Components are popular approach to build microfrontends.

A virtual DOM is a lightweight JavaScript representation of the Document Object Model (DOM) used in declarative web frameworks such as React, Vue.js, and Elm. Updating the virtual DOM is comparatively faster than updating the actual DOM.

## Programação imperativa ou declarativa

O DOM é a interpretação final do código HTML. Pode ser necessário alterar o DOM, mas usar os metodos do DOM pode ser custoso e verboso. Seria interessante se pudesse ser dito o que se deseja sem se preocupar em como é feito ao invés de cada passo a ser dado.

O React é uma biblioteca declarativa que você pode usar para criar interfaces.
Como desenvolvedor, você pode dizer ao React o que deseja que aconteça com a interface do usuário, e o React descobrirá as etapas de como atualizar o DOM em seu nome.

Outros links:
How declarative UI compares to imperative 
https://react.dev/learn/reacting-to-input-with-state#how-declarative-ui-compares-to-imperative

## Começando com React

https://nextjs.org/learn/react-foundations/getting-started-with-react

Precisa do react.js e do react-dom.js para começar, dai em diante é usar o ReactDOM para trabalhar com o DOM.

React usa JSX, que precisa ser compilado em Javascript regular.
JSX é uma extensão da sintaxe do Javascript que permite descrever a UI como familiar a sintaxe HTML.
Regras do JSX: https://react.dev/learn/writing-markup-with-jsx#the-rules-of-jsx
1. Return a single root element (se nao quiser usar uma tag html use o Fragment <></>)
2. Close all the tags 
3. camelCase all most of the things!

Navegadores não entendem JSX, é necessário um Compilador JavaScript, como o babel para transformar JSX em javascript
```
<script type="text/jsx">
</script>    
```

## Javascript Essencial para React

- Functions and Arrow Functions
- Objects
- Arrays and array methods
- Destructuring
- Template literals
- Ternary Operators
- ES Modules and Import / Export Syntax

Você pode exportar funções, var, let, const, e — como veremos mais tarde - classes.
```javascript
export function draw
export { name, draw, reportArea, reportPerimeter };
import { name, draw, reportArea, reportPerimeter } from "./modules/square.js";
```

## Construindo UI com Componentes
https://nextjs.org/learn/react-foundations/building-ui-with-components

Conceitos do core do React:
- Components
- Props
- State

Interfaces de usuário podem ser fragmentadas em blocos menores chamados `componentes`. São códigos auto-contidos, reutilizáveis.

React components são basicamente JavaScript.

Os componentes são funções que retornam um elemento UI.
Ex:
```javascript
<script type="text/jsx">
  const app = document.getElementById("app")
 
  function Header() {
     return <h1>Develop. Preview. Ship.</h1>;
   }
 
  const root = ReactDOM.createRoot(app);
  root.render(Header);
</script>
```

## Dados com props
https://nextjs.org/learn/react-foundations/displaying-data-with-props

Os dados podem ser passados para os componentes do react através de atributos, que são conhecidos como props. A passagem é semelhante passar valores para atributos em tags HTML.

Props são informações somente leitura passada aos componentes.

Note: In React, data flows down the component tree. This is referred to as one-way data flow. State, which will be discussed in the next chapter, can be passed from parent to child components as props.

```javascript
function HomePage() {
  return (
    <div>
      <Header title="React" />
    </div>
  );
}

function Header(props) {
  return <h1>Develop. Preview. Ship.</h1>;
}

function Header(props) {
  console.log(props); // { title: "React" }
  return <h1>Develop. Preview. Ship.</h1>;
}
```

Para usar variaveis, funcoes, operador ternario no JSX, usar o {}
```javascript
function Header({ title }) {
  console.log(title);
  return <h1>{title}</h1>;
}
```

## Interatividade com State
https://nextjs.org/learn/react-foundations/updating-state

React ajuda na interatividade com `state` e `event handlers`
No React eventos são camelCase.

React contém um conjunto de funções chamadas de `hooks`. Eles permitem que você adicione lógica adicional como `state` aos seus componentes.
Entenda state como toda informação em sua UI que muda durante o tempo, geralmente por interação (trigger) do usuario.

useState
Exemplo:
```javascript
function HomePage() {
  // ...
  const [likes, setLikes] = React.useState(0);
 
  function handleClick() {
    setLikes(likes + 1);
  }
 
  return (
    <div>
      {/* ... */}
      <button onClick={handleClick}>Likes ({likes})</button>
    </div>
  );
}
```

## Código inicial

```javascript
<html>
  <body>
    <div id="app"></div>
 
    <script src="https://unpkg.com/react@18/umd/react.development.js"></script>
    <script src="https://unpkg.com/react-dom@18/umd/react-dom.development.js"></script>
    <script src="https://unpkg.com/@babel/standalone/babel.min.js"></script>
 
    <script type="text/jsx">
      const app = document.getElementById("app")
 
      function Header({ title }) {
        return <h1>{title ? title : "Default title"}</h1>
      }
 
      function HomePage() {
        const names = ["Ada Lovelace", "Grace Hopper", "Margaret Hamilton"]
 
        const [likes, setLikes] = React.useState(0)
 
        function handleClick() {
          setLikes(likes + 1)
        }
 
        return (
          <div>
            <Header title="Develop. Preview. Ship." />
            <ul>
              {names.map((name) => (
                <li key={name}>{name}</li>
              ))}
            </ul>
 
            <button onClick={handleClick}>Like ({likes})</button>
          </div>
        )
      }
 
      const root = ReactDOM.createRoot(app);
      root.render(<HomePage />);
    </script>
  </body>
</html>
```


## Instalando next.js

Para usar next.js precisa de no minimo node v18.17.0.

Não precisará de react e react-dom scripts.
Não precisará do babel para compilar o JSX.

Crie um arquivo package.json com {}.

Rode o seguinte comando no terminal
```bash
npm install react@latest react-dom@latest next@latest
```

O package.json será preenchido
```json
{
  "dependencies": {
    "next": "^14.0.3",
    "react": "^18.2.0",
    "react-dom": "^18.2.0"
  }
}
```

FIcaria assim:
```javascript
import { useState } from 'react';
 
function Header({ title }) {
  return <h1>{title ? title : 'Default title'}</h1>;
}
 
function HomePage() {
  const names = ['Ada Lovelace', 'Grace Hopper', 'Margaret Hamilton'];
 
  const [likes, setLikes] = useState(0);
 
  function handleClick() {
    setLikes(likes + 1);
  }
 
  return (
    <div>
      <Header title="Develop. Preview. Ship." />
      <ul>
        {names.map((name) => (
          <li key={name}>{name}</li>
        ))}
      </ul>
 
      <button onClick={handleClick}>Like ({likes})</button>
    </div>
  );
}
```

The only code left in the HTML file is JSX, so you can change the file type from .html to .js or .jsx.

### Funcionamento do next.js
https://nextjs.org/learn/react-foundations/installation

O next.js usa file-system como roteamento. Isso significa que em vez de usar código para definir rotas, vc pode usar pastas e arquivos.

Here's how you can create your first page in Next.js:

1. Create a new folder called app and move the index.js file inside it.
2. Rename your index.js file to page.js. This will be the main page of your application.
3. Add export default to your <HomePage> component to help Next.js distinguish which component to render as the main component of the page.

```javascript
import { useState } from 'react';
 
function Header({ title }) {
  return <h1>{title ? title : 'Default title'}</h1>;
}
 
export default function HomePage() {
  // ...
}
```

Adicione um script `next dev` no package.json

## Server and Client Components
https://nextjs.org/learn/react-foundations/server-and-client-components

- Server and Client Environments
- Network Boundary

Next.js usa `Server Components` por padrão

Refatorando a app anterior

/app/like-button.js
```javascript
'use client';
 
import { useState } from 'react';
 
export default function LikeButton() {
  const [likes, setLikes] = useState(0);
 
  function handleClick() {
    setLikes(likes + 1);
  }
 
  return <button onClick={handleClick}>Like ({likes})</button>;
}
```

/app/page.js
```javascript
import LikeButton from './like-button';
 
function Header({ title }) {
  return <h1>{title ? title : 'Default title'}</h1>;
}
 
export default function HomePage() {
  const names = ['Ada Lovelace', 'Grace Hopper', 'Margaret Hamilton'];
 
  return (
    <div>
      <Header title="Develop. Preview. Ship." />
      <ul>
        {names.map((name) => (
          <li key={name}>{name}</li>
        ))}
      </ul>
      <LikeButton />
    </div>
  );
}
```