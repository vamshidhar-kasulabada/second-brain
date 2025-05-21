### Angular Forms Overview

Angular provides two main ways to handle forms:

1. [Template-Drive Froms](./template-drive-forms/Readme.md): Simpler and suitable for smaller forms. They rely on Angular's two-way data binding and directives in templates.

2. [Reactive Forms](./reactive-forms/Readme.md): More robust and suitable for complex forms, offering greater control over form validation and state management.

---

### Template-driven Forms

- **Module Required**: Import `FormsModule` from `@angular/forms` in your module.

- **Setup**:
  - Define the form directly in the HTML template.
  - Use `ngModel` for two-way data binding.
  - Handle form submission using the `(ngSubmit)` directive.

- **Example**:
  ```html
  <form (ngSubmit)="onSubmit()" #form="ngForm">
    <label for="name">Name:</label>
    <input id="name" [(ngModel)]="model.name" name="name" required>

    <label for="email">Email:</label>
    <input id="email" [(ngModel)]="model.email" name="email" required>

    <button type="submit" [disabled]="form.invalid">Submit</button>
  </form>
  ```

- **Component Setup**:
  ```typescript
  import { Component } from '@angular/core';

  @Component({
    selector: 'app-my-form',
    templateUrl: './my-form.component.html',
  })
  export class MyFormComponent {
    model = {
      name: '',
      email: ''
    };

    onSubmit() {
      console.log(this.model);
    }
  }
  ```

---

### Reactive Forms

- **Module Required**: Import `ReactiveFormsModule` from `@angular/forms` in your module.

- **Setup**:
  - Create forms programmatically using `FormGroup` and `FormControl`.
  - Bind the form to the template using the `[formGroup]` directive.
  - Use `formControlName` to connect inputs to form controls.

- **Example**:
  ```typescript
  import { Component } from '@angular/core';
  import { FormGroup, FormControl } from '@angular/forms';

  @Component({
    selector: 'app-my-form',
    templateUrl: './my-form.component.html',
  })
  export class MyFormComponent {
    myForm = new FormGroup({
      name: new FormControl(''),
      email: new FormControl(''),
    });

    onSubmit() {
      console.log(this.myForm.value);
    }
  }
  ```

- **Template Binding**:
  ```html
  <form [formGroup]="myForm" (ngSubmit)="onSubmit()">
    <label for="name">Name:</label>
    <input id="name" formControlName="name">

    <label for="email">Email:</label>
    <input id="email" formControlName="email">

    <button type="submit">Submit</button>
  </form>
  ```

---

### Choosing Between the Two

- **Template-driven Forms**:
  - Best for simple forms and smaller applications.
  - Easier to set up with less boilerplate code.
  - Automatically handles form state and validation.

- **Reactive Forms**:
  - Ideal for complex forms and larger applications.
  - Offers more control and flexibility over form state and validation.
  - More scalable and testable.
