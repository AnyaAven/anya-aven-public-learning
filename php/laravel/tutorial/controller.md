## Controllers

---

Controllers to abstract the data out of the route files.

---

### Make a controller with Artisan
```shell
php artisan make:controller
```

Name the file with common conventions of `ModelnameController`, example: `UserController`.

---
### Controller Methods
Use these methods:
* Index: All the instances (paginated if needed)
* Create
* Edit
* Update
* Destroy

An example with a model of `User`:
```injectablephp
<?php

namespace App\Http\Controllers;

use App\Models\User;
use Illuminate\Http\Request;

class UserController extends Controller
{
    public function index()
    {
        $users = User::all();

        dd($users);

    }

    public function create()
    {
        User::create([
            'name' => \request('title'),
            'email' => \request('email'),
            'password' => \request('password'),
        ]);

        return redirect('/users');
    }

    public function edit(User $user)
    {
        return view('users.edit', ['user' => $user]);
    }

    public function update(User $user)
    {
        // Authorize if needed

        // Validate info
        \request()->validate([
            'name' => ['min:1'],
        ]);

        return redirect('/users' . $user->id);
    }

    public function destroy(User $user)
    {
        // Authorize if needed
        $user->delete();

        return redirect('/users');
    }
}
```

---
### Inside your routes file

```injectablephp
Route::get('/users', [UserController::class, 'index']);
Route::get('/users/create', [UserController::class, 'create']);
Route::get('/users/{user}', [UserController::class, 'show']);
Route::post('/users', [UserController::class, 'store']);
Route::get('/users/{user}/edit', [UserController::class, 'edit']);
Route::patch('/users/{user}', [UserController::class, 'update']);
Route::delete('/users/{user}', [UserController::class, 'destroy']);
```

