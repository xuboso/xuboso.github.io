---
layout: post
title: Laravel Tips
published: true
---

[Laravel how to create resetful request](http://laravel.io/forum/02-20-2014-sending-a-delete-request-via-ajax)

[Laravel video tutorial](https://laracasts.com/series/laravel-5-fundamentals)

[awesome-laravel](https://github.com/chiraggude/awesome-laravel)

[awesome-php](https://github.com/ziadoz/awesome-php)

### Larave5 how to use migration to add or update column

1. You must use `php artisan make:migration` to generate a new migration file
2. Modify your new migration file
3. Use `php artisan migrate` to update database
4. Notice if you modify column you must add `dcotrine/dbal` in your composer.json file

``` php
    <?php

    // location app/database/migrations/2015_11_17_034816_add_role_to_users.php
    use Illuminate\Database\Schema\Blueprint;
    use Illuminate\Database\Migrations\Migration;

    class AddRoleToUsers extends Migration
    {
        /**
         * Run the migrations.
         *
         * @return void
         */
        public function up()
        {
            Schema::table('users', function(Blueprint $table)
            {
                $table->string('role');
            });

        }

        /**
         * Reverse the migrations.
         *
         * @return void
         */
        public function down()
        {
            Schema::table('users', function(Blueprint $table)
            {
                $table->dropColumn('role');
            });

        }
    }

```

### laravel how to resolve jsonp request
``` php
return response()->json(['result' => 'hello world'])->setCallback(Input::get('callback'));
```

### if you use laravel role based permission package Zizaco/entrust, you may get this error
you can go to [github issuse](https://github.com/Zizaco/entrust/issues/379#issuecomment-148379518) for answer
![laravel error image](/images/posts/laravel-error-1.png)

[How Laravel facades work](http://www.sitepoint.com/how-laravel-facades-work-and-how-to-use-them-elsewhere/)

[how to send email to activate account after use register](http://transmission.vehikl.com/do-more-during-registration-in-laravel-5/)
