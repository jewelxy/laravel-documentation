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
=> Required dependencies composer require doctrine/dbal 

| Command | Description |
| ------- | ----------- |
| `$table->string('name', 50) ->change();` | Change the size of the coumn |
| `$table->renameColumn('from','to');` | Renaming columns |
| `$table->dropColumn('votes')` | Dropping Columns |
| `$table->dropColumn(['votes','avatar','location']);` | Dropping Columns |
| `$table->string('email')->nullable();` | make column nullable |
