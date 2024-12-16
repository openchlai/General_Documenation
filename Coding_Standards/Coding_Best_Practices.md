
## Coding Best Practices

Adhering to coding best practices ensures the software is robust, maintainable, and easy for contributors to understand and expand upon. Below are detailed guidelines to follow when writing code for UNICEF-supported projects.

---

### 1. Follow Industry-Standard Coding Styles
Consistent coding styles improve code readability and make collaboration easier. Use linters and formatters to enforce style rules.

#### Python
- Adhere to [PEP 8](https://peps.python.org/pep-0008/), the de facto coding style guide for Python. Key aspects include:
  - Use 4 spaces per indentation level.
  - Keep lines under 79 characters.
  - Use meaningful variable names and avoid single-letter variables, except for counters.
  - Separate classes, functions, and blocks of code with two blank lines.
  - Write docstrings for all classes, methods, and functions using triple double quotes (`"""`).

#### JavaScript
- Follow the [Airbnb JavaScript Style Guide](https://github.com/airbnb/javascript), which is widely accepted in the industry. Highlights include:
  - Use `const` and `let` instead of `var`.
  - Prefer arrow functions for concise syntax (`() => {}`).
  - Write descriptive variable and function names.
  - Always use semicolons (`;`) and trailing commas in multiline arrays or objects.
  - Avoid deeply nested code by breaking down logic into smaller functions.

**Tip**: Use tools like `flake8` or `black` for Python and `eslint` or `prettier` for JavaScript to automate style checking and formatting.

---

### 2. Write Clean, Modular, and Reusable Code

#### Clean Code
- Break code into smaller, meaningful functions to improve readability.
- Avoid redundant or unused code—keep the codebase lean and efficient.
- Stick to the [DRY principle](https://en.wikipedia.org/wiki/Don%27t_repeat_yourself) (Don’t Repeat Yourself) to reduce duplication.

#### Modular Code
- Group related functionality into modules or components to improve organization and make code easier to maintain.
- Avoid monolithic files by splitting logic into smaller, logically cohesive files.

#### Reusable Code
- Write functions and modules that can be reused across different parts of the project.
- Parameterize functions where appropriate to increase flexibility.
- Document reusable components clearly so other developers know how to use them.

---

### 3. Ensure Proper Commenting and Code Readability

#### Comments
- Write meaningful comments to explain **why** something is done, not just **what** the code does.
- Add inline comments sparingly for non-obvious logic:
  ```python
  # Normalize values to a range of 0 to 1
  normalized_value = (value - min_value) / (max_value - min_value)
  ```
- Use block comments for sections of complex logic or workflows.

#### Docstrings
- Add docstrings to functions and classes to explain their purpose, expected parameters, and return values:
  ```python
  def add_numbers(a: int, b: int) -> int:
      """
      Adds two integers and returns the result.

      Args:
          a (int): The first number.
          b (int): The second number.

      Returns:
          int: The sum of the two numbers.
      """
      return a + b
  ```
- Avoid excessive commenting that merely repeats the code; instead, strive for self-explanatory variable and function names.

---

### 4. Design for Cross-Platform Compatibility
- Ensure the application runs smoothly on all intended platforms, including various operating systems, browsers, or mobile devices.
- Use libraries or frameworks that promote cross-platform functionality (e.g., Flask/Django for Python web apps, Vue/React for JavaScript frontend).
- Test on multiple platforms and devices to identify compatibility issues early.

---

### 5. Prioritize Accessibility
- Follow the [Web Content Accessibility Guidelines (WCAG)](https://www.w3.org/WAI/standards-guidelines/wcag/) to ensure applications are accessible to all users, including those with disabilities.
  - Use semantic HTML elements (e.g., `<button>` instead of `<div>` for buttons).
  - Provide text alternatives for non-text content (e.g., `alt` attributes for images).
  - Ensure sufficient contrast between text and background colors.
  - Implement keyboard navigation and ensure focus indicators are visible.
  - Test with assistive technologies like screen readers.

By following these practices, the codebase will not only be easier to maintain but also foster collaboration among contributors, improve user experience, and align with UNICEF's mission to create inclusive and high-quality software.
