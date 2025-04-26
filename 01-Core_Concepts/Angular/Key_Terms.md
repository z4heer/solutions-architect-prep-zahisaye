# Angular Key Terms

Angular is a powerful framework for building single-page web applications (SPA) with a strong emphasis on component-based architecture. This document covers essential key terms, interview questions, code snippets, and best practices for Angular development.

---

## 🧠 Mind Map

**Core Angular Concepts**:

- **Components**
  - Template
  - Styles
  - Class
- **Modules**
  - NgModule
  - Lazy Loading
- **Services**
  - Dependency Injection
  - Singleton
- **Directives**
  - Structural
  - Attribute
- **Pipes**
  - Built-in Pipes
  - Custom Pipes
- **Routing**
  - RouterModule
  - Navigation
- **Forms**
  - Template-driven Forms
  - Reactive Forms
- **Observables**
  - RxJS
  - Subjects

---

## 🧑‍💻 Key Technical Words & Definitions

1. **Component**: The fundamental building block in Angular that controls a part of the UI. Components consist of a TypeScript class, HTML template, and CSS styles.
   
2. **Module**: A logical container for grouping related components, services, directives, and pipes in an Angular application. The `NgModule` decorator defines a module.

3. **Service**: A class that is used to share data or logic across multiple components. Services are typically injected into components using Angular's **Dependency Injection** system.

4. **Directive**: An Angular feature that allows the modification of DOM behavior. There are two types:
   - **Structural Directives**: Modify the structure of the DOM (e.g., `*ngIf`, `*ngFor`).
   - **Attribute Directives**: Modify the appearance or behavior of elements (e.g., `ngClass`, `ngStyle`).

5. **Pipe**: A mechanism for transforming data in templates. Angular comes with several built-in pipes (e.g., `date`, `currency`), and developers can also create custom pipes.

6. **RxJS**: A library for reactive programming using observables. It allows asynchronous events and data streams to be handled in a declarative manner.

7. **Dependency Injection (DI)**: A design pattern used by Angular to manage the injection of services into components, directives, and other services.

8. **Routing**: A system in Angular that helps navigate between views or pages, utilizing the `RouterModule` and URL paths.

9. **Observables**: A core concept in Angular for handling asynchronous data streams, often used with services and HTTP requests. 

10. **Forms**: Angular supports two types of forms:
    - **Template-driven Forms**: Simple forms based on HTML templates and Angular directives.
    - **Reactive Forms**: More complex forms with explicit control over form models in TypeScript.

---

## 🎯 Common Interview Questions

1. **What are Angular Components and how do they interact with each other?**
   - Components control parts of the UI and interact through input/output properties and event binding.

2. **Explain Dependency Injection in Angular.**
   - DI allows services and other dependencies to be injected into Angular components, services, or directives.

3. **What is the difference between template-driven forms and reactive forms in Angular?**
   - Template-driven forms use directives in the template to create forms, while reactive forms are model-driven and created in the component using `FormGroup` and `FormControl`.

4. **How does Angular handle two-way data binding?**
   - Angular uses `[(ngModel)]` to bind input fields to component properties, enabling two-way binding.

5. **What is the purpose of the Angular Router and how is it implemented?**
   - The Router enables navigation between views or pages within the application. Routes are defined in `RouterModule`, and navigation is triggered using `routerLink` or programmatically through the router service.

6. **What are Angular lifecycle hooks, and what are some examples?**
   - Lifecycle hooks are methods that allow developers to tap into key events in a component's lifecycle (e.g., `ngOnInit()`, `ngOnChanges()`, `ngOnDestroy()`).

---

## 💻 Code Snippet

### Creating a Basic Angular Component

```typescript
import { Component } from '@angular/core';

@Component({
  selector: 'app-hello-world',
  template: `<h1>{{ message }}</h1>`,
  styleUrls: ['./hello-world.component.css']
})
export class HelloWorldComponent {
  message = 'Hello, World!';
}
```

### Using Dependency Injection in a Service

```typescript
import { Injectable } from '@angular/core';

@Injectable({
  providedIn: 'root',
})
export class MyService {
  getData() {
    return 'Some data';
  }
}
```

### Using Observables with HTTP Request

```typescript
import { Component, OnInit } from '@angular/core';
import { HttpClient } from '@angular/common/http';
import { Observable } from 'rxjs';

@Component({
  selector: 'app-data-fetch',
  template: `<div>{{ data }}</div>`,
})
export class DataFetchComponent implements OnInit {
  data: string;

  constructor(private http: HttpClient) {}

  ngOnInit() {
    this.fetchData().subscribe(data => {
      this.data = data;
    });
  }

  fetchData(): Observable<string> {
    return this.http.get<string>('https://api.example.com/data');
  }
}
```

---

## 📝 Best Practices Summary

1. **Modular Architecture**: Break down large applications into smaller, feature-based modules. Use `NgModule` to logically group related components, services, and pipes.
   
2. **Lazy Loading**: Implement lazy loading for modules that are not required initially, which helps to reduce the initial bundle size and improve application performance.

3. **Separation of Concerns**: Keep business logic in services and UI logic in components. This promotes reusability and testability.

4. **Unidirectional Data Flow**: Ensure that data flows in a predictable and structured manner by using services and inputs/outputs for communication between components.

5. **Strong Typing with TypeScript**: Leverage TypeScript's static typing to prevent runtime errors and improve maintainability.

6. **Error Handling**: Handle errors gracefully in services and components, especially when dealing with HTTP requests or async operations.

7. **Performance Optimization**: Use `ChangeDetectionStrategy.OnPush` for improved performance in complex applications. Optimize HTTP requests by using caching or pagination.

---

## 📋 Cheat Sheet Summary

- **Component Declaration**: 
  - `@Component()` decorator, template, and styles.
  
- **Dependency Injection**:
  - `@Injectable()`, `providedIn: 'root'` for service injection.

- **Routing**:
  - Use `RouterModule` to define routes.
  - Navigate with `routerLink` or `this.router.navigate()`.

- **Forms**:
  - Template-driven forms: `ngModel`, `ngSubmit`.
  - Reactive forms: `FormGroup`, `FormControl`, `FormBuilder`.

- **Directives**:
  - Structural: `*ngIf`, `*ngFor`.
  - Attribute: `ngClass`, `ngStyle`.

- **HTTP Requests**:
  - Use `HttpClient` for API calls, e.g., `http.get()`, `http.post()`.

- **Lifecycle Hooks**:
  - `ngOnInit()`, `ngOnChanges()`, `ngOnDestroy()`.

---

## ⚡ Common Mistakes

1. **Not Using `OnPush` Change Detection**: Failing to use `ChangeDetectionStrategy.OnPush` when appropriate can lead to performance bottlenecks, especially in larger applications.

2. **Direct Manipulation of the DOM**: Avoid direct DOM manipulation using native JavaScript methods. Instead, rely on Angular’s directives like `*ngFor` and `*ngIf`.

3. **Improper Use of `ngModel`**: While `ngModel` is useful for two-way data binding in template-driven forms, it can lead to performance issues in complex forms. Consider using reactive forms for better control.

4. **Overuse of Services**: It’s tempting to put all business logic in services, but this can lead to bloated services. Use components for presentation and services strictly for data handling.

5. **Not Unsubscribing from Observables**: Always unsubscribe from observables when they are no longer needed (e.g., HTTP calls or subscriptions), or use `async` pipe to handle automatic unsubscription.

6. **Ignoring Unit Testing**: Not writing unit tests for components, services, or pipes can result in bugs that are hard to catch early. Use Jasmine and Karma for testing Angular applications.

---

## 🔍 Further Reading

- [Angular Documentation](https://angular.io/docs)
- [RxJS Documentation](https://rxjs-dev.firebaseapp.com/)
- [Angular Change Detection](https://angular.io/guide/change-detection)
- [Angular Lifecycle Hooks](https://angular.io/guide/lifecycle-hooks)
