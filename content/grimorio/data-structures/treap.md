---
title: Treap
tags:
  - data-structures
alias:
  - árbol de búsqueda binaria aleatorio
  - árbol de búsqueda aleatorizado
  - tree heap
  - randomized binary search tree
---
## 1. Qué es y cómo funciona

### Intuición
Un Treap puede pensarse como un archivador de fichas de alumnos. Cada ficha tiene un **legajo** y un número de **suerte** asignado al azar. El legajo indica dónde guardarla, dejando los menores a la izquierda y los mayores, a la derecha. El número de suerte decide qué ficha queda más arriba en el archivador.

De la misma forma, el Treap conserva los datos ordenados por su **clave** (los legajos), pero usa las **prioridades aleatorias** (suerte) para evitar que el archivador se convierta en una fila larga cuando los legajos llegan ordenados. Esto evita que el orden de llegada determine directamente la forma del árbol.

### Definición / propiedades

Un **Treap** es un árbol binario donde cada nodo guarda una **clave**, un valor asociado y una **prioridad** aleatoria. Debe cumplir dos invariantes:

- **Propiedad de BST (árbol binario de búsqueda):** las claves menores quedan en el subárbol izquierdo y las mayores, en el derecho.
- **Propiedad de heap máximo:** la prioridad de cada nodo es mayor o igual que la de sus hijos.

### Representación

Cada nodo contiene una clave, una prioridad y dos referencias: hijo izquierdo e hijo derecho. La raíz tiene la prioridad más alta; hacia abajo, las prioridades disminuyen. Al mismo tiempo, las claves menores quedan a la izquierda y las mayores, a la derecha.

![Representación de un Treap](/attachments/grimorio/data-structures/treap.svg)

## 2. Operaciones y complejidad

### Operaciones principales
- `op1(x)` qué hace
- `op2()` qué hace
- `op3(k)` qué hace

### Complejidad
- `op1`: $O(\log n)$ promedio, $O(n)$ peor caso
- `op2`: $O(1)$
- Espacio: $O(n)$

> **Nota:** aclarar acá si alguna complejidad es amortizada o esperada, y bajo qué supuesto.

### Detalles operativos
- Comportamiento en estructura vacía / llena
- Duplicados: se permiten o no, y qué pasa si se insertan
- Costos ocultos: reallocs, rehash, recorridos, copias

## 3. Implementación

### Idea de implementación
Estrategia típica y algoritmos clave, en prosa. Los pasos principales de la
operación más interesante (la que define la estructura).

### Invariantes
- Qué debe garantizar el código después de cada operación
- Condiciones sobre punteros / tamaños / orden

### Ejemplo de código

```python
class NombreEstructura:
    def __init__(self):
        ...

    def op1(self, x):
        ...
```

Uso típico con entrada y salida esperada:

```python
e = NombreEstructura()
e.op1(3)
print(e.op2())  # -> 3
```

## 4. Uso y criterio

### Casos de uso
- Problema concreto 1
- Problema concreto 2

### Cuándo NO usarlo
- Escenario donde parece adecuada pero es contraproducente, y por qué

### Comparaciones
Comparación explícita contra al menos una alternativa: [[hash table]] frente a
esta estructura, cuándo elegir cada una y con qué criterio.

### Ventajas / desventajas
- **Ventaja:** ...
- **Desventaja:** ...

### Señales de reconocimiento
- Pista en el enunciado que indica que esta estructura es la adecuada
- Otra pista

## 5. Relaciones y extensiones

### Variantes
- Variante 1 y qué mejora
- Variante 2 y qué mejora

### Relación con otras estructuras
- Cómo se combina o de qué depende conceptualmente
- Enlazar acá también: [[deque]], [[set]]

### Notas avanzadas

#### Persistencia
...

#### Concurrencia
...

## 6. Referencias y recursos
- [[COR2011]] - Chapter X.Y Título del capítulo
- [Título del recurso](https://ejemplo.com)
- Visualización interactiva: [nombre](https://ejemplo.com)
