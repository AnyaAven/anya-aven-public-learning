## Variable Variables

Use the results of a variable to gain access to another variable

```injectablephp
$Bar = "a";
  $Foo = "Bar";
  $World = "Foo";
  $Hello = "World";
  $a = "Hello";

  $a; //Returns Hello
  $$a; //Returns World
  $$$a; //Returns Foo
  $$$$a; //Returns Bar
  $$$$$a; //Returns a

  $$$$$$a; //Returns Hello
  $$$$$$$a; //Returns World

  //... and so on ...//
```

#### Resources
[PHP Docs](https://www.php.net/manual/en/language.variables.variable.php)