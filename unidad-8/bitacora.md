# Unidad 8

## Bitácora de proceso de aprendizaje

### Actividad 1.

#### Indica qué herramienta te interesa explorar y por qué.
Usare la herramienta de Unreal Enige 5 ya que tengo experiencia en su uso y ma gustaria enfocarme bastante en los efectos visuales de esta herramienta.
#### Explica qué relación tiene esa herramienta con tu línea de énfasis o interés profesional.
Esta herramienta junata mis gustos y habilidades en lo que son los efectos visuales y la composicion en el mundo audio visual de una manera mas tecnica y profecional sin avandonar el arte.
#### Busca 2 o 3 referentes realizados con esa herramienta o cercanos a su ecosistema.
https://www.youtube.com/shorts/MHcydxswpHM
https://www.youtube.com/shorts/RP0IKOJiclM
https://roberthodgin.com/project/taxi-taxi
#### Explica qué te interesa de esos referentes.
me gusta mucho como se ve el sistema de particulas siguiendo varias rutas aleatoriamente pero sin chocar unos con otras.
#### Propón uno o dos posibles contextos profesionales para tu pieza final.
Para mi flujo de trabajo el uso de flow fields y flocking puede ayudar bastante en la produccion virtual en un diferentes contexto que se nesesita para efectos visuales que se sientan inmersivos.

### Actividad 2.

#### Indica qué sistema del curso vas a transferir.
usare el sistema de flow fields y flocking para este trabajo.
#### Explica brevemente cómo funcionaba ese sistema en p5.js.

#### Justifica por qué quieres transferirlo a la herramienta elegida.
Aunque con Unreal es dificil encontrar ejemplos para ilustrar (solo con fliking, flow fiedels se usa mucho en la industria de videojuegos), ls herramientas que puedes programar con Blueprints, teine funciones que permite desarrollar y calucular ese tipo de cormpontamiento creando una muy buena interaccion.
#### Explica qué tipo de pieza visual te imaginas construir con esa combinación.
El tipo de piesa que quiero hacer es un flujo de particulas como un flijo de naves en una ciudad cyberpunck en con una vista isometrica, que de una nerrativa inmersiva como si siguieramos el viento lleando de un lugar a otro.
#### Señala qué dificultades técnicas anticipas.
No hay mucho ejemplos en los que pueda basarme y ese tipo de tutoriales escasean, al usar Blueprints, es dificil generar el codigo y es mas buscar referencias y guias para hacer este tranbajo.

### Actividad 3.

#### Describe qué componentes o módulos necesitas aprender en tu herramienta.

- **Niagara systema:** es una herramienta que ofrece Unreal engine para el control de particulas y el uso de ellas para volverlo inmersivas.
- **Lignight**: En unreal nesesito mantener esta funcion lo mas optimisado para que la inmercion funcione bien.
  
#### Realiza al menos dos pruebas técnicas.

<img width="1153" height="661" alt="image" src="https://github.com/user-attachments/assets/28218b10-956c-4ca9-b875-72020d79738a" />
aunque esta en el mismo proyecto, logre usar Flow fields y flocking usando blueprints, asi que ambas pruebas se hicieron en simultaneo.

#### Explica qué resuelve cada prueba.
Ambas como se hicieron en simlutaneo se demosntro que se puede emular los compotamiento del Flow fields y flocking unsando los blueprints pero si advieto, es mas dificil de lo que se cree.

#### Indica qué parte del sistema ya lograste reconstruir.
El Flow fields es le sistema que ya esta bien establecido, poruqe permite dare una guia en todas partes.

#### Explica qué parte sigue sin resolverse.
El flocking aun no se aplica del todo sus 3 reglas pero esta muy cerca de terminar.

### Actividad 4.

Construye una tabla, esquema o mapa comparando:

#### Cómo funcionaba el sistema en p5.js.
Tanto el sistema de Flow Fields como el Flocking son dos técnicas fundamentales en p5.js para crear movimiento emergente y orgánico. Aunque ambos simulan comportamientos colectivos, lo hacen de maneras muy diferentes.
En esencia, el Flow Field es como una corriente invisible que guía a las partículas , mientras que el Flocking es un conjunto de reglas internas que los propios agentes (llamados "boids") siguen para moverse en grupo, como una bandada de pájaros.
#### cómo se implementa en la nueva herramienta.
En Unreal Engine no hay un botón de "flocking", pero puedes construirlo. Para bandadas (flocking) lo más fácil es usar el plugin gratuito "FlockSteeringBehavior" en la tienda de Unreal, que ya viene con las reglas de pájaros o peces listas para usar. Para campos de flujo (flow fields) —donde muchas cosas siguen una corriente invisible— la mejor solución simple es el proyecto de código abierto "FlowField-RVO2", que además hace que los personajes se esquiven entre ellos mientras siguen la corriente. Si tu idea es algo más artístico (como viento o humo), puedes lograr un efecto parecido usando el sistema visual Niagara que viene incluido en Unreal 5.
#### Qué se mantiene.
Aunque Unreal Engine y p5.js son mundos muy diferentes (uno es un motor profesional para juegos 3D y el otro es una librería creativa para canvas 2D), la lógica central de estos algoritmos se mantiene prácticamente idéntica. Lo que cambia es el "idioma" en el que la escribes (C++/Blueprints vs JavaScript) y la escala (3D vs 2D).
#### Qué cambia.
En p5.js todo es código simple y 2D; en Unreal es código más robusto y 3D, con más herramientas visuales, pero también más pasos para hacer lo mismo. La lógica no cambia, pero la exigencia de rendimiento y la complejidad de implementación sí aumentan significativamente.
#### Qué ventajas aparecen.
p5.js es para arte generativo que se mira en una pantalla. Unreal es para arte generativo que se habita. La ventaja de Unreal no es solo el 3D bonito, sino que el espectador puede caminar dentro de la bandada, tocarla con sus manos (en VR), escucharla en 3D, y sentir que las partículas reaccionan a su presencia física. Pasás de ser un observador externo a vivir dentro del algoritmo.
#### Qué limitaciones nuevas surgen.
Si usás p5.js, en esta obra se ve en una pantalla plana y el espectador la mira desde afuera. Si usás Unreal, el espectador camina adentro de la bandada y siente el flow field rodeándolo. La diferencia no es técnica, es experiencial: uno se observa, el otro se habita. Empezá en p5.js para entender el algoritmo y después pasá a Unreal si necesitás que la gente esté adentro.

### Cierra respondiendo:
#### ¿Qué aprendiste sobre el sistema al tener que reconstruirlo fuera de p5.js?
Reconstruirlo fuera de p5.js te enseña que p5.js es un paraíso artificial. Te protege de la complejidad real: manejo del tiempo, optimización de vecinos, grillas 3D, visualización costosa, y espacios infinitos. Aprendés que el algoritmo es solo el 20% del problema. El otro 80% es hacer que corra rápido en un mundo real con límites, luces, y un espectador que se mueve dentro. p5.js te dejaba pensar solo en la poesía del movimiento; fuera de él, también tenés que pensar en la ingeniería.

Usar ele ejemlo de la actividad de la muscia, ya que este proyecto esta basado en esto.

## Bitácora de aplicación 
### Actividad 5.
- Herramienta elegida.
- Sistema transferido.
- Contexto profesional concreto.
- Concepto visual.
- Referencias.
- Bocetos.
- Explicación de la transferencia.
- Mapa de decisiones.
- Mapa de presentación.
- Evidencia del uso de IA.
- Código, archivo, proyecto o documentación técnica según la herramienta. 
- Registro visual de la pieza.

## Bitácora de reflexión
