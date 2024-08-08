## Classes / Objects 

---
<!-- TOC -->
  * [Classes / Objects](#classes--objects-)
    * [Constructor](#constructor)
      * [Destructor](#destructor)
    * [Visibility](#visibility)
    * [Subclassing](#subclassing)
    * [`final` keyword](#final-keyword)
    * [Accessing Properties](#accessing-properties)
      * [Class Constants or Static](#class-constants-or-static)
      * [Properties or Methods](#properties-or-methods)
      * [Parent](#parent)
<!-- TOC -->
---
### Constructor

---
`__construct()` function is called automatically when using `new` keyword
to create instances of the class.

Similar concept to dunder functions in Python, this will start with two underscores.

#### Destructor

---
`__destruct()` function that is automatically called at the end of the script.

### Visibility

---
* public (default)
* protected - only within the class and subclasses
* private - only within the class

### Subclassing

---
Use the keyword `extends`.

> `class Strawberry extends Fruit {...`

### `final` keyword
The `final` keyword can be used to prevent class inheritance 
or to prevent method overriding.

```injectablephp
final class Fruit {                  // cannot extend
  final public function intro() {    // cannot be overwritten
    // some code
  }
}

```

### Accessing Properties

---
#### Class Constants or Static

Define constant properties in a class and access them using the `::` double colon
or scope resolution operator followed by the constant name.

Use the keyword `self` to access the constant inside the class.

Use the keyword `static` for class properties.

```injectablephp
class Goodbye {
  const LEAVING_MESSAGE = "Thank you for reading";
  static this_is_changable = "Static properties are on the class, not instances"
  $prop = "property of Goodbye"
  public function bye() {          
    echo self::LEAVING_MESSAGE;    // `self` example 1
  }
}
echo Goodbye::LEAVING_MESSAGE;     // Class example 2
```

#### Properties or Methods
Unlike JavaScript that uses dot notation, we use dart or arrow (`->`) notation
to access methods or properties.

```injectablephp
$goodbye = new Goodbye();
$goodbye->byebye();

```

#### Parent
Access a parent's property or method with the `parent` keyword and `::`.

```injectablephp
class domain {
  protected static function getWebsiteName() {
    return "anyaaven.com";
  }
}

class domainW3 extends domain {
  public $websiteName;
  public function __construct() {
    $this->websiteName = parent::getWebsiteName();
  }
}
```