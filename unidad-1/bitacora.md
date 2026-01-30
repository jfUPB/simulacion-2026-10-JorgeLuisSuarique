# Unidad 1
## Bitácora de proceso de aprendizaje

## Actividad 1.
### Frase.
Si un Artista Lanza una moneda hará que cada cara te muestre un sinfín de obras maestras.

## Actividad 2.
### Codigo Original.
``` js
// The Nature of Code
// Daniel Shiffman
// http://natureofcode.com

let walker;

function setup() {
  createCanvas(640, 240);
  walker = new Walker();
  background(255);
}

function draw() {
  walker.step();
  walker.show();
}

class Walker {
  constructor() {
    this.x = width / 2;
    this.y = height / 2;
  }

  show() {
    stroke(0);
    point(this.x, this.y);
  }

  step() {
    const choice = floor(random(4));
    if (choice == 0) {
      this.x++;
    } else if (choice == 1) {
      this.x--;
    } else if (choice == 2) {
      this.y++;
    } else {
      this.y--;
    }
  }
}
```
<img width="274" height="237" alt="image" src="https://github.com/user-attachments/assets/facbe298-e8ba-4fff-a4f7-603152b0e104" />

### Que quiero que suceda.
quiero mejorar el comportamiento y el movimiento de de los trasos, cambiar la cuadricula por lineas mas curbadas y que se vea el proceso mas organicos. Visualmente, dejará de verse como el rastro digital de un videojuego de los 80 y comenzará a parecerse a un dibujo a tinta hecho a mano alzada o al patrón que deja una hormiga explorando. Este simple cambio (de 4 opciones a un ángulo aleatorio) es un salto enorme hacia la estética generativa, porque la aleatoriedad ya no solo selecciona un camino predefinido, sino que genera uno nuevo y único en cada paso.

### Codigo Nuevo.
``` js
// The Nature of Code - Walker Aleatorio Mejorado
// Modificado con movimiento angular y trazo continuo

let walker;

function setup() {
  createCanvas(640, 240);
  walker = new Walker();
  background(255); // Fondo blanco
}

function draw() {
  // Dibuja un rectángulo semitransparente para crear efecto de rastro
  fill(255, 10);
  noStroke();
  rect(0, 0, width, height);
  
  // Actualiza y muestra el caminante
  walker.step();
  walker.show();
}

class Walker {
  constructor() {
    this.x = width / 2;
    this.y = height / 2;
    this.prevX = this.x;
    this.prevY = this.y;
  }

  show() {
    stroke(0);
    strokeWeight(1);
    line(this.prevX, this.prevY, this.x, this.y);
  }

  step() {
    // Guarda la posición actual
    this.prevX = this.x;
    this.prevY = this.y;
    
    // Movimiento en ángulo aleatorio
    let angle = random(TWO_PI);
    this.x += 2 * cos(angle);
    this.y += 2 * sin(angle);
    
    // Mantiene al caminante dentro del lienzo
    this.x = constrain(this.x, 0, width);
    this.y = constrain(this.y, 0, height);
  }
}
```
<img width="115" height="104" alt="image" src="https://github.com/user-attachments/assets/ae83390e-6414-431f-8457-7e3a925533c8" />
El resultado real es que, en lugar de rellenar el lienzo con una trama de líneas rectas (como un bordado pixelado), el caminante comenzó a tejer una trama de curvas suaves y únicas, creando una composición que es imposible de predecir pero coherente en su fluidez. Es la prueba visual perfecta de tu frase: el artista (tú, al cambiar el código) diseñó una nueva "moneda" (la ruleta de los 360º) y cada lanzamiento revela una obra única del sinfín de posibilidades.


## Actividad 3.
# Diferencia entre una distribución uniforme y una no uniforme de números aleatorios.
La distribución uniforme usa un solo proceso igualitario para todos, lo que genera una secuencia impredecible y sin tendencia. La distribución no uniforme aplica una regla jerárquica desde el principio, lo que hace que, entre muchos resultados aleatorios, unos se destaquen más y creen un patrón o tendencia reconocible en el conjunto.

``` js
// The Nature of Code - Walker con Distribución NO UNIFORME
// Sesgado hacia la derecha

let walker;

function setup() {
  createCanvas(640, 240);
  walker = new Walker();
  background(255);
}

function draw() {
  // Fondo semitransparente para efecto de rastro
  fill(255, 20);
  noStroke();
  rect(0, 0, width, height);
  
  walker.step();
  walker.show();
}

class Walker {
  constructor() {
    this.x = width / 2;
    this.y = height / 2;
    this.prevX = this.x;
    this.prevY = this.y;
  }

  show() {
    stroke(0, 150, 255); // Azul para distinguirlo
    strokeWeight(1.5);
    line(this.prevX, this.prevY, this.x, this.y);
  }

  step() {
    // Guardar posición actual como anterior
    this.prevX = this.x;
    this.prevY = this.y;
    
    // DISTRIBUCIÓN NO UNIFORME: Sesgo hacia la derecha
    // random(-0.5, 1.0) significa:
    // - Valores entre -0.5 y 1.0 radianes
    // - Más rango positivo (derecha) que negativo (izquierda)
    // - Probabilidad de ángulos hacia la derecha: ~75%
    // - Probabilidad de ángulos hacia la izquierda: ~25%
    let biasedAngle = random(-0.5, 1.0);
    
    // Aplicar el movimiento con el ángulo sesgado
    this.x += 2 * cos(biasedAngle);
    this.y += 2 * sin(biasedAngle);
    
    // Mantener dentro del lienzo
    this.x = constrain(this.x, 0, width);
    this.y = constrain(this.y, 0, height);
  }
}
```

## Actividad 4.
``` js
// Visualización de Distribución Normal (Gaussiana)
// Genera y muestra cómo se distribuyen valores aleatorios alrededor de una media

let valores = [];
let totalValores = 1000;
let media = 0;
let desviacion = 80;

function setup() {
  createCanvas(800, 400);
  background(240);
  
  // Generar valores con distribución normal
  for (let i = 0; i < totalValores; i++) {
    // La función clave: randomGaussian()
    // Parámetros: media, desviación estándar
    let valor = randomGaussian(media, desviacion);
    valores.push(valor);
  }
  
  dibujarDistribucion();
  mostrarEstadisticas();
}

function dibujarDistribucion() {
  // Dibujar fondo de la gráfica
  fill(255);
  stroke(200);
  rect(50, 50, width - 100, height - 100);
  
  // Encontrar valores mínimos y máximos para escalar
  let minVal = min(valores);
  let maxVal = max(valores);
  
  // Crear histograma
  let numBarras = 30;
  let histograma = new Array(numBarras).fill(0);
  
  // Contar valores en cada barra del histograma
  for (let valor of valores) {
    // Mapear valor a índice de barra
    let indice = int(map(valor, minVal, maxVal, 0, numBarras - 1));
    indice = constrain(indice, 0, numBarras - 1);
    histograma[indice]++;
  }
  
  // Dibujar barras del histograma
  let maxFreq = max(histograma);
  let barWidth = (width - 100) / numBarras;
  
  fill(30, 120, 200, 180);
  noStroke();
  
  for (let i = 0; i < numBarras; i++) {
    let x = 50 + i * barWidth;
    let barHeight = map(histograma[i], 0, maxFreq, 0, height - 150);
    rect(x, height - 50 - barHeight, barWidth - 1, barHeight);
  }
  
  // Dibujar línea de la media
  stroke(255, 50, 50, 200);
  strokeWeight(2);
  let xMedia = map(media, minVal, maxVal, 50, width - 50);
  line(xMedia, 50, xMedia, height - 50);
  
  // Dibujar línea de la curva normal teórica
  dibujarCurvaNormal(minVal, maxVal);
}

function dibujarCurvaNormal(minVal, maxVal) {
  // Dibujar la curva teórica de la distribución normal
  noFill();
  stroke(50, 180, 80, 200);
  strokeWeight(2);
  
  beginShape();
  for (let x = minVal; x <= maxVal; x += (maxVal - minVal) / 100) {
    // Fórmula de la densidad de probabilidad normal
    let exponent = -0.5 * pow((x - media) / desviacion, 2);
    let y = (1 / (desviacion * sqrt(TWO_PI))) * exp(exponent);
    
    // Escalar para visualización
    let xPixel = map(x, minVal, maxVal, 50, width - 50);
    let yPixel = map(y, 0, 0.01, height - 50, 50);
    
    vertex(xPixel, yPixel);
  }
  endShape();
}

function mostrarEstadisticas() {
  // Calcular estadísticas reales
  let suma = 0;
  for (let valor of valores) {
    suma += valor;
  }
  let mediaReal = suma / valores.length;
  
  // Calcular desviación estándar real
  let sumaDiferencias = 0;
  for (let valor of valores) {
    sumaDiferencias += pow(valor - mediaReal, 2);
  }
  let desviacionReal = sqrt(sumaDiferencias / valores.length);
  
  // Mostrar texto informativo
  fill(0);
  noStroke();
  textSize(14);
  textAlign(LEFT);
  
  text("Distribución Normal (Gaussiana)", 60, 30);
  textSize(12);
  text(`Media teórica: ${media}`, 60, height - 20);
  text(`Desviación teórica: ${desviacion}`, 200, height - 20);
  text(`Media real: ${nf(mediaReal, 0, 2)}`, 400, height - 20);
  text(`Desviación real: ${nf(desviacionReal, 0, 2)}`, 550, height - 20);
  
  // Leyenda
  fill(30, 120, 200, 180);
  rect(600, 20, 15, 15);
  fill(0);
  text("Frecuencia observada", 620, 32);
  
  fill(255, 50, 50, 200);
  stroke(255, 50, 50, 200);
  strokeWeight(2);
  line(600, 45, 615, 45);
  fill(0);
  noStroke();
  text("Media", 620, 50);
  
  stroke(50, 180, 80, 200);
  strokeWeight(2);
  line(600, 60, 615, 60);
  fill(0);
  text("Curva teórica normal", 620, 65);
}

function draw() {
  // Animación opcional: añadir valores en tiempo real
  // (comenta esta sección si quieres una visualización estática)
  if (frameCount % 5 === 0 && valores.length < 5000) {
    let nuevoValor = randomGaussian(media, desviacion);
    valores.push(nuevoValor);
    
    background(240);
    dibujarDistribucion();
    mostrarEstadisticas();
  }
}

// Cambiar parámetros con clic del mouse
function mousePressed() {
  media = random(-50, 50);
  desviacion = random(30, 120);
  valores = [];
  
  for (let i = 0; i < totalValores; i++) {
    valores.push(randomGaussian(media, desviacion));
  }
  
  background(240);
  dibujarDistribucion();
  mostrarEstadisticas();
}
```
Este código es un simulador y visualizador interactivo de la Distribución Normal (Gaussiana). Su función principal es demostrar cómo funciona el azar "natural" o "orgánico", donde los valores no son todos igualmente probables, sino que tienden a agruparse alrededor de un punto central.
![https://editor.p5js.org/JorgeLuisSuarique/sketches/nCwPFBqdZ]
![Grabación 2026-01-27 130203](https://github.com/user-attachments/assets/09089132-23ff-4d4e-8ad8-f83d96ba698c)

## Actividad 5
### Explicacion
Elegí esta implementación híbrida del Vuelo de Lévy porque captura la esencia de la solución al problema del sobremuestreo que describiste —combinar muchos pasos pequeños de búsqueda local (con distribución gaussiana para un movimiento orgánico) con saltos grandes ocasionales (con una distribución power-law aproximada para simular la rareza de los desplazamientos largos)—, ofreciendo así una metáfora visual potente y eficiente de optimización de la exploración, donde la estructura emergente de racimos conectados por trazos largos no solo es matemáticamente interesante, sino también narrativa y estéticamente rica, demostrando en la práctica el poder de mezclar distribuciones de azar con intención creativa.
``` js
// Caminante con Vuelo de Lévy Mejorado
// Combina pasos pequeños frecuentes con saltos grandes ocasionales
// para optimizar la búsqueda en el espacio

let walker;
let steps = 0;
let maxSteps = 1000;
let levyJumps = 0;
let trail = [];
let maxTrailLength = 100;

function setup() {
  createCanvas(800, 500);
  walker = new Walker(width / 2, height / 2);
  background(20, 25, 35); // Fondo azul oscuro nocturno
  
  // Estilo de texto
  textFont('Arial');
  textAlign(LEFT);
  
  // Título
  fill(240, 245, 255);
  textSize(20);
  text('🦅 Vuelo de Lévy - Búsqueda Optimizada', 30, 35);
}

function draw() {
  // Fondo semitransparente para efecto de estela
  noStroke();
  fill(20, 25, 35, 15);
  rect(0, 0, width, height);
  
  // Dibujar rejilla sutil
  drawGrid();
  
  // Actualizar y mostrar caminante
  walker.step();
  walker.display();
  
  // Mostrar estadísticas
  displayStats();
  
  // Control de pasos
  steps++;
  if (steps >= maxSteps) {
    resetWalker();
  }
}

function drawGrid() {
  stroke(40, 50, 70, 60);
  strokeWeight(0.5);
  
  // Líneas verticales
  for (let x = 0; x <= width; x += 50) {
    line(x, 0, x, height);
  }
  
  // Líneas horizontales
  for (let y = 0; y <= height; y += 50) {
    line(0, y, width, y);
  }
}

function displayStats() {
  fill(200, 220, 255, 220);
  noStroke();
  textSize(12);
  
  let statsY = 70;
  let lineHeight = 22;
  
  text('📊 Estadísticas del Vuelo:', 30, statsY);
  text(`   Pasos totales: ${steps}`, 40, statsY + lineHeight);
  text(`   Saltos de Lévy: ${levyJumps}`, 40, statsY + lineHeight * 2);
  text(`   Porcentaje de saltos: ${(levyJumps/steps*100).toFixed(1)}%`, 40, statsY + lineHeight * 3);
  text(`   Tamaño actual del paso: ${walker.currentStepSize.toFixed(1)}px`, 40, statsY + lineHeight * 4);
  
  // Leyenda
  text('🎨 Leyenda:', width - 180, statsY);
  text('   ● Paso normal', width - 180, statsY + lineHeight);
  text('   ✦ Salto de Lévy', width - 180, statsY + lineHeight * 2);
  text('   ▬ Trayectoria', width - 180, statsY + lineHeight * 3);
  
  // Instrucciones
  fill(150, 200, 255);
  textSize(11);
  text('🖱️ Haz clic para nueva posición | R para reiniciar', 30, height - 20);
}

function resetWalker() {
  // Reiniciar en posición aleatoria
  walker = new Walker(random(width), random(height));
  steps = 0;
  levyJumps = 0;
  trail = [];
  background(20, 25, 35);
}

function keyPressed() {
  if (key === 'r' || key === 'R') {
    resetWalker();
  }
}

function mousePressed() {
  // Nuevo caminante en posición del clic
  walker = new Walker(mouseX, mouseY);
  steps = 0;
  levyJumps = 0;
  trail = [];
  background(20, 25, 35);
}

class Walker {
  constructor(x, y) {
    this.x = x;
    this.y = y;
    this.prevX = x;
    this.prevY = y;
    this.color = color(
      random(180, 240),
      random(180, 220),
      random(220, 255)
    );
    this.levyColor = color(255, 200, 100);
    this.currentStepSize = 0;
    this.isLevyJump = false;
  }
  
  step() {
    // Guardar posición anterior
    this.prevX = this.x;
    this.prevY = this.y;
    
    // Guardar en el historial de trayectoria
    trail.push({x: this.x, y: this.y});
    if (trail.length > maxTrailLength) {
      trail.shift();
    }
    
    // Decidir tipo de paso (Levy o normal)
    let r = random(1);
    
    if (r < 0.02) { // 2% de probabilidad de salto de Lévy
      this.isLevyJump = true;
      levyJumps++;
      
      // Salto de Lévy: paso grande con distribución power-law
      // Usamos una distribución que favorece saltos grandes pero decrecientes
      let levyStep = this.generateLevyStep();
      this.currentStepSize = levyStep;
      
      // Dirección aleatoria para el salto
      let angle = random(TWO_PI);
      this.x += levyStep * cos(angle);
      this.y += levyStep * sin(angle);
      
    } else { // 98% pasos normales pequeños
      this.isLevyJump = false;
      
      // Paso normal: distribución gaussiana centrada en paso pequeño
      let normalStep = abs(randomGaussian(5, 2));
      this.currentStepSize = normalStep;
      
      // Dirección con leve tendencia a continuar
      let angle = random(TWO_PI * 0.7);
      this.x += normalStep * cos(angle);
      this.y += normalStep * sin(angle);
    }
    
    // Mantener dentro de bordes con rebote
    if (this.x < 0 || this.x > width) {
      this.x = constrain(this.x, 0, width);
      this.x += (this.x < width/2) ? 10 : -10;
    }
    if (this.y < 0 || this.y > height) {
      this.y = constrain(this.y, 0, height);
      this.y += (this.y < height/2) ? 10 : -10;
    }
  }
  
  generateLevyStep() {
    // Generador de paso con distribución de potencia (aproximación a Lévy)
    // p(step) ∝ step^(-μ) donde μ ~ 1-3
    let u = random(0.01, 0.99);
    let mu = 2.0; // Parámetro de la distribución
    let minStep = 30;
    let maxStep = 200;
    
    // Transformación inversa para distribución power-law
    let step = minStep * pow((maxStep/minStep), u);
    step = pow(step, 1/mu);
    
    return constrain(step, minStep, maxStep);
  }
  
  display() {
    // Dibujar trayectoria histórica
    if (trail.length > 1) {
      noFill();
      stroke(this.color.levels[0], this.color.levels[1], this.color.levels[2], 80);
      strokeWeight(1);
      
      beginShape();
      for (let i = 0; i < trail.length; i++) {
        vertex(trail[i].x, trail[i].y);
      }
      endShape();
    }
    
    // Dibujar línea del último movimiento
    strokeWeight(1.5);
    if (this.isLevyJump) {
      stroke(this.levyColor);
    } else {
      stroke(this.color);
    }
    line(this.prevX, this.prevY, this.x, this.y);
    
    // Dibujar punto en posición actual
    noStroke();
    if (this.isLevyJump) {
      fill(this.levyColor);
      push();
      translate(this.x, this.y);
      rotate(frameCount * 0.1);
      star(0, 0, 8, 4, 5);
      pop();
    } else {
      fill(this.color);
      ellipse(this.x, this.y, 8, 8);
    }
    
    // Destacar paso de Lévy con efecto
    if (this.isLevyJump) {
      // Anillo de expansión
      noFill();
      stroke(this.levyColor.levels[0], this.levyColor.levels[1], this.levyColor.levels[2], 150);
      strokeWeight(1);
      ellipse(this.x, this.y, 25, 25);
    }
  }
}

// Función para dibujar estrella (para saltos de Lévy)
function star(x, y, radius1, radius2, npoints) {
  let angle = TWO_PI / npoints;
  let halfAngle = angle / 2.0;
  beginShape();
  for (let a = 0; a < TWO_PI; a += angle) {
    let sx = x + cos(a) * radius2;
    let sy = y + sin(a) * radius2;
    vertex(sx, sy);
    sx = x + cos(a + halfAngle) * radius1;
    sy = y + sin(a + halfAngle) * radius1;
    vertex(sx, sy);
  }
  endShape(CLOSE);
}
```
![https://editor.p5js.org/JorgeLuisSuarique/sketches/VDtG84O2u]
![Grabación 2026-01-27 142247](https://github.com/user-attachments/assets/1c98fe58-fcb0-45f3-8764-e28ea3b881fa)

## Actividad 6.
El resultado esperado de esta visualización era demostrar de manera interactiva y contundente la diferencia esencial entre el Ruido Perlin y la aleatoriedad pura: observar claramente cómo el Perlin genera una curva suave, coherente y orgánica (como una montaña o una ola) donde cada valor fluye naturalmente desde el anterior, creando un patrón con "memoria", mientras que el azar uniforme produce una línea quebrada, caótica e impredecible donde cada salto es un evento aislado y abrupto; esta comparación directa, junto con una aplicación práctica que muestra cómo el Perlin puede generar terrenos naturales, permite comprender que su valor no está en ser "más o menos aleatorio", sino en ofrecer un azar estructurado y con continuidad que es la base para simular la complejidad y fluidez del mundo natural en el arte generativo.
``` js
// VISUALIZACIÓN INTERACTIVA: PERLIN NOISE vs RANDOM NOISE
// Muestra la diferencia esencial entre azar orgánico y caos puro

let historicoPerlin = [];
let historicoRandom = [];
let tiempo = 0;
let velocidad = 0.02;
let modo = 'comparacion'; // 'comparacion' o 'terreno'

function setup() {
  createCanvas(1000, 600);
  
  // Inicializar historiales
  for (let i = 0; i < 200; i++) {
    historicoPerlin.push(0);
    historicoRandom.push(0);
  }
  
  background(10, 15, 25);
  textFont('Courier New');
}

function draw() {
  if (modo === 'comparacion') {
    dibujarComparacion();
  } else {
    dibujarTerreno();
  }
  
  dibujarInterfaz();
}

function dibujarComparacion() {
  // Fondo oscuro
  background(10, 15, 25);
  
  // Título
  fill(240, 245, 255);
  textSize(20);
  textAlign(CENTER);
  text('🎯 COMPARACIÓN: PERLIN NOISE vs RANDOM NOISE', width/2, 30);
  
  // Actualizar tiempo
  tiempo += velocidad;
  
  // === LADO IZQUIERDO: PERLIN NOISE ===
  push();
  translate(50, 100);
  
  // Encabezado
  fill(100, 200, 255);
  textSize(16);
  textAlign(LEFT);
  text('PERLIN NOISE (Orgánico)', 0, -30);
  
  // Generar nuevo valor Perlin
  let nuevoPerlin = noise(tiempo); // Valor entre 0 y 1
  
  // Actualizar histórico
  historicoPerlin.shift();
  historicoPerlin.push(nuevoPerlin);
  
  // Dibujar cuadrícula
  stroke(40, 60, 80, 100);
  strokeWeight(1);
  for (let x = 0; x <= 400; x += 50) {
    line(x, 0, x, 200);
  }
  for (let y = 0; y <= 200; y += 25) {
    line(0, y, 400, y);
  }
  
  // Ejes
  stroke(80, 120, 180);
  strokeWeight(2);
  line(0, 100, 400, 100); // Línea central
  line(0, 0, 0, 200); // Eje Y
  
  // Dibujar curva Perlin
  noFill();
  stroke(80, 180, 255, 220);
  strokeWeight(3);
  beginShape();
  for (let i = 0; i < historicoPerlin.length; i++) {
    let x = map(i, 0, historicoPerlin.length - 1, 0, 400);
    let y = map(historicoPerlin[i], 0, 1, 200, 0);
    vertex(x, y);
  }
  endShape();
  
  // Punto actual
  fill(80, 180, 255);
  noStroke();
  let ultimoX = 400;
  let ultimoY = map(historicoPerlin[historicoPerlin.length-1], 0, 1, 200, 0);
  ellipse(ultimoX, ultimoY, 10, 10);
  
  // Valor numérico
  textSize(12);
  fill(150, 220, 255);
  text(`Valor actual: ${nuevoPerlin.toFixed(3)}`, 300, 220);
  text(`Tiempo: ${tiempo.toFixed(2)}`, 300, 240);
  
  pop();
  
  // === LADO DERECHO: RANDOM NOISE ===
  push();
  translate(550, 100);
  
  // Encabezado
  fill(255, 150, 100);
  textSize(16);
  textAlign(LEFT);
  text('RANDOM NOISE (Caótico)', 0, -30);
  
  // Generar nuevo valor Random
  let nuevoRandom = random(1); // Valor entre 0 y 1
  
  // Actualizar histórico
  historicoRandom.shift();
  historicoRandom.push(nuevoRandom);
  
  // Dibujar cuadrícula
  stroke(80, 60, 40, 100);
  strokeWeight(1);
  for (let x = 0; x <= 400; x += 50) {
    line(x, 0, x, 200);
  }
  for (let y = 0; y <= 200; y += 25) {
    line(0, y, 400, y);
  }
  
  // Ejes
  stroke(180, 120, 80);
  strokeWeight(2);
  line(0, 100, 400, 100);
  line(0, 0, 0, 200);
  
  // Dibujar línea Random
  noFill();
  stroke(255, 150, 100, 220);
  strokeWeight(3);
  beginShape();
  for (let i = 0; i < historicoRandom.length; i++) {
    let x = map(i, 0, historicoRandom.length - 1, 0, 400);
    let y = map(historicoRandom[i], 0, 1, 200, 0);
    vertex(x, y);
  }
  endShape();
  
  // Punto actual
  fill(255, 150, 100);
  noStroke();
  let ultimoXR = 400;
  let ultimoYR = map(historicoRandom[historicoRandom.length-1], 0, 1, 200, 0);
  ellipse(ultimoXR, ultimoYR, 10, 10);
  
  // Valor numérico
  textSize(12);
  fill(255, 200, 150);
  text(`Valor actual: ${nuevoRandom.toFixed(3)}`, 300, 220);
  text(`Sin correlación temporal`, 300, 240);
  
  pop();
  
  // === EXPLICACIÓN CENTRAL ===
  fill(200, 230, 255, 220);
  textSize(14);
  textAlign(CENTER);
  
  let explicacionY = 400;
  text('🔑 DIFERENCIA FUNDAMENTAL:', width/2, explicacionY);
  textSize(12);
  text('Perlin Noise: Cada valor está CORRELACIONADO con los anteriores', width/2, explicacionY + 25);
  text('Random Noise: Cada valor es INDEPENDIENTE (sin memoria)', width/2, explicacionY + 45);
  
  // Analogía
  fill(150, 255, 150);
  text('ANALOGÍA:', width/2, explicacionY + 75);
  text('Perlin = Paseo por la montaña (cambios suaves)', width/2, explicacionY + 95);
  text('Random = Teletransportación aleatoria (saltos bruscos)', width/2, explicacionY + 115);
}

function dibujarTerreno() {
  // Visualización alternativa: terreno generado con Perlin
  background(10, 15, 25);
  
  // Título
  fill(240, 245, 255);
  textSize(20);
  textAlign(CENTER);
  text('🏔️ TERENO GENERADO CON PERLIN NOISE', width/2, 30);
  
  tiempo += velocidad * 0.5;
  
  // Generar terreno
  noStroke();
  for (let x = 0; x < width; x += 2) {
    // Usar Perlin para altura
    let noiseVal = noise(x * 0.01, tiempo);
    let altura = map(noiseVal, 0, 1, 100, height - 100);
    
    // Color según altura
    let verdes = map(altura, 100, height - 100, 100, 50);
    let alturaNorm = map(altura, 100, height - 100, 0, 1);
    
    fill(50, verdes, 30);
    rect(x, altura, 2, height - altura);
    
    // Nieve en cimas
    if (alturaNorm < 0.3) {
      fill(200, 230, 255, 150);
      rect(x, altura - 5, 2, 5);
    }
  }
  
  // Explicación
  fill(200, 230, 255);
  textSize(14);
  text('Perlin crea transiciones suaves → Terreno natural', width/2, height - 40);
  text('Random crearía picos abruptos → Terreno artificial', width/2, height - 20);
}

function dibujarInterfaz() {
  // Controles
  fill(180, 200, 255, 200);
  noStroke();
  rect(20, height - 80, 200, 60, 10);
  
  fill(10, 15, 25);
  textSize(12);
  textAlign(LEFT);
  text('🎮 CONTROLES:', 35, height - 65);
  text('ESPACIO: Cambiar vista', 35, height - 50);
  text('↑↓: Velocidad (ahora: ' + velocidad.toFixed(2) + ')', 35, height - 35);
  
  // Indicador de modo
  fill(modo === 'comparacion' ? [100, 200, 255, 200] : [150, 255, 150, 200]);
  textAlign(RIGHT);
  textSize(14);
  text(modo === 'comparacion' ? '📈 MODO COMPARACIÓN' : '🏔️ MODO TERRENO', width - 30, height - 30);
}

function keyPressed() {
  if (key === ' ') {
    modo = modo === 'comparacion' ? 'terreno' : 'comparacion';
  }
  
  if (keyCode === UP_ARROW) {
    velocidad = min(0.1, velocidad + 0.005);
  }
  
  if (keyCode === DOWN_ARROW) {
    velocidad = max(0.001, velocidad - 0.005);
  }
}
```
![https://editor.p5js.org/JorgeLuisSuarique/sketches/-Ncm5xj6w]
<img width="900" height="734" alt="image" src="https://github.com/user-attachments/assets/6705f87f-3938-4f54-8d20-b911b566507e" />








## Bitácora de aplicación 
## Actividad 7.
Una obra generativa es una creación artística en la que el artista no diseña directamente el resultado final, sino que establece un sistema de reglas, procesos y parámetros a menudo mediante código algorítmico que, al ejecutarse, produce de forma autónoma y potencialmente infinita la obra en sí. Su esencia radica en la delegación de la agencia creativa: el artista actúa como arquitecto de posibilidades, definiendo el espacio en el que operarán elementos como la aleatoriedad, el ruido procedural o la interacción en tiempo real. El resultado es una pieza viva, única en cada ejecución y en constante evolución, que explora la belleza del orden emergente, la complejidad a partir de simplicidad y el diálogo entre la intención humana y la lógica autónoma del sistema.

El código actual implementa tres conceptos de forma aislada: un campo gaussiano estático, partículas con vuelo de Lévy guiadas por ruido de Perlin individual, y un sistema de alerta que activa huida coordinada con clics. Sin embargo, no constituye una obra generativa coherente porque los conceptos no interactúan creativamente, la interacción se reduce a un único gesto (clic = huida) sin consecuencias acumulativas, y el sistema no genera comportamientos emergentes ni evoluciona, limitándose a una demostración técnica donde el usuario no puede esculpir, construir o transformar significativamente el sistema en tiempo real.

``` js
// OBRA SIMPLE: TRES CONCEPTOS, UNA VISIÓN CLARA
let particulas = [];
let gaussCentroX, gaussCentroY, gaussRadio;
let perlinTiempo = 0;
let perlinValor = 0;

function setup() {
  createCanvas(800, 600);
  
  // Inicializar centro gaussiano
  gaussCentroX = width / 2;
  gaussCentroY = height / 2;
  gaussRadio = 100;
  
  // Crear partículas simples
  for (let i = 0; i < 40; i++) {
    particulas.push(new Particula());
  }
  
  background(20);
}

function draw() {
  // CONCEPTO 1: PERLIN como estado emocional (FONDO)
  perlinTiempo += 0.01;
  perlinValor = noise(perlinTiempo); // Valor entre 0 y 1
  
  // Fondo cambia con Perlin
  let fondoH = map(perlinValor, 0, 1, 200, 280); // Azul a púrpura
  background(fondoH, 30, 50, 20);
  
  // Título que cambia con Perlin
  fill(255);
  textSize(16);
  textAlign(CENTER);
  text(`ESTADO PERLIN: ${perlinValor.toFixed(2)}`, width/2, 30);
  
  // CONCEPTO 2: GAUSSIANA como tu influencia (INTERACCIÓN)
  actualizarGaussiana();
  dibujarGaussiana();
  
  // CONCEPTO 3: LÉVY como partículas vivas (ACCIÓN)
  actualizarParticulas();
  dibujarParticulas();
  
  // Leyenda minimalista
  dibujarLeyenda();
}

function actualizarGaussiana() {
  // El centro sigue al mouse suavemente
  gaussCentroX = lerp(gaussCentroX, mouseX, 0.1);
  gaussCentroY = lerp(gaussCentroY, mouseY, 0.1);
  
  // El radio cambia con Perlin
  gaussRadio = 80 + perlinValor * 40;
}

function dibujarGaussiana() {
  // Zona de influencia gaussiana
  noFill();
  stroke(255, 200, 100, 150);
  strokeWeight(2);
  ellipse(gaussCentroX, gaussCentroY, gaussRadio * 2, gaussRadio * 2);
  
  // Centro
  fill(255, 200, 100, 200);
  noStroke();
  ellipse(gaussCentroX, gaussCentroY, 10, 10);
}

function actualizarParticulas() {
  for (let p of particulas) {
    // ¿Está dentro de la zona gaussiana?
    let distancia = dist(p.x, p.y, gaussCentroX, gaussCentroY);
    let enZonaGauss = distancia < gaussRadio;
    
    // PERLIN afecta la probabilidad general de saltos
    let probBase = map(perlinValor, 0, 1, 0.02, 0.1);
    
    // GAUSSIANA modifica la probabilidad localmente
    if (enZonaGauss) {
      // Dentro de la zona: más probabilidad de saltos largos
      p.probSalto = probBase * 3;
    } else {
      // Fuera: comportamiento normal
      p.probSalto = probBase;
    }
    
    p.actualizar();
  }
}

function dibujarParticulas() {
  for (let p of particulas) {
    p.dibujar();
  }
}

function dibujarLeyenda() {
  fill(255, 230);
  textSize(12);
  textAlign(LEFT);
  text('🌀 PERLIN: Estado emocional (fondo)', 20, height - 60);
  text('🎯 GAUSSIANA: Tu influencia (círculo)', 20, height - 40);
  text('🦅 LÉVY: Vida que explora (líneas)', 20, height - 20);
}

// ============ CLASE PARTICULA SIMPLE ============
class Particula {
  constructor() {
    this.x = random(width);
    this.y = random(height);
    this.historial = [];
    this.maxHistorial = 5;
    this.color = color(random(150, 255), random(150, 255), 255, 200);
  }
  
  actualizar() {
    // Guardar posición anterior
    this.historial.push({x: this.x, y: this.y});
    if (this.historial.length > this.maxHistorial) {
      this.historial.shift();
    }
    
    // DECISIÓN LÉVY: ¿Salto largo o paso corto?
    if (random() < this.probSalto) {
      this.saltoLevy();
    } else {
      this.pasoNormal();
    }
    
    // Mantener en pantalla
    this.x = (this.x + width) % width;
    this.y = (this.y + height) % height;
  }
  
  saltoLevy() {
    // SALTO LARGO (distribución power-law)
    let angulo = random(TWO_PI);
    let largo = pow(random(0.01, 0.99), 1/2.0) * 100; // Power-law
    
    this.x += cos(angulo) * largo;
    this.y += sin(angulo) * largo;
  }
  
  pasoNormal() {
    // PASO CORTO (distribución normal)
    let angulo = random(TWO_PI);
    let corto = random(1, 3); // Simple, no Gaussian para simplicidad
    
    this.x += cos(angulo) * corto;
    this.y += sin(angulo) * corto;
  }
  
  dibujar() {
    // Dibujar historial
    if (this.historial.length > 1) {
      for (let i = 0; i < this.historial.length - 1; i++) {
        let p1 = this.historial[i];
        let p2 = this.historial[i + 1];
        
        // Líneas más opacas si son recientes
        let alpha = map(i, 0, this.historial.length, 50, 200);
        stroke(red(this.color), green(this.color), blue(this.color), alpha);
        strokeWeight(1);
        line(p1.x, p1.y, p2.x, p2.y);
      }
    }
    
    // Dibujar partícula actual
    noStroke();
    fill(this.color);
    ellipse(this.x, this.y, 4, 4);
  }
}

function mousePressed() {
  // Interacción simple: click crea nueva partícula
  let p = new Particula();
  p.x = mouseX;
  p.y = mouseY;
  particulas.push(p);
  
  // Limitar número máximo
  if (particulas.length > 60) {
    particulas.shift();
  }
}
```
![https://editor.p5js.org/JorgeLuisSuarique/sketches/6KHU30kl2]
<img width="894" height="740" alt="image" src="https://github.com/user-attachments/assets/b8a757c8-4bcc-4542-a1d7-a9eaf1968f26" />

## Bitácora de reflexión
**1)**
La diferencia fundamental es que random() genera caos puro e independiente, donde cada valor es un evento aislado sin relación con los anteriores (como lanzar dados repetidamente), ideal para sorpresa total y eventos discretos; mientras que noise() produce aleatoriedad orgánica con memoria, creando un campo continuo donde valores cercanos son similares y las transiciones son suaves (como el curso de un río), perfecto para simular naturaleza, movimientos fluidos y variaciones espaciales coherentes. Usarías random() para barajar cartas o inicializar posiciones aleatorias, y noise() para generar terrenos montañosos o el movimiento natural de un enjambre.
**2)**
Visualmente, una caminata aleatoria con distribución uniforme produce un patrón de exploración caótica y dispersa, con trazos angulares que se extienden en todas direcciones por igual, creando una textura de líneas quebradas que llena el espacio de manera homogénea pero sin estructura clara. En cambio, una con distribución normal (gaussiana) genera un movimiento orgánico y concentrado, donde la mayoría de los pasos son pequeños y similares, ocasionalmente interrumpidos por desplazamientos más largos pero raros, resultando en trazos más suaves, curvilíneos y con una tendencia a formar racimos o núcleos de actividad densa, imitando el comportamiento errante natural de insectos o partículas en un fluido.
**3)**
En el arte generativo, la aleatoriedad actúa como motor creativo y colaborador autónomo, cumpliendo al menos dos funciones esenciales: primero, funciona como generador de unicidad y sorpresa, asegurando que cada ejecución del sistema produzca resultados únicos e impredecibles, lo que transforma al artista de ejecutor absoluto en un diseñador de sistemas que establece reglas pero delega la materialización final al azar controlado; y segundo, sirve como simulador de procesos naturales y orgánicos, permitiendo imitar la complejidad y variación de fenómenos como el crecimiento de plantas, el fluir del agua o la formación de nubes a través de distribuciones no uniformes (como el ruido de Perlin o la distribución gaussiana), inyectando a la obra una sensación de vida y autenticidad que el determinismo puro no podría alcanzar.
**4)**
En mi obra final, el concepto de Vuelo de Lévy fue la elección central y adecuada porque buscaba crear la ilusión de un enjambre inteligente con propósito, no solo partículas errantes. Mientras que una caminata aleatoria uniforme habría producido un movimiento caótico y sin rumbo como mosquitos en pánico, el patrón powerlaw del Lévy, con sus numerosos pasos pequeños interrumpidos por saltos largos ocasionales, simuló de manera eficiente una búsqueda estratégica de recursos. Esto generó una narrativa visual emergente donde las partículas parecían explorar meticulosamente zonas locales antes de lanzarse audazmente a nuevos territorios, creando una danza entre concentración y expansión que evocaba directamente el comportamiento de aves o insectos en la naturaleza, cumpliendo así mi objetivo de combinar algoritmia con una sensación de vida e intencionalidad orgánica.
**5)**
En el contexto de la simulación, un paseo o caminata aleatoria (random walk) es un modelo matemático que describe una trayectoria formada por una serie de pasos sucesivos, donde cada paso se determina al azar a partir de una distribución de probabilidad. Es la abstracción fundamental para simular procesos de exploración, difusión o búsqueda en espacios digitales, desde el movimiento de una partícula en un fluido hasta la fluctuación de precios en el mercado. La esencia del paseo aleatorio es su falta de memoria: la dirección de cada paso es independiente de los anteriores, haciendo de la trayectoria resultante un registro puro de azar secuencial.

La característica particular que define una caminata de Lévy o "Lévy flight es su distribución de los tamaños de paso según una ley de potencia (power-law), donde muchos pasos son muy cortos y unos pocos son extremadamente largos. A diferencia de una caminata aleatoria común donde los pasos tienen un tamaño típico (como en la distribución normal), en el Lévy flight la probabilidad de dar un paso de longitud *L* decae como *L^(−μ)* (con 1 < μ < 3), lo que significa que no existe una escala de longitud característica: los saltos largos, aunque raros, son posibles y cruciales. Este patrón multiescala y fractal optimiza la cobertura del espacio al equilibrar la búsqueda local intensiva (pasos cortos) con la exploración global audaz (saltos largos), imitando la estrategia de búsqueda de alimentos de animales como albatros, abejas y primates, y generando visualmente trayectorias con racimos de actividad densa conectados por líneas de huida largas y dramáticas.
