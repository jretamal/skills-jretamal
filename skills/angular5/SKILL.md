---
name: angular5
description: Generates Angular 5 code with TypeScript 2.5 patterns. Trigger when working specifically with Angular 5 projects or when compatibility with Angular 5 is required.
license: MIT
metadata:
  author: jretamal
  version: '1.0'
---

# Angular 5 + TypeScript 2.5 Developer Guidelines

1. This skill is exclusively for Angular 5 projects using TypeScript 2.5.

2. When generating code, follow Angular 5 conventions. Use the Angular CLI for scaffolding.

3. Once you finish generating code, run `ng build` to ensure there are no build errors.

## Creating New Projects

**Execution Rules for `ng new`:**

- **Step 1: Check for an explicit user version.**
  - **IF** the user requests Angular 5, use `npx @angular/cli@5 new <project-name>`.
  - **Command:** `npx @angular/cli@5 new <project-name>`

- **Step 2: Check for an existing Angular installation.**
  - **IF** no specific version is requested, run `ng version`.
  - **IF** installed, use `ng new <project-name>`

- **Step 3: Fallback.**
  - **IF** no installation exists, use `npx @angular/cli@5 new <project-name>`

## Key Differences in Angular 5 + TypeScript 2.5

Angular 5 with TypeScript 2.5 uses:

- **Decorators**: `@Component`, `@Injectable`, `@Input`, `@Output`
- **Strict typing**: TypeScript 2.5 features
- **Generic types**: Full generic support

## Components

- **Fundamentals**: Component structure, metadata. Read [components.md](references/components.md)
- **Inputs**: Using @Input(). Read [inputs.md](references/inputs.md)
- **Outputs**: Using @Output() with EventEmitter. Read [outputs.md](references/outputs.md)
- **Lifecycle**: ngOnInit, ngOnChanges. Read [lifecycle.md](references/lifecycle.md)

For docs: `https://v5.angular.io/docs`.

## Reactivity

- **Observables**: RxJS Observables. Read [observables.md](references/observables.md)
- **BehaviorSubject**: State management. Read [behavior-subject.md](references/behavior-subject.md)
- **Async Pipe**: Auto-unsubscribe. Read [async-pipe.md](references/async-pipe.md)

## Forms

- **Reactive Forms**: Complex forms. Read [reactive-forms.md](references/reactive-forms.md)
- **Template-driven**: Simple forms. Read [template-driven-forms.md](references/template-driven-forms.md)

## Dependency Injection

- **Fundamentals**: DI overview. Read [di-fundamentals.md](references/di-fundamentals.md)
- **Services**: @Injectable. Read [services.md](references/services.md)
- **NgModule**: Module system. Read [ngmodule.md](references/ngmodule.md)

## Routing

- **Routes**: URL paths. Read [routes.md](references/routes.md)
- **Lazy Loading**: loadChildren. Read [lazy-loading.md](references/lazy-loading.md)
- **Guards**: CanActivate. Read [guards.md](references/guards.md)

## Styling

- **Component Styles**: Scoped styles. Read [styling.md](references/styling.md)

## Testing

- **Testing**: Jasmine/Karma. Read [testing.md](references/testing.md)
- **Component Testing**: TestBed. Read [component-testing.md](references/component-testing.md)

## CLI

- **Commands**: ng generate, ng build. Read [cli.md](references/cli.md)
