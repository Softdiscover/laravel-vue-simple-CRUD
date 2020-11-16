# Laravel CRUD

## Steps to create the CRUD with vue

1.  `composer create-project --prefer-dist laravel/laravel test`
2. then add `test` folder to virtualhost in order to run the application
3. installing UI package: `composer require laravel/ui`
3. then add auth module: `php artisan ui vue --auth`
4. before running migrate, go to app/Providers/AppServiceProvider.php and modify:
```
<?php

namespace App\Providers;

use Illuminate\Support\ServiceProvider;
use Illuminate\Support\Facades\Schema;

class AppServiceProvider extends ServiceProvider
{
    /**
     * Register any application services.
     *
     * @return void
     */
    public function register()
    {
        //
    }

    /**
     * Bootstrap any application services.
     *
     * @return void
     */
    public function boot()
    {
        //
        Schema::defaultStringLength(191);
    }
}

```
5. then run: `php artisan migrate`
6. then install npm dependencies: `npm install`
7. to compile assets run the command: `npm run dev`


## adding new controllers
1. In order to add new controller, run the following command:
	`php artisan make:controller ThoughtController --api`
2. for making model:
	`php artisan make:model Thought -m`
3. then migrate `php artisan migrate`
4. then create a seeder: `php artisan make:seeder UsersTableSeeder`
5. adding this code on UsersTableSeeder on run method: 
```
<?php

namespace Database\Seeders;

use Illuminate\Database\Seeder;
use App\Models\User;
class UsersTableSeeder extends Seeder
{
    /**
     * Run the database seeds.
     *
     * @return void
     */
    public function run()
    {
        User::create([
            'name' => 'Juan',
            'email' => 'hola@poasdfa.com',
            'password' => bcrypt('asdfasdf')
        ]);
    }
}

```

6. then run `php artisan db:seed`
7. clean cache `php artisan config:cache`.
8. check routes with: `php artisan route:list`

   

 
