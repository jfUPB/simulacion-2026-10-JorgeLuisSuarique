# Unidad 5
## Bitácora de proceso de aprendizaje
### Actividad 1.
- **¿Qué propiedades tiene cada partícula? Clasifícalas: ¿Cuáles definen su estado físico? ¿Cuáles su estado vital?**
  las porpiedades de cada perticula son las siguientes: Motion101, tiempo de vida y aparieicia. Su estado fisico se define en el Show y su estado Vital se define en donde llaman el Motion 101 y su tiem po de vida.
- **¿Qué condición determina que una partícula “muere”? ¿Es una muerte instantánea o gradual?**
  cada particula no tiene una muerte instantanea su funcion ba des aceleraqndo por un tiempo determinado y al monmento de morir deja de consumir recursos de memoria en la PC
- **¿Cómo se actualiza la partícula en cada frame? Identifica el patrón motion 101 dentro de la partícula.**
  Cada particula se actialisa usando la gavedad, la velocidad y la posciocion durtanto su caida y esta cadena se le conoe como Motion 101 

### ACtividad 2.
- **¿Qué responsabilidades que antes estaban en draw() ahora están dentro de la clase Emitter?**
  Las Responsabilidades que ahora se ven en la clase Emitter es el Push de las particulas y el checking de cada particula.
- **¿Cuál es la ventaja de encapsular la lógica de emisión en una clase separada?**
  hay mas fluides y orden en el codigo a la hora de ejecutar y evitan los errores
- **En este ejemplo hay un array de emitters. ¿Quién crea los emitters? ¿Quién crea las partículas dentro de cada emitter?**
  El Draw crea los emitter y la clase Emitter construye las particulas que llamas desde la clase de particulas
- **Dibuja un diagrama que muestre la jerarquía: sketch → [emitters] → [partículas]. ¿Cuántos niveles de “colección” hay?**
- **Describe este ejemplo usando palabras que NO mencionen p5.js, JavaScript, ni ninguna herramienta específica. Usa solo términos como: entidad, estado, colección, emisor, ciclo de vida, fuerza.**

### Actividad 3.
- **¿Qué tienen en común las subclases de partículas? ¿Qué tienen de diferente?**
  Lo que tienen  en común todas las sub clases son las caracteristcas que no estan sobre escritas y su diferencia son las caracteristicas Sobre Escritas.
- **¿Por qué es importante que el Emitter no necesite saber qué tipo específico de partícula está gestionando? Explica esto con tus propias palabras.**
  El Emitter es una clase independiente que ya tiene una estructura propia y simplificada, en donde es llamado a cada sunclase de particulas para que su función se combine con la de las particulas
- **Si mañana quisieras agregar un tercer tipo de partícula, ¿Qué tendrías que crear y qué NO tendrías que modificar?**
  
- **Compara con Example 4.2: ¿Cambió la lógica del Emitter? ¿Cambió la lógica de muerte? ¿Qué capa del sistema se modificó y cuáles permanecieron intactas?**


### Actividad 4.
- **En Example 4.6, ¿Dónde se define la gravedad? ¿Quién la aplica a las partículas? ¿Es una fuerza global o local?**
- **En Example 4.7, ¿Qué diferencia hay entre la gravedad y la fuerza del repeller? ¿Dónde “vive” cada una?**
- **La fuerza del repeller depende de la distancia entre la partícula y el repeller. ¿Qué principio físico se está modelando?**
- **¿Cambió la clase Particle entre Example 4.6 y 4.7? ¿Qué implica esto sobre la separación entre comportamiento de la partícula y fuerzas externas?**

## Bitácora de aplicación 


## Bitácora de reflexión
