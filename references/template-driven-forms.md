# Template-Driven Forms

Template-driven forms use two-way binding with `[(ngModel)]`.

## Setup

Import `FormsModule`:

```ts
import { FormsModule } from '@angular/forms';

@NgModule({
  imports: [FormsModule]
})
export class AppModule {}
```

## Building the Form

```html
<form #userForm="ngForm" (ngSubmit)="onSubmit()">
  <div>
    <label>Name:</label>
    <input type="text" [(ngModel)]="user.name" name="name" required />
  </div>
  
  <div>
    <label>Role:</label>
    <select [(ngModel)]="user.role" name="role">
      <option value="Admin">Admin</option>
      <option value="Guest">Guest</option>
    </select>
  </div>
  
  <button type="submit" [disabled]="!userForm.form.valid">Submit</button>
</form>
```

```ts
export class UserFormComponent {
  user = { name: '', role: 'Guest' };
  
  onSubmit() {
    console.log('Form submitted:', this.user);
  }
}
```

## Form Control State

CSS classes:
- ng-touched / ng-untouched
- ng-dirty / ng-pristine
- ng-valid / ng-invalid

```css
.ng-valid[required] {
  border-left: 5px solid #42a948;
}
.ng-invalid:not(form) {
  border-left: 5px solid #a94442;
}
```

## Validation Messages

```html
<input type="text" [(ngModel)]="user.name" name="name" 
  #nameCtrl="ngModel" required />

<div *ngIf="nameCtrl.invalid && (nameCtrl.dirty || nameCtrl.touched)">
  <div *ngIf="nameCtrl.errors?.['required']">Name is required.</div>
</div>
```

## Resetting

```html
<button type="button" (click)="userForm.reset()">Reset</button>
```

## Best Practices

- Use for simple forms
- Use `[(ngModel)]` with `name` attribute