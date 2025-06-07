<!DOCTYPE html>
<html lang="pt-BR">
<head>
  <meta charset="UTF-8" />
  <meta name="viewport" content="width=device-width, initial-scale=1" />
  <title>Para Meu Amor ❤️</title>
  <style>
    html, body {
      margin: 0;
      padding: 0;
      height: 100%;
      background: #b22222;
      overflow: hidden;
      font-family: Arial, Helvetica, sans-serif;
      color: white;
      display: flex;
      justify-content: center;
      align-items: center;
      flex-direction: column;
      text-align: center;
    }

    canvas {
      position: fixed;
      top: 0;
      left: 0;
      z-index: -1;
      width: 100%;
      height: 100%;
    }

    .container {
      background: rgba(255, 255, 255, 0.1);
      backdrop-filter: blur(10px);
      padding: 30px;
      border-radius: 20px;
      max-width: 400px;
      width: 90%;
      user-select: none;
    }

    .polaroid {
      background: white;
      padding: 10px;
      border-radius: 10px;
      box-shadow: 0 5px 15px rgba(0,0,0,0.3);
      margin-bottom: 20px;
      cursor: pointer;
    }

    .polaroid img {
      width: 100%;
      border-radius: 5px;
      display: block;
      margin: 0 auto;
      max-width: 350px;
      animation: pulse 3s infinite;
    }

    .caption {
      font-size: 1.2em;
      margin-top: 10px;
      color: #b22222;
      font-weight: bold;
    }

    .text-below {
      font-size: 1.4em;
      margin-bottom: 20px;
      color: white;
      text-shadow: 1px 1px 3px rgba(0,0,0,0.4);
    }

    iframe.spotify-player {
      border-radius: 12px;
      width: 100%;
      height: 80px;
      border: none;
      margin-bottom: 15px;
    }

    .lyrics {
      font-size: 1.1em;
      color: white;
      text-shadow: 1px 1px 4px rgba(0,0,0,0.7);
      white-space: pre-wrap;
      margin-top: 0;
      margin-bottom: 15px;
      font-weight: normal;
      font-family: Arial, Helvetica, sans-serif;
    }

    @keyframes pulse {
      0%, 100% { transform: scale(1); }
      50% { transform: scale(1.03); }
    }
  </style>
</head>
<body>
  <canvas id="heartCanvas"></canvas>

  <div class="container">
    <div class="polaroid" title="Clique na foto e veja a mágica ✨">
      <img id="mainImage" src="https://i.postimg.cc/HVxrX9W2/foto-pb.jpg" alt="Casal" />
      <div class="caption">Clique na foto e veja a mágica ✨</div>
    </div>

    <div class="text-below">
      você na minha vida é tão especial assim como o impala é especial para o Dean, você chegou na minha vida e a mudou por completo, meus dias passaram a ter mais cor e a minha vida passou a ser mais feliz, não pude comprar um presente mas fiz isso para você. saiba que eu te amo muito meu amor da minha vida 🩷✨️
    </div>

    <iframe
      class="spotify-player"
      src="https://open.spotify.com/embed/track/5PT9tP3oj4SQByxzjxj0hR"
      allow="autoplay; clipboard-write; encrypted-media; fullscreen; picture-in-picture"
      allowfullscreen
      loading="lazy"
      title="Spotify Player"
    ></iframe>

    <pre class="lyrics">
Oh, she knows what I think about
And what I think about
One love, two mouths
One love, one house
No shirt, no blouse
Just us, you find out
Nothing that I wouldn't wanna tell you about, no
'Cause it's too cold
For you here
And now, so let me hold
Both your hands in the holes of my sweater
    </pre>
  </div>

  <script>
    const canvas = document.getElementById('heartCanvas');
    const ctx = canvas.getContext('2d');
    let hearts = [];

    function resizeCanvas() {
      canvas.width = window.innerWidth;
      canvas.height = window.innerHeight;
    }
    window.addEventListener('resize', resizeCanvas);
    resizeCanvas();

    function createHeart() {
      return {
        x: Math.random() * canvas.width,
        y: -10,
        size: Math.random() * 0.6 + 0.4,
        dy: Math.random() * 1 + 1,
        color: 'pink',
      };
    }

    function drawHeart(x, y, size, color) {
      ctx.save();
      ctx.translate(x, y);
      ctx.scale(size, size);
      ctx.beginPath();
      ctx.moveTo(0, 0);
      ctx.bezierCurveTo(0, -3, -3, -3, -3, 0);
      ctx.bezierCurveTo(-3, 3, 0, 5, 0, 6);
      ctx.bezierCurveTo(0, 5, 3, 3, 3, 0);
      ctx.bezierCurveTo(3, -3, 0, -3, 0, 0);
      ctx.fillStyle = color;
      ctx.shadowColor = color;
      ctx.shadowBlur = 10;
      ctx.fill();
      ctx.restore();
    }

    function animate() {
      ctx.clearRect(0, 0, canvas.width, canvas.height);

      // Adiciona novos corações (chuva)
      if (hearts.length < 150) { // controla a quantidade máxima para performance
        for (let i = 0; i < 3; i++) {
          hearts.push(createHeart());
        }
      }

      hearts.forEach((h, i) => {
        h.y += h.dy;
        drawHeart(h.x, h.y, h.size, h.color);

        if (h.y > canvas.height) {
          hearts.splice(i, 1);
        }
      });

      requestAnimationFrame(animate);
    }

    // Alternar foto P&B e colorida
    const mainImage = document.getElementById('mainImage');
    mainImage.addEventListener('click', () => {
      if (mainImage.src.includes('HVxrX9W2')) {
        mainImage.src = 'https://i.postimg.cc/s11zJ6Sv/foto-colorida.jpg';
      } else {
        mainImage.src = 'https://i.postimg.cc/HVxrX9W2/foto-pb.jpg';
      }
    });

    animate();
  </script>
</body>
</html>
