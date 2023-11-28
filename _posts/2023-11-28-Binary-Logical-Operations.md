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
    <h1>Binary Logic Operations</h1>
    <div>
        <label>Input 1: <input type="text" id="input1"></label>
    </div>
    <div>
        <label>Input 2: <input type="text" id="input2"></label>
    </div>
    <div>
        <select id="operation">
            <option value="AND">AND</option>
            <option value="OR">OR</option>
            <option value="XOR">XOR</option>
            <option value="NOT">NOT</option>
        </select>
    </div>
    <button onclick="performOperation()">Calculate</button>
    <div id="result">Result: </div>
    <script>
        function performOperation() {
            const input1 = document.getElementById('input1').value;
            const input2 = document.getElementById('input2').value;
            const operation = document.getElementById('operation').value;
            let result;
            switch (operation) {
                case 'AND':
                    result = (parseInt(input1, 2) & parseInt(input2, 2)).toString(2);
                    break;
                case 'OR':
                    result = (parseInt(input1, 2) | parseInt(input2, 2)).toString(2);
                    break;
                case 'XOR':
                    result = (parseInt(input1, 2) ^ parseInt(input2, 2)).toString(2);
                    break;
                case 'NOT':
                    result = (~parseInt(input1, 2)).toString(2);
                    break;
                default:
                    result = 'Invalid operation';
            }
            document.getElementById('result').innerHTML = 'Result: ' + result;
        }
    </script>
</body>
</html>
