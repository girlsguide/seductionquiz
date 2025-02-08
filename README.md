<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Feminine Seduction Type Quiz</title>
    <style>
        body { font-family: Arial, sans-serif; text-align: center; padding: 20px; }
        .quiz-container { max-width: 500px; margin: auto; }
        .hidden { display: none; }
    </style>
</head>
<body>
    <div class="quiz-container">
        <h2>What's Your Feminine Seduction Type? 💕</h2>
        <form id="quizForm">
            <p>1. How do you naturally attract attention?</p>
            <label><input type="radio" name="q1" value="Femme Fatale"> Mysterious & Magnetic</label><br>
            <label><input type="radio" name="q1" value="Girl Next Door"> Friendly & Approachable</label><br>
            <label><input type="radio" name="q1" value="Princess"> Elegant & Graceful</label><br>
            
            <p>2. What's your ideal first date?</p>
            <label><input type="radio" name="q2" value="Femme Fatale"> A passionate, deep conversation over wine</label><br>
            <label><input type="radio" name="q2" value="Girl Next Door"> A cozy coffee date</label><br>
            <label><input type="radio" name="q2" value="Princess"> A luxury dinner with candlelight</label><br>
            
            <button type="button" onclick="calculateResult()">See Your Result</button>
        </form>

        <div id="emailSection" class="hidden">
            <h3>Enter Your Email to See Your Result ✨</h3>
            <input type="email" id="email" placeholder="Your email" required>
            <button onclick="showResult()">Submit</button>
        </div>

        <div id="result" class="hidden">
            <h3>Your Feminine Seduction Type is: <span id="resultType"></span> 💖</h3>
            <p>Learn more about your type in my exclusive email series! 🌟</p>
        </div>
    </div>

    <script>
        let selectedType = "";

        function calculateResult() {
            const answers = document.querySelectorAll('input[type="radio"]:checked');
            if (answers.length < 2) {
                alert("Please answer all questions!");
                return;
            }

            let counts = { "Femme Fatale": 0, "Girl Next Door": 0, "Princess": 0 };
            answers.forEach(ans => counts[ans.value]++);
            selectedType = Object.keys(counts).reduce((a, b) => counts[a] > counts[b] ? a : b);

            document.getElementById("quizForm").classList.add("hidden");
            document.getElementById("emailSection").classList.remove("hidden");
        }

        function showResult() {
            let email = document.getElementById("email").value;
            if (!email.includes("@")) {
                alert("Please enter a valid email!");
                return;
            }

            document.getElementById("emailSection").classList.add("hidden");
            document.getElementById("result").classList.remove("hidden");
            document.getElementById("resultType").textContent = selectedType;
        }
    </script>
</body>
</html>
