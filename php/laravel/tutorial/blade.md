## Blade
Blade is the templating engine for Laravel. Similar to Jinja for Python.

Put all blade components in a directory called
`Components`(case-insensitive but must be called components) inside `views` directory.

Make a blade component with a file `name-of-component.blade.php`

The name of the component will need to be added in the file.
Always start blade components with `x-`

```injectablephp
<x-name-of-component>
   <h1> first blade component! </h1>
</x-name-of-component>
```

---
### `$slot` variable

We always have access to `$slot` variable. Similar to `children` in react,
it will add what is in between.
`<x-comp>Hello World</x-compo>` <-- Hello world will be the result of `$slot`.

We can insert that ourselves with the
php tag and echo or use double curly braces `{{ }}` to do the same thing.
`layout.blade.php`
```injectablephp
<html>
    <body> 
        <?php echo $slot ?>
        /* or */
        {{ $slot }}
    </body>
</html>
```

---
### Attributes and Props
Attributes are HTML attributes like `href` or `class`.
Props are similar to props in React, they are named yourself.
They are an object passed to the component.

`layout.blade.php`
```injectablephp
<html>
    <body> 
        <x-nav-link href="/">Home</x-nav-link>
        <x-nav-link href="/about" style="color: green;">About</x-nav-link>
    </body>
</html>
```

`nav-link.blade.php`
```injectablephp
<a {{ $attributes }}> {{slot}} </a> 
   
```

#### Props

Add props at the top of your blade component.
Defaults have been added.
```injectablephp
@props(['active' => false, 'type' => 'button'])
```

---
### Information on the request

Determine if you are on a specific page with
`request()->is('/')` or `request()->is('/about')`: Returns a boolean.

---
### Evaluating an expression on an attribute
Use `:` before the attribute to evaluate it as an expression rather than a string
`:active="request()->is('/')`

---
### Blade Directives - Sugar syntax
Use `@` to find a blade directive for your need. 

Common uses are `@if(condition)` and `@else`, or `@foreach`. 
Almost always they will end with `@end` something, like `@endif` or `@endforeach`.

### Variables in view routes

Use `{ }` to insert a variable name into your `uri` argument and pass it into the callback.
`Route::get('/about/{id}, function ($id)'`

### Data Dump function `dd()`
This will dump the data passed in to the view and render it in the browser. 
Helpful for debugging.

```injectablephp
Route::get('/about/{id}', function ($id) {
    dd($id);
});
```

### Errors
If the form has errors from the route, you will have access to an `$errors` array.
You can also use the error tag to add for each individual input.

```injectablephp blade
<div>
    <input id='title' />
<div>
@error('title')
{{ $message }}
@enderror
```

### Methods on forms
Natively the browser only supports `GET` and `POST` on forms. 
```html
<form method="post">
</form>
```

But We can hint to laravel / blade that we will be using a patch with 
```injectablephp
<form method="post">
@method('PATCH')
</form>
```
