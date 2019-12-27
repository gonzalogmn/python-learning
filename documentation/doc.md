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

# 4. The absolute basics

# 5. Lists, tuples and sets