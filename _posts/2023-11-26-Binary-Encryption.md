---
hide: True
layout: notebook
title: Binary Encryption
type: hacks
courses: {'compsci': {'week': 1}}
---

<html>
<body>
    <h2>Binary Encryption</h2>
    <textarea id="inputText" placeholder="Enter text here"></textarea><br>
    <button onclick="encrypt()">Encrypt</button>
    <button onclick="decrypt()">Decrypt</button><br>
    <h2>Result:</h2>
    <p id="result"></p>
</body>
</html>
<script>
    function encrypt() {
    var input = document.getElementById("inputText").value;
    var binary = '';
    for (var i = 0; i < input.length; i++) {
        binary += input[i].charCodeAt(0).toString(2) + " ";
    }
    document.getElementById("result").innerText = binary.trim();
    }
    function decrypt() {
        var input = document.getElementById("inputText").value;
        var text = '';
        var arr = input.split(" ");
        for (var i = 0; i < arr.length; i++) {
            text += String.fromCharCode(parseInt(arr[i], 2));
        }
        document.getElementById("result").innerText = text;
    }
</script>