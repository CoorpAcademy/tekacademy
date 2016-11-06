# Components
https://gitpitch.com/coorpacademy/tekacademy/components

#HSLIDE
## What is it ?

#VSLIDE
 - View

#VSLIDE
 - View
 - Library

#VSLIDE
 - How it is designed

#VSLIDE
 - How it is designed
 - How it is developed

#VSLIDE
 - How it is designed
 - How it is developed
 - How it is used

#VSLIDE
 - How it is designed
 - How it is developed
 - How it is used
 - How it works

#VSLIDE
Let's get started
```
npm i
npm start
---> sandbox on http://localhost:3004
```

#HSLIDE
## THE LIBRARY
#### How it is designed

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

A matter of responsibility.
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
```JavaScript
<div className={style.brand}>
  <BrandCard {...brand}/>
</div>
```

#VSLIDE
### Implementation
    - creation des dom + css
    - branchement des parents/enfants jusqu'au template

#HSLIDE
### How it is developed

#VSLIDE
## Tools

#VSLIDE
### validation -> api-check
```
const conditions = checker.shape({
  props: checker.shape({
    popular: checker.bool
  }).strict,
  children: checker.none
});
```

#VSLIDE
### factory + jsx
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
### CSS-MODULES

- Class composition / dependencies
- Inline style
- Class forwarding to a child via its props
- Media queries
- No global scope, no conflicts

#HSLIDE
### How it is used

#VSLIDE
### build
- babel
  -> /lib es5
  -> /es  es6

#VSLIDE
### build
- babel
  -> /lib es5
  -> /es  es6
- webpack ---> dist css/js

#VSLIDE
### build
- babel
  -> /lib es5
  -> /es  es6
- webpack ---> dist css/js
- bundler --> webpack (mooc/www-static)

#VSLIDE
### mooc
- bundler
- adapter angular --> directives
- https://github.com/CoorpAcademy/coorpacademy/blob/master/app/server/lib/components.js

#VSLIDE
### mooc
```html
<discipline-cards props="props"/>
```
```js
$scope.props = {
    image: 'tree',
    theme: $state.params.theme,
    disciplines: [],
    onDisciplineClick: function(discipline) {
        $rootScope.openDiscipline(discipline);
    },
    onModuleClick: function(module) {
        $rootScope.openModule(module);
    }
};
```

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
## How it is done

#VSLIDE
### lerna --> packages
![packages](assets/packages.png)

#VSLIDE
### factories --> DOM
![rendering](assets/rendering.png)

#HSLIDE
## Next
- Sandbox upgrade
 - Edit your props
 - Tags and components lookup
- Pattern lab (see [Lonely Planet's](http://rizzo.lonelyplanet.com/styleguide/design-elements/colours))
- Everything is a component



