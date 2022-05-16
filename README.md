Laravel Documentation
=====================
### Creating Coloum (Migration)

| Command | Description |
| ------- | ----------- |
| `$table->bigIncrements('id');` | Auto incrementing UNSIGNED BIGINT (Primary key) equivalent column |
| `$table->bigInteger('votes');` | Biginger equivalent column |
| `$table->boolean('confirmed');` | BOOLEAN equivalent to the table |
| `$table->date('created_at');` | DATE equivalent to the table|
| `$table->longText('description');` | LONGTEXT equivalent to the table |
| `$table->string('name', 100);` | VARCHAR equivalent with a length |
| `$table->text('description');` | TEXT equivalent to the table |
| `$table->time('sunrise');` | TIME equivalent to the table |

### Column Modifiers 
#### Required dependencies: composer require doctrine/dbal 

| Command | Description |
| ------- | ----------- |
| `$table->string('name', 50) ->change();` | Change the size of the coumn |
| `$table->renameColumn('from','to');` | Renaming columns |
| `$table->dropColumn('votes')` | Dropping Columns |
| `$table->dropColumn(['votes','avatar','location']);` | Dropping Columns |
| `$table->string('email')->nullable();` | make column nullable |

### Table Modifiers
#### Required dependencies: composer require doctrine/dbal
 
| Command | Description |
| ------- | ----------- |
| `Schema:: rename($from,$to);` | table rename |
| `Schema::drop('users');` | table delete |
| `Schema::dropIfExists('user');` | table delete if exits |

### Rolling back Migrations
 
| Command | Description |
| ------- | ----------- |
| `php artisan migrate:rollback` | rolls back the last "batch" of migration |
| `php artisan migrate:rollback --step=2` | roll back the last two migrations: |
| `php artisan migrate:reset` | roll back all of your application's migrations |
| `php artisan migrate:refresh` | roll back all your migrations and then execute the migrate command |
| `php artisan migrate:refresh --step=3` | rollback & re-migrate the last three migrations |
