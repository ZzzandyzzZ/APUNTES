# PYTHON
## LISTA
### Sublistas:
- sub=list[0:3] : de la posicion 0 hasta 2
- sub=list[:3] : de la posicion 0 hasta 2
- sub=list[1:] : de la posicion 1 hasta final
- sub=list[1::2] : de la posicion 1 hasta final de dos en dos

- sub=list[::-1] : inverso

### Ordenar:
- ascendente: lista.sort()
- descendente: lista.sort(reverse=true)
### MAX MIN
- a = min(lista)
- a = max(lista)
### Tamaño
- len(lista)
### Buscar
- valor in lista => booleano
### Indice de valor
- lista.index(valor) => int
### Contar elemento
- lista.count(valor) => int
## TUPLA
- tupla =(1,2,3)
- acceder tupla[1]
### Asigna valores
- uno,dos,tres =tupla[0] ,tupla[1] ,tupla[2]
- uno,dos,tres =tupla
### Operador * para elementos restantes
- uno ,* dos =tupla => dos =[2,3]
### Asociar elementos de dos tuplas o listas
```
tupla =(1,2,3,4)
lista=[3,5,7,9]
tuple(zip(tupla,lista))
//resultado ((1,3),(2,5),(3,7),(4,9))
```
### Ignorar elementos:
- _,uno,dos =tupla
- Varios elementos *_
### Convertir a lista
- nuevo = list(tupla)
### Convertir lista a tupla
- nuevp = tuple(lista)

## STRING 
### Separar string
- cadena.split("; ");
### Juntar lista de strings
- "separador".join(lista)
### String con salto de linea
```
texto="""
a
b"""
texto.splitlines()
```
### Primera letra en mayuscula
- resultado = texto.capitalize()
### Invertir mayusculas y minusculas
- resultado = texto.swapcase()
### Todo a mayuscula
- resultado = texto.upper()
### Todo a miniscula
- resultado = texto.lower()
### Verificar si es mayuscula o minuscula
- texto.isupper() texto.islower()
### Primera letra de cada palabra en mayuscula
- texto.title()
### Reemplazar char
- texto.replace(original,reemplazo,cuantasVeces(opc))
### Quitar espacios al inicio o final
- texto.strip()
### Asignacion dinamica de string
- resultado =" TEXTO POR %s" %("ENTRADA")
- resultado =" TEXTO POR {a}".format(a="ENTRADA")
### Buscar textos
- texto.count("texto")
- "texto" in texto
- texto.find("texto")
### Verificar si inicia o termina con un string especifico
- texto.starstwith("texto")
- texto.endswith("texto")
## Diccionario
- diccionario ={}
- diccionario =dict()
- diccionario ={"A":10}
### Obtener llaves y valores
- dic.keys()
- dic.values()
- dic.items()
### Obtener dato y asignar dato por defecto:
- dic.get("key",value])
- dic.setdefault("key",value])
### Eliminar 
- del dic["valor"]
- dic.pop("valor")
### Limpiar
- dic.clear()
- dic ={}
## Ciclo 
- Reccorrer con valores e indice
```
for indice ,valor in enumerate(lista):
	print(indice,valor)
```

## Variable
### Asignar con condicion:
- var="valor" if condicion else "valor2"
## Funciones
### Parametros indefinidos
- def fun(*args):
- def fun(requerido,*args):
### Variable funcion:
```
def fun():
	return "a"
varFun=fun;
varFun()
```
### Funcion lambda
- fan=lambda parametro=default,par2 : operacion
