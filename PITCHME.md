# Jest
![Logo](https://cdn.auth0.com/blog/testing-react-with-jest/logo.png)

### JS test runner
maintained by Facebook <!-- .element: class="fragment" -->

#HSLIDE
### Global picture

- Performance (parallel processes)<!-- .element: class="fragment" -->
- Mocking <!-- .element: class="fragment" -->
- Snapshot testing <!-- .element: class="fragment" -->
- Code coverage <!-- .element: class="fragment" -->

#HSLIDE
### migrating from AVA

#VSLIDE
### jest-codemod
Codemods that simplify migrating JavaScript test files from Mocha, Tape and AVA to Jest.

#VSLIDE
```
> npm install -g jest-codemods
> jest-codemods
```

#VSLIDE
simple prompts
![packages](assets/codemod-1.png) <!-- .element: class="fragment" -->

![packages](assets/codemod-2.png) <!-- .element: class="fragment" -->

#VSLIDE
![packages](assets/codemod-info.png)

![packages](assets/results-1-after-codemod.png)<!-- .element: class="fragment" -->

#VSLIDE
### manual migration
jest config in package.json

#VSLIDE
`"testRegex": "/packages(/.*)?/src(/.*)?/test(?!/fixtures)(/.*)?/*.js$"`

![packages](assets/results-1-after-regex.png)<!-- .element: class="fragment" -->

#VSLIDE
keywords (`it`, `expect`)

![packages](assets/results-1-after-corrections.png)<!-- .element: class="fragment" -->

#HSLIDE
##Testing React components

#HSLIDE
##enzyme by Airbnb
- provides tools to manipulate/traverse React output<!-- .element: class="fragment" -->
- any test runner<!-- .element: class="fragment" -->
- shallow (without children)<!-- .element: class="fragment" -->
- mount (entire component)<!-- .element: class="fragment" -->
- example with [AVA](https://github.com/airbnb/enzyme/blob/master/docs/guides/tape-ava.md#ava)<!-- .element: class="fragment" -->

#HSLIDE
##snaphosts

![packages](assets/snapshot.png)<!-- .element: class="fragment" -->

#HSLIDE
##coverage --> Istanbul
```
"coverageDirectory": "coverage",
    "coverageReporters": [
      "lcov",
      "text-summary"
    ],
    "collectCoverage": true,
    "collectCoverageFrom": [
      "packages/**/src/**/*.js",
      "!**/test/**",
      "!**/node_modules/**"
    ],
    "coveragePathIgnorePatterns": [
      "/packages(/.*)?/src(/.*)?/test(/.*)?$",
      "/packages(/.*)?/dist(/.*)?$",
      "/packages(/.*)?/es(/.*)?$",
      "/packages(/.*)?/lib(/.*)?$"
    ]
```

![packages](assets/coverage.png)<!-- .element: class="fragment" -->

#HSLIDE
##sources

- Testing Reac with [Jest](https://auth0.com/blog/testing-react-applications-with-jest/?utm_source=echojs&utm_medium=sc&utm_campaign=testing_react_jest)

- [Airbnb using Enzyme](https://medium.com/airbnb-engineering/enzyme-javascript-testing-utilities-for-react-a417e5e5090f#.e8xj686ds)

- Testing React components with [Jest + Enzyme](https://hackernoon.com/testing-react-components-with-jest-and-enzyme-41d592c174f#.q489aotk8)

- [Grommet](https://blog.grommet.io/post/2016/09/01/how-we-landed-on-jest-snapshot-testing-for-javascript) uses Jest snapshots
