# Math_learning_app
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
        <button onclick="checkAnswer()">Υποβολή</button>
        <p id="feedback"></p>
    </div>
    
    <script>
        let num1 = Math.floor(Math.random() * 10) + 1;
        let num2 = Math.floor(Math.random() * 10) + 1;
        let correctAnswer = num1 + num2;
        document.getElementById("question").innerText = `${num1} + ${num2} = ?`;
        
        function checkAnswer() {
            let userAnswer = document.getElementById("answer").value;
            let feedback = document.getElementById("feedback");
            if (parseInt(userAnswer) === correctAnswer) {
                feedback.innerText = "Σωστό! Μπράβο!";
                feedback.style.color = "green";
            } else {
                feedback.innerText = "Λάθος, προσπάθησε ξανά.";
                feedback.style.color = "red";
            }
        }
    </script>
</body>
</html>
