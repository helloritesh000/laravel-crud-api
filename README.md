# laravel-crud-api
Simple Article CRUD API in Laravel --> These steps have been followed to build this CRUD API in laravel
To run this please follow the 2nd section of this readme.

Section 1: 
------------------------
1) Create Laravel Project using cli command or composer
C:\xampp\htdocs> laravel new laravelcrud
  OR
C:\xampp\htdocs> composer create-project laravel/laravel laravelcrud
2) Goto project folder and set DB connection string in .env file
C:\xampp\htdocs> cd laravelcrud
3) Create articles migration
C:\xampp\htdocs\laracrud> php artisan make:migration create_articles_table --create=articles
output : Created Migration: 2019_06_15_135808_create_articles_table
4) Add additional properties in migration file in database/migrations/[date].create_articles_table.php file
5) Create dummy data for Article to play around (this include creating seed, factory, model under database folder)
C:\xampp\htdocs\laracrud> php artisan make:seed ArticleSeed
output : Seeder created successfully.
C:\xampp\htdocs\laracrud> php artisan make:factory articlefactory
output : Factory created successfully.
C:\xampp\htdocs\laracrud> php artisan make:model Article
output : Model created successfully.
6) Add the seed data in ArticleSeed.php and call in  call it in DatabaseSeeder.php
   public function run()
    {
        factory(App\Article::class, 30)->create();
    }
7) Build the seed data in article factory
    $factory->define(App\Article::class, function (Faker $faker) {
      return [
          'title' => $faker->text(50),
          'body' => $faker->text(200),
      ];
  });
8) Migrate the changes to DB for creating tables
C:\xampp\htdocs\laracrud> php artisan migrate
output : 
Migration table created successfully.
Migrating: 2014_10_12_000000_create_users_table
Migrated:  2014_10_12_000000_create_users_table
Migrating: 2014_10_12_100000_create_password_resets_table
Migrated:  2014_10_12_100000_create_password_resets_table
Migrating: 2019_06_15_135808_create_articles_table
Migrated:  2019_06_15_135808_create_articles_table
9) Place the dummy data to DB
C:\xampp\htdocs\laracrud> php artisan db:seed
output : Seeding: ArticleSeed
output : Database seeding completed successfully.
10) Create api controller and inplement as implemented in  App\Http\Controllers\ArticleController
C:\xampp\htdocs\laracrud> php artisan make:controller ArticleController --resource
output : Controller created successfully.
11) Create resource file used returning api calls
C:\xampp\htdocs\laracrud> php artisan make:resource Article
output : Resource created successfully.
12) Add api routes in routes/api.php
  Route::get('/articles', 'ArticleController@index');
  Route::get('/articles/{id}', 'ArticleController@show');
  Route::delete('/articles/{id}', 'ArticleController@destroy');
  Route::post('/articles', 'ArticleController@store');
  Route::put('/articles', 'ArticleController@store');
13) Verify in postman

Section 2:
-----------------------
1) Please the folder in xampp httpdocs folder or similar server public folder
2) Create a database in phpmyadmin and provide the connection string in .env file
3) Migrate the tables
  C:\xampp\htdocs\laracrud> php artisan migrate
4) Seed the data (not mandatory)
  C:\xampp\htdocs\laracrud> php artisan db:seed
5) Verify in postman


