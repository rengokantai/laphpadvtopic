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
#####PHP interfaces overview
ex
```
<?php 
interface LogInterface{
  public function log(string $mes);
}
```
use
```
<?php
class Query{
  public function logQuery(LogInterface $logger, string $mes){
    $logger->log($mes);
    return true;
  }
}
```
#####PHP standard interfaces (SPL)
```
Countable->count(void)
OuterIterator->getInnerIterator(void)
RecursiveIterator->getChildren hasChildren
SeekableIterator->seek(int)
```
####3. PHP traits
#####PHP Traits overview
Traits provide implementation details.  
One of the advantages of a trait, over an interface, is that the trait can provide methods with any visibility level. interfaces can only provide public method signatures.  

ex
```
<?php
trait Log{
  protexted function log($msg){
    echo ""
  }
}

class Table{
  use Log;
  public function saeve(){
    $this->log(''); //use this everyehere
  }
}
```
####4. Advanced PHP Object-Oriented Programming
#####PHP magic methods
ex
```
__sleep
__wakeup
```
```
__invoke // It gives us the ability to create classes that are called invokable classes.In essence, we create classes that can have one method, their invoke method.
```
Ex: __invoke
```
class Compare{
  public function __invoke($a,$b){return $a===$b;}
}
$comp = new Compare;
$comp(1,2); //false
```
#####PHP constructors and deconstructors
Deconstructor:  
The goal here is to destroy any other state that your object has that needs to be released.  
Once PHP knows there are no more references to that class or that PHP itself is performing a shut down  
ie. that the request is completed and everything is being completed on PHP side, that is when the deconstructor runs.  



####8. PHP Password Hashing
#####PHP password hashing
```
password_hash  //5.5+
```
usage
```
password_hash(string $password,integer $algo[,array $options])
//algo= PASSWORD_DEFAULT, PASSWORD_BCRYPT
//options: deprecated in PHP7
```
#####PHP password verification
ex
```
<?php
$pass = password_hash("ke",PASSWORD_DEFAULT);
echo "{$pass}"
$match = password_verify('wrong",$pass);
```

#####Update PHP passwords
ex
```
<?php
$pass = password_hash("ke",PASSWORD_DEFAULT);
echo "{$pass}"
if(password_needs_rehash($pass,PASSWORD_DEFAULT,['cost'=>10]){
  $newHash=(password_needs_rehash('test',PASSWORD_DEFAULT,['cost'=>10])
}
```
####9. PHP type hints
#####Basic PHP type hints

#####PHP strict type declarations
bool,float,int,string  
Four examples:
```
function sum(int $a,int $b){
  return $a+$b;
}
sum(0.5,0.5); //0 decimal part is stripped
```

```
declare(strict_types=1);
function sum(int $a,int $b){
  return $a+$b;
}
sum(0.5,0.5); //error
```
Ex3: strict declaration in callee
```
file1.php
declare(strict_types=1);
function sum(int $a,int $b){
  return $a+$b;
}
//file2.php
sum(0.5,0.5); //0
```

Ex4: strict declaration in caller
```
file1.php
function sum(int $a,int $b){
  return $a+$b;
}
//file2.php
declare(strict_types=1);
sum(0.5,0.5); //error
```


####11. PHP Exceptions
#####PHP exception overview
```
public __construct ([string $message="" [, int $code=0[,Throwable $previous=NULL]]])
```

#####Nested exceptions
```
<?php
try{
  a();
}catch(Exception $e){
  echo $e->getMessage();
  echo $e->getPrevious()->getMessage();
}

function a($num=null){
  try{
    b($num);
  }catch(Exception $e){
    throw new Exception('error from a',null, $e);
  }
}

function b($num){
  if(is_null($num)){
    throw new Exception('error from b');
  }
}
```
#####PHP SPL exceptions
#####Extend PHP exceptions
```
<?php
class KeException extends InvalidArgumentException{
    
}
```
