# Unidad 2

## Bitácora de proceso de aprendizaje

### Actividad 1
El trabajo que más me gustó fue la animación procedural de Raven Kwok. Es impresionante cómo utiliza la interacción generativa de vectores para articular las extremidades; la manera en que el cubo central coordina los vectores que emulan las patas de un cangrejo hace que el desplazamiento no se vea mecánico, sino como un movimiento biológico fluido y natural.

### Actividad 2
¿Cómo funciona la suma dos vectores en p5.js?
La suma de vectores en p5.js funciona mediante el método .add(). Matemáticamente, lo que hace la librería es sumar los componentes correspondientes de cada vector: la x de uno con la x del otro, y la y de uno con la y del otro.
Para ejecutarlo, simplemente llamas al método desde el vector que quieres modificar, pasando el segundo vector como argumento: vectorA.add(vectorB)

¿Por qué esta línea position = position + velocity; no funciona?
No funciona porque en JavaScript el operador + no está programado para entender objetos complejos como los vectores; solo sabe sumar números o unir cadenas de texto (strings).
Al intentar usar el signo +, el lenguaje convierte los vectores a un formato de texto ilegible para el cálculo matemático, lo que provoca que pierdas las coordenadas numéricas y tu programa falle.

### Actividad 3

¿Qué tuviste que hacer para hacer la conversión propuesta?
```js
// Actividad: Histograma de Probabilidad usando Vectores
// Basado en el ejemplo de Daniel Shiffman - Capítulo 0

let totals = []; // Aquí guardaremos objetos p5.Vector
let numBins = 20;

function setup() {
  createCanvas(640, 240);
  let w = width / numBins;

  // En lugar de un arreglo de números, creamos un arreglo de vectores
  for (let i = 0; i < numBins; i++) {
    // x = posición en el eje horizontal
    // y = altura (que empieza en 0)
    totals[i] = createVector(i * w, 0);
  }
}

function draw() {
  background(255);

  // 1. Lógica de probabilidad: elegimos un índice al azar
  let index = floor(random(totals.length));

  // 2. Manipulación del vector: aumentamos la componente Y del vector elegido
  // No hay Motion 101, solo estamos usando el vector como almacenamiento
  totals[index].y++;

  // 3. Dibujo de la gráfica
  stroke(0);
  strokeWeight(2);
  fill(127);

  let w = width / totals.length;
  for (let i = 0; i < totals.length; i++) {
    // Usamos las componentes .x y .y del vector para dibujar el rectángulo
    rect(totals[i].x, height - totals[i].y, w - 1, totals[i].y);
  }
}
```
Pasar de un modelo de datos disperso (donde la posición se calculaba por un lado y el valor por otro) a un modelo de datos agrupado, donde el Vector funciona como una entidad que conoce tanto su lugar en el lienzo como su estado interno de crecimiento.

Escribe el código que utilizaste para resolver el ejercicio.
```js
// The Nature of Code
// Daniel Shiffman
// http://natureofcode.com

// An array to keep track of how often random numbers are picked

let randomCounts = [];
let total = 20;

function setup() {
  createCanvas(640, 240);
  for (let i = 0; i < total; i++) {
    randomCounts[i] = 0;
  }
}

function draw() {
  background(255);
  const index = floor(random(total));
  randomCounts[index]++;

  // Draw a rectangle to graph results
  stroke(0);
  strokeWeight(2);
  fill(127);
  const w = width / randomCounts.length;

  for (let x = 0; x < randomCounts.length; x++) {
    rect(x * w, height - randomCounts[x], w - 1, randomCounts[x]);
  }
}

```

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

El código que genera el resultado que te pedí.
```js
let t = 0; 

function setup() {
    createCanvas(500, 500);
}

function draw() {
    background(220);

    // 1. Definimos los puntos base
    let v0 = createVector(50, 50);  // El origen de las flechas roja y azul
    let v1 = createVector(400, 0);  // Flecha Roja (relativa a v0)
    let v2 = createVector(0, 400);  // Flecha Azul (relativa a v0)
    
    // 2. Cálculo de la Flecha Morada (Interpolación/Línea de tiempo)
    // El valor 'amount' oscila suavemente entre 0 y 1 gracias al seno
    let amount = map(sin(t), -1, 1, 0, 1);
    let v3 = p5.Vector.lerp(v1, v2, amount);
    
    // 3. Cálculo de la Flecha Negra (Conecta punta roja con punta azul)
    // Regla: Destino - Origen (v2 - v1)
    let v4 = p5.Vector.sub(v2, v1);

    // 4. Dibujar las flechas
    // La roja, azul y morada nacen en v0
    drawArrow(v0, v1, 'red');
    drawArrow(v0, v2, 'blue');
    drawArrow(v0, v3, 'purple'); 
    
    // La negra nace donde termina la roja (v0 + v1)
    let baseNegra = p5.Vector.add(v0, v1);
    drawArrow(baseNegra, v4, 'black');

    t += 0.02; // Incremento del tiempo para la animación
}

function drawArrow(base, vec, myColor) {
    let d = vec.mag(); // Longitud del vector
    let arrowSize = 12; // Tamaño de la punta (triángulo)

    push();
    stroke(myColor);
    strokeWeight(3);
    fill(myColor);
    
    // Transformaciones
    translate(base.x, base.y);
    rotate(vec.heading());
    
    // Dibujamos la línea desde el origen local hasta su longitud 'd'
    line(0, 0, d, 0);
    
    // Dibujamos el triángulo usando 'd' como punto de referencia
    // El primer punto (d, 0) es la punta exacta.
    // Los otros dos puntos están d-arrowSize (atrás) y centrados en Y.
    triangle(d, 0, 
             d - arrowSize, -arrowSize / 2, 
             d - arrowSize, arrowSize / 2);
    pop();
}
```

¿Cómo funciona lerp() y lerpColor().

Estas funciones operan bajo el principio de interpolación lineal, que consiste en calcular un valor intermedio entre un punto de inicio y uno de llegada basándose en un porcentaje. La función lerp() toma dos valores numéricos o vectores y devuelve el dato exacto que se encuentra a una distancia específica entre ambos; por ejemplo, si el porcentaje es 0.5, devuelve el punto medio exacto. Por otro lado, lerpColor() realiza este mismo cálculo pero aplicado a los canales de color rojo, verde y azul, mezclando cromáticamente dos colores para generar una transición suave que depende totalmente de ese mismo valor porcentual.

¿Cómo se dibuja una flecha usando drawArrow()?

El dibujo de la flecha se basa en transformar el sistema de coordenadas para simplificar la geometría. Primero se traslada el origen al punto de inicio y se rota el lienzo según la dirección del vector, lo que permite que la flecha siempre se dibuje como una línea horizontal hacia la derecha sin importar su inclinación real. Una vez orientado el lienzo, se traza la línea principal hasta la magnitud total del vector y se añade un triángulo en el extremo final. La precisión de la punta se logra colocando el vértice delantero en la distancia máxima y los otros dos vértices un poco más atrás y centrados verticalmente, asegurando que la flecha sea siempre simétrica y esté alineada con su eje.

### Actividad 7
Cuál es el concepto del marco motion 101 y cómo se interpreta geométricamente.
Son los conceptos basicos del movimiento de una sujeto a diferentes velocidades cuyo valor va cambiando progresivamentre, tambien dicho concepto puede calcular la velocidad que el usario lo asigna y permita mantener una aceleracion constante a la particula que se le asigna. El Motion 101 es un acelerador de particulas en pocoas palabras.
¿Cómo se aplica motion 101 en el ejemplo?
El concepto de Motion 101 se aplica en este código mediante la integración de la velocidad como el factor de cambio constante sobre la ubicación del objeto. Esta jerarquía física se hace efectiva dentro del método update(), donde la instrucción this.position.add(this.velocity) cumple con la regla fundamental de que la posición de un cuerpo en el siguiente instante es el resultado de sumar su velocidad actual a su posición presente. Al encapsular estos vectores dentro de una clase, el programa simula un comportamiento físico básico donde el movimiento no se define teletransportando al objeto a coordenadas fijas, sino acumulando pequeños desplazamientos en cada fotograma del ciclo de dibujo, lo que genera la ilusión de una trayectoria fluida y continua en el lienzo.

### Actividad 8
¿Qué observaste cuando usas cada una de las aceleraciones propuestas?
Con la aceleración constante, el objeto muestra un comportamiento mecánico y determinado; aunque comienza con una velocidad lenta, rápidamente gana ímpetu en una dirección fija, lo que demuestra que incluso un empuje pequeño, si es persistente, termina por crear una velocidad descontrolada que requiere límites para no perderse fuera del lienzo. En el caso de la aceleración aleatoria, el movimiento se vuelve errático y nervioso, similar al de un insecto o una partícula en suspensión; aquí la aceleración cambia en cada fotograma, lo que provoca que la velocidad nunca logre estabilizarse en una dirección, resultando en un objeto que parece "vibrar" o deambular sin un rumbo claro por el espacio. Finalmente, con la aceleración hacia el mouse, se observa el efecto más orgánico de los tres, ya que el objeto desarrolla una intención. En este escenario, el vector de aceleración se recalcula constantemente según la posición del cursor, creando un efecto de atracción magnética donde el objeto no solo persigue al objetivo, sino que suele "orbitarlo" o pasarse de largo debido a la inercia acumulada, demostrando perfectamente cómo la aceleración es la fuerza que moldea la trayectoria en respuesta al entorno.

## Bitácora de aplicación 
### Actividad 9

Esta obra es una simulación poética de un ecosistema nocturno donde la física se convierte en el lenguaje de la emoción. El concepto central es la reactividad orgánica: la idea de que el entorno digital no solo debe responder al usuario, sino que debe hacerlo con una inercia y una fluidez que imiten la vida real. La pieza evoca un jardín místico donde la luz no es estática, sino un subproducto del movimiento y la perturbación, sugiriendo que la belleza surge de la interacción entre el hombre y la naturaleza.
Las Reglas de Aceleración y su Propósito:
Para dotar de vida a este sistema, apliqué tres reglas distintas de aceleración, cada una con una intención narrativa y técnica específica:
Aceleración de Restauración (Elasticidad): En las briznas de pasto, la aceleración se calcula como una fuerza opuesta al desplazamiento (basada en la Ley de Hooke). Esta fue una decisión de diseño para generar una sensación de resistencia y peso; quería que el pasto "luchara" por volver a su estado original tras ser desplazado por el viento o el cursor, otorgándole una cualidad táctil y material al código.
Aceleración por Ruido (Campo de Flujo): El viento utiliza una aceleración gobernada por Perlin Noise. A diferencia de una aceleración aleatoria pura, esta regla crea una coherencia espacial. Artísticamente, esto busca evocar la invisible pero rítmica presencia del aire, haciendo que el jardín entero respire al unísono en lugar de vibrar de forma caótica.
Aceleración por Impulso y Disipación (Damping): En las luciérnagas, apliqué una aceleración inicial explosiva seguida de una disipación constante de la velocidad. Esta exploración artística busca imitar el vuelo errático de los insectos, donde cada destello es un esfuerzo físico que se agota lentamente, reforzando la idea de la efimeridad de la luz en la oscuridad.
En conjunto, estas reglas transforman el simple algoritmo de Motion 101 en una exploración sobre la inercia y la vida, donde la aceleración no es solo un cambio de velocidad, sino la "voluntad" de los objetos dentro del lienzo digital.

```` js
let blades = [];
let fireflies = [];
let t = 0; 

function setup() {
  createCanvas(windowWidth, windowHeight);
  let spacing = 30;
  // Crear el campo con perspectiva
  for (let z = 0; z < 250; z += 20) {
    for (let x = -100; x < width + 200; x += spacing) {
      let xPos = x - z * 0.5; 
      let yPos = height * 0.4 + z;
      blades.push(new Blade(xPos, yPos, z));
    }
  }
}

function draw() {
  background(255); 
  t += 0.05; // El paso del tiempo para el viento

  // Dibujar de atrás hacia adelante para la profundidad
  blades.sort((a, b) => a.z - b.z);

  for (let b of blades) {
    
    // --- 1. CÁLCULO DE FUERZAS (AQUÍ DECIDIMOS EL COMPORTAMIENTO) ---
    
    // Fuerza A: El Viento (Generativo)
    let n = noise(b.base.x * 0.005, b.base.y * 0.005, t);
    let windAngle = map(n, 0, 1, -PI, PI);
    let wind = p5.Vector.fromAngle(windAngle).mult(0.45);
    
    // Fuerza B: El Mouse (Interacción)
    let mouseForce = createVector(0, 0);
    let d = dist(mouseX, mouseY, b.position.x, b.position.y);
    if (d < 100) {
      mouseForce = p5.Vector.sub(b.position, createVector(mouseX, mouseY));
      mouseForce.setMag(map(d, 0, 100, 4, 0));
      
      // Si el mouse agita el pasto, nacen luciérnagas
      if (dist(mouseX, mouseY, pmouseX, pmouseY) > 2 && random(1) < 0.07) {
        fireflies.push(new Firefly(b.position.x, b.position.y));
      }
    }

    // Fuerza C: La Elasticidad (El pasto queriendo volver a su sitio)
    let spring = p5.Vector.sub(b.anchor, b.position).mult(0.08);

    // --- 2. APLICACIÓN DE FUERZAS A LA ACELERACIÓN ---
    b.applyForce(wind);
    b.applyForce(mouseForce);
    b.applyForce(spring);

    // --- 3. EJECUCIÓN DEL MOTOR MOTION 101 ---
    b.update();
    b.display();
  }

  // Dibujar luciérnagas
  for (let i = fireflies.length - 1; i >= 0; i--) {
    fireflies[i].update();
    fireflies[i].display();
    if (fireflies[i].isDead()) fireflies.splice(i, 1);
  }
}

class Blade {
  constructor(x, y, z) {
    this.base = createVector(x, y);
    this.h = map(z, 0, 250, 40, 100);
    this.z = z;

    // Componentes de Motion 101
    this.position = createVector(x, y - this.h); 
    this.velocity = createVector(0, 0);
    this.acceleration = createVector(0, 0);
    
    this.anchor = this.position.copy(); // Punto original de la punta
    this.topSpeed = 7;
  }

  // Este método es el "acumulador" de fuerzas
  applyForce(force) {
    this.acceleration.add(force); 
  }

  update() {
    // >>> INICIO DE MOTION 101 <<<
    
    // 1. La aceleración cambia la velocidad
    this.velocity.add(this.acceleration);
    
    // 2. Limitamos la velocidad para que no sea infinita
    this.velocity.limit(this.topSpeed);
    
    // 3. La velocidad cambia la posición
    this.position.add(this.velocity);
    
    // 4. RESET: La aceleración debe volver a cero en cada frame
    // Si no la reseteas, las fuerzas se acumulan eternamente
    this.acceleration.mult(0);
    
    // 5. Rozamiento (Damping): para que el pasto eventualmente se detenga
    this.velocity.mult(0.9);
    
    // >>> FIN DE MOTION 101 <<<
  }

  display() {
    stroke(0);
    strokeWeight(map(this.z, 0, 250, 1, 4));
    noFill();
    
    // Dibujamos una curva estética (Bézier)
    // El punto de control se mueve un poco con la velocidad para dar fluidez
    let cpX = this.base.x + (this.velocity.x * 3);
    let cpY = (this.base.y + this.position.y) / 2;
    
    bezier(this.base.x, this.base.y, cpX, cpY, cpX, cpY, this.position.x, this.position.y);
  }
}

class Firefly {
  constructor(x, y) {
    this.position = createVector(x, y);
    this.velocity = p5.Vector.random2D().mult(random(1, 2));
    this.acceleration = createVector(0, -0.05); // Fuerza constante hacia arriba
    this.lifespan = 255;
  }

  update() {
    // Las luciérnagas también son pequeñas máquinas Motion 101
    this.velocity.add(this.acceleration);
    this.position.add(this.velocity);
    this.lifespan -= 4;
  }

  display() {
    noStroke();
    fill(255, 230, 0, this.lifespan);
    ellipse(this.position.x, this.position.y, 4);
    fill(255, 255, 0, this.lifespan * 0.2);
    ellipse(this.position.x, this.position.y, 10);
  }

  isDead() { return this.lifespan < 0; }
}
````
https://editor.p5js.org/JorgeLuisSuarique/sketches/lOw71JjbT
<img width="792" height="487" alt="image" src="https://github.com/user-attachments/assets/253ced16-b709-4b53-a667-24afa6ce2cb5" />


## Bitácora de reflexión


