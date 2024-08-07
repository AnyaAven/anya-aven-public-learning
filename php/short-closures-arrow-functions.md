## Short Closures / Arrow Functions

Syntactical sugar for functions

* They start with the fn keyword
* They can only have one expression, which is the return statement
* No return keyword allowed
* Arguments and return types can be type hinted
* 
```injectablephp
$ids = array_map(fn($post) => $post->id, $posts);
```
vs.

```injectablephp
$ids = array_map(function ($post) {
    return $post->id;
}, $posts);
```

References are allowed, both for the arguments as the return values
`fn&($x) => $x`

### Values from outer scope
Another significant difference between short and normal closures is that the 
short ones don't require the use keyword to be able to access data from the outer scope.

#### Without short closures:
```injectablephp
$outerVariable = 10;

$closure = function() use ($outerVariable) {
    return $outerVariable * 2;
};

echo $closure(); // Outputs: 20
```

#### With
```injectablephp
$outerVariable = 10;

$shortClosure = fn() => $outerVariable * 2;

echo $shortClosure(); // Outputs: 20
```