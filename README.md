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


# Configurando o babel.
[...]
