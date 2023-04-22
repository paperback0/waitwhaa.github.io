# waitwhaa.github.io

<!DOCTYPE html>
<html>
  <head>
    <title>Invention Game</title>
    <style>
      #game-board {
        display: flex;
        flex-direction: column;
        align-items: center;
      }
      
      button {
        font-size: 1.5em;
        margin: 10px;
        padding: 10px;
      }
    </style>
  </head>
  <body>
    <h1><center>What happened first?</center></h1>
    <div id="game-board">
      <h2>Score: <span id="score">0</span></h2>
      <div>
        <button id="item1"></button>
        <button id="item2"></button>
      </div>
      <button id="play-again">Play Again</button>
    </div>

    <script>
      // generate a list of items and their corresponding years
      const itemList = [
        { item: "Telephone", year: 1876 },
        { item: "Television", year: 1927 },
        { item: "Computer", year: 1941 },
        { item: "Lightbulb", year: 1879}
        // add more items and years as needed
      ];

      // randomly select two items from the list
      let item1, item2;
      function selectItems() {
        item1 = itemList[Math.floor(Math.random() * itemList.length)];
        item2 = itemList[Math.floor(Math.random() * itemList.length)];
        
        // make sure item1 and item2 are not the same item
        while (item1.item === item2.item) {
          item2 = itemList[Math.floor(Math.random() * itemList.length)];
        }
      }
      selectItems();

      // display the items on the game board
      const item1Btn = document.getElementById("item1");
      const item2Btn = document.getElementById("item2");
      item1Btn.textContent = item1.item;
      item2Btn.textContent = item2.item;

      // add event listener to the buttons
      let score = 0;
      item1Btn.addEventListener("click", () => {
        if (item1.year < item2.year) {
          // user was correct
          score++;
          document.getElementById("score").textContent = score;
          alert("Correct!");
          
        } else {
          // user was incorrect
          score = 0;
          document.getElementById("score").textContent = score;
          alert("Incorrect!");
        }
        selectItems();
        item1Btn.textContent = item1.item;
        item2Btn.textContent = item2.item;
      });

      item2Btn.addEventListener("click", () => {
        if (item2.year < item1.year) {
          // user was correct
          score++;
          document.getElementById("score").textContent = score;
          alert("Correct!");
        } else {
          // user was incorrect
          score = 0;
          document.getElementById("score").textContent = score;
          alert("Incorrect!");
        }
        selectItems();
        item1Btn.textContent = item1.item;
        item2Btn.textContent = item2.item;
      });

      // add event listener to the play again button
      const playAgainBtn = document.getElementById("play-again");
      playAgainBtn.addEventListener("click", () => {
        score = 0;
        document.getElementById("score").textContent = score;
        selectItems();
        item1Btn.textContent = item1.item;
        item2Btn.textContent = item2.item;
      });
    </script>
  </body>
</html>
