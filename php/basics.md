## Basics of PHP

---

Similar to JavaScript syntactically.
This .md file will mainly indicate the key differences and similarities from JS.

---
### .php file

---

All php files should have a `.php` extension and a starting php script tag.
The closing tag is optional.
```injectablephp
<?php
// PHP code goes here
$y = 10;
?>
```

### Comments

---
```injectablephp
// single line comment
# single line comment (not used as much)
/* multi lined comment */
```

### Variables

---
* A variable starts with the $ sign, followed by the name of the variable
* A variable name must start with a letter or the underscore character
* A variable name cannot start with a number

```injectablephp
<?php
$x = 5;
```

### Splitting and joining

---
In the php world, exploding and imploding.
```injectablephp 
$x = "Hello World!";
$y = explode(" ", $x);
```

### Print and string template literals

---
Use `echo` to output the `$txt` variable. 
For readability, may use concatenate operator `.`.
```injectablephp 
$txt = "php";
echo "I love $txt!";

echo "I love " . $txt . "!";
```

##### `print_r` vs echo

---
Notice that echo will print the data type, not the result.
Use `print_r` for the result
```injectablephp 
$x = "Hello World!";
$y = explode(" ", $x);

//Use the print_r() function to display the result:
print_r($y); // Array ( [0] => Hello [1] => World! ) 
echo $y // Array
```

### Weakly Typed

---
PHP has weak typing.
PHP automatically associates a data type to the variable.
In PHP 7, type declarations were added by enabling the strict requirement. 
It will throw a `Fatal Error` on a type mismatch.

```injectablephp
<?php declare(strict_types=1); // strict requirement

$a = 1.2; // PHP adds the type automatically

function addNumbers(float $b) : float {
    global $a; // go get the global variable
    return $a + $b;
}
echo addNumbers(1.2, 5.2); // Does not argue with more arguments given.
```

Unlike TypeScript, `float` will go before the variable name.

### Data Types

---
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

```injectablephp 
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

---

Double quoted string literals perform operations for special characters, e.g., 
variables inside strings.
Single quoted strings does not perform such actions, 
it returns the string like it was written

[String Functions](https://www.w3schools.com/php/php_ref_string.asp)

### Casting

---
Similar to Number() or stringify functionality. 
Casting in php will do it's best to convert data types.

This may lead to unexpected results.
When casting a Boolean into a string, it gets the value "1". 
When casting NULL into a string, it is converted into an empty string "".

To cast to null use `(unset)`
```injectablephp 
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

```injectablephp
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

---
Constants are automatically global.

To define a constant we can use `define(name, value)`
or define with the keyword `const` 

##### const vs define()

---
* const cannot be created inside another block scope, like inside a function or inside an if statement.
* define can be created inside another block scope.

##### Magic Constants

---
Some constants are built into php.

| Constant           | Description                                                                                  |
|--------------------|----------------------------------------------------------------------------------------------|
| `__CLASS__`        | If used inside a class, the class name is returned.                                          |
| `__DIR__`          | The directory of the file.                                                                   |
| `__FILE__`         | The file name including the full path.                                                       |
| `__FUNCTION__`     | If inside a function, the function name is returned.                                         |
| `__LINE__`         | Th e current line number.                                                                    |
| `__METHOD__`       | If used inside a function that belongs to a class, both class and function name is returned. |
| `__NAMESPACE__`    | If used inside a namespace, the name of the namespace is returned.                           |
| `__TRAIT__`        | If used inside a trait, the trait name is returned.                                          |
| ClassName::class   | Returns the name of the specified class and the name of the namespace, if any.               |

### Operators

---

Most operators are similar to other languages.

##### Strict vs Loose equality

---
Key things to watch for is that `==` and `===` both exist. 
Always use `===` strict equals.

###### `<=>` Spaceship Operator

---
Returns an integer less than, equal to, or greater than zero.

##### `xor` Xor Operator (Pronunciation: "x or")

---
`xor`: True if either side is truthy but not both.

##### `+` Union Operator (Array)

---
Joins two arrays. 
Notice key of `a` is only added once.

```injectablephp 
<?php
$x = array("a" => "red", "b" => "green");  
$y = array("a" => "red", "c" => "yellow");  

print_r($x + $y); // union of $x and $y
// Array ( [a] => red [b] => green [c] => yellow )
?>  
```

##### Conditional Assignment

---
* `?:` Ternary, the same as JS
* `??` Null coalescing: The value of $x is expr1 if expr1 exists, and is not NULL.
If expr1 does not exist, or is NULL, the value of $x is expr2.

###### Reference:  [W3 Schools](https://www.w3schools.com/php/php_operators.asp)

### Switch Statement

---
Switch statement is the same as JS.

### Arrays

---
Dynamic arrays are arrays that can change size dynamically at runtime. 
In PHP, all arrays are dynamic by default.
* Indexed
```injectablephp 
`$cars = array("Volvo", "BMW", "Toyota");` 
echo $cars[0]; // Volvo
```

* Associative (keys are strings) ---- Similar to JS's object key value pairs
```injectablephp 
$car = array("brand"=>"Ford", "model"=>"Mustang", "year"=>1964);
echo $car["model"];
```

* Sparse
```injectablephp
$sparse_array = [1 => 'one', 3 => 'three', 5 => 'five'];
```

#### Count
`count($cars)`

### Loops

---
Same loops as JS except we don't have `for { el in arr}` loops.

Instead, we have `foreach`. 
Assign a variable name to either the **value** or the **key and value** pair.
```injectablephp
$colors = array("red", "green", "blue", "yellow");

foreach ($colors as $x) {
  echo "$x"; // red // green // blue // yellow
}

foreach ($members as $x => $y) {
  echo "$x : $y"; // 0 : red // 1 : green // 2 : blue // 3 : yellow
}
```
#### Mutation by reference
`$x` is a variable with block scope, changing the variable inside does not affect
`$colors` array. 
```injectablephp 
foreach ($colors as $x) {
  if ($x == "blue") $x = "pink";
}
```
But by using the `&` character in the foreach declaration, 
the array item is assigned by reference, which results in any changes done 
to the array item will also be done to the original array, mutation!
```injectablephp 
foreach ($colors as &$x) {          // Notice the & character!!
  if ($x == "blue") $x = "pink";
}
```

#### Passing by Reference in functions `&$argument`
```injectablephp 
function add_five(&$value) {
  $value += 5;
}
```


### Objects / Classes

---
```injectablephp 
class Fruit {
  // Properties
  public $name;
  public $color;

  // Methods
  function set_name($name) {
    $this->name = $name;
  }
  function get_name() {
    return $this->name;
  }
}
```