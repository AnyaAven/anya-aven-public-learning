## Routes

---
### `abort()` function
Use the `abort()` function to bubble up errors.
If you'd like to bubble up a 404:
```injectablephp
abort(404);
```

---
### 419 Error: CSRF
If you experience a 419 Error, you are attempting to send a post
with a tampered CSRF token; laravel will throw an error code of 419.

Add `@csrf` to your form in your blade template.

---
### Validation
Inside your route you may validate data off of the request.
```injectablephp
request()->validate([
'title' => ['required', 'min:3'],
'other field name...' => ['required'],
]);
```
Laravel will automatically fail the route if the form isn't valid and send the 
user back to the url with the errors.
Inside your template you will have `$errors` array.

---
### Route Model Binding
Instead of finding a job manually, we can use a route model binding for a cleaner,  
more readable code.

```injectablephp
// Show Route
Route::get('/jobs/{id}', function ($id){
    $job = Job::find($id);
    
    return view('jobs.show', ['job' => $job])
});
```

Vs.

```injectablephp
// Show Route
Route::get('/jobs/{job}', function (Job $job){ // This tells laravel that we no 
    // no longer expect a string for $id but rather a Job instance.
    
    return view('jobs.show', ['job' => $job])
});
```

Both the wildcard and the parameter need to be the same, laravel will find the Job
based on id passed into within the wildcard. 
The wildcard refers to the `{job}` in the URI.
By default, it will find by the id, but can also be changed. 
For example, the URI could be `/jobs/{job:slug}` vs the default of `/jobs/{job:id}`
(Don't need to say `:id` as that is the default, they are the same thing).


## After Tutorial Knowledge
--------------------------------------------------------------------------------

### Regular expressions in Routes
This is fairly obscure knowledge and may not be relevant.

This route will accept not just any endpoint, only the endpoint that matches the 
regular expression in the `where` method.
```injectablephp
Route::get('/{any}', function() {
    return view('app');
})->where('any', '^(?!api).*');
```