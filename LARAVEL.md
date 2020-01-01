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

- Ejecutar migraciones: <br>
	`php artisan migrate`

- Ejecutar seeders: <br>
	`php artisan migrate:refresh --seed`

## UBICACIONES:

- 'timezone' Config app.php

- resources lang 'es'

- controladores http 

- modelos app 

- migracion database migrations

- env configurar base datos
## NOTAS:

- ERROR por emojis app providers appservicePro.. ->boot Schema::defaultStringLenght(191);
	use Illuminate\Support\Facades\Schema
- env
		DB_PORT
		DB_DATABASE
		DB_USERNAME
		DB_PASSWORD

- para envio de archivos en un un form:
		enctype="multipart/form-data"

## TERMINOS:
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

## CODIGOS:

### RUTAS:

- Rutas con parametros:
	
``` 

Route::get('/name/{name}/apellido/{apellido?}',function($name,$apellido='HOLI'){
	return "HOLA ".$name." ".$apellido;
});

Route::resource('nombreRuta','nombreControlador');
```
### VISTAS:

- para escapar HTML (mostrar codigo javascript como texto): <br>
	`e($variable);`
- Acceder a vistas: <br>

	`return view('nombreVista.funcion')`<br>
	`return view('carpeta.nombreVista')`

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
- migracion->up->create:
		Atributos de la tabla
		$table->string('name');


### TESTEO:
- Para tener mas detalle del error(en la funcion del test:
			$this->withoutExceptionHandling();

### DEBUGUEAR
- para mostrar un dato:
		dd(function)






