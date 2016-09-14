### laphpadvtopic
#####Use PHP namespaces
project.php
```
<?php
namespace Project;
class Table{
  public static function get90{
    echo "Project.Table.get" 
  }
}
```

app.php
```
<?php
namespace App
include "project.php"
use Project\Table as ProjectTable;
class Table{
  public static function get(){
    echo "App.Table.get";
  }
}
ProjectTable::get();
```
#####Composer overview
[packagist](http://packagist.com)
```
composer require pkname
```
autoload
```
<?php
require __DIR__ . '/vendor/autoload.php';
use Rych\Random\Ran;
echo (new Random())->getRandomInteger(1,5) //[1,5]
```

####2. PHP interfaces
####3. PHP traits
#####PHP Traits overview
Traits provide implementation details
