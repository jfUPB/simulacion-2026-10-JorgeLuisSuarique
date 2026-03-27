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
<img width="1661" height="620" alt="image" src="https://github.com/user-attachments/assets/d221b21b-ede1-4b5e-95b3-5a573998690b" />
- **Describe este ejemplo usando palabras que NO mencionen p5.js, JavaScript, ni ninguna herramienta específica. Usa solo términos como: entidad, estado, colección, emisor, ciclo de vida, fuerza.**
La entidad que contiene la lógica individual de cada elemento fugaz (partícula), la entidad que agrupa y administra una colección de ellas (emisor), y el ámbito global que mantiene la colección de emisores. El ciclo de vida de las partículas está completamente contenido dentro de cada emisor, lo que permite escalar la cantidad de sistemas sin que interfieran entre sí.

### Actividad 3.
- **¿Qué tienen en común las subclases de partículas? ¿Qué tienen de diferente?**
  Lo que tienen  en común todas las sub clases son las caracteristcas que no estan sobre escritas y su diferencia son las caracteristicas Sobre Escritas.
- **¿Por qué es importante que el Emitter no necesite saber qué tipo específico de partícula está gestionando? Explica esto con tus propias palabras.**
  El Emitter es una clase independiente que ya tiene una estructura propia y simplificada, en donde es llamado a cada sunclase de particulas para que su función se combine con la de las particulas
- **Si mañana quisieras agregar un tercer tipo de partícula, ¿Qué tendrías que crear y qué NO tendrías que modificar?**
Crearías un nuevo archivo para una tercera clase que extienda la clase base Particle, implementando su propio método show() y opcionalmente otros métodos si querés comportamiento diferente). No tendrías que modificar ni Emitter (porque ya maneja polimórficamente cualquier tipo de partícula ni Particle porque la nueva clase hereda su estructura básica, solo ajustarías la lógica de creación en Emitter.addParticle() para incluir la nueva opción en la decisión aleatoria.
  
- **Compara con Example 4.2: ¿Cambió la lógica del Emitter? ¿Cambió la lógica de muerte? ¿Qué capa del sistema se modificó y cuáles permanecieron intactas?**
La lógica del Emitter desapareció por completo porque se eliminó esa capa de abstracción: ya no existe una entidad que encapsule la colección ni la creación de partículas, pasando toda esa responsabilidad al flujo principal. La lógica de muerte no cambió en absoluto, ya que Particle mantiene idéntico su ciclo de vida con lifespan e isDead. Se modificó la capa de orquestación y gestión (eliminando la clase Emitter y moviendo su lógica al ámbito global), mientras que permaneció intacta la capa de la partícula individual (Particle) junto con su comportamiento físico y su ciclo de vida autónomo.

### Actividad 4.
- **En Example 4.6, ¿Dónde se define la gravedad? ¿Quién la aplica a las partículas? ¿Es una fuerza global o local?**
La gravedad se define en draw como un vector constante. La aplica el emisor a todas las partículas mediante su método applyForce, que recorre la colección y llama al método homónimo de cada partícula. Es una fuerza global, porque un mismo vector se aplica por igual a todas las entidades, y su definición reside en el ámbito principal, permitiendo cambiarla centralizadamente sin modificar las clases internas.

- **En Example 4.7, ¿Qué diferencia hay entre la gravedad y la fuerza del repeller? ¿Dónde “vive” cada una?**
La gravedad es una fuerza global constante que se define en el ámbito principal y se aplica genéricamente a todas las partículas a través del emisor. La fuerza del repeller, en cambio, es local y variable.
  
- **La fuerza del repeller depende de la distancia entre la partícula y el repeller. ¿Qué principio físico se está modelando?**
Se está modelando una fuerza inversamente proporcional al cuadrado de la distancia, similar a la repulsión electrostática entre cargas del mismo signo o a la fuerza gravitacional pero con signo invertido.
  
- **¿Cambió la clase Particle entre Example 4.6 y 4.7? ¿Qué implica esto sobre la separación entre comportamiento de la partícula y fuerzas externas?**
La clase Particle no cambió entre el proyecto del repeller y el anterior con solo gravedad: sigue teniendo el mismo estado (posición, velocidad, aceleración), el mismo método applyForce que simplemente suma fuerzas a su aceleración, y el mismo update() que integra movimiento y reduce vida.


**¿Quién crea partículas?**

- **4.2:** Cada Emitter se crea en mousePressed y luego cada emisor crea una partícula por ciclo en su addParticle.
- **4.4:** Un único Emitter creado en setup() crea una partícula por ciclo en addParticle.
- **4.5:** No hay emisor; el propio draw crea una partícula por ciclo directamente con new Particle.
- **4.6:** Un único Emitter creado en setup crea una partícula por ciclo en addParticle.
- **4.7:** Un único Emitter creado en setup crea una partícula por ciclo en addParticle.


**¿Hay clase Emitter?**

- **4.2:** Sí, existe la clase Emitter y se crean múltiples instancias.
- **4.4:** Sí, existe la clase Emitter con una sola instancia.
- **4.5:** No, no existe la clase Emitter.
- **4.6:** Sí, existe la clase Emitter con una sola instancia.
- **4.7:** Sí, existe la clase Emitter con una sola instancia.


**¿Hay herencia?**

- **4.2:** No. Solo existe la clase Particle.
- **4.4:** Sí. Confetti hereda de Particle y sobrescribe el método show.
- **4.5:** No. Solo existe la clase Particle.
- **4.6:** No. Solo existe la clase Particle.
- **4.7:** No. Solo existe la clase Particle y Repeller es una clase independiente.


**¿Hay fuerzas externas?**

- **4.2:** No. La gravedad está definida dentro de cada partícula en su método.
- **4.4:** No. La gravedad está definida dentro de cada partícula en su método.
- **4.5:** No. La gravedad está definida dentro de cada partícula en su método.
- **4.6:** Sí. La gravedad se define en y el emisor la aplica a todas las partículas mediante.
- **4.7:** Sí. Hay dos fuerzas externas: la gravedad y la fuerza del repeller calculada por Repeller y aplicada por el emisor.


**¿Hay interacción entre elementos?**

- **4.2:** No. Cada emisor y sus partículas son independientes; no interactúan entre sí.
- **4.4:** No. Las partículas no interactúan entre sí ni con otros elementos.
- **4.5:** No. Las partículas no interactúan entre sí.
- **4.6:** No. Solo hay fuerzas externas aplicadas uniformemente, pero no hay interacción bidireccional entre elementos.
- **4.7:** Sí. El repeller interactúa con cada partícula: calcula una fuerza basada en la distancia, y las partículas responden a esa fuerza modificando su trayectoria.


**¿Cómo mueren las partículas?**

- **4.2** Cada partícula reduce su lifespan en cada ciclo, el emisor la elimina recorriendo su colección de atrás hacia adelante con splice.
- **4.4:** Mismo mecanismo: reducción de lifespan y eliminación por el emisor con recorrido inverso.
- **4.5** Mismo mecanismo: reducción de lifespan y eliminación, pero el recorrido inverso y splice ocurren directamente en draw sobre el arreglo global.
- **4.6** Mismo mecanismo: reducción de lifespan y eliminación por el emisor con recorrido inverso.
- **4.7:** Mismo mecanismo: reducción de lifespan y eliminación por el emisor con recorrido inverso.

**Modificacion de la 4.7:**
**¿Qué líneas de código tocaste?**
las lineas de codigo que se tocaron fueron las ddel draw, se eliminaron (let gravity = createVector(0, 0.1); y emitter.applyForce(gravity);)
y des pues se agrego lo demas.

**¿Qué clases/funciones modificaste?**
Solo se toco la funcion Draw en la clase de Sketch

**¿Qué partes del programa NO necesitaste modificar?**
la funcion de Setup de la clase de Sketch y las demas clases que conforman el ejemplo 4.7

**¿Por qué fue posible hacer este cambio sin afectar las demás capas?**
Fue posible cmabiar el Draw ya que orquesta el modo como cada clase que la funcion heredo puede ser usada como herraientas, por ende puedo retirar y cambias lineas de codgio mientras no se cambie las funciones internas.

https://editor.p5js.org/natureofcode/sketches/H4TMayNak
## Bitácora de aplicación 

### Actividad 5.

- El nasimiento y la muerte de una estrella es un ciclo que rosa lo perpuetuo mostrando una perspectiva de la vida y el tiempo de manera circular.

- El cosmos se comporta como nosotros vemos las ideas y la manera de ver en la humanida, estalla y vuelve a comensar desde cero hasta que veulve a estallar.

<img width="1297" height="678" alt="image" src="https://github.com/user-attachments/assets/7c16d25f-3d3e-4485-801f-50251987f547" />
<img width="1293" height="677" alt="image" src="https://github.com/user-attachments/assets/7a0f4d61-a7c5-48a0-8fc4-fc2adddee6e7" />


https://editor.p5js.org/JorgeLuisSuarique/sketches/WJR5tTdOi
```` js
let nebulae = [];
let star = null;
let supernovae = [];

let fase = "nebula"; // "nebula", "star", "explosion"

function setup() {
  createCanvas(800, 600);
  // Iniciar con nebulosas
  for (let i = 0; i < 80; i++) {
    nebulae.push(new Nebula(random(width), random(height)));
  }
}

function draw() {
  background(0, 30);
  
  if (fase === "nebula") {
    // ========== FASE NEBULOSA ==========
    
    // Mover nebulosas con atracción al mouse
    for (let n of nebulae) {
      if (mouseIsPressed) {
        let mouse = createVector(mouseX, mouseY);
        let dir = p5.Vector.sub(mouse, n.position);
        let dist = constrain(dir.mag(), 5, 100);
        let force = dir.copy().setMag(0.2);
        n.applyForce(force);
      }
      n.update();
      n.show();
    }
    
    // Detectar colapso: si hay muchas nebulosas cerca del mouse
    if (mouseIsPressed) {
      let mousePos = createVector(mouseX, mouseY);
      let cerca = [];
      for (let n of nebulae) {
        if (n.position.dist(mousePos) < 40) {
          cerca.push(n);
        }
      }
      
      if (cerca.length >= 12) {
        // Eliminar todas las nebulosas
        nebulae = [];
        // Crear estrella
        star = new Star(mouseX, mouseY);
        fase = "star";
      }
    }
    
    // Instrucciones
    fill(255);
    text("Fase: Nebulosa", 10, 20);
    text("Arrastra el mouse para juntar nebulosas", 10, 40);
    text("Junta 12 nebulosas cerca del mouse para crear una estrella", 10, 60);
    
  } else if (fase === "star") {
    // ========== FASE ESTRELLA ==========
    
    // Actualizar y mostrar estrella
    star.update();
    star.show();
    
    // Si la estrella muere, pasar a explosión
    if (star.isDead()) {
      // Crear supernovas
      for (let i = 0; i < 60; i++) {
        supernovae.push(new Supernova(star.position.x, star.position.y));
      }
      star = null;
      fase = "explosion";
    }
    
    // Instrucciones
    fill(255);
    text("Fase: Estrella", 10, 20);
    text("La estrella crece... pronto explotará", 10, 40);
    
  } else if (fase === "explosion") {
    // ========== FASE EXPLOSIÓN ==========
    
    // Actualizar y mostrar supernovas
    for (let i = supernovae.length - 1; i >= 0; i--) {
      let s = supernovae[i];
      s.update();
      s.show();
      if (s.isDead()) {
        supernovae.splice(i, 1);
      }
    }
    
    // Mientras hay supernovas, generar nuevas nebulosas gradualmente
    if (supernovae.length > 0 && nebulae.length < 60) {
      // Aparecen nuevas nebulosas de a poco
      for (let i = 0; i < 2; i++) {
        nebulae.push(new Nebula(random(width), random(height)));
      }
    }
    
    // Cuando ya no hay supernovas y hay suficientes nebulosas, volver a fase nebulosa
    if (supernovae.length === 0 && nebulae.length >= 30) {
      fase = "nebula";
    }
    
    // Instrucciones
    fill(255);
    text("Fase: Explosión", 10, 20);
    text("La estrella explotó... nuevas nebulosas están naciendo", 10, 40);
    text("Nebulosas: " + nebulae.length, 10, 60);
  }
}
````
<img width="815" height="737" alt="image" src="https://github.com/user-attachments/assets/443b51e7-9b1c-4c5d-9a5d-82e8baa1c101" />
<img width="814" height="725" alt="image" src="https://github.com/user-attachments/assets/b06d7415-9681-443c-a16f-99f5ca37f946" />
<img width="808" height="728" alt="image" src="https://github.com/user-attachments/assets/cf3f6dff-a7bb-48f4-b1b7-a02f7f7bf9e8" />

## Bitácora de reflexión
### Actividad 6.
**Parte 1.**
- Una partícula es una entidad con estado.
- Una partícula tiene ciclo de vida.
- Un sistema de partículas gestiona colecciones dinámicas de elementos.
- La creación y eliminación de partículas no es un detalle técnico menor, sino parte central del modelo.
- Debe haber separación entre la lógica de una partícula individual y la lógica del sistema/emisor.
- Un emisor o particle system es una abstracción importante.
- Pueden existir sistemas de sistemas.
- Puede haber heterogeneidad usando herencia y polimorfismo.
- Las partículas pueden responder a fuerzas globales y locales.
- La representación visual puede variar sin cambiar el principio algorítmico de fondo.

**Parte 2.**
Piensa en tu pieza del Apply: si la quisieras recrear en Unity (o TouchDesigner, o Blender), ¿Qué se mantendría igual y qué cambiaría? ¿Qué partes de tu diseño son independientes de la herramienta?
