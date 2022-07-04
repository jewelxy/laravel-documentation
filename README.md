Migration
=========
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


Query Builder
=============
### Retriving result
| Description | Query |
| ------- | ----------- |
| `Retriving all rows from a table` | DB::table('tbl_name')->get(); |
| `Retriving a single row` | DB::table('tbl_name')->where('name','typeName')->first(); |
| `Column from a table` | DB::table('tbl_name')->where('name','john')->value('email'); |
| `show by its id coloum value, use find method` | DB::table('tbl_name')->find(3); |
| `Retriving a list of column value` | DB::table('tbl_name')->pluck('col_name'); |
| `Retriving multiple column value` | DB::table('tbl_name')->pluck('title','name'); |
| `Retriving specific data` | DB::table('students')->where('id','1')->value('name'); |

### Aggregates
| Description | Query |
| ------- | ----------- |
| `Count row number`| DB::table('tbl_name')->count();|
| `Find max values` | DB::table('tbl_name')->max('col_name');|
| `Find min values` | DB::table('tbl_name')->min('col_name');|
| `FInd Average` | DB::table('students')->avg('col_name'); |


### Selects
| Description | Query |
| ------- | ----------- |
| `return distinict result`| DB::table('tbl_name')->distinct()->get();|
| `select single column` | DB::table('tbl_name')->select('name')->get();|
| `select multiple column` | DB::table('tbl_name')->select(' ', ' ')->get();|

### Merge
| Description | Query |
| ------- | ----------- |
| 			| $marks = DB::table('exm_marks')->get();|
| Join multi result | $student = DB::table('students')->get();|
|  			| $makeMerge = $student->merge($marks);|

### Left / Right  join clause
| Description | Query |
| ------- | ----------- |
| `Joining Column` | $resultJoin = DB::table('students')->leftJoin('std_marks','students.roll', '=', 'std_marks.roll')->get();|

### Data insert
| Description | Query |
| ------- | ----------- |
| `Insert new row` |DB::table('students')->insert(['name' => 'nameHere', 'class' =>'20','roll'=>'5' ],);|
| `Insert new row or ignore` |DB::table('students')->insertOrIgnore([ ['email' =>'toha@gmail.com', 'votes' => 0 ],['email' => 'meherima@gmail.com', 'votes' => 0 ,]);|

### Delete
| Description | Query |
| ------- | ----------- |
| `Delete row` |DB::table('students')->where('nname','=','sumon')->delete();|
| `Dlete all row but not reset autoincrement id` |DB::table('students')->delete();|
| `Delete all row and reset autoincrement id` |DB::table('students')->turncate();|

### Update
| Description | Query |
| ------- | ----------- |
| `Update data` |DB::table('students')->where('id',1)->update(['name' => 'newName');|

Eloquent ORM
=============
### Model Creation
| Description | Artisan Command |
| ------- | ----------- |
| `Model creation command` | php artisan make:model modelName |
| `With Migration` | php artisan make:model modelName -m |
| `Extra Classs` | use illuminate\Database\Eloquent\Model; |

### Model Properties
| Description | Query |
| ------- | ----------- |
| `To define table name` | protected $table = 'table name'; |
| `To define primary column` | protected $primaryKey = 'id'; |
| `To define increment status` |public $incrementing = false; |
| `To define primary column data type` |protected $keyTypes = 'string'; |
| `To define timestamps status` |public $timestamps = false; |
| `TO define date format` |protected $dateFormat = 'U'; |
| `To define db connection` |protected $connection = 'connection-name';|

### Model(Retriving result)
| Description | Query |
| ------- | ----------- |
| `Retriving all rows from a table` | ModelName::get(); |
| `Retriving a single row` | ModelName::where('name','Toha')->first(); |
| `Column from a table` |ModelName::where('name','john')->value('email'); |
| `show by its id coloum value, use find method` |ModelName::find(3); |
| `Retriving a list of column value` |ModelName::pluck('title'); |
| `Retriving multiple list of column value` |ModelName::pluck('title','name'); |

### Model(Retriving result)
| Description | Query |
| ------- | ----------- |
| `Count row number` | $users = ModelName::count(); |
| `Find max values` | $price = ModelName::max(' '); |
| `Find min values` | $price = ModelName::min(' '); |
| `FInd Average` | $price = ModelName::avg(' '); |

### Model(Selects)
| Description | Query |
| ------- | ----------- |
| `return distinict result` | ModelName::distinct()->get(); |
| `select single column` | ModelName::select('name')->get(); |
| `select multiple column` | ModelName::select(' ', ' ')->get(); |

### Model(Merge)
| Description | Query |
| ------- | ----------- |
|  | $marks =examMarksModel::get();|
|`Join multi result`| $student = studentsModel::get();|
|  |  $makeMerge = $student->merge($marks); |
