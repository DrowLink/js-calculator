js-calculadora

<p align="center">
  <img src="https://github.com/DrowLink/js-calculator/assets/111207841/6fa8069d-a42e-49a7-b5d7-dc55ac799082" alt="Sublime's custom image"/>
</p>

<br/>

Este es uno de mis primeros proyectos. La estructura-sintaxis de la calculadora no es mi idea original, hecha con fines educativos.

### EXPLICACIÓN DE LA ESTRUCTURA HTML: ###

    <input type="text" class="screen" id="screen" placeholder="0">
    <button class="symbol" onclick="wipe()">AC</button>
    <button class="symbol" onclick="wipe()">C</button>
    <button class="symbol" onclick="show('/')">/</button>
    <button class="symbol" onclick="show('*')">*</button>

    <button class="number" onclick="show('7')">7</button>
    <button class="number" onclick="show('8')">8</button>
    <button class="number" onclick="show('9')">9</button>
    <button class="symbol" onclick="show('-')">-</button>

    <button class="number" onclick="show('4')">4</button>
    <button class="number" onclick="show('5')">5</button>
    <button class="number" onclick="show('6')">6</button>
    <button class="symbol" onclick="show('+')">+</button>

    <button class="number" onclick="show('1')">1</button>
    <button class="number" onclick="show('2')">2</button>
    <button class="number" onclick="show('3')">3</button>
    <button class="symbol" onclick="show('.')">.</button>

    <button class="number" onclick="show('(')">(</button>
    <button class="number" onclick="show('0')">0</button>
    <button class="number" onclick="show(')')">)</button>
    <button class="symbol" onclick="calc('=')">=</button>

La estructura HTML hecha de esta manera para encajar con un diseño típico de calculadora. Clases utilizadas para aplicar CSS. Hablando de etiquetas de botón, el atributo onclick está vinculado con funciones .js que desarrollan el proceso para mostrar un resultado correcto.

### EXPLICACIÓN DE LA ESTRUCTURA CSS: ###

      * {
    box-sizing: border-box;
    margin: 0;
    padding: 0;
    }
    
Primero aplicando a todos los elementos disponibles border-box, margin y padding 0. Para aplicar el estilo predeterminado para editarlos a continuación de manera fácil y bien hecha (algunas buenas prácticas)

    *::before,
    *::after {
        box-sizing: inherit;
    }
    
::before toma el primer elemento secundario y ::después del último elemento secundario, este tamaño de caja: heredar se aplica al primero y al último de todos los elementos.

    html,
    body {
        font-size: 16px;
        font-family: sans-serif;
        height: 100%;
    }
    
De esta forma selecciona todos los textos para ponerlo de la misma forma (manteniendo el minimalismo y la uniformidad)

     body {
        background: #10131c;
        display: flex;
        align-items: center;
        justify-content: center;
        -webkit-font-smoothing: antialiased;
        -webkit-tap-highlight-color: transparent;
    }
    
Al colocar la calculadora en el centro de la página, el tutorial que seguí también usó webkits, pero están obsoletos de acuerdo con los documentos de MDN.

    input {
        border: none;
        outline: none;
    }

    input:focus {
        outline: none;
    }

    button {
        border: none;
        outline: none;
        background: none;
        cursor: pointer;
    }
  
Estas son las típicas líneas css para embellecer el diseño, //cursor: puntero cambia el estilo del mouse a puntero (demasiado obvio jajaja)

    .calculator {
      background: #212532;
      display: grid;
      grid-template-columns: repeat(4, 1fr);
      gap: .75rem;
      width: 325px;
      border: 1px solid #333;
      padding: .75rem;
      border-radius: 1rem;
      position: fixed;
      top: 50%;
      left: 50%;
      transform: translate(-50%, -50%);
  }

Líneas CSS más importantes, visualización como cuadrícula, dimensiones definidas, bordes, posiciones CSS (transformar, traducir)

        .screen {
    grid-column: 1 / 5;
    border-radius: .75rem;
    font-size: 2rem;
    height: 6rem;
    color: #fff;
    background: #333849;
    text-align: end;
    padding: .5rem;
     }
 
Más alineaciones de cuadrícula y algunos efectos de texto.

      ::placeholder {
    color: #fff;
      }
  
Colorear el único atributo de marcador de posición.

    .symbol,
    .number {
        display: flex;
        align-items: center;
        justify-content: center;
        text-align: center;
        aspect-ratio: 1;
        font-size: 1.25rem;
        color: #fff;
        border-radius: 50%;
        transition: .15s ease;
    }

Ligera transición en Botones y más estilos agregados

    .symbol {
        background: #c15216;

    }

    .symbol:hover {
        background: #fa742c;
    }

    .number {
        background: #333849;
    }

    .number:hover {
        background: #333849ac;
    }

Definición de los colores de los botones y sus desplazamientos (cuando el mouse se coloca en el botón cambia su color)

### EXPLICACIÓN DE LÍNEAS JS: ###

    let display = document.getElementById('screen')

Selector DOM para mostrar la lógica en la entrada

    const wipe = () => {
        display.value = '';
    }

Borra las funciones cuando presiona AC o C, establece el valor de visualización en indefinido (sale como vacío para los usuarios)

    const show = (n) => {
        display.value += n;
    }

Forma abstracta y también inteligente de poner números en la pantalla id = "screen" (entrada)

    const calc = () => {
        display.value = eval(display.value);
    }

Da el resultado gracias al objeto global "eval" que resuelve un problema aritmético de cadenas.

por ejemplo, si tiene una cadena:

            let resolve = "(2 * 5) - 6" (typeof string)
            
hacer eval() resolverá la cadena como si fueran números

            eval(resolve) ==> console output : 4
