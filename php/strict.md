### Strict Typing in PHP
Add `<?php declare(strict_types=1);` to the first line in your file.

* in mode 0, it automatically validates and casts certain scalar types 
(e.g. int parameter will convert '123' to 123, but error on 'hello')
* in mode 1, it requires the caller to do that validation and casting 
before-hand, and rejects any parameter not of the correct type 
(e.g. both '123' and 'hello' are rejected for an int parameter)

#### Globally enabled? No
Each file will need to opt in to strict typing.
Otherwise, older libraries would be incompatible.

##### References
[wiki php](https://wiki.php.net/rfc/scalar_type_hints_v5)
[stack overflow](https://stackoverflow.com/questions/37111470/enabling-strict-types-globally)