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

Como veremos en esta sección del trabajo práctico, la verdadera utilidad del algoritmo de Metropolis-Hastings se aprecia cuando se obtienen muestras de distribuciones en más de una dimensión, incluso cuando no se conoce la constante de normalización. Paradójicamente, los ejemplos trabajados a continuación también serán los que nos permitirán advertir sus limitaciones y motivarán la búsqueda de mejores alternativas.

Normal multivariada

La distribución normal multivariada es la generalización de la distribución normal univariada a múltiples dimensiones (o mejor dicho, el caso en una dimensión es un caso particular de la distribución en múltiples dimensiones). La función de densidad de la distribución normal en k dimensiones es:

p(x|mu,sigma)=1/2pi^(k/2)det(sigma)^(1/2) exp ( -1/2 (x-mu)^T sigma^(-1) (x-mu) )

donde mu es el vector de medias y sigma la matriz de covarianza.

6.Escriba una función que implemente el algoritmo de Metropolis-Hastings para tomar muestras de una función de probabilidad bivariada dada. Separe en funciones cada una de los pasos del algoritmo. La probabilidad de salto será normal bivariada de matriz de covarianza variable (utilizar para ello la función rmvnorm del paquete {mvtnorm}). Otorgue flexibilidad al algoritmo haciendo que reciba como argumento la matriz de covarianza de la probabilidad de transición.

7. Utilice la función escrita en el punto anterior para obtenga muestras de una distribución normal bivariada con media mu* y matriz de covarianza sigma*. Determine una matriz de covarianza que crea conveniente para la distribución de propuesta. Justifique su decisión y valide la bondad del método mediante el uso de traceplots y las estadísticas que crea adecuadas.

mu*=[0.4,0.75]^T 

sigma*=|1.35,0.4|
       |0.4 ,2.4|

8.Estime las siguientes probabilidades utilizando las muestras obtenidas:

i)Pr(X_1>1,X_2<0)
ii)Pr(X_1>1,X_2>2)
iii)Pr(X_1>0.4,X_2>0.75)

Luego, calcule esas mismas probabilidades mediante algún método que crea conveniente (función de distribución, integración manual, integración numérica, monte carlo, etc.), y compare los resultados con los obtenidos en base a las muestras seleccionadas con MH y concluya.
