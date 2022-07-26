# Python profesional

# ¿Cómo funciona Python?

Existen lenguajes de programación compilados y lenguajes de programación interpretados. 

Por ejemplo, C++ es un lenguaje compilado

![Untitled](Python%20profesional%20af58b7d07f6d4fe8b6c905504f747d10/Untitled.png)

Lo que sucede en C++ es que las líneas de código se transforma mediante el compilador (una herramienta que posee el lenguaje) a código máquina. C++ se comunica directamente con la computadora utilizando el compilador, por eso se llama compilador.

C++ y la computadora se comunican por medio de un compilador, pero Python no es así. Python es un lenguaje interpretado.

![Untitled](Python%20profesional%20af58b7d07f6d4fe8b6c905504f747d10/Untitled%201.png)

No pasamos a código de máquina, sino a bitcode. El bitcode es un lenguaje especial, que puede ser leído por un interprete. Lo especial del bitcode es que es leído por una máquina virtual. Esta máquina puede ser ejecutada en diferentes sistemas operativos. Es por eso que se dice que Python es multiplataforma. 

![Untitled](Python%20profesional%20af58b7d07f6d4fe8b6c905504f747d10/Untitled%202.png)

## ¿Qué es el garbaje collecto?

En python se tiene una sección del lenguaje de programación, una de sus partes es el recolector de basura. Esta toma los objetos y variables que no están en uso y eliminarlas. 

## ¿Qué es la carpeta _pycache_?

Lo que está adentro de esta carpeta es el bitcode para que pueda ser leído por la máquina virtual, esta funciona como un tipo de recuperación de código. 

# Cómo organizar las carpetas de tus proyectos

## Módulos

`random` es un módulo.  Un módulo es cualquier archivo de python. Generalmente un módulo contiene código que se puede reutilizar. 

## Paquete

Una carpeta que contiene módulo: siempre posee el archivo __init__.py.

Ejemplo se tiene el paquete para poder realizar exploración espacial

![Untitled](Python%20profesional%20af58b7d07f6d4fe8b6c905504f747d10/Untitled%203.png)

y la organizacioń de esta sería 

![Untitled](Python%20profesional%20af58b7d07f6d4fe8b6c905504f747d10/Untitled%204.png)

# ¿Qué son los tipados?

> Estático, dinámico, débil y fuerte.
> 

![Datos primitivos.](Python%20profesional%20af58b7d07f6d4fe8b6c905504f747d10/Untitled%205.png)

Datos primitivos.

Así como existen varios tipos de datos primitivos, también existen varios tipos de lenguajes.  Un lenguaje va a tener un tipado diferente dependiendo cómo trata a los tipos de datos. 

![Untitled](Python%20profesional%20af58b7d07f6d4fe8b6c905504f747d10/Untitled%206.png)

Este cuadrante muestra que tipo de tipado es cada lenguaje.

![Untitled](Python%20profesional%20af58b7d07f6d4fe8b6c905504f747d10/Untitled%207.png)

En esta imagen se puede ver como es correr un código compilado, que conlleva tiempo de compilación y tiempo de ejecución. 

## Tipado estático

Son los que levantan los errores de tipos en tiempo de compilación. 

![Untitled](Python%20profesional%20af58b7d07f6d4fe8b6c905504f747d10/Untitled%208.png)

El programa no se va a ejecutar hasta que corrijamos ese error. 

```java
String str = "Hello";
str = 5;
```

Un ejemplo es en Java, que es un lenguaje estático donde con este programa a la hora de querer correr este programa lanzará un error. Este error no sucede en Python, pero sí en Java.

## Tipado dinámico

Son lo opuesto a los tipados estáticos, no levantan el error en el tiempo de compilación sino hasta el tiempo de ejecución.

![Untitled](Python%20profesional%20af58b7d07f6d4fe8b6c905504f747d10/Untitled%209.png)

Un ejemplo de tipado dinámico es Python. Aunque este no tiene un tiempo de compilación. Ejemplo:

```python
str = "Hello"
str = 5
```

Este código funcionará y no dará error. Dado que Python comparte otra de las calificaciones.

```python
x = 1 
y = "2"
z = x + y #Esto fallará
```

Este código va a fallar dado que Python es tipado fuerte. 

## Tipado fuerte vs débil

El lenguaje de tipado fuerte tratan con más severidad los errores de tipo mientras los de lenguaje débil son más flexibles

# Tipado estático en Python

Python es un programa dinámico, pero también podría volverse uno estático. 

## Static Typing

### Con variables

```python
a: int = 5
print(a)

b: str = "Hola!"
print(b)

c: bool = True
print(c)
```

Se coloca ese dos puntos int en nuestro código. Así se le asigna tipo a las variables en Python, esto es desde la versión 3.6 en adelante. 

### Con funciones

```python
def suma(a: int, b: int) -> int:
	return a+b

print(suma(a,b))
```

Para decir que ambos parámetros serán enteros, se hace lo mismo para las variables.  También podemos decir que tipo de variable va a retornar la función con -> int:. 

```python
def suma(a: int, b: int) -> int:
	return a+b

print(suma("a","b"))
```

Si se tiene ahora que los valores que tomará la función suma son del tipo str dará resutado 12 y no lo marca como error.

### Con listas y diccionarios

```python
from typing import Dict, List

positives: List[int] = [1, 2, 3, 4, 5]
users: Dict[str, int] = {
	'argentina': 1,
	'mexico': 34,
	'colombia': 45,
}

countries: List[Dict[str, int]] = [
	{
		'name': 'Argentina',
		'people': '450000',
	},
	{
		'name': 'México',
		'people': '900000',
	},
	{
		'name': "Colombia",
		'people': '9999999999999',
	},
]
```

Se importa Dict y List y se puede escribir de la forma mostrada. Indicando los tipos que tendrán,

### Con tuplas

```python
from typing import Tuple
numbers: Tuple[int, float, int] = (1, 0.5, 1)
```

La diferencia con las listas es que las tuplas son inmutables, se puede definir de que será cada valor que tenga.

# Practicando tipado estático

```python
#Código de un programa profesiona para un saber si una cadena 
#de carácteres es un palíndromo

#Función que define si es un palíndromo o no
#Toma valores string y devuelve uno del tipo booleano
def is_palindrome(string: str) -> bool:
    #Reemplaza los espación por espacios vaciós
    #Para dar la oportunidad de escribir frases
    #con el método .lower colocamos todo minúsculas
    string = string.replace(" ", "").lower()
    #Se le da vuelta al iterable
    return string == string[::-1]

def run():
    print(is_palindrome())
    

if __name__ == '__main__':
    run()
```

Esta es programa para saber si algo es un palíndromo. El problema se presenta cuando se le intenta dar como parámetros a la función una variable del tipo int. Pero el Traceback no da la información, por eso se hace uso de mypy corriendo lo siguiente en consola

`mypy [palindrome.py](http://palindrome.py) —check-untyped-defs`

MyPy dice lo siguiente: Encontramos un error en un archivo. El argumento 1 de la función “is_palindrome” es incompatible porque espera un valor str no un int.

# Scope: alcance de las variables

Una variable solo está disponible dentro de la región donde fue creada.

## Local scope

```python
#Local scope

def my_func():
	y = 5
	print(y)

my_func()
```

Es la región que corresponde al ámbito de una función donde vive una o más variables. 

En este ejemplo la variable y está creada dentro del scope local, dentro del alcance local de esta función y no puede ser leída afuera. 

## Global scope

```python
#Global scope

y = 5

def my_func():
	print(y)

def my_other_func():
	print(y)

my_func()
my_other_func()
```

Existe también el global scope que se tiene variables que tienen alcance en todo el programa. Si se crea la variable y fuera de las funciones puede ser leída dentro de todas la funciones que tengamos después.

Esto sucede porque el global scope, la región de la variable es todo nuestro código.

Ejemplo:

```python
z = 5

def my_func():
	z = 3
	print(z)

my_func()
print(z)
```

En este caso al ejecutar este código imprime primero 3 y luego 5, porque hacen referencia a diferentes variables

```python
z = 5

def my_func():
	z = 3
	
	def my_other_func():
		z = 2 
		print(z)

my_other_func()
print(z)

my_func()
print(z)

```

El resultado obtenido seráa 2, 3, 5. Se tiene 3 variables, una en scope global y dos en scope local.

# Closures

## Nested functions (funciones anidadas)

Funciones creadas dentro de otra función.

```python
def main():
	a = 1
	def nested():
		print(a)
	#nested()
	return nested()

my_func = main()
my_func()
```

 

Esto, además de ser una función anidada también es un closure.  Un closure se da cuando una variable que está en un scope superior es recordada por una función que está en un scope inferior.

```python
def main():
	a = 1
	def nested():
		print(a)
	#nested()
	return nested()

my_func = main()
my_func()
#Código para borrar una función
del(main)

my_func()
```

Al realizar este cambio se espera que la función my_func() del final ya no corriera dado que la función main() fue eliminada, pero no es así. Esta sigue su curso. Esto es porque el closure está recordando una variable de scope superior. 

Un scope entonces, recuerda variables de orden superior aunque estas sean eliminadas.

**reglas para encontrar un closure**

1. debemos tener una nested function
2. la nested function debe referenciar un valor de un scope superior
3. la función que envuelve la nested debe retornarla también

cuando tenemos una clase que tiene solo un métodocuando trabajamos con decoradores.

```python
def make_multiplier(x):
	def multiplier(n):
		return x*n
	return multiplier

times10 = make_multiplier(10)
times4 = make_multiplier(4)

print(times10(3))
print(times4(4))
print(times10(times4(2)))
```

En este caso se tiene la función make_multiplier que recibe x y la nested function multiplier toma valores de n, pero recuerda valores de un scope superior porque retorna el valor de x*n. Esto regresa multiplier.

Cumplimos las 3 reglas: tenemos una nested function. Esta nested function referencia a un valor de un scope superior.Y esta nested fuction es retornada.

Las funciones times son ahora la función multiplayer con los correspondientes números asignados, pero estas solo conocen x y no n. 

al realizar un times10(3) le estamos dando un valor de n, dado que esta recuerda el valor de x asignado que fue 15.  La función times4 realiza lo mismo, e incluso se pueden combinar. Así funcionan los Closures.

## ¿Dónde aparecen los Closures?

Cuando se tiene una clase corta, con un sólo método, se aplica closures para que sea más elegante.

El siguiente es cuando trabajamos con decoradores. 

## Ejemplos de Closures

```python
#Ejemplo de Closure

#Debe existir una nested function
#Debe tomar valores de un scope superior
#La función nested debe ser retornada
def make_repeter_of(n):
    def repeater(string):
        assert type(string) == str, "Solo puedes utilizar cadenas"
        return string * n
    return repeater

def run():
    #Esta función recordará el valor de 5
    repeat_5 = make_repeter_of(5)
    repeat_10 = make_repeter_of(10)
    print(repeat_5("Hola"))
    print(repeat_10('Platzi'))
    
if __name__ == '__main__':
    run()
```

```python
#Reto

def make_division_by(n):
    #Este Closure regresa una función que returna la 
    #división de x por un número n
    def divisor(x):
        return x/n
    return divisor

division_by_3 = make_division_by(3)
print(division_by_3(18))

division_by_5 = make_division_by(5)
print(division_by_5(100))

division_by_18 = make_division_by(18)
print(division_by_18(54))
```

# Decoradores

Un decorador es un closure. Es una función que recibe como parámetros otra función, le añade cosas y la ejecuta y retorna una función diferente.

```python
def decorador(func):
	def envoltura():
		print('Esto se añade a mi función original')
	return envoltura

def saludo():
	print('Hola')

saludo()
#Output[]
#Hola

saludo = decorador(saludo)
saludo()
#Output[]
#Esto se añade a mi función original
#Hola
```

El decorador toma un función como parámetro y toma una función envoltura que imprime un mensaje. Ejecuta la función y retorna una función diferente.

La función saludo, imprime “hola”

Cuando se asigna saludo = decorador(saludo)

y se imprime saludo(), se añade a nuestra función hola la envoltura y lo muestra en pantalla y lo decora.

Este mismo patrón ocurre con todos los decoradores.

Azucar sintáctica es cuando tenemos un código que está embellecido para que sea más bonito. El sugar sintact de los decoradores, es utilizar un @ antes de la función.

```python
def decorador(func):
	def envoltura():
		print('Esto se añade a mi función original')
	return envoltura

@decorador
def saludo():
	print('hola!')

saludo()
```

Por lo tanto al ejecutar saludo, se ejecuta primero la envoltura y de último saludo. 

Un decorador también es un closure y sirve exclusivametne para agregar cosas a una función.

```python
def mayusculas(func):
	def envoltura(texto):
		return func(texto).upper()
	return envoltura

@mayusculas
def mensaje(nombre):
	return f'{nombre}, recibe un mensaje'

print(mensaje('Cesar'))
```

![Untitled](Python%20profesional%20af58b7d07f6d4fe8b6c905504f747d10/Untitled%2010.png)

**Ejemplo**

```python
#Decorators
#Modulo datetime
from datetime import datetime

#Para que se puedan utilizar todo tipo de datos
#se utiliza args y kwargs, asi pueden usarse en
#funciones como suma
def execution_time(func):
    def wrapper(*args, **kwargs):
        initial_time = datetime.now()
        func(*args, **kwargs)
        final_time = datetime.now()
        time_elapsed = final_time - initial_time
        print('Pasaron', time_elapsed.total_seconds(), "segundos")
    return wrapper

@execution_time
def random_func():
    #Se coloca un guió bajo porque no interesa las variables
    #De cada una de las vueltas.
    for _ in range(1,100000000):
        pass

#random_func()

@execution_time
def suma(a: int, b: int) -> int:
    return a + b

#suma(5,5)

#El tipo de parámetros que tiene nombre tienen un tipo
#de arguments y son llamados tipo kwargs. Con el doble
#Asteriscos decimos que no importa la cantidad de de tipos 
#Kwargs, que se ejecute igual
@execution_time
def saludo(nombre = 'Cesar'):
    print("hola" + nombre)

random_func()
suma(5,5)
saludo('Jefferson')
```

# Iteradores

Una estructura de datos para guardar datos infinitos.

Un iterable es todo aquellos objetos que podemos recorrer en un ciclo. Las listas son iterables, las cadenas de carácteres, entre otros. 

Cuando hacemos un ciclo, no funciona como creemos. El iterable se transforma en un iterador y es ese el que puede recorrerse entre el lenguaje.

```python
#Creando un iterador
my_list = [1, 2, 3, 4, 5]
my_iter = iter(my_list)

#Iterando un iterador
print(next(my_iter))

#Cuando no quedan datos, la excepción Stopiteration es elevada
```

Lo que hace el lenguaje es lo que se muestra en la segunda línea. Construye la lista en un iterador, es decir, todos los iterables pueden ser convertidos en iterador para ser recorridos. Cuando tengo el elemento iterador, puedo acceder a cada uno de los elementos del iterable que partío. Esto utilizando la función building next. Cuando no quede ningún elemento lanzará un error StopIteration. 

```python
#Creando un iterador
my_list = [1, 2, 3, 4, 5]
my_iter = iter(my_list)

#Iterando un iterador
while True:
	try:
		element = next(my_iter)
		print(element)
	except StopIteration
		break
```

Cuando decimos While True se repetirá indefinidamente. Dentro del ciclo tenemos las clausulas try y except para manejo de errores. Sacamos el siguiente elemento de nuestro iterador y se imprime. Si algún momento existe el error StopIterator, cerrarmos el ciclo while. Esto se puede realizar con todos los iteradores. 

```python
my_list = [1, 2, 3, 4, 5]
for element in my_list:
	print(element)
```

Y luego tenemos el ciclo for. Un ciclo for es sugar sintatic del ciclo while mostrado anteriormente. El ciclo for es un alias de todo el código mostrado anteriormente.

## ¿Cómo construyo un iterador?

Utilizando clases y métodos. También es necesario conocer el protocolo de iteradores. Es necesario implementar el método __iter__ y el método __next__. 

```python
#Iteradores

class EvenNumbers:
    """ Clase que implementa un iterador de todos los números
        pares, o los números pares hasta un máximo """
    def __init__(self, max = None):
        self.max = max
        
    def __iter__(self):
        self.nums = 0
        return self
    
    def __next__(self):
        if not self.max or self.num <= self.max:
            result = self.num
            self.num += 2
            return result
        else:
            raise StopIteration
```

EvenNumbers números pares hasta un máximo. Se tiene el constructor, como primer parámetro self que hace referencia al objeto seguro y un parametro max inicializado en None. Aquí al atributo mas será igual al atributo max que está llegando en el constructor. 

Luego tiene los dos métodos necesarios para construir un iterador.  El método __iter__ convierte un iterable en un iterador. 

El método __next__ permite extraer cada uno de los elementos del iterador. Se utiliza el condicional que pregunta si no se paso de número máximo o el número que estoy recorriendo es  menor o igual al número max, se le asigna el objeto num a result. self.num toma los valores pares donde va contando de 2 en dos con +=2 y se regresa result.

Si se paso el número max, entonces se muestra StopIteration.

Las ventajas de trabajar con iteradores ahorra recursos. Se puede almacenar secuencias matemáticas teoricamente completas. Los iteradores ocupan poca memoria. Trabajamos más rápido y ocupamos menos memoria.

# La sucesión de Fibonacci

Un ejemplo para entender las iteraciones.

$$
f_0=0\\f_1=1\\f_n=f_{n-1}+f_{n-2}
$$

Teniendo el número aureo:

$$
\varphi=\frac{1+\sqrt{5}}{2}
$$

Es posible reescribir la ecuación como

$$
f_n=\frac{\varphi^n-(-\varphi^{-1})^n}{\sqrt{5}}
$$

Esto es posible escribirlo en Python y almacenarlo en nuestra memoria. 

> Instanciar:  es el acto de convertir a través de los planos de una clase, un objeto.
> 

```python
#Iterators (Fibonacci)

import time

class FiboIter():
    
    #def __init__():
    
    def __iter__(self):
        self.n1 = 0
        self.n2 = 1
        self.counter = 0
        return self
    
    def __next__(self):
        #Condiciones iniciales
        if self.counter == 0:
            self.counter += 1
            return self.n1
        elif self.counter == 1:
            self.counter += 1
            return self.n2
        else:
            #Se hace un swap, la ocupación de n1 pasa a ser 
            #La ocupación de n2 y la de n2 pasa a ser la de aux
            self.aux = self.n1 + self.n2
            #self.n1 = self.n2
            #self.n2 = self.aux
            self.n1, self.n2 = self.n2, self.aux
            self.counter += 1
            return self.aux

if __name__ == '__main__':
    fibonacci = FiboIter()
    for element in fibonacci:
        print(element)
        #Se pausa después de 1 segundo
        time.sleep(1)
```

# Generadores

 “Sugar syntax” de los iteradores. Son básicamente funciones que guardan un estado. Es un iterador escrito de manera más simple. 

```python
def my_gend():
    """ Un ejemplo de generadores"""
    
    print('Hello world!')
    n=0
    yield n
    
    print('Hello Heaven!')
    n=1
    yield n
    
    print('Hello Hell!')
    n=2
    yield n
    
a = my_gend()
print(next(a)) #Hello world
print(next(a)) #Hello heaven
print(next(a)) #Hello hell
print(next(a)) #StopIteration
```

Los generadores son funciones y los iteradores son clases.  La función my_gend muestra en pantalla un mensaje y crea una variable en el scope local llamada n y hace un yield. Yield es exactamente lo mismo que return, con la diferencia de terminar a la función, yield pausa a la función. Si después vuelvo a llamar a la función, no empieza desde el principio sino desde donde lo dejó ese yield. Por eso se dice que los generadores guardan estados.

Como un generador es sugar syntax de un iterador, también debemos instanciarlo. Esto con a = my_gend() con el método next es que en lugar de trabajar como un iterador y traer el siguiente elemento, la función next te llevará al yield más proximo.

Cuando no hay más yields se muestra un ejemplo Stop Iteration. Como un iterador.

```python
#Iterator expression

my_list = [0, 1, 4, 7, 9, 10]

my_second_list = [x*2 for x in my_list] #Generator comprehensions
my_second_gen = (x*2 for x in my_list)  #Generator expression
```

Un list comprehensions almacena todos los elementos en memoria. Si se necesita tener una base de datos enormes, no se puede trabajar con list comprehensions. Para esto se ocupa generator expressions.El generator expressions trae un elemento a la vez cuando lo recorras. Si luego con un ciclo for te vas por cada uno de los elementos creados con el generator expressions, es ir sacando 1 por 1 los elementos. 

Las ventajas de usar generadores, es la misma que tiene usar iteradores. Ahorra tiempo y memoria y se puede guardar secuencias infinitas.

Python internamente utiliza operaciones con generadores para aumentar el rendimiento.Tal es el caso de máx , min o sum.Ejemplo:

```
suma = sum([i for i in range(100)]) # Crea la lista en memoria.
suma_gen = sum(i for i in range(100)) #Itera sobre los valores.

```

El el primer caso, creamos una lista que no nos servirá y se termina guardando el espacio en memoria, en el segundo caso se itera cada valor hasta obtener el resultado sin la necesidad de guardar en memoria cada valor.

## Mejorando la sucesión de Fibonacci utilizando generadores

```python
#Generators 
# Suseción de Fibonacci utilizando generadores

import time

#sin utilizar clases.
def fibo_gen():
    n1 = 0
    n2 = 1
    counter = 0
    while True:
        if counter == 0:
            counter += 1
            yield n1
        elif counter == 1:
            counter += 1
            yield n2
        else:
            aux = n1 + n2
            n1, n2 = n2, aux
            counter += 1
            yield aux
    
if __name__ == '__main__':
    fibonacci = fibo_gen()
    for element in fibonacci:
        print(element)
        time.sleep(1)
```

> Recordemos que yield es un retorn, pero que toma la función en donde se dejó.
> 

# Sets en Python

Un set es una colección desordenada de elementos únicos e inmutables.

```python
my_set = {3,4,5}
print("my_set=", my_set)

my_set2 = {"hola", 23.3, False, True}
print("my_set2=", my_set2)

my_set3 = {3, 3, 2}
print("my_set3=", my_set3)

my_set4 = {[1,2,3], 4}
print("my_set4=", my_set4) 
```

Los sets se escriben entre llaves, como los diccionarios, con la diferencia que no se utiliza los dos puntos para las llaves. Python si colomos un valor repetido como en my_set3 quita el 3. En my_set 4 no permitirá utilizar la lista porque esta es mutable.  Para crear un set vacío.

```python
empty_set = {}
print(type(empty_set)) #«class 'dict»
empty_set = set()
print(type(empty_set)) #«class 'set'»
```

## Casting con sets (convertir un set a otra estructura de datos)

```python
my_set = {1,2,3}
print(my_set)
#output {1,2,3}

#Añadir un elemento
my_set.add(4)
print(my_set)
#output {1,2,3,4}

#Añadir múltiples elementos
my_set.update([1,2,5])
print(my_set)
#output {1,2,3,4,5}

#Añadir múltiples elementos
my_set.update((1,7,2), {6,8})
print(my_set)
#output {1,2,3,4,5,6,7,8}
```

**Añadir elementos a un set**

Python añade los elementos a un set, pero aquellos que ya se encuentren dentro de set no los repite. Puede ingresarse una lista, una tupla u otro set, pero valores repetidos no serán incluídos.

```python
my_set = {1,2,3,4,5,6,7}
print(my_set)
#{1,2,3,4,5,6,7}

#Borrar un elemento existente
my_set.discard(1)
print(my_set)
#{2,3,4,5,6,7}

#Borrar un elemento existente
my_set.remove(2)
print(my_set)
#{3,4,5,6,7}

#borrar un elemento inexistente 
my_set.discard(10)
print(my_set)
#{3,4,5,6,7}

#Borrar un elemento inexistente
my_set.remove(12)
print(my_set)
#KeyError: 12
```

**Quitar elementos de un set**

Para quitar elementos de un set se tienen dos métodos: discard y remove.

Se tiene en este código un set con números del 1 al 7, si se quiere eliminar un número se quita con discard o remove. Ambos cumplen con su funcionalidad, pero existe una diferencia y es cuando se quiere borrar un número inexistente discard si corre y no modifica nada, mientras que con remove lanza un key error.

```python
my_set = {1,2,3,4,5,6,7}
print(my_set)
#{1,2,3,4,5,6,7}

#borrar un elemento aleatorio
my_set.pop()
print(my_set)

#limpiar el set completo
my_set.clear()
print(my_set)
```

# Operaciones con sets

## Unión de dos conjuntos

La unión de dos conjuntos es el resultado de combinar los elementos de todos los conjuntos. Si hay un elemento que se repite, no se agrega dos veces, solo uno. 

```python
my_set = {3,4,5}
my_set = {5,6,7}

my_set3 = my_set1 | my_set2
print(my_set3)
#Output
#{3,4,5,6,7}
```

Se utiliza el operador pipe para unir los set y puede ser guardado en una nueva variable. Esto es la unión

## Intersección de dos conjuntos

La intersección entre conjuntos es unirlos pero quedarse unicamente con los elementos que tienen en común

```python
my_set = {3,4,5}
my_set = {5,6,7}

my_set = my_set & my_set2
print(my_set3)
#Output
#{5}
```

Toma el elemento común entre dos conjuntos y la intersección se hace por medio del signo &.

## Diferencia de dos conjuntos

Se toma dos sets y de uno quitar todos los elementos que tiene el otro.

```python
my_set = {3,4,5}
my_set = {5,6,7}

my_set3 = my_set1 - my_set2
print(my_set3)
#Output {3,4}

my_set4 = my_set2 - my_set1
print(my_set4)
#Output {6,7}
```

La operación se hace con el símbolo “-”.  Y quita todos los elementos que se encuentran en la intersección. 

## Diferencia simétrica de dos conjuntos

La diferencia simétrica es lo contrario de la intersección. Es el resultado de quedarme con ambos sets, pero sin lo que se comparten

```python
my_set1 = {3,4,5}
my_set2 = {5,6,7}

my_set3 = my_set1 ^ my_set2
print(my_set3)
#Output
#{3,4,6,7}
```

Obtenemos solamente los valores que no están en la intersección.

Se utiliza el operador hat ^. 

# Eliminando los repetidos de una lista

Con ciclos for

con sets

```python
#Sets
#Programa que elimine los duplicados de una lista

def remove_duplicates(some_list):
    without_duplicates = []
    for element in some_list:
        if element not in without_duplicates:
            without_duplicates.append(element)
    return without_duplicates
    
def run():
    random_list = [1,1,2,2,4]
    print(remove_duplicates(random_list))
    
if __name__ == '__main__':
    run()
```

```python
def remove_duplicates(some_list):
    return list(set(some_list))

def run():
    random_list = [1,1,2,2,4]
    print(remove_duplicates(random_list))
    
if __name__ == '__main__':
    run()
```

# Manejo de fechas

Para manejar fechas se utiliza el módulo datetime el cual viene por defecto en Python.

```python
import datetime

my_time = datetime.datetime.now()

print(my_time)

#Output[] 
#2022-07-25 19:21:59.136902

```

Este módulo datetime tiene una clase dentro del módulo, por eso se necesita lamar al módulo y con un punto acceder a la clase que tiene dentro y tiene el mismo nombre y con un punto acceder al método now().

Llamando al método now que se encuentra dentro de la clase datetime que se encuentra en el módulo datetime.

Esto me trae la hora universal UTC, me trae la fecha y hora actual de mi computadora, pero si no tengo configurado nada, me trae la hora universal.

```python
import datetime

my_day = datetime.date.today()
print(my_time)

#Output[] 
#2022-07-25

```

Para ver la fecha se utiliza el método today()

También podemos acceder a cierta información 

```python
import datetime
my_day = datetime.date.today()
print(f'Year: {my_day.year}')
print(f'Month: {my_day.month}')
print(f'Day: {my_day.day}')
```

## Formateo de fechas

Esto ocurre cuando se tienen las fechas en formato mm/dd/yyyy en algunos países y dd/mm/yyyy en otros. Si queremos la fecha en alguno de estos formatos, es necesario usar la tabla de formato

![Untitled](Python%20profesional%20af58b7d07f6d4fe8b6c905504f747d10/Untitled%2011.png)

```python
from datetime import datetime

my_datetime = datetime.now()
print(my_datetime)

my_str = my_datetime.strftime('%d/%m/%Y')
print(f'Formato LATAM: {my_str}')

my_str = my_datetime.strftime('%m/%d/%Y')
print(f'Fortamo USA: {my_str} ')

my_str = my_datetime.strftime('Estamos en el año %Y')
print(f'Formato random: {my_str}')
```

```python
2022-07-25 22:26:14.267790
Formato LATAM: 25/07/2022
Fortamo USA: 07/25/2022 
Formato random: Estamos en el año 2022
```

Es importante evitar usar datetime.now() porque toma la hora local. Mejor usar datetime.utcnow() para usar la hora universal. Nosotros trabajamos con equipos de todo el mundo, no podemos usar hora local

# Times zones

El módulo que nos ayuda a trabajar con zonas horarias se utiliza el módulo pytz y se debe instalar con pip. 

```python
from datetime import datetime
import pytz

guatemala_timezone = pytz.timezone("America/Guatemala")
guatemala_date = datetime.now(guatemala_timezone)
print("Guatemala: ", guatemala_date.strftime("%d/%m/%Y, %H:%M:%S"))
```

```python
Guatemala:  25/07/2022, 22:54:41
```