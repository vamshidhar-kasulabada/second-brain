# ngIf

`*ngIf` is a structural directive in Angular that conditionally adds or removes an element from the DOM (Document Object Model). It's a fundamental tool for controlling what is displayed to the user based on certain conditions.

Here's a detailed explanation:

**Basic Syntax:**

```html
<element *ngIf="expression">Content to display conditionally</element>
```

**Explanation:**

*   **`*ngIf`:** The asterisk (`*`) indicates that this is a structural directive. Structural directives modify the DOM by adding, removing, or manipulating elements.
*   **`expression`:** This is a TypeScript expression that evaluates to a boolean value (or a truthy/falsy value).
*   **Behavior:**
    *   If the `expression` evaluates to `true` (or a truthy value), the element and its content are added to the DOM.
    *   If the `expression` evaluates to `false` (or a falsy value), the element and its content are removed from the DOM. This is important: the element is *removed*, not just hidden with CSS.

**Truthy and Falsy Values:**

Like JavaScript, Angular's `*ngIf` uses the concept of truthiness and falsiness:

*   **Truthy:** Any value that is not falsy. Examples: `true`, any non-zero number, any non-empty string, any object, any array.
*   **Falsy:** `false`, `0`, `""` (empty string), `null`, `undefined`, `NaN`.

**Example:**

```typescript
import { Component } from '@angular/core';

@Component({
  selector: 'app-conditional-example',
  template: `
    <p *ngIf="showContent">This content is shown when showContent is true.</p>
    <p *ngIf="!showContent">This content is shown when showContent is false.</p>

    <button (click)="toggleContent()">Toggle Content</button>
  `
})
export class ConditionalExampleComponent {
  showContent = true;

  toggleContent() {
    this.showContent = !this.showContent;
  }
}
```

In this example, the first `<p>` tag is displayed only when `showContent` is `true`, and the second `<p>` tag is displayed only when `showContent` is `false`.

**`*ngIf` with `else`:**

You can use the `else` syntax to provide an alternative template to display when the `*ngIf` condition is false:

```html
<element *ngIf="expression; else elseBlock">Content to display if true</element>
<ng-template #elseBlock>Content to display if false</ng-template>
```

**Example with `else`:**

```html
<div *ngIf="isLoggedIn; else notLoggedIn">
  Welcome, User!
</div>

<ng-template #notLoggedIn>
  Please log in.
</ng-template>
```

**`*ngIf` with `then` and `else` (Less Common):**

You can also use the `then` syntax, although it's less frequently used:

```html
<element *ngIf="expression; then thenBlock else elseBlock"></element>
<ng-template #thenBlock>Content to display if true</ng-template>
<ng-template #elseBlock>Content to display if false</ng-template>
```

**Important Considerations:**

*   **DOM Manipulation:** `*ngIf` adds or removes elements from the DOM. This has performance implications. For simple show/hide toggles, using CSS (`[hidden]` or `*ngClass`) might be more performant as it avoids DOM manipulation. Use `*ngIf` when you want to completely remove the element and its associated resources (like event listeners).
*   **Null Checks:** Be careful when using `*ngIf` with potentially null or undefined values. Use the safe navigation operator (`?.`) to avoid errors:

    ```html
    <p *ngIf="user?.name">Welcome, {{ user.name }}!</p>
    ```

    This prevents an error if `user` is null or undefined.

*   **Asynchronous Operations:** When working with asynchronous operations (like HTTP requests), you often use `*ngIf` to display loading indicators:

    ```html
    <div *ngIf="isLoading">Loading...</div>
    <div *ngIf="!isLoading && data">Data: {{ data | json }}</div>
    ```

**Key Advantages of `*ngIf`:**

*   **Conditional Rendering:** The primary purpose is to control the rendering of content based on a condition.
*   **Resource Management:** Removing elements from the DOM releases associated resources.
*   **Clear Logic:** The `*ngIf` directive makes the conditional logic in your templates clear and easy to understand.

**Key Disadvantages of `*ngIf`:**

*   **DOM Manipulation Overhead:** Adding and removing elements from the DOM can have a performance cost, especially with frequent changes.
*   **No Direct `else if`:** You need to use nested `*ngIf` or the `else` syntax to achieve `else if` behavior. (This is addressed with the new `@if` syntax)

**Summary:**

`*ngIf` is a powerful and essential tool for conditional rendering in Angular. Use it to control the presence of elements in the DOM based on conditions. Be mindful of its performance implications and use it appropriately. The new `@if` syntax offers a more streamlined and readable way to achieve the same result, especially with complex conditions, and is generally preferred for new projects.

