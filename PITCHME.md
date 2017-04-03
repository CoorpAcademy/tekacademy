# Once Upon A Time

![logobig](assets/logobig.png)

#HSLIDE
### What? How ? 
### Get! Easy :)


[npm i -g getstorybook](https://raw.githubusercontent.com/coorpacademy/tekacademy/storybook/assets/npmiStorybook.png)

cd my-repo

[getstorybook](https://raw.githubusercontent.com/coorpacademy/tekacademy/storybook/assets/getStorybook.png)

#VSLIDE

###Use

```
npm run storybook
```

![storybook](assets/storybook.png)

#HSLIDE

### Looks good !

- Easy search
- Every component with every fixtures
- Automatic render
- Action logger

[LIVE ACTION](http://localhost:3004/)

#VSLIDE

### What now ?

it's all about stories

1 story === 1 fixtures

![storyFixture](assets/storyFixture.png)

#VSLIDE

### Writing a story

One by one

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

### Writing a story

load all of them

```
import { configure } from '@kadira/storybook';

function loadStories() {
  require('../storybook');
}

configure(loadStories, module);

```

#VSLIDE

### Adding Actions

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


#HSLIDE

### WHAT NOW ?

- Overview on components
- Better understanding
- Testing each component
- Exporting as a static app

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
- [ReactConf2017](https://www.youtube.com/watch?v=rMf3nDUfUpY&feature=youtu.be&t=4704)
