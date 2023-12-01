---
hide: True
layout: notebook
title: Binary Game
type: hacks
courses: {'compsci': {'week': 1}}
---

<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Binary Guessing Game</title>
</head>
<body>
    <h1>Welcome to the Binary Guessing Game!</h1>
    <div>
        <!-- Updated input field with pattern and maxlength -->
        <input type="text" id="userGuess" placeholder="Enter your binary guess" pattern="^[0-1]{1,8}$" maxlength="8"/>
        <button onclick="makeAGuess()">Guess</button>
    </div>
    <div44 id="output"></div44>
    <script>
        var minValue = 0;
        var maxValue = 255;
        var secretBinary = generateRandomBinary(minValue, maxValue);
        var attempts = 0;
        var outputDiv = document.getElementById('output');
        function generateRandomBinary(minValue, maxValue) {
            return (Math.floor(Math.random() * (maxValue - minValue + 1)) + minValue).toString(2);
        }
        function makeAGuess() {
            var playerGuess = document.getElementById('userGuess').value;
            // Validate the input
            if (!/^[0-1]{1,8}$/.test(playerGuess)) {
                outputDiv.innerHTML = "Invalid input. Please enter a binary number (0s and 1s) with up to 8 digits.";
                return;
            }
            try {
                var guessDecimal = parseInt(playerGuess, 2);
                if (playerGuess === secretBinary) {
                    outputDiv.innerHTML = `Congratulations! You guessed the correct binary number ${secretBinary} (decimal: ${guessDecimal}) in ${attempts} attempts.`;
                } else {
                    if (playerGuess < secretBinary) {
                        outputDiv.innerHTML = `Too low! Your guess ${playerGuess} in decimal is ${guessDecimal}. Try again.`;
                        minValue = guessDecimal + 1;
                    } else {
                        outputDiv.innerHTML = `Too high! Your guess ${playerGuess} in decimal is ${guessDecimal}. Try again.`;
                        maxValue = guessDecimal - 1;
                    }
                    attempts += 1;
                }
            } catch (error) {
                outputDiv.innerHTML = "Invalid input. Please enter a valid binary number.";
            }
        }
    </script>
</body>
</html>
