# Lazy Loading

Lazy loading loads modules when the user navigates to them, reducing initial bundle size.

## Lazy Loading a Module

```ts
const routes: Routes = [
  {
    path: 'users',
    loadChildren: () => import('./users/users.module').then(m => m.UsersModule)
  }
];
```

## Preloading Strategy

```ts
import { RouterModule, PreloadAllModules } from '@angular/router';

@NgModule({
  imports: [RouterModule.forRoot(routes, { preloadingStrategy: PreloadAllModules })]
})
export class AppModule {}
```

## Benefits

- Faster initial load time
- Better performance on slow connections