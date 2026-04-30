# Reactive Forms

Reactive forms provide a model-driven approach to handling form inputs.

## Core Classes

From `@angular/forms`:
- `FormControl`: Manages value and validity of an input.
- `FormGroup`: Manages a group of controls.
- `FormArray`: Manages an array of controls.
- `FormBuilder`: Factory for creating controls.

## Setup

Import `ReactiveFormsModule`:

```ts
import { ReactiveFormsModule } from '@angular/forms';

@NgModule({
  imports: [ReactiveFormsModule]
})
export class AppModule {}
```

## Using FormBuilder

```ts
import { FormBuilder, FormGroup, Validators } from '@angular/forms';

@Component({ selector: 'app-profile-editor', templateUrl: './profile-editor.html' })
export class ProfileEditorComponent {
  profileForm: FormGroup;
  
  constructor(private fb: FormBuilder) {
    this.profileForm = this.fb.group({
      firstName: ['', Validators.required],
      lastName: [''],
      address: this.fb.group({
        street: [''],
        city: ['']
      }),
      aliases: this.fb.array([])
    });
  }
}
```

## Template Binding

```html
<form [formGroup]="profileForm" (ngSubmit)="onSubmit()">
  <input type="text" formControlName="firstName" />
  
  <div formGroupName="address">
    <input type="text" formControlName="street" />
  </div>
  
  <button type="submit" [disabled]="!profileForm.valid">Submit</button>
</form>
```

## Accessing Controls

```ts
get aliases() {
  return this.profileForm.get('aliases') as FormArray;
}

addAlias() {
  this.aliases.push(this.fb.control(''));
}
```

## Updating Values

- `patchValue()`: Partial update
- `setValue()`: Full model replacement

```ts
updateProfile() {
  this.profileForm.patchValue({ firstName: 'Nancy' });
}
```

## Value Changes

```ts
this.profileForm.valueChanges.subscribe(value => {
  console.log('Form value:', value);
});
```

## Best Practices

- Use for complex forms
- Use `patchValue` for partial updates