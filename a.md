# Markdown
## Subtitulo 1
### Subtitulo 2
* **Documentación en Github**
* Ecuaciones!
    * En Notebook de python
* Viñeta 1
* Viñeta 2
# Documentar en lenguaje de *programación*
``` python
def suma(x1:int, x2:int):
    return x1 + x2
```

``` matlab
function y = suma(x1, x2)
    y = x1+ x2;
```
# Micelánea
* Cambia distribución de teclado
windows + spacio

# Redacción de ecuaciones en Markdown 
Comando para previsualizar: ctrl+shift+v

# Ejemplo
Fórmula para calcular las raices de la ecuación cuadrática. 
$x_1= (-b + \sqrt{b^2 -4ac})/2a $

$x_1= \frac{-b + \sqrt{b^2 -4ac}}{2a} $

$x_2= \frac{-b - \sqrt{b^2 -4ac}}{2a} $

$\pi,\alpha,\beta, \hat{y}, \leftarrow$

# Ejercicio
Escribir la ecuación Navier Stokes.

$\rho \partial$
$\rho \delta$

$\rho  \frac{ D \overrightarrow{V}}{Dt} = $

$\sum_{i}^{4} $

Hay que subirlo al taller.

**Ecuación Navier Stokes**
$\rho \frac{D \overrightarrow{V}}{Dt} = $
$\nabla p + \mu \nabla^2 \overrightarrow{V} + \rho \overrightarrow{g} $


# Taller!
* Se debe presentar:
    * Notebook
    * Enlace al repositorio

## Ejercicio 1
La sumatoria $1 + 1/2 + 1/4 +1/8 ... $ tal que el error absoluto $e_{abs} < 10^{-1}$.

``` python
# Valor real conocido
v_real = 2.0

# Umbral del error absoluto deseado
error_deseado = 1e-1

# Inicialización
SUM = 0.0
term = 1.0   # Primer término de la serie
i = 0

print("Iteración |   término   |    SUM     |   e_abs")
print("-----------------------------------------------")

# Genera términos hasta alcanzar la precisión deseada
while True:
    i += 1
    SUM += term
    e_abs = abs(v_real - SUM)

    # Muestra los valores intermedios
    print(f"{i:9d} | {term:10.4f} | {SUM:9.4f} | {e_abs:7.4f}")

    if e_abs < error_deseado:
        break

    # El siguiente término es la mitad del actual (más eficiente que 1/(2**i))
    term *= 0.5

# Muetra los resultados
print("\n========= RESULTADOS =========")
print(f"Número de términos (N): {i}")
print(f"Suma aproximada (SUM): {SUM:.4f}")
print(f"Error absoluto (e_abs): {e_abs:.4f}")
print("===============================")
```

## Ejercicio 2 (Bubble sort)
![XSDF](.\E2.png) -->

### Corrida de escritorio
$v_1=[3, 2, 5, 8, 4, 1]$

| i | Vector |
| -- | -- |
| 0 | $ [3, 2, 5, 8, 4, 1] $ |
| 1 | $ [3, 2, 5, 4, 1, 8] $|
| 2 | $ [3, 2, 4, 1, 5, 8] $|
| 3 | $ [3, 2, 1, 4, 5, 8] $|
...

Resultado final:

$v_{sorted} = [1,2,3,4,5,8]$

``` python
# Ejercicio 2.1 (v1)
v1 = [3, 2, 5, 8, 4, 1]
n = len(v1)

print("VECTOR ORIGINAL:", v1)

for i in range(n):
    swapped = False
    print(f"\nIteración {i+1}:")
    for j in range(1, n - i):
        print(f"  Comparando {v1[j-1]} y {v1[j]}", end=" → ")
        if v1[j] < v1[j - 1]:
            v1[j], v1[j - 1] = v1[j - 1], v1[j]
            swapped = True
            print("Intercambio →", v1)
        else:
            print("Sin cambio")
    if not swapped:
        print("  No hubo intercambios, el arreglo ya está ordenado.")
        break

print("\nVECTOR ORDENADO:", v1)
```

Casos de prueba:
* $v_2=[-1, 0, 4, 5, 6, 7]$

``` python
# Ejercicio 2.2 (v2)
v2 = [-1, 0, 4, 5, 6, 7]
n = len(v2)

print("VECTOR ORIGINAL:", v2)

for i in range(n):
    swapped = False
    print(f"\nIteración {i+1}:")
    for j in range(1, n - i):
        print(f"  Comparando {v2[j-1]} y {v2[j]}", end=" → ")
        if v2[j] < v2[j - 1]:
            v2[j], v2[j - 1] = v2[j - 1], v2[j]
            swapped = True
            print("Intercambio →", v2)
        else:
            print("Sin cambio")
    if not swapped:
        print("  No hubo intercambios, el arreglo ya está ordenado.")
        break

print("\nVECTOR ORDENADO:", v2)
```

* $v_3$ 100_000 número aleatorios entre -200 y 145.
``` python
# Ejercicio 2.3 (v3)
import random
import time

# Generar 100,000 números aleatorios entre -200 y 145
v3 = [random.randint(-200, 145) for _ in range(100_000)]
n = len(v3)

print("VECTOR ORIGINAL (primeros 10 elementos):", v3[:10])

inicio = time.time()
for i in range(n):
    swapped = False
    # Solo mostrar las primeras 10 iteraciones completas
    if i < 10:
        print(f"\nIteración {i+1}:")
    for j in range(1, n - i):
        if v3[j] < v3[j - 1]:
            v3[j], v3[j - 1] = v3[j - 1], v3[j]
            swapped = True
        # Mostrar solo comparaciones de las primeras 10 iteraciones y los primeros 10 elementos
        if i < 10 and j < 10:
            print(f"  Comparando índices {j-1} y {j}: {v3[j-1]} <-> {v3[j]}")
    if not swapped:
        if i < 10:
            print("  No hubo intercambios, el arreglo ya está ordenado.")
        break
fin = time.time()

print(f"\nTiempo total de ejecución: {fin - inicio:.2f} segundos")
print("Primeros 10 elementos ordenados:", v3[:10])
print("Últimos 10 elementos ordenados:", v3[-10:])
```

# Algoritmo 3
![XSDF](.\fibonacci.png)

| n | fib(n) |
| -- | -- |
| 0 | 0 |
| 1 | 1 |
| 2 | 1 |
| 3 | 2 |
| 4 | 3 |
| 5 | 5 |
| 6 | 8 |
| 6 | 13 |
| ... | ... |
|$n = 11 $ | ? |
|$n = 84 $ | ? |
|$n = 1531$ | ? |

``` python
def fibonacci_iterativo(n):
    if n == 0:
        return 0
    
    x = 0
    y = 1

    for i in range(1, n):
        z = x + y
        x = y
        y = z

    return y

# Pruebas:
for n in [11, 84, 1531]:
    print(f"fib({n}) = {fibonacci_iterativo(n)}")
```

## Graficar!
* El valor de la serie $fib(n)$
* El valor del cociente 

    $\phi \rightarrow \frac{fib(n)} {fib(n-1)} \approx 1.618$ número áureo.


| n | $ fib(n) /fib(n-1) $ |
| -- | -- |
| 2 | $1/1=1 $ |
| 3 | $2/1 = 2$ |
| 4 | $3/2 = 1.5$ |
| 5 | $5/3= 1.66667$ |
| 6 | $8/5= 1.6$ |
| 7 | $13/8 = 1.625 $ |
| 8 | $21/13 = 1.615 $ |
| ... | ... |
|$\infty $ | $ \frac{1 + \sqrt{5}} {2} \approx 1.618$ (número áureo) |

``` python
import matplotlib.pyplot as plt

# Función para generar la serie Fibonacci hasta n términos
def fibonacci(n):
    fib = [0, 1]  # valores iniciales
    for i in range(2, n):
        fib.append(fib[-1] + fib[-2])
    return fib

# Número de términos
n = 20
fib_series = fibonacci(n)

# Calcular los cocientes fib(n)/fib(n-1)
ratios = [fib_series[i] / fib_series[i - 1] for i in range(2, n)]

# Valor teórico del número áureo
phi = (1 + 5 ** 0.5) / 2

# === Gráficos ===

# 1️ Gráfico de la serie Fibonacci
plt.figure(figsize=(10, 4))
plt.plot(range(n), fib_series, marker='o', label='fib(n)')
plt.title("Serie Fibonacci")
plt.xlabel("n")
plt.ylabel("fib(n)")
plt.grid(True)
plt.legend()
plt.show()

# 2️ Gráfico del cociente fib(n)/fib(n-1)
plt.figure(figsize=(10, 4))
plt.plot(range(2, n), ratios, marker='o', label='fib(n)/fib(n-1)')
plt.axhline(y=phi, color='r', linestyle='--', label=f'Número áureo φ ≈ {phi:.5f}')
plt.title("Cociente entre términos consecutivos de Fibonacci")
plt.xlabel("n")
plt.ylabel("fib(n)/fib(n-1)")
plt.grid(True)
plt.legend()
plt.show()
```

# Breve revisión *git*
* Inicializar repositorio
``` bash
git init 
```
* ¿Qué significa la U?
    * No están añadidos
    * Se añaden con
    ``` bash
    git add file1 file2... 
    ```
    * Nunca!  Añade **TODO**!
    ``` bash
    git add . 
    ```
    * git commit
    ``` bash
    git commit -m "actualización de código" 
    ```
# Modificación del Algoritmo 2
Modifique el Algoritmo 02 y determine el número de comparaciones realizadas al ordenar la serie 5, 4, 3, 2, 1
``` python
v1 = [3, 2, 5, 4, 1]
n = len(v1)
comparaciones = 0  # Contador de comparaciones

print("VECTOR ORIGINAL:", v1)

for i in range(n):
    swapped = False
    print(f"\nIteración {i+1}:")
    for j in range(1, n - i):
        comparaciones += 1  # Se realiza una comparación
        print(f"  Comparando {v1[j-1]} y {v1[j]}", end=" → ")
        if v1[j] < v1[j - 1]:
            v1[j], v1[j - 1] = v1[j - 1], v1[j]
            swapped = True
            print("Intercambio →", v1)
        else:
            print("Sin cambio")
    if not swapped:
        print("  No hubo intercambios, el arreglo ya está ordenado.")
        break

print("\nVECTOR ORDENADO:", v1)
print("Número de comparaciones realizadas:", comparaciones)
```
# Usando el Algoritmo 03 y la aritmética de redondeo con 3 cifras
Determine la iteración desde la cual el error relativo de $\frac{y_{i-1}}{y_i} \quad (i > 0) $ con respecto a $\frac{1 + \sqrt{5}} {2} $ está dentro de $10^{-5} $
``` python
def FL_rounding(x, digits=3):
    """Redondeo a 'digits' cifras significativas para float"""
    if x == 0:
        return 0.0
    else:
        import math
        return round(x, digits - int(math.floor(math.log10(abs(x)))) - 1)

def fibonacci_iterativo_FL_seguro(n, digits=3):
    """Fibonacci iterativo usando FL_rounding solo para la razón"""
    if n == 0:
        return 0, None, None
    x = 0  # enteros grandes
    y = 1
    phi = (1 + 5**0.5)/2
    iteracion_error = None
    ratio = None

    for i in range(1, n+1):
        z = x + y
        x = y
        y = z
        if i > 1:
            # convertimos a float para calcular la razón y redondear
            ratio_float = y / x
            ratio = FL_rounding(ratio_float, digits)
            error = abs(phi - ratio) / phi
            if iteracion_error is None and error < 1e-5:
                iteracion_error = i
    return y, ratio, iteracion_error

# Valores de n que queremos probar
valores_n = [11, 84, 1531]

print("n | fib(n) | ratio y_i/y_{i-1} | iteración error < 1e-5")
print("---|--------|-----------------|-----------------------")
for n in valores_n:
    fib_n, ratio, iter_error = fibonacci_iterativo_FL_seguro(n, digits=3)
    print(f"{n} | {fib_n} | {ratio} | {iter_error}")
```
# Algoritmo 4
Implemente la serie geométrica $\sum_{n=1}^{inf} $ $\frac{1}{n} $
A qué valor converge?
El Algoritmo 04 implementa la serie armónica, no converge: diverge y su suma tiende a +∞
``` python
import matplotlib.pyplot as plt

# Algoritmo 04 - Serie armónica con gráfica
# Suma parcial de 1 + 1/2 + 1/3 + ... + 1/n

# Número de términos
N = int(input("Ingrese el número de términos N: "))

suma = 0.0
valores = []  # Para guardar las sumas parciales

for n in range(1, N + 1):
    suma += 1 / n
    valores.append(suma)

# Mostrar el último valor
print(f"Suma parcial con N={N}: {suma:.6f}")

# Graficar la serie
plt.figure(figsize=(8, 5))
plt.plot(range(1, N + 1), valores, label='Suma parcial ∑(1/n)')
plt.title('Crecimiento de la Serie Armónica')
plt.xlabel('Número de términos (n)')
plt.ylabel('Valor acumulado')
plt.grid(True)
plt.legend()
plt.show()
```
**Link repositorio**
[github_TamyBenavidez]()