## Loop Scope

What happens when we declare a variable with loops?
What scope does it exist in?
---
### JavaScript
In JavaScript, we cannot access the variable outside the `block scope`.

```js
const arr = [1,2,3];
for(const a of arr){
    console.log(a);
}
console.log(a) // ReferenceError: a is not defined
```
**Output**: 1, 2, 3 with ReferenceError.

---
### Python
In Python, we have `local scope`. `a` is declared with the `for` loop and can still 
be accessed outside, except that there is a warning `Name 'a' can be undefined`.

```python
arr = [1, 2, 3]
for a in arr:
    print(a)

print(a) # Name 'a' can be undefined
```
Output: 1, 2, 3, 3

---
### PHP
In PHP, we have `local scope`. `a` is declared with the `foreach` loop and can still
be accessed outside.

`unset` keyword unsets the variable to a location in memory.

```injectablephp
$arr = [1, 2, 3];

foreach ($arr as $a){ // can be with or without reference, `&`
    echo $a;
}

echo $a;
unset($a); // Unsets the variable to a location in memory
//echo $a; // If executed, throws error: Undefined variable '$a' 
```

Output: 1, 2, 3, 3