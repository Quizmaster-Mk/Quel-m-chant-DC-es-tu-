<!DOCTYPE html>
<html lang="fr">
<head>
  <meta charset="UTF-8" />
  <meta name="viewport" content="width=device-width, initial-scale=1.0"/>
  <title>Quel méchant DC êtes-vous ?</title>
  <style>
    body {
      font-family: 'Courier New', monospace;
      background-color: #001f3f;
      color: #fff;
      margin: 0;
      padding: 20px;
      text-align: center;
    }

    header img {
      max-width: 150px;
      margin-bottom: 20px;
    }

    h1 {
      color: #ffcc00;
      text-shadow: 2px 2px 5px #ff5733;
      font-size: 36px;
      margin-bottom: 20px;
    }

    .question {
      margin: 20px auto;
      background-color: #3399ff;
      color: #000;
      padding: 20px;
      border-radius: 10px;
      max-width: 600px;
      box-shadow: 0 0 10px rgba(255, 204, 0, 0.7);
    }

    .question h2 {
      color: white;
    }

    .options button {
      background-color: #005f99;
      color: #fff;
      padding: 10px 20px;
      border: none;
      margin: 5px;
      font-size: 16px;
      cursor: pointer;
      border-radius: 5px;
      box-shadow: 0 0 5px #003366;
      transition: all 0.3s ease;
    }

    .options button:hover {
      background-color: #003366;
      transform: scale(1.05);
    }

    .result {
      background-color: #3399ff;
      color: #000;
      padding: 20px;
      border-radius: 10px;
      margin-top: 20px;
      display: none;
      box-shadow: 0 0 10px rgba(255, 204, 0, 0.7);
    }

    .score {
      font-size: 16px;
      margin-top: 10px;
      color: #001f3f;
    }
  </style>
</head>
<body>
  <header>
    <img src="https://upload.wikimedia.org/wikipedia/commons/3/3d/DC_Comics_logo.svg" alt="Logo DC">
  </header>

  <h1>Quel méchant DC êtes-vous ?</h1>

  <div id="quiz-container">
    <div class="question" id="question-container">
      <h2 id="question-text"></h2>
      <div class="options" id="options-container"></div>
    </div>
  </div>

  <div class="result" id="result-container">
    <h2>Vous êtes...</h2>
    <p id="result-text"></p>
    <p class="score">Votre résultat est basé sur vos choix !</p>
    <button onclick="startQuiz()">Recommencer le quiz</button>
  </div>

  <script>
    const questions = [
      { question: "Quel est votre but ultime ?", options: ["Dominer le monde", "Semer le chaos", "Vaincre les héros", "Contrôler la nature", "Prouver votre supériorité", "Se venger", "Renverser un dieu", "Gagner de l'argent", "Répandre la peur", "Faire justice à votre manière"], result: [0, 1, 2, 6, 3, 5, 8, 7, 4, 9] },
      { question: "Votre arme favorite ?", options: ["Votre cerveau", "Un marteau géant", "Une toxine", "Un fusil de précision", "Vos poings", "Le pouvoir magique", "Des plantes", "Une bombe", "Des énigmes", "Vos griffes"], result: [0, 5, 4, 7, 6, 8, 4, 1, 3, 9] },
      { question: "Comment traitez-vous vos ennemis ?", options: ["Vous les humiliez", "Vous les détruisez", "Vous jouez avec eux", "Vous les manipulez", "Vous les ignorez", "Vous les séduisez", "Vous les piégez", "Vous les combattez frontalement", "Vous les éliminez rapidement", "Vous les corrompez"], result: [0, 2, 1, 3, 9, 4, 8, 6, 7, 5] },
      { question: "Votre plus grande force ?", options: ["L'intelligence", "L'imprévisibilité", "La force physique", "La stratégie", "La magie", "La ruse", "La technologie", "La cruauté", "La séduction", "La vitesse"], result: [0, 1, 6, 7, 5, 3, 8, 2, 4, 9] },
      { question: "Votre plus grand défaut ?", options: ["Orgueil", "Folie", "Colère", "Jalousie", "Narcissisme", "Cruauté", "Agressivité", "Instabilité", "Manipulation", "Mépris des autres"], result: [0, 1, 6, 4, 9, 2, 5, 3, 8, 7] },
      { question: "Votre ennemi juré ?", options: ["Superman", "Batman", "Wonder Woman", "The Flash", "La Justice League", "Green Arrow", "Aquaman", "Cyborg", "Harley Quinn", "Tout le monde"], result: [0, 1, 9, 6, 2, 7, 5, 8, 4, 3] },
      { question: "Votre look idéal ?", options: ["Costume de PDG", "Maquillage clownesque", "Armure divine", "Tenue verte sexy", "Tenue tactique", "Masque mystérieux", "Look militaire", "Style antique", "Juste un fouet", "Combinaison sombre"], result: [0, 1, 2, 4, 6, 3, 7, 5, 9, 8] },
      { question: "Votre quartier général ?", options: ["Un gratte-ciel", "Un asile", "Une planète infernale", "Une serre", "Une base secrète", "Une forteresse", "Un labo", "Un manoir", "Un camp d’entraînement", "Un vieux théâtre"], result: [0, 1, 2, 4, 6, 8, 3, 5, 7, 9] },
      { question: "Quel mot vous définit ?", options: ["Ambitieux", "Fou", "Impitoyable", "Intellectuel", "Séducteur", "Stratégique", "Vengeur", "Énigmatique", "Divin", "Sauvage"], result: [0, 1, 2, 3, 4, 7, 5, 8, 6, 9] },
      { question: "Quel est votre vice secret ?", options: ["Le pouvoir", "Le chaos", "La destruction", "Le mystère", "L’amour", "L’argent", "L’honneur", "Le savoir", "La justice", "Le sang"], result: [0, 1, 2, 3, 4, 7, 6, 8, 9, 5] }
    ];

    const characters = [
      { name: "Lex Luthor", description: "Le maître manipulateur et rival suprême de Superman, toujours un coup d'avance." },
      { name: "Joker", description: "Le clown prince du crime, imprévisible et redoutablement dérangé." },
      { name: "Darkseid", description: "Un tyran cosmique impitoyable, rêvant d'asservir tout l'univers." },
      { name: "Riddler", description: "L'obsédé des énigmes, vous aimez montrer que vous êtes plus intelligent que tout le monde." },
      { name: "Poison Ivy", description: "Protectrice de la nature, séduisante et dangereuse, vos plantes sont vos armes." },
      { name: "Black Adam", description: "Puissant et antique, vous suivez votre propre code de justice." },
      { name: "Bane", description: "Stratège brutal, vous alliez force physique et intelligence tactique." },
      { name: "Deathstroke", description: "Assassin méthodique, froid et précis, vous êtes une arme humaine." },
      { name: "Harley Quinn", description: "Excentrique, imprévisible, mais farouchement indépendante et attachante." },
      { name: "Cheetah", description: "Féroce et rapide, vous êtes une chasseuse animée par une soif de pouvoir." }
    ];

    let currentQuestion = 0;
    let userAnswers = [];

    function startQuiz() {
      currentQuestion = 0;
      userAnswers = [];
      document.getElementById('result-container').style.display = 'none';
      document.getElementById('quiz-container').style.display = 'block';
      showQuestion();
    }

    function showQuestion() {
      const question = questions[currentQuestion];
      document.getElementById('question-text').innerText = question.question;
      const optionsContainer = document.getElementById('options-container');
      optionsContainer.innerHTML = '';

      question.options.forEach((option, index) => {
        const button = document.createElement('button');
        button.innerText = option;
        button.onclick = () => {
          userAnswers.push(question.result[index]);
          currentQuestion++;
          if (currentQuestion < questions.length) {
            showQuestion();
          } else {
            showResult();
          }
        };
        optionsContainer.appendChild(button);
      });
    }

    function showResult() {
      const counts = Array(characters.length).fill(0);
      userAnswers.forEach(index => counts[index]++);
      const maxIndex = counts.indexOf(Math.max(...counts));
      const result = characters[maxIndex];
      document.getElementById('result-text').innerText = `${result.name} - ${result.description}`;
      document.getElementById('quiz-container').style.display = 'none';
      document.getElementById('result-container').style.display = 'block';
    }

    startQuiz();
  </script>
</body>
</html>
