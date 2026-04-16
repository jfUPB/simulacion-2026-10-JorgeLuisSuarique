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
### Actividad 4.
### Actividad 5.

## Bitácora de aplicación 


## Bitácora de reflexión
