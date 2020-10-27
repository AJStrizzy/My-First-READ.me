## Steps to install on local computer
1. Go to [repo](https://github.com/AJStrizzy/tic-tac-toe) on Github profile
2. `fork` and `clone` repo
3. Clone to local machine
```text
git clone https://github.com/AJStrizzy/tic-tac-toe.git
```
4. Go to `tic-tac-toe` directory
5. Open `index.html` in browser
```text
open index.html
```
```html
<div class="container">
    <h1 class="title">Tic <span>Tac</span> Toe</h1>
    <div class="status-action">
      <div class="status">x is next</div>
      <div class="reset">Reset</div>
    </div>
   <div class="game-grid">
     <div class="game-cell"></div>
     <div class="game-cell"></div>
     <div class="game-cell"></div>
     <div class="game-cell"></div>
     <div class="game-cell"></div>
     <div class="game-cell"></div>
     <div class="game-cell"></div>
     <div class="game-cell"></div>
     <div class="game-cell"></div>
   </div>
</div>
```
Sets up a container to hold all the elemts of the tic-tac toe board. Including the title of the game, the status of whose move is next, the reset button as well as a 3x3 grid.

```javascript
// Game Constants
const xSymbol = '×';
const oSymbol = '○';
```
Defines the symbols that will be used on the game board.

```javascript
const checkGameStatus = () => {
    const topLeft = cellDivs[0].classList[1];
    const topMiddle = cellDivs[1].classList[1];
    const topRight = cellDivs[2].classList[1];
    const middleLeft = cellDivs[3].classList[1];
    const middleMiddle = cellDivs[4].classList[1];
    const middleRight = cellDivs[5].classList[1];
    const bottomLeft = cellDivs[6].classList[1];
    const bottomMiddle = cellDivs[7].classList[1];
    const bottomRight = cellDivs[8].classList[1];
```
Defines each of the 9 cells in the 3x3 grid so they can be interacted with.

```javascript
 if (topLeft && topLeft === topMiddle && topLeft === topRight) {
        handleWin(topLeft);
    } else if (middleLeft && middleLeft === middleMiddle && middleLeft === middleRight) {
        handleWin(middleLeft);
    } else if (bottomLeft && bottomLeft === bottomMiddle && bottomLeft === bottomRight) {
        handleWin(bottomLeft);
    } else if (topLeft && topLeft === middleLeft && topLeft === bottomLeft) {
        handleWin(topLeft);
    } else if (topMiddle && topMiddle === middleMiddle && topMiddle === bottomMiddle ) {
        handleWin(topMiddle);
    } else if (topRight && topRight === middleRight && topRight === bottomRight) {
        handleWin(topRight);
    } else if (topLeft && topLeft === middleMiddle && topLeft === bottomRight) {
        handleWin(topLeft);
    } else if (topRight && topRight === middleMiddle && topRight === bottomLeft) {
        handleWin(topRight);
    } else if(topLeft && topMiddle && topRight && middleLeft && middleMiddle && middleRight && bottomLeft && bottomMiddle && bottomRight) {
        gameIsLive = false
        statusDiv.innerHTML = 'Tie Game';
    } else {
        xIsNext = !xIsNext;
        if(xIsNext) {
            statusDiv.innerHTML = `${xSymbol} is next`
        } else {
            statusDiv.innerHTML= `<span>${oSymbol} is next</span>`;
        }
    }
};
```
Defines all possible win conditions and what to do in case of a win. Also defines how game should continue until a win happens, or game ends in a tie.
  