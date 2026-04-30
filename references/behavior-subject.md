# BehaviorSubject

BehaviorSubject:
- Always emits current value to new subscribers
- Requires an initial value
- Holds current value state

## Basic Usage

```ts
import { BehaviorSubject } from 'rxjs';

const countSubject = new BehaviorSubject<number>(0);

countSubject.subscribe(value => console.log('Subscriber:', value));
countSubject.next(1);
countSubject.next(2);

console.log('Current value:', countSubject.value);
```

## Service with BehaviorSubject

```ts
import { Injectable } from '@angular/core';
import { BehaviorSubject, Observable } from 'rxjs';

@Injectable({ providedIn: 'root' })
export class DataService {
  private dataSubject = new BehaviorSubject<string[]>([]);
  
  get data$(): Observable<string[]> {
    return this.dataSubject.asObservable();
  }
  
  get currentData(): string[] {
    return this.dataSubject.value;
  }
  
  updateData(newData: string[]) {
    this.dataSubject.next(newData);
  }
}
```

## Component Usage

```ts
data$ = this.dataService.data$;

ngOnDestroy() {
  this.destroy$.next();
  this.destroy$.complete();
}
```

## Template Binding

```html
<ul>
  <li *ngFor="let item of data$ | async">{{ item }}</li>
</ul>
```

## Best Practices

- Use for state management
- Expose as Observable (not Subject)
- Use `async` pipe for auto-cleanup