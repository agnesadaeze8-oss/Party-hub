<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <title>Party Hub</title>
  <meta name="viewport" content="width=device-width, initial-scale=1.0">

  <style>
    body {
      margin: 0;
      font-family: Arial, sans-serif;
      background: linear-gradient(135deg, #6a11cb, #2575fc);
      color: #fff;
      text-align: center;
    }

    .container {
      padding: 20px;
      max-width: 500px;
      margin: auto;
    }

    h1 {
      margin-top: 40px;
      font-size: 2.5em;
    }

    button {
      width: 100%;
      padding: 15px;
      margin: 10px 0;
      font-size: 1.1em;
      border: none;
      border-radius: 10px;
      cursor: pointer;
      background: #fff;
      color: #2575fc;
      font-weight: bold;
    }

    button:hover {
      background: #f1f1f1;
    }

    .card {
      background: rgba(255,255,255,0.15);
      padding: 20px;
      border-radius: 15px;
      margin-top: 30px;
      min-height: 100px;
    }

    .hidden {
      display: none;
    }

    footer {
      margin-top: 40px;
      font-size: 0.8em;
      opacity: 0.8;
    }
  </style>
</head>

<body>

  <div class="container">
    <h1>🎉 Party Hub</h1>
    <p>Choose a game mode</p>

    <div id="menu">
      <button onclick="startGame('ice')">🧊 Ice Breakers</button>
      <button onclick="startGame('party')">🎲 Party Games</button>
      <button onclick="startGame('drink')">🍹 Drinking Games</button>
    </div>

    <div id="game" class="hidden">
      <div class="card" id="question"></div>
      <button onclick="nextQuestion()">Next</button>
      <button onclick="goBack()">Back to Menu</button>
    </div>

    <footer>
      Party Hub MVP • Play with friends
    </footer>
  </div>

  <script>
    const games = {
      ice: [
        "What’s your most embarrassing moment?",
        "If you could live anywhere, where would it be?",
        "What’s one secret talent you have?"
      ],
      party: [
        "Everyone dance for 10 seconds!",
        "Last person to clap takes a forfeit!",
        "Vote who would survive a zombie apocalypse."
      ],
      drink: [
        "Take 2 sips if you’ve ever skipped class.",
        "Drink if your phone battery is below 20%.",
        "Choose someone to drink."
      ]
    };

    let currentGame = [];
    let index = 0;

    function startGame(type) {
      currentGame = games[type];
      index = 0;
      document.getElementById("menu").classList.add("hidden");
      document.getElementById("game").classList.remove("hidden");
      showQuestion();
    }

    function showQuestion() {
      document.getElementById("question").innerText =
        currentGame[index];
    }

    function nextQuestion() {
      index = (index + 1) % currentGame.length;
      showQuestion();
    }

    function goBack() {
      document.getElementById("game").classList.add("hidden");
      document.getElementById("menu").classList.remove("hidden");
    }
  </script>

</body>
</html>
