Resumen de The Quick Python Book, de Manning.

# 1. About Python

# 2. Getting started

# 3. The Quick Python overview

## Built-in data types

### Numbers

Los cuatro tipos de datos numéricos son: integers, floats, complex numbers y Booleans.

Tenemos la librería `math` para operar con números:

```python
import math
math.ceil(3.49)
```

Y `cmath` para operar con números complejos (3 + 2j, por ejemplo).

### Lists

```python
[1, "two", 3, 4.0, ["a", "b"]]
```

Una lista puede contener una mezcla de tipos como elementos.

```python
x = ["first", "second", "third", "fourth"]

x[0] #'first'
x[-1] #'fourth'
x[1:-1] #['second', 'third']
x[:3] #['first', 'second', 'third']
```

Existen funciones (`len`, `max` y `min`), operadores (`in`, + y *), `del`, y los métodos de lista (`append`, `count`, `extend`, `index`, `insert`, `pop`, `remove`, `reverse` y `sort`).

Los operadores + y * crean una nueva lista, dejando la original como estaba.

### Tuples

Son similares a las listas, pero son inmutables. Es decir, no pueden ser modificadas una vez creadas.

```python
()
(1,)
(1, "two", 3L, 4.0, ["a", "b"])
```

Tiene los métodos `count` e `index`.

Se puede convertir una lista en una tupla con `tuple`:

```python
x = [1, 2, 3, 4]
tuple(x)
```

Y al revés con `list`:

```python
x = (1, 2, 3, 4)
list(x)
```

### Strings

El módulo `re` provee funcionalidad sobre expresiones regulares.

```python
x = "live and enjoy life"
import re
regexpr = re.compile(r"[\t ]+")
regexpr.sub(" ", x)

```

### Dictionaries

La función `len` devuelve el número de pares clave-valor del diccionario.
La función `del` elimina un par.
Como métodos tenemos `clear`, `copy`, `get`, `items`, `keys`, `update` y `values`.

```python
x = {1: "one", 2: "two"}
x["first"] = "one"
x[("Delorme", "Ryan", 1995)] = (1, 2, 3)
list(x.keys()) # ["first", 2, 1, ("Delorme", "Ryan", 1995)]
```

### Sets

Un set es una colección desordenada de objetos.

```python
x = set([1, 2, 3, 1, 3, 5])
x # {1, 2, 3, 5} Ha eliminado duplicados
1 in x # True
```

### File objects
El acceso a ficheros se realiza mediante un objeto file de Python.

```python
f = open("myfile", "w")
f.write("First line with necessary newline character\n")
f.write("Second line to write to the file\n")
f.close()
```
## Control flow structures

### Boolean values and expressions

Valores *falsy*: False, 0, None, [], "".
Valores *truthy*: True, resto de valores.

Operadores de comparación: <, <=, ==, >, >=, !=, is, is not, in, not in.
Operadores lógicos: and, not, or.

### if-else

```python
x = 5
if x < 5:
  y = -1
  z = 5
elif x > 5:
  y = 1
  z = 11
else:
  y = 0
  z = 10
print(x, y, z)
```

### while

```python
u, v, x, y = 0, 0, 100, 30
while x > y:
  u = u + y
  x = x - y
  if x < y + 2
    v = v + x
    x = 0
  else:
    v = v + y + 2
    x = x - y - 2
print(u, v)
```

El bucle puede contener un `break` (que termina el loop) o un `continue` (que aborta la ejecución de la iteración actual del loop).

### for

Mediante un bucle for se puede iterar por cualquier tipo iterable, como una lista o una tupla. Se iterará por cada uno de los elementos en la secuencia, como un foreach.

```python
...
for x in item_list:
...
```

### Function definition

```python
def funct1(x, y, z):
  value = x + 2*y + z ** 2
  return value

um v = 3, 4
funct1(u, z=v, y=2) # Llamada con parámetros en diferente orden

# Función con parámetros por defecto
def funct2(x, y=1, z=1):
  return x + 2 * y + z ** 2

funct2(3, z=4)

# Función con parámetro especial que recolecta todos los argumentos extra en una tupla
def funct3(x, y=1, z=1, *tup):
  print((x,y,z) + tup)

funct3(1, 2, 3, 4, 5, 6, 7, 8, 9) # Me devuelve (1, 2, 3, 4, 5, 6, 7, 8, 9)

# Función con parámetro especial que recolecta los parámetros extra en un diccionario
def funct4(x, y=1, z=1, **kwargs):
  print(x, y, z, kwargs)

funct4(1, 2, m=5, n=9, z=3) # Me devuelve 1 2 3 {'n': 9, 'm': 5}
```

### Exceptions
Las excepciones se pueden capturar mediante la sentencia `try-except-else-finally`. Cualquier excepción que no sea capturada, supondrá el fin de la ejecución del programa.

```python
filenames = ["myfile1", "nonExistent"]
for file in filenames:
  try:
    f = open(file, 'r')
    line = f.readline()
    if line == "":
      f.close()
      raise EmptyFileError("%s: is empty" % file)
  except IOError as error:
    print("%s: could not be opened: %s" % (file, error.strerror))
  except EmptyFileError as error:
    print (error)
  else:
    print("%s: %s" % (file, f.readline()))
  finally:
    print("Done processing", file)
```
El `else` es opcional, solo se ejecuta si no se da ninguna excepción.

### Context handling using the with keyword

Otra forma de encapsular a estructura `try-except-finally` es mediante el uso de `with` y un context manager.

Python define los context managers para cosas como el acceso a ficheros.

Se pueden definir context managers propios, creados manualmente.

Una ventaja de los context managers es que tienen definidas acciones de *cleanup*, que se ejecutan siempre, se lance excepción o no.

```python
filename = "myfile.txt"
with open(filename, "r") as f:
  for line in f:
    print(f)
```
`with` establece un context manager que envuelve la función `open` y el siguiente bloque. En este caso, la acción de *cleanup* predefinida es cerrar el fichero, aunque ocurra una excepción.

## Module creation (COMPLETAR)

## Object-oriented programming (COMPLETAR)

# 4. The absolute basics

## Variables and assignments

En Python no hay que tipar las variables. Las variables (en Python) no son buckets o almacenes. Son más bien un tag o label que se refiere a un objeto del espacio de nombres del intérprete de Python. Varias labels (o variables) pueden apuntar al mismo objeto, y cuando cambia el objeto, el valor al que apuntan todas esas variables también cambia.

Por ejemplo:

```python
a = [1, 2, 3]
b = a
c = b
b[1] = 5
print(a, b, c) # Me muestra [1, 5, 3] [1, 5, 3] [1, 5, 3]
```

Si las variables apuntan a constantes o valores inmutables, esta distinción no está tan clara:

```python
a = 1
b = a
c = b
b = 5
print(a, b, c) # Muestra 1 5 1
```
Esto ocurre porque los objetos a los que apuntan no pueden cambiar (son inmutables). En el punto en el que b = 5, b pasa a apuntar a 5, pero las otras dos variables no.

- `del`: elimina la variable.
```python
x = 5
del x
```

## Strings

Los *backslashes* se pueden usar para escapar caracteres. `\n` significa el carácter de nueva línea, `\t` es un tab, etc.

Si un string lo delimitamos con triple comilla (simple o doble), nos permite escribir el string en varias líneas.

## Numbers

Python ofrece cuatro tipos de números: integers, floats, complex numbers y Booleans. Un integer solo está restringido por los recursos de la máquina

### Built-in numeric functions
Python provee en su core de las siguientes funciones para operar con números: `abs`, `divmod`, `float`, `hex`, `int`, `max`, `min`, `oct`, `pow`, `round`.

Para operaciones más avanzadas está disponible el módulo `math`.

El core de Python no está pensado para operaciones numéricas intensivas por las limitaciones de velocidad. Pero mediante la extensión `NumPy` podemos hacer uso de numerosas implementaciones de operaciones avanzadas, como operaciones con arrays, matrices multidimensionales o transformadas de Fourier.

## The None value
`None` se utiliza para representar el valor vacío. Se suele utilizar como *placeholder* para indicar un punto en una estructura de datos donde en determinado momento existirán datos.

## Getting input from the user
Se usa `input()`.

```python
name = input("Name? :")
```

# 5. Lists, tuples and sets

## Lists are like arrays
Una lista de Python es como un array en Java o C: es una colección ordenada de objetos. La lista se define mediante corchetes:

```python
x = [1, 2, 3]
```
Al contrario que en otros lenguajes, las listas en Python pueden contener diferentes tipos de elementos. Un elemento de una lista puede ser cualquier objeto de Python.

```python
x = [2, "two", [1, 2, 3]]
```

## List indices
En Python, el primer índice es el 0.
Si un índice es negativo, indica una posición contando desde el final de la lista, siendo el -1 la última posición de la lista, el -2 la penúltima, y así sucesivamente.

- `list[index1:index2]`: extrae todos los elementos incluyendo el index1 hasta el index2 (sin incluir), y los devuelve como una nueva lista.

```python
x = ["first", "second", "third", "fourth"]
x[1:-1] # Me devuelve ["second", "third"]
x[-2:-1] # Me devuelve ["third"]
x[-1:2] # Ojo, me devuelve una lista vacía []
x[:] # Me devuelve UNA COPIA de la lista ["first", "second", "third", "fourth"]
```
El último ejemplo se utiliza para obtener una copia de una lista.

## Modifying lists

```python
x = [1, 2, 3, 4]
x[1] = "two"
x # [1, 'two', 3, 4]
```
También se puede usar la siguiente notación:

```python
lista[index1:index2] = listb
```
Esto causa el reemplazo de ese rango por el contenido de `listb`, la cual puede tener más o menos elementos que los que se han eliminado.

Con esto se puede hacer cosas como por ejemplo:

```python
x = [1, 2, 3, 4]
x[len(x):] = [5, 6, 7]
x # [1, 2, 3, 4, 5, 6, 7]
```
Para añadir un solo elemento en la lista, se puede usar el operador `append`. Si intentamos hacer un `append` de una lista, esta se añade como un único elemento más. Paraañadir los elementos de una lista a otra, hay que usar el método `extend`.

Otro método es `insert`, que sirve para insertar nuevos elementos entre los elementos de una lista, o al inicio, o al final.

```python
x = [1, 2, 3]
x.insert(2, "hello")
x # [1, 2, 'hello', 3]

x.insert(0, "start")
x # ['start', 1, 2, 'hello', 3]
```

Para eliminar elementos de una lista tenemos el operador `del`.

```python
x = ['a', 2, 'c', 7, 9, 11]
del x[1]
x # ['a', 'c', 7, 9, 11]
```
El método `remove` no es el inverso de `insert`. `remove` busca la primera ocurrencia de un valor en la lista y lo elimina de la lista.

```python
x = [1, 2, 3, 4, 3, 5]
x.remove(3)
x # [1, 2, 4, 3, 5]
```
Si `remove` no puede encontrar el valor, lanza un error.

## Sorting lists

Las listas se pueden ordenar usando el método `sort`.

Pero ojo, el método `sort` modifica la lista original. Para ordenar una lista sin modificar la lista original, se puede:
* Usar la función `sorted()`.
* Hacer una copia de la lista y ordenar la copia.

```python
x = [2, 4, 1, 3]
y = x[:]
y.sort()
```
Si se intenta aplicar un `sort` a una lista con números y strings, lanzará una excepción.

### Custom sorting

Para ello, hay que escribir una función que devuelva un valor o clave sobre la que ordenar.

Por ejemplo:

```python
def compare_num_of_chars(string1):
  return len(string1)

...

words_list.sort(key=compare_num_of_chars)
```

### The sorted() function

Las listas tienen el método `sort` pero otros iterables en Python, como las claves de un diccionario, no lo tienen. Python tiene también la función `sorted()`, que devuelve una lista ordenada a partir de un iterable:

```python
x = (4, 3, 1, 2)
y = sorted(x) # [1, 2, 3, 4]
```

## Other common list operations

### List membership with the in operator

```python
3 in [1, 3, 4, 4]  # True
3 not in [1, 3, 4, 5] # False
```

### List concatenation with the + operator

Para crear una lista concatenando dos listas existentes:

```python
z = [1, 2, 3] + [4, 5]
```

### List initialization with the * operator

El operador * sirve para producir una lista de un determinado tamaño, que se inicializa a un determinado valor dado. Este operador se utiliza bastante para trabajar con listas grandes, cuyo tamaño se conoce previamente.

Aunque se puede usar el método `append`, se tiene mayor eficiencia con *.

```python
z = [None] * 4 # [None, None, None, None]
```

### List minimum or maximum with min and max

Se puede usar `min` y `max` para buscar el menor y mayor elemento de la lista.

```python
min([3, 7 ,0 ,-2, 11]) # -2
```

### List search with index

Si queremos saber dónde se encuentra un elemento en una lista, usamos `index`.

```python
x = [1, 3, "five", 7, -2]
x.index(7) # 3
```

Si se intenta buscar un elemento que no está en la lista dará error.

### List matches with count

`count` también busca un valor en una lista, pero devuele el número de veces que el valor aparece en la lista.

```python
x = [1, 2, 2, 3, 5, 2, 5]
x.count(2) # 3
```

## Nested lists and deep copies

Las listas se pueden anidar:

```python
m = [[0, 1, 2], [10, 11, 12]]
```
Las listas anidadas pueden dar problemas. Por ejemplo:

```python
nested = [0]
original = [nested, 1]
```

Con esta situación, el valor de la lista anidada puede cambiarse desde ambos puntos:

```python
nested[0] = 'zero'
original # [['zero'], 1]
original[0][0] = 0
nested # [0]
```

Pero si damos a `nested` como valor otra lista, la conexión se rompe:

```python
nested = [2]
original = [[0], 1]
```

Hemos visto que se puede obtener una copia de una lista haciendo `x[:]`. También usando el operador + ( x + []) o * (x * 1).
Todas estas crean una *shallow copy* de la lista, que es lo uqe necesitaremos la mayoría de las veces.

Pero si la lista tiene otras listas anidadas, lo que necesitamos es una *deep copy*.

Esto lo podemos hacer con la función `deep-copy` del módulo `copy`.

```python
original = [[0], 1]
shallow = original[:]

import copy
deep = copy.deepcopy(original)
```

Las diferencias entre las copias *shallow* y *deep* son que las listas a las que apuntan el objeto original y *shallow* son la misma. Si cambiamos el valor en la lista anidada en alguno de ellos, en la otra cambia también.

```python
shallow[1] = 2
shallow # [[0], 2]
original # [[0], 1]

shallow[0][0] = 'zero'
original # [['zero'], 1]
```

Sin embargo, la copia *deep* es independiente de la original:

```python
deep[0][0] = 5
original # [['zero'], 1]
```

## Tuples

Las tuplas son estructuras parecidas a las listas, pero no se pueden modificar, solo se pueden crear. La razón de la existencia de las tuplas es que cumplen roles donde las listas no son tan eficientes, como claves de diccionarios.

Para crear una tupla:

```python
x = ('a', 'b', 'c')
```

La principal diferencia entre listas y tuplas es que las tuplas son inmutables.

Eso sí, se pueden crear tuplas a partir de tuplas existentes usando los operadores + y *:

```python
x + x
2 * x
```

Y la copia de una tupla se puede realizar de la misma forma que una lista:

```python
x[:]
x * 1
x + ()
```

### One-element tuples need a comma

```python
x = 3
y = 4
(x + y) # 7
(x + y,) # Tupla (7,)
```

### Packing and unpacking tuples

Python permite poner tuplas en la parte izquierda de una asignación:

```python
(one, two, three) = (1, 2, 3)
one # 1
```

También se pueden escribir sin paréntesis:

```python
one, two, three = 1, 2, 3
```

En Python 3, se permite que un elemento marcado con * reciba todos los elementos que no casen en una asignación:

```python
x = (1, 2, 3, 4)
a, b, c* = x
c # [3, 4]
a, b*, c = x
b # [2, 3]
```

### Converting between lists and tuples

Las tuplas se pueden convertir en listas con la función `list`. Y al revés con `tuple`.

```python
list((1, 2, 3, 4)) # [1, 2, 3, 4]
tuple([1, 2, 3, 4]) # (1, 2, 3, 4)
```

Nota, `list` se utiliza también para partir una string en sus caracteres:

```python
list("Hello") # ['H', 'e', 'l', 'l', 'o']
```

## Sets

Un set en Python es una colección de objetos que se usa cuando lo que importar es la pertenencia y la unicidad del objeto en la colección. 

Los elementos de un set deben ser inmutables y hasheables. Esto quiere decir que ints, floats, strings y tuplas pueden ser miembros de un set, pero listas, diccionarios y sets no.

### Set operations

Crear un set:

```python
x = set([1, 2, 3, 1, 3, 5]) # {1, 2, 3, 5}
```

```python
x.add(6)
x.remove(5)
1 in x
```

Unión de sets:

```python
y = set({1, 7, 8, 9})
x | y # {1, 2, 3, 6, 7, 8, 9}
```

Intersección:

```python
x & y # {1}
```

Elementos que estén en un set o en el otro, pero no en ambos:

```python
x ^ y # {2, 3, 6, 7, 8, 9}
```

### Frozensets

Como los sets no son inmutables ni hasheables, no pueden pertenecer a otros sets. Para remediar esto, Python tiene el `frozenset`, que es un set que no puede ser modificado una vez creado. Estos sí pueden ser miembros de otros sets:

```python
x = set({1, 7, 8, 9})
z = frozenset(x)
x.add(z)
```

# 6. Strings

## Strings as sequences of characters

Un string puede ser considerado como una secuencia de caracteres, por lo que podemos hacer selección por índice:

```python
x = "Hello"
x[0] # 'H'
x[-1] # 'o'
```

La mayor diferencia entre un string y una lista es que un string no es modificable. Hacer algo como `string[0]='a'` da error.

## Basic string operations

### Numeric (octal and hexadecimal) and Unicode escape sequences

Se puede añadir cualquier caracter ASCII en un string añadiendo una secuencia de escape en octal o hexadecimal.

Una secuencia de escape en octal es un `\` seguido de tres dígitos definiendo el número en octal. El caracter en ASCII correspondiente sustituirá a este octal.

Una secuenca de escape en hexadecimal es un `\x` seguido de los caracteres en hexadecimal.

```python
'\155' # 'm'
'\x6D' # 'm'
```

### Printing vs. evaluating strings

La función `print` pasa el string a la terminal, la cual puede interpretar los caracteres especiales de forma especial.

```python
print('a\n\tb')
# a
#   b
```

## String methods

### Converting strings to numbers

Las funciones `int` y `float` nos permiten convertir strings en integers o floats.

```python
float('123.456') # 123.456
int('ff', 16) # 255
```

### Getting rid of extra whitespace

`strip`, `lstrip`, `rstrip`.

```python
x = " Hello,  World\t\t"
x.strip() # "Hello,  World"
```
En este caso ha tomado el tab `\t` como espacio. Esto difiere según el sistema operativo. Para saber en nuestro sistema qué considera Python como espacio en blanco:

```python
import string
string.whitespace # '\t\n\r\x0b\xoc'
```

Y también le podemos pasar por parámetro a estos métodos qué queremos considerar como espacios.

### String searching

`find`, `rfind`, `index`, `rindex`, `count`.

`find` necesita un argumento: el substring por el que se busca. Devuelve la posición del primer caracter del substring en el string, o -1 si no encuentra ocurrencia.

```python
x = "Mississippi"
x.find("ss") # 2
x.find("ss", 0, 3) # -1
```

`rfind` hace lo mismo pero empezando por la derecha. Devuelve la última occurencia.

```python
x = "Mississippi"
x.rfind("ss") # 5
```

`index` y `rindex` son lo mismo, solo que, en caso de no ocurrencia, lanzan un error `ValueError`, en vez de devolver -1.

`count` devuelve el número de ocurrencias de un substring en un string.

Para búsquedas más complejas, está el módulo `re`, que permite hacer búsquedas por expresiones regulares.

### Modifying strings

`replace`:

```python
x = "Mississippi"
x.replace("ss","+++") # Mi+++i+++ippi
```

El módulo `re` tiene opciones más complejas.

### Modifying strings with list manipulations

A veces queremos modificar strings como si fueran un list de caracteres. En ese caso, podemos convertir el string en un list.

```python
text="Hello, world"
wordList = list(text)
...
text = "".join(wordList)
```

Si vamos a procesar millones de strings, esta forma resulta demasiado costosa, porque crear y borrar strings resulta costoso.

### Useful methods and constants

Estos métodos no cambian el string, sino que devuelven una parte del string o generan uno nuevo.

```python
x.upper()
x.lower()
x.title()
x.find()
...
```

## Converting from objects to strings

En Python, casi todo puede ser convertido en una representación en string, usando la función `repr`.

```python
x = [1]
x.append([3, 4])
'the list x is ' + repr(x) # the list x is [1, [3, 4]]

repr(len) # <built-in function len>
```

Python también tiene la función `str`, que pretende representar la información de una forma legible por una persona.

## Using the format method

Método `format`.

```python
"{0} is the {1} of {2}".format("Ambrosia", "food", "the gods")

"{foods} is the food of {user}".format(food="Ambrosia", user="the gods")
```

## String Interpolation

```python
value = 42
message = f"The answer is {value}"
print(message) # The answer is 42
```

## Bytes

Un objeto bytes es similar a un string, pero con una importante diferencia: un string es una secuencia inmutable de caracteres Unicode, mientras que un objeto bytes is una secuencia de integers con valores entre 0 y 256. Los bytes se utilizan cuando se manejan datos binarios.

```python
unicode_a_with_acute = '\N{LATIN SMALL LETTER A WITH ACUTE}' # á
xb = unicode_a_with_acute.encode() # b'\xc3\xa1'
xb.decode() # á
```

# 7. Dictionaries
Es el nombre que da Python a los arrays asociativos o maps, que se implementan usando hash tables.

## What is a dictionary?

Vamos a compararlo con las listas:
* Los valores en listas son accedidos por índices (integer), que indican dónde se encuentra un valor en una lista.
* En los diccionarios, se accede por integer, string u otros objetos de Python llamados keys, que indican dónde se encuentra un valor en un diccionario.
* Tanto las listas como diccionarios pueden almacenar objetos de cualquier tipo.
* Los valores almacenados en una lista son ordenados implícitamente por su posición en la lista. Los valores en un diccionario no están implícitamente ordenados. Si queremos que estén ordenados usaremos un ordered dictionary, que es una subclase de diccionario que puede importarse del módulo `collections`.

Una lista y un diccionario vacíos: 

```python
x = []
y = {}
```

Podemos almacenar valores en el diccionario como si fuera una lista:

```python
y[0] = 'Hello'
y[1] = 'Goodbye'
```

Si hicieramos esto mismo en una lista, nos daría error, porque no se puede asignar una posición que no existe en la lista.

Pero podemos almacenar más key como strings en el diccionario:

```python
y["two"] = 2
y["pi"] = 3.14
```
Esto es algo que con las listas no se puede hacer.

## Other dictionary operations

Se puede definir un diccionario de forma explícita como una serie de pares key-value separados por coma:

```python
>>> english_to_french = {'red': 'rouge', 'blue': 'bleu'}
>>> len(english_to_french)
2
# Return keys
>>> list(english_to_french.keys())
['red', 'blue']
# Return values
>>> list(english_to_french.values())
['rouge', 'bleu']
# Return keys and their associated values as a sequence of tuples
>>> list(english_to_french,items())
[('red','rouge'), ('blue','bleu')]
# Remove entry from a dictionary
>>> del english_to_french['green']
# Test presence of key on dictionary
>>> 'red' in english_to_french
# Get or default
>>> english_to_french.get('blue', 'No translation')
# Shallow copy dictionary
>>> y = english_to_french.copy()
## Deep copy dictionary
>>> y = english_to_french.deepcopy()
# Update dictionary with other dictionary
>>> z = {1: 'One', 2: 'Two'}
>>> x = {0: 'zero', 1: 'one'}
>>> x.update(z)
>>> x
{0:'zero', 1: 'One', 2: 'Two'}
```

Los métodos `keys, values, items` no devuelven listas, sino views que se comportan como secuencias pero siendo dinámicamente actualizadas cuando el diccionario cambia.

Si no lo convertimos en lista, se comportan como secuencias, y podremos iterar sobre ellas con un for.

Desde Python 3.6, los diccionarios mantienen el orden en el que fueron creadas las keys.

## What can be used as a key?

Cualquier objeto de Python que sea inmutable y hasheable puede usarse como key de un diccionario.

Numbers o strings son inmutables. Si una variable x se le da el valor number 3, y luego le asignamos el 4, no estamos cambiando el valor number 3 en sí.

Las lists o dictionaries son mutables.

Desafortunadamente, como las keys tienen que ser inmutables y hasheables, las listas no se pueden usar como keys, pero muchas veces interesaria una key de tipo lista. Por ejemplo, almacenar información de una persona bajo una key que consiste en el nombre y apellido de una persona, pudiendo usar una lista de dos elementos como key.

Python resuelve esto usando las tuplas, que son básicamente listas inmutables.

Además, las keys deben ser hasheables. Para serlo, un valor debe tener un valor hash (devuelto por el método `__hash__`) que nunca cambiará durante la vida del valor. Esto quiere decir que las tuplas que contengan valores mutables no son hasheables, aunque las tuplas sean técnicamente inmutables.

Solo las tuplas que no contengan objetos mutables son hasheables y válidas para usarse como keys de diccionarios.

## Sparse matrices

En Python, una matriz se representa así:

```python
matrix = [[3,0,-2], [0,9,0]]
element = matrix[rownum][colnum]
```

Sin embargo, en muchos casos podemos tener matrices muy grandes, pero que la mayor parte de valores sean 0. Para conservar memoria, se usan las sparse matrices.

Se trata de diccionarios con tuplas como índices.

```python
matrix = {(0, 0): 3, (0, 2): -2, (0, 3): 11, (1, 1): 9, (2, 1): 7, (3, 3): -5}
```

Así, ahora puedo acceder a los elementos de la matriz:

```python
if (rownum, colnum) in matrix:
  element = matrix[(rownum, colnum)]
else:
  element = 0

# Otra opción
element = matrix.get((rownum, colnum), 0)
```
# 9. Functions

## Basic function definitions

```python
>>> def fact(n):
  """Return the factorial of the given number."""
  r = 1
  while n > 0:
    r = r * n
    n = n -1
  return r
```

La segunda línea es una docstring. Se puede obtener su valor mediante `fact.__doc__`.


## Function parameter options

### Positional parameters

Los parámetros de una función pueden tener valores por defecto: `def fun(arg1, arg2=default, arg3=default2, ...)`. Los parámetros con valores por defecto deben definirse como los últimos en la lista.

### Passing arguments by parameter name

### Variable numbers of arguments

#### Dealing with an indefinite number of positional arguments

Si añadimos * al último parámetro de una función, haremos que todos los argumentos que no casen (y sean sin keyword) se junten en una tupla con el nombre del parámetro.

```python
>>> def maximum(*numbers):
      if len(numbers) == 0:
        return None

>>> maximum(3,2,8)
```

#### Dealing with an indefinite number of arguments passed by keyword

Si el último parámetro lo prefijamos con **, recolectará los argumentos keyword-passed que no estén definidos, y los junta en un diccionario.

```python
>>> def example_fun(x, y, **other):
      for k in other.keys():
        ...

>>> example_fun(2, y="1", foo=3, bar=4)
```

### Mixing argument-passing techniques

La regla general es que los argumentos posicionales van primero, luego los argumentos nombrados, luego el argumento * y finalmente el **.

## Mutable objects as arguments

Los argumentos se pasan por object reference. El parámetro pasa a ser una nueva referencia al objeto. Para objetos inmutables (tuplas, strings, numbers), lo que se hace con el parámetro no afecta fuera de la función. Pero si pasas un objeto mutable (lista, diccionario, instancia de clase), todo cambio hecho al objeto cambia a lo que esté referenciando el argumento fuera de la función.

Si se reasigna el parámetro, no afectará al argumento.

Ejemplo:

```python
def f(n, list1, list2):
  list1.append(3)
  list2 = [4,5,6]
  n = n + 1

x = 5
y = [1,2]
z = [4,5]

f(x,y,z)

x, y, z  # (5, [1, 2, 3], [4, 5])
```

## Local, nonlocal, and global variables

Se puede hacer una variable global declarándolo con `global`. Las variables globales pueden ser accedidas y cambiadas por la función. Existen fuera de la función y pueden ser accedidas y cambiadas por otras funciones que la declaren global o por código que no esté dentro de una función.

```python
def fun():
  global a
  a = 1
  b = 2
```

## Assigning functions to variables

```python
def f_to_kelvin(degrees_f):
  return 273.15 + (degrees_f - 32) * 5 / 9

abs_temperature = f_to_kelvin
abs_temperature(32)
```

También las podemos asignar a listas, tuplas y diccionarios:

```python
t = {'FtoK': f_to_kelvin}
t['FtoK'](32)
```

## lambda expressions

```python
lambda parameter1, parameter2, ...: epression
```

```python
t2 = {'FtoK': lambda deg_f: 273.15 + (deg_f - 32) * 5 / 9}
```

## Generator functions

Es un tipo especial de función que podemos usar para definir nuestros propios iteradores. Cuando definimos una función generator, devolvemos el valor de cada iteración usando `yield`. El generator dejará de devolver valores cuando no haya más iteraciones, o si encuentra un `return` al final de la función.

Las varaibles locales en una función generator se guardan de una llamada a otra, al contrario que las funciones normales.

```python
def four():
  x = 0
  while x < 4:
    print("in generator, x =", x)
    yield x
    x += 1

for i in four():
  print(i)

```

Esto mostrará:

```python
in generator, x = 0
0
in generator, x = 1
1
in generator, x = 2
2
in generator, x = 3
3
```

## Decorators

Es posible, por ejemplo, una función que tome otra función como parámetro, la wrapee en otra función, y luego que retorne la nueva función. Esta nueva combinación se puede usar en vez de la función original:

```python
>>> def decorate(func):
      print("in decorate function, decorating", func.__name__)
      def wrapper_func(*args):
        print("Executing", func.__name__)
        return func(*args)
      return wrapper_func

>>> def myfunction(parameter):
      print(parameter)

>>> myfunction = decorate(myfunction)
in decorate function, decorating myfunction
>>> myfunction("hello")
Executing myfunction
hello
```

Un decorador es azúcar sintáctico sobre este proceso, y nos permite wrapear una función dentro de otra.

Para usar un decorador hay que: definir la función que decorará otras funciones, y luego usarla en los método/s que quiera wrapear.

```python
>>> def decorate(func):
      print("in decorate function, decorating", func.__name__)
      def wrapper_func(*args):
        print("Executing", func.__name__)
        return func(*args)
      return wrapper_func

>>> @decorate
    def myfunction(parameter):
      print(parameter)

in decorate function, decorating myfunction
>>> myfunction("hello")
Executing myfunction
hello
```

# 10. Modules and scoping rules

## What is a module?

Un módulo es un fichero que contiene código. Define un grupo de funciones de Python u otros objetos, y el nombre del módulo es el nombre del fichero.

Un namespace es un diccionario the los identificadores disponibles para un bloque, función, clase o módulo. Cada módulo tiene su namespace, lo cual evita conflictos entre nombres.

## A first module

```python
# Fichero mymath.py
pi = 3.1415
def area(r):
  #...

# Uso
import mymath
mymath.pi

# Uso
from mymath import pi
pi
```

Cuando un módulo se carga por primera vez o es recargado, todo su código se parsea. Si hay algún error de sintáxis lanzará un error. Si no, se crea un fichero .pyc que contiene el byte code creado.



## The import statement

Tres formas:

```python
import modulename

from modulename import name1, name2, name2, ...

from modulename import *

```
El último importará todos los nombres públicos (los que no empiecen por __), y los hará disponibles directamente en el módulo, sin necesidad de especificar el módulo.

## The module search path

Dónde busca Python los módulos está definido en una variable llamada `path`, a la que se puede acceder a través del módulo `sys`:

```python
>>> import sys
>>> sys.path
```

El valor mostrado depende de la configuración de nuestro sistema. Mostrará la lista de directorios sobre los que Python busca (en orden) cuando ejecute un import.

El primer módulo que satisfaga el import será el usado. Si no se encuentra ningún módulo, se lanzará una excepcion `ImportError`.

La variable `sys.path` se inicializará con el valor de la variable de entorno `PYTHONPATH`, si existe, o si no a partir de un valor por defecto que dependerá de nuestra instalación.

Además, cada vez que corramos un script de Python, la variable `sys.path` para este script tendrá el directorio que contenga el script como primer elemento.

### Where to place your own modules

Para asegurar que nuestros programas usan nuestros módulos, debemos:
* Colocar nuestros módulos en uno de los directorios donde Python normalmente busque módulos. Esta no se debe usar, porque estos directorios están pensados para site-specific code (código específico para la máquina)
* Colocar todos los módulos usados por el programa en el mismo directorio que el programa. Es una buena opción para módulos que estén asociados a un programa concreto.
* Crear un directorio (o directorios) para mantener los módulos, y modificar la variable `sys.path` para incluir este nuevo directorio o directorios. Opción buena para módulos que vayan a ser usados por más de un programa.

Para modificar la variable `sys.path` se puede hacer mediante código, modificando la variable de entorno `PYTHONPATH` o usando un fichero .pth. Esto último, en Windows se puede crear un fichero .pth en el directorio al que apunte `sys.prefix`.

```python
# Fichero myModules.pth
mymodules
c:\Users\naomi\python\modules
```

## Python scoping rules and namespaces
El concepto clave aquí es el de namespace. Un namespace es un mapeo de identificadores con objetos. Es decir, cómo Python mantiene qué variables e identificadores están activos y a dónde apuntan.

Así, una sentencia como `x = 1` añade a x en el namespace y le asocia con el valor 1.

Cuando se ejecuta un bloque de código en Python, existen tres namespaces: local, global y built-in.

Cuando se encuentra un identificador durante una ejecución, Python primero mira en el namespace local. Si no encuentra el identificador, mira en el namespace global. Si aún así no lo encuentra, mira en el built-in namespace. Si aún así no lo encuentra, se lanza una excepción `NameError`.

Para un módulo, un comando ejecutado en una sesión o un script corriendo desde un fichero, los namespaces local y global son el mismo. Crear una variable, función o importar algo de otro módulo resulta en una nueva entrada en este namespace.

Pero cuando se hace una llamada a una función, se crea un nuevo namespace local, y se crean entradas por cada parámetro en la llamada. Y cada vez que se cree una variable en la función, también se añadirá una nueva entrada.

El namespace global de una función es el namespace global del bloque que contiene a la función (el módulo, fichero o sesión interactiva). Es independiente del contexto dinámico desde el que haya sido llamada.

En todas estas situaciones, el namespace built-in es el del módulo `__builtins__`. Este módulo contiene, entre otras cosas, todas las funciones built-in que haya encontrado (como `len, min, max, int, float, list, tuple, range, str o repr`) y otras clases built-in de Python, como las excepciones (como `NameError`).

Se pueden sobreescribir elementos del módulo built-in. Si por ejemplo creamos una lista en nuestro programa y la ponemos en la variable `list`, no podrás usar la función `list` existente en el módulo built-in.

Vamos con un ejemplo, usando las funciones `locals` y `globals`, que devueven diccionarios que contienen los bindings de los namespaces local y global.

```python
>>> locals()
{'__builtins__': <module 'builtins' (built-in)>, '__name__': '__main__','__doc__': None, '__package__': None}
>>> globals()
{'__builtins__': <module 'builtins' (built-in)>, '__name__': '__main__','__doc__': None, '__package__': None}
```

Los namespaces local y global para esta sesión interactiva son el mismo. El nombre del módulo principal `__main__`, un string vacío para `__doc__` y el módulo usado para el namespace built-in `__builtins__`.

Si ahora creamos una variable y la importamos:

```python
>>> z = 2
>>> import math
>>> from cmath import cos
>>> globals()
{'cos': <built-in function cos>, '__builtins__': <module 'builtins'(built-in)>, '__package__': None, '__name__': '__main__', 'z': 2,'__doc__': None, 'math': <module 'math' from '/usr/local/lib/python3.0/libdynload/math.so'>}
>>> locals()
{'cos': <built-in function cos>, '__builtins__': <module 'builtins' (built-in)>, '__package__': None, '__name__': '__main__', 'z': 2, '__doc__': None, 'math': <module 'math' from '/usr/local/lib/python3.0/libdynload/math.so'>}
>>> math.ceil(3.4)
4
```

Ambos namespaces siguen siendo iguales. 

Si ahora creamos una función en una sesión interactiva:

```python
>>> def f(x):
      print("global: ", globals())
      print("Entry local: ", locals())
      y = x
      print("Exit local: ", locals())
>>> z = 2
>>> globals()
{'f': <function f at 0xb7cbfeac>, '__builtins__': <module 'builtins' (built-in)>, '__package__': None, '__name__': '__main__', 'z': 2, '__doc__': None}
>>> f(z)
global: {'f': <function f at 0xb7cbfeac>, '__builtins__': <module 'builtins' (built-in)>, '__package__': None, '__name__': '__main__', 'z': 2, '__doc__': None}
Entry local: {'x': 2}
Exit local: {'y': 2, 'x': 2}
>>>
```

Aquí podemos ver el namespace local dentro de la función, y vemos que el namespace global es el mismo que el de la sesión interactiva.

Si llamamos a una función de un módulo, el namespace global de la función será el del módulo en donde la función esté definida, no tiene que ver desde dónde se llame.

```python
"""scopetest: our scope test module"""
v = 6
def f(x):
  """f: scope test function"""
  print("global: ", list(globals().keys()))
  print("entry local:", locals())
  y = x
  w = v
  print("exit local:", locals().keys())
```

```python
>>> import scopetest
>>> z = 2
>>> scopetest.f(z)
global: ['__name__', '__doc__', '__package__', '__loader__', '__spec__',
'__file__', '__cached__', '__builtins__', 'v', 'f']
entry local: {'x': 2}
exit local: dict_keys(['x', 'w', 'y'])
```

Como se ve, el namespace global no incluye z, que está definido en la sesión interactiva.

# 11. Python programs

## Creating a very basic program

### Starting a script from a command line

```bash
python script1.py
```

### Command-line arguments

Los comandos se almacenan en `sys.args`.

```python
import sys
def main():
  print(sys.argv)
main()
```

```bash
python script2.py arg1 arg2 3
```

### Redirecting the input and output of a script

Se puede redirigir la entrada y/o salida de un script `sys.stdin` y `sys.stdout`.

```python
import sys
def main():
  contents = sys.stdin.read()
  sys.stdout.write(contents.replace(sys.argv[1], sys.argv[2]))
main()
```

Este script lee de la entrada estándar y escribe en la salida lo que lee.

Si lo llamamos de la siguiente forma, el script copia en outfile el contenido de infile sustituyendo "zero" por "0":

```bash
python replace.py zero 0 < infile > outfile
```

En general, esta línea `python script.py arg1 arg2 arg3 arg4 < infile > outfile` tiene como efecto que la entrada sea infile y que todas las operaciones `print` o `sys.stdout` sean redirigidas a outfile.

Si queremos hacer append en outfile en vez de sobreescribir: `python replace.py a A < infile >> outfile`.

También podemos hacer pipe de los comandos: `python replace.py 0 zero < infile | python replace.py 1 one > outfile`.

### The argparse module

El módulo `argparse` da soporte para pasar diferentes tipos de argumentos.

```python
from argparse import ArgumentParser

def main():
  parser = ArgumentParser()
  parser.add_argument("indent", type=int, help="indent for report")
  parser.add_argument("input_file", help="read data from this file")
  parser.add_argument("-f", "--file", dest="filename", help="write report to FILE", metavar="FILE")
  parser.add_argument("-x", "--xray", help="specify xray strength factor")
  parser.add_argument("-q", "--quiet", action="store_false", dest="verbose", default=True, help="don't print status messages to stdout")

  args = parser.parse_args()
  print("arguments:", args)
main()
```
Este código crea una instancia de `ArgumentParser` y añade dos argumentos posicionales: `indent` y `input_file`. Los argumentos posicionales son aquellos sin el prefijo - y son requeridos.

`argparse` devuelve un objeto Namespace que contiene los argumentos.

### Using the fileinput module

El módulo `fileinput` es útil para scripts. Da soporte para procesar líneas de entrada de uno o más ficheros. Lee los argumentos (de `sys.argv`) y los toma como un listado de ficheros de entrada. Luego permite iterar secuencialmente sobre esas líneas.

```python
import fileinput
def main():
  for line in fileinput.input():
    if not line.startswith('##'):
      print (line, end="")
main()
```

Si tenemos dos ficheros:

```
## sole1.tst: test data for the sole function
0 0 0
0 100 0
##
0 100 100
```

y 

```
## sole2.tst: more test data for the sole function
12 15 0
##
100 100 0
```

Y llamamos al script: `python script4.py sole1.tst sole2.tst`, obtendremos el resultado con los dos ficheros combinados:

```
0 0 0
0 100 0
0 100 100
12 15 0
100 100 0
```

Si no hay argumentos de entrada, se leerá de la entrada estándar.

Este módulo nos da más información:
* `lineno`: número de líneas que se han leído.
* `filelineno`: número de líneas que se han leído del fichero actual.
* `filename`: nombre del fichero actual.
* `isfirstline`: si es la primera línea del fichero.

## Making a script directly executable on UNIX

Para hacer un script ejecutable directamente en UNIX, añadir al inicio del fichero `#! /usr/bin/env python`, y cambiar el modo del fichero `chmod +x script.py`

## Programs and modules

Separar la función controladora del resto de código es una buena opción.

```python
#! /usr/bin/env python3
import sys

def num2words(num_string):
  ...

def main():
  print(num2words(sys.argv[1]))
main()
```

Llamamos al script: `python script6.py 59`.

La gente combina scripts con módulos cuando quieren que las funciones que hayan creado en un script estén disponibles para otros módulos o scripts.

Para combinar el uso como un script y un módulo:

```python
if __name__ == '__main__':
  main()
else:
  # module-specific initialization code if any
```

Si se le llama como un script, se ejecutará con el nombre `__main__`. Si se le importa en un módulo o sesión interactiva, su nombre será el nombre del fichero.


## Distributing Python applications

### Wheels packages

Es la forma actual estándar de empaquetar y distribuir módulos y aplicaciones.

### zipapp and pex

Si tenemos una aplicación que está en múltiples módulos, podemos distribuirla como un zip ejecutable. 

Si el fichero zip contiene un fichero llamado `__main__.py`, Python puede usar este fichero como punto de entrada al archivo y ejecutar el fichero `__main__.py` directamente. Además, los contenidos del zip se añaden al `sys.path`, así que estarán disponibles para ser importados por `__main__.py`.

### py2exe and py2app

### Creating executable programs with freeze

Se pueden crear ejecutables con Python que corran en máquinas que no tengan Python instalado, usando la herramienta `freeze`.

En el proceso de "freezing" de un programa Python, se crean ficheros de C, que se compilan usando un compilador de C.

# 14. Exceptions

## Exceptions in Python

Una excepción es un objeto generado automáticamente por funciones de Python mediante una sentencia `raise`. Cuando ocurre, en vez de avanzar a la siguiente línea después de la excepción, se busca un handler que pueda manejar la excepción generada. Si se encuentra, se invocará. Si no se encuentra ninguno, el programa abortará con un mensaje de error.

Python, al contrario que en otros lenguajes como Java, confía en las excepciones para hacer frente a errores una vez ya han ocurrido. 

### Types of Python exceptions

```python
BaseException
  SystemExit
  KeyboardInterrupt
  GeneratorExit
  Exception
    StopIteration
    ArithmeticError
      FloatingPointError
      OverflowError
      ZeroDivisionError
    AssertionError
...
```
Se aconseja que cualquier excepción creada extienda de `Exception`, no de `BaseException`.

Esto es para poder terminar una ejecución con Ctrl-C, que no sea capturada esa excepción (KeyboardInterrupt no es subclase de Exception).

### Raising exceptions

Para lanzar una excepción: `raise exception(args)`.

### Catching and handling exceptions

Una excepción no tiene por qué causar la terminación de un programa.

```python

try:
  body
except exception_type1 as var1:
  exception_code1
except:
  default_exception_code
else:
  else_body
finally:
  finally_body
```

### Defining new exceptions

```python
class MyError(Exception):
  pass
```

Se puede pasar una string como parámetro:

```python
try:
  raise MyError("Some information")
except MyErrror as error:
  print("Situation: ",error)
```

También se pueden pasar varios parámetros:

```python
try:
  raise MyError("Some information", "my_filename", 3)
except MyError as error:
  print("Situation: {0} with file {1}\n error code: {2}".format(error.args[0], error.args[1], error.args[2]))
```

### Debugging programs with the assert statement

`assert` es una forma especial de una sentencia `raise`.

```python
assert expression, argument
```

Si falla la aserción y la variable de sistema `__debug__` está a True, se genera un `AssertionError`. 

### The exception inheritance hierarchy

Si hay varios `except`, y el primero de ellos cumple, los siguientes nunca se ejecutarán

### Example: a disk-writing program in Python

## Context managers using the with keyword

En algunas situaciones, como leer ficheros, siguen un mismo patrón. En el caso de leer de un fichero, la mayor parte de las veces se necesita abrir una sola vez (mientras se leen los datos). Después es fichero puede cerrarse.

```python
try:
  infile = open(filename)
  data = infile.read()
finally:
  infile.close()
```

Python 3 define una forma más genérica de definir esto: usar "context managers".

Los "context managers" pueden wrapear un bloque y gestionar requerimientos de entrada y salida del bloque, y se marcan con la palabra `with`:

```python
with open(filename) as infile:
  data = infile.read()
```
Estas dos líneas son equivalentes a las anteriores. En ambos casos, sabemos que el fichero será cerrado después de la última lectura, haya ido bien o no.

Podemos crear nuestros propios "context managers" para cosas como bloquear y desbloquear recursos, cerrar ficheros, commitear transacciones...

# 15. Classes and object-oriented programming

## Defining classes
Una clase es un tipo de dato.

```python
class MyClass:
  # body

instance = MyClass()
```

### Using a class instance as a structure or record
Los data fields de una instancia no necesitan ser declarados en la definicion, pueden crearse al vuelo.

Se puede inicializar los campos de una instancia automáticamente usando el método `__init__` en el cuerpo. Esta función se ejecuta cada vez que una instancia de la clase se crea, siendo esa instancia el primer argumento, `self`.

```python
class Circle:
  def __init__(self):
    self.radius = 1

my_circle = Circle()
print(my_circle.radius)
```

Python tiene algo que es más un constructor, el método `__new__`, que es lo que se llama en la creación del objeto y devuelve un objeto no inicializado (luego se inicializará en el constructor). A no ser que se vaya a hacer una subclase de un tipo inmutable, como `str` o `int`, es raro sobreescribir el método `__new__`.

## Instance variables

```python
class Circle:
  def __init__(self):
    self.radius = 1
```
`radius` es una variable de instancia de `Circle`. Cada instancia de la clase tendrá su propia copia de `radius`.

Si una variable no existe, la crea automáticamente.

## Methods
Función asociada a una clase en particular.

```python
class Circle:
  def __init__(self):
    self.radius = 1

  def area(self):
    return self.radius * self.radius * 3.14

c = Circle()
c.area()
```
El primer argumento de cualquier método es la instancia invocada, llamada `self` por convención.

Cuando se llame a un método `instance.method(arg1, arg2, ...)`, Python seguirá estas reglas:
* Buscará el método en el namespace de la instancia.
* Si no lo encuentra, buscará el método en la clase de la instancia.
* Si no lo encuentra, buscará en la superclase.

## Class variables
Una class variable es una variable asociada a una clase, no a una instancia de la clase, y es accesible por todas las instancias de la clase.

Una variable de clase se crea por asignación en el body de la clase, no en la función `__init__`.

```python
class Circle:
  pi = 3.14159
  def __init__(self):
    self.radius = 1

Circle.pi
```

```
>>> Circle
<class '__main__.Circle'>
>>> c.__class__
<class '__main__.Circle'>
```

La clase Circle se representa internamente por una estructura de datos abstracta, y esa estructura es la que se obtiene del atributo `__class__` de `c`, instancia de Circle. Así, podemos obtener el valor de pi a partir de la propia instancia `c` sin hacer referencia a la clase:

```
>>> c.__class__.pi
```

### An oddity with class variables
Cuando Python está buscando una variable de instancia, si no puede encontrar una variable de instancia con ese nombre, intentará encontrar y devolver el valor de una variable de clase que tenga el mismo nombre. Si no puede encontrar una variable de clase, entonces dará error.

Así, las variables de clase hacen eficiente implementar valores por defecto en variables de instancia: simplemente crea una variable de clase con el mismo nombre y un valor por defecto adecuado, evitando así el tiempo y la memoria de tener que inicializar esa variable de instancia cada vez que se cree una instancia.

```python
>>> c = Circle(3)
>>> c.pi
3.14159
```

Sin embargo, si tratamos de cambiar su valor, no funcionará como una variable de clase real.

```python
>>> c1 = Circle(1)
>>> c2 = Circle(2)
>>> c1.pi = 3.14
>>> c1.pi
3.14
>>> c2.pi
3.14159
>>> Circle.pi
3.14159
```

Esto ocurre porque la asignación `c1.pi` realmente crea una variable de instancia en `c1`, sin afectar a la variable de clase `Circle.pi`.

## Static methods and class methods

### Static methods
Para crear un método estático, hay que usar `@staticmethod`.

```python
class Circle:
  all_circles = [] # class variable containing list of all circles that have been created
  pi = 3.14159
  def __init__(self, r=1):
    self.radius = r
    self.__class__.all_circles.append(self)
  def area(self):
    return self.__class__.pi * self.radius * self.radius
  
  @staticmethod
  def total_area():
    total = 0
    for c in Circle.all_circles:
      total = total + c.area()
    return total
```

```python
>>> import circle
>>> c1 = circle.Circle(1)
>>> c2 = circle.Circle(2)
>>> circle.Circle.total_area()
```

### Class methods
Los métodos de clase son similares a los método estáticos en cuanto a que pueden ser invocados antes de que un objeto de la clase sea instanciado, o usando una instancia de la clase. Como diferencia, a los métodos de clase se les pasa como primer parámetro la clase a la que pertenecen. Para los métodos de clase hay que usar `@classmethod`.

```python
class Circle:
  all_circles = [] # class variable containing list of all circles that have been created
  pi = 3.14159
  def __init__(self, r=1):
    self.radius = r
    self.__class__.all_circles.append(self)
  def area(self):
    return self.__class__.pi * self.radius * self.radius
  
  @classmethod
  def total_area(cls):
    total = 0
    for c in cls.all_circles:
      total = total + c.area()
    return total
```

```python
>>> import circle_cm
>>> c1 = circle_cm.Circle(1)
>>> c2 = circle_cm.Circle(2)
>>> circle_cm.Circle.total_area()
```

De esta forma, se puede usar `cls` en vez de `self.__class__`.

Usando un método de clase en vez de un método estático, no hay que usar el nombre de la clase directamente en `total_area`. De esta forma, cualquier subclase de Circle puede llamar a `total_area` refiriéndose a sus propios miembros, no a los de Circle.

## Inheritance
Es más flexible que la herencia en lenguajes compilados como Java o C++.

```python
class Square:
  def __init__(self, side=1, x=0, y=0):
    self.side = side
    self.x = x
    self.y = y

class Circle:
  def __init__(self, radius=1, x=0, y=0):
    self.radius = radius
    self.x = x
    self.y = y
```

Viendo el código, podemos abstraer x e y en una clase general.

```python
class Shape:
  def __init__(self, x, y):
    self.x = x
    self.y = y

class Square(Shape):
  def __init__(self, side=1, x=0, y=0):
    super().__init__(x,y)
    self.side = side

class Circle(Shape):
  def __init__(self, r=1, x=0, y=0):
    super().__init__(x,y)
    self.radius = r
```

Se debe llamar explícitamente al método `__init__` de la clase de la que se hereda. Si no, en el ejemplo anterior, las instancias de Circle y Square no tendrán las variables de instancia x e y seteadas.


## Inheritance with class and instance variables
La herencia permite a una instancia heredar atributos de la clase. Las variables de instancia se asocian con objetos de instancia, y solo existe una variable de instancia con un nombre para una instancia.

```python
class P:
  z = "Hello"
  def set_p(self):
    self.x = "Class P"
  def print_p(self):
    print(self.x)

class C(P):
  def set_c(self):
    self.x = "Class C"
  def print_c(self):
    print(self.x)
```

Si ejecutamos:

```python
>>> c = C()
>>> c.set_p()
>>> c.print_p()
Class P
>>> c.print_c()
Class P
>>> c.set_c()
>>> c.print_c()
Class C
>>> c.print_p()
Class C
```
C hereda de P, pero `c` no hereda de una instancia invisible de P. Lo que hereda son los métodos y variables de clase de P. Como solo hay una instancia (c), toda referencia a la variable de instancia x se refiere a c.x. Esto es así sea cual sea la clase que defina el método invocado por c.

```python
>>> c.z; C.z; P.z
'Hello'
'Hello'
'Hello'
```

Pero si tratamos de cambiar el valor de la la variable de clase `z` a través de la clase C, se creará una nueva variable de clase en la clase C. Esto no tiene ningún efecto sobre la variable de clase en P.

```python
>>> C.z = "Bonjour"
>>> c.z; C.z; P.z
'Bonjour'
'Bonjour'
'Hello'
```
Igualmente, si tratamos de cambiar el valor de z a través de c, se creará una nueva variable de instancia:

```python
>>> c.z = "Ciao"
>>> c.z; C.z; P.z
'Ciao'
'Bonjour'
'Hello'
```

## Private variables and private methods

Una variable privada o método privado es aquel que no puede ser visto fuera de los métodos de la clase en la que ha sido definido.

Cualquier método o variable de instancia cuyo nombre comience por doble barra baja es privado.

El mecanismo usado para proveer de esta privacidad es modificando el nombre de las variables y métodos privados cuando el código se compila en bytecode. Lo que hace es hacer prepend de _classname al nombre de la variable:

```python
>>> dir(m)
['_MyClass_y', 'x', '...']
```

## Using @property for more flexible instance variables
Una property combina la posibilidad de dar acceso a una variable de instancia a través de métodos como getters y setters, y el acceso a las variables de instancia a través de la notación típica por punto.

```python
class Temperature:
  def __init__(self):
    self._temp_fahr = 0
  
  @property
  def temp(self):
    return (self._temp_fahr - 32) * 5 / 9
```

Sin setter, esta propiedad será readonly. Si añadimos setter:

```python
  @temp.setter
  def temp(self, new_temp):
    selt._temp_fahr = new_temp * 9 / 5 + 32
```

Ahora podemos usar la notación por punto para hacer get y set de la propiedad `temp`.

## Scoping rules and namespaces for class instances

Cuando estás en un método o una clase, tienes acceso directo al namespace local (parámetros y variables declaradas en el método), el namespace global (funciones y variables declaradas a nivel de módulo) y el built-in namespace (funciones y excepciones built-in). Se busca sobre estos namespaces en orden: local, global y built-in.

También, a través de la variable `self`, tenemos acceso al namespace de la instancia (variables de instancia, variables de instancia privadas, variables de instancia de la superclase), el namespace de la clase (métodos, variables de clase, métodos privados y variables de clase privadas) y al namespace de la superclase (métodos de la superclase y variables de clase de la superclase).

```python
mv = "module variable: mv"

def mf():
  return "moduele function (can be used like a class method in other languages): mf()"

class SC:
  scv = "superclass class variable: self.scv"
  _pscv = "private superclass class variable: no access"

  def __init__(self):
    self.siv = "superclass instance variable: self.siv (but use SC.siv for assignment)"
    self.__psiv = "private superclass instance variable: no access"

  def sm(self):
    return "superclass method: self.sm()"

  def __spm(self):
    return "superclass private method: no access"

class C(SC):
  cv = "class variable: self.cv (but use C.cv for assignment)"
  __pcv = "class private variable: self.__pcv (but use C.__pcv for assignment)"

  def __init__(self):
    SC.__init__(self)
    self.__piv = "private instance variable: self.__piv"

  def m2(self):
    return "method: self.m2()"

  def __pm(self):
    return "private method: self.__pm()"

  def m(self, p="parameter: p"):
    lv = "local variable: lv"
    self.iv = "instance variable: self.xi"

    print("Access local, global and build.in namespaces directly")

    print("local namespace:", list(locals().keys()))
    print(p)

    print(lv)
    print("global namespace:", list(globals().keys()))

    print(mv) # module variable

    print(mf())
    print("Access instance, class, and superclass namespaces through self")

    print("Instance namespace:", dir(self))

    print(self.iv)

    print(self.__piv)

    print(self.siv)
    print("Class namespace:",dir(C))
    print(self.cv)

    print(self.m2())

    print(self.__pcv

    print(self.__pm())
    print("Superclass namespace:",dir(SC))
    print(self.sm())

    print(self.scv)
```

```python
>>> import cs
>>> c = cs.C()
>>> c.m()
Access local, global and built-in namespaces directly
local namespace: ['lv', 'p', 'self']
parameter: p
local variable: lv

global namespace: ['C', 'mf', '__builtins__', '__file__', '__package__',
'mv', 'SC', '__name__', '__doc__']
module variable: mv
module function (can be used like a class method in other languages): mf()

Access instance, class, and superclass namespaces through 'self'
Instance namespace: ['_C__pcv', '_C__piv', '_C__pm', '_SC__pscv',
'_SC__psiv', '_SC__spm', '__class__', '__delattr__', '__dict__',
'__doc__', '__eq__', '__format__', '__ge__', '__getattribute__',
'__gt__', '__hash__', '__init__', '__le__', '__lt__', '__module__',
'__ne__', '__new__', '__reduce__', '__reduce_ex__', '__repr__',
'__setattr__', '__sizeof__', '__str__', '__subclasshook__',
'__weakref__', 'cv', 'iv', 'm', 'm2', 'scv', 'siv', 'sm']
instance variable: self.xi
private instance variable: self.__piv
superclass instance variable: self.siv (but use SC.siv for assignment)

Class namespace: ['_C__pcv', '_C__pm', '_SC__pscv', '_SC__spm', '__class__',
'__delattr__', '__dict__', '__doc__', '__eq__', '__format__', '__ge__',
'__getattribute__', '__gt__', '__hash__', '__init__', '__le__',
'__lt__', '__module__', '__ne__', '__new__', '__reduce__',
'__reduce_ex__', '__repr__', '__setattr__', '__sizeof__', '__str__',
'__subclasshook__', '__weakref__', 'cv', 'm', 'm2', 'scv', 'sm']
class variable: self.cv (but use C.cv for assignment)
method: self.m2()
class private variable: self.__pcv (but use C.__pcv for assignment)
private method: self.__pm()

Superclass namespace: ['_SC__pscv', '_SC__spm', '__class__', '__delattr__',
'__dict__', '__doc__', '__eq__', '__format__', '__ge__',
'__getattribute__', '__gt__', '__hash__', '__init__', '__le__',
'__lt__', '__module__', '__ne__', '__new__', '__reduce__',
'__reduce_ex__', '__repr__', '__setattr__', '__sizeof__', '__str__',
'__subclasshook__', '__weakref__', 'scv', 'sm']
superclass method: self.sm()
superclass class variable: self.scv
```
## Destructors and memory managements
No es necesario crear y llamar a un destructor para asegurar que la memoria de la instancia se libera. Python provee de una forma automática de gestionar la memoria mediante un mecanismo de reference-counting. Es decir, mantiene el número de referencias a la instancia, y cuando llega a cero, la memoria usada por la instancia es reclamada, y cualquier objeto referenciado por la instancia decrementa su contador en uno.

Sin embargo, cuando hay que liberar algún otro espacio o recurso en la destrucción, a mejor práctica es unas un context manager. Usando el módulo `contextlib` podemos crear un custom context manager.

## Multiple inheritance

Python permite la herencia múltiple. `class A(B,C,D):`.

```python
class E:

class F:

class G:

class D(G):

class C:

class B(E,F):

class A(B,C,D):
```

La situación se complica si alguna de las clases de las que se hereda comparten nombres de métodos, porque Python debe decidir cuál es el método a seleccionar.

La respuesta está en el orden en el que Python busca cuando no encuentra el método en la clase original en la que se invocó el método.

Mirará de izquierda a derecha sobre las clases base de la clase original, pero siempre mirará sobre todas las clases ancestras de una clase antes de mirar la siguiente a la derecha.

Si tenemos `a` como instancia de la clase A, y ejecutamos `a.f()`:
* Python mirara en A.
* B.
* E.
* F. Ahí encontrará el método.


# 17. Data types as objects

Python tiene tipado dinámico, es decir, los tipos se determinan en runtime, no compile time.

## Types are objects, too

```python
>>> type(5)
<class 'int'>
>>> type(['hello','goodbye'])
<class 'list'>
```

La función `type` devuelve el tipo del objeto. Esta función devuelve un type object, un objeto de tipo type.

## Using types

Esta función se puede usar para proveer de type checking. Podemos por ejemplo comparar tipos:

```python
>>> type("Hello") == type(5)
False
```

## Types and user-defined classes

```python
>>> class A:
      pass

>>> class B(A):
      pass
```

```python
>>> b = B()
>>> type(b)
<class '__main__.B'>
```

Se puede obtener la misma información accediendo al atributo `__class__`:

```python
>>> b.__class__
<class '__main__.B'>

>>> b_class = b.__class__
>>> b_class == B
True

>>> b_class.__name__
'B'

>>> b_class.__bases__
(<class '__main__.A'>,)
```

Sin embargo, hay una forma más user friendly de obtener esta misma información: usando `isinstance` y `issubclass`.

```python
>>> class C:
      pass

>>> class D:
      pass

>>> class E(D):
      pass

>>> x = 12
>>> c = C()
>>> d = D()
>>> e = E()

>>> isinstance(x,E)
False
>>> isinstance(e,E)
True
>>> isinstance(e,D)
True
>>> isinstance(d,E)
False
>>> y = 12
>>> isinstance(y, type(5))
```

La función `issubclass` sirve solo para class types:

```python
>>> issubclass(C,D)
False
>>> issubclass(E,D)
True
>>> issubclass(e.__class__,D)
True
```

## Duck typing

Es la forma en la que Python determina si un objeto es de un tipo requerido para una operación, enfocando en su interfaz más que en su tipo.

## What is a special method attribute?
"Special method attribute" es un atributo de una clase Python con un significado especial. Se define como un método pero no se usa como tal.

Los métodos especiales normalmente no se invocan directamente, sino que son llamados automáticamente por Python en respuesta a un requerimiento sobre un objecto de esa clase.

El ejemplo más sencillo es `__str__`. Si se define en la clase, en cualquier momento en el que Python necesite una representación de la instancia mediante un string "user-friendly", se invocará el método `__str__`.

```python
class Color:
  def __init__(self, red, green, blue):
    self._red = red
    self._green = green
    self._blue = blue
  def __str__(self):
    return "Color: R={0:d}, G={1:d}, B={2:d}".format (self._red, self._green, self._blue)
```

## Making an object behave like a list

El problema de ejemplo es un fichero de texto que contiene registros de personas. Cada registro es una línea que contiene el nombre, edad y residencia de una persona, separados por ::.

Imagina que necesitamos información sobre las edades de la gente del fichero. Hay varias maneras de procesarlo:

```python
fileobject = open(filename, 'r')
lines = fileobject.readlines()
fileobject.close()
for line in lines:
. . . do whatever . . .
```

Esta técnica funcionaría, pero va a leer el fichero entero de una sola vez en memoria. Si el fichero es demasiado grande, el programa no funcionará.

```python
fileobject = open(filename, 'r')
for line in fileobject:
. . . do whatever . . .
fileobject.close()
```
Esto soluciona el problema de tener poca memoria, porque leerá una línea cada vez. Pero imagina que solo queremos los dos primeros campos (nombre y edad). Necesitaremos algo que pueda tratar el texto como una lista de líneas, pero sin leer el fichero entero de una vez.

## The __getitem__ special method attribute

Una solución es usar el método especial `__getitem__`, que permite a las instancias de esa clase responder a sintaxis de acceso a listado.

Si la clase `AClass` define `__getitem__`, y `obj` es una instancia de esa clase, se pueden hacer cosas como `x = obj[n]` o `for x in obj:`. Es decir, se puede usar `obj` como si fuera una lista.

```python
class LineReader:
  def __init__(self,filename):
    self.fileobject = open(filename, 'r')
  def __getitem__(self,index):
    line = self.fileobject.readline()
    if line == "";
      self.fileobject.close()
      raise IndexError
    
    else:
      return line.split("::")[:2]

for name, age in LineReader("filename"):
  ...do whatever...
```

### How it works

Todo objeto que define `__getitem__` como un método de instancia puede devolver elementos como si fuera una lista. Todos los accesos de la forma `object[i]` se transforman en `object.__getitem__(i)`.

La clase `LineReader` que hemos creado está pensada para usarse dentro de un bucle for, por lo que ignora el index de cada vez.

### Implementing full list functionality

Python tiene el método especial `__setitem__`, que da una forma de definir lo que hay que hacer cuando un objeto se usa como `obj[n] = val`.

## Giving an object full list capability

Python no tiene listas tipadas. Usando métodos especiales podemos crear una clase que se comporte como una lista tipada.

```python
class TypedList:
  def __init__(self, example_element, initial_list=[]):
    self.type = type(example_element)
    if not isinstance(initial_list, list):
      raise TypeError("Second argument of TypedList must be a list.")
    for element in initial_list:
      self.__check(element)
    self.elements = initial_list[:]
  def __check(self, element):
    if type(element) != self.type:
      raise TypeError("Attempted to add an element of incorrect type to a typed list.")
  def __setitem__(self, i, element):
    self.__check(element)
    self.elements[i] = element
  def __getitem__(self, i):
    return self.elements[i]
```

## Subclassing from built-in types

En la realidad, en vez de hacer el caso anterior, se suele hacer una subclase del tipo lista o `UserList`. 

### Subclassing list
(Ver ejemplos en el libro).

### Subclassing UserList
(Ver ejemplos en el libro).

## When to use special method attributes

