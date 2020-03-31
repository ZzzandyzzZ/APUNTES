# JAVASCRIPT
## VARIABLES Y CONSTANTES
### Declaracion
- cont nombre
- var nombre
### Verificar tipo
- typeof
### Casteo
- parseInt()
- parseFloat()
- Number()
- numero.toString()
### Verificar si es numero
- isNan(valor)
### Verificar si es entero
- Number.isInteger(numero)
### Reondear
- numero.toFixed(1)
## String
### Tamaño
- variable.length
### Buscar
- Permite expresiones regulares 
`	cadena.search()`
- Busca cadena dentro de otra,desde un punto especifico,retorna primera posicion
`	cadena.indexOf("string",int)`
- Buscar ultimo encontrado,retorna ultima posicion
`	cadena.lastIndexOf()`
- Buscar todas las coincidencias
`	cadena.match("string")`
### Substring
- Inicio y tamaño,retorna string
`	cadena.substr(inicio,tamaño)`
- Inicio y cuenta del el inicio,retorna string
`	cadena.substring(inicio,tamaño)`
### Char en un indice
- cadena.charAt(posicion)
### Si empieza con una palabra
- cadena.startsWith("string");
### Si termina con una palabra
- cadena.endswith("string")
### Si incluye una palabra
- cadena.includes("string",inicio=0)
### Repetir un string
- a.repeat(numeroVeces)
### Reemplazar uns string dentro de otro
- a.replace("string","reemplazo")
### Cortar desde cierta posicion
- a.slice(posicion)
### Eliminar espacios al inicio y al final
- a.trim()
### Convertir a minusculas
- cadena.toLowerCase()

### Convertir a mayussculas
- cadena.toUpperCase()
### Concatenar
- cadena.concat("string")
### Escapar variables dentro de un string
- var cadena=`string ${variable}`
## ARRAY
### Crear
- var a = new Array(el,el2);
- var a = [el,el2];
### Obtener array de la pagina HTML
```
var content=Array.from(document.querySelectorAll(".clase"),);
var mapeo = content.map(val=>val.textContent);
```
### Tamaño
- array.length
### Insertar al final
- array.push(el)
### Eliminar el ultimo y retornarlo
- array.pop()
### Juntar el array en un solo string
- array.join()
### Ordenar forma creciente
- array.sort()
### Ordenar forma decreciente
- array.reverse()
### Recorrer por indice
- for(let i in array)
- array.forEach((el,i)=>accion)
### Buscar elemento y retornarlo.caso contrario undefined
- array.fin(el=>el=="valor")
### Buscar elento t retornar posicion
- array.finIndex(el=>el=="valor")
### Buscar todos los elementos
- array.filter(el=>el=="valor")
### SI hay valores q cumplen la condicion
- array.some(el=>el<40)
## Objetos
### crear
- var clase = new Clase(1);
- Por funcion:
```
function Clase(par){
	this.par=par;
	this.fun=function fun(){}
}
```
- Por clase:
```
class Clase{
	constructor(par){
		this.par=par;
	}
	fun(){}
}
```
### Herencia
- class clase extends Padre{}
### Llamar propiedades del padre
- constructor
`	super(par,par2)`

## TIPOS DE DATOS
### FECHA 
- var fecha = Date()
- fecha.getDate() => dia
- fecha.getHours() => hora
### Simbolos
- var simbolo = Symbol()
### Objetos
- var fecha = new Date()

## FUNCIONES
### Mas de un parametro
- function fun(...args){}
### Enviar array como parametro
- var args=[1,2,3];
- function fun(...args){}
### Funcion anonima
- var fun = function (arg,arg2){}
### Arrow function
- var fun = arg =>RETURN
- var fun = (arg,arg2) =>RETURN

## LOOPS
### Recorrer elementos
- for(let ele of array){}

## PAGINA WEB
### Agregar evento a boton
#### Mouse
```
var evento = document.querySelector(".name");
evento.addEventListener("clic",function(){});
// clic mousehover mouseout
```
#### Teclado
- Cualquier tecla
```
window.addEventListener("keypress",function(){});
// keypress keydown keyup
```
- Tecla especifica
```
window.addEventListener("keypress",function(event){
	alert(event.keyCode);
	alert(String.fromCharCode(event.keyCode));
});

```
### Funciones de carga
- Cuando la pagina termine de cargar
`window.addEventListener("load",function(){});`
### Funciones de tiempo
- Realiza la funcion cada cierto tiempo
```
var timpo=setInterval(function(){},2000);
```
- Reliza la funcion luego de pasar el tiempo
`setTimeout(function(){},2000);`


### Funciones multimedia
```
var video = document.querySelector(".name");
video.addEventListener("play",function(){});
// play ended seeking(adelantar)
```
## VENTANAS EMERGENTES
- alert()
- confirm()
```
	var confi =confirm("");
	if(confi){}
	else{}
```
- prompt()

## BOM (Browser Object Model)
### Atributos
- window.name
- Tamaño de toda la ventana : window.outerWidth
- window.outerHeight
- Tamaño del documento: window.innerWidth
- window.innerHeight
- Scroll horizontal: window.pageXOffset
- window.pageYOffset
-  Distacia del monitor a la ventana,por la izquierdawindow.screenX
-  Distacia del monitor a la ventana,por arriba: window.screenY
### Funciones
- window.alert()
- Se puede declarar otra variable y usar las propiedades de window
- var ven = window.open("URL")
- window.close()
- Aumentar tamaño: window.resizeBy(x,y)
- Cambiar tamaño: window.resizeTo(x,y)
- window.moveBy(x,y)
- window.moveTo(x,y)
- Traer adelante: window.focus()
- Imprimir en papel: window.print()
- Cantidad de frames: window.length
### Frame
- Creacion
```
	<iframe src="URL" width=""></iframe>
```
### History
- Historial de cambios y obejtos usados en la pagina
- var historial =window.history;
### Location
- Path donde se encuentra el sitio web
- var localizacion = window.location
### Navigator
- Tipo de navegador que usamos
- var navegador = window.mavigator.vendor;
### Screen
- Caracteristicas de la pantalla
- var pantalla = window.screen
## DOM (Document Objetc Model)
### Obtener un elemento del HTML
- var a=document.querySelector("#id");
- var a=document.querySelector(".clase");
- var a=document.querySelector("a[class="name"]");
- var a = document.getElementById("name");
### Obtener varios elementos
- var a=document.querySelectorAll("#id");
- var a=document.querySelectorAll(".clase");
- var a = document.getElementsByClassName("name")[0];
- var a = document.getElementsByTagName("p")[0];
### Obtener un elemento en un orden
- var a=document.querySelectorAll("id")[posicion];

### Cambiar estilos de objeto HTML
- a.style.propiedad="valor";
### Cambiar contenido
- a.innerHTML="contenido";
- a.innerHTML+="contenido";
### Cambiar Clase
- a.className=a.className.replace("deEste","aEste");

