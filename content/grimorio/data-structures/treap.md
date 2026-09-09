---
title: Treap
tags:
  - data-structures
alias:
  - nombre en español
  - sigla o alias común
---
## 1. Qué es y cómo funciona

### Intuición
Analogía cotidiana en una o dos oraciones: la idea simple detrás de la estructura.
Qué problema hace fácil o eficiente, y por qué las alternativas obvias no alcanzan.

### Definición / propiedades
- Invariante principal (la regla que siempre se cumple)
- Propiedad de orden / acotamiento / restricción sobre los elementos
- Qué garantiza y qué explícitamente NO garantiza

### Representación
![](/attachments/grimorio/data-structures/nombre-estructura.svg)

Descripción de la organización interna: nodos, punteros, arreglos, niveles.
Acá conviene mencionar sobre qué se apoya, enlazando a otras estructuras:
puede construirse sobre [[array]] o [[linked list]], y la elección importa porque...

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
