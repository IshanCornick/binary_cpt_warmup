---
hide: True
layout: notebook
title: Binary Song Converter
type: hacks
courses: {'compsci': {'week': 1}}
---

<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Song to Binary Converter</title>
</head>
<body>
    <h1>Song to Binary Converter</h1>
    <textarea id="songInput" placeholder="Enter song lyrics here..." rows="10" cols="50" oninput="convertToBinary()"></textarea>
    <h2>Binary Output</h2>
    <div id="binaryOutput"></div>
    <script>
        function convertToBinary() {
            const lyrics = document.getElementById('songInput').value;
            const binaryOutput = lyrics.split('').map(char => {
                return char.charCodeAt(0).toString(2).padStart(8, '0');
            }).join(' ');
            document.getElementById('binaryOutput').innerText = binaryOutput;
        }
    </script>
</body>
</html>
