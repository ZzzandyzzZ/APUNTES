***
# PHP 
***

## DATOS

- Interprete de PHP: ZEND.
- En constantes no se usa el $.
```
cont nombre;
define('nombre','valor'); -> se puede usar funciones y variables
```
## FUNCIONES
- var_dump(): Tipo y valor de una variable
- gettype(): Tipo de una variable
- preg_match($patron,$text): existe o no el patron
- preg_match_all($patron,$text): guarda todas las coincidencias
- triggererror("mensaje",tipo):detiene ejecucion con error
- require_once('archivo.php'):incluir archivo
## STRING
- Comillas dobles: Revisa variables e incluye caracteres escapados.
- Comillas simples: Todo es string reconoce enter
- Concatenacion con '*'
- substr($string,inicio,tamaño-opc);
- strpos("string","q buscas",int(desde donde)-opc); => retorna int = posicion
- str_replace($search,$replace,$text,$count-opc);

## ECHO
### Heredoc
``` echo<<<ID
	texto " '
	ID;
--------------------------
	$variable=<<<ID
			ID;
```
### Nowdoc
- Funciona como comillas simples:
``` echo<<<'ID'
	texto " '
	'ID';
--------------------------
	$variable=<<<ID
			ID;
```
### sptrintf()
- Especificar tipo de dato:
```
	sptrintf("texto $d",int);
```
### printr()
- Imprime array
## ASIGNACION DE TIPO
- Dinamico: se asigna segun el valor que se le de.
- Forzado : (int)$variable
- Funcion : intval($variable)
## Operadores
- Ternario: (condicion)? expresion:expresion
- Elvis: $variable ?:valorPorDefecto => retorna la variable de no tener valor le asigna uno,debe tener valor null
- Fusion null : $variable ??valorPorDefecto => No debe tener ningun valor

## COndiciones

### IF ELSE
```
if(){         if():
}				
else{     =>  else:
}			  
			  endif;
```
## ARRAY

- list($variable,$var)=array('valor','val');

## FUNCIONES
- Anonima:
```
$fun = function(){};
$fun()
```
- Variable:
```
function fun(){}
$var='fun';
$var();
```
- Modo cuarsitivo:
```
function fun(int $a){}
fun('5');
```
- Modo estricto: Entradas y salidas
```
declare(strict_types=1):int;
```
## Clases
- Modificadores de acceso:
```
	public protected private
```
- Acceder a atributos:
```
	this->$var;
```
- Variables estaticas:
```
	Desde la clase: self::$var;
	Desde fuera: NombreClase::$var;
```
- Llamar funcion sin instanciar:
(new Clase())->fun();
- Clase anonima:
```
$var = new Class{}
```
### SET GET
- Funciones magicas:
```
	public function __set($atr,$val){
		$this->$atr=$val;
	}
	public function __get($atr){
		return $this->$atr;
	}
```
### herencia
- Acceder constructor o functiones:
`	parent::__construct();`
- Acceder a constantes:
`	self::var;`
### Constructor Destructor
```
function __construct(){}
function __destruct(){}

```
### Clase y function abstracta
```
abstract class Name{}
abstract function Name{}
```
### Polimorfismo
- Anulacion de funciones: Clase hija propia definicion.
- Sobrecarga de function: Funcion con diferentes parametros.
## Interfaces
- Implementacion:
```
interface Name{
public function Name();
public function Name2();
}
```
- Uso en clases:
```
class Name implements Interface{}
```
## Trait
- Hereder funciones que no tengan nada q ver con la clase:
```
trait Name{
function fun(){}
}
```

## Namespace
- Declarar:
```
namespace ubicacion;
class Name{}
```
- Escapar: No usar el namespace en herencia u otras clases
```
class Name extends \Herencia {}
```
- Uso:
```
$a = new ubicacion\Name;
use ubicacion;
use ubicacion as ub;
```
## Autocarga
```
private function loadClass($class){
	$path=str_replace('\\','/',$class).'php';
	if(file_exists($path))
		require_once($path);
}
public function load(){
	spl_autoload_register(array($this,'loadClass'));
}
```
## WEB 
- Metodo GET guarda los datos en el historial de la pagina,se ve en la URL.
- Obtener datos enviados desde un form:
```
	$var=_POST['name'];
	$var=_REQUEST['name'];
```
- Para verificar que metodo se uso:
```
$_SERVER['REQUEST_METHOD']=='POST'
```
- Redireccionar con encabezados:
```
	header('location:index.php?answer=hola');
```
- Recibir header:
```
	echo $_GET['answer'];
```
### SESIONES
- Para poder usar sesiones:
```
	session_start();
	Cambiar nombre de cookie:
	session_start(['name'=>'valor']);
```
- Eliminar todas las sesiones:
`	session_destroy()`
- Eliminar una sesion:
`	unset($_SESSION['name']);`
- Crear sesion:
` 	$_SESSION['name']='val'`
- Verificar si tiene valor:
`	isset($_SESSION['name'])`
## Base de datos
- Conectarse:
```
class Connection{
	private $driver='mysql';
	private $host='localhost';
	private $user='root';
	private $pass='';
	private $dbName='name';
	private $charset='utf8';
	protected function conexion(){
		try{
			$pdo = new PDO("{$this->driver}:host={$this->host};dbname={$this->dbName};charset={}",$user,$pdo->setAttribute(PDO::ATTR_ERRMODE,PDO::ERRMODE_EXCEPTION));
			return $pdo;
		}catch(PDOException){
			echo $e->getMessage();
		}
	}
}
```
- Operacinoes CRUD:
```
require_once('connection.php);
abstract class Crud extends Connection{
	private $table;
	$private $pdo;
	public function __construct($table){
		$this->table=$table;
		$this->pdo=parent::conexion();
	}
	public function getById($id){
		try{
			$stm=$this->pdo->prepare("SELECT * FROM $this->table WHERE id=?");

			$stm->execute(array($id));
			return $stm->fetchAll(PDO::FETCH_OBJ);
		}catch(PDOException $e){
			echo $e->getMessage();
		}
	}
	public function deleteById($id){
		try{
			$stm=$this->pdo->prepare("DELETE * FROM $this->table WHERE id=?");

			$stm->execute(array($id));
			return $stm->fetchAll(PDO::FETCH_OBJ);
		}catch(PDOException $e){
			echo $e->getMessage();
		}
	}
	abstract function
}
```