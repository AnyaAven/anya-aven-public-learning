## Create a Database Seeder

---

Group related seeders together in one file.

We can have an example of a one-to-many relationship of space to items.

`DatabaseDataSeeder.php`
```injectablephp
<?php

namespace Database\Seeders;

use App\Models\Item;
use App\Models\Space;
use App\Models\User;
// use Illuminate\Database\Console\Seeds\WithoutModelEvents;
use Illuminate\Database\Seeder;

class DatabaseDataSeeder extends Seeder
{
    public function run(): void
    {
        Space::factory()->count(6)->create();

        Item::factory()->count(8)->create();
    }
}
```

Run your shell command
```shell
 php artisan db:seed --class=DatabaseDataSeeder
```