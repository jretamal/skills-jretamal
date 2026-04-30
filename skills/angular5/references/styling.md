# Styling Components

Angular components can define styles that apply to their template.

## Defining Styles

```ts
@Component({
  selector: 'app-photo',
  template: '<img src="photo.jpg" />',
  styles: ['img { border-radius: 50%; }']
})
export class PhotoComponent {}

// Or external file
@Component({
  selector: 'app-photo',
  templateUrl: 'photo.component.html',
  styleUrls: ['photo.component.css']
})
export class PhotoComponent {}
```

## View Encapsulation

| Mode | Behavior |
| :--- | :--- |
| Emulated (Default) | Scopes styles using unique attributes |
| ShadowDom | Uses browser's native Shadow DOM |
| None | Styles are global |

```ts
import { ViewEncapsulation } from '@angular/core';

@Component({
  encapsulation: ViewEncapsulation.None,
  selector: 'app-global',
  template: '...'
})
export class GlobalStyledComponent {}
```

## Special Selectors

### :host

```css
:host {
  display: block;
}
```

### :host-context

```css
:host-context(.theme-dark) {
  background: #333;
}
```

### ::ng-deep

```css
::ng-deep .child-component {
  /* Affects child components */
}
```

## Best Practices

- Use view encapsulation to prevent leakage
- Avoid ::ng-deep when possible