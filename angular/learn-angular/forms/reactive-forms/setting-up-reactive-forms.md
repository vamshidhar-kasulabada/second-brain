# Setting Up Reactive Forms

1. **Import Reactive Forms Module:**

   First, ensure that you have imported the `ReactiveFormsModule` in your Angular module:

   ```typescript
   import { ReactiveFormsModule } from '@angular/forms';

   @NgModule({
     imports: [
       // other imports
       ReactiveFormsModule
     ],
     // other module properties
   })
   export class AppModule { }
   ```

2. **Component Setup:**

   In your component, you'll need to import `FormGroup` and `FormControl` from `@angular/forms` and set up your form controls.

   ```typescript
   import { Component } from '@angular/core';
   import { FormGroup, FormControl } from '@angular/forms';

   @Component({
     selector: 'app-example-form',
     templateUrl: './example-form.component.html'
   })
   export class ExampleFormComponent {
     // Define a FormGroup instance
     myForm = new FormGroup({
       name: new FormControl(''),
       email: new FormControl(''),
     });

     onSubmit() {
       console.log(this.myForm.value); // Log form values on submit
     }
   }
   ```

3. **Template Setup:**

   In your component's template, use `formGroup` and `formControlName` to link the form controls to the component.

   ```html
   <form [formGroup]="myForm" (ngSubmit)="onSubmit()">
     <label for="name">Name:</label>
     <input id="name" formControlName="name">
     
     <label for="email">Email:</label>
     <input id="email" formControlName="email">
     
     <button type="submit">Submit</button>
   </form>
   ```

### Explanation of Key Concepts

- **FormGroup**: This is a collection of `FormControl` instances that are tracked together. It represents the entire form.

- **FormControl**: This tracks the value and validation status of an individual form input.

- **formControlName**: This directive binds the input element in the template to the corresponding `FormControl` in the `FormGroup`.

- **ngSubmit**: This event is triggered when the form is submitted. It allows you to define a method in your component to handle form submission.

# fromControlName VS [formControl]

### `formControlName`

- **Usage Context**: `formControlName` is used within a `FormGroup` context. It is typically used when you have a form that is built using a `FormGroup` and you want to bind individual controls within that group.

- **Syntax**: This directive is used without brackets and is a simple string that matches the name of the control in the `FormGroup`.

- **Example**:
  ```html
  <form [formGroup]="myForm">
    <input formControlName="name">
  </form>
  ```
  In this example, `name` is a control that is part of the `FormGroup` named `myForm`.

### `[formControl]`

- **Usage Context**: `[formControl]` is used to bind a standalone `FormControl` that is not part of a `FormGroup`. It is used when you have a single form control that you want to bind to an input element.

- **Syntax**: This directive is used with square brackets because it binds to a property of the component, which is a `FormControl` instance.

- **Example**:
  ```typescript
  myControl = new FormControl('');
  ```

  ```html
  <input [formControl]="myControl">
  ```
  In this example, `myControl` is a standalone `FormControl` instance that is directly bound to the input element.

### Summary

- Use `formControlName` when working within a `FormGroup` and you want to bind controls by name.
- Use `[formControl]` when dealing with standalone `FormControl` instances outside of a `FormGroup`.

Both methods are part of Angular's reactive forms module and allow you to handle form inputs with a model-driven approach.
