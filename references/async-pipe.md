# Async Pipe

The `async` pipe subscribes to an Observable/Promise automatically and unsubscribes on destroy.

## Basic Usage

```ts
import { CommonModule } from '@angular/common';

@Component({
  selector: 'app-user-list',
  imports: [CommonModule],
  template: `
    <ul>
      <li *ngFor="let user of users$ | async">{{ user.name }}</li>
    </ul>
  `
})
export class UserListComponent {
  users$ = this.userService.getUsers();
  
  constructor(private userService: UserService) {}
}
```

## With ngIf

```html
<div *ngIf="user$ | async as user">
  <p>{{ user.name }}</p>
</div>
```

## With Promises

```ts
userPromise: Promise<User>;

@Component({...})
export class AppComponent {
  userPromise = this.userService.getUser();
}
```

```html
<div *ngIf="userPromise | async as user">
  {{ user.name }}
</div>
```

## Without async Pipe

```ts
ngOnInit() {
  this.users$ = this.userService.getUsers();
  this.users$.subscribe(users => this.users = users);
}
```

## Best Practices

- Always use async pipe to prevent memory leaks
- Don't subscribe manually unless necessary