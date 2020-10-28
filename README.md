# Conceitos ReactJS.

## o que é o react? 
* bibilioteca para construção de interfaces.
* web, mobile, rv , etc...
* construção de single page aplication.
 
 #### exemplo de código.
```js
import React from 'react'

import './button.css'
import icon from './button.png'

function Button() {
  return (
    <button>
      <img src={icon} />
    </button>
  )
}
```

## JSX.
* escrever HTML dentro do javascript.
* com react podemos criar nossos próprios componentes.

- com o jsx é possível escrever código html, temos uma função chamada Button()
que retona um botão html com um span dentro.
```js
function Button() {
  return (
    <button type="button">
      <span class="icon"></span>
    </button>
  )
}
```
- em um outro local podemos importar essa função da seguinte forma.
```js
function Header() {
  return < Button />
}
```

## Babel / Webpack.
* o browser não entende todo esse código ( imports, e etc.. ).
* o babel converte o código JS de uma forma que o browser entenda.
* webpack possui várias funções.
 * criação do bundle, arquivo com todo código da aplicação.
 * ensinar ao javascript como importar arquivos css, imagens e etc ( loaders ).
 * Live reload com webpack dev server.


## Componentização.
* Dividir pedaços da aplicação em partes menores.
* Esses pedaços podem ser repetidos.
* Componente é uma função que retorna um html ( JSX ).
**index.js**
```js
import React from 'react'
import { render } from 'react'
```
**App.js** ( 1º componente ).
```js
import React from 'react'
import Header from './components/Header'

export default function App() {
 return <Header />
}
```
**Header.js** ( 2º componente )
```js
import React from 'react'

export default function Header() {
 return (
  <header>
   <h1> Exemplo de header </h1>
  </header>
 )
 
 }
```

## Propriedades.
* Informação que se deseja passar de um componente pai para um componente filho.
* as propriedades vão vir como parametro da função do componente.
* existe uma propriedade chamada children que retonar o conteúdo dentro do componente.

**index.js**
```js
import React from 'react'
import { render } from 'react'
```
**App.js** ( 1º componente ).
```js
import React from 'react'
import Header from './components/Header'

export default function App() {
 return (
 <>
  <Header title="homePage">
   <ul>
    <li>HomePage</li>
    <li>Projects</li>
   </ul>
  </Header>
  <Header title="TestePage>
   <ul>
    <li>HomePage</li>
    <li>Projects</li>
   </ul>
  </Header>
 </>
}
```
**Header.js** ( 2º componente )
```js
import React from 'react'

export default function Header({ title, children}) {
 return (
  <header>
   <h1>{title}</h1>
   
   { childen }
  </header>
 )
 
 }
```

## Estado e Imutabilidade.
* Garante performance mesmo em aplicações com muitos dados.
* É preciso informar a key ( chave única ) em operações de loop no react.
* useState faz parte de API do react e é usado para controlar o estado.
* useState retorna um array com duas posições a primeiro é o estado inicial que é informado no parâmetro da função
a segunda é uma função que fica responsável por atualizar o estado.
* o estado não deve ser alterado diretamente é preciso copiar o estado para outra variável para então setar o novo valor.
* como foi feito aqui : setProjects([...projects, `Novo projeto ${Date.now()}`])


**index.js**
```js
import React from 'react'
import { render } from 'react'
```
**App.js** ( 1º componente ).
```js
import React, { useState } from 'react'
import Header from './components/Header'

export default function App() {
 const [projects, setProjects] = useState(['Desenvolvimento de app', 'Front-end web'])
 
 function handleAddProject() {
  setProjects([...projects, `Novo projeto ${Date.now()}`])
 }
 
 return (
 <>
  <Header title="Projects" />
  
  <ul>
   {projects.map(project => <li key={project}>{project}</li>)}
  </ul>
  
  <button type="button" onClick={handleAddProject}>Adicionar projeto</button>
 </>
}
```
**Header.js** ( 2º componente )
```js
import React from 'react'

export default function Header({ title}) {
 return (
  <header>
   <h1>{title}</h1>
  </header>
 )
 
 }
```
