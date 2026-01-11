# TASK-FLOW
<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>CodeQuiz</title>
  <link rel="stylesheet" href="style.css">
</head>
<body>

  <div class="quiz-container">
    <h1>CodeQuiz</h1>
    <div id="question"></div>
    
    <div id="options"></div>
    <button id="nextBtn" onclick="nextQuestion()">Next</button>
    <h3 id="result"></h3>
  </div>

  <script src="script.js"></script>
</body>
</html>
body {
  font-family: Arial, sans-serif;
  background: #eef;
  margin: 0;
  padding: 0;
}

.quiz-container {
  width: 350px;
  background: white;
  margin: 60px auto;
  padding: 20px;
  border-radius: 10px;
}

button {
  width: 100%;
  padding: 10px;
  margin-top: 15px;
  background: #007bff;
  color: white;
  border: none;
  border-radius: 5px;
  cursor: pointer;
}

.option-btn {
  display: block;
  width: 100%;
  padding: 10px;
  margin: 8px 0;
  background: #ddd;
  border-radius: 5px;
  cursor: pointer;
}
let questions = [
  {
    q: "Which language runs in a web browser?",
    options: ["Python", "Java", "C++", "JavaScript"],
    answer: "JavaScript"
  },
  {
    q: "CSS stands for?",
    options: ["Color Style Sheets", "Cascading Style Sheets", "Coding Style System", "None"],
    answer: "Cascading Style Sheets"
  }
];

let index = 0;
let score = 0;

function loadQuestion() {
  document.getElementById("result").innerHTML = "";
  document.getElementById("question").innerHTML = questions[index].q;
  
  let optionsHtml = "";
  questions[index].options.forEach(option => {
    optionsHtml += `<button class="option-btn" onclick="selectOption('${option}')">${option}</button>`;
  });
  
  document.getElementById("options").innerHTML = optionsHtml;
}

function selectOption(selected) {
  if (selected === questions[index].answer) score++;
  index++;
  if (index >= questions.length) showResult();
  else loadQuestion();
}

function nextQuestion() {
  loadQuestion();
}

function showResult() {
  document.getElementById("question").innerHTML = "Quiz Completed!";
  document.getElementById("options").innerHTML = "";
  document.getElementById("result").innerHTML = `Score: ${score} / ${questions.length}`;
}

loadQuestion();
