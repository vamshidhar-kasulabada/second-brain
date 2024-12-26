# Signal Inputs in Angular

Signal Inputs in Angular allow developers to create reactive properties within a component using the `input()` function. This feature, introduced as part of Angular’s signal reactivity system, provides a more declarative and fine-grained way to handle input properties.

---

## What are Input Signals?
Input signals are a way to define component inputs as reactive signals. Unlike traditional `@Input` bindings, input signals enable:
1. **Reactive Tracking**: Automatically track changes to inputs.
2. **Fine-Grained Updates**: Minimize unnecessary updates by targeting specific changes.
3. **Simplified Change Detection**: Avoid manual lifecycle hooks like `ngOnChanges`.

---

## Syntax and Declaration
To declare an input signal, use the `input()` function provided by Angular:

### Example:
```typescript
import { Component, signal, input, computed } from '@angular/core';

@Component({
  selector: 'app-signal-input',
  template: `
    <p>User: {{ user() }}</p>
    <p>Greeting: {{ greeting() }}</p>
  `,
})
export class SignalInputComponent {
  user = input<string>(); // Declare an input signal

  // Derived signal based on the input
  greeting = computed(() => `Hello, ${this.user()}!`);
}
```

### Parent Component:
```typescript
@Component({
  selector: 'app-parent',
  template: `<app-signal-input [user]="'Angular Developer'"></app-signal-input>`
})
export class ParentComponent {}
```

### Output in the Browser:
```plaintext
User: Angular Developer
Greeting: Hello, Angular Developer!
```

---

## Key Features of Input Signals

1. **Reactivity**: Changes to the parent component’s input are automatically propagated to the child component without manual intervention.
2. **Derived Signals**: Combine input signals with `computed()` to create derived or transformed values.
3. **Cleaner Code**: Eliminates the need for boilerplate code such as `ngOnChanges`.

---

## Advanced Usage

### 1. Default Values for Input Signals
You can provide default values for input signals to ensure they have valid data if no input is provided:

```typescript
@Component({
  selector: 'app-default-input',
  template: `<p>{{ user() }}</p>`
})
export class DefaultInputComponent {
  user = input<string>('Default User');
}
```

In this example, if the parent component doesn’t bind a value to `user`, it will default to `'Default User'`.

---

### 2. Required Input Signals
Input signals can enforce required inputs using the `required` option:

```typescript
@Component({
  selector: 'app-required-input',
  template: `<p>User: {{ user() }}</p>`
})
export class RequiredInputComponent {
  user = input<string>({ required: true });
}
```

In this example, Angular will throw an error if the parent component fails to bind a value to the `user` input, ensuring data integrity.

### Parent Component Example:
```html
<app-required-input [user]="'Jane Doe'"></app-required-input>
```

---

### 3. Validation with Input Signals
Input signals can be validated dynamically using `computed()`:

```typescript
@Component({
  selector: 'app-validated-input',
  template: `
    <p *ngIf="isValid(); else error">User: {{ user() }}</p>
    <ng-template #error><p>Invalid User!</p></ng-template>
  `
})
export class ValidatedInputComponent {
  user = input<string>('');

  isValid = computed(() => this.user().trim().length > 0);
}
```

---

### 4. Combining Multiple Input Signals
Input signals can be combined to produce computed results:

```typescript
@Component({
  selector: 'app-combined-inputs',
  template: `
    <p>Full Name: {{ fullName() }}</p>
  `
})
export class CombinedInputsComponent {
  firstName = input<string>('');
  lastName = input<string>('');

  fullName = computed(() => `${this.firstName()} ${this.lastName()}`.trim());
}
```

### Parent Component Example:
```html
<app-combined-inputs [firstName]="'John'" [lastName]="'Doe'"></app-combined-inputs>
```

### Output:
```plaintext
Full Name: John Doe
```

---

## Comparison: Traditional @Input vs Input Signals

| Feature                     | Traditional `@Input` | Input Signals             |
|-----------------------------|----------------------|---------------------------|
| **Change Detection**        | Manual or `ngOnChanges` | Automatic                 |
| **Default Values**          | Set in the class     | Inline in `input()`       |
| **Required Inputs**         | Not natively supported | Built-in with `{ required: true }` |
| **Dependency Tracking**     | Not built-in         | Built-in with signals     |
| **Combining Values**        | Manual logic         | Simplified with `computed`|

---

## Common Use Cases

1. **Dynamic Properties**: Use input signals for dynamic properties that require reactive updates.
2. **Derived Values**: Create computed signals to transform or combine inputs.
3. **Form Validations**: Leverage the reactivity of signals to validate inputs in real-time.
4. **Required Inputs**: Enforce strict input requirements with the `required` option.

---

## Summary
Input signals in Angular provide a modern, reactive way to handle component inputs. By leveraging the power of Angular signals, input signals simplify change detection, enhance performance, and reduce boilerplate code. They are particularly useful for creating dynamic, reactive, and maintainable Angular applications.


