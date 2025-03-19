<!DOCTYPE html>
<html lang="el">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>Μαθαίνω Μαθηματικά</title>
  <style>
    body { 
      font-family: Arial, sans-serif; 
      text-align: center; 
      background-color: #f4f4f4; 
    }
    .container { 
      max-width: 600px; 
      margin: 50px auto; 
      padding: 20px; 
      background: white; 
      box-shadow: 0px 0px 10px rgba(0, 0, 0, 0.1); 
      border-radius: 10px; 
    }
    button { 
      background: #28a745; 
      color: white; 
      padding: 10px; 
      border: none; 
      cursor: pointer; 
      border-radius: 5px; 
      margin: 5px;
    }
    button:hover { 
      background: #218838; 
    }
  </style>
</head>
<body>
  <div class="container">
    <h1>Μαθαίνω Μαθηματικά</h1>
    <p>Λύσε την παρακάτω αριθμητική πράξη:</p>
    <h2 id="question"></h2>
    <input type="number" id="answer" placeholder="Γράψε την απάντηση">
    <br>
    <button onclick="checkAnswer()">Υποβολή</button>
    <button onclick="generateQuestion()">Νέα Ερώτηση</button>
    <p id="feedback"></p>
  </div>
  
  <script>
    let num1, num2, correctAnswer, operation;
    
    function generateQuestion() {
      const operations = ['+', '-', '*', '/'];
      operation = operations[Math.floor(Math.random() * operations.length)];
      
      if (operation === '+') {
        num1 = Math.floor(Math.random() * 10) + 1;
        num2 = Math.floor(Math.random() * 10) + 1;
        correctAnswer = num1 + num2;
      } else if (operation === '-') {
        num1 = Math.floor(Math.random() * 10) + 1;
        num2 = Math.floor(Math.random() * 10) + 1;
        // Διασφαλίζουμε θετικό αποτέλεσμα
        if (num2 > num1) {
          [num1, num2] = [num2, num1];
        }
        correctAnswer = num1 - num2;
      } else if (operation === '*') {
        num1 = Math.floor(Math.random() * 10) + 1;
        num2 = Math.floor(Math.random() * 10) + 1;
        correctAnswer = num1 * num2;
      } else if (operation === '/') {
        // Επιλογή διαιρέτη και αποτελέσματος ώστε να έχουμε ακέραιο πηλίκο
        num2 = Math.floor(Math.random() * 9) + 1; 
        correctAnswer = Math.floor(Math.random() * 10) + 1;
        num1 = num2 * correctAnswer;
      }
      
      document.getElementById("question").innerText = `${num1} ${operation} ${num2} = ?`;
      document.getElementById("feedback").innerText = "";
      document.getElementById("answer").value = "";
    }
    
    function checkAnswer() {
      let userAnswer = parseFloat(document.getElementById("answer").value);
      let feedback = document.getElementById("feedback");
      
      if (userAnswer === correctAnswer) {
        feedback.innerText = "Σωστό! Μπράβο!";
        feedback.style.color = "green";
      } else {
        feedback.innerText = "Λάθος, προσπάθησε ξανά.";
        feedback.style.color = "red";
      }
    }
    
    // Δημιουργία αρχικής ερώτησης κατά την φόρτωση της σελίδας
    generateQuestion();
  </script>
</body>
</html>
