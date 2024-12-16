
## Coding Best Practices

Adhering to coding best practices ensures the software is robust, maintainable, and easy for contributors to understand and expand upon. Below are detailed guidelines to follow when writing code for UNICEF-supported projects.

---

### 1. Follow Industry-Standard Coding Styles

Consistent coding styles improve code readability and make collaboration easier. Use linters and formatters to enforce style rules.

#### PHP
- Adhere to the [PHP Standards Recommendations (PSRs)](https://www.php-fig.org/psr/) developed by the PHP Framework Interop Group.
  - **PSR-1**: Basic coding standards.
  - **PSR-12**: Extended coding style guide.
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
