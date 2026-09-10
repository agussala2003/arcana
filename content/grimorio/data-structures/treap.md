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
Todo se apoya en dos primitivas; el resto se expresa en términos de ellas.

- `split(T, x)` parte el treap en dos: uno con las claves $\le x$ y otro con las mayores
- `merge(T1, T2)` une dos treaps, bajo la precondición de que toda clave de `T1` sea menor que toda clave de `T2`
- `find(x)` busca una clave descendiendo por comparación, igual que en un [[binary search tree]]
- `insert(x)` genera una prioridad aleatoria, hace `split` por `x` y dos `merge` con el nodo nuevo
- `erase(x)` ubica el nodo y lo reemplaza por el `merge` de sus dos hijos
- `union(T1, T2)` combina dos treaps cualesquiera, sin la precondición de `merge`

### Complejidad
- `split`, `merge`, `find`, `insert`, `erase`: $O(\log n)$ esperado
- `union` sobre treaps de tamaños $m \le n$: $O(m \log(n/m))$ esperado
- `build` a partir de una lista ya ordenada: $O(n)$
- Espacio: $O(n)$, más $O(\log n)$ esperado de pila por la recursión

> **Nota:** las cotas son **esperadas**, no amortizadas ni de peor caso. El azar está en las prioridades, no en los datos: no existe una secuencia de entrada que degrade el treap, pero una tirada desafortunada puede producir un árbol de altura $O(n)$. La probabilidad es despreciable y se renueva en cada inserción.

### Detalles operativos
- Las claves son únicas: insertar una repetida no crea un nodo nuevo. La prioridad no desempata claves.
- `merge` con la precondición violada rompe el orden de claves de forma silenciosa.
- Prioridades repetidas no invalidan la estructura, pero degradan la cota si el generador tiene poco rango.
- Costo oculto: cada nodo guarda dos punteros y dos enteros, y los nodos están dispersos en memoria.

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

-   **Conjuntos dinámicos ordenados:** permite mantener elementos ordenados mientras se realizan inserciones, búsquedas y eliminaciones de forma eficiente, con costo esperado **O(log n)**.
-   **Consultas sobre rangos:**  permite localizar los límites de un intervalo y recorrer los elementos comprendidos entre ellos de manera eficiente.
- **División y combinación de conjuntos ordenados:** permite separar eficientemente un conjunto según una clave o unir dos conjuntos compatibles gracias a las operaciones `split` y `merge`, facilitando la manipulación de subconjuntos completos sin procesar cada elemento individualmente.


### Cuándo NO usarlo

-   **Cuando no importa mantener los datos ordenados:** si solo se necesita buscar elementos por clave, el orden del Treap no aporta ningún beneficio.
-   **Cuando los datos casi no cambian:** la complejidad y sobrecarga de mantener un árbol con prioridades y punteros no se justifica. 
-   **Cuando se necesita garantizar un rendimiento O(log n) en el peor caso:** el Treap ofrece esta complejidad solo en promedio. Una combinación poco favorable de prioridades puede hacer que el árbol quede muy desbalanceado, empeorando su rendimiento hasta **O(n)**.

  

### Comparaciones

-   **vs Hash Table:** ofrece búsqueda, inserción y eliminación en **O(1) promedio**, pero no mantiene los elementos ordenados. Conviene cuando el orden no importa, pero usamos un Treap cuando necesitamos conservar el orden o realizar recorridos y consultas por rango.
- **vs BST simple:** ambos mantienen los datos ordenados, pero un BST simple puede quedar muy desbalanceado según el orden en que se insertan los elementos, haciendo que sus operaciones empeoren hasta **O(n)**. Lo usamos cuando no es necesario garantizar un buen rendimiento ante cualquier orden de inserción, y usamos un Treap cuando necesitamos mantener una altura esperada de **O(log n)**.

  

### Ventajas / desventajas

  **Ventajas:**
   -   Mantiene los datos ordenados mientras permite inserciones, búsquedas y eliminaciones eficientes.
-   Implementación relativamente simple frente a otros árboles balanceados.
-   Soporta `split` y `merge` eficientemente, facilitando operaciones sobre conjuntos completos.
-   No depende del orden de inserción para obtener un buen rendimiento esperado. 

**Desventajas:** 
-   No garantiza O(log n) en el peor caso.
-   Puede quedar desbalanceado en casos poco probables.
-   Consume más memoria que estructuras simples.
-   Depende de una buena generación de prioridades aleatorias para mantener su rendimiento esperado.
  

### Señales de reconocimiento

-    _“El sistema debe registrar nuevos elementos y eliminar existentes constantemente, manteniéndolos siempre ordenados.”_
-   _“Los datos pueden llegar en cualquier orden, y se requiere realizar búsquedas de forma eficiente.”_
-   _“El sistema debe consultar frecuentemente los elementos comprendidos entre dos valores determinados.”_
-   _“Se requiere dividir un conjunto de elementos según una clave y posteriormente combinar conjuntos ya ordenados.”_

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
