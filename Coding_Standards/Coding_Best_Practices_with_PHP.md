
## Coding Best Practices

Adhering to coding best practices ensures the software is robust, maintainable, and easy for contributors to understand and expand upon. Below are detailed guidelines to follow when writing code for UNICEF-supported projects.

---

### 1. Follow Industry-Standard Coding Styles

Consistent coding styles improve code readability and make collaboration easier. Use linters and formatters to enforce style rules.

#### PHP
- Adhere to the [PHP Standards Recommendations (PSRs)](https://www.php-fig.org/psr/) developed by the PHP Framework Interop Group.
  - **PSR-1**: Basic coding standards.
  - **PSR-12**: Extended coding style guide.
- **PSR-2**: Coding style guide.
# PSR-12 Coding Style Guide Summary

## 1. Files
- **Encoding**: All PHP files must use `UTF-8` without BOM.
- **Line endings**: Use LF (`\n`) for line endings.
- **Indentation**: Use 4 spaces for indentation, not tabs.
- **Line length**: Limit lines to 120 characters; soft limit at 80 for readability.
- **Closing tag**: Omit the closing `?>` tag for files containing only PHP.

---

## 2. Namespaces and Imports
- Place one blank line after the `namespace` declaration and before any `use` declarations.
- Group `use` statements together, one per line.
- Alphabetically order `use` statements.

---

## 3. Classes, Traits, and Interfaces
- Open curly braces for classes go on the **next line**.
- Use a blank line between class-level declarations (properties, methods).
- **Visibility** must be explicitly declared for all properties and methods (`public`, `protected`, `private`).

---

## 4. Methods and Functions
- Method and function names must be in **camelCase**.
- Open curly braces for functions go on the **same line** as the function declaration.
- Arguments must be separated by a single space after commas.
- Default values for arguments must not have spaces around the equals sign.

---

## 5. Control Structures
- Control keywords (e.g., `if`, `for`, `while`) must have **one space** after them.
- The opening curly brace for control structures must be on the **same line** as the control keyword.
- Avoid unnecessary parentheses for `return`, `include`, etc.

---

## 6. Operators
- Binary and ternary operators should have a space on **both sides** (e.g., `$a = $b + $c`).
- No spaces around unary operators (e.g., `++$i`, `$j--`).

---

## 7. Arrays
- Use the `[]` syntax for arrays.
- Multiline arrays should have each element on its own line with a **trailing comma**.

---

## 8. Constants
- Constants declared with `define` should be in **uppercase letters** with underscores (e.g., `MY_CONSTANT`).

---

## 9. PHP DocBlocks
- Use PHPDoc for documenting classes, methods, and functions.
- Align tags vertically for readability.

---

## 10. Miscellaneous
- No **trailing whitespace** at the end of lines.
- Blank lines may be added to improve readability but avoid multiple consecutive blank lines.
- Use **meaningful names** for variables, classes, and methods.

  - **PSR-4**: Autoloading standards.
- Use tools like `PHP_CodeSniffer` or `PHP-CS-Fixer` to automate style checking and formatting.

**Key PHP Practices:**
- Use 4 spaces for indentation.
- Use meaningful and descriptive variable and function names.
- Avoid deeply nested code; split logic into smaller functions.
- Add docblocks for classes, methods, and functions.

**Example**:
```php
<?php

/**
 * User class handles user-related operations.
 */
class User
{
    private string $name;

    public function __construct(string $name)
    {
        $this->name = $name;
    }

    /**
     * Greet the user with a message.
     *
     * @return string
     */
    public function greet(): string
    {
        return "Hello, " . $this->name . "!";
    }
}

// Usage
$user = new User("Alice");
echo $user->greet(); // Output: Hello, Alice!
```
---

### 2. Write Clean, Modular, and Reusable Code

#### Clean Code
- Avoid hardcoding values; use constants or configuration files.
- Stick to the [DRY principle](https://en.wikipedia.org/wiki/Don%27t_repeat_yourself) (Don’t Repeat Yourself).
- Avoid magic numbers or strings in the code; define constants.

**Example**:
```php
<?php

define('TAX_RATE', 0.15);

/**
 * Calculate the total price after applying tax.
 *
 * @param float $price
 * @return float
 */
function calculateTotal(float $price): float
{
    return $price + ($price * TAX_RATE);
}

echo calculateTotal(100.0); // Output: 115.0
```
#### Modular Code
- Use namespaces and organize files into logical directories.
- Break large functions into smaller, single-responsibility functions.

**Example**:
```php
<?php

namespace App\Services;

/**
 * EmailService handles email-related operations.
 */
class EmailService
{
    public function sendEmail(string $recipient, string $subject, string $message): bool
    {
        // Simulate email sending
        return mail($recipient, $subject, $message);
    }
}

// Usage
$emailService = new App\Services\EmailService();
$emailService->sendEmail("test@example.com", "Welcome", "Hello and welcome!");
```
---

### 3. Ensure Proper Commenting and Code Readability

#### Comments
- Use single-line comments for short notes and block comments for detailed explanations.

**Example**:
```php
<?php

// Calculate factorial recursively
function factorial(int $n): int
{
    if ($n <= 1) {
        return 1;
    }

    // Recursive call
    return $n * factorial($n - 1);
}
```
#### Docblocks
- Use [PHPDoc](https://docs.phpdoc.org/) for documenting classes, methods, and functions.

**Example**:
```php
<?php

/**
 * Class Calculator provides basic mathematical operations.
 */
class Calculator
{
    /**
     * Add two numbers.
     *
     * @param float $a
     * @param float $b
     * @return float
     */
    public function add(float $a, float $b): float
    {
        return $a + $b;
    }
}
```
---

### 4. Design for Cross-Platform Compatibility

- Ensure the application can run on different server environments (e.g., Linux, Windows, macOS).
- Use environment variables and a `.env` file for configurations.

**Example of using `.env` with `vlucas/phpdotenv`:**
```php
<?php

require 'vendor/autoload.php';

use Dotenv\Dotenv;

$dotenv = Dotenv::createImmutable(__DIR__);
$dotenv->load();

// Access environment variables
$dbHost = $_ENV['DB_HOST'];
$dbName = $_ENV['DB_NAME'];
```
---

### 5. Prioritize Accessibility

- Design web applications with accessibility in mind.
- Use semantic HTML elements and ensure compatibility with assistive technologies.

**Example of accessible form:**
```php
<form action="/submit" method="post">
    <label for="name">Name</label>
    <input type="text" id="name" name="name" required>

    <label for="email">Email</label>
    <input type="email" id="email" name="email" required>

    <button type="submit">Submit</button>
</form>
```
---

By incorporating PHP-specific examples and following these best practices, your code will be cleaner, more maintainable, and accessible for developers and users alike.
