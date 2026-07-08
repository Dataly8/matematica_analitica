# Linear Algebra: Purchase Recommendation
*[Versión en español abajo](#versión-en-español) · Read in English below*

Applying matrix multiplication to a real decision problem: **which store minimizes each customer's total spend?**

## Problem

Three customers (Rafa, Pedro, María) each need different quantities of four bakery products (palmeras, donuts, hojaldres, tartas). Two stores — Manolo Bakes and Starbucks — offer different prices for each product. The goal is to compute how much each customer would spend at each store and recommend the cheaper option.

## Approach

The problem maps naturally onto a matrix product:

- **Matrix A** (3×4): quantity of each product per customer.
- **Matrix B** (4×2): price of each product at each store.
- **A · B** (3×2): total spend per customer at each store.

```python
resultado = A @ B
```

The resulting matrix is loaded into a pandas DataFrame (customers as rows, stores as columns). For each customer, `idxmin()` returns the store with the lowest total spend and `min()` the amount, producing an automated recommendation.

## Key results

- **Rafa → Starbucks** (saves 1 €).
- **Pedro → Manolo Bakes** (saves 2.5 €). The difference is driven by tartas: Pedro buys two, and they are more expensive at Starbucks.
- **María → tie** (same spend at both). Recommendation falls back to non-price criteria (product quality, convenience).

## Why this matters

The exercise shows how a core linear algebra operation — the matrix product — encodes a "quantities × prices" business calculation, and how the raw numeric output becomes an actionable recommendation once framed correctly. The tie case is a reminder that when the data doesn't decide, the analyst still has to.

## Tools

Python · NumPy · pandas

## Context

Deliverable for the *Mathematics for Data Processing* module of my Master's in Business Intelligence & Analytics. Notebook and write-up are in Spanish.

_________________________________________________________________________________________________________________________________________________________________

## Versión en español

# matematica_analitica
Caso práctico de álgebra lineal aplicada: cálculo de gasto y recomendación de compra mediante producto de matrices en Python.

# Entrega: Aplicaciones del producto de matrices

Ejercicio del módulo *Matemáticas y estadística en el tratamiento de datos*.
Aplica el producto de matrices a un caso práctico de recomendación de compra.

## Problema

Tres personas (Rafa, Pedro y María) quieren comprar cuatro productos y pueden
elegir entre dos tiendas con precios distintos. El objetivo es calcular cuánto
gastaría cada persona en cada tienda y recomendar a cada una dónde comprar.

## Enfoque

El cálculo se resuelve como un **producto de matrices**:

- Matriz de **cantidades** (personas × productos), de dimensión 3×4.
- Matriz de **precios** (productos × tiendas), de dimensión 4×2.
- Su producto genera la matriz de **gasto** (personas × tiendas), de dimensión 3×2.

Cada celda del resultado combina, en una sola operación, la compra de una persona
con los precios de una tienda: cruza dos fuentes de datos y agrega el gasto total.

## Contenido del repositorio

- `sprint1_producto_matrices.ipynb`: notebook con el desarrollo completo
  (construcción de matrices, producto, presentación en tabla y recomendación).

## Herramientas

- Python (NumPy y pandas)
- Google Colab

## Conclusiones

- **Rafa** → Starbucks (49,0 €).
- **Pedro** → Manolo Bakes (58,5 €); las tartas son su factor diferencial.
- **María** → empate (43,5 € en ambas): el precio no decide, la recomendación
  pasa a basarse en calidad o conveniencia.

El caso de María ilustra que el dato ofrece la respuesta, pero la interpretación
aporta el criterio: un empate numérico requiere razonar más allá del precio.
