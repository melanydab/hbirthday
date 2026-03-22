<!DOCTYPE html>
<html lang="es">
<head>
  <meta charset="UTF-8">
  <title>Feliz Cumple</title>

  <style>
    body {
      margin: 0;
      height: 100vh;
      background: #ffd6e7;
      font-family: Arial, sans-serif;
      overflow: hidden;
    }

    /* ===== PRIMERA PANTALLA ===== */
    .pantalla1 {
      position: absolute;
      width: 100%;
      height: 100%;
      display: flex;
      justify-content: center;
      align-items: center;
    }

    .contenedor {
      position: relative;
      width: 1000px;
      height: 1000px;
      top: 40px;
    }

    .texto {
      position: absolute;
      top: 55%;
      left: 50%;
      transform: translate(-50%, -50%);
      text-align: center;
      color: #333;
      font-size: 32px;
      font-weight: bold;
      width: 400px;
    }

    .corazon {
      color: red;
    }

    img {
      position: absolute;
      width: 240px;
      height: 240px;
      object-fit: cover;
      border-radius: 30px;
      box-shadow: 0 0 25px rgba(0,0,0,0.3);
    }

    /* HEXÁGONO */
    .img1 { top: 40px; left: 50%; transform: translateX(-50%); }
    .img2 { top: 25%; left: 5%; }
    .img3 { top: 25%; right: 5%; }
    .img4 { bottom: 25%; left: 5%; }
    .img5 { bottom: 25%; right: 5%; }

    /* ===== SEGUNDA PANTALLA ===== */
    .pantalla2 {
      position: absolute;
      width: 100%;
      height: 100%;
      display: none;
      justify-content: center;
      align-items: center;
      background: #ffd6e7;
    }

    video {
      width: 100vw;
      height: 100vh;
      object-fit: contain;
      z-index: 2;
    }

    /* ===== CORAZONES ===== */
    .heart {
      position: absolute;
      bottom: -50px;
      font-size: 18px;
      color: #ff4d88;
      animation: subir linear infinite;
      opacity: 0.7;
      pointer-events: none;
    }

    @keyframes subir {
      0% {
        transform: translateY(0) scale(1);
        opacity: 0.7;
      }
      100% {
        transform: translateY(-110vh) scale(1.5);
        opacity: 0;
      }
    }
  </style>
</head>

<body>

<!-- 🎵 Música -->
<audio id="musica" loop>
  <source src="20.mp3" type="audio/mpeg">
</audio>

<!-- 💗 PRIMERA PANTALLA -->
<div class="pantalla1" id="p1">
  <div class="contenedor">
    <div class="texto">
      Feliz cumple, te amo cada dia <span class="corazon">♥</span>
    </div>

    <img src="2.jpg" class="img1">
    <img src="3.jpg" class="img2">
    <img src="4.jpg" class="img3">
    <img src="5.jpg" class="img4">
    <img src="6.jpg" class="img5">
  </div>
</div>

<!-- 🎬 SEGUNDA PANTALLA -->
<div class="pantalla2" id="p2">
  <video id="video" src="1.mp4" controls></video>
</div>

<script>
  const audio = document.getElementById("musica");
  const p1 = document.getElementById("p1");
  const p2 = document.getElementById("p2");
  const video = document.getElementById("video");

  let clicks = 0;

  document.body.addEventListener("click", () => {
    clicks++;

    if (clicks === 1) {
      audio.play();
    } else if (clicks === 2) {
      // 🔇 detener música
      audio.pause();
      audio.currentTime = 0;

      // cambiar pantalla
      p1.style.display = "none";
      p2.style.display = "flex";

      // reproducir video
      video.play();
    }
  });

  // 💗 corazones
  for (let i = 0; i < 80; i++) {
    let heart = document.createElement("div");
    heart.className = "heart";
    heart.innerHTML = "♥";

    heart.style.left = Math.random() * 100 + "vw";
    heart.style.fontSize = (15 + Math.random() * 30) + "px";
    heart.style.animationDuration = (4 + Math.random() * 4) + "s";
    heart.style.animationDelay = Math.random() * 5 + "s";

    document.body.appendChild(heart);
  }
</script>

</body>
</html>
