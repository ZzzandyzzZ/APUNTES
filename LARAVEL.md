***
# LARAVEL 
***
## COMANDOS:

- Crear nuevo proyecto: <br>
`composer create-project --prefer-dist laravel/laravel ejemplo1 `


- Todos los comandos: <br>
`php artisan list `
- Cambiar nombre aplicacion: <br>
	`php artisan app:name ejemplo1`
- Crear controlador : <br>
	`php artisan make:controller nombre --resource`
- Crear modelo: <br>
	`php artisan make:model Nombre(singular) --migration(-m)`
- Crear migracion: <br>
	`php artisan make:migration nombre -table=nombretabla`
	`si el nombre de la migracion es create_nombre_table hara una clase especial para crear tablas`
- Crear Test:<br>
`	php artisan make:test EjemploTest (sufijo Test importante)`
- Ejecutar migraciones: <br>
	`php artisan migrate`

- Ejecutar seeders: <br>
	`php artisan migrate:refresh --seed`
- Eliminar migraciones en orden inverso <br>
	`php artisan:reset`
- Reset + migrate: <br>
	`php artisan:refresh`
	
- Eliminar ultimo grupo de migraciones:
	`php artisan:rollback`
- Ejecutar seeder: <br>
	`php artisan db:seed`

- Limpiar y ejecutar seed: <br>
	`php artisan migrate:fresh --seed`
- Autocompletar clases cuando uses tinker: <br>
	`composer dump-autoload`
- Crear factory con modelo:
	`php artisan make:factory NombreFactory --model=Modelo`
- Crear modelo con factory y migracion:
	`php artisan make:model Nombre -mf`
	
- Ejecutar test:
	`T: vendor\bin\phpunit`
- Hacer alias en windows:
	` doskey nombre=comando`
- Ejecutar aplicacion en celulares:
	`OPC: php artisan serve --host 0.0.0.0 --port 80`  
## UBICACIONES:

- rutas 'routes'

- vistas 'resources/views'

- 'timezone' Config app.php

- resources lang 'es'

- controladores http 

- modelos app 

- migracion database migrations

- env configurar base datos
## NOTAS:
- Studly Caps:
	Formato usado para variables o archivos : NombreArchivo
- ERROR por emojis app providers appservicePro.. ->boot Schema::defaultStringLenght(191);
	use Illuminate\Support\Facades\Schema


- para envio de archivos en un un form:
		enctype="multipart/form-data"
- Para acceder a la carpeta publica:
	asset('ruta/ruta');
- Para cambiar idioma:
	`config/app.php -> locale = es`

## TERMINOS:
- Composer:
		- Manejador de dependencias de PHP
		- Manejador de paquetes para PHP que proporciona un estándar para administrar, descargar e instalar dependencias y librerías
- Front Controller:
		Patron de diseño que usa laravel,todas las peticiones pasan por un solo archivo(index.php)
- REST:
		representational State Transfer
		
- Artisan:
		Interfaz de linea de comandos

- Http: Hipertext Transfer Protocol
		GET imagenes
		POST informacion 
		PUT/PATCH actualizar
		DELETE eliminar
- Controlador:
		Manejar peticiones del usuario
- CRUD:
		create,read,update,delete
- CSRF protection:cross site request forgery
		falsificacion de solicitudes entre sitios
- Eloquent ORM: object relational mapping 
		Es una tecnica de programacion para convertir datos utilizando un lenguaje de programacion oritantado a objetos y la utilizacion de una base de datos relacional como motor de persistencia.
		Para acceder a datos no SQL,sino LenOrieAObj
- Modelo:
		Capa encargada de mostrar la info de la BaseDatos= GESTIONAR
- Migracion:
		Tipo de control de versiones en la BD, modificar compartir esquema base datos.Puede crear tablas en PHP sin SQL.
- Slug:
		Forma amigable de representar texto de enlaces
- Seeder:
		Modulo que permite almacenar datos de prueba en nuestra aplicacion
- ORM (Object Relational Mapping) :
	ORM te permite convertir los datos de tus objectos en un formato correcto para poder guardar la información en una base de datos

## CODIGOS:

### RUTAS:

- Rutas con parametros:
	
``` 

Route::get('/name/{name}/apellido/{apellido?}',function($name,$apellido='HOLI'){
	return "HOLA ".$name." ".$apellido;
});

Route::resource('nombreRuta','nombreControlador@funcion');
```
- Condicionar rutas:
	- Enteros:
		``->where('variable'=>'[\d]+']);``
	- Valores exactos:
		``->where(['variable' => 'create|delete|update']);``
	- String:
		``->where(['variable' => '[-\w]+']);``
		
- Asignar nombre a la ruta:
`	Route::get('/ruta/ruta','controlador@funcion')->name('nombre')`
- Redireccionar desde un controlador a otra ruta:
` return redirect()-route('nombre.ruta');`

### VISTAS:

- para escapar HTML (mostrar codigo javascript como texto): <br>
	`e($variable);`
- Acceder a vistas: <br>

	`return view('nombreVista.funcion')`<br>
	`return view('carpeta.nombreVista')`

### PLANTILLAS:

- Plantilla principal:
	@yield('nombre')
	@extends('carpeta.principal');
- Para sobreescribir:
	@section('nombre')
	@show
- Para conservar ambos:
	@parent (en la secundaria,dentro de la seccion)
- Pagina secundaria:
	@section('nombre) <br>
	@endsection


### CONTROLADORES:

- Controlador con un solo metodo:
		function  __invoke($parametro){}
		Route::get('/ruta','controlador');


- Para pasar variables a una vista
		$elementosTabla = Modelo::all();

		return view('nombreVista',['nombreHTML'=>$elemtosTabla,mas parametros]);

		return view('nombreVista')with->(['nombreHTML'=>$elemtosTabla,mas parametros]);

		return view('nombreVista',compact('elementosTabla'));
- Para verificar si tiene un valor en la URL:
		URL = /ruta?nombre
		request()->has('nombre');
		controladores->store():
		return $request->all() para token y datos enviados
		return $request->input('nombreAtributo')
		$trainer = new NombreModelo();
		$trainer ->atributo=$request->input('atributo');
		$trainer->save();
		use NombreProyecto\NombreModelo
### BASE DE DATOS:
- Crear Tabla:
```
	public function up()
        Schema::create('nombre', function (Blueprint $table) {
            $table->atributos;
        });
```
- Modificar tabla:
```
	Schema::table('nombre',function(Blueprint $table){
		$table->string('adicional',tamaño(int))->modificador();
	});
	
	Schema::table('nombre',function(Blueprint $table){
		$table->dropColumn('NombreColumna');
	});

```
- Clave foranea:
```
	$table->foreign('actual_id')->references('llegada_id')->on('otraTabla');
	
	$tabla->dropForeign(['actual_id']);
	
```
- configurar BaseDatos:
	env
		DB_CONNECTION= 'pgsql'
		DB_PORT = 5432
		DB_DATABASE 
		DB_USERNAME
		DB_PASSWORD
	config->database.php
		‘default’ => env(‘DB_CONNECTION’, ‘pgsql’),
 para postgresql:
	
### SEEDERS:

- Argumentos adicionales:
` 	->first()`
`	->take(1)`
`	->take(1)->get() = ->first()`
`	->where('campo','comparacion','dato') `
`	->where('campo','=','dato') =  ->where('campo','dato')`
`	->where(['campo'=>'dato'])`
`	->whereCampo('dato')`
`	->value('campo')`
- Vaciar tabla:
`	DB::table('nombre')->truncate();`
- Vaciar varias tablas:
```
	foreach($tables as $table)
		DB::table($table)->truncate();
```

- Eliminar clave foranea:
`	DB::statement('SET FOREIGN_KEY_CHECKS = 0');`
- Activar clave foranea:
`	DB::statement('SET FOREIGN_KEY_CHECKS = 1');`
- Encriptar contraseñas:
`	bcrypt('contraseña');`
- Consultas SQL:
	SELECCIONAR:
	- INSEGURO:
`	$dato = DB::select('SELECT columna FROM tabla WHERE columna="dato" ');`
	- SEGURO:
`	$dato = DB::select('SELECT columna FROM tabla WHERE columna=?',['dato']);`
	INSERTAR:
	- INSEGURO:
`	$dato = DB::select('INSERT INTO tabla(campo) VALUES("dato")');`
	- SEGURO:
`	$dato = DB::select('INSERT INTO tabla(campo) VALUES(?)',['dato']);`
```
	$dato = DB::select('INSERT INTO tabla(campo) VALUES(:campo)',[
	'campo'=>dato'
	]);
```
- Insertar datos:
```
	NEW SEEDER run
	use Illuminate/Support/Facades/DB;
	DB::table('nombre')->insert([
		'columna'=> 'valor',
		etc
	]);
	DATABASE SEEDER run
		$this->call(NEW SEEDER::class);
		$this->call('NEW SEEDER');
```

- Seleccionar datos:
`	$variable= DB::table('nombre')->select('campo')->get();`
### MODELOS:
- NOTA: Podemos usar consultas SQL en modelos... con funciones magicas
- Funciones estaticas para el modelo

- Funciones publicas para una fila o registro

- Cargar de forma masiva: Crear un modelo con un array asociativo

- Para definir que atributos carguen de forma masiva:
`	protected $fillable=['campo','campo2'];`
- Convertir tipo de un atributo:
`	protected $casts=['campo' => 'boolean'];`
- Ocultar atributos:
`	protected $hidden=['campo'];`
- Guardar o actualizar en objetos:
`	$modelo->save();`
- Existe o no:
`	$modelo->exist;`
- Para acceder a un dato de clave foranea (relacion 1 a 1):
```
	Si el atributo es Modelo_id:
	public function pertenencia(){
		return $this->belongsTo(Modelo::class);
	}
	Si el atributo es diferente(id_Modelo):
	public function pertenencia(){
		return $this->belongsTo(Modelo::class,'id_Modelo');
	}
```
- Para accder a todos los pertenecientes a un modelo(relacion 1 a N):
```
	public function pertenecienteS(){
		return $this->hasMany(Modelo::class);
	}
```
- Llamar como atributo vs llamar como funcion:
```
	$modelo->funcion  // retorna collecion
	$modelo->funcion()->condicion()->get()    // retorna una relacion
	se puede añadir condiciones:
	
```
- Eliminar registro:
`	$modelo->delete();`
- Poner nombre de modelo y tabla distinto:
`	protected $table ='nombre_tabla;`
- No usar timestamps:
`	public $timestamps=false;`
- Crear registro:
```	
	Modelo::create([
		'campo'=>'valor'
	]);
```
- Seleccionar:
`	Modelo::where()->condicion();`
- Obtener solo un campo de un modelo:
`	modelo->pluck('campo');`

### FACTORIES:
- Definir factory:
```
	$factory->define(Modelo::class,function (Faker $faker){
		return [
			'campo' =>$faker->sentence(cantidad) // diferentes tipos
		]
	});
```
- Crear registros:
```
	factory(Modelo::class)->create([
		'atributo'=> 'valor
	]);
	
	Cantidad exacta:
	factory(Modelo::class,cantidad)->create();
	factory(Modelo::class)->times(cantidad)->create();
```

### TESTEO:
- Para tener mas detalle del error(en la funcion del test:
			$this->withoutExceptionHandling();
- Ejecutar los test:<br>
	function test_nombre(){}
	<br>
	/**@test */
	function nombre(){}
### PHP UNIT:
- En phpunit.xml agregar:
`	<env name="DB_DATABASE value="segundaDB" />`

### URLS:
- Para poner un enlace q es un URL en la pagina:
`	<a href="{{url('/direccion/dir2/'.$variable->dato)}}></a>`
`	<a href="{{url("/direccion/dir2/{$variable->dato}")}}></a>`
- Retroceder pagina:
`	<a href="{{url()->previous()}}></a>`
- Enlazar controladores:
`	<a href="{{action('controlador@funcion',['campo'->'dato'])}}></a>`
- Acceder a los nombres de las rutas:
`	<a href="{{route('nombre','['campo'=>'dato']')}}></a>`
### MANEJO DE ERRORES:
- Enviar un error 404:
`	return response->view('nombre',[datos],numero (status));`
- Simplificar pagina no encontrada en busquedas:
`	Modelo::findOrFail($id); `<br>
`	Buscara la vista en la carpeta error con valor 404`
### DEBUGUEAR
- para mostrar un dato:
		dd(function)
		
### DIRECTIVAS 

- LAYOUTS:
```
	@extends('carpeta.nombreLayout')
	@section('title','titulo')
	@section('content')@endsection
	{{$variable}}
```
- DIRECTIVAS PARA RECORRIDO:
```
	@foreach($elementosTabla as $eleTabla)
	@endforeach
```
- DIRECTIVA PARA CONDICIONES:
```
	@if
	@else
	@endif

	@unless = if(! condicion)

	@empty($variable)
	@else
	@endempty

	@forelse($lista as $i) = if(empty) 
	@endempty                else 
	@endorelse			     for() 
```

### REQUEST

- Obetener un request enviado por metodo post:
`	$variable = request()->all();`
- Acceder a datos de request:
`	$variable['campo'];`

## IMPORTAR CSV O EXCEL

- Nota: importar :
	`use App\Imports\ExampleImport;`
	`use Maatwebsite\Excel\Facades\Excel;`
	agregar archivos en:
	`storage\app`
1.- Instalar:
	`composer require maatwebsite/excel`
2.- Publicar archivo;
	`php artisan vendor:publish --provider="Maatwebsite\Excel\ExcelServiceProvider"`
3.- Crear modelo y migracion:
	`php artisan make:model -mc Example`
4.- Modificar en el modelo para agregar de forma masiva:
	`protected $guarded = [];`
5.- Crear el import con el modelo:
	`php artisan make:import ExampleImport --model=Example`
6.- Asignar a cada columna el valor correspondiente:
	```
	return new Example([
            'Name'=>$row[1],
			'Slug'=>$row[2]
        ]);
	```
7..- Cargar los datos:
	`Excel::import(new ExmpleImport, 'archivo.xls');`





