# Signals

## Introduction to Signals
Signals are a reactive state management feature introduced in Angular to simplify and enhance reactivity in applications. They provide a declarative way to handle state changes and automatically propagate updates, making state management easier and more intuitive.

## When Were Signals Introduced?
Signals were introduced in **Angular 16**, released in May 2023. This feature marked a significant step forward in simplifying Angular's reactive programming model by providing an alternative to RxJS for many common use cases.

## Basic Usage of Signals
Signals in Angular have three primary components:

### 1. **Signals (State)**
Signals are used to represent a piece of reactive state. You can create a signal, access its value, and update it.

```typescript
import { signal } from '@angular/core';

const count = signal(0); // Create a signal with an initial value of 0

console.log(count()); // Access the current value (prints 0)

count.set(1);         // Update the value to 1
console.log(count()); // Access the updated value (prints 1)
```

### 2. **Computed Signals (Derived State)**
Computed signals derive their value from other signals. They automatically recompute whenever the source signals change.

```typescript
import { signal, computed } from '@angular/core';

const count = signal(0);
const doubled = computed(() => count() * 2); // Derived signal

console.log(doubled()); // Prints 0
count.set(5);
console.log(doubled()); // Prints 10
```

### 3. **Effects (Side Effects)**
Effects allow you to run logic in response to signal changes, making them useful for tasks like logging, making API calls, or updating the DOM.

```typescript
import { signal, effect } from '@angular/core';

const count = signal(0);

effect(() => {
    console.log(`Count changed: ${count()}`);
});

count.set(2); // Logs: Count changed: 2
count.set(5); // Logs: Count changed: 5
```

## Example: Using Signals in a Component
Here's an example of how to use signals in an Angular component:

```typescript
import { Component, signal } from '@angular/core';

@Component({
  selector: 'app-counter',
  template: `
    <p>Count: {{ count() }}</p>
    <button (click)="increment()">Increment</button>
  `
})
export class CounterComponent {
  count = signal(0);

  increment() {
    this.count.set(this.count() + 1);
  }
}
```

## Advantages of Signals
- **Declarative:** Simplifies state management.
- **Automatic Change Detection:** Updates the view automatically when signals change.
- **Lightweight API:** Easy to understand and use compared to RxJS.
- **Integration with Templates:** Bind signals directly in templates for reactivity.

Signals are a powerful addition to Angular that can greatly simplify reactivity and state management in your applications.

