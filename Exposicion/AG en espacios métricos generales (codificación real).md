

2.1 (Cadenas Markov finitas) → 2.4 (Convergencia débil) → 3.1 (Límite campo medio) → 3.4 (Límite difuso) → 4.2 (Kernels de cruce) → 7.3 (AG en espacios métricos) → 7.1 (Gibbs) → 7.2 (Juegos evolutivos)

---
## Sobre Evolution strategies - A comprehensive introduction (como un resumen)
Tres fuentes de algoritmos evolutions, evolutionary algorithms (EA) se han mantenido y el interés en ellos ha aumentado en los últimos quince años:
- Evolutionary programming (EP)
- Genetic algorithms (GA)
	- Son métodos de optimización estocástica inspirados en la evolución natural. Operan sobre una población de individuos o soluciones candidatas que evoluciona mediante: Selección, cruce, mutación.
	- El proceso itera hasta encontrar una solución aceptable (óptimo global o aproximado)
- Evolution Strategies (ES)

### Experimental evolutionary optimization
En un principios ES no estaba pensado para computar minimos o máximos de *real-valued static functions with fiex numers of variables and without noise during their evaluation*


---

# "Espacios métricos generales"
En este contexto se refiere a que el espacio de genotipos no tiene por qué ser $\mathbb{R}^n$, podría ser:
- Espacios de Hilbert o de Banach
- Un espacio métrico con una distancia, pudiendo asi definir vecindades y convergencia
Asi se permite generalizar y extender los AG, donde las soluciones ahora podría ser curvas, superfices,...,

## ¿por qué no con Topología?
En resumen, la topología define la vecindad (qué puntos están cerca), pero la métrica define cuánto están de cerca, lo cual es crucial para guiar la búsqueda y analizar la convergencia.

Pero entonces podríamos debilitarle a estos espacios y buscar en semi métricas?, o como se llame

## Evolutionary computation I: Genetic Algorithms
*"The role of evolution in the study of biology and, more generally, the life sciences and demographics is paramount. Essentially, evolution acts as a type of natural optimization process based on the conceptually simple operations of competition, reproduction, and mutation. The term EC (sometimes called evolutionary algorithms) refers to a class of stochastic search and optimization methods built on the mathematical emulation of natural evolution."*
Aunque los AG son algoritmos de búsqueda generales, una aplicación principal (quizás la principal) es la búsqueda aplicada a la optimización de funciones.

Mientras que los algoritmos de recocido del Capítulo 8 se basan en analogías con el enfriamiento físico de sustancias, el AG se basa libremente en los principios de la evolución natural y la supervivencia del más apto. De hecho, en la terminología de los AG, un criterio de maximización equivalente, como —L(θ) (o su análogo basado en una forma codificada de θ), a menudo se denomina función de fitness para enfatizar el concepto evolutivo de que el más apto de una especie tiene una mayor probabilidad de sobrevivir y transmitir su material genético.

Una diferencia con los AG es que trabaja con un población de posibles soluciones o soluciones potenciales. En otros casos hay un candidato a la solución ($\widehat{\theta}_{k}$) para moverse al optimo, actualizando la estimación de éste
![[Pasted image 20260526170215.png]]



Con esta estructura basada en población en mente, los pasos fundamentales de un AG u otro algoritmo evolutivo pueden reducirse a:  
1. **Inicialización.**  
	Seleccionar un tamaño de población inicial y valores para los elementos de la población;  codificar los elementos de θ de una manera conveniente para las operaciones del algoritmo (por ejemplo, codificar en forma binaria).  
2. **Mezcla.** 
	Mezclar los elementos de la población actual según análogos algorítmicos de los principios de evolución y producir un nuevo conjunto de valores poblacionales.  
3. **Evaluación.** 
	Medir el rendimiento de los nuevos valores poblacionales y determinar si el algoritmo debe terminarse. Regresar al paso 1 si se requiere una mejora adicional y/o no se ha agotado el presupuesto de evaluaciones de la función.

> [!NOTE]
> La idea centrar en los AG es mover un conjunto de cromosomas (población), de una colección inicial de valores a un punto donde la función fitness es optima. El tamaño de la población (número de cromosomas en la población) se tomará como $N$


> [!warning]
> *"Unfortunately, some interest also appears to be due to a regrettable amount of “hype” and exaggerated claims. While GAs (and more generally, EC) are important tools within stochastic optimization, there appears to be no formal evidence of consistently superior performance —relative to other appropriate types of stochastic algorithms—in any broad, identifiable class of problems*"

#### ¿Diferencia práctica entre mejora y optimización?
La optimización a menudo se centra en la cuestión de la convergencia de un algoritmo, mientras que el sistema adaptativo de Holland enfatiza el comportamiento intermedio mientras el aprendizaje tiene lugar.


Imagina que tu AG evoluciona en $\mathbb{R}^n$ 
Puede haber **trayectorias patológicas** donde el algoritmo nunca converja al óptimo.  
Esas trayectorias forman un conjunto de medida cero.  
**Las ignoramos** porque la probabilidad de que ocurran es 0.

## Def (Espacio métrico)
Un espacio métrico es una pareja $(X,d)$ donde $X$ es un conjunto y $d$ es una métrica o función de distancia sobre $X$, es decir, las siguientes condiciones se satisfacen:
1) $\forall\, x,y \in X: \, d(x,y)\geq 0 \;$ y $\, d(x,y)=0 \iff x=y\;$ (definida positiva)
2) $\forall \, x,y \in X: \, d(x,y) = d(y,x)\;$ (simetría)
3) $\forall \, x,y,z \in X: \, d(x,z) \leq d(x,y) + d(y,z)\;$ (desigualdad del triángulo)

Todo espacio normado induce una métrica, es decir que todo espacio normado es métrico, pero lo contrario no es cierto. No todo espacio métrico es inducido por una norma
Para cualquier conjunto $X$, sea $d(x,x)=0$ y $d(x,y) = 1$ si $x \neq y \in X$

## Códificación binaria estandar

## Códificación estándar
Aqui no hay una codificación perse, ya que se trabaja con el valor directo de $\theta$ (?)


## ¿Qué hace a un problema difícil?
Para precisar: ¿qué hace a un problema de AG difícil?. Bueno, identificar qué aspectos de un problema AG lo vuelve difícil, es ya algo difícil en sí, sino podríamos plantear una siguiente pregunta que es, ¿qué hace que un problema sea adecuado para AG?

Sin embargo, aunque la conexión con la evolución natural podría sugerir que el AG es de alguna manera un algoritmo optimizado, esta línea de razonamiento parece equivocada al menos por tres razones: 
1. No hay evidencia de que la evolución natural sea un proceso optimizado para el desarrollo de las especies (¡es difícil ver cómo la cola de un pavo real puede ser el resultado de un proceso optimizado!)
2. Los teoremas de free lunch (Subsección 1.2.2 y Sección 10.6) garantizan que "en promedio" un AG no puede funcionar mejor que otros algoritmos 
3. Existen muchos estudios numéricos sobre problemas razonables donde otros métodos superan claramente a los AG.




## Teorema 10.1
A canonical GA with roulette wheel selection, $0 \leq P_{c} \leq 1,$ and $0< P_{m}<1$  does not converge in the sense that
$$
\lim_{ k \to \infty } P(\hat{L}_{\min,k} = L(\theta^{*}) \neq 1
$$
Comments on proof: The proof is given in Rudolph. The proof is based on Markov chains. The GA can be represented as a Markov chain with $2^{NB}$ states, each representing a possible population


### Example 10.1—Failure of convergence for a GA. 
Consider a very small scale canonical GA with $N = 2$ and $B = 3$. Let $P_{c} > 0$ and $P_{m}$ be negligibly small. The total number of possible populations is $2^{NB}= 64$ (i.e., at every iteration, the GA will produce one of these 64 populations). Among these 64 states are $2^{B}=8$ states where the two population elements are identical. In these eight states, crossover between the two population elements will not change the elements. For example, if the population has the two chromosomes $\{[1 01], [101]\}$, the population after crossover is also guaranteed to be $\{[10 1], [101]\}$. By the principles of roulette selection there is a nonzero probability of reaching any one of these eight absorbing states because they all have nonzero fitness values. Because the mutation probability is negligible, the GA becomes “stuck” after reaching one of these states. (Even if the population should eventually change due to a mutation, the selection/crossover process will repeat itself and continue pushing the GA to the absorbing states.) Unless the chromosomes in the absorbing states correspond to $\theta^{*}$ upon decoding, the GA does not converge to the optimum. 

## Media empírica asociada
Cuando tenemos una población de $N$ individuos en $\mathbb{R}^{n}$. Es una forma de describir la distribución de esos puntos sin importar su orden.
Para cualquier conjunto $A \subseteq \mathbb{R}^{n}$:
$$
\mu_{t}^{N}(A) = \frac{\text{número de indivuos en A}}{N}
$$
es decir, la porporción de la población que está en $A$. Resume la población sin importar el orden de los individuos, permite comparar poblaciones, es la base para el límite de campo medio.

## Límite de campo medio
Nos permite pasar de un proceso estocástico, con ruido, a un sistema determinista, sin ruido, cuando $N \to \infty$. Esto es que el comportamiento promedio de la población se vuelve determinista y puede escribirse mediante una ecuación que ya no tiene aleatoriedad.

## Kernel de transición
En una cadena de Markov, describe cómo pasa el sistema de un estado a otro.
	Es una función que, dada la población actual $P_{t}$, nos dice la probabilidad de obtener cada posible población $P_{t+1}$

# Terminología


## Insesgamiento
### Selección
explota la información de aptitud (fitness) para guiar la búsqueda hacia regiones prometedoras (sesgada hacia lo bueno).
### Variación
Explora el espacio de búsqueda. No usa ninguna información fitness más que la información del espacio de busqueda de la población parental(?). *Explora el espacio de búsqueda, introduce novedad.*

***
El principio de **máxima entropía** (Jaynes, 1957) dice:

> Dada cierta información conocida (por ejemplo, media y varianza fijas), la distribución de probabilidad que **maximiza la entropía** (es decir, que introduce la **menor información adicional posible**) es la más "insesgada" o "menos comprometida".

En el contexto de la mutación:

- **Información conocida**: el estado actual del individuo (punto de partida) y la intensidad de mutación σσ (varianza).
    
- **Distribución de máxima entropía**: la que **no favorece ninguna dirección** en el espacio. Es la **menos informada** posible.



# Condiciones necesarias y suficiencia

- $\mu < \lambda$