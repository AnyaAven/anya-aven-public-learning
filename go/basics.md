# Basics of GO Lang

## Pointers
In GO we must explicitly resolve an address.

This is different from JavaScript or Python.

```javascript
let a = 100;
let b = a;
console.log(a, b) // 100 100
```
```python
a = 100
b = a
print(a, b) # 100, 100
```

In GO we need to explicitely tell the variable to go to the address.
Most languages other than JS and Python are similar to this.
```go
package main;
import "fmt"
func main () {
	a := 42;
	b := &a        // point to a
	fmt.Println(a, b, *b) // 42, 0xc000012070 42 (read a through the pointer)
}
```