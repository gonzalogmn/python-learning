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

