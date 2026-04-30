# Dependency Injection Fundamentals

DI is a design pattern to organize and share code across an application.

## Two Ways

1. **Providing**: Making values available.
2. **Injecting**: Asking for those values.

## Services

A service is a TypeScript class decorated with `@Injectable()`.

```ts
import { Injectable } from '@angular/core';

@Injectable({
  providedIn: 'root'
})
export class AnalyticsLogger {
  trackEvent(category: string, value: string) {
    console.log('Analytics:', { category, value });
  }
}
```

## Injecting Dependencies

### Constructor Injection

```ts
@Component({ selector: 'app-navbar', template: '...' })
export class NavbarComponent {
  constructor(private analytics: AnalyticsLogger) {}
}
```

### Using inject()

```ts
import { Component, inject } from '@angular/core';
import { Router } from '@angular/router';

@Component({ selector: 'app-navbar', template: '...' })
export class NavbarComponent {
  private router = inject(Router);
}
```

## Where inject() Works

- Class field initializers
- Constructor body
- Factory functions

## Common Uses

- Data fetching
- State management
- Authentication

## Best Practices

- Use constructor injection
- Use `providedIn: 'root'` for singletons