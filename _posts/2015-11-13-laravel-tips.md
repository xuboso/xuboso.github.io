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
