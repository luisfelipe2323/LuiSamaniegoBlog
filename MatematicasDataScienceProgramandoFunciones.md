### Librerías



```python
import matplotlib.pyplot as plt   # librería para graficar
import numpy as np                # librería para manejo de vectores y utilidades matemáticas
```

# Funciones algebraicas

### Función lineal

Tiene la forma de $$f(x)=mx + b$$ donde $m$ y $b$  $\in R$. 

$m$ puede ser calculada por: $$m=\frac{y_{2}-y_{1}}{x_{2}-x_{1}}$$

y $b$ es el punto de corte con el eje $y$. Su dominio es $Dom_{f} = (-\infty, \infty)$. Su imagen es $Im_{f} = (-\infty, \infty)$





```python
N = 100 # número de puntos

def f(m,x,b):
  return m*x + b


m = (7-6)/(3-2)

x = np.linspace(-10.0, 10.0, num=N)

b = 10

y = f(m,x,b)


fig, ax = plt.subplots()
ax.plot(x, y)
ax.grid()
ax.axhline(y=0, color='r')
ax.axvline(x=0, color='r')
```




    <matplotlib.lines.Line2D at 0x7f3f74645e80>




    
![png](output_4_1.png)
    


### Función Polinómicas

Tiene la forma de $$P(x)=a_{n}x^{n} + a_{n-1}x^{n-1}+...+a_{2}x^{2}+a_{1}x + a_{1}$$

a una función que tiene esta forma se le llama polinomio de grado $n$. A los elementos $a$ los llamaremoc coeficientes donde $a \in R$. 

**Por ejemplo:**

$$P(x)= 2x^{7} - x^{4} + 3x^{2} + 4$$

que es un polinómio de grado 7.


### Funciones potencia

Hay unas funciones que son un caso particular de las funciones polinómicas que son las funciones potencia, las cuales tienen la forma:


$$f(x)= x^{a}, a \in R$$ 


**Por ejemplo:**

$$f(x)= x^{2}$$

El dominio de $f(x)=x^{2}$ es $Dom_{f} = (-\infty, \infty)$. Su imagen es $Im_{f} = [0, \infty)$






```python
def f(x):
  return 2*x**7 - x**4 + 3*x**2 + 4

x = np.linspace(-100.0, 100.0, num=N)

y = f(x)

fig, ax = plt.subplots()
ax.plot(x, y)
ax.grid()
ax.axhline(y=0, color='r')
ax.axvline(x=0, color='r')
```




    <matplotlib.lines.Line2D at 0x7fc529f34d30>




    
![png](output_6_1.png)
    


# Funciones trascendentes

Son funciones que no pueden ser expresadas con polinomios. 

### Funciones trigonométricas

Algunos ejemplos son las funciones $cos(x)$, $sen(x)$ y $tan(x)$


```python
from math import pi

def f(x):
  return np.sin(x)

x = np.linspace(-2*pi, 2*pi, N)

y = f(x)

fig, ax = plt.subplots()
ax.plot(x, y)
ax.grid()
ax.axhline(y=0, color='r')
ax.axvline(x=0, color='r')
```




    <matplotlib.lines.Line2D at 0x7fc529a5b7b8>




    
![png](output_9_1.png)
    


### Función exponencial

Tienen la forma de $$f(x)=a^x$$ donde la base $a$ es una constante positiva. Un gran ejemplo de una función exponencial es usando la base como el número de euler:

$$f(x)=e^x$$


```python
def f(x):
  return np.e**x

x = np.linspace(-1, 1, num=100000)

y = f(x)

delta = 0.01

fig, ax = plt.subplots()
ax.plot(x, y)
ax.grid()
ax.set_ylim(1 - delta,1 + delta)
ax.set_xlim(0 - delta, 0 + delta)
ax.axhline(y=0, color='r')
ax.axvline(x=0, color='r')
```




    <matplotlib.lines.Line2D at 0x7fc529798be0>




    
![png](output_11_1.png)
    


### Función logaritmo

El logaritmo está definido por la **realación**:

$$log_{b}(x) = n \Longleftrightarrow x=b^n$$ 

donde: 



*   $b$ es la base.
*   $n$ es el exponente al que está elevado la base.
*   $x$ es el resultado de elevar la base $b$ al exponente $n$

**Ejemplo:**

Teniendo b=2 y n=8, entonces:

$$2^8=256$$

Por lo que $x=256$. Calculando el logaritmo base 2 de $x$ es:

$$log_{2}(256) = 8$$






```python
# utilidad en los decibelios

def f(x):
  return np.log10(x)

x = np.linspace(0.01, 1000, num=N)

y = f(x)

fig, ax = plt.subplots()
ax.plot(x, y)
ax.grid()
ax.axhline(y=0, color='r')
ax.axvline(x=0, color='r')
```




    <matplotlib.lines.Line2D at 0x7fc5298435c0>




    
![png](output_13_1.png)
    


# Función seccionada

Son funciones que tienen diferentes valores definidos por un intervalo. Por ejemplo la función escalón de Heaviside: 

$$H(x) = 
     \begin{cases}
        0, &\quad \text{para, } x < 0 \\
        1,  &\quad\text{para. } x \ge 0 \\
     \end{cases}
$$


```python
def H(X):
  Y = np.zeros(len(X))
  for idx,x in enumerate(X):
    if x>=0:
      Y[idx] = 1.0
  return Y

# Datos para graficación

N = 1000

X = np.linspace(-1,1, num=N)

y = H(X)

fig, ax = plt.subplots()
ax.plot(X, y)
ax.grid()
```


    
![png](output_15_0.png)
    

