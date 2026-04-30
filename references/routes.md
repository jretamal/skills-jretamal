# Routes

Routes define which component renders for a URL path.

## Basic Configuration

```ts
import { Routes } from '@angular/router';

const routes: Routes = [
  { path: '', component: HomePageComponent },
  { path: 'users', component: UserListComponent },
  { path: 'user/:id', component: UserDetailComponent },
  { path: '**', component: NotFoundComponent }
];
```

## RouterModule

Configure in NgModule:

```ts
@NgModule({
  imports: [RouterModule.forRoot(routes)]
})
export class AppModule {}
```

## Route Parameters

```ts
{ path: 'user/:id', component: UserDetailComponent }
```

Access in component:

```ts
import { ActivatedRoute } from '@angular/router';

constructor(private route: ActivatedRoute) {
  const id = this.route.snapshot.paramMap.get('id');
  this.route.paramMap.subscribe(params => {
    const id = params.get('id');
  });
}
```

## Redirects

```ts
{ path: 'users', redirectTo: '/admin/users' }
```

## Child Routes

```ts
{
  path: 'product/:id',
  component: ProductComponent,
  children: [
    { path: 'info', component: ProductInfoComponent },
    { path: 'reviews', component: ProductReviewsComponent }
  ]
}
```

```html
<router-outlet></router-outlet>
```

## Best Practices

- Use wildcards (`**`) for 404 at the end
- Use route parameters for dynamic paths