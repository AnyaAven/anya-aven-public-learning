## Form Attribute

---
The form attribute tells the input / button what form it will go to.
By default it will be the highest parent form but can be overwritten with
the form attribute.
```html
<form method="POST">
    <button>Press me! I will send the form data!</button>
</form>
```
Example with form attribute
```html
<form method="POST">
    <button form="your-form">Press me! I will activate the second form!</button>
    
    <form method="POST" id="your-form">
        
    </form>
</form>

```