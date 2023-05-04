Observables are a powerful way to work with asynchronous data streams in JavaScript. In ES6, the Observable class was introduced to provide a standardized way to work with these streams.

An observable represents a stream of data that can be observed over time. You can subscribe to an observable to receive notifications when new data is available, and you can also transform and combine observables to create more complex streams.

Here's an example of how to create and subscribe to an observable:

```javascript
const { Observable } = require('rxjs');

const observable = new Observable((subscriber) => {
  subscriber.next(1);
  subscriber.next(2);
  subscriber.next(3);
  subscriber.complete();
});

observable.subscribe({
  next: (value) => console.log(value),
  complete: () => console.log('Observable complete'),
});
```

In this example, we're creating a new Observable object that emits three values (1, 2, and 3) and then completes. We're then subscribing to the observable to log each value as it's emitted, and to log a message when the observable completes.

Observables can also be transformed and combined using a variety of operators. Here's an example of how to use the map operator to transform an observable:

```javascript
const { Observable } = require('rxjs');
const { map } = require('rxjs/operators');

const observable = new Observable((subscriber) => {
  subscriber.next(1);
  subscriber.next(2);
  subscriber.next(3);
  subscriber.complete();
});

observable
  .pipe(map((value) => value * 2))
  .subscribe({
    next: (value) => console.log(value),
    complete: () => console.log('Observable complete'),
  });
```

In this example, we're using the pipe method and the map operator to transform the values emitted by the observable by multiplying each value by 2 before emitting it. The resulting observable emits the values 2, 4, and 6.

Observables can also be combined using operators like merge and zip. Here's an example of how to use the merge operator to combine two observables:

```javascript
const { Observable } = require('rxjs');
const { merge } = require('rxjs/operators');

const observable1 = new Observable((subscriber) => {
  subscriber.next(1);
  setTimeout(() => subscriber.next(2), 1000);
});

const observable2 = new Observable((subscriber) => {
  subscriber.next('A');
  setTimeout(() => subscriber.next('B'), 500);
});

merge(observable1, observable2)
  .subscribe({
    next: (value) => console.log(value),
    complete: () => console.log('Observable complete'),
  });
```

In this example, we're using the merge operator to combine two observables into a single observable that emits values from both streams. The resulting observable emits the values 1, 'A', 'B', and 2.

These are just a few examples of how to use observables in ES6. The Observable class and the RxJS library provide many other operators and methods for working with asynchronous data streams.