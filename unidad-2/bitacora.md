# Unidad 2

## Bitácora de proceso de aprendizaje

### Actividad 1

### Actividad 2
¿Cómo funciona la suma dos vectores en p5.js?
La suma de vectores en p5.js funciona mediante el método .add(). Matemáticamente, lo que hace la librería es sumar los componentes correspondientes de cada vector: la x de uno con la x del otro, y la y de uno con la y del otro.
Para ejecutarlo, simplemente llamas al método desde el vector que quieres modificar, pasando el segundo vector como argumento: vectorA.add(vectorB)

¿Por qué esta línea position = position + velocity; no funciona?
No funciona porque en JavaScript el operador + no está programado para entender objetos complejos como los vectores; solo sabe sumar números o unir cadenas de texto (strings).
Al intentar usar el signo +, el lenguaje convierte los vectores a un formato de texto ilegible para el cálculo matemático, lo que provoca que pierdas las coordenadas numéricas y tu programa falle.

### Actividad 3

### Actividad 4
¿Qué resultado esperas obtener en el programa anterior?
Lo natural es esperar que la función haga su trabajo y cambie los números, y eso es exactamente lo que pasa. Al imprimir el vector antes y después, ves cómo pasa de $(6, 9)$ a $(20, 30)$. La función no solo "mira" los datos, sino que entra en la variable y los transforma por completo.

¿Qué resultado obtuviste?
El resultado que obtienes es que el vector cambia de forma permanente: primero la consola muestra [6, 9, 0] y, tras ejecutar la función, cambia a [20, 30, 0]. Esto sucede porque, al ser un objeto, no le enviaste a la función una copia de los datos, sino el acceso directo al vector original (paso por referencia), permitiendo que la función modificara sus entrañas de manera definitiva.

Recuerda los conceptos de paso por valor y paso por referencia en programación.


¿Qué tipo de paso se está realizando en el código?
los vectores en p5.js no se entregan como una copia (como harías con un número), sino que entregas "el acceso" al original. Es como si en lugar de darle a la función una foto de tu vector, le dieras el control remoto del mismo; cualquier botón que la función apriete, lo verás reflejado en tu variable original.

¿Qué aprendiste?
Los vectores son objetos "vivos" y compartidos. Si los pasas por una función, cualquier cambio interno es permanente. Esto es genial para mover cosas en la pantalla, pero si alguna vez necesitas hacer pruebas sin arruinar el original, te toca usar .copy() para crear un clon independiente y no "darle las llaves de tu casa" a la función.

### Actividad 5
¿Para qué sirve el método mag()? Nota que hay otro método llamado magSq(). ¿Cuál es la diferencia entre ambos? ¿Cuál es más eficiente?
El método mag() te dice cuánto mide la "flecha" del vector, es decir, su longitud real. La diferencia con magSq() es que este último te da ese mismo valor pero al cuadrado, saltándose el paso de calcular la raíz cuadrada. En términos de eficiencia, magSq() es mucho más rápido para la computadora porque las raíces cuadradas son operaciones pesadas; por eso, si solo necesitas comparar qué vector es más largo que otro, es mejor usar la versión al cuadrado.

¿Para qué sirve el método normalize()?
Este método sirve para simplificar un vector a su mínima expresión sin que pierda el rumbo. Lo que hace es ajustar su longitud para que sea exactamente 1, manteniendo la dirección hacia donde apuntaba originalmente. Es como si le quitaras la "fuerza" al vector para quedarte únicamente con la "brújula", lo cual es perfecto cuando solo te interesa saber hacia dónde debe moverse algo, pero no a qué velocidad.

Te encuentras con un periodista en la calle y te pregunta ¿Para qué sirve el método dot()? ¿Qué le responderías en un frase?
Si tuviera que explicárselo a alguien en la calle, le diría que el método dot() es una forma de medir qué tanto "colaboran" dos vectores entre sí o qué tan alineados están. En una frase: "Es un cálculo que nos devuelve un número para saber si dos direcciones van hacia el mismo lado, si son perpendiculares o si van en sentidos opuestos".

El método dot() tiene una versión estática y una de instancia. ¿Cuál es la diferencia entre ambas?
La diferencia es básicamente quién "ejecuta" la acción. Cuando usas la versión de instancia (v1.dot(v2)), le estás pidiendo a un vector específico que se compare con otro. En cambio, la versión estática (p5.Vector.dot(v1, v2)) es como llamar a un juez externo que toma a los dos involucrados y hace la cuenta por ellos. En p5.js, la versión estática es muy útil cuando no quieres que tus vectores originales se alteren al hacer operaciones matemáticas.

Ahora el mismo periodista curioso de antes te pregunta si le puedes dar una intuición geométrica acerca del producto cruz. Entonces te pregunta ¿Cuál es la interpretación geométrica del producto cruz de dos vectores? Tu respuesta debe incluir qué pasa con la orientación y la magnitud del vector resultante.
Para entender el producto cruz, imagina que los dos vectores están apoyados sobre una mesa; el resultado será un nuevo vector que sale disparado de la mesa totalmente vertical, como un poste perpendicular a ambos. Su orientación sigue la "regla de la mano derecha" (hacia arriba o hacia abajo según el giro) y su magnitud es fascinante porque representa el área del rectángulo inclinado que ambos vectores formarían; entre más abiertos y perpendiculares estén, más largo será ese vector resultante.

¿Para que te puede servir el método dist()?
Este método es el que usas cuando necesitas saber la distancia real entre dos puntos en tu lienzo. Es fundamental para la interactividad: te sirve para saber si el personaje está tocando una moneda, si un proyectil impactó a un enemigo o simplemente para calcular qué tan lejos está el cursor del ratón de un objeto para que este reaccione a su cercanía.

¿Para qué sirven los métodos normalize() y limit()?
Estos dos métodos son los que ponen orden al caos del movimiento. normalize() se asegura de que la dirección sea pura y constante (longitud 1), mientras que limit() actúa como un regulador de velocidad: permite que un vector crezca todo lo que quiera, pero en cuanto llega a un valor máximo que tú decidas, lo frena en seco para que no se descontrole. Juntos permiten que un objeto se mueva con fluidez pero sin salir disparado fuera de la pantalla.

### Actividad 6

### Actividad 7
Cuál es el concepto del marco motion 101 y cómo se interpreta geométricamente.
Son los conceptos basicos del movimiento de una sujeto a diferentes velocidades cuyo valor va cambiando progresivamentre, tambien dicho concepto puede calcular la velocidad que el usario lo asigna y permita mantener una aceleracion constante a la particula que se le asigna. El Motion 101 es un acelerador de particulas en pocoas palabras.
¿Cómo se aplica motion 101 en el ejemplo?


### Actividad 8
¿Qué observaste cuando usas cada una de las aceleraciones propuestas?
con la aceleracion constante de cada podemos dar diferentes interaciones

## Bitácora de aplicación 



## Bitácora de reflexión

