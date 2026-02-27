# Unidad 3

## Bitácora de proceso de aprendizaje
### Actividad 1.
Con toda mi sinceridad debo decir que el trabajo de Robert Hodgin es increíble, ahora mi opinión a lo que dice y lo que está pasando.
Antes que nada, debo aclarar que no soy un loco extremista no estoy en contra de que la IA no ayude a la sociedad, ni tampoco estoy en contra de que no se pueda usar como un buen pincel en el mundo artístico, tampoco niego el uso de ella para la vida cotidiana y los trabajos importante, para mi si se usa correctamente nos puede apoyar en nuestras falencias y superar nuestras promesas.
Con eso ultimo aclarado bajo mi perspectiva es que la maquina no fue el culpable de muchas cosas que han llegado, si no que fuimos nosotros y nuestra necesidad de sobre estimularnos y de dejar de ver al arte como un proceso y más como un producto masivo hemos dejado que la IA, nos apresara más (me incluyo ahí), pero si tomamos en cuenta el punto de vista de él cree que no tiene la IA por acabar con todos pero teme y tememos a futuro como seria la industria si desaparecen nuestra profesión, si al final todo valió la pena, si debemos aprender oficios para sobrevivir? pero creo que hay otro futuro que no estamos viendo, la Inteligencia artificial generativa avanza a pasos agigantados y cada vez más grande pero ese es exactamente su punto débil. hace poco escuche, "las grandes empresas le está metiendo un infierno de plata a OpenAI y a muchas generadoras de IA" pero es suficiente para el levitante que está en una instalación del tamaño de canchas de football juntas con sus parqueaderos? están metiendo mucha plata sí, pero sus ganancias ni siquiera se ven reflejadas, debemos contar sobre la sobre saturación de contenido en redes que es tanto que incluso ese Leviatán se está alimentado y los ingenieros de están luchando 24/7 para evitar ese problema, pero hay que entender un factor y es que lo que hace un artista normal en una semana lo hace 10 veces más una IA en una hora, pero es exactamente el problema de lo que se conoce como efecto de "la cola de la serpiente"  o mejor conocido como "Colapso del Modelo" (cuando una serpiente se come su propia cola), y buscar referencias de artistas en la actualidad es buscar una aguja en un pajar sobre todos en las redes occidentales al final, por más que le metan trillones, si la IA solo escupe "slop", el mercado se va a cansar de pagar por contenido que parece un sueño de fiebre en 4K. La burbuja puede estallar no porque falte plata, sino porque se quedaron sin realidad que copiar.
Pienso también que esto es más un "Oscurantismo Digital", en donde nos llenamos más de cosas hechas por una máquina que por verdadero contenido artístico digital, pero pienso también que cuando esto termine (todo lo que tiene un comienzo tiene un fin) va haber un renacimiento, una realineación y una perspectiva artista mucho más artístico, nos quedaremos con las herramientas que realmente son útiles y las demás simplemente desaparecen, un evento llamado la "Purga digital", solo se quedaran las que no dependen o no dependen del todo de la nube de OpenIA y que realmente tenga una utilidad tanto fuera como adentro del ámbito artístico y aprenderemos de nuestros errores, no pasa hoy ni mañana, tampoco de la noche a la mañana pero lentamente se ira cambiando las cosas.
Finalizando esto, claro que están las empresas chinas (pero son actualmente más limitadas, censuradas y con marca de agua obligatoria para el mercado) que por alguna razón son mas eficientes y baratas de mantener, pero la saturación del ojo humano a sido tal que será mas críticos. Cambiaran las cosas de algún modo y debemos prepararnos para lo incierto.

### Actividad 2.
El método procedural me parece uno de las maneras más bonitas de crear arte a través de Código, no soy bueno en el Código pero me interesa bastante la formación de biomas, ciudades y demás a través de eso, cuando implementamos el Motion 101 permite que el arte respire, se mueve y viva con una lógica interna creíble, pero eso no quita el toque artístico mientras al mismo tiempo eres tú quien mueve todo y decides que es y cómo se va creando tu mundo.
Los saberes de la fisica nos da mas que informacion para calcular un vuelo, un lanzamiento, un salto, una caida y mas, al entenderla 

### Actividad 3.
FRICCIÓN
```` js
let particulas = [];

function setup() {
  createCanvas(800, 600);
  for (let i = 0; i < 150; i++) {
    particulas.push(new Particula());
  }
}

function draw() {
  background(0);
  dibujarMapa();
  
  for (let p of particulas) {
    p.aplicarFriccion();
    p.actualizar();
    p.dibujar();
  }
  
  fill(255);
  text("🚗 FRICCIÓN - Click repeler | Espacio +", 10, 20);
}

function dibujarMapa() {
  // Grid de calles
  stroke(100, 30);
  strokeWeight(1);
  for (let y = 0; y < height; y += 50) line(0, y, width, y);
  for (let x = 0; x < width; x += 50) line(x, 0, x, height);
  
  // Zonas
  noStroke();
  fill(50, 30); rect(200, 150, 250, 200); // Central Park (alta fricción)
  fill(200, 30); rect(400, 250, 150, 100); // Times Square (baja fricción)
  fill(100, 30); rect(550, 200, 150, 200); // Zona financiera (media)
}

class Particula {
  constructor() {
    this.pos = createVector(random(width), random(height));
    this.vel = createVector(random(-2, 2), random(-2, 2));
    this.acc = createVector(0, 0);
  }
  
  aplicarFriccion() {
    let coef = 0.03;
    let x = this.pos.x, y = this.pos.y;
    
    if (x > 200 && x < 450 && y > 150 && y < 350) coef = 0.08;      // Central Park
    else if (x > 400 && x < 550 && y > 250 && y < 350) coef = 0.01; // Times Square
    else if (x > 550 && x < 700 && y > 200 && y < 400) coef = 0.04; // Zona financiera
    else if (x % 50 < 5 || y % 50 < 5) coef = 0.02;                  // Calles
    
    let friccion = this.vel.copy().mult(-coef);
    this.acc.add(friccion);
  }
  
  actualizar() {
    this.vel.add(this.acc);
    this.vel.limit(5);
    this.pos.add(this.vel);
    this.acc.mult(0);
    
    if (this.pos.x < 0 || this.pos.x > width) {
      this.vel.x *= -0.8;
      this.pos.x = constrain(this.pos.x, 0, width);
    }
    if (this.pos.y < 0 || this.pos.y > height) {
      this.vel.y *= -0.8;
      this.pos.y = constrain(this.pos.y, 0, height);
    }
  }
  
  dibujar() {
    let v = this.vel.mag();
    fill(map(v, 0, 5, 100, 255), 100, 100, 200);
    noStroke();
    ellipse(this.pos.x, this.pos.y, 5, 5);
  }
}

function mousePressed() {
  for (let p of particulas) {
    if (dist(mouseX, mouseY, p.pos.x, p.pos.y) < 50) {
      p.vel.add(p5.Vector.sub(p.pos, createVector(mouseX, mouseY)).setMag(2));
    }
  }
}

function keyPressed() {
  if (key === ' ') for (let i = 0; i < 5; i++) particulas.push(new Particula());
}
````

https://github.com/user-attachments/assets/fa1245dd-7b3f-4671-97b4-a0b5dce5aba9


RESISTENCIA
```` js
let particulas = [];

function setup() {
  createCanvas(800, 600);
  for (let i = 0; i < 150; i++) {
    particulas.push(new Particula());
  }
}

function draw() {
  background(0);
  dibujarMapa();
  
  for (let p of particulas) {
    p.aplicarResistencia();
    p.actualizar();
    p.dibujar();
  }
  
  fill(255);
  text("💨 RESISTENCIA - Click viento | Espacio +", 10, 20);
}

function dibujarMapa() {
  stroke(100, 30);
  strokeWeight(1);
  for (let y = 0; y < height; y += 50) line(0, y, width, y);
  for (let x = 0; x < width; x += 50) line(x, 0, x, height);
  
  noStroke();
  fill(50, 30); rect(200, 150, 250, 200);
  fill(200, 30); rect(400, 250, 150, 100);
  fill(100, 30); rect(550, 200, 150, 200);
}

class Particula {
  constructor() {
    this.pos = createVector(random(width), random(height));
    this.vel = createVector(random(-2, 2), random(-2, 2));
    this.acc = createVector(0, 0);
  }
  
  aplicarResistencia() {
    let x = this.pos.x, y = this.pos.y;
    let coef = 0.02;
    
    if (x > 200 && x < 450 && y > 150 && y < 350) coef = 0.04; // Central Park
    
    let resistencia = this.vel.copy().mult(-coef * this.vel.mag());
    this.acc.add(resistencia);
    
    // Viento en calles
    if (x % 50 < 5) this.acc.add(createVector(0.05 * sin(frameCount * 0.05), 0));
  }
  
  actualizar() {
    this.vel.add(this.acc);
    this.vel.limit(5);
    this.pos.add(this.vel);
    this.acc.mult(0);
    
    if (this.pos.x < 0 || this.pos.x > width) {
      this.vel.x *= -0.8;
      this.pos.x = constrain(this.pos.x, 0, width);
    }
    if (this.pos.y < 0 || this.pos.y > height) {
      this.vel.y *= -0.8;
      this.pos.y = constrain(this.pos.y, 0, height);
    }
  }
  
  dibujar() {
    let v = this.vel.mag();
    fill(100, map(v, 0, 5, 100, 255), 100, 200);
    noStroke();
    ellipse(this.pos.x, this.pos.y, 5, 5);
  }
}

function mousePressed() {
  for (let p of particulas) {
    if (dist(mouseX, mouseY, p.pos.x, p.pos.y) < 50) {
      p.vel.add(p5.Vector.sub(p.pos, createVector(mouseX, mouseY)).setMag(1));
    }
  }
}

function keyPressed() {
  if (key === ' ') for (let i = 0; i < 5; i++) particulas.push(new Particula());
}
````


https://github.com/user-attachments/assets/e810a083-4beb-4cb2-be00-bf54abd0b67c



ATRACCIÓN
```` js
let particulas = [];
let atractores = [];

function setup() {
  createCanvas(800, 600);
  
  atractores = [
    { x: 400, y: 300, fuerza: 500 },
    { x: 250, y: 200, fuerza: 400 },
    { x: 600, y: 300, fuerza: 450 },
    { x: 300, y: 400, fuerza: 350 }
  ];
  
  for (let i = 0; i < 150; i++) {
    particulas.push(new Particula());
  }
}

function draw() {
  background(0);
  dibujarMapa();
  
  // Dibujar atractores
  for (let a of atractores) {
    fill(255, 200, 0, 100);
    noStroke();
    ellipse(a.x, a.y, 20, 20);
  }
  
  for (let p of particulas) {
    p.aplicarAtraccion();
    p.actualizar();
    p.dibujar();
  }
  
  fill(255);
  text("⭐ ATRACCIÓN - Click repeler | Espacio +", 10, 20);
}

function dibujarMapa() {
  stroke(100, 20);
  strokeWeight(1);
  for (let y = 0; y < height; y += 50) line(0, y, width, y);
  for (let x = 0; x < width; x += 50) line(x, 0, x, height);
}

class Particula {
  constructor() {
    this.pos = createVector(random(width), random(height));
    this.vel = createVector(random(-1, 1), random(-1, 1));
    this.acc = createVector(0, 0);
  }
  
  aplicarAtraccion() {
    for (let a of atractores) {
      let dir = createVector(a.x, a.y).sub(this.pos);
      let d = constrain(dir.mag(), 20, 200);
      let mag = (0.5 * 500) / (d * d);
      this.acc.add(dir.setMag(mag));
    }
  }
  
  actualizar() {
    this.vel.add(this.acc);
    this.vel.limit(4);
    this.pos.add(this.vel);
    this.acc.mult(0);
    
    if (this.pos.x < 0 || this.pos.x > width) {
      this.vel.x *= -0.8;
      this.pos.x = constrain(this.pos.x, 0, width);
    }
    if (this.pos.y < 0 || this.pos.y > height) {
      this.vel.y *= -0.8;
      this.pos.y = constrain(this.pos.y, 0, height);
    }
  }
  
  dibujar() {
    fill(100, 100, map(this.vel.mag(), 0, 4, 100, 255), 200);
    noStroke();
    ellipse(this.pos.x, this.pos.y, 5, 5);
    
    // Líneas hacia atractores cercanos
    for (let a of atractores) {
      let d = dist(this.pos.x, this.pos.y, a.x, a.y);
      if (d < 80) {
        stroke(255, 100, 0, map(d, 0, 80, 100, 0));
        line(this.pos.x, this.pos.y, a.x, a.y);
      }
    }
  }
}

function mousePressed() {
  for (let p of particulas) {
    if (dist(mouseX, mouseY, p.pos.x, p.pos.y) < 50) {
      p.vel.add(p5.Vector.sub(p.pos, createVector(mouseX, mouseY)).setMag(2));
    }
  }
}

function keyPressed() {
  if (key === ' ') for (let i = 0; i < 5; i++) particulas.push(new Particula());
}
````

https://github.com/user-attachments/assets/46a54928-b787-4fa0-9280-81c533f2be26



## Bitácora de aplicación 

Durante la primavera y el verano, guarda sus cuentos en cada una de sus hojas. Pero cuando llega el otoño, llega el momento de compartir esas historias con el mundo.
Cada hoja que cae del árbol es una historia diferente. Hay hojas soñadoras que flotan suavemente mirando al cielo, como si recordaran los días cálidos que pasaron. Hay hojas aventureras que se alejan decididas, buscando nuevos horizontes más allá de la colina. Hay hojas hogareñas que dan vueltas cerca del árbol, sin querer alejarse demasiado de casa. Y hay hojas traviesas que bailan sin rumbo, cambiando de dirección caprichosamente como niños jugando.
El viento otoñal, que tú controlas con el mouse, es el soplido del destino. Puedes ayudar a las hojas a volar, alejarlas suavemente o crear remolinos de historias. Pero nunca decides por ellas: cada hoja tiene su propia personalidad y voluntad, y aunque puedes influir en su camino, la decisión final de hacia dónde ir siempre es de ella.
La magia de esta obra está en cómo la personalidad de cada hoja se traduce en fuerzas físicas que manipulan su aceleración. La hoja soñadora no solo flota, sino que una fuerza suave y constante la eleva ligeramente mientras cae, como si el viento la meciera con ternura. La hoja aventurera siente un impulso invisible que la aleja del árbol, una curiosidad que la empuja hacia lo desconocido. La hoja hogareña experimenta una fuerza nostálgica que la atrae de vuelta a casa, como un recuerdo que no la deja ir
```` js
// ============================================
// 🍂 EL ÁRBOL Y SUS HOJAS - VERSIÓN SIMPLIFICADA
// Árbol simple, solo se mueven las hojas
// ============================================

// ============================================
// 🎬 CONFIGURACIÓN INICIAL
// ============================================
let arbol;
let hojas = [];
let viento = 0;
let brisa = 0;
let soplo = 0;
let narracion = "";

// Pasto
let briznas = [];

// Interacción
let mouseAnteriorX = 0;
let mouseAnteriorY = 0;
let soplando = false;
let inicioSoploX = 0;
let inicioSoploY = 0;

function setup() {
  createCanvas(800, 600);
  
  // Árbol simple en el centro, bien plantado
  arbol = new Arbol(400, 400);
  
  // Crear briznas de pasto
  for (let i = 0; i < 150; i++) {
    briznas.push(new Brizna(i));
  }
  
  // Crear 25 hojas
  for (let i = 0; i < 25; i++) {
    hojas.push(new Hoja(i));
  }
  
  narracion = "El viejo árbol contaba historias...";
}

function draw() {
  // Fondo cálido
  background(245, 240, 230);
  
  // ==========================================
  // 🌱 PASTO CON BRISA
  // ==========================================
  brisa = sin(frameCount * 0.01) * 0.6;
  
  for (let brizna of briznas) {
    brizna.actualizar(brisa);
    brizna.dibujar();
  }
  
  // ==========================================
  // 🌳 DIBUJAR ÁRBOL (SIMPLE)
  // ==========================================
  arbol.dibujar();
  
  // ==========================================
  // 🌬️ VIENTO LENTO
  // ==========================================
  viento = sin(frameCount * 0.005) * 0.1;
  
  // ==========================================
  // 🖱️ INTERACCIÓN
  // ==========================================
  if (mouseIsPressed) {
    soplo = 0.25;
    dibujarSoplo(mouseX, mouseY);
    
    for (let hoja of hojas) {
      let distancia = dist(hoja.pos.x, hoja.pos.y, mouseX, mouseY);
      if (distancia < 120) {
        let direccion = p5.Vector.sub(hoja.pos, createVector(mouseX, mouseY));
        let fuerza = map(distancia, 0, 120, 0.4, 0);
        direccion.setMag(soplo * fuerza);
        hoja.acc.add(direccion);
      }
    }
  } else {
    soplo = 0;
  }
  
  // ==========================================
  // 🍃 ACTUALIZAR HOJAS
  // ==========================================
  for (let hoja of hojas) {
    hoja.aplicarFuerzas(viento, soplo);
    hoja.actualizar();
    hoja.dibujar();
  }
  
  // ==========================================
  // 📖 NARRATIVA
  // ==========================================
  contarHistoria();
  
  // Texto
  fill(0);
  noStroke();
  textFont('Georgia');
  textSize(12);
  text("🌬️ SOPLA: Mouse | Click + arrastre | Espacio: liberar", 20, height - 20);
  
  textSize(20);
  textStyle(BOLD);
  text("El Árbol y sus Hojas", 20, 40);
  textStyle(NORMAL);
  textSize(14);
  text(narracion, 20, 65);
}

// ============================================
// 🌳 CLASE ARBOL - VERSIÓN SIMPLE
// ============================================
class Arbol {
  constructor(x, yBase) {
    this.x = x;
    this.yBase = yBase;
    this.altura = 160;
  }
  
  dibujar() {
    push();
    stroke(0);
    strokeCap(ROUND);
    
    // Sombra ligera
    noStroke();
    fill(0, 10);
    ellipse(this.x + 8, this.yBase + 5, 70, 15);
    
    // TRONCO
    stroke(0);
    strokeWeight(8);
    line(this.x, this.yBase, this.x, this.yBase - this.altura);
    
    // RAMAS (4 principales)
    strokeWeight(5);
    
    // Izquierda inferior
    line(this.x, this.yBase - 40, this.x - 45, this.yBase - 60);
    // Derecha inferior
    line(this.x, this.yBase - 40, this.x + 45, this.yBase - 60);
    // Izquierda superior
    line(this.x, this.yBase - 100, this.x - 35, this.yBase - 130);
    // Derecha superior
    line(this.x, this.yBase - 100, this.x + 35, this.yBase - 130);
    
    // Ramitas pequeñas
    strokeWeight(3);
    line(this.x - 45, this.yBase - 60, this.x - 60, this.yBase - 80);
    line(this.x + 45, this.yBase - 60, this.x + 60, this.yBase - 80);
    
    pop();
  }
}

// ============================================
// 🌱 CLASE BRIZNA
// ============================================
class Brizna {
  constructor(id) {
    this.id = id;
    this.x = random(width);
    this.baseY = 450 + random(-10, 20);
    this.altura = random(25, 45);
    this.offset = random(TWO_PI);
  }
  
  actualizar(brisa) {
    this.movimiento = sin(frameCount * 0.02 + this.offset) * brisa * 2;
  }
  
  dibujar() {
    push();
    stroke(0, 40);
    strokeWeight(1);
    noFill();
    
    let puntaX = this.x + this.movimiento;
    let puntaY = this.baseY - this.altura;
    
    // Tallo curvo
    beginShape();
    vertex(this.x, this.baseY);
    quadraticVertex(this.x + this.movimiento * 0.5, this.baseY - this.altura * 0.5,
                    puntaX, puntaY);
    endShape();
    
    // Hojita en la punta
    strokeWeight(0.8);
    line(puntaX, puntaY, puntaX + 2, puntaY - 3);
    line(puntaX, puntaY, puntaX - 2, puntaY - 3);
    
    pop();
  }
}

// ============================================
// 🍃 CLASE HOJA
// ============================================
class Hoja {
  constructor(id) {
    this.id = id;
    
    // Motion 101
    this.pos = createVector(
      400 + random(-40, 40),
      300 + random(-30, 20)
    );
    this.vel = createVector(0, 0);
    this.acc = createVector(0, 0);
    
    // Estado
    this.enArbol = true;
    this.tiempoEspera = random(100, 300);
    
    // Personalidad
    let tipos = ['soñadora', 'aventurera', 'hogareña', 'traviesa'];
    this.personalidad = random(tipos);
    
    // Física suave
    this.peso = random(0.3, 0.6);
    this.flotabilidad = random(0.8, 1.2);
    
    // Rotación
    this.angulo = random(TWO_PI);
    this.velAngular = 0;
  }
  
  aplicarFuerzas(viento, soplo) {
    if (this.enArbol) {
      this.tiempoEspera--;
      if (this.tiempoEspera < 0) {
        this.enArbol = false;
      }
      return;
    }
    
    // Gravedad suave
    let gravedad = createVector(0, 0.02 * this.peso);
    this.acc.add(gravedad);
    
    // Viento
    let fuerzaViento = createVector(viento * 0.2, 0);
    this.acc.add(fuerzaViento);
    
    // Flotabilidad natural
    let flote = createVector(
      sin(frameCount * 0.01 + this.id) * 0.02 * this.flotabilidad,
      cos(frameCount * 0.008 + this.id) * 0.01
    );
    this.acc.add(flote);
    
    // Personalidad (sutil)
    if (this.personalidad === 'soñadora') {
      this.acc.add(createVector(sin(frameCount * 0.01 + this.id) * 0.02, -0.003));
    } else if (this.personalidad === 'aventurera') {
      let direccion = p5.Vector.sub(this.pos, createVector(400, 280));
      direccion.setMag(0.008);
      this.acc.add(direccion);
    } else if (this.personalidad === 'hogareña') {
      if (dist(this.pos.x, this.pos.y, 400, 280) > 150) {
        let retorno = p5.Vector.sub(createVector(400, 280), this.pos);
        retorno.setMag(0.006);
        this.acc.add(retorno);
      }
    } else if (this.personalidad === 'traviesa') {
      this.acc.add(createVector(random(-0.015, 0.015), random(-0.015, 0.015)));
    }
    
    // Soplo del usuario
    if (soplo > 0) {
      let distancia = dist(this.pos.x, this.pos.y, mouseX, mouseY);
      if (distancia < 120) {
        let direccion = p5.Vector.sub(this.pos, createVector(mouseX, mouseY));
        let fuerza = map(distancia, 0, 120, 0.3, 0);
        direccion.setMag(soplo * fuerza * 0.8);
        this.acc.add(direccion);
      }
    }
  }
  
  actualizar() {
    if (!this.enArbol) {
      // Motion 101
      this.vel.add(this.acc);
      this.vel.limit(1.2);
      this.pos.add(this.vel);
      this.acc.mult(0);
      
      // Rotación
      this.velAngular = this.vel.x * 0.03;
      this.angulo += this.velAngular;
      
      // Bordes suaves
      if (this.pos.x < 0) {
        this.pos.x = 0;
        this.vel.x *= -0.2;
      }
      if (this.pos.x > width) {
        this.pos.x = width;
        this.vel.x *= -0.2;
      }
      
      // Suelo
      if (this.pos.y > 450) {
        this.pos.y = 450;
        this.vel.y *= -0.1;
        this.vel.x *= 0.98;
      }
    }
  }
  
  dibujar() {
    push();
    translate(this.pos.x, this.pos.y);
    rotate(this.angulo);
    
    stroke(0);
    
    if (this.enArbol) {
      // Hojas en el árbol (puntos)
      strokeWeight(1);
      for (let i = 0; i < 3; i++) {
        point(random(-3, 3), random(-4, 4));
      }
    } else {
      // Hoja volando
      strokeWeight(1);
      noFill();
      
      // Forma simple
      beginShape();
      vertex(0, -4);
      quadraticVertex(2.5, 0, 0, 4);
      quadraticVertex(-2.5, 0, 0, -4);
      endShape();
      
      // Veta
      line(0, -2, 0, 2);
      
      // Detalle mínimo de personalidad
      strokeWeight(0.5);
      if (this.personalidad === 'soñadora') {
        arc(0, -7, 4, 2, 0, PI);
      } else if (this.personalidad === 'aventurera') {
        line(2, -6, 4, -8);
      }
    }
    
    pop();
  }
}

// ============================================
// 🎨 DIBUJAR SOPLO
// ============================================
function dibujarSoplo(x, y) {
  push();
  noFill();
  stroke(0, 20);
  strokeWeight(0.8);
  
  for (let i = 0; i < 3; i++) {
    let tam = 25 + i * 20 + sin(frameCount * 0.08 + i) * 5;
    ellipse(x, y, tam, tam * 0.5);
  }
  pop();
}

// ============================================
// 📖 NARRATIVA
// ============================================
function contarHistoria() {
  let hojasVolando = hojas.filter(h => !h.enArbol).length;
  
  if (hojasVolando === 0) {
    narracion = "Las hojas esperan paciente su momento...";
  } else if (hojasVolando < 8) {
    narracion = "Algunas hojas comienzan a bailar con la brisa.";
  } else if (hojasVolando < 15) {
    narracion = "El viento susurra historias a las hojas.";
  } else {
    narracion = "Cada hoja encuentra su propio camino...";
  }
}

// ============================================
// 🖱️ INTERACCIONES
// ============================================
function mousePressed() {
  let nuevaHoja = new Hoja(hojas.length);
  nuevaHoja.enArbol = false;
  nuevaHoja.pos = createVector(mouseX, mouseY);
  nuevaHoja.vel = createVector(random(-0.3, 0.3), random(-0.3, 0.3));
  hojas.push(nuevaHoja);
  
  soplando = true;
  inicioSoploX = mouseX;
  inicioSoploY = mouseY;
}

function mouseDragged() {
  if (soplando) {
    push();
    stroke(0, 30);
    strokeWeight(1);
    line(inicioSoploX, inicioSoploY, mouseX, mouseY);
    let fuerza = dist(mouseX, mouseY, inicioSoploX, inicioSoploY);
    noFill();
    ellipse(mouseX, mouseY, fuerza/3, fuerza/4);
    pop();
  }
}

function mouseReleased() {
  if (soplando) {
    let direccion = createVector(mouseX - inicioSoploX, mouseY - inicioSoploY);
    let fuerzaSoplo = direccion.mag();
    direccion.normalize();
    
    for (let hoja of hojas) {
      let distancia = dist(hoja.pos.x, hoja.pos.y, inicioSoploX, inicioSoploY);
      if (distancia < 150) {
        let factor = map(distancia, 0, 150, 1, 0.2);
        let soploFinal = p5.Vector.mult(direccion, fuerzaSoplo * factor * 0.03);
        hoja.acc.add(soploFinal);
      }
    }
  }
  soplando = false;
}

function keyPressed() {
  if (key === ' ') {
    for (let hoja of hojas) {
      hoja.enArbol = false;
    }
  }
  
  if (key === 'R' || key === 'r') {
    hojas = [];
    for (let i = 0; i < 25; i++) {
      hojas.push(new Hoja(i));
    }
  }
}

````
https://editor.p5js.org/JorgeLuisSuarique/sketches/19HRTqZz_

https://github.com/user-attachments/assets/1009b8e7-2cd3-4819-ae09-1c1880124819


## Bitácora de reflexión

### Actividad 5.
Explica detalladamente en tu bitácora ¿Qué es el marco de movimiento motion 101 y cómo se relacionan: fuerza, aceleración, velocidad y posición?
El marco de movimi9ento de Motion 101 es un sistema en cadena de sumatoria de fuerzas basado en la segunda ley de Newton, en donde comberjen para que el moviemitnto se sienta mas vivo cuando programas arte generativo por mantener las sumatorias de fuerzas y mientras nostros podemos decidir en que se usa y en que no se usa en el mundo que creamos.
Como se correlacionan como bien es la segunda ley de Newtoon "la sumatoria de todas las fuerzas es igual a la masa por sus aceleraciones", queriedo decir la ley de la fisica coesiste en si misma de la siguiente manera la velocidad es el cambio de la posicion, la aceleracion es el cambio de la velocidad, la fuerza es la masa multiplicada por la aceleracion y la poscioin es el lugar en el espacio, como bien vemos la fuerza, aceleración, velocidad y posición convergen entre si y en su mayoria dependen de cada uno para realisar la accion, el motion 101 describe todo esto en codigo procedural para el arte generativo.

<img width="882" height="439" alt="image" src="https://github.com/user-attachments/assets/6f8e5681-5ba2-4ef3-bbb8-4963739c4c00" />

https://editor.p5js.org/JorgeLuisSuarique/sketches/jMzUOK1Mg

```` js
// ============================================
// 🖤 MÓVIL DE CALDER - EQUILIBRIO PERFECTO
// Todo se mueve, nada cae
// ============================================

// ============================================
// 🎬 CONFIGURACIÓN INICIAL
// ============================================
let movil;
let viento = 0;
let soplo = 0;
let narracion = "";

// Interacción
let mouseAnteriorX = 0;
let mouseAnteriorY = 0;
let soplando = false;
let inicioSoploX = 0;
let inicioSoploY = 0;

function setup() {
  createCanvas(900, 700);
  
  // Crear el móvil con equilibrio perfecto
  movil = new MovilCalder();
  
  narracion = "El punto de equilibrio... todo baila, nada cae";
}

function draw() {
  background(255);
  
  // ==========================================
  // 🌬️ VIENTO NATUAL (afecta a todo)
  // ==========================================
  viento = sin(frameCount * 0.004) * 0.2 + cos(frameCount * 0.003) * 0.15;
  
  // ==========================================
  // 🖱️ INTERACCIÓN
  // ==========================================
  if (mouseIsPressed) {
    soplo = 0.5;
    dibujarSoplo(mouseX, mouseY);
  } else {
    soplo = 0;
  }
  
  // SOPLO RÁPIDO
  let velocidadMouse = dist(mouseX, mouseY, mouseAnteriorX, mouseAnteriorY);
  if (velocidadMouse > 8) {
    let soploFuerte = map(velocidadMouse, 8, 35, 0.3, 0.9);
    movil.aplicarSoplo(mouseX, mouseY, soploFuerte);
  }
  
  mouseAnteriorX = mouseX;
  mouseAnteriorY = mouseY;
  
  // ==========================================
  // 🔄 ACTUALIZAR MÓVIL
  // ==========================================
  movil.actualizar(viento, soplo, mouseX, mouseY);
  movil.dibujar();
  
  // ==========================================
  // 📖 NARRATIVA
  // ==========================================
  contarHistoria();
  
  // Texto
  fill(0);
  noStroke();
  textFont('Georgia');
  textSize(12);
  text("🌬️ SOPLA: Mouse | Click + arrastre | R: reiniciar", 20, height - 20);
  textSize(18);
  textStyle(BOLD);
  text("🖤 Móvil de Calder - El Equilibrio", 20, 40);
  textStyle(NORMAL);
  textSize(14);
  text(narracion, 20, 65);
}

// ============================================
// 🖤 CLASE MÓVIL CALDER
// ============================================
class MovilCalder {
  constructor() {
    // ===== PUNTO DE SUSPENSIÓN SUPERIOR =====
    this.puntoSuperior = createVector(width/2, 80);
    
    // ===== LÍNEA VERTICAL CENTRAL (EJE DE EQUILIBRIO) =====
    this.verticalCentral = new LineaEquilibrio(
      this.puntoSuperior,                    // inicio
      createVector(width/2, 200),            // fin (largo: 120px)
      2.0,                                    // peso (más pesada, más estable)
      true                                    // es el eje central
    );
    
    // ===== GRAN LÍNEA HORIZONTAL (3 VECES MÁS LARGA) =====
    // Se conecta al final de la vertical central
    this.horizontalGrande = new LineaEquilibrio(
      createVector(width/2, 200),                     // inicio (mismo punto)
      createVector(width/2 + 240, 200),                // fin (120*2 = 240px)
      1.5,                                              // peso medio
      false,                                            // no es el eje
      true                                              // es horizontal
    );
    
    // También hacia la izquierda (simetría)
    this.horizontalIzquierda = new LineaEquilibrio(
      createVector(width/2, 200),
      createVector(width/2 - 240, 200),
      1.5,
      false,
      true
    );
    
    // ===== 4 LÍNEAS VERTICALES FLEXIBLES (CUELGAN DE LA HORIZONTAL) =====
    this.verticalesFlexibles = [];
    let puntosX = [
      width/2 - 180,
      width/2 - 60,
      width/2 + 60,
      width/2 + 180
    ];
    
    for (let i = 0; i < 4; i++) {
      this.verticalesFlexibles.push(
        new LineaFlexible(
          createVector(puntosX[i], 200),  // inicio (en la horizontal)
          100,                             // longitud
          i,                               // id
          1.2 - i * 0.1                    // peso (varía ligeramente)
        )
      );
    }
    
    // ===== 16 HOJAS TRIANGULARES =====
    this.hojas = [];
    for (let v = 0; v < this.verticalesFlexibles.length; v++) {
      let vertical = this.verticalesFlexibles[v];
      
      for (let h = 0; h < 4; h++) {
        this.hojas.push(
          new HojaTriangular(
            vertical,                       // vertical padre
            h,                              // posición en la vertical
            v * 4 + h,                      // id único
            0.8 + h * 0.1                    // peso (más livianas abajo)
          )
        );
      }
    }
  }
  
  actualizar(viento, soplo, mouseX, mouseY) {
    // Actualizar eje vertical central
    this.verticalCentral.actualizar(viento, soplo, mouseX, mouseY);
    
    // Actualizar horizontales (su posición depende de la vertical central)
    this.horizontalGrande.inicio = this.verticalCentral.fin.copy();
    this.horizontalGrande.actualizar(viento, soplo, mouseX, mouseY);
    
    this.horizontalIzquierda.inicio = this.verticalCentral.fin.copy();
    this.horizontalIzquierda.actualizar(viento, soplo, mouseX, mouseY);
    
    // Actualizar verticales flexibles (su inicio sigue a las horizontales)
    for (let i = 0; i < this.verticalesFlexibles.length; i++) {
      let vf = this.verticalesFlexibles[i];
      
      // El inicio de cada vertical flexible sigue el punto correspondiente en la horizontal
      if (i < 2) {
        // Las dos de la izquierda siguen la horizontal izquierda
        let progreso = (i === 0) ? 0.7 : 0.3;
        vf.inicio.x = this.horizontalIzquierda.inicio.x + 
                     (this.horizontalIzquierda.fin.x - this.horizontalIzquierda.inicio.x) * progreso;
        vf.inicio.y = this.horizontalIzquierda.fin.y;
      } else {
        // Las dos de la derecha siguen la horizontal derecha
        let progreso = (i === 2) ? 0.3 : 0.7;
        vf.inicio.x = this.horizontalGrande.inicio.x + 
                     (this.horizontalGrande.fin.x - this.horizontalGrande.inicio.x) * progreso;
        vf.inicio.y = this.horizontalGrande.fin.y;
      }
      
      vf.actualizar(viento, soplo, mouseX, mouseY);
    }
    
    // Actualizar hojas (su punto de anclaje sigue a las verticales flexibles)
    for (let hoja of this.hojas) {
      hoja.actualizar(viento, soplo, mouseX, mouseY);
    }
  }
  
  aplicarSoplo(mouseX, mouseY, intensidad) {
    this.verticalCentral.aplicarSoplo(mouseX, mouseY, intensidad);
    this.horizontalGrande.aplicarSoplo(mouseX, mouseY, intensidad);
    this.horizontalIzquierda.aplicarSoplo(mouseX, mouseY, intensidad);
    
    for (let vf of this.verticalesFlexibles) {
      vf.aplicarSoplo(mouseX, mouseY, intensidad);
    }
    
    for (let hoja of this.hojas) {
      hoja.aplicarSoplo(mouseX, mouseY, intensidad);
    }
  }
  
  dibujar() {
    // Dibujar en orden (de atrás hacia adelante)
    this.verticalCentral.dibujar(2.5);
    this.horizontalGrande.dibujar(2.2);
    this.horizontalIzquierda.dibujar(2.2);
    
    for (let vf of this.verticalesFlexibles) {
      vf.dibujar();
    }
    
    for (let hoja of this.hojas) {
      hoja.dibujar();
    }
  }
}

// ============================================
// 📏 LÍNEA DE EQUILIBRIO (se mueve con el viento)
// ============================================
class LineaEquilibrio {
  constructor(inicio, fin, peso, esEje = false, esHorizontal = false) {
    this.inicio = inicio.copy();
    this.finInicial = fin.copy();
    this.fin = fin.copy();
    this.peso = peso;                // Mayor peso = más estable
    this.esEje = esEje;              // El eje central es más firme
    this.esHorizontal = esHorizontal;
    
    // Motion 101
    this.vel = createVector(0, 0);
    this.acc = createVector(0, 0);
    
    // Restitución (vuelve al equilibrio)
    this.resistencia = 0.92;
  }
  
  actualizar(viento, soplo, mouseX, mouseY) {
    // Calcular posición de equilibrio (relativa al inicio)
    let equilibrio = createVector(
      this.inicio.x + (this.finInicial.x - this.inicio.x),
      this.inicio.y + (this.finInicial.y - this.inicio.y)
    );
    
    // Fuerza restauradora (más fuerte en el eje)
    let restauracion = p5.Vector.sub(equilibrio, this.fin);
    let fuerzaRestauracion = this.esEje ? 0.08 : 0.04;
    restauracion.mult(fuerzaRestauracion);
    this.acc.add(restauracion);
    
    // Viento (afecta menos al eje central)
    let factorViento = this.esEje ? 0.3 : 0.8;
    if (this.esHorizontal) factorViento *= 1.5; // La horizontal se mueve más
    
    let fuerzaViento = createVector(
      viento * factorViento / this.peso,
      this.esHorizontal ? viento * 0.1 : 0
    );
    this.acc.add(fuerzaViento);
    
    // Soplo del mouse
    if (soplo > 0) {
      let distancia = dist(this.fin.x, this.fin.y, mouseX, mouseY);
      if (distancia < 200) {
        let direccion = p5.Vector.sub(this.fin, createVector(mouseX, mouseY));
        let fuerza = map(distancia, 0, 200, 0.5, 0);
        direccion.setMag(soplo * fuerza / this.peso);
        this.acc.add(direccion);
      }
    }
    
    // MOTION 101
    this.vel.add(this.acc);
    this.vel.mult(this.resistencia);
    this.vel.limit(3 / this.peso);
    this.fin.add(this.vel);
    this.acc.mult(0);
  }
  
  aplicarSoplo(mouseX, mouseY, intensidad) {
    let distancia = dist(this.fin.x, this.fin.y, mouseX, mouseY);
    if (distancia < 250) {
      let direccion = p5.Vector.sub(this.fin, createVector(mouseX, mouseY));
      let factor = map(distancia, 0, 250, 1, 0.2);
      direccion.setMag(intensidad * factor * 0.5 / this.peso);
      this.acc.add(direccion);
    }
  }
  
  dibujar(grosor = 2) {
    push();
    stroke(0);
    strokeWeight(grosor);
    line(this.inicio.x, this.inicio.y, this.fin.x, this.fin.y);
    pop();
  }
}

// ============================================
// 🌿 LÍNEA FLEXIBLE (con columna vertebral)
// ============================================
class LineaFlexible {
  constructor(inicio, longitud, id, peso) {
    this.id = id;
    this.inicio = inicio.copy();
    this.longitud = longitud;
    this.peso = peso;
    
    // Motion 101
    this.fin = createVector(inicio.x, inicio.y + longitud);
    this.vel = createVector(0, 0);
    this.acc = createVector(0, 0);
    
    this.resistencia = 0.94;
  }
  
  actualizar(viento, soplo, mouseX, mouseY) {
    // Equilibrio (vertical desde el inicio)
    let equilibrio = createVector(this.inicio.x, this.inicio.y + this.longitud);
    
    // Fuerza restauradora
    let restauracion = p5.Vector.sub(equilibrio, this.fin);
    restauracion.mult(0.06);
    this.acc.add(restauracion);
    
    // Viento
    let fuerzaViento = createVector(viento * 1.2 / this.peso, viento * 0.1);
    this.acc.add(fuerzaViento);
    
    // Soplo
    if (soplo > 0) {
      let distancia = dist(this.fin.x, this.fin.y, mouseX, mouseY);
      if (distancia < 150) {
        let direccion = p5.Vector.sub(this.fin, createVector(mouseX, mouseY));
        let fuerza = map(distancia, 0, 150, 0.4, 0);
        direccion.setMag(soplo * fuerza / this.peso);
        this.acc.add(direccion);
      }
    }
    
    // MOTION 101
    this.vel.add(this.acc);
    this.vel.mult(this.resistencia);
    this.vel.limit(2);
    this.fin.add(this.vel);
    this.acc.mult(0);
  }
  
  aplicarSoplo(mouseX, mouseY, intensidad) {
    let distancia = dist(this.fin.x, this.fin.y, mouseX, mouseY);
    if (distancia < 200) {
      let direccion = p5.Vector.sub(this.fin, createVector(mouseX, mouseY));
      let factor = map(distancia, 0, 200, 1, 0.2);
      direccion.setMag(intensidad * factor * 0.4 / this.peso);
      this.acc.add(direccion);
    }
  }
  
  dibujar() {
    push();
    stroke(0);
    strokeWeight(1.5);
    
    // Línea principal
    line(this.inicio.x, this.inicio.y, this.fin.x, this.fin.y);
    
    // "Columna vertebral" (pequeñas vértebras)
    let pasos = 6;
    for (let i = 1; i < pasos; i++) {
      let t = i / pasos;
      let x = lerp(this.inicio.x, this.fin.x, t);
      let y = lerp(this.inicio.y, this.fin.y, t);
      
      strokeWeight(0.8);
      line(x - 3, y, x + 3, y);
    }
    
    pop();
  }
}

// ============================================
// 🍂 HOJA TRIANGULAR
// ============================================
class HojaTriangular {
  constructor(verticalPadre, posicionVertical, id, peso) {
    this.verticalPadre = verticalPadre;
    this.posicionVertical = posicionVertical; // 0,1,2,3 (de arriba a abajo)
    this.id = id;
    this.peso = peso;
    
    // El punto de anclaje se actualizará en cada frame
    this.puntoAnclaje = createVector(0, 0);
    
    // Motion 101 para la hoja
    this.pos = createVector(0, 0);
    this.vel = createVector(0, 0);
    this.acc = createVector(0, 0);
    
    this.tamano = 12 + posicionVertical * 2; // Más grandes abajo
    this.angulo = 0;
    this.velAngular = 0;
    
    this.longitudHilo = 12;
    this.resistencia = 0.95;
    
    // Personalidad
    let tipos = ['elegante', 'inquieta', 'serena', 'libre'];
    this.personalidad = tipos[id % 4];
  }
  
  actualizar(viento, soplo, mouseX, mouseY) {
    // Actualizar punto de anclaje (sigue a la vertical padre)
    let t = (this.posicionVertical + 1) / 4; // 0.25, 0.5, 0.75, 1.0
    this.puntoAnclaje.x = lerp(this.verticalPadre.inicio.x, this.verticalPadre.fin.x, t);
    this.puntoAnclaje.y = lerp(this.verticalPadre.inicio.y, this.verticalPadre.fin.y, t);
    
    // Si es la primera vez, inicializar posición
    if (this.pos.x === 0 && this.pos.y === 0) {
      this.pos = createVector(
        this.puntoAnclaje.x,
        this.puntoAnclaje.y + this.longitudHilo
      );
    }
    
    // Equilibrio (justo debajo del anclaje)
    let equilibrio = createVector(
      this.puntoAnclaje.x,
      this.puntoAnclaje.y + this.longitudHilo
    );
    
    // Fuerza restauradora
    let restauracion = p5.Vector.sub(equilibrio, this.pos);
    restauracion.mult(0.05);
    this.acc.add(restauracion);
    
    // Viento (más efecto en hojas inferiores)
    let factorViento = 0.4 + this.posicionVertical * 0.2;
    let fuerzaViento = createVector(viento * factorViento / this.peso, viento * 0.05);
    this.acc.add(fuerzaViento);
    
    // Personalidad
    if (this.personalidad === 'inquieta') {
      this.acc.add(createVector(random(-0.02, 0.02), random(-0.01, 0.01)));
    } else if (this.personalidad === 'libre') {
      this.acc.add(createVector(sin(frameCount * 0.01 + this.id) * 0.02, 0));
    }
    
    // Soplo
    if (soplo > 0) {
      let distancia = dist(this.pos.x, this.pos.y, mouseX, mouseY);
      if (distancia < 130) {
        let direccion = p5.Vector.sub(this.pos, createVector(mouseX, mouseY));
        let fuerza = map(distancia, 0, 130, 0.5, 0);
        direccion.setMag(soplo * fuerza / this.peso);
        this.acc.add(direccion);
      }
    }
    
    // MOTION 101
    this.vel.add(this.acc);
    this.vel.mult(this.resistencia);
    this.vel.limit(1.8);
    this.pos.add(this.vel);
    this.acc.mult(0);
    
    // Rotación
    this.velAngular = this.vel.x * 0.02 + sin(frameCount * 0.02) * 0.01;
    this.angulo += this.velAngular;
  }
  
  aplicarSoplo(mouseX, mouseY, intensidad) {
    let distancia = dist(this.pos.x, this.pos.y, mouseX, mouseY);
    if (distancia < 150) {
      let direccion = p5.Vector.sub(this.pos, createVector(mouseX, mouseY));
      let factor = map(distancia, 0, 150, 1, 0.2);
      direccion.setMag(intensidad * factor * 0.3 / this.peso);
      this.acc.add(direccion);
    }
  }
  
  dibujar() {
    push();
    translate(this.pos.x, this.pos.y);
    rotate(this.angulo);
    
    // Hilo
    stroke(0, 40);
    strokeWeight(0.5);
    line(0, -this.longitudHilo, 0, 0);
    
    // Triángulo
    stroke(0);
    strokeWeight(1.2);
    noFill();
    
    let t = this.tamano;
    beginShape();
    vertex(0, -t);
    vertex(-t/1.5, t/2);
    vertex(t/1.5, t/2);
    endShape(CLOSE);
    
    // Veta
    strokeWeight(0.6);
    line(0, -t/2, 0, t/3);
    
    pop();
  }
}

// ============================================
// 🌬️ DIBUJAR SOPLO
// ============================================
function dibujarSoplo(x, y) {
  push();
  noFill();
  stroke(0, 20);
  strokeWeight(0.8);
  
  for (let i = 0; i < 3; i++) {
    let tam = 40 + i * 30 + sin(frameCount * 0.1 + i) * 8;
    ellipse(x, y, tam, tam * 0.6);
  }
  pop();
}

// ============================================
// 📖 NARRATIVA
// ============================================
function contarHistoria() {
  let tiempo = frameCount * 0.005;
  let frases = [
    "En el centro, el equilibrio...",
    "La gran horizontal se mece con el viento...",
    "Cuatro líneas flexibles, dieciséis hojas...",
    "Todo baila, nada cae...",
    "Como un Calder que respira...",
    "Tu soplo las hace girar...",
    "Pero siempre vuelven...",
    "El equilibrio perfecto..."
  ];
  
  let indice = floor(tiempo) % frases.length;
  narracion = frases[indice];
}

// ============================================
// 🖱️ INTERACCIONES
// ============================================
function mousePressed() {
  soplando = true;
  inicioSoploX = mouseX;
  inicioSoploY = mouseY;
}

function mouseDragged() {
  if (soplando) {
    push();
    stroke(0, 30);
    strokeWeight(1);
    line(inicioSoploX, inicioSoploY, mouseX, mouseY);
    
    let fuerza = dist(mouseX, mouseY, inicioSoploX, inicioSoploY);
    noFill();
    ellipse(mouseX, mouseY, fuerza/2, fuerza/3);
    pop();
  }
}

function mouseReleased() {
  if (soplando) {
    let direccion = createVector(mouseX - inicioSoploX, mouseY - inicioSoploY);
    let fuerzaSoplo = direccion.mag();
    direccion.normalize();
    
    movil.aplicarSoplo(mouseX, mouseY, fuerzaSoplo * 0.15);
  }
  soplando = false;
}

function keyPressed() {
  if (key === 'R' || key === 'r') {
    movil = new MovilCalder();
  }
}
````




