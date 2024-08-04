## Basics of PHP

---
### .php file

All php files should have a `.php` extension and a starting php script tag.
The closing tag is optional.
```php
<?php
// PHP code goes here
$y = 10;
?>
```

### Comments 
```php
// single line comment
# single line comment (not used as much)
/* multi lined comment */
```

### Variables
* A variable starts with the $ sign, followed by the name of the variable
* A variable name must start with a letter or the underscore character
* A variable name cannot start with a number

```php
<?php
$x = 5;
```

### Splitting and joining
In the php world, exploding and imploding.
```php 
$x = "Hello World!";
$y = explode(" ", $x);
```

### Print and string template literals
Use `echo` to output the `$txt` variable. 
For readability, may use concatenate operator `.`.
```php 
$txt = "php";
echo "I love $txt!";

echo "I love " . $txt . "!";
```

##### `print_r` vs echo
Notice that echo will print the data type, not the result.
Use `print_r` for the result
```php 
$x = "Hello World!";
$y = explode(" ", $x);

//Use the print_r() function to display the result:
print_r($y); // Array ( [0] => Hello [1] => World! ) 
echo $y // Array
```

### Loose or strict typing
PHP automatically associates a data type to the variable.
In PHP 7, type declarations were added by enabling the strict requirement. 
It will throw a `Fatal Error` on a type mismatch.

### Data Types
* String
* Integer
* Float (floating point numbers. Also called double)
* Boolean
* Array
* Object
* NULL
* Resource
* Infinity 
* NaN

`var_dump($txt)` returns the data type and value
Use `is_int()` and similar functions to return booleans. 

```php 
<?php
var_dump(5);          // int(5)
var_dump("John");     // string(4) "John"
var_dump(3.14);       // float(3.14)
var_dump(true);       // bool(true)
var_dump([2, 3, 56]); // array(3) {
                      //   [0]=>
                      //   int(2)
                      //   [1]=>
                      //   int(3)
                      //   [2]=>
                      //   int(56)
                      // }
var_dump(NULL);       // NULL
?>
```

### Strings, Single or Double?

Double quoted string literals perform operations for special characters, e.g., 
variables inside strings.
Single quoted strings does not perform such actions, 
it returns the string like it was written

[String Functions](https://www.w3schools.com/php/php_ref_string.asp)

### Casting
Similar to Number() or stringify functionality. 
Casting in php will do it's best to convert data types.

This may lead to unexpected results.
When casting a Boolean into a string, it gets the value "1". 
When casting NULL into a string, it is converted into an empty string "".

To cast to null use `(unset)`
```php 
$a = 5;       // Integer
$b = 5.34;    // Float
$c = "hello"; // String
$d = true;    // Boolean
$e = NULL;    // NULL

// STRINGS
$a = (string) $a;
$b = (string) $b;
$c = (string) $c;
$d = (string) $d;
$e = (string) $e;

var_dump($a); // string(1) "5"
var_dump($b); // string(4) "5.34"
var_dump($c); // string(5) "hello"
var_dump($d); // string(1) "1"
var_dump($e); // string(0) ""

// INTEGERS     // var_dump() results 
$a = (int) $a;  // int(5)
$b = (int) $b;  // int(5)
$c = (int) $c;  // int(0)
$d = (int) $d;  // int(1)
$e = (int) $e;  // int(0)
```
[PHP Casting](https://www.w3schools.com/php/php_casting.asp)

##### Array and Object Casting

Arrays
```php
$a = array("Volvo", "BMW", "Toyota"); // indexed array
/* var_dump() results

object(stdClass)#1 (3) {
  [0]=>
  string(5) "Volvo"
  [1]=>
  string(3) "BMW"
  [2]=>
  string(6) "Toyota"
}
*/
$b = array("Peter"=>"35", "Ben"=>"37", "Joe"=>"43"); // associative array
/* var_dump() results

object(stdClass)#2 (3) {
  ["Peter"] => string(2) "35"
  ["Ben"] => string(2) "37"
  ["Joe"] => string(2) "43"
}
*/
```

### Constants and Magic Constants
Constants are automatically global.

To define a constant we can use `define(name, value)`
or define with the keyword `const` 

##### const vs define()
* const cannot be created inside another block scope, like inside a function or inside an if statement.
* define can be created inside another block scope.
