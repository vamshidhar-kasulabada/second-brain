# Angular Pipes

#### What are Pipes?

Pipes in Angular are a feature that allows you to transform data directly within your templates. They are used to format or transform data for display without changing the underlying data model.

#### How Pipes Work

- **Syntax**: Pipes are used in templates with the `|` (pipe) character, followed by the pipe name and any optional parameters.
- **Pure and Impure Pipes**: 
  - **Pure Pipes** are only called when the input data changes.
  - **Impure Pipes** are called on every change detection cycle, which can affect performance.

#### Built-in Pipes

1. **DatePipe**: Formats a date according to the specified locale.
   ```html
   <!-- Example: Displays the current date in 'fullDate' format -->
   {{ today | date:'fullDate' }}
   ```

2. **CurrencyPipe**: Formats a number as currency.
   ```html
   <!-- Example: Formats number as USD currency -->
   {{ price | currency:'USD':'symbol' }}
   ```

3. **DecimalPipe**: Formats a number with a specified decimal place.
   ```html
   <!-- Example: Formats number with 1 minimum and 2 maximum decimal places -->
   {{ number | number:'1.2-2' }}
   ```

4. **PercentPipe**: Converts a number into a percentage string.
   ```html
   <!-- Example: Displays a decimal as a percentage -->
   {{ decimal | percent }}
   ```

5. **JsonPipe**: Converts an object into a JSON string.
   ```html
   <!-- Example: Displays an object in JSON format -->
   {{ object | json }}
   ```

6. **SlicePipe**: Returns a subset of an array or string.
   ```html
   <!-- Example: Displays elements from index 1 to 3 of an array -->
   {{ array | slice:1:3 }}
   ```

7. **UpperCasePipe / LowerCasePipe**: Transforms text to upper or lower case.
   ```html
   <!-- Example: Converts text to uppercase -->
   {{ text | uppercase }}
   ```

#### Creating Custom Pipes

You can create your own custom pipes to handle specific data transformations.

```typescript
// Import necessary Angular core functionalities
import { Pipe, PipeTransform } from '@angular/core';

// Define a pipe with the @Pipe decorator
@Pipe({name: 'customPipe'})
export class CustomPipe implements PipeTransform {
  transform(value: any, ...args: any[]): any {
    // Custom transformation logic
    return modifiedValue;
  }
}
```

#### Using Pipes in Templates

To use a pipe, apply it in your HTML template by using the pipe operator (`|`).

```html
<!-- Example: Using a custom pipe -->
{{ data | customPipe:arg1:arg2 }}
```


### Resources
- [Angular Docs](https://angular.dev/guide/templates/pipes)
