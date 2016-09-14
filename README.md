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
