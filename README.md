
<html>
  <head>
    <title>Invention Game</title>
    <style>
      body {
        background-image: url("https://media-cldnry.s-nbcnews.com/image/upload/newscms/2019_18/1432153/cinco-de-mayo-celebrations-today-main-190501.jpg");
        background-size: cover;
      }
      
      #game-board {
        display: flex;
        flex-direction: column;
        align-items: center;
      }
      
            button {
        font-size: 2.4em;
        margin: 70px;
        padding: 30px;
      }
      
      /* added styles for the h1 element */
      h1 {
        font-size: 2.5em;
        background-color: #ccc;
        padding: 20px 20px 10px 10px;
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
        { item: "The Battle Of Puebla", year: 1862 },
        { item: "Mexican Independance Declared", year: 1810 },
        { item: "The Mexican Peso becoming the official currency of mexico", year: 1823 },
        { item: "The First Commercial Flight by a Mexican Airline", year: 1921},
        { item: "The Establishing of the Bank Of Mexio", year: 1925},
        { item: "The First Celebration of Cinco De Mayo in the USA", year: 1863},

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
