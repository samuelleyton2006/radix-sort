# radix-sort


Explicacion de el sistema de radix sort:

# Radix Sort: Algoritmo de Ordenamiento por Bases

Este repositorio contiene una implementación del **Radix Sort**, un algoritmo eficiente para ordenar números o cadenas basado en las posiciones de sus dígitos o caracteres. Este método es ampliamente utilizado debido a su capacidad para manejar grandes volúmenes de datos de forma rápida y escalable.

## ¿Qué es Radix Sort?

El **Radix Sort** organiza elementos agrupándolos en cubetas según el valor de sus dígitos, sin realizar comparaciones directas entre ellos. Se puede implementar usando dos enfoques:
- **LSD (Least Significant Digit)**: Ordena desde el dígito menos significativo al más significativo. Ideal para números enteros.
- **MSD (Most Significant Digit)**: Ordena desde el dígito más significativo al menos significativo. Útil para cadenas de caracteres.

## Principales Características

- **Complejidad Lineal**: Depende del número de elementos y de la longitud de los mismos.
- **Aplicaciones**:
  - Procesamiento de datos masivos (Big Data).
  - Ordenamiento eficiente en bases de datos y motores de búsqueda.
  - Criptografía y seguridad informática.

## Funcionamiento

1. Determinar el número máximo de dígitos en los elementos a ordenar.
2. Crear "cubetas" para cada posible valor de un dígito.
3. Iterar sobre cada dígito desde el menos significativo al más significativo:
   - Agrupar los elementos en cubetas según el valor del dígito actual.
   - Recopilar los elementos en orden para procesar el siguiente dígito.

## Ejemplo de Uso

Dado el conjunto `[345, 721, 425, 572, 836, 467, 672, 194, 365, 236, 891, 746, 431, 834, 247, 529, 216, 389]`, el Radix Sort los ordena en pasos según cada posición de dígito, resultando finalmente en:

```plaintext
[194, 216, 236, 247, 345, 365, 389, 425, 431, 467, 529, 572, 672, 721, 746, 834, 836, 891]

```

Ejemplo de implementacion en python : 

```python

def radix_sort(arr):
    max_num = max(arr)
    max_digits = len(str(max_num))
    place = 1

    while max_digits > 0:
        buckets = [[] for _ in range(10)]
        for num in arr:
            digit = (num // place) % 10
            buckets[digit].append(num)
        arr = []
        for bucket in buckets:
            arr.extend(bucket)
        place *= 10
        max_digits -= 1

    return arr


```
En este caso para el ejemplo de uso, se utilizaria :

```
numeros = [345, 721, 425, 572, 836, 467, 672, 194, 365, 236, 891, 746, 431, 834, 247, 529, 216, 389]
print("Original:", numeros)
print("Ordenados:", radix_sort(numeros))

