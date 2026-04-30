# Services

Services are reusable code for data fetching, business logic, or state management.

## Creating a Service

```ts
import { Injectable } from '@angular/core';
import { HttpClient } from '@angular/common/http';

@Injectable({
  providedIn: 'root'
})
export class DataService {
  constructor(private http: HttpClient) {}
  
  getData() {
    return this.http.get('/api/data');
  }
}
```

## Using ProvidedIn: 'root'

Creates a singleton, auto-available, enables tree-shaking.

## Injecting into Components

```ts
@Component({
  selector: 'app-example',
  template: '...'
})
export class ExampleComponent implements OnInit {
  constructor(private dataService: DataService) {}
  
  ngOnInit() {
    this.dataService.getData().subscribe(data => {
      console.log(data);
    });
  }
}
```

## Component-Specific Services

```ts
@Component({
  selector: 'app-local',
  providers: [LocalService]
})
export class LocalComponent {}
```

## Best Practices

- Use `providedIn: 'root'` for shared services
- Use constructor injection