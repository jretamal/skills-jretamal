# RxJS Observables

In Angular 5, Observables handle async data. Import from `rxjs/Observable` and operators from `rxjs/operators`.

## Creating Observables

```ts
import { Observable, of, from, interval, fromEvent } from 'rxjs';
import { map, filter, take } from 'rxjs/operators';

// Create from a value
const obs$ = of(1, 2, 3);

// Create from an array
const obs2$ = from([1, 2, 3]);

// Create from an event
const clicks$ = fromEvent(document, 'click');
```

## Subscription

```ts
const myObservable$ = of(1, 2, 3);

myObservable$.subscribe(
  value => console.log(value),
  error => console.error(error),
  () => console.log('Complete')
);
```

## Operators

```ts
import { map, filter, tap, take, switchMap } from 'rxjs/operators';

of(1, 2, 3, 4, 5).pipe(
  filter(x => x % 2 === 0),
  map(x => x * 2),
  take(2)
).subscribe();
```

## Error Handling

```ts
import { catchError, throwError } from 'rxjs/operators';

this.http.get('/api/data').pipe(
  catchError(error => {
    return throwError(() => new Error('Error'));
  })
).subscribe();
```

## Subject

```ts
import { Subject } from 'rxjs';

const subject$ = new Subject<number>();
subject$.subscribe(value => console.log('Subscriber:', value));
subject$.next(1);
```

## Common Patterns

- Use `take(1)` for single-value
- Use `takeUntil(destroy$)` for cleanup