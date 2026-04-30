# Component Testing

Testing Angular components with TestBed.

## Basic Component Test

```ts
import { ComponentFixture, TestBed } from '@angular/core/testing';
import { UserComponent } from './user.component';

describe('UserComponent', () => {
  let component: UserComponent;
  let fixture: ComponentFixture<UserComponent>;

  beforeEach(async () => {
    await TestBed.configureTestingModule({
      declarations: [UserComponent]
    }).compileComponents();

    fixture = TestBed.createComponent(UserComponent);
    component = fixture.componentInstance;
  });

  it('should create', () => {
    expect(component).toBeTruthy();
  });
});
```

## Testing with Input

```ts
it('should display user name', () => {
  component.user = { name: 'John', age: 25 };
  fixture.detectChanges();
  
  const element = fixture.nativeElement;
  expect(element.querySelector('p').textContent).toContain('John');
});
```

## Testing with Output

```ts
it('should emit event on click', () => {
  spyOn(component.valueChanged, 'emit');
  
  const button = fixture.nativeElement.querySelector('button');
  button.click();
  
  expect(component.valueChanged.emit).toHaveBeenCalledWith(10);
});
```

## Using DebugElement

```ts
import { By } from '@angular/platform-browser';

it('should find button with CSS', () => {
  const button = fixture.debugElement.query(By.css('button'));
  button.triggerEventHandler('click', null);
});
```

## Component with Dependencies

```ts
beforeEach(async () => {
  await TestBed.configureTestingModule({
    declarations: [UserListComponent],
    providers: [UserService]
  }).compileComponents();
  
  const userService = TestBed.inject(UserService);
  spyOn(userService, 'getUsers').and.returnValue(of([{name: 'John'}]));
});
```

## Testing Forms

```ts
import { ReactiveFormsModule } from '@angular/forms';

await TestBed.configureTestingModule({
  declarations: [ProfileEditorComponent],
  imports: [ReactiveFormsModule]
}).compileComponents();
```

## Testing Async Operations

```ts
it('should load users', fakeAsync(() => {
  component.ngOnInit();
  tick();
  
  expect(component.users.length).toBe(2);
}));
```

## Best Practices

- Always test component creation
- Use detectChanges after input changes
- Use fakeAsync for timing