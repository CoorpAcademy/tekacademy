# Components
https://gitpitch.com/coorpacademy/tekacademy/components

#HSLIDE
## qu'est ce que cest
chris

#VSLIDE
 - vue uniquement
 - bibliotheque de vdom

#VSLIDE
 - vdom + jsx

```js
 export default (treant, options) => {
  const {h} = treant;

  return (props, children) => {
    const state = props.popular ? style.popular : style.default;

    return (
      <span className={state}>★</span>
    );
  };
};
```

#VSLIDE
 + cssmodules

```css
.default {
  color: #B0BEC5;
  margin-right: 2px;
}

.popular {
  color: #FFB90D;
  margin-right: 2px;
}
```

#VSLIDE
 `treant -> h`

#VSLIDE
 `treant -> h -> generic vdom`

#VSLIDE
 `treant -> h -> generic vdom -> engine`

#VSLIDE
 `treant -> h -> generic vdom -> engine -> render`

#VSLIDE
  lerna --> packages
    - components
    - bundler
    - treant-core
    - treant-engines
    - treant-adapter

#VSLIDE
    treantjs
        h -> generic vdom -> engine -> render

#HSLIDE
## installation
  - slide: clone  npm i  npm start
  --> sandbox
  --> demo

#HSLIDE
## THE LIBRARY

#VSLIDE?image=http://bradfrost.com/wp-content/uploads/2013/06/atomic-design.png

#VSLIDE

First things first: define your templates.

#VSLIDE
- discussion vue/metier définition des templates

#VSLIDE
- definir les etats des templates --> les fixtures

#VSLIDE
- decoupe en components mutualisés entre les templates

#HSLIDE
## creer un template : implementation
julien

#VSLIDE
### analyse macro
    - choix de la responsabilite parent/enfant  [grid VS card]
    - decoupe de api/fixtures par composants

#VSLIDE
### realisation macro
    - creation des dom + css
    - branchement des parents/enfants jusqu'au template

#HSLIDE
## creer un template : outils
chris

#VSLIDE
### validation -> api-check
 code conditions

#VSLIDE
### factory + jsx
 code createComponent


#VSLIDE
julien

### css-modules
        class composition
        inline
        ajout de classe sur un enfant
        media queries

#HSLIDE
## branchement sur les apps
chris

#VSLIDE
build
   - babel --> /lib /es
   - webpack ---> dist css/js
   - bundler --> webpack

#VSLIDE
- adapters --> mooc/www

#VSLIDE
- mooc
   code directive

#VSLIDE
- www
   code helper

#VSLIDE
- webpack pour les apps
  code jsx

#VSLIDE
- le branchement
  - npm link
  - publish npm + bump sur le projet

#HSLIDE
julien
## Next
- ameliorer la sandbox -> pick props, tags + recherche de composants
- migrer les trucs existants
- tout ce qui est nouveau en UI doit etre dans components



