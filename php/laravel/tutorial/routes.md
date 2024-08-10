## Routes

---
### `abort()` function
Use the `abort()` function to bubble up errors.
If you'd like to bubble up a 404:
```injectablephp
abort(404);
```

### 419 Error: CSRF
If you experience a 419 Error, you are attempting to send a post
with a tampered CSRF token; laravel will throw an error code of 419.

Add `@csrf` to your form in your blade template.