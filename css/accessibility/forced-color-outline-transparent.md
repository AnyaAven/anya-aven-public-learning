## Outline Accessibility

---

Instead of using `outline:none` in your CSS, try reaching for `outline-color:transparent`.

This will cause the same visual effect but also allow user's preferences to override it.

For example, there is a `forced-color` mode in windows that enables low or high
contrast on a user's device. This will allow the user to change the color while 
`outline:none` will not.
