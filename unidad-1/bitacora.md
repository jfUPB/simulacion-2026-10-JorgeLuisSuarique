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
```
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

```
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


## Bitácora de proceso de aprendizaje


## Bitácora de aplicación 



## Bitácora de reflexión

