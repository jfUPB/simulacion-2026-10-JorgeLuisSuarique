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

- **Concepto visual.**

Autopista de datos: es una ciudad holográfica cyberpunk donde agentes luminosos (naves o vehículos de datos) circulan por un campo de flujo que simula una red de avenidas digitales. La masa de agentes se comprime en las intersecciones y se dispersa en las rectas, traduciendo visualmente la tensión entre la euforia rítmica y la melancolía atmosférica de la canción. Los cubos holográficos representan los edificios de la ciudad distópica, y las líneas de flujo forman el mapa urbano. La pieza funciona como un instrumento visual que el performer puede tocar en tiempo real.

- **Relación entre la visual y la canción.**

"DYSTOPIA" tiene un BPM de 139 y una dualidad emocional única: ritmo rápido y eufórico pero atmósfera melancólica y oscura. La visual responde directamente a esta dualidad. Los graves (bajos y bombo) controlan la expansión y contracción del campo de flujo, como latidos de la ciudad viva. Los medios (voces y sintetizadores) cambian la paleta de colores entre cian, magenta y azul neón. Los agudos (hats y texturas) aumentan la velocidad máxima y la fuerza de dirección de los agentes, acelerando la ciudad cuando la canción se intensifica. La amplitud general controla la densidad de agentes en escena, creciendo hacia los clímax y disminuyendo en los pasajes más íntimos.

- **Moodboard o referencias.**

- Tron Legacy (2010) — escenas del grid → Autopistas de luz, líneas neón sobre negro absoluto, sensación de velocidad inmersiva.

- Blade Runner 2049 — hologramas urbanos → Mapas de ciudad flotantes, densos y azules, con texturas de interferencia.

- Stuz0r — "Cyberpunk City" (serie de ilustraciones) → Cubos isométricos, neón magenta/cian, atmósfera lluviosa y decadente.

- Incredibox Dystopia — trailer oficial → Visores LED, cyborgs, texturas glitch, paleta oscura con acentos brillantes.

- Pinterest: "holographic city map cyberpunk" → Cuadrículas brillantes, puntos de datos flotantes, mapas aéreos con profundidad.

- **Dos o más bocetos.**

<img width="1359" height="763" alt="image" src="https://github.com/user-attachments/assets/c4859279-b5d2-466c-ad0c-63cc240c7826" />
<img width="562" height="696" alt="image" src="https://github.com/user-attachments/assets/c253e398-9480-46ff-b618-79f730c4f009" />


- **Mapa de decisiones.**

<img width="1494" height="542" alt="image" src="https://github.com/user-attachments/assets/9ffb0105-a48e-4c08-a17a-928ea18e15cd" />

- **Mapa de interpretación.**

<img width="1127" height="849" alt="image" src="https://github.com/user-attachments/assets/90a261d0-b2e3-429a-8178-6bd763beea2d" />


- **Justificación del algoritmo elegido.**

Elegí una combinación híbrida de campo de flujo (flow field) y bandada (flocking) porque la canción "DYSTOPIA" tiene una dualidad entre el orden mecánico y el caos orgánico. El campo de flujo proporciona una estructura tipo autopista que refleja la parte rítmica y eufórica, mientras que las reglas de flocking aportan imprevisibilidad y vida colectiva, traduciendo la melancolía y la tensión emocional. Esta mezcla permite que el intérprete controle en vivo el equilibrio entre ambos, haciendo que la visual sea tan dinámica y contrastante como la música.

- **Explicación de la relación audio-visual.**

La relación audio-visual se basa en el análisis en tiempo real de la frecuencia y amplitud de la canción mediante FFT. Los graves modifican el color y la escala del campo de flujo, haciendo que la cuadrícula de líneas se tiña de magenta y pulse al ritmo del bombo. Los agudos controlan la velocidad y la fuerza de los agentes, acelerando el movimiento de las partículas en los momentos más intensos. La energía general ajusta la densidad de agentes, de modo que la música no es un fondo, sino el motor que esculpe constantemente la forma, el color y la dinámica de la ciudad holográfica.

- **Evidencia del uso de IA.**

La IA me ayudo en el refuerzo de la idea, me ayudó a crear el script para este proyecto, mientras yo lo guiaba enfocándome en los resultados y la idea artística. Durante este proceso tenia siempre una idea, pero habían conceptos técnicos como el nombre del estilo y patrones al usarlo que la IA me ayudo a esclarecer, mientras yo me aseguraba de cada idea en la manera de como mostrarla y en que perspectiva evidenciar los resultados.

- **Código fuente.**
```` js
// DYSTOPIA - Autopista de Datos v2
// Partículas con ciclo de vida + ciudad isométrica + audio reactivo

let agents = [];
let flowField;
let fft;
let audio;
let isPlaying = false;

// Parámetros del sistema
let agentCount = 150;
let useFlowField = true;
let useFlocking = true;
let colorMode = 0;
let nightMode = false;

// Controles performativos
let maxspeedBase = 5;
let maxforceBase = 0.3;
let mouseForceMult = 1.0;
let mouseSpeedMult = 1.0;

// Elementos visuales
let cityBlocks = [];
let trailsEnabled = true;
let repeller = null;
let repellerTimer = 0;

// Ciclo de vida
let agentLifespanMax = 300;    // frames que vive cada agente
let spawnRate = 2;             // cuántos agentes nuevos por frame al mantener densidad

// Paletas de colores (se pueden modificar dinámicamente con el audio)
const palettes = [
  { agent1: [0, 255, 255], agent2: [0, 150, 255], cityTop: [0, 200, 255], cityLeft: [0, 100, 200], cityRight: [0, 50, 150] },
  { agent1: [255, 0, 255], agent2: [200, 0, 150], cityTop: [255, 100, 255], cityLeft: [180, 0, 180], cityRight: [120, 0, 120] },
  { agent1: [255, 255, 0], agent2: [255, 100, 0], cityTop: [255, 200, 0], cityLeft: [200, 100, 0], cityRight: [150, 50, 0] },
  { agent1: [100, 255, 150], agent2: [50, 200, 100], cityTop: [100, 255, 150], cityLeft: [50, 180, 80], cityRight: [20, 100, 40] }
];

// Variables para efectos de audio
let bassHue = 0;      // para cambio de color dinámico
let trebleIntensity = 1;

function setup() {
  createCanvas(windowWidth, windowHeight);
  initCityBlocks();
  flowField = new FlowField(30);
  
  // Crear agentes iniciales
  for (let i = 0; i < agentCount; i++) {
    agents.push(new HybridAgent(random(width), random(height)));
  }
  
  // Inicializar FFT
  fft = new p5.FFT();
  
  // Configurar audio (cambia el nombre si es necesario: 'Dystopia.mp3')
  userStartAudio().then(() => {
    audio = loadSound('Dystopia.mp3', 
      () => {
        audio.loop();
        isPlaying = true;
        fft.setInput(audio);
      },
      (err) => {
        console.error("Error cargando audio, usando micrófono");
        getAudioContext().resume();
        let mic = new p5.AudioIn();
        mic.start();
        fft.setInput(mic);
        isPlaying = true;
      }
    );
  }).catch(() => console.log("Esperando clic"));
}

function draw() {
  background(0, nightMode ? 30 : 20);
  
  // Actualizar audio y efectos
  if (isPlaying && fft && typeof fft.getLevel === 'function') {
    updateFromAudio();
  }
  
  // Dibujar ciudad isométrica
  drawCityIso();
  
  // Dibujar campo de flujo (sutil)
  if (useFlowField && frameCount % 5 === 0) {
    drawFlowFieldDebug();
  }
  
  // Actualizar repeller temporal
  if (repeller && millis() - repellerTimer > 1500) {
    repeller = null;
  }
  
  // Actualizar agentes y eliminar muertos
  for (let i = agents.length - 1; i >= 0; i--) {
    let agent = agents[i];
    
    if (useFlowField) agent.follow(flowField);
    if (useFlocking) agent.flock(agents);
    if (repeller) agent.applyForce(repeller.repel(agent));
    
    applyMouseForces(agent);
    agent.update();
    agent.show(trailsEnabled);
    
    if (agent.isDead()) {
      agents.splice(i, 1);
    }
  }
  
  // Mantener densidad (crear nuevos agentes para reemplazar muertos)
  let targetCount = agentCount;
  while (agents.length < targetCount) {
    for (let i = 0; i < spawnRate; i++) {
      agents.push(new HybridAgent(random(width), random(height)));
    }
  }
  if (agents.length > targetCount) {
    agents = agents.slice(0, targetCount);
  }
}

function updateFromAudio() {
  let level = fft.getLevel();
  let bassEnergy = fft.getEnergy(20, 100);
  let trebleEnergy = fft.getEnergy(2000, 12000);
  
  // Efecto 1: cambio de paleta con los graves
  // Mapeamos bassEnergy (0-255) a índice de paleta (0-3) con transición suave
  let newColorMode = floor(map(bassEnergy, 0, 255, 0, palettes.length));
  colorMode = constrain(newColorMode, 0, palettes.length - 1);
  
  // Efecto 2: intensidad de brillo con agudos
  trebleIntensity = map(trebleEnergy, 0, 255, 0.8, 1.5);
  
  // Ajuste de flujo y velocidades
  let bassNorm = map(bassEnergy, 0, 255, 0.7, 1.5);
  flowField.setScale(bassNorm);
  
  let trebleNorm = map(trebleEnergy, 0, 255, 0.8, 1.8);
  let dynamicSpeed = constrain(maxspeedBase * trebleNorm * mouseSpeedMult, 2, 12);
  let dynamicForce = constrain(maxforceBase * trebleNorm * mouseForceMult, 0.1, 1.0);
  
  let targetCount = floor(map(level, 0, 0.3, 60, 280));
  if (!isNaN(targetCount)) agentCount = constrain(targetCount, 50, 300);
  
  for (let agent of agents) {
    agent.maxspeed = dynamicSpeed;
    agent.maxforce = dynamicForce;
  }
  
  // Pulso visual en edificios (se hace en drawCityIso)
  pulseCityIso(bassNorm);
}

function applyMouseForces(agent) {
  let mouse = createVector(mouseX, mouseY);
  let distToMouse = p5.Vector.dist(agent.position, mouse);
  
  if (mouseIsPressed && mouseButton === LEFT && distToMouse < 100) {
    let force = p5.Vector.sub(mouse, agent.position);
    let strength = map(distToMouse, 0, 100, 0.8, 0);
    force.setMag(strength);
    agent.applyForce(force);
  } else if (mouseIsPressed && mouseButton === RIGHT && distToMouse < 150) {
    let force = p5.Vector.sub(agent.position, mouse);
    let strength = map(distToMouse, 0, 150, 1.0, 0);
    force.setMag(strength);
    agent.applyForce(force);
  }
}

// ---------- Ciudad isométrica cúbica ----------
function initCityBlocks() {
  cityBlocks = [];
  let cols = floor(width / 70);
  let rows = floor(height / 70);
  for (let i = 0; i < cols; i++) {
    for (let j = 0; j < rows; j++) {
      if (random() > 0.65) { // densidad
        let x = (i - cols/2) * 70 + random(-15, 15);
        let y = (j - rows/2) * 70 + random(-15, 15);
        let h = random(20, 100);
        cityBlocks.push({ x, y, h, w: 35 });
      }
    }
  }
}

function drawCityIso() {
  let pal = palettes[colorMode];
  let angle = radians(30);
  let cosAngle = cos(angle);
  let sinAngle = sin(angle);
  
  for (let block of cityBlocks) {
    let x = block.x;
    let y = block.y;
    let h = block.h * (0.8 + trebleIntensity * 0.2); // altura modulada por agudos
    let w = block.w;
    
    // Coordenadas isométricas del suelo
    let x0 = width/2 + (x - y) * cosAngle;
    let y0 = height/2 + (x + y) * sinAngle;
    
    // Vértices del cubo (suelo y techo)
    let p1 = {x: x0, y: y0};                         // frente
    let p2 = {x: x0 + w * cosAngle, y: y0 + w * sinAngle}; // derecha
    let p3 = {x: x0, y: y0 + w * 2 * sinAngle};            // atrás
    let p4 = {x: x0 - w * cosAngle, y: y0 + w * sinAngle}; // izquierda
    
    // Cara superior (techo)
    fill(pal.cityTop[0], pal.cityTop[1], pal.cityTop[2], 180);
    beginShape();
    vertex(p1.x, p1.y - h);
    vertex(p2.x, p2.y - h);
    vertex(p3.x, p3.y - h);
    vertex(p4.x, p4.y - h);
    endShape(CLOSE);
    
    // Cara izquierda
    fill(pal.cityLeft[0], pal.cityLeft[1], pal.cityLeft[2], 150);
    beginShape();
    vertex(p1.x, p1.y);
    vertex(p4.x, p4.y);
    vertex(p4.x, p4.y - h);
    vertex(p1.x, p1.y - h);
    endShape(CLOSE);
    
    // Cara derecha
    fill(pal.cityRight[0], pal.cityRight[1], pal.cityRight[2], 150);
    beginShape();
    vertex(p1.x, p1.y);
    vertex(p2.x, p2.y);
    vertex(p2.x, p2.y - h);
    vertex(p1.x, p1.y - h);
    endShape(CLOSE);
  }
}

function pulseCityIso(intensity) {
  // Hacemos vibrar ligeramente los edificios (efecto de pulso)
  for (let block of cityBlocks) {
    // Esto modifica temporalmente la altura; se restablece en cada frame
    // pero como pulseCityIso se llama desde updateFromAudio, la altura se modifica dinámicamente
    block.h = constrain(block.h * (0.98 + intensity * 0.05), 20, 120);
  }
}

// ---------- Flow field y agentes ----------

function drawFlowFieldDebug() {
  // Colorear según los graves (bassEnergy se actualiza en updateFromAudio)
  let bass = fft ? fft.getEnergy(20, 100) : 128;
  let r = map(bass, 0, 255, 0, 255);
  let g = map(bass, 0, 255, 100, 255);
  let b = map(bass, 0, 255, 200, 255);
  
  // Grosor y longitud según agudos
  let treble = fft ? fft.getEnergy(2000, 12000) : 128;
  let thickness = map(treble, 0, 255, 0.5, 2.5);
  let lengthScale = map(treble, 0, 255, 4, 12);
  
  stroke(r, g, b, 180);
  strokeWeight(thickness);
  
  for (let i = 0; i < flowField.cols; i++) {
    for (let j = 0; j < flowField.rows; j++) {
      let v = flowField.field[i][j];
      let x = i * flowField.resolution;
      let y = j * flowField.resolution;
      let dx = v.x * lengthScale;
      let dy = v.y * lengthScale;
      line(x, y, x + dx, y + dy);
      
      // Pequeño destello en cada punto de la cuadrícula (opcional)
      stroke(r, g, b, 100);
      point(x, y);
    }
  }
}

function mousePressed() {
  if (mouseButton === LEFT) {
    // En lugar de crear nuevos agentes, redirige los cercanos al mouse
    let mousePos = createVector(mouseX, mouseY);
    let countRedirected = 0;
    for (let agent of agents) {
      let d = p5.Vector.dist(agent.position, mousePos);
      if (d < 100) {
        // Nueva dirección: aleatoria + un poco hacia el mouse (efecto "empuje")
        let desiredDir = p5.Vector.sub(mousePos, agent.position);
        desiredDir.setMag(agent.maxspeed);
        // Mezcla: 70% dirección aleatoria, 30% hacia el mouse (para mantener la esencia)
        let randomDir = p5.Vector.random2D();
        randomDir.setMag(agent.maxspeed);
        let newVel = p5.Vector.lerp(randomDir, desiredDir, 0.3);
        agent.velocity = newVel;
        // Reiniciar vida para que no muera pronto
        agent.lifespan = agentLifespanMax;
        countRedirected++;
      }
    }
    console.log(`Redirigidos ${countRedirected} agentes`);
  } else if (mouseButton === RIGHT) {
    repeller = new TempRepeller(mouseX, mouseY);
    repellerTimer = millis();
  }
}

function keyPressed() {
  switch(key) {
    case 'f': case 'F': useFlowField = !useFlowField; break;
    case 'g': case 'G': useFlocking = !useFlocking; break;
    case 'c': case 'C': colorMode = (colorMode + 1) % palettes.length; break;
    case 'n': case 'N': nightMode = !nightMode; break;
    case '+': agentCount = constrain(agentCount + 20, 50, 300); break;
    case '-': agentCount = constrain(agentCount - 20, 50, 300); break;
  }
}

function mouseMoved() {
  mouseForceMult = map(mouseX, 0, width, 0.5, 2.0);
  mouseSpeedMult = map(mouseY, 0, height, 0.5, 2.0);
}

function windowResized() {
  resizeCanvas(windowWidth, windowHeight);
  initCityBlocks();
  flowField = new FlowField(30);
}

// ---------------------- CLASES ----------------------
class FlowField {
  constructor(r) {
    this.resolution = r;
    this.cols = floor(width / this.resolution) + 1;
    this.rows = floor(height / this.resolution) + 1;
    this.field = new Array(this.cols);
    for (let i = 0; i < this.cols; i++) this.field[i] = new Array(this.rows);
    this.init();
    this.scale = 1.0;
  }
  init() {
    noiseSeed(random(10000));
    let xoff = 0;
    for (let i = 0; i < this.cols; i++) {
      let yoff = 0;
      for (let j = 0; j < this.rows; j++) {
        let angle = map(noise(xoff, yoff), 0, 1, 0, TWO_PI);
        this.field[i][j] = p5.Vector.fromAngle(angle);
        yoff += 0.1;
      }
      xoff += 0.1;
    }
  }
  setScale(s) { this.scale = s; }
  lookup(position) {
    let col = constrain(floor(position.x / this.resolution), 0, this.cols - 1);
    let row = constrain(floor(position.y / this.resolution), 0, this.rows - 1);
    let v = this.field[col][row].copy();
    v.mult(this.scale);
    return v;
  }
}

class HybridAgent {
  constructor(x, y) {
    this.position = createVector(x, y);
    this.velocity = p5.Vector.random2D();
    this.velocity.setMag(random(1, 3));
    this.acceleration = createVector(0, 0);
    this.r = 4;
    this.maxspeed = 5;
    this.maxforce = 0.3;
    this.trail = [];
    this.trailMax = 15;
    this.lifespan = agentLifespanMax;   // <--- nuevo: vida
  }
  
  applyForce(force) { this.acceleration.add(force); }
  
  follow(flow) {
    let desired = flow.lookup(this.position);
    desired.setMag(this.maxspeed);
    let steer = p5.Vector.sub(desired, this.velocity);
    steer.limit(this.maxforce);
    this.applyForce(steer);
  }
  
  flock(agents) {
    let sep = this.separate(agents);
    let ali = this.align(agents);
    let coh = this.cohere(agents);
    sep.mult(1.2);
    ali.mult(1.0);
    coh.mult(1.0);
    this.applyForce(sep);
    this.applyForce(ali);
    this.applyForce(coh);
  }
  
  separate(agents) {
    let desiredSep = 25;
    let steer = createVector(0, 0);
    let count = 0;
    for (let other of agents) {
      if (other === this) continue;
      let d = p5.Vector.dist(this.position, other.position);
      if (d > 0 && d < desiredSep) {
        let diff = p5.Vector.sub(this.position, other.position);
        diff.normalize();
        diff.div(d);
        steer.add(diff);
        count++;
      }
    }
    if (count > 0) {
      steer.div(count);
      steer.setMag(this.maxspeed);
      steer.sub(this.velocity);
      steer.limit(this.maxforce);
    }
    return steer;
  }
  
  align(agents) {
    let neighborDist = 50;
    let sum = createVector(0, 0);
    let count = 0;
    for (let other of agents) {
      if (other === this) continue;
      let d = p5.Vector.dist(this.position, other.position);
      if (d > 0 && d < neighborDist) {
        sum.add(other.velocity);
        count++;
      }
    }
    if (count > 0) {
      sum.div(count);
      sum.setMag(this.maxspeed);
      let steer = p5.Vector.sub(sum, this.velocity);
      steer.limit(this.maxforce);
      return steer;
    }
    return createVector(0, 0);
  }
  
  cohere(agents) {
    let neighborDist = 50;
    let sum = createVector(0, 0);
    let count = 0;
    for (let other of agents) {
      if (other === this) continue;
      let d = p5.Vector.dist(this.position, other.position);
      if (d > 0 && d < neighborDist) {
        sum.add(other.position);
        count++;
      }
    }
    if (count > 0) {
      sum.div(count);
      return this.seek(sum);
    }
    return createVector(0, 0);
  }
  
  seek(target) {
    let desired = p5.Vector.sub(target, this.position);
    desired.setMag(this.maxspeed);
    let steer = p5.Vector.sub(desired, this.velocity);
    steer.limit(this.maxforce);
    return steer;
  }
  
  update() {
    this.velocity.add(this.acceleration);
    this.velocity.limit(this.maxspeed);
    this.position.add(this.velocity);
    this.acceleration.mult(0);
    
    // Reducir vida
    this.lifespan -= 1;
    
    // Guardar trail
    this.trail.push(this.position.copy());
    if (this.trail.length > this.trailMax) this.trail.shift();
    
    // Wraparound
    if (this.position.x < 0) this.position.x = width;
    if (this.position.x > width) this.position.x = 0;
    if (this.position.y < 0) this.position.y = height;
    if (this.position.y > height) this.position.y = 0;
  }
  
  show(trailsOn) {
    let pal = palettes[colorMode];
    let angle = this.velocity.heading();
    // La opacidad se reduce conforme la vida disminuye
    let alpha = nightMode ? 150 : 220;
    alpha *= map(this.lifespan, 0, agentLifespanMax, 0.3, 1.0);
    
    // Trail también se desvanece
    if (trailsOn && this.trail.length > 1) {
      for (let i = 0; i < this.trail.length - 1; i++) {
        let t = map(i, 0, this.trail.length, 0.2, 1);
        let alphaTrail = map(this.lifespan, 0, agentLifespanMax, 20, 120) * t;
        stroke(pal.agent1[0], pal.agent1[1], pal.agent1[2], alphaTrail);
        strokeWeight(2);
        line(this.trail[i].x, this.trail[i].y, this.trail[i+1].x, this.trail[i+1].y);
      }
    }
    
    push();
    translate(this.position.x, this.position.y);
    rotate(angle);
    fill(pal.agent1[0], pal.agent1[1], pal.agent1[2], alpha);
    stroke(pal.agent2[0], pal.agent2[1], pal.agent2[2], alpha);
    strokeWeight(1);
    beginShape();
    vertex(this.r * 2, 0);
    vertex(-this.r * 2, -this.r);
    vertex(-this.r * 2, this.r);
    endShape(CLOSE);
    pop();
  }
  
  isDead() {
    return this.lifespan <= 0;
  }
}

class TempRepeller {
  constructor(x, y) {
    this.position = createVector(x, y);
    this.power = 200;
  }
  repel(agent) {
    let force = p5.Vector.sub(this.position, agent.position);
    let distance = constrain(force.mag(), 10, 100);
    let strength = this.power / (distance * distance);
    force.setMag(strength);
    return force;
  }
}
````
- **Enlace al sketch.**

https://editor.p5js.org/JorgeLuisSuarique/sketches/wwIZjVNgi

- **Capturas o registros de momentos importantes de la pieza.**

<img width="856" height="818" alt="image" src="https://github.com/user-attachments/assets/08ce463b-8758-42df-881d-29de1fda89b2" />


## Bitácora de reflexión
