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

#VSLIDE
![Logo](http://bradfrost.com/wp-content/uploads/2013/06/atomic-design.png)

#VSLIDE

**First things first:** define your *templates*.

#VSLIDE

**Step 2:** hope your UI / UX friends make *consistent* work.

#VSLIDE

**Step 3:** define the interface / fixtures for every template.
```
export default {
  props: {
    type: 'text',
    title: 'Name',
    placeholder: 'Your name',
    value: 'Foo',
    onChange: value => console.log(value)
  }
};
```

#VSLIDE

**Step 4:** split *everything* into atoms, molecules and organisms. Consistency is key.

#HSLIDE
## A TEMPLATE'S GENESIS

#VSLIDE
### Analysis

#VSLIDE

![Logo](http://atomicdesign.bradfrost.com/images/content/instagram-atomic.png)

#VSLIDE

Do what you're supposed to do.

#VSLIDE

```JavaScript
const GridList = (props, children) => {
  return (
    <div className={style.wrapper}>
      {children}
    </div>
  );
};
```
```JavaScript
<GridList>
  {brandCards}
</GridList>
```

#VSLIDE
- decoupe de api/fixtures par composants

#VSLIDE
### Implementation
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
### CSS-MODULES

- Class composition / dependencies
- Inline style
- Class forwarding to a child via its props
- Media queries
- No global scope, no conflicts

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
## Next
- Sandbox upgrade
 - Edit your props
 - Tags and components lookup
- Pattern lab (see [Lonely Planet's](http://rizzo.lonelyplanet.com/styleguide/design-elements/colours))
- Everything is a component



