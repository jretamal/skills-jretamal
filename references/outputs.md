# Outputs (Custom Events)

Outputs allow a child component to emit custom events using `@Output()` with `EventEmitter`.

## Using @Output()

```ts
import { Component, Output, EventEmitter } from '@angular/core';

@Component({
  selector: 'custom-slider',
  template: `<button (click)="changeValue(50)">Set to 50</button>`
})
export class CustomSliderComponent {
  @Output() valueChanged = new EventEmitter<number>();
  @Output() panelClosed = new EventEmitter<void>();

  changeValue(newValue: number) {
    this.valueChanged.emit(newValue);
  }
}
```

## Usage in Template

Bind to the event using parentheses:

```html
<custom-slider (valueChanged)="onValueChange($event)" (panelClosed)="onPanelClosed()"></custom-slider>
```

## Alias

```ts
@Output('customEventName')
changed = new EventEmitter<void>();
```

```html
<custom-slider (customEventName)="handler()"></custom-slider>
```

## Programmatic Subscription

```ts
@Output() myEvent = new EventEmitter<string>();

ngAfterViewInit() {
  this.childComponent.myEvent.subscribe((value) => {
    console.log('Event received:', value);
  });
}
```

## Two-Way Binding

```ts
@Input() value: number;
@Output() valueChange = new EventEmitter<number>();
```

```html
<custom-counter [(value)]="count"></custom-counter>
```

## Best Practices

- Use `EventEmitter` with `@Output()` for child-to-parent.
- Use camelCase for event names.
- Avoid prefixing with `on`.