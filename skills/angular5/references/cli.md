# Angular CLI

The Angular CLI (`ng`) is the primary tool for managing an Angular workspace.

## Managing Dependencies

Use `ng add` for Angular libraries:

```bash
ng add @angular/material
ng add @angular/pwa
```

Use `ng update` for Angular versions:

```bash
ng update @angular/core@15 @angular/cli@15
```

## Generating Code

Use `ng generate` or `ng g`:

| Target | Command |
| :--- | :--- |
| Component | `ng g c path/to/name` |
| Service | `ng g s path/to/name` |
| Directive | `ng g d path/to/name` |
| Pipe | `ng g p path/to/name` |
| Class | `ng g class path/to/name` |
| Guard | `ng g g path/to/name` |
| Module | `ng g m path/to/name` |

Options:
- `--flat`: Put file in src/app instead of directory
- `--inline-template`: Use inline template
- `--inline-style`: Use inline styles

## Development Server

```bash
ng serve
ng serve --open
ng serve --port 4201
```

## Building

```bash
ng build
ng build --configuration=production
```

Output in `dist/<project-name>/`.

## Running Tests

```bash
ng test
ng test --watch=false
ng e2e
```

## Linting

```bash
ng lint
```

## Best Practices

- Always use CLI to generate code
- Use `ng add` for adding Angular packages
- Use `ng update` for version updates