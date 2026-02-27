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
