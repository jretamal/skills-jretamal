# Components

Angular components are the fundamental building blocks. Each component consists of a TypeScript class with behaviors, an HTML template, and a CSS selector.

## Component Definition

Use the `@Component` decorator.

```ts
import { Component } from '@angular/core';

@Component({
  selector: 'app-profile',
  template: `
    <img src="profile.jpg" alt="Profile photo" />
    <button (click)="save()">Save</button>
  `,
  styles: [`
    img {
      border-radius: 50%;
    }
  `]
})
export class ProfileComponent {
  save() {
    /* ... */
  }
}
```

## Metadata Options

- `selector`: CSS selector for the component.
- `template`: Inline HTML template.
- `templateUrl`: Path to external HTML file.
- `styles`: Inline CSS (array of strings).
- `styleUrl` / `styleUrls`: Path to external CSS.
- `directives`: Directives used in template.
- `encapsulation`: View encapsulation mode.

## Using Components

In Angular 5, components are declared in an NgModule:

```ts
import { NgModule } from '@angular/core';
import { CommonModule } from '@angular/common';

@NgModule({
  declarations: [ProfileComponent],
  imports: [CommonModule],
  exports: [ProfileComponent]
})
export class AppModule {}
```

Use in template:

```html
<app-profile></app-profile>
```

## Template Control Flow

Angular 5 uses `*ngIf` and `*ngFor`.

### Conditional Rendering

```html
<div *ngIf="user.isAdmin">Admin Dashboard</div>
<div *ngIf="user.isAdmin; else notAdmin">Admin Dashboard</div>
<ng-template #notAdmin>Standard Dashboard</ng-template>
```

### Loops

```html
<ul>
  <li *ngFor="let item of items; trackBy: trackById">{{ item.name }}</li>
</ul>
```

```ts
trackById(index: number, item: Item): number {
  return item.id;
}
```

### ngSwitch

```html
<div [ngSwitch]="status">
  <div *ngSwitchCase="'loading'">Loading...</div>
  <div *ngSwitchCase="'error'">Error!</div>
  <div *ngSwitchDefault>Unknown</div>
</div>
```

## Core Concepts

- **Host Element**: DOM element matching the selector.
- **View**: DOM rendered by the template.
- **Module-based**: Components declared in NgModule.
- **Component Tree**: Tree structure of components.