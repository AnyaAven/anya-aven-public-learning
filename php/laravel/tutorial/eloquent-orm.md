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