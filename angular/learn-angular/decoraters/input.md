# @Input Decorator in Angular

The `@Input` decorator in Angular is used to pass data from a parent component to a child component. It is essential for parent-to-child communication in Angular applications.

---

## Key Features
- **Parent-to-Child Communication**: Pass data from the parent component to a child component.
- **Property Binding**: Use Angular’s property binding syntax (`[propertyName]="value"`).
- **Dynamic Updates**: Updates in the parent’s property are reflected in the child automatically.

---

## Syntax
```typescript
import { Component, Input } from '@angular/core';

@Component({
  selector: 'app-child',
  template: `
    <p>{{ data }}</p>
  `,
})
export class ChildComponent {
  @Input() data: string = ''; // Declare an input property
}
```

---

## Basic Example

### Parent Component
**ParentComponent HTML**:
```html
<app-child [name]="'Angular'" [count]="5"></app-child>
```

**ParentComponent Class**:
```typescript
import { Component } from '@angular/core';

@Component({
  selector: 'app-parent',
  template: `<app-child [name]="'Angular'" [count]="5"></app-child>`,
})
export class ParentComponent {}
```

### Child Component
**ChildComponent Class**:
```typescript
import { Component, Input } from '@angular/core';

@Component({
  selector: 'app-child',
  template: `
    <p>Name: {{ name }}</p>
    <p>Count: {{ count }}</p>
  `,
})
export class ChildComponent {
  @Input() name: string = ''; // Input property for name
  @Input() count: number = 0; // Input property for count
}
```

### Output in the Browser:
```plaintext
Name: Angular
Count: 5
```

---

## Advanced Usage

### 1. Renaming the Input Binding
You can alias the property name to make it different from the internal variable name in the child component.

```typescript
@Input('customName') name: string = '';
```

**Parent Component**:
```html
<app-child [customName]="'New Name'"></app-child>
```

---

### 2. Default Values
You can provide default values for `@Input` properties in the child component:

```typescript
@Input() name: string = 'Default Name';
```

If the parent doesn't provide a value, the default value is used.

---

### 3. Using Getters and Setters
If you need additional logic when the input changes, use getters and setters:

#### Example:
```typescript
private _name: string = '';

@Input()
set name(value: string) {
  console.log('Previous Value:', this._name);
  this._name = value.toUpperCase(); // Convert to uppercase
  console.log('New Value:', this._name);
}
get name(): string {
  return this._name;
}
```

This allows you to:
1. Log changes to the value.
2. Transform or validate the input before assigning it internally.

#### Example Usage in Template:
```html
<app-child [name]="'Angular'"></app-child>
```

---

### 4. Required Inputs
In Angular 16 and later, you can mark `@Input` properties as required using the `required` property:

#### Example:
```typescript
@Component({
  selector: 'app-child',
  template: `<p>{{ requiredProp }}</p>`
})
export class ChildComponent {
  @Input({ required: true }) requiredProp!: string; // Mark input as required
}
```

If the parent component does not bind a value to `requiredProp`, Angular will throw an error at runtime:

#### Parent Component:
```html
<app-child [requiredProp]="'Required Value'"></app-child>
```

This feature ensures strict enforcement of required properties, improving component reliability.

---

## Key Notes
1. **Change Detection**: Angular automatically detects changes to `@Input` properties and updates the child component.
2. **Property Binding Syntax**: Use square brackets (`[propertyName]`) for binding.
3. **Optional Inputs**: Default values can make inputs optional.
4. **Readonly Inputs**: Inputs cannot be directly modified in the child component.
5. **Required Inputs**: Use `{ required: true }` or runtime checks to enforce required properties.
6. **Custom Logic**: Use getters and setters to add custom logic or validations.

---

## Common Errors
1. **Missing Input Decorator**:
   If you forget to use `@Input`, Angular won't recognize the property for binding.

2. **Undefined Input**:
   Ensure the parent provides a value or the child component has a default value.

---

## Summary Table
| **Feature**             | **Description**                                             |
|-------------------------|---------------------------------------------------------|
| Basic Input             | Pass data from parent to child.                          |
| Renaming Input Binding  | Use an alias for the input property.                     |
| Default Value           | Set a default value in the child component.             |
| Getters and Setters     | Perform additional logic when the input changes.        |
| Required Inputs         | Enforce that the parent must provide a value.           |

---

`@Input` is a powerful decorator that enables modular and reusable components by facilitating communication between parent and child components in Angular.


