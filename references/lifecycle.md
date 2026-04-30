# Component Lifecycle

Angular components have a lifecycle. Implement lifecycle hook interfaces.

## Lifecycle Hooks

| Hook | Method | Description |
| :--- | :--- | :--- |
| OnChanges | `ngOnChanges(changes: SimpleChanges)` | Called when @Input() changes. |
| OnInit | `ngOnInit()` | Called once, after first ngOnChanges. |
| DoCheck | `ngDoCheck()` | Called during every change detection. |
| AfterContentInit | `ngAfterContentInit()` | Called after content projection. |
| AfterContentChecked | `ngAfterContentChecked()` | Called after every content check. |
| AfterViewInit | `ngAfterViewInit()` | Called after view is initialized. |
| AfterViewChecked | `ngAfterViewChecked()` | Called after every view check. |
| OnDestroy | `ngOnDestroy()` | Called before destruction. Cleanup here. |

## Example

```ts
import { Component, OnInit, OnDestroy, OnChanges, SimpleChanges } from '@angular/core';

@Component({ selector: 'app-example', template: `...` })
export class ExampleComponent implements OnInit, OnDestroy, OnChanges {
  @Input() data: string;

  ngOnInit() {
    console.log('Component initialized');
  }

  ngOnChanges(changes: SimpleChanges) {
    console.log('Input changed:', changes);
  }

  ngOnDestroy() {
    console.log('Component destroyed');
  }
}
```

## AfterViewInit and AfterContentInit

Called after child components/content are initialized:

```ts
ngAfterViewInit() {
  setTimeout(() => {
    this.childComponent.doSomething();
  });
}
```

## OnDestroy

Always unsubscribe from Observables:

```ts
ngOnDestroy() {
  this.mySubscription.unsubscribe();
  this.destroy$.next();
  this.destroy$.complete();
}
```