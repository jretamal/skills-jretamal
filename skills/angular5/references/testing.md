# Testing Fundamentals

This guide covers the fundamental principles for testing Angular applications using Jasmine and Karma.

## Core Setup

Install dependencies via Angular CLI:

```bash
ng test
```

This runs `karma.conf.js` and starts Karma server.

## Basic Test with TestBed

```ts
import { TestBed } from '@angular/core/testing';
import { MyComponent } from './my.component';

describe('MyComponent', () => {
  let component: MyComponent;
  let fixture: ComponentFixture<MyComponent>;

  beforeEach(async () => {
    await TestBed.configureTestingModule({
      declarations: [MyComponent]
    }).compileComponents();

    fixture = TestBed.createComponent(MyComponent);
    component = fixture.componentInstance;
    fixture.detectChanges();
  });

  it('should create', () => {
    expect(component).toBeTruthy();
  });
});
```

## ComponentFixture

- `fixture.componentInstance`: The component class
- `fixture.nativeElement`: The DOM element
- `fixture.detectChanges()`: Trigger change detection
- `fixture.whenStable()`: Wait for async operations

## Testing Services

```ts
import { TestBed } from '@angular/core/testing';
import { DataService } from './data.service';

describe('DataService', () => {
  let service: DataService;

  beforeEach(() => {
    TestBed.configureTestingModule({
      providers: [DataService]
    });
    service = TestBed.inject(DataService);
  });

  it('should return data', () => {
    service.getData().subscribe(data => {
      expect(data).toBeTruthy();
    });
  });
});
```

## Testing with HTTP

```ts
import { HttpClientTestingModule, HttpTestingController } from '@angular/common/http/testing';

TestBed.configureTestingModule({
  imports: [HttpClientTestingModule],
  providers: [DataService]
});

const httpMock = TestBed.inject(HttpTestingController);
```

## Best Practices

- Use TestBed for component tests
- Always call detectChanges() after changes
- Use fakeAsync() for timing tests