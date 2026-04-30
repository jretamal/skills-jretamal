# NgModule

NgModule organizes and configures an Angular application.

## Creating an NgModule

```ts
import { NgModule } from '@angular/core';
import { CommonModule } from '@angular/common';
import { FormsModule } from '@angular/forms';

@NgModule({
  declarations: [AppComponent, UserComponent, UserPipe],
  imports: [CommonModule, FormsModule],
  exports: [UserComponent],
  providers: [UserService],
  bootstrap: [AppComponent]
})
export class AppModule {}
```

## Module Properties

| Property | Description |
| :--- | :--- |
| declarations | Components, directives, pipes belonging to this module |
| imports | Modules this module needs |
| exports | Components available to other modules |
| providers | Services application-wide |
| bootstrap | Root component (only in root module) |

## Feature Modules

```ts
@NgModule({
  declarations: [UserComponent],
  imports: [CommonModule, FormsModule],
  exports: [UserComponent]
})
export class UserModule {}
```

## Lazy Loading

```ts
const routes: Routes = [
  { path: 'users', loadChildren: () => import('./users/users.module').then(m => m.UsersModule) }
];
```

## Shared Module

```ts
@NgModule({
  declarations: [MaybeUsedPipe],
  imports: [CommonModule],
  exports: [CommonModule, MaybeUsedPipe]
})
export class SharedModule {}
```

## Best Practices

- Each feature gets its own module
- Use SharedModule for common directives