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
public function employer() {
    return $this->hasMany(Job::class); // Will now show you all the jobs it relates to
}
```

### Pivot Tables


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

### Attaching a relationship
use the `attach()`