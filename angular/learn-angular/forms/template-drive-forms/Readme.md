### Template-driven Forms in Angular

Template-driven forms are a simple and straightforward way to handle form data in Angular applications. They are ideal for smaller forms and applications where you can leverage Angular's two-way data binding.

---

#### Key Features

- **Simplicity**: Less code compared to reactive forms, with much of the logic handled in the template.
- **Two-way Data Binding**: Uses Angular’s `ngModel` directive for easy data binding.
- **Automatic Form Validation**: Angular provides built-in directives for common validation tasks.
- **Ease of Use**: Ideal for simple forms where advanced form control is not required.

---

#### Setup

1. **Import FormsModule**: Ensure `FormsModule` is imported in your Angular module.

   ```typescript
   import { NgModule } from '@angular/core';
   import { BrowserModule } from '@angular/platform-browser';
   import { FormsModule } from '@angular/forms';

   @NgModule({
     imports: [
       BrowserModule,
       FormsModule
     ],
     declarations: [ /* your components */ ],
     bootstrap: [ /* your root component */ ]
   })
   export class AppModule { }
   ```

2. **Define the Form Model**: Create a model in your component class to hold form data.

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

3. **Create the Form in Template**: Use `ngModel` for two-way data binding in your HTML template.

   ```html
   <form (ngSubmit)="onSubmit()" #form="ngForm">
     <label for="name">Name:</label>
     <input id="name" [(ngModel)]="model.name" name="name" required>

     <label for="email">Email:</label>
     <input id="email" [(ngModel)]="model.email" name="email" required>

     <button type="submit" [disabled]="form.invalid">Submit</button>
   </form>
   ```

---

#### Key Directives and Usage

- **`ngModel`**: Binds the form input to a property in the component's class.
- **`ngForm`**: Automatically created directive that tracks the form state.
- **`required`, `minlength`, `maxlength`, etc.**: HTML5 and Angular validation attributes for form controls.
- **`ngSubmit`**: Event binding to handle form submission.

---

#### Validation

- Angular provides built-in validation using attributes like `required`, `minlength`, `maxlength`, etc.
- Validation state can be accessed through the form's controls, e.g., `form.controls['name'].valid`.

---

#### Advantages

- **Ease of Setup**: Quick to set up for simple forms.
- **Declarative Approach**: Uses HTML to define form logic, making it easier to read and maintain for small applications.

---

#### Limitations

- **Scalability**: Not as scalable for large forms or complex validation logic.
- **Control**: Less programmatic control over form state and validation compared to reactive forms.
