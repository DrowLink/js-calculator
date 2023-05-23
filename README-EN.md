# js-calculator
js-calculator

This is one of my first projects. The calculator structure-syntax is not my original idea, done with educational purposes.

### EXPLAINING HTML STRUCTURE: ###

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
    
   
The HTML Structure done on this way to fit with a typical calculator layout.
classes used to apply CSS.
Talking about Button tags, the onclick attribute is linked with .js functions that develops the process in order to show a correct result.


### EXPLAINING CSS STRUCTURE: ###

      * {
    box-sizing: border-box;
    margin: 0;
    padding: 0;
    }

First applying to all elements availables border-box, margin and padding 0. To apply default style in order to edit them below easily and well-done (some good practices)

    *::before,
    *::after {
        box-sizing: inherit;
    }
    
  ::before takes the first child element and ::after the last child, this box-sizing: inherit is being applied to first and last all elements.

    html,
    body {
        font-size: 16px;
        font-family: sans-serif;
        height: 100%;
    }
    
 This way selects all texts to put it in the same way (maintaining minimalism and uniformity)
 
     body {
        background: #10131c;
        display: flex;
        align-items: center;
        justify-content: center;
        -webkit-font-smoothing: antialiased;
        -webkit-tap-highlight-color: transparent;
    }

Putting calculator on center of the page, also webkits were used by the tutorial i followed, but they are deprecated according to MDN docs.

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

  This are typical css lines to beautify design, //cursor: pointer changes the mouse style to pointer (too obvious lol)
  
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
    
    
Most important CSS lines, display as grid, defined dimentions, borders, CSS positions (transform, translate)

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
     
     
More grid aligns and some text effects.

      ::placeholder {
    color: #fff;
      }
      
Coloring the only placeholder attribute.

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
    
Slight transition in Buttons and more styles added

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
    
    
Defining buttons colors and their hovers (when mouse placed on button changes its color)


### EXPLAINING JS LINES: ###

    let display = document.getElementById('screen')

DOM selector to show the logical on the input

    const wipe = () => {
        display.value = '';
    }
    
 Clear functions when you press AC or C, sets the display value to undefined (or empty for users)
    
    const show = (n) => {
        display.value += n;
    }
    
 Abstract and also smart way to put numbers on the display id="screen" (input)
 
    const calc = () => {
        display.value = eval(display.value);
    }
    
 Gives the result thanks the global object eval that resolve an string arithmetic problems
 
 for example if you have one string: 
 
                let resolve = "(2 * 5) - 6" (typeof string)
                
doing the eval() will resolve the string as if they were numbers

                eval(resolve) ==> console output : 4
                
                

