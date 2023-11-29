---
hide: True
layout: notebook
title: Binary Logical Operators
type: hacks
courses: {'compsci': {'week': 1}}
---

<html lang="en">
<head>
    <meta charset="UTF-8">
    <title>Binary Logical Operations</title>
</head>
<body>
    <br>
    <label>Input 1: <input type="text" id="input1" placeholder="Enter binary number"></label>
    <br>
    <br>
    <label id="input2Label">Input 2: <input type="text" id="input2" placeholder="Enter binary number"></label>
    <br>
    <br>
    <select id="operation" onchange="toggleInput2()">
        <option value="AND">AND</option>
        <option value="OR">OR</option>
        <option value="XOR">XOR</option>
        <option value="NOT">NOT</option>
    </select>
    <br>
    <br>
    <button onclick="performOperation()">Calculate</button>
    <br>
    <br>
    <div23>Result: <span id="result"></span></div23>
    <script>
        function toggleInput2() {
            document.getElementById('input2Label').style.display = 
                document.getElementById('operation').value === 'NOT' ? 'none' : 'inline';
        }
        function performOperation() {
            let input1 = parseInt(document.getElementById('input1').value, 2);
            let input2 = parseInt(document.getElementById('input2').value, 2);
            const operation = document.getElementById('operation').value;
            let result;
            switch (operation) {
                case 'AND': result = input1 & input2; break;
                case 'OR': result = input1 | input2; break;
                case 'XOR': result = input1 ^ input2; break;
                case 'NOT': 
                    // Limit input1 to 8 bits
                    input1 = input1 & 0xFF;
                    // Perform NOT operation and limit result to 8 bits
                    result = (~input1) & 0xFF; 
                    break;
                default: result = 'Invalid operation'; return;
            }
            const binaryResult = formatByte(result);
            document.getElementById('result').textContent = binaryResult + ' (Decimal: ' + result + ')';
        }
        function formatByte(number) {
            return ('00000000' + number.toString(2)).substr(-8);
        }
        toggleInput2(); // Initial call to set up the correct display
    </script>
</body>
</html>

