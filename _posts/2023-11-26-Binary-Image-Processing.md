---
hide: True
layout: notebook
title: Binary Image Processing
type: hacks
courses: {'compsci': {'week': 1}}
---

<html lang="en">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>Binary Image Processing with JS</title>
  <style>
    #processButton { display: none; } /* Initially hide the process button */
  </style>
</head>
<body>
  <label for="imageLink">Image Link:</label>
  <br>
  <input type="text" id="imageLink" placeholder="Enter image link...">
  <br>
  <button id="loadButton">Load Image</button>
  <br>
  <canvas id="canvas" width="300" height="300" style="border:1px solid #000;"></canvas>
  <br>
  <button id="processButton">Process Image to Binary</button>

  <script>
    document.addEventListener('DOMContentLoaded', function() {
      const canvas = document.getElementById('canvas');
      const ctx = canvas.getContext('2d');
      const loadButton = document.getElementById('loadButton');
      const processButton = document.getElementById('processButton');
      let img = new Image();

      function clearCanvas() {
        ctx.clearRect(0, 0, canvas.width, canvas.height);
      }

      function loadAndDisplayImage() {
        const imageLink = document.getElementById('imageLink').value;
        
        if (!imageLink) {
          alert('Please enter an image link.');
          return;
        }

        clearCanvas();
        img.crossOrigin = 'Anonymous';
        img.onload = function() {
          ctx.drawImage(img, 0, 0, canvas.width, canvas.height);
          processButton.style.display = 'inline'; // Show process button on image load
        };
        img.onerror = function() {
          alert('Error loading image. Please check the URL and try again.');
          processButton.style.display = 'none'; // Hide process button on error
        };

        img.src = imageLink;
      }

      function convertToBinary(imageData) {
        const data = imageData.data;
        for (let i = 0; i < data.length; i += 4) {
          const brightness = 0.34 * data[i] + 0.5 * data[i + 1] + 0.16 * data[i + 2];
          const threshold = 128;
          const color = brightness > threshold ? 255 : 0;
          data[i] = data[i + 1] = data[i + 2] = color;
        }
        return imageData;
      }

      function processImage() {
        if (!img.src) {
          alert('Please load an image first.');
          return;
        }

        const imageData = ctx.getImageData(0, 0, canvas.width, canvas.height);
        const binaryData = convertToBinary(imageData);
        ctx.putImageData(binaryData, 0, 0);
      }

      loadButton.addEventListener('click', loadAndDisplayImage);
      processButton.addEventListener('click', processImage);
    });
  </script>
</body>
</html>
