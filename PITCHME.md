# Once Upon A Time

![logobig](assets/logobig.png)

#VSLIDE

###New tool

First released about 1 year ago

[@kadira/storybook](https://www.npmjs.com/package/@kadira/storybook)


#HSLIDE
### What? How? 
### Get! Easy :)

```
$ npm i -g getstorybook

$ cd my-repo

$ getstorybook
```

#VSLIDE

![npmiStorybook](assets/npmiStorybook.png)

#VSLIDE

![getstorybook](assets/getStorybook.png)


#VSLIDE

###Use

$ npm run storybook

![storybook](assets/storybook.png)

#HSLIDE

### Looks good !

- Easy search
- Every component with every fixtures
- Automatic render (hot reloading)
- Action logger
- Documentation

[LIVE ACTION](http://localhost:3004/)

#VSLIDE

### What now ?

it's all about stories

Stories are substates of the component

1 story === 1 fixtures

```
.add('with secondary', () => (
  <Button
    href={#}
    target={_self}
    light={false}
    small={false}
    secondary={false}
  >
    Coorpacademy
  </Button>
))
```
#VSLIDE

```
export default {
  props: {
    submitValue: 'coorpacademy',
    href: '#',
    light: 'false',
    small: 'false',
    secondary: 'false'
  }
};
```

#VSLIDE

### Writing stories of my component 

```
// file: src/stories/index.js

import React from 'react';
import { storiesOf, action } from '@kadira/storybook';
import Button from '../components/Button';

storiesOf('Button', module)
  .add('with text', () => (
    <Button onClick={action('clicked')}>Hello Button</Button>
  ))
  .add('with some emoji', () => (
    <Button onClick={action('clicked')}>😀 😎 👍 💯</Button>
  ));
```

#VSLIDE

###Actions Addon

"Action" is an Storybook Addon

```
import { storiesOf, action } from '@kadira/storybook'
// or import { action } from '@kadira/storybook-addon-actions'

storiesOf('Button', module)
  .add('default view', () => (
    <Button onClick={ action('button-click') }>
      Hello World!
    </Button>
  ))

```

#VSLIDE

###Documentation

```
'simple usage',
  `
    This is the basic usage with the button with providing a label to show the text.
  `,
  ...
```

![addonInfo](assets/addonInfo.png)


#HSLIDE

### WHAT NOW ?

- Overview on components ✔
- Better understanding ✔
- Actions x
- Link components x
- Document x
- Test each component x (enzyme ?)
- Exporting as a static app x

#HSLIDE

### TESTING

- Structure : StoryShots (jestSnapshots)
- Interaction (with Enzyme)
- CSS testing et manual testing

#HSLIDE

### CONFIGURATION

Babel, Webpack, css, ES2016

#HSLIDE

### Links

- [StoryBook doc](https://getstorybook.io/docs)
- [ReactConf2017](https://www.youtube.com/watch?v=PF0Vi-iIyoo)
