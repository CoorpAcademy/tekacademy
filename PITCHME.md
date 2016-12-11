# Rx.JS

#VSLIDE

> The observer pattern is a software design pattern in which an object, called the subject, maintains a list of its dependents, called observers, and notifies them automatically of any state changes, usually by calling one of their methods (wikipedia)

#VSLIDE

![Observable.of](http://reactivex.io/rxjs/img/of.png)

- is a sequence of ongoing events ordered (in time).
- immutable

#VSLIDE

- Single value
- Array
- Async task
- Promise
- Stream

#HSLIDE

## Timer

```js
Rx.Observable.interval(1000)
  .subscribe(value => 
    document.getElementById('counter').innerText = value
  )
```

<iframe width="100%" height="300" src="//jsfiddle.net/6yruwy71/55/embedded/result/" allowfullscreen="allowfullscreen" frameborder="0"></iframe>

#VSLIDE

![Observable.interval](http://reactivex.io/rxjs/img/interval.png)

#HSLIDE

## Counter

```js
const counter = document.getElementById('counter');
const increment = document.getElementById('increment');

const increment$ = Rx.Observable.fromEvent(increment, 'click')
  .map(() => 1);
const counter$ = increment$
  .startWith(0)
  .scan((acc, value) => acc + value, 0);

counter$.subscribe(value => counter.innerText = value)
```

<iframe width="100%" height="300" src="//jsfiddle.net/6yruwy71/20/embedded/result/" allowfullscreen="allowfullscreen" frameborder="0"></iframe>

#VSLIDE

![Observable.fromEvent](http://reactivex.io/rxjs/img/fromEvent.png)

#VSLIDE

![Observable.map](http://reactivex.io/rxjs/img/map.png)

#VSLIDE

![Observable.startWith](http://reactivex.io/rxjs/img/startWith.png)

#VSLIDE

![Observable.scan](http://reactivex.io/rxjs/img/scan.png)

#HSLIDE

## Observable of observable

![Observable.mergeAll](http://reactivex.io/rxjs/img/mergeAll.png)

#VSLIDE

## Counter

```js
const counter = document.getElementById('counter');
const increment = document.getElementById('increment');
const decrement = document.getElementById('decrement');

const increment$ = Rx.Observable.fromEvent(increment, 'click')
  .map(() => 1);
const decrement$ = Rx.Observable.fromEvent(decrement, 'click')
  .map(() => -1);
const counter$ = Rx.Observable.of(increment$, decrement$)
  .mergeAll()
  .startWith(0)
  .scan((acc, value) => acc + value, 0);

counter$.subscribe(value => counter.innerText = value)
```

<iframe width="100%" height="300" src="//jsfiddle.net/6yruwy71/50/embedded/result/" allowfullscreen="allowfullscreen" frameborder="0"></iframe>

#VSLIDE

```js
const counter = document.getElementById('counter');
const increment = document.getElementById('increment');
const decrement = document.getElementById('decrement');

const increment$ = Rx.Observable.fromEvent(increment, 'click')
  .map(() => 1).take(1);
const decrement$ = Rx.Observable.fromEvent(decrement, 'click')
  .map(() => -1).take(1);
  
const counter$ = Rx.Observable.of(increment$, decrement$)
  .repeat()
  .concatAll()
  .startWith(0)
  .scan((acc, value) => acc + value, 0);

counter$.subscribe(value => counter.innerText = value)
```

<iframe width="100%" height="300" src="//jsfiddle.net/6yruwy71/48/embedded/result/" allowfullscreen="allowfullscreen" frameborder="0"></iframe>

#VSLIDE

![Observable.take](http://reactivex.io/rxjs/img/take.png)

#VSLIDE

![Observable.repeat](http://reactivex.io/rxjs/img/repeat.png)

#VSLIDE

![Observable.concatAll](http://reactivex.io/rxjs/img/concatAll.png)

#HSLIDE

## Observable

[Proposal](https://github.com/tc39/proposal-observable)

The Observable type can be used to model push-based data sources such as DOM events, timer intervals, and sockets. In addition, observables are:

- Compositional: Observables can be composed with higher-order combinators.
- Lazy: Observables do not start emitting data until an observer has subscribed.

#VSLIDE

```js
const counter$ = new Rx.Observable(observer => {
  observer.next('foo');
  observer.next('bar');
});

counter$.subscribe(
  value => document.getElementById('subscribe').innerText = value,
  error => document.getElementById('error') = error.stack,
  () => document.getElementById('complete') = value
);
```

<iframe width="100%" height="300" src="//jsfiddle.net/6yruwy71/28/embedded/result/" allowfullscreen="allowfullscreen" frameborder="0"></iframe>

#VSLIDE

```js
const counter$ = new Rx.Observable(observer => {
  observer.next('foo');
  observer.error(new Error('error'));
  observer.complete();
  observer.next('bar');
});

counter$.subscribe(
  value => document.getElementById('subscribe').innerText = value,
  error => document.getElementById('error').innerText = error.message,
  () => document.getElementById('complete').innerText = value
);
```

<iframe width="100%" height="300" src="//jsfiddle.net/6yruwy71/36/embedded/result/" allowfullscreen="allowfullscreen" frameborder="0"></iframe>

#VSLIDE

```js
const counter$ = new Rx.Observable(observer => {
  observer.next('foo');
  observer.complete();
  observer.error(new Error('error'));
  observer.next('bar');
});

counter$.subscribe(
  value => document.getElementById('subscribe').innerText = value,
  error => document.getElementById('error').innerText = error.message,
  () => document.getElementById('complete').innerText = value
);
```

<iframe width="100%" height="300" src="//jsfiddle.net/6yruwy71/37/embedded/result/" allowfullscreen="allowfullscreen" frameborder="0"></iframe>

#VSLIDE

```js
const date$ = new Rx.Observable(observer => {
  setInterval(() => {
    observer.next(new Date());
  }, 1000);
});

date$.subscribe(
  value => document.getElementById('date').innerText = value,
);
```

<iframe width="100%" height="300" src="//jsfiddle.net/6yruwy71/51/embedded/result/" allowfullscreen="allowfullscreen" frameborder="0"></iframe>

#VSLIDE

```js
const date$ = new Rx.Observable(observer => {
  const intervalId = setInterval(() => {
    observer.next(new Date());
  }, 1000);
  
  return () => clearInterval(intervalId);
});

date$.take(1).subscribe(
  value => document.getElementById('date').innerText = value,
);
```

<iframe width="100%" height="300" src="//jsfiddle.net/6yruwy71/45/embedded/result/" allowfullscreen="allowfullscreen" frameborder="0"></iframe>

#HSLIDE

## HOT & COLD

#VSLIDE

```js
const foo = document.getElementById('foo');
const bar = document.getElementById('bar');

const values$ = Rx.Observable.of('foo', 'bar');

values$.subscribe(value => foo.innerText = foo.innerText + value);
values$.subscribe(value => bar.innerText = bar.innerText + value);
```

<iframe width="100%" height="300" src="//jsfiddle.net/6yruwy71/52/embedded/result/" allowfullscreen="allowfullscreen" frameborder="0"></iframe>

#VSLIDE

```js
const counter1 = document.getElementById('counter1');
const counter2 = document.getElementById('counter2');
const increment = document.getElementById('increment');

const increment$ = Rx.Observable.fromEvent(increment, 'click')
  .map(() => 1);
const counter$ = increment$
  .startWith(0)
  .scan((acc, value) => acc + value, 0);

counter$.subscribe(value => counter1.innerText = value);
counter$.subscribe(value => counter2.innerText = value);
```

<iframe width="100%" height="300" src="//jsfiddle.net/6yruwy71/54/embedded/result/" allowfullscreen="allowfullscreen" frameborder="0"></iframe>

#VSLIDE

> The observer pattern is a software design pattern in which an object, called the subject, maintains a list of its dependents, called observers, and notifies them automatically of any state changes, usually by calling one of their methods (wikipedia)

#VSLIDE

![Observer pattern](https://upload.wikimedia.org/wikipedia/commons/thumb/8/8d/Observer.svg/854px-Observer.svg.png)

#VSLIDE

```js
const counter1 = document.getElementById('counter1');
const counter2 = document.getElementById('counter2');
const increment = document.getElementById('increment');

const increment$ = Rx.Observable.fromEvent(increment, 'click')
  .map(() => 1)
  .share();
const counter$ = increment$
  .startWith(0)
  .scan((acc, value) => acc + value, 0);

counter$.subscribe(value => counter1.innerText = value);
counter$.subscribe(value => counter2.innerText = value);
```

<iframe width="100%" height="300" src="//jsfiddle.net/6yruwy71/42/embedded/result/" allowfullscreen="allowfullscreen" frameborder="0"></iframe>

#VSLIDE

- `.share()`
- `.publish()`
- [`.publishLast()`](https://github.com/CoorpAcademy/squirrel/blob/master/src/store.js#L7)
- `.publishReplay(bufferSize, windowTime)`

#HSLIDE

## Node's Stream VS Rx.Observable

+ Composable
+ Lazy
+ Cold: Observable could be HOT
- No-Backpressure

#VSLIDE

## Browser application with Rx and CycleJS

[CycleJS](https://cycle.js.org/)

```js
import {run} from '@cycle/xstream-run';
import {div, label, input, hr, h1, makeDOMDriver} from '@cycle/dom';

function main(sources) {
  const sinks = {
    DOM: sources.DOM.select('.field').events('input')
      .map(ev => ev.target.value)
      .startWith('')
      .map(name =>
        div([
          label('Name:'),
          input('.field', {attrs: {type: 'text'}}),
          hr(),
          h1('Hello ' + name),
        ])
      )
  };
  return sinks;
}

run(main, { DOM: makeDOMDriver('#app-container') });
```

#VSLIDE

## Node server with Rx and Cycle.js

[Dr. Gleb Bahmutov's article](https://glebbahmutov.com/blog/node-server-with-rx-and-cycle/)