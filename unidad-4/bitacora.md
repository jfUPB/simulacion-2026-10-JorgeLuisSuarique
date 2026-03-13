# Unidad 4

## Bitácora de proceso de aprendizaje

### Actividad 1.
Documenta en tu bitácora de aprendizaje los aspectos que más te llamaron la atención de la obra de Memo.
En el trabajo de Memo lo que mas me llamo la tención es la colisión de partículas con base a la musica que esta sonando, También cada colisión con los Assests da un mayor control y profundidad a la obra.

### Actividad 2.
**¿Qué está pasando en esta simulación? ¿Cuál es la interacción?**
En esta simulación estamos viendo una representación visual de un sistema de dos masas conectadas que giran alrededor de un centro, como si fueran dos planetas unidos por una barra o un par de ojos que miran alrededor. El código dibuja una línea horizontal con dos círculos en sus extremos, y esta figura completa rota continuamente en el centro del lienzo.

**Nota que en cada frame se está trasladando el origen del sistema de coordenadas al centro de la pantalla. ¿Por qué crees que se hace esto?**
Se traslada el origen al centro de la pantalla por una razón muy práctica y elegante: simplifica enormemente las matemáticas necesarias para la rotación. En lugar de tener que calcular las nuevas posiciones de cada punto de la figura usando trigonometría compleja, simplemente movemos todo el sistema de coordenadas y luego rotamos ese sistema completo.

**Cuál es la relación entre el sistema de coordenadas y la función rotate().**
La relación entre el sistema de coordenadas y la función rotate() es que rotate() no gira los objetos individuales, sino que gira el propio sistema de coordenadas sobre el cual se dibujan los objetos. Cuando llamamos a rotate(angle), estamos aplicando una transformación que afecta a todo lo que se dibuje después, hasta que usemos push() y pop() para aislar la transformación.

**¿Por qué crees que se hace esto? y ¿Por qué aunque en cada frame se hace lo mismo, los elementos gráficos rotan?**
Fíjate que la línea va de (-50,0) a (50,0) y los círculos están en (50,0) y (-50,0), y aunque pareciera que se dibujan en la esquina, en realidad antes el código ya movió todo el sistema de coordenadas al centro de la pantalla con translate() y lo rotó con rotate(), es como si agarraras una hoja transparente, la pusieras en el centro de la mesa y la giraras, para luego dibujar siempre el mismo palito con dos bolitas en el mismo lugar de la hoja, pero como la hoja está girada, lo que ves en pantalla aparece rotado, y como en cada frame el ángulo aumenta un poquito, la hoja está un poco más girada que antes, dando la ilusión de que los elementos giran aunque en su propio mundo local siempre están quietos.

**Identifica el marco motion 101. ¿Qué es lo que se está haciendo en este marco?**
En este marco Motion 101 lo que se está haciendo es aplicar el principio fundamental de la física newtoniana a un objeto gráfico: la aceleración (que aquí apunta hacia el mouse) modifica la velocidad, y la velocidad modifica la posición. Pero lo hermoso de este código es que además incorpora una capa de conciencia espacial: el objeto no solo se mueve, sino que sabe hacia dónde se está moviendo gracias al ángulo de su velocidad, y usa esa información para orientarse visualmente.

**Qué hace la función heading()?**
La función heading() convierte el vector velocidad en un ángulo, específicamente el ángulo que ese vector forma con el eje horizontal. Si el vector apunta totalmente a la derecha, heading() devuelve 0 radianes; si apunta hacia arriba, devuelve -PI/2 (o 270 grados); si apunta hacia la izquierda, devuelve PI (180 grados).

**¿Qué hace la función push() y pop()? Realiza algunos experimentos para entender su funcionamiento.**
Es como tener un asistente que anota dónde dejaste las herramientas, tú las mueves todas para trabajar cómodo, y cuando terminas el asistente las devuelve a su lugar exacto. Si pruebas comentando push() y pop(), verás que las transformaciones se acumulan y el rectángulo termina apareciendo en lugares y ángulos rarísimos.

**¿Qué hace rectMode(CENTER)? Realiza algunos experimentos para entender su funcionamiento.**
Normalmente los rectángulos se dibujan desde su esquina superior izquierda, entonces rect(0,0,30,10) pondría la esquina en el origen. Con rectMode(CENTER), el rectángulo se dibuja desde su centro, entonces rect(0,0,30,10) centra el rectángulo exactamente en el origen.

**¿Cuál es la relación entre el ángulo de rotación y el vector de velocidad? Trata de dibujar en un papel el vector de velocidad y cómo se relaciona con el ángulo de rotación y la operación de traslación y rotación.**
El ángulo de rotación ES la dirección del vector velocidad convertida a grados o radianes. Imagina que dibujas en un papel un punto que representa al objeto, y desde ese punto dibujas una flecha que es su velocidad, apuntando hacia algún lado. El ángulo de esa flecha respecto a la horizontal es exactamente lo que devuelve heading(). Luego, cuando haces translate() llevas el origen del sistema de coordenadas justo a donde está el objeto, y cuando haces rotate(angle) giras todo el papel para que la dirección en la que apuntaba la flecha ahora mire hacia la derecha del sistema local. Finalmente dibujas el rectángulo horizontal en ese sistema rotado, y al volver al sistema original, el rectángulo aparece orientado exactamente en la dirección de la flecha.

### Actividad 3.
Para transformar el código original en un vehículo controlable, sustituimos la lógica de seguimiento automático del mouse por una entrada de teclado directa (keyIsDown), permitiendo que el usuario genere vectores de aceleración hacia la izquierda o derecha manualmente. Se reestructuró el método update para reiniciar la aceleración en cada frame e incluir una fuerza de fricción constante, lo que evita que el vehículo se deslice infinitamente y otorga una sensación de control físico real. Finalmente, reemplazamos el rectángulo por un triángulo dinámico que, mediante la función velocity.heading(), orienta su vértice principal hacia la dirección exacta del movimiento, convirtiendo un simple seguidor en un objeto con orientación y voluntad propia.
**sketch.js**
```` js
let mover;

function setup() {
  createCanvas(800, 600);
  mover = new Mover();
}

function draw() {
  background(240); // Un fondo claro para ver bien los trazos
  
  mover.update();
  mover.checkEdges();
  mover.show();
}
````
**mover.js**
```` js
// The Nature of Code - Modificado para control por teclado
// Daniel Shiffman

class Mover {
  constructor() {
    this.position = createVector(width / 2, height / 2);
    this.velocity = createVector(0, 0);
    // Cambiamos 0 por un vector para poder sumar fuerzas correctamente
    this.acceleration = createVector(0, 0); 
    this.topspeed = 5;
    this.r = 16;
  }

  update() {
    // 1. Resetear la aceleración en cada frame para que no sea infinita
    this.acceleration.mult(0);

    // 2. Control por teclado: Flechas Izquierda y Derecha
    let fuerza = 0.2; 
    if (keyIsDown(LEFT_ARROW)) {
      this.acceleration.add(createVector(-fuerza, 0));
    }
    if (keyIsDown(RIGHT_ARROW)) {
      this.acceleration.add(createVector(fuerza, 0));
    }

    // 3. Motor Motion 101
    this.velocity.add(this.acceleration);
    this.velocity.limit(this.topspeed);
    this.position.add(this.velocity);

    // 4. Rozamiento suave (Fricción)
    // Esto hace que el vehículo se detenga poco a poco al soltar las teclas
    this.velocity.mult(0.97);
  }

  show() {
    // Obtenemos el ángulo hacia donde apunta la velocidad
    let angle = this.velocity.heading();

    stroke(0);
    strokeWeight(2);
    fill(127);
    
    push();
    translate(this.position.x, this.position.y);
    rotate(angle);

    // Dibujamos un triángulo en lugar de un rectángulo
    // El frente del triángulo apunta hacia la derecha (0 radianes)
    triangle(this.r * 2, 0, -this.r, -this.r * 0.8, -this.r, this.r * 0.8);

    pop();
  }

  checkEdges() {
    if (this.position.x > width) {
      this.position.x = 0;
    } else if (this.position.x < 0) {
      this.position.x = width;
    }

    if (this.position.y > height) {
      this.position.y = 0;
    } else if (this.position.y < 0) {
      this.position.y = height;
    }
  }
}
````
<img width="815" height="457" alt="image" src="https://github.com/user-attachments/assets/960da233-e89a-418c-8b8e-51863477ce88" />

### Actividad 4.
**Identifica motion 101. ¿Qué modificación hay que hacer al motion 101 cuando se quiere agregar fuerzas acumulativas? Trata de recordar por qué es necesario hacer esta modificación.**

El Motion 101 básico suele ser solo "posición + velocidad". Sin embargo, al introducir fuerzas, la modificación clave es que la aceleración debe reiniciarse al final de cada frame usando this.acceleration.mult(0). Es necesario hacer esto porque las fuerzas son acumulativas dentro de un mismo frame (puedes tener gravedad, viento y empuje actuando a la vez), pero no deben persistir al siguiente. Si no la limpiaras, el objeto guardaría el "impulso" anterior y saldría disparado infinitamente, violando las leyes de la física donde la fuerza causa una aceleración instantánea, no permanente.

**Identifica dónde está el Attractor en la simulación. Cambia el color de este.**

El Attractor es el círculo central (la "fuente de gravedad") que atrae a los demás objetos. Para cambiar su color, debes ir al archivo attractor.js, dentro del método display(). Busca la parte donde dice fill(175, 200); (que es el gris por defecto) y cámbialo por algo más llamativo, como un naranja o un azul profundo, por ejemplo: fill(255, 150, 0);. Esto hará que la "fuerza central" destaque visualmente de los Movers.

**Observa que el Attractor tiene dos atributos this.dragging y this.rollover. Estos atributos no se modifican en el código, pero permitirían mover el attractor con el mouse y cambiar su color cuando el mouse está sobre él. ¿Cómo podrías modificar el código para que esto funcione? considera las funciones que ofrece p5.js para interactuar con el mouse.**

Para que dragging y rollover funcionen, necesitas añadir lógica que compare la posición del mouse con la del Attractor. Podrías añadir métodos en la clase Attractor que usen dist(mouseX, mouseY, this.position.x, this.position.y).
Para el Rollover: En cada frame verificas si esa distancia es menor al radio; si lo es, this.rollover = true.
Para el Dragging: Usas las funciones globales de p5.js mousePressed() (para activar el arrastre si haces clic sobre él) y mouseReleased() (para soltarlo), permitiendo que el Attractor siga la posición del mouse mientras mantienes presionado el botón.


### Actividad 5.
**¿Cuál es la relación entre r y theta con las posiciones x y y?**
La relación entre el radio ($r$) y el ángulo ($\theta$) con las posiciones cartesianas ($x$, $y$) se define mediante las funciones trigonométricas seno y coseno, donde $x$ representa la proyección horizontal del radio ($x = r \cdot \cos\theta$) y $y$ representa su proyección vertical ($y = r \cdot \sin\theta$). En esta estructura, mientras que en el sistema cartesiano nos movemos en una cuadrícula de filas y columnas, en el sistema polar nos desplazamos una distancia determinada ($r$) desde un punto de origen central siguiendo una dirección angular específica ($\theta$); de este modo, al variar el ángulo de forma constante en el código, los valores de $x$ y $y$ oscilan rítmicamente, permitiendo que un objeto dibuje trayectorias circulares, espirales o pulsaciones orgánicas en la pantalla.

**Primera Modificacion de Draw**
Al ejecutar este código, la simulación experimentará un error crítico o un comportamiento visual estático debido a que las variables $x$ e $y$ en la función line() ya no están definidas ni calculadas, lo que impide dibujar el trazo correctamente. Además, la función p5.Vector.fromAngle(theta) genera por defecto un vector unitario con una magnitud de tan solo 1 píxel, provocando que el círculo se dibuje prácticamente sobre el origen $(0,0)$ y su rotación sea imperceptible para el ojo humano. Esto ocurre porque se ha eliminado la lógica de conversión manual de coordenadas polares a cartesianas y no se ha proporcionado el radio ($r$) como segundo argumento al vector, resultando en un sistema que carece de la distancia necesaria para visualizar el movimiento circular en la pantalla.

**Sogunda Modificacion de Draw**
En esta segunda modificación, la simulación recupera su movimiento circular fluido porque la función p5.Vector.fromAngle(theta, r) ahora recibe el radio ($r$) como segundo argumento, realizando internamente toda la conversión trigonométrica de coordenadas polares a cartesianas que antes hacíamos de forma manual. Al asignar el resultado al vector v, las propiedades v.x y v.y contienen automáticamente los valores proyectados de la distancia y el ángulo, permitiendo que tanto la línea como el círculo se dibujen con la magnitud correcta desde el centro de la pantalla. Esto ocurre porque el método fromAngle simplifica el código al encapsular las fórmulas de seno y coseno en un solo objeto vectorial, permitiendo que el objeto orbite a la distancia definida por el radio mientras el ángulo theta aumenta en cada frame.

### Actividad 6.
La reflexión principal es que esta modificación transforma una fórmula matemática abstracta en una experiencia física tangible. Al permitirnos manipular variables como la amplitud o el periodo en tiempo real, dejamos de ver la sinusoide como una simple línea curva en un libro y empezamos a entenderla como un lenguaje de movimiento.

### Actividad 7.
El aprendizaje fundamental de este proceso es que el código deja de ser una máquina de repetición para convertirse en un sistema vivo cuando sustituimos los valores estáticos por relaciones dinámicas. Al cambiar el random() por el Ruido de Perlin, aprendemos que la naturaleza no es caótica, sino coherente; la aleatoriedad orgánica permite que cada agente mantenga su individualidad sin romper la armonía del conjunto.

### Actividad 8.
El proceso consistió en transformar una estructura matemática estática en un sistema dinámico mediante la gestión del tiempo y la fase. Trasladamos la lógica del setup() al draw() para permitir el redibujo constante y creamos una variable de fase global (startAngle) que evoluciona en cada fotograma; al utilizar esta variable como punto de partida para el ángulo de cada círculo, logramos que la función seno se desplace horizontalmente, convirtiendo una oscilación individual de "arriba y abajo" en una percepción visual de movimiento colectivo que fluye como una ola.

### Actividad 9.
El proceso consistió en transformar un sistema simple en una cadena física mediante la duplicación de elementos y el anclaje dinámico. Añadimos un segundo cuerpo y un segundo resorte, pero con la diferencia crucial de que el punto de apoyo del nuevo resorte no es un punto fijo en el techo, sino la posición en tiempo real del primer cuerpo.

### Actividad 10.
El proceso consistió en crear una jerarquía de movimiento donde el segundo péndulo utiliza la masa del primero como su propio punto de anclaje dinámico. Al actualizar el vector pivot del segundo péndulo con la posición actual del bob del primero en cada fotograma, logramos que la base del segundo sistema se desplace continuamente; esto permite que el segundo eslabón herede la velocidad y el ángulo del anterior, transformando dos oscilaciones simples en un sistema acoplado con trayectorias mucho más complejas y realistas.

## Bitácora de aplicación 

### Actividad 11.


## Bitácora de reflexión



