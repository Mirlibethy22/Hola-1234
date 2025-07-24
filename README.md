<!DOCTYPE html>
<html lang="es">
<head>
  <meta charset="UTF-8">
  <title>¿Quieres ser mi novia?</title>
  <meta name="viewport" content="width=device-width,initial-scale=1">
  <style>
    body {
      margin: 0;
      padding: 0;
      background: radial-gradient(circle at 50% 30%, #f9e0ff 0%, #f7fbfc 100%);
      height: 100vh;
      overflow: hidden;
      display: flex;
      align-items: center;
      justify-content: center;
      perspective: 1200px;
      font-family: 'Poppins', 'Segoe UI', sans-serif;
    }
    .container {
      position: relative;
      text-align: center;
      z-index: 2;
      transform-style: preserve-3d;
      animation: float 6s infinite ease-in-out;
    }
    @keyframes float {
      0% { transform: rotateY(-10deg) translateY(0px); }
      50% { transform: rotateY(10deg) translateY(-30px); }
      100% { transform: rotateY(-10deg) translateY(0px); }
    }
    .holo-text {
      font-size: 3.5rem;
      font-weight: bold;
      letter-spacing: 0.08em;
      background: linear-gradient(90deg, #e100ff, #00f9ff, #ff007a, #fff200 90%);
      background-size: 200% auto;
      background-clip: text;
      -webkit-background-clip: text;
      color: transparent;
      -webkit-text-stroke: 1.5px #fff0;
      text-shadow:
        0 0 35px #fff7,
        0 2px 10px #e100ff88,
        0 4px 20px #00f9ffaa,
        0 0 10px #ff007a44,
        0 0 0 #fff;
      filter: drop-shadow(0 0 5px #fff);
      animation: holo-gradient 4s infinite linear;
    }
    @keyframes holo-gradient {
      0% { background-position: 0% 50%; }
      100% { background-position: 100% 50%; }
    }
    .kiss {
      font-size: 2rem;
      position: absolute;
      animation: flykiss 5s infinite alternate;
      filter: blur(0.5px) drop-shadow(0 0 6px #ffb6c1);
    }
    .kiss1 { left: 10%; top: -40px; animation-delay: 0s;}
    .kiss2 { right: 10%; top: -40px; animation-delay: 1.2s;}
    .kiss3 { left: 40%; bottom: -40px; animation-delay: 2.4s;}
    .kiss4 { right: 40%; bottom: -40px; animation-delay: 3.6s;}
    @keyframes flykiss {
      0% { transform: scale(1) rotate(-10deg);}
      50% { transform: scale(1.3) rotate(15deg) translateY(-20px);}
      100% { transform: scale(1) rotate(-10deg);}
    }
    .heart3d {
      position: absolute;
      width: 100px;
      height: 90px;
      left: 50%;
      top: 50%;
      transform: translate(-50%, -50%) rotateY(0deg);
      animation: spinHeart 5s infinite linear;
      z-index: -1;
      pointer-events: none;
    }
    @keyframes spinHeart {
      0% { transform: translate(-50%,-50%) rotateY(0deg);}
      100% { transform: translate(-50%,-50%) rotateY(360deg);}
    }
    /* 3D Heart CSS */
    .heart3d .heart-shape {
      position: absolute;
      width: 100px;
      height: 90px;
      left: 0; top: 0;
      background: radial-gradient(circle at 50% 30%, #ff4f70 80%, #ffbfd7 100%);
      clip-path: path('M50 15 Q90 15 90 50 Q90 85 50 85 Q10 85 10 50 Q10 15 50 15 Z');
      box-shadow: 0 0 40px #ff4f70cc, 0 0 100px #ffbfd7aa;
      filter: blur(0.5px);
      opacity: 0.8;
      transform-style: preserve-3d;
    }
    .heart3d .shine {
      position: absolute;
      left: 35px;
      top: 35px;
      width: 30px;
      height: 25px;
      background: radial-gradient(ellipse at center, #fff7 60%, #fff0 100%);
      border-radius: 50%;
      opacity: 0.7;
      z-index: 2;
      transform: rotate(-15deg);
    }
    /* Floating animated hearts */
    .floating-heart {
      position: absolute;
      font-size: 2.2rem;
      pointer-events: none;
      opacity: 0.85;
      filter: drop-shadow(0 0 10px #ff90b3);
      animation: floatHeart 8s infinite ease-in-out;
    }
    @keyframes floatHeart {
      0% { transform: translateY(0) scale(1); opacity:0.7;}
      40% { transform: translateY(-120px) scale(1.2); opacity:1;}
      100% { transform: translateY(-220px) scale(0.9); opacity:0;}
    }
    /* Holographic glitter particles */
    .glitter {
      position: absolute;
      width: 8px; height: 8px;
      pointer-events: none;
      border-radius: 50%;
      background: linear-gradient(45deg, #fff, #e100ff, #00f9ff, #ff007a, #fff200);
      filter: blur(2px) brightness(1.5);
      opacity: 0.6;
      animation: glitterAnim 3s infinite alternate;
    }
    @keyframes glitterAnim {
      from { transform: scale(1);}
      to { transform: scale(1.8);}
    }
    /* Rainbow border */
    .rainbow-border {
      position: absolute;
      inset: -18px;
      border: 8px solid transparent;
      border-image: linear-gradient(120deg, #ff4f70, #e100ff, #00f9ff, #fff200, #ff4f70) 1;
      border-radius: 32px;
      z-index: 0;
      animation: rainbowSpin 8s linear infinite;
      pointer-events: none;
    }
    @keyframes rainbowSpin {
      0% { filter: hue-rotate(0deg);}
      100% { filter: hue-rotate(360deg);}
    }
  </style>
</head>
<body>
  <div class="rainbow-border"></div>
  <div class="container">
    <div class="kiss kiss1">💋</div>
    <div class="kiss kiss2">😘</div>
    <div class="kiss kiss3">💖</div>
    <div class="kiss kiss4">💞</div>
    <div class="heart3d">
      <div class="heart-shape"></div>
      <div class="shine"></div>
    </div>
    <div class="holo-text">¿Quieres ser mi novia?</div>
  </div>
  <!-- Hearts & Glitter will be dynamically added -->
  <script>
    // Floating hearts array
    const heartEmojis = ["❤️","💗","💓","💖","💕","💘","💝","🧡","💜","💙","💚"];
    for(let i=0;i<28;i++){
      const heart = document.createElement('div');
      heart.className = 'floating-heart';
      heart.textContent = heartEmojis[Math.floor(Math.random()*heartEmojis.length)];
      heart.style.left = (Math.random()*96)+"vw";
      heart.style.top = (40+Math.random()*40)+"vh";
      heart.style.animationDelay = (Math.random()*8)+"s";
      heart.style.fontSize = (2 + Math.random()*2)+"rem";
      document.body.appendChild(heart);
    }
    // Glitter particles
    for(let i=0;i<24;i++){
      const glitter = document.createElement('div');
      glitter.className = 'glitter';
      glitter.style.left = (Math.random()*98)+"vw";
      glitter.style.top = (Math.random()*98)+"vh";
      glitter.style.animationDelay = (Math.random()*3)+"s";
      document.body.appendChild(glitter);
    }
  </script>
</body>
</html>
