# Custom Validators


### Custom Validator Example: Minimum Age Validator

Let's create a custom validator that checks if the user's age is above a minimum age requirement.

1. **Define the Validator Function:**

   This function will check if the age is at least a certain value (e.g., 18).

   ```typescript
   import { AbstractControl, ValidationErrors } from '@angular/forms';

   export function minimumAgeValidator(minAge: number) {
     return (control: AbstractControl): ValidationErrors | null => {
       const age = control.value;
       if (age !== null && age < minAge) {
         return { minimumAge: { requiredAge: minAge, actualAge: age } };
       }
       return null;
     };
   }
   ```

2. **Use the Custom Validator in a FormControl:**

   Apply this custom validator to a `FormControl` for age.

   ```typescript
   import { Component } from '@angular/core';
   import { FormGroup, FormControl } from '@angular/forms';
   import { minimumAgeValidator } from './path-to-your-validator';

   @Component({
     selector: 'app-example-form',
     templateUrl: './example-form.component.html'
   })
   export class ExampleFormComponent {
     myForm = new FormGroup({
       age: new FormControl('', [minimumAgeValidator(18)]),
     });

     onSubmit() {
       console.log(this.myForm.value);
     }
   }
   ```

3. **Display Validation Errors in the Template:**

   Use the template to show an error message if the validation fails.

   ```html
   <form [formGroup]="myForm" (ngSubmit)="onSubmit()">
     <label for="age">Age:</label>
     <input id="age" formControlName="age" type="number">
     <div *ngIf="myForm.get('age').hasError('minimumAge')">
       You must be at least {{ myForm.get('age').getError('minimumAge').requiredAge }} years old. Your age is {{ myForm.get('age').getError('minimumAge').actualAge }}.
     </div>
     <button type="submit">Submit</button>
   </form>
   ```

### Explanation

- **Validator Function:** The `minimumAgeValidator` function takes a `minAge` parameter and returns a validation function. This function checks if the control's value is less than the minimum age and returns an error object if it is.

- **Applying Validator:** When creating the `FormControl` for age, the custom validator is included in the array of validators.

- **Error Handling:** In the template, the `hasError` and `getError` methods are used to check and display the error message, showing the required and actual age.
