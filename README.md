<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>🎉 Happy Birthday! 🎉</title>
  <style>
    body {
      text-align: center;
      background: linear-gradient(135deg, #f9a8d4, #fbcfe8);
      color: #850e65;
      font-family: 'Comic Sans MS', cursive;
    }

    h1 {
      font-size: 3em;
      margin-top: 50px;
      animation: bounceIn 2s ease;
    }

    #message {
      margin: 20px auto;
      font-size: 1.5em;
      width: 80%;
      animation: fadeIn 3s;
    }

    @keyframes fadeIn {
      from { opacity: 0; }
      to { opacity: 1; }
    }

    @keyframes bounceIn {
      0%, 20%, 50%, 80%, 100% {
        transform: translateY(0);
      }
      40% {
        transform: translateY(-30px);
      }
      60% {
        transform: translateY(-15px);
      }
    }

    #confettiCanvas {
      position: fixed;
      top: 0;
      left: 0;
      width: 100%;
      height: 100%;
      pointer-events: none;
      z-index: 0;
    }

    /* Photo card styling */
    #photoCard {
      width: 300px; /* 4/2 ratio of the page */
      border: 5px solid #961154; /* Shocking pink border */
      border-radius: 15px;
      overflow: hidden;
      position: absolute;
      bottom: 5%; /* Positioned at the bottom half of the screen */
      left: 50%;
      transform: translateX(-50%);
      box-shadow: 0px 4px 10px rgba(0, 0, 0, 0.1);
      background-color: white;
    }

    #photoCard img {
      width: 100%;
      height: auto;
    }
  </style>
</head>
<body>
  <canvas id="confettiCanvas"></canvas>

  <h1>🎉 Happy Birthday Fairy! 🎉</h1>
  <p id="message">
    Happy Birthday Best Friend😀 Many Happy returns of the day! Wishing you a year, full of joy, laughter, and amazing memories. Enjoy every moment because you deserve it all!! 
  </p>

  <!-- Photo Card Section -->
  <div id="photoCard">
    <!-- Add the URL to your photo here -->
    <img src="IMG_70DDA439F6C2-1.jpeg" alt="Picture of Us">
  </div>
  
  <audio id="happyBirthdaySong" src="https://www.bensound.com/bensound-music/bensound-birthdaysong.mp3"></audio>

  <script>
    // Confetti effect
    var canvas = document.getElementById('confettiCanvas');
    var ctx = canvas.getContext('2d');
    var confettiElements = [];
    var confettiCount = 300;

    function resizeCanvas() {
      canvas.width = window.innerWidth;
      canvas.height = window.innerHeight;
    }

    window.addEventListener('resize', resizeCanvas);
    resizeCanvas();

    function createConfetti() {
      for (let i = 0; i < confettiCount; i++) {
        confettiElements.push({
          x: Math.random() * canvas.width,
          y: Math.random() * canvas.height - canvas.height,
          size: Math.random() * 10 + 5,
          speedX: Math.random() * 2 - 1,
          speedY: Math.random() * 4 + 1,
          color: `hsl(${Math.random() * 360}, 100%, 50%)`
        });
      }
    }

    function drawConfetti() {
      ctx.clearRect(0, 0, canvas.width, canvas.height);
      confettiElements.forEach(function (c) {
        c.x += c.speedX;
        c.y += c.speedY;
        if (c.y > canvas.height) {
          c.y = -10;
        }
        ctx.fillStyle = c.color;
        ctx.fillRect(c.x, c.y, c.size, c.size);
      });
    }

    function updateConfetti() {
      drawConfetti();
      requestAnimationFrame(updateConfetti);
    }

    createConfetti();
    updateConfetti();

    // Automatically play birthday song on load
    var audio = document.getElementById('happyBirthdaySong');
    window.onload = function() {
      audio.play();
    };
  </script>
</body>
</html>

