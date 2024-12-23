Event binding in Angular allows you to listen for events emitted by DOM elements (like clicks, input changes, etc.) and respond to them with actions defined within your component's TypeScript code. This enables you to create interactive and dynamic user experiences.

**How it works:**

1. **Target Event:** Identify the DOM event you want to listen for (e.g., `click`, `input`, `submit`).
2. **Target Element:** Select the HTML element in your template where this event might occur.
3. **Binding Syntax:** Use parentheses `()` around the target event within the template and assign it to a method or expression in your component.

**Example:**

```typescript
// app.component.ts
import { Component } from '@angular/core';

@Component({
  selector: 'app-root',
  template: `
    <button (click)="onButtonClick()">Click Me</button>
  `
})
export class AppComponent {
  onButtonClick() {
    alert('Button clicked!'); 
  }
}
```

In this example:

- `click` is the **target event** we are listening for.
- The `<button>` is the **target element**.
- `(click)="onButtonClick()"` establishes the **event binding**.

When the button is clicked:

- The `click` event is emitted by the `<button>` element.
- Angular detects the event binding and calls the `onButtonClick()` method in the component.
- The `alert('Button clicked!')` code within the method is executed.

**Key points:**

- **User Interactions:** Event binding is crucial for handling user interactions and making your applications responsive.
- **Event Object:** You can optionally pass the `$event` object to your event handling method to access event-specific information. For instance, in an `input` event, `$event.target.value` would give you the current value of the input field.
- **Template Statements:** While using a method call like `onButtonClick()` is common, you can also write simple expressions directly within the event binding if the logic is very concise.

