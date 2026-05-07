# Unidad 7

## Bitácora de proceso de aprendizaje

### Actividad 1.
<img width="486" height="484" alt="image" src="https://github.com/user-attachments/assets/16df2d8e-7205-48ab-82ea-082ef302c68f" />
Me gusta este tipo de trabajo porque la palabra en ilgles de la luna tiene doble "O" y hace que una de ls "o" orbita sobre otra como si ese fuera la luna.

<img width="486" height="482" alt="image" src="https://github.com/user-attachments/assets/15013df4-9e71-4c2d-b34a-105a0453360c" />
Esta imagen es curiosa porque crear un efecto palidromo pero mas enfocado en el diseño que representa esta palabra y usa el contexto para daornar mas.

<img width="483" height="483" alt="image" src="https://github.com/user-attachments/assets/89606599-0ae7-4234-b3de-4ed3d29f954b" />
Me gusta como el relog decora la palabra reljog en ingles para expresar mejor el contexto de sicha palabra.

**Palabras que propongo.**

**Iceberg:** podemos hacer que la B de dicha palabra sea la punta del iceberg y las demas letras su borde o el Iceberg teniendo una forma que se ahemege a la B para el trabajo.



### Actividad 2.
https://brm.io/matter-js/demo/#mixed

- **Engine:** Es el motor que hace funcionar la física. Calcula la gravedad, las colisiones y el movimiento de todo. Sin él, los objetos se quedarían quietos para siempre.
- **World:** Es el escenario donde ocurre todo. Aquí pones los objetos, el suelo, las paredes y las uniones. Si no añades algo al mundo, no aparecerá en la simulación.

- **Bodies:** Son los objetos físicos (rectángulos, círculos o formas personalizadas). Cada cuerpo tiene peso, rebote y fricción. Para una palabra, cada letra sería un cuerpo diferente.

- **Constraint:** Son las uniones que conectan cuerpos entre sí. Sirven para crear cadenas, resortes o articulaciones. Con esto puedes unir letras para formar una palabra flexible.

- **MouseConstraint:** Permite agarrar y arrastrar objetos con el ratón. Al hacer clic y mover, aplicas fuerza al cuerpo. Así puedes interactuar con la palabra y mover sus letras.


### Actividad 3.

#### Experimento 1_ 
- **Explica qué dato estás leyendo del audio.**: El volumen (amplitud) captado por el micrófono, de 0 (silencio) a 1 (fuerte).

- **Explica qué comportamiento visual o físico activa ese dato.**: Un círculo cambia de tamaño: silencio = pequeño, sonido fuerte = grande.

- **Describe qué tipo de respuesta sonora te serviría más para tu palabra y por qué.**: Continua, porque sigue el flujo natural del sonido en tiempo real.

#### Experimento 2_ 

- **Explica qué dato estás leyendo del audio.**: La energía del sonido, que es la amplitud acumulada o sostenida en el tiempo (no el volumen instantáneo, sino cuánta energía total ha habido).

- **Explica qué comportamiento visual o físico activa ese dato.**: Un círculo que se llena como un termómetro: con cada sonido que entra, la energía se acumula y el círculo se va llenando de color. Si hay silencio por unos segundos, la energía se reinicia.

- **Describe qué tipo de respuesta sonora te serviría más para tu palabra y por qué.**: Puntual con memoria (acumulativa), porque representa la "cantidad total de sonido" que ha entrado, no solo el volumen del momento.

### Actividad 4.
- Muestra una prueba inicial.
  <img width="602" height="291" alt="image" src="https://github.com/user-attachments/assets/bbcbeec2-f704-4d54-bfeb-6b4dbb0ffc89" />
  
- Explica qué parte de la palabra construiste.
  Construí la palabra completa "acordeón" como texto dentro de un canvas.
  
- Explica qué propiedad física manipulaste.
  Manipulé la escala horizontal (estiramiento) de la palabra. Cuando el audio suena, la palabra se hace más ancha; cuando el audio termina, vuelve a su tamaño normal.
  
- Explica qué aspecto del audio afecta qué comportamiento.
  El volumen (amplitud) del audio de acordeón afecta el ancho de la palabra. A mayor volumen, más se estira la palabra, simulando la apertura del fuelle de un acordeón real.
  
- Evalúa qué funcionó y qué no para el significado que quieres construir.
  La relación entre el volumen del audio y el estiramiento de la palabra funciona bien como metáfora del fuelle del acordeón: más sonido = más abierto. Sin embargo, el estiramiento es uniforme y no tiene pliegues ni separación entre letras, lo que pierde la textura visual de un acordeón real. Para la pieza final, debo dividir la palabra en segmentos que se separen entre sí.

## Bitácora de aplicación 

### Actividad 5
#### Palabra elegida.
**Precionar** 
#### Justificación conceptual.
Un mazo que preiona sobre las demas letras.
#### Análisis de su significado visual y comportamental.
Precionar sobre las demas letras como si aplastara objetos de goma.
#### Moodboard o referencias.
<img width="478" height="483" alt="image" src="https://github.com/user-attachments/assets/412df177-242d-4347-a8a4-99e33dcdffa4" />
<img width="690" height="460" alt="image" src="https://github.com/user-attachments/assets/b5d65945-1150-4d0d-b4b1-fb5af79acc50" />
#### Bocetos.

#### Mapa de decisiones.
#### Mapa de interpretación.
#### Explicación de la relación entre audio y comportamiento.
El audio es un sonido de precionar algo de goma pero siendo un sonido sueva, no el chillido que conocemos.
#### Evidencia del uso de IA.
La IA ayudó en la implementación técnica: física del mazo, estiramiento del mango, control del sonido con duración de 1 segundo, detección de clic y animación completa. La idea narrativa, la elección de la palabra "presionar", la mecánica de aplastamiento y la decisión de usar un chirrido de goma son de mi autoría.
#### Código fuente.
````js
let animacionActiva = false;
let aplastamiento = 0;
let sonidoIniciado = false;

let letras = ["r", "e", "s", "i", "o", "n", "a", "r"];
let posicionesOriginales = [];

let mangoX = 120;
let cabezaX = 160;
let cabezaY;

let chirrido;
let audioActivado = false;

function preload() {
  soundFormats('mp3', 'wav', 'ogg');
  chirrido = loadSound('presionar.mp3');
}

function setup() {
  createCanvas(windowWidth, windowHeight);
  cabezaY = height / 2;
  
  let inicioX = cabezaX + 40;
  for (let i = 0; i < letras.length; i++) {
    posicionesOriginales.push(inicioX + i * 50);
  }
  
  textAlign(CENTER, CENTER);
  textSize(20);
  fill(0);
  text("🖱️ Haz CLIC en la cabeza de la P (mazo) para aplastar", width/2, 70);
}

function draw() {
  background(240);
  
  // Dibujar letras "resionar"
  for (let i = 0; i < letras.length; i++) {
    push();
    translate(posicionesOriginales[i], height/2);
    let escalaX = 1 + aplastamiento * 1.4;
    let escalaY = map(aplastamiento, 0, 1, 1, 0.25);
    scale(escalaX, escalaY);
    let gris = map(aplastamiento, 0, 1, 80, 180);
    fill(gris, 100, 150);
    textSize(42);
    text(letras[i], 0, 0);
    pop();
  }
  
  // Dibujar mazo (P)
  push();
  let estiramientoMango = map(aplastamiento, 0, 1, 1, 2.8);
  let desplazamientoCabeza = map(aplastamiento, 0, 1, 0, 180);
  let tamanoCabeza = map(aplastamiento, 0, 1, 50, 110);
  
  fill(160, 80, 40);
  noStroke();
  rect(mangoX, cabezaY - 15, 25 * estiramientoMango, 30);
  
  fill(200, 60, 60);
  ellipse(cabezaX + desplazamientoCabeza, cabezaY, tamanoCabeza, tamanoCabeza);
  
  fill(255);
  textSize(tamanoCabeza * 0.6);
  textAlign(CENTER, CENTER);
  text("P", cabezaX + desplazamientoCabeza, cabezaY);
  pop();
  
  // === SONIDO (1 segundo, se activa en impacto) ===
  if (animacionActiva && audioActivado && chirrido) {
    if (aplastamiento >= 0.55 && !sonidoIniciado) {
      chirrido.play();                // solo una vez
      chirrido.setVolume(0.8);
      sonidoIniciado = true;
      
      setTimeout(() => {
        if (chirrido.isPlaying()) {
          chirrido.stop();
        }
      }, 1000);                      // 1 segundo de duración
    }
  }
  
  if (!animacionActiva && sonidoIniciado && chirrido && chirrido.isPlaying()) {
    chirrido.stop();
    sonidoIniciado = false;
  }
  
  // Barra de aplastamiento
  fill(150);
  rect(width/2 - 100, height - 80, 200, 12);
  fill(200, 50, 50);
  rect(width/2 - 100, height - 80, 200 * aplastamiento, 12);
  
  fill(100);
  textSize(14);
  if (audioActivado) {
    fill(0, 150, 0);
    text("🔊 Sonido listo", width/2, height - 40);
  } else {
    fill(150);
    text("🔇 Haz clic en la cabeza de la P", width/2, height - 40);
  }
  
  stroke(200, 0, 0, 80);
  noFill();
  ellipse(cabezaX + map(aplastamiento, 0, 1, 0, 180), cabezaY, 80, 80);
  noStroke();
}

function mousePressed() {
  let cabezaActualX = cabezaX + map(aplastamiento, 0, 1, 0, 180);
  let distancia = dist(mouseX, mouseY, cabezaActualX, cabezaY);
  
  if (distancia < 70 && !animacionActiva) {
    animacionActiva = true;
    sonidoIniciado = false;
    
    if (!audioActivado && chirrido) {
      userStartAudio();
      audioActivado = true;
    }
    
    aplastamiento = 0;
    
    let subir = setInterval(() => {
      if (aplastamiento < 1) {
        aplastamiento += 0.08;
      } else {
        clearInterval(subir);
        setTimeout(() => {
          let bajar = setInterval(() => {
            if (aplastamiento > 0) {
              aplastamiento -= 0.06;
            } else {
              clearInterval(bajar);
              animacionActiva = false;
            }
          }, 25);
        }, 350);
      }
    }, 25);
  }
}

function windowResized() {
  resizeCanvas(windowWidth, windowHeight);
  cabezaY = height / 2;
  let inicioX = cabezaX + 40;
  for (let i = 0; i < letras.length; i++) {
    posicionesOriginales[i] = inicioX + i * 50;
  }
}
````
#### Enlace al sketch.
https://editor.p5js.org/JorgeLuisSuarique/sketches/SUojdNuNf
#### Capturas o registros de la pieza.
<img width="848" height="705" alt="image" src="https://github.com/user-attachments/assets/80adabcf-9d96-46cb-ac2a-7006821fcfd3" />


## Bitácora de reflexión
