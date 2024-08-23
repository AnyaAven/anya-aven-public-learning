## Labels, to wrap or to id; that is the question

Labels are important for screen readers! 
The way I was taught was to have two attributes: `for` and `id`.
Instead, you can place your input inside your label tag!

This is especially handy for radio buttons as clicking on the text
enables the box.

Old way:
```html
<label for="html">
    Select a story:
</label>
<select id="html">
    <option value="happy">Happy</option>
    <option value="sad">Sad</option>
</select>
```

The wrap way:
```html
<label>
    Select a story:
    <select>
        <option value="happy">Happy</option>
        <option value="sad">Sad</option>
    </select>
</label>
```
