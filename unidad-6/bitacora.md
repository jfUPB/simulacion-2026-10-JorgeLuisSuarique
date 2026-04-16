# Unidad 6

## Bitácora de proceso de aprendizaje
### Actividad 1.
**Loxodography**.

<img width="575" height="696" alt="image" src="https://github.com/user-attachments/assets/8beddb7f-e54e-43d2-a5ad-c668e0ea4823" />

**composición:** Está densamente centrada. El foco principal es un rostro esquemático compuesto por cientos de pequeñas formas, generalmente en el centro del lienzo. El "marco" o "página" a menudo se representa con bordes definidos, como si fuera un libro.

**densidad:** Muy alta en el centro, donde se acumulan las formas para crear las facciones (ojos, nariz, boca). La densidad es la principal herramienta para generar la imagen figurativa: más formas juntas = sombra o rasgo; menos formas = luz o espacio vacío.

**dirección del movimiento:** El movimiento es sutil pero constante. Las formas individuales (que parecen pinceladas o pétalos) tienen una orientación direccional. A menudo, todas apuntan en una dirección similar, creando una textura de "cepillo" o "viento". En las zonas de la cara, la dirección puede variar para seguir la "forma" del rasgo, como si las pinceladas modelaran un rostro.

**color:** Utiliza paletas reducidas pero de alto contraste. Puede ser una combinación de dos o tres colores (ej: naranja, rosa y verde) sobre un fondo oscuro. El color no es realista; es casi fluorescente o de alta saturación, lo que acentúa la sensación digital pero orgánica. El color crea la emoción, mientras que la densidad crea la forma.

**ritmo:** Está marcado por la repetición de la misma unidad gráfica (el "pétalo" triangular) una y otra vez. El ritmo es hipnótico, como un latido constante. La variación en la orientación de cada pétalo crea un ritmo interno más complejo, casi como una partitura musical para los ojos.

**repetición y variación:** Es la clave de la pieza. La repetición de la forma base (pétalo triangular) unifica toda la obra. La variación está en su orientación (ángulo), su color (dentro de la paleta) y su posición. El sistema es extremadamente simple (una forma), pero su aplicación variada genera una complejidad enorme (un rostro).

Crean una tensión fascinante entre lo mecánico y lo orgánico, lo abstracto y lo figurativo. Sabes que estás viendo un sistema repetitivo generado por código, pero tu cerebro no puede evitar reconocer un rostro humano.

Yo creo que el sistema funciona creatndo formas triangulares. El algoritmo crea un "mapa" interno en las zonas donde debe haber una orientación de los pétalos siguiendo un patrón circular y en la nariz, las orientaciones apuntan hacia abajo junto al fondo donde las orientaciones son más uniformes, quizás con ruido. El algoritmo decide dónde colocar más pétalos. Hay una "imagen guía" (un mapa de densidad) de un rostro. Las zonas oscuras de ese mapa reciben más pétalos. Las claras, menos. Colocar cientos o miles de estos pétalos, siguiendo las reglas de posición (mapa de densidad) y orientación (mapa de dirección). El color se asigna según la posición o una paleta fija.

-------
**New Space**.

<img width="408" height="538" alt="image" src="https://github.com/user-attachments/assets/b073ddf2-361e-4560-bbba-fcc9e7976cbf" />

**composición:** Es una naturaleza muerta moderna. Los objetos (silla, lámpara, fruta) están dispuestos en un espacio ambiguo, a menudo sobre una superficie de mesa. La composición es equilibrada pero intencionadamente "torpe", como si los objetos flotaran.

**densidad:** Es muy variable. Las sombras y las zonas de mayor profundidad son muy densas, llenas de líneas y texturas oscuras. Las zonas iluminadas son casi vacías, dejando ver el "papel" (el fondo). La línea es la reina.

**dirección del movimiento:** Está en las pinceladas o trazos que construyen las superficies. Cada objeto está "dibujado" con cientos de trazos cortos y paralelos. La dirección de estos trazos define la volumetría y la textura. Por ejemplo, la pantalla de la lámpara puede tener trazos verticales, mientras que la silla los tiene horizontales. El movimiento es la textura.

**color:** Aquí es clave. La paleta es casi monocromática, usando un solo color (como un rojo ladrillo, un azul añil o un negro intenso) sobre un fondo claro. La fuerza no está en el contraste de color, sino en el contraste de valor (claros y oscuros) y en la textura. Parece un grabado porque usa un "color de tinta" contra el "color del papel".

**ritmo:** Lo marca la repetición frenética de esos trazos cortos y paralelos. Es un ritmo rápido, casi obsesivo, que llena las superficies. La variación en la longitud, el grosor y la separación de esos trazos es lo que da vida a los objetos. Donde los trazos se juntan, hay sombra; donde se separan, hay luz.

**repetición y variación:** De nuevo, la repetición del trazo es la unidad básica. La variación está en la dirección, la densidad y la agrupación de esos trazos para simular el volumen, la sombra y la textura de los objetos cotidianos. No hay líneas de contorno; el contorno emerge del límite donde los trazos de un objeto se encuentran con los del fondo u otro objeto.

or la misma razón que un grabado al aguafuerte es potente: la restricción genera expresividad. Usar un solo "color" y un solo tipo de "marca" (el trazo) te obliga a simplificar y a encontrar la esencia de la forma. La potencia está en cómo el sistema de reglas (trazo corto, paralelo, con cierta longitud) puede generar una enorme variedad de texturas: la madera de la silla, el metal de la lámpara, la suavidad de una pera. Es minimalista en sus medios pero maximalista en su resultado.

El sistema aquí es un simulador de grabado con un modelo 3D muy simple de la escena. El algoritmo "raycasting" pero en lugar de calcular el color, calcula la dirección de los trazos. Decide, para cada punto de la superficie, en qué dirección dibujar el trazo. Esto puede basarse en la curvatura de la superficie (para simular el volumen) o en un campo vectorial predefinido. Luego, "siembra" miles de puntos sobre la imagen y para cada punto, dibuja un trazo siguiendo la dirección del campo en esa zona. La longitud y el grosor del trazo pueden variar según la luminosidad (trazo más largo y grueso en sombras). Se aplica un proceso para que los trazos no sean perfectos, añadiendo un poco de ruido o "imperfección" para que parezca hecho a mano, no por una máquina perfecta.


### Actividad 2.

**¿Qué es un agente autónomo?**

Es una entidad que toma decisiones por sí misma para moverse en un entorno, sin recibir órdenes paso a paso. Piensa en un vehículo que decide cómo evitar un obstáculo o perseguir un objetivo basándose en lo que percibe a su alrededor, no porque alguien le diga "gira a la izquierda ahora". La autonomía implica que el agente tiene un objetivo (llegar a un punto, huir de un peligro) y usa reglas internas para calcular su siguiente movimiento, lo que lo diferencia de una simple partícula que solo obedece fuerzas externas como la gravedad.

**¿Qué es una steering force?**

es una fuerza interna que el propio agente genera para cambiar su trayectoria de manera intencional. Es como si el agente tuviera un volante: la steering force es la aceleración que aplica para dirigirse hacia un objetivo, alejarse de una amenaza o seguir un camino. A diferencia de la gravedad o el viento, que empujan al objeto desde fuera sin importar lo que este quiera, la steering force nace de la decisión del agente y se suma a las otras fuerzas que ya actúan sobre él.

**¿En qué se diferencia una steering force de fuerzas como gravedad, viento o fricción?**

La diferencia clave entre una steering force y una fuerza externa como la gravedad es que la gravedad es ciega y universal: empuja todo hacia abajo sin preguntar. La steering force, en cambio, es inteligente y contextual: cambia según lo que el agente percibe en ese momento. Mientras la gravedad siempre suma el mismo vector (0, 0.1), una steering force puede ser "acelera hacia el mouse" o "aléjate de ese obstáculo", y su valor se recalcula en cada instante en función de la posición del agente y del entorno.

### Actividad 3.

**¿Cómo está construido el campo de flujo?**

El campo de flujo se construye como una cuadrícula invisible que cubre todo el lienzo, donde cada celda de esa cuadrícula contiene un vector (una flecha) que indica una dirección. Para crearlo, se define primero la resolución (por ejemplo, 20 píxeles por celda), se calcula cuántas columnas y filas entran en el lienzo, y luego se usa un bucle anidado para rellenar cada celda con un vector, cuya dirección puede venir de diferentes fuentes: ruido de Perlin, un patrón matemático como un círculo, o incluso la lectura de una imagen.

**¿Qué representa cada celda o vector del campo?**

Cada vector representa la "velocidad deseada" ideal para cualquier partícula que se encuentre exactamente en esa celda. Es como una señal invisible en ese punto del espacio que le susurra al agente: "Si pasas por aquí, deberías intentar moverte en esta dirección". La intensidad del vector (su longitud) indica qué tan rápido querría ir el agente idealmente, aunque luego cada agente puede decidir si obedece o no según sus propias limitaciones.

**¿Cómo usa un agente su posición para consultar el campo?**

El agente usa su posición actual (x, y) para "mapearse" dentro de la cuadrícula: divide su coordenada x por la resolución de la celda para saber en qué columna está, y su coordenada y por la resolución para saber en qué fila está. Es como si el lienzo fuera un tablero de ajedrez gigante y el agente tuviera que mirar el suelo para ver en qué casilla está parado, y luego leer la flecha dibujada en esa casilla.

**¿Cómo se convierte el vector consultado en una decisión de movimiento?**

El agente toma ese vector del campo de flujo y lo trata como su "velocidad deseada", es decir, hacia dónde le gustaría ir. Luego aplica la fórmula de steering de Reynolds: resta su velocidad actual de esa velocidad deseada, lo que genera una fuerza de dirección (steering force). Esta fuerza se limita (para no ser demasiado brusca) y se suma a su aceleración, desviando suavemente su trayectoria para alinearse con el campo de flujo.

**resolución:** Tamaño de cada celda en píxeles (ej: 20). Define cuántas celdas hay (cols = width/resolución, rows = height/resolución). A menor resolución, más celdas y más detalle; a mayor resolución, menos celdas y un campo más tosco.

**maxspeed:** Velocidad máxima que puede alcanzar cada vehículo. Limita qué tan rápido se mueven los agentes.

**maxforce:** Fuerza de dirección máxima que puede aplicar un vehículo para girar. Controla qué tan brusco o suave es el cambio de dirección.

**cantidad de agentes:** Número de vehículos que siguen el campo de flujo. Más agentes generan más densidad y patrones colectivos; menos agentes hacen visible la trayectoria individual.

Voy a cambiar el incremento de yoff dentro del bucle anidado en init() de 0.1 a 0.05. Esto hace que el ruido de Perlin varíe más lentamente en la dirección vertical. El efecto visual es que el campo de flujo se vuelve más "suave" y las transiciones entre direcciones de vectores son menos abruptas, generando que los agentes sigan curvas más amplias y menos fragmentadas, como si el viento o la corriente tuviera cambios más graduales en lugar de giros bruscos. Visualmente se pierde algo de la textura "ruidosa" original y se gana en fluidez.

**¿Qué tipo de movimiento produce este algoritmo?**

El algoritmo de flow field produce un movimiento orgánico y fluido donde múltiples agentes se deslizan siguiendo las direcciones invisibles marcadas por una cuadrícula de vectores generada con ruido de Perlin, creando trayectorias suaves que se curvan y entrecruzan sin que los agentes choquen entre sí, como hojas arrastradas por corrientes de aire o agua.

**¿Qué sensaciones visuales te sugiere?**

Visualmente me sugiere calma hipnótica y movimiento colectivo sin propósito aparente, como observar un banco de peces o una bandada de pájaros desde lejos, donde cada individuo parece seguir una coreografía invisible generando una sensación de orden emergente y fluidez relajante.

**¿En qué tipo de pieza musical imaginas que podría funcionar bien?**

Esta pieza funcionaría bien con música electrónica ambiental y texturas modulares en evolución, similar a las obras de Brian Eno o del minimalismo de Steve Reich, donde capas sonoras que se repiten generan patrones complejos que nunca son exactamente iguales, creando una experiencia inmersiva y contemplativa.

### Actividad 4.

- **Separación:** Es la regla que hace que cada agente evite chocar con sus vecinos más cercanos, generando una fuerza que lo empuja en dirección opuesta cuando alguien invade su espacio personal.

- **Alineación:** Es la tendencia de cada agente a ajustar su dirección y velocidad para igualar el promedio de sus vecinos, logrando que todos se muevan en sintonía como una bandada coordinada.

- **Cohesión:** Es la fuerza que empuja a cada agente hacia el centro del grupo calculando el punto medio de las posiciones de sus vecinos, evitando que alguien se rezague y manteniendo la unidad de la bandada.

Los parámetros clave son el radio de percepción (neighborDistance), la distancia mínima de separación (desiredSeparation) y los pesos de cada fuerza (como 1.5 para separación, 1.0 para alineación y cohesión).

Cambié el peso de separación en la función flock de 1.5 a 3.0. El efecto visual es que la bandada se vuelve mucho más dispersa y nerviosa, los boids mantienen una distancia mayor entre sí y el grupo pierde su forma compacta original. El comportamiento emergente cambia de compacto y fluido a disperso y cauteloso, donde la separación domina por completo sobre la cohesión.

- **Compacto:** La bandada se mantiene muy unida, con los boids casi pegados entre sí formando una masa densa que se mueve como un solo organismo.

- **Disperso:** Los agentes se separan y ocupan un área grande del lienzo, manteniendo distancias considerables entre ellos sin formar un grupo definido.

- **Estable:** El movimiento es predecible y constante, sin cambios bruscos de dirección o velocidad, como un río que fluye sin sobresaltos.

- **Nervioso:** Los boids cambian de dirección constantemente de manera rápida e impredecible, generando una sensación de agitación y alerta continua.

- **Caótico:** No hay ningún orden aparente, los agentes chocan entre sí y se mueven en direcciones contradictorias sin seguir ninguna regla colectiva.

- **Fluido:** El movimiento es suave y continuo, con transiciones elegantes donde la bandada se estira, se contrae y gira como una sola masa líquida.

**¿Qué atmósfera visual produce el flocking?**

El flocking produce una atmósfera hipnótica y orgánica que sugiere vida colectiva, inteligencia sin líder y calma, como observar un banco de peces deslizándose bajo el agua o una bandada de pájaros trazando figuras en el cielo.

**¿En qué tipo de relación con una canción podría funcionar mejor este algoritmo?**

Este algoritmo funcionaría mejor en relación con una canción de electrónica ambiental o post-rock instrumental, donde las capas melódicas se superponen y evolucionan lentamente sin golpes de batería ni cambios bruscos, permitiendo que la música respire y se transforme al ritmo de la bandada.

### Actividad 5.

- **Tipo de movimiento que producen:** El flow field produce un movimiento fluido y predecible donde todos los agentes siguen trayectorias suaves dictadas por una cuadrícula invisible, como hojas arrastradas por una corriente de agua. El flocking produce un movimiento orgánico y sincronizado donde los agentes se mueven en bandada siguiendo reglas locales de separación, alineación y cohesión, como pájaros o peces en la naturaleza.
  
- **Nivel de control visual:** El flow field ofrece un control visual muy alto porque el diseñador define explícitamente la dirección de los vectores en cada celda, pudiendo crear patrones geométricos, remolinos o flujos personalizados. El flocking ofrece un control visual bajo e indirecto porque el diseñador solo define pesos y radios, pero el comportamiento emergente no se puede predecir ni diseñar con precisión.
  
- **Nivel de emergencia:** El flow field tiene un nivel de emergencia bajo porque el movimiento global es la suma directa de las instrucciones del campo, sin interacciones complejas entre agentes. El flocking tiene un nivel de emergencia muy alto porque la forma de la bandada, sus giros y su cohesión surgen únicamente de las interacciones locales entre agentes, sin ningún líder ni plano global.
  
- **Tipo de atmósfera o sensación:** El flow field transmite una sensación de flujo controlado y destino marcado, como un río que lleva hojas o un viento que arrastra polen, con una calma que viene de la previsibilidad. El flocking transmite una sensación de vida impredecible y autonomía colectiva, como observar un banco de peces que cambia de forma constantemente, con una calma hipnótica que viene de la sincronía.
  
- **Relación posible con una pieza musical:** El flow field funcionaría bien con música minimalista y repetitiva como las composiciones de Steve Reich o Philip Glass, donde patrones que se repiten generan variaciones sutiles. El flocking funcionaría mejor con música ambiental y evolutiva como la de Brian Eno o Sigur Rós, donde capas sonoras se superponen y transforman lentamente sin estructura fija.
  
- **Ventajas y limitaciones de cada uno:** La ventaja del flow field es su predecibilidad y control total sobre el flujo, pero su limitación es que los agentes no interactúan entre sí, por lo que nunca se genera sorpresa ni comportamiento colectivo complejo. La ventaja del flocking es su capacidad de generar comportamientos emergentes sorprendentes y vidas simuladas, pero su limitación es la dificultad de controlar exactamente la forma final de la bandada, que puede volverse caótica si los pesos no están bien calibrados.

##### Cancion
La canción que pienso usar es DYSTOPIA de So Far So Good, Incredible Polo, siendo esta una canción eufórica por su ritmo rápido y letras sobre alcanzar estrellas, pero melancólica por su atmósfera de baja valencia y su estética cyberpunk que evoca soledad y urgencia. Para esta dualidad usaría flocking con alta velocidad y cohesión para la parte eufórica, logrando una bandada fluida que se expande como luces de neón acelerando, pero con un flow field de fondo que añada una deriva lenta y controlada, trayendo esa melancolía de fondo. Las agujas brillantes se moverían sincronizadas como coches en una autopista futurista, y en los momentos más intensos del drop haría que los agentes exploten radialmente con colores cian y magenta, para luego volver a unirse en formación, mezclando la energía del ritmo con la tristeza de fondo.

## Bitácora de aplicación 

### Actividad 06:



## Bitácora de reflexión
