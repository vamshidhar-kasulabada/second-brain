Property binding in Angular is a fundamental technique for establishing a one-way data flow from your component's TypeScript code to the properties of HTML elements or even child components within your templates. It allows you to dynamically update the appearance or behavior of elements based on changes in your component's data.

**How it works:**

1. **Source:** You have a property in your component's TypeScript class that holds the data you want to bind.
2. **Target:** You identify the target HTML element or component property in your template where you want to display or use the data.
3. **Binding Syntax:** You use the square brackets `[]` around the target property within the template and assign it to the source property from your component.

**Example:**

```typescript
// app.component.ts
import { Component } from '@angular/core';

@Component({
  selector: 'app-root',
  template: `
    <input type="text" [value]="username">
  `
})
export class AppComponent {
  username = 'John Doe'; 
}
```

In this example:

- `username` is the **source** property in the component.
- `value` is the **target** property of the `<input>` element.
- `[value]="username"` establishes the **property binding**.

Whenever the value of `username` changes in the component, Angular will automatically update the `value` property of the input field, ensuring that they stay in sync.

**Key points:**

- **One-Way Binding:**  Property binding is one-way; changes in the target element (e.g., user input in the text field) don't automatically update the source property in the component. For two-way data flow, you'll need two-way binding with `[(ngModel)]`. 
- **Versatile Usage:**  You can use property binding to set values for various attributes, such as `src` for images, `disabled` for buttons, and more.
- **Dynamic Updates:**  Any changes to the source property in the component are reflected in the target element dynamically and efficiently due to Angular's change detection mechanism. 

