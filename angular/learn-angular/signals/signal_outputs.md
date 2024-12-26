# Angular `output()` Function and Signals

## Introduction
The `output()` function is part of Angular's reactivity system introduced in Angular 16+. It is used to define an **output signal** that enables child-to-parent communication in a more reactive and declarative way compared to the traditional `@Output()` and `EventEmitter` approach.

In this document, we'll explore how the `output()` function works with a simple example of a Todo List App.

## Key Concepts

- **Signal**: A reactive mechanism for emitting data.
- **`output()` Function**: Used to define a signal in a child component that emits data to the parent component.
- **`emit()`**: Used to emit a value from the signal.

## Example Scenario: Todo List App

### Child Component (`TodoItemComponent`)

The child component contains a Todo item and a button to mark the Todo as complete. When the button is clicked, the child emits the updated Todo object via a signal.

```typescript
import { Component, output } from '@angular/core';

interface Todo {
  id: number;
  title: string;
  completed: boolean;
}

@Component({
  selector: 'app-todo-item',
  template: `<button (click)="markAsComplete()">Mark as Complete</button>`
})
export class TodoItemComponent {
  todo: Todo = { id: 1, title: 'Finish Angular Tutorial', completed: false };

  // Define an output signal that emits the updated Todo item
  completeTodo = output<Todo>();

  markAsComplete() {
    this.todo.completed = true;
    this.completeTodo.emit(this.todo);
  }
}
```

### Parent Component (`AppComponent`)

The parent component listens for the signal emitted by the child and updates its list of Todos.

```typescript
import { Component } from '@angular/core';

interface Todo {
  id: number;
  title: string;
  completed: boolean;
}

@Component({
  selector: 'app-root',
  template: `
    <app-todo-item (completeTodo)="handleComplete($event)"></app-todo-item>
    <ul>
      <li *ngFor="let todo of todos">{{ todo.title }} - {{ todo.completed ? 'Completed' : 'Pending' }}</li>
    </ul>
  `
})
export class AppComponent {
  todos: Todo[] = [
    { id: 1, title: 'Learn Angular', completed: false },
    { id: 2, title: 'Write Documentation', completed: false },
  ];

  handleComplete(updatedTodo: Todo) {
    const index = this.todos.findIndex(todo => todo.id === updatedTodo.id);
    if (index !== -1) {
      this.todos[index] = updatedTodo;
    }
  }
}
```

### How It Works:
1. **Child Component**:
   - When the button is clicked, the child component marks the Todo as complete and emits the updated Todo object using the `completeTodo.emit(this.todo)` call.

2. **Parent Component**:
   - The parent listens for the emitted signal via `(completeTodo)="handleComplete($event)"`.
   - The `handleComplete()` method is called with the updated Todo object and updates the parent’s list of Todos.

## Benefits of `output()` over `@Output()`
1. **No Need for `EventEmitter`**: The `output()` function simplifies the process by eliminating the need for `@Output()` and `EventEmitter`.
2. **Reactivity**: Signals automatically trigger updates when data changes, without requiring manual subscriptions or event handling.
3. **Type Safety**: The `output()` function allows you to specify the type of data being emitted, ensuring type safety and reducing runtime errors.
4. **Cleaner Code**: The code is more declarative, making the intent clearer and reducing boilerplate code.

## Summary
- The `output()` function is used to create signals in child components that emit data to the parent.
- It replaces `@Output()` and `EventEmitter`, providing a cleaner and more efficient way of managing child-to-parent communication.
- Signals are reactive and type-safe, making them more robust and easier to maintain.

