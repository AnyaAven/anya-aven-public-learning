### Security Caution for Cross Site Scripting

`$_SERVER["PHP_SELF"]` should be used with caution!
If used on a page, a user can enter a `/` to the url adding a script.

`http://www.example.com/test_form.php/%22%3E%3Cscript%3Ealert('hacked')%3C/script%3E`

Translates to
`<script>alert('hacked')</script>`

`$_SERVER["PHP_SELF"]` exploits can be avoided by using the `htmlspecialchars()` function.

The `htmlspecialchars()` function converts special characters to HTML entities.

`&quot;&gt;&lt;script&gt;alert('hacked')&lt;/script&gt;`