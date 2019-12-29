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


# 4. The absolute basics

# 5. Lists, tuples and sets
