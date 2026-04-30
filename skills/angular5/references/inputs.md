# Inputs

Inputs allow data to flow from parent to child using `@Input()` decorator.

## Using @Input()

```ts
import { Component, Input } from '@angular/core';

@Component({
  selector: 'app-user',
  template: `<p>User: {{ name }} ({{ age }})</p>`
})
export class UserComponent {
  @Input() name: string = 'Guest';
  @Input() age: number = 0;
}
```

## Usage in Template

```html
<app-user [name]="userName" [age]="25"></app-user>
```

## Setters for Transformation

Use an input setter to transform the value:

```ts
@Input()
set disabled(value: boolean) {
  this._disabled = value;
}

get disabled(): boolean {
  return this._disabled;
}
private _disabled = false;
```

## Alias

```ts
@Input('btnLabel')
label: string = '';
```

```html
<app-user btnLabel="Submit"></app-user>
```

## Best Practices

- Use `@Input()` for parent-to-child data flow.
- Use setters for transformation.
- Use `ngOnChanges` to react to input changes.