TP2: Metropolis-Hastings

Metropolis-Hastings en 1D

El algoritmo de Metropolis-Hastings (MH) permite generar muestras (pseudo-)aleatorias a partir de una distribución de probabilidad P
que no necesariamente pertence a una familia de distribuciones conocida. El único requisito es que se pueda evaluar la función de 
densidad (o de masa de probabilidad) p*(theta) en cualquier valor de theta, incluso cuando p*(theta)  sea impropia (es decir, 
incluso aunque sea desconocida la constante de normalización que hace que la integral en el soporte de la función sea igual a uno).

1.Escriba una función que implemente el algoritmo de Metropolis-Hastings para tomar muestras de una distribución de probabilidad 
unidimensional a partir de su función de densidad. Separe en funciones cada uno de los pasos del procedimiento. Otorgue flexibilidad 
al algoritmo permitiendo elegir entre un punto de inicio arbitrario o al azar y utilizar distribuciones de propuesta de transición 
arbitrarias (por defecto, se utiliza una distribución normal estándar).

Distribución de Kumaraswamy

La distribución de Kumaraswamy es una distribución de probabilidad continua que se utiliza para modelar variables aleatorias con soporte 
en el intervalo (0,1). Si bien graficamente la forma de su función de densidad puede hacernos recordar a la distribución beta, vale 
mencionar que la distribución de Kumaraswamy resulta en una expresión matemática cuyo cómputo es más sencillo:

p(x|a,b)=abx^(a-1)(1-x^a)^(b-1)     a,b>0

2.Grafique la función de densidad de la distribución de Kumaraswamy para 5 combinaciones de los parámetros a y b que crea convenientes. 
Concluya sobre la utilidad que puede tener en la estadística bayesiana.

3.Utilizando la función construida en el punto 1, obtenga 5000 muestras de una distribución de Kumaraswamy con parámetros a=6 y b=2. 
Utilice una distribución de propuesta beta. Tenga en cuenta que la misma se puede parametrizar según media mu=alpha/(alpha+beta)  y 
concentración k=alpha+beta.

Compare las cadenas obtenidas al utilizar tres grados de concentración distintos en la distribución de propuesta. Calcule la tasa de 
aceptación. Compare utilizando histogramas y funciones de autocorrelación (puede utilizar la función acf o escribir una función propia).
Para elegir el punto inicial del algoritmo de MH, obtenga un valor aleatorio de una distribución conocida que sea conveniente.

4.Utilizando cada una de las cadenas anteriores, compute la media de la distribución y los percentiles 5 y 95 de X y de logit(X).

Metropolis-Hastings en 2D

