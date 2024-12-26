# @Output Decorator in Angular

The `@Output` decorator in Angular is used to create custom events in a child component and emit them to a parent component. It allows communication from a child to its parent, enabling the parent to respond to specific actions performed within the child component.

---

## How @Output Works

1. **Define an EventEmitter**: In the child component, use `EventEmitter` to define an event.
2. **Emit the Event**: Trigger the event using the `.emit()` method of `EventEmitter`.
3. **Bind to the Event**: In the parent component, bind to the custom event using Angular's event binding syntax (`()`).

---

## Syntax and Example

### Child Component
The child component creates and emits the event:

```typescript
import { Component, EventEmitter, Output } from '@angular/core';

@Component({
  selector: 'app-child',
  template: `<button (click)="sendData()">Send Data</button>`
})
export class ChildComponent {
  @Output() dataSent = new EventEmitter<string>();

  sendData() {
    this.dataSent.emit('Hello from Child Component!');
  }
}
```

### Parent Component
The parent component listens to the child component's event:

```typescript
import { Component } from '@angular/core';

@Component({
  selector: 'app-parent',
  template: `<app-child (dataSent)="onDataReceived($event)"></app-child>`
})
export class ParentComponent {
  onDataReceived(data: string) {
    console.log(data); // Output: Hello from Child Component!
  }
}
```

---

## Key Features

### 1. Communication from Child to Parent
The `@Output` decorator is the primary way to notify the parent component of actions or data from the child component.

### 2. Event Binding Syntax
The parent component binds to the child component’s event using parentheses, e.g., `(eventName)`.

### 3. Custom Event Names
By default, the property name is used as the event name. However, you can customize the event name by passing it as an argument to `@Output`:

```typescript
@Output('customEventName') dataSent = new EventEmitter<string>();
```

The parent component will now listen for `customEventName` instead of `dataSent`.

---

## Advanced Examples

### 1. Passing Complex Data
You can emit complex objects instead of simple strings:

#### Child Component
```typescript
@Component({
  selector: 'app-child',
  template: `<button (click)="sendData()">Send Data</button>`
})
export class ChildComponent {
  @Output() dataSent = new EventEmitter<{ id: number, name: string }>();

  sendData() {
    this.dataSent.emit({ id: 1, name: 'Angular' });
  }
}
```

#### Parent Component
```typescript
@Component({
  selector: 'app-parent',
  template: `<app-child (dataSent)="onDataReceived($event)"></app-child>`
})
export class ParentComponent {
  onDataReceived(data: { id: number, name: string }) {
    console.log(data); // Output: { id: 1, name: 'Angular' }
  }
}
```

### 2. Combining @Input and @Output
You can use `@Input` and `@Output` together to enable two-way binding.

#### Child Component
```typescript
@Component({
  selector: 'app-child',
  template: `<input [(ngModel)]="value" (ngModelChange)="valueChange.emit(value)">`
})
export class ChildComponent {
  @Input() value: string = '';
  @Output() valueChange = new EventEmitter<string>();
}
```

#### Parent Component
```typescript
@Component({
  selector: 'app-parent',
  template: `<app-child [(value)]="parentValue"></app-child>`
})
export class ParentComponent {
  parentValue: string = 'Initial Value';
}
```

---

## Best Practices

1. **Strong Typing**: Always type the `EventEmitter` to ensure type safety.
   ```typescript
   @Output() dataSent = new EventEmitter<string>();
   ```

2. **Emit Sparingly**: Only emit events for critical interactions to avoid unnecessary complexity.

3. **Custom Event Names**: Use custom event names when the default names may cause confusion.

4. **Avoid Emit Loops**: Be cautious when combining `@Input` and `@Output` to avoid infinite loops.

---

## Common Use Cases

1. **Form Submission**: Notify the parent when a form is submitted in the child component.
2. **Data Transfer**: Pass user actions or selected data from a child to a parent.
3. **Toggle States**: Communicate toggling states like opening/closing modals or expanding/collapsing sections.

---

## Summary
The `@Output` decorator is a powerful tool for enabling parent-child communication in Angular. By leveraging `EventEmitter`, it simplifies the process of sending events and data from child components to parent components, making your Angular applications more dynamic and interactive.


