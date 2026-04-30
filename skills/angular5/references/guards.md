# Route Guards

Route guards control whether a user can navigate to or leave a route.

## CanActivate

Controls access to a route:

```ts
import { Injectable } from '@angular/core';
import { CanActivate, ActivatedRouteSnapshot, RouterStateSnapshot, Router } from '@angular/router';
import { AuthService } from './auth.service';

@Injectable({ providedIn: 'root' })
export class AuthGuard implements CanActivate {
  constructor(private authService: AuthService, private router: Router) {}
  
  canActivate(
    route: ActivatedRouteSnapshot,
    state: RouterStateSnapshot
  ): boolean {
    if (this.authService.isLoggedIn()) {
      return true;
    }
    this.router.navigate(['/login']);
    return false;
  }
}
```

## CanActivateChild

Controls access to child routes:

```ts
@Injectable({ providedIn: 'root' })
export class AdminGuard implements CanActivateChild {
  constructor(private authService: AuthService, private router: Router) {}
  
  canActivateChild(
    route: ActivatedRouteSnapshot,
    state: RouterStateSnapshot
  ): boolean {
    return this.canActivate(route, state);
  }
}
```

## CanDeactivate

Controls navigation away from a route:

```ts
import { CanDeactivate } from '@angular/router';
import { CanComponentDeactivate } from './can-deactivate.interface';

export class CanDeactivateGuard implements CanDeactivate<CanComponentDeactivate> {
  canDeactivate(component: CanComponentDeactivate): boolean {
    return component.canDeactivate ? component.canDeactivate() : true;
  }
}
```

## Applying Guards

```ts
const routes: Routes = [
  {
    path: 'admin',
    component: AdminComponent,
    canActivate: [AuthGuard],
    canActivateChild: [AdminGuard]
  }
];
```

## Best Practices

- Use guards for route security (always validate on server too)