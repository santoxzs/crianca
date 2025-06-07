# crianca<!DOCTYPE html>
<html lang="pt-BR">
<head>
  <meta charset="UTF-8" />
  <title>Para o amor da minha vida</title>
  <style>
    body {
      margin: 0;
      padding: 0;
      font-family: sans-serif;
      background: #fff;
      overflow-x: hidden;
      text-align: center;
    }

    #envelope-container {
      display: flex;
      flex-direction: column;
      align-items: center;
      justify-content: center;
      height: 100vh;
      cursor: pointer;
    }

    #envelope {
      width: 200px;
      transition: transform 1s ease;
    }

    #clique {
      margin-top: 10px;
      font-size: 1.2rem;
      color: #444;
    }

    .hidden {
      display: none;
    }

    .chuva {
      position: fixed;
      width: 100%;
      height: 100%;
      background-image: url('data:image/png;base64,iVBORw0KGgoAAAANSUhEUgAAADIAAAAyCAYAAAAeP4ixAAAACXBIWXMAAAsSAAALEgHS3X78AAAAvUlEQVRoge3XMQrCQBBF0SXsB1s7kV3cIS20A7ZBTkGoY5OQj/vbcTr/2HnRkBAAAAAADgMe7Ac40pEqZi4rbmZk7d91aCoivchUg5pMXYwTw2ZGPi/0VwrMNtkfEsg9YoILZ1h8VkjYQ3bVSEUTNjNgMVmIUAvybG7AoUlhWzBFJJT1YDa9WymCvhAVZXgCHuBKu0jeWYgNdU+hC0roGgAAAAASUVORK5CYII=');
      background-repeat: repeat;
      animation: coracoes 10s linear infinite;
      opacity: 0.3;
      z-index: -1;
    }

    @keyframes coracoes {
      0% {
        background-position: 0 -100%;
      }
      100% {
        background-position: 0 100%;
      }
    }

    .polaroid {
      background: #fff;
      padding: 15px;
      margin: 40px auto;
      width: 90%;
      max-width: 400px;
      box-shadow: 0 0 20px rgba(0,0,0,0.2);
      border-radius: 10px;
    }

    .polaroid img {
      width: 100%;
      cursor: pointer;
      border-radius: 5px;
      transition: 0.5s;
    }

    .mensagem {
      margin-top: 20px;
      font-size: 1rem;
      color: #333;
    }

    .hint {
      font-size: 0.9rem;
      color: #888;
      margin-bottom: 10px;
    }
  </style>
</head>
<body>
  <div id="envelope-container">
    <img src="https://i.imgur.com/o7D7W1e.png" alt="Envelope" id="envelope">
    <p id="clique">clique</p>
  </div>

  <div id="conteudo" class="hidden">
    <div class="chuva"></div>
    <div class="polaroid">
      <p class="hint">clique na foto e veja a mágica</p>
      <img src="https://i.postimg.cc/HVxrX9W2/foto-pb.jpg" id="foto" alt="Foto do casal" />
      <p class="mensagem">
        você na minha vida é tão especial assim como o impala é especial para o Dean, você chegou na minha vida e a mudou por completo, meus dias passaram a ter mais cor e a minha vida passou a ser mais feliz, não pude comprar um presente mas fiz isso para você. saiba que eu te amo muito meu amor da minha vida 🩷✨️
      </p>
    </div>
  </div>

  <script>
    const envelope = document.getElementById("envelope");
    const conteudo = document.getElementById("conteudo");
    const foto = document.getElementById("foto");

    envelope.addEventListener("click", () => {
      envelope.style.transform = "rotateX(180deg)";
      setTimeout(() => {
        document.getElementById("envelope-container").classList.add("hidden");
        conteudo.classList.remove("hidden");
      }, 1000);
    });

    foto.addEventListener("click", () => {
      foto.src = "https://i.postimg.cc/s11zJ6Sv/foto-colorida.jpg";
    });
  </script>
</body>
</html>
