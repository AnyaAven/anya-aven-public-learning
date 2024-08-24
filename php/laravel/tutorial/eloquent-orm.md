## Eloquent 
Eloquent is the Laravel ORM.

### To set up your models and table

```injectablephp
use Illuminate\Database\Eloquent\Model;

class Job extends Model
{
    // Code here
}
```

### "Convention over Configuration"

If you have a table called "jobs" your model would be "Job"

### Table and Model name
When using `Job::all();`, Eloquent will look for a table called "jobs."

If you'd like it to find a different table name 
```injectablephp
class Job extends Model
{
    protected $table = 'job_listings';
}
```

### Create
```injectablephp
Job::create(['title' => 'Director', 'salary' => '$1,000,000'])
```
Error!
>   Illuminate\Database\Eloquent\MassAssignmentException  Add [title] to fillable property to allow mass assignment on [App\Models\Job].

Laravel does not allow data to be added this way. This is because the data
could be malicious (maybe from a form request) and is not verified.

To change this we need to add a `title` property to our `Job` model. 
```injectablephp
    protected $fillable = ['title', 'salary'];
```
Now _only_ `title` and `salary` will be fillable. 
If the user entered a non fillable property `is_admin` it will be ignored by Eloquent.

#### fillable vs guarded
We can either say what we want to fill (more specific and secure!) or we can
say what we want to be gaurded and _not_ filled.
```injectablephp
protected $guarded = [];
```

### Auto Time Stamps
Eloquent always adds `created_at` and `updated_at`

### Factory

To add a factory to your class add the `hasFactory` trait with `use HasFactory`.
You will also need a class in `Database\Factories`.

```injectablephp
class UserFactory extends Factory
{
    /**
     * The current password being used by the factory.
     */
    protected static ?string $password;

    /**
     * Define the model's default state.
     *
     * @return array<string, mixed>
     */
    public function definition(): array
    {
        return [
            'name' => fake()->name(),
            'email' => fake()->unique()->safeEmail(),
            'email_verified_at' => now(),
            'password' => static::$password ??= Hash::make('password'),
            'remember_token' => Str::random(10),
        ];
    }
}
```

Use the `fake` / `faker` api to simulate real data.
```injectablephp
fake()->name();
fake()->unique()->safeEmail();
```

#### To add fake data:
```injectablephp
User::factory(10)->create(); // This will create 10 fake users
```

#### Variations of users
Add a state (static method) on your factory.

In this case we will have a user with an unverified email:
```injectablephp
public function unverified(): static
    {
        return $this->state(fn (array $attributes) => [ // notice the state() func
            'email_verified_at' => null,
        ]);
    }
```

To add an unverified user:
```injectablephp
User::factory()->unverified()->create(); // This will create 1 unverified fake user
```

---
### Relationships
#### Adding Foreign Keys

Inside your migration file, we can add: 
```injectablephp
$table->foreignIdFor(\App\Models\Employer::class);
```
You'll also need to update your Model's factory:
``employer_id => Employer::factory()``

#### Update your Models

`Job`
```injectablephp
public function employer() {
    return $this->belongsTo(Employer::class);
}
```

`Employer`
```injectablephp
public function jobs() {
    return $this->hasMany(Job::class); // Will now show you all the jobs it relates to
}
```
---
### Querying

Querying returns a `collection` type similar to an array.
```injectablephp
// All
$users = User::all();
// Find by id
$users = User::find(3) // id 3
// Find by relation
$users = User->employer->name; // Finds the employer relationship on the model and returns the name
```

---
### Attaching a relationship (many to many)
use the `attach()`

---
### Eager vs Lazy loading
Use the debug toolbar to keep track of queries. 

[Episode](https://laracasts.com/series/30-days-to-learn-laravel-11/episodes/13)

---
### Pagination
Instead of getting every relationship with eager loading, we
can paginate our loads.
```injectablephp
$jobs = Job::with('employer')->get(); // get all the jobs with employer relationship
$jobs = Job::with('employer')->paginate(3); // Get all of them them 3 at a time
```
You can see it if you add a query to the url, `?page=2`, `?page=3`, etc.

In the view for blade you can add `{{ $jobs-> links() }}`

#### Simple
We could also have simple pagination, only showing `previous` and `next` buttons
instead of page 1 through 8 for example.
```injectablephp
$jobs = Job::with('employer')->simpleOaginate(3); 
```
> Simple pagination is very common and usually it's not common 
> for a user to want to go from page 2 to page 8 with regular pagination.

#### Cursor 
This is the most optimized version of pagination but at the cost of the url.
It cannot be linked to as the url is random like `?cursor=t738qq34ith`.

The encoded string will hold the information of what to grab next. 
This is only useful with extremely large data sets.
```injectablephp
$jobs = Job::with('employer')->cursorOaginate(3); 
```

---
### Seeder

You can customize your seeder per model in the `seeder` directory.
Use factories to set up unique data base seeds.

Run this to seed your Database:
```injectablephp
php artisan db:seed
```

## After Tutorial Knowledge
--------------------------------------------------------------------------------

### Pluck

To pluck / find certain data from a model:
```injectablephp
$users = User::pluck('name'); // [ 0 => Victor Rowe" 1 => "Julianne Orzo" ]
```
