---
hide: True
layout: notebook
title: Binary Image Processing
type: hacks
courses: {'compsci': {'week': 1}}
---

<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>Binary Image Processing with JS</title>
</head>
<body>
  <label for="imageLink">Image Link:</label>
  <input type="text" id="imageLink" placeholder="Enter image link...">
  <button onclick="processImage()">Process Image</button>
  <canvas id="canvas" width="300" height="300" style="border:1px solid #000;"></canvas>

  <script>
    document.addEventListener('DOMContentLoaded', function() {
      const canvas = document.getElementById('canvas');
      const ctx = canvas.getContext('2d');

      function drawBinaryImage() {
        ctx.fillStyle = 'white';
        ctx.fillRect(50, 50, 50, 50);
        ctx.fillStyle = 'black';
        ctx.fillRect(150, 150, 50, 50);
      }

      function clearCanvas() {
        ctx.clearRect(0, 0, canvas.width, canvas.height);
      }

      function processImage() {
        const imageLink = document.getElementById('imageLink').value;
        
        if (!imageLink) {
          alert('Please enter an image link.');
          return;
        }

        clearCanvas();

        const proxyUrl = 'https://cors-anywhere.herokuapp.com/';
        const imageUrl = proxyUrl + imageLink;

        const img = new Image();
        img.crossOrigin = 'Anonymous';
        img.src = imageUrl;

        img.onload = function() {
          ctx.drawImage(img, 0, 0, canvas.width, canvas.height);
        };
      }

      drawBinaryImage();
    });
  </script>
</body>
</html>
