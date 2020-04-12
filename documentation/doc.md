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

(68)



