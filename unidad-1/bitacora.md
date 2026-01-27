# Unidad 1

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
```
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

## Bitácora de proceso de aprendizaje


## Bitácora de aplicación 



## Bitácora de reflexión


