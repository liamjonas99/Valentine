# Valentine<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>Be My Valentine?</title>

  <script src="https://cdn.jsdelivr.net/npm/canvas-confetti@1.6.0/dist/confetti.browser.min.js"></script>

  <style>
    body {
      margin: 0;
      height: 100vh;
      background: linear-gradient(180deg, #ffd6e8, #ffeef6);
      display: flex;
      justify-content: center;
      align-items: center;
      font-family: -apple-system, BlinkMacSystemFont, "Segoe UI", sans-serif;
    }

    .card {
      background: #ffdce9;
      padding: 40px 30px;
      border-radius: 30px;
      text-align: center;
      width: 90%;
      max-width: 360px;
      position: relative;
      box-shadow: 0 20px 40px rgba(255, 0, 100, 0.25);
      overflow: hidden;
    }

    .hearts {
      font-size: 18px;
      margin-bottom: 15px;
    }

    h1 {
      color: #e6005c;
      font-size: 28px;
      margin-bottom: 30px;
    }

    .yes-btn {
      background: #ff2f7a;
      color: white;
      font-size: 22px;
      padding: 18px 40px;
      border: none;
      border-radius: 40px;
      width: 80%;
      cursor: pointer;
      box-shadow: 0 10px 20px rgba(255, 47, 122, 0.4);
      margin-bottom: 20px;
    }

    .no-btn {
      position: absolute;
      bottom: 40px;
      left: 50%;
      transform: translateX(-50%);
      background: transparent;
      border: 2px solid #ff8fb3;
      color: #ff5c8a;
      padding: 6px 14px;
      border-radius: 20px;
      font-size: 14px;
      cursor: pointer;
    }

    .success {
      font-size: 26px;
      color: #e6005c;
    }
  </style>
</head>
<body>

  <audio id="music" src="https://cdn.pixabay.com/audio/2022/03/15/audio_5c8d4b0c56.mp3"></audio>

  <div class="card" id="card">
    <div class="hearts">💗 💕 💗 💕 💗</div>
    <h1>Cami, will you<br>be my Valentine? 💖</h1>

    <button class="yes-btn" onclick="yesClicked()">Yes 💘</button>
    <button class="no-btn" id="noBtn">No</button>
  </div>

  <script>
    const noBtn = document.getElementById("noBtn");
    const card = document.getElementById("card");

    function moveNo() {
      const maxX = card.clientWidth - noBtn.clientWidth - 20;
      const maxY = card.clientHeight - noBtn.clientHeight - 20;
      noBtn.style.left = Math.random() * maxX + "px";
      noBtn.style.top = Math.random() * maxY + "px";
    }

    noBtn.addEventListener("mouseenter", moveNo);
    noBtn.addEventListener("click", moveNo);
    noBtn.addEventListener("touchstart", moveNo);

    function yesClicked() {
      document.getElementById("music").play();
      confetti({ particleCount: 150, spread: 80, origin: { y: 0.6 } });
      card.innerHTML = `
        <div class="success">
          💖 SHE SAID YES!! 💖<br><br>
          Happy Valentine’s Day 🥰
        </div>
      `;
    }
  </script>

</body>
</html>
