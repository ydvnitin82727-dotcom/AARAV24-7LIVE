<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">

  <title>aarav24*7 steam</title>

  <style>
    * {
      margin: 0;
      padding: 0;
      box-sizing: border-box;
      font-family: Arial, sans-serif;
    }

    body {
      background: #0b0b0b;
      color: white;
    }

    header {
      background: #151515;
      padding: 18px;
      text-align: center;
      border-bottom: 2px solid #ff1744;
    }

    header h1 {
      font-size: 28px;
      color: #ff1744;
    }

    header p {
      margin-top: 5px;
      color: #aaa;
    }

    .player-box {
      width: 95%;
      max-width: 900px;
      margin: 30px auto;
      background: #151515;
      padding: 20px;
      border-radius: 15px;
      box-shadow: 0 0 25px rgba(255, 23, 68, 0.25);
    }

    .live {
      display: inline-block;
      background: red;
      padding: 7px 14px;
      border-radius: 20px;
      font-weight: bold;
      margin-bottom: 15px;
    }

    video {
      width: 100%;
      height: 400px;
      background: black;
      border-radius: 10px;
    }

    .buttons {
      display: flex;
      gap: 10px;
      margin-top: 18px;
      flex-wrap: wrap;
    }

    button {
      border: none;
      padding: 12px 18px;
      border-radius: 8px;
      background: #ff1744;
      color: white;
      font-size: 15px;
      cursor: pointer;
    }

    button:hover {
      background: #d50032;
    }

    .info {
      width: 95%;
      max-width: 900px;
      margin: 20px auto;
      background: #151515;
      padding: 20px;
      border-radius: 15px;
    }

    .info h2 {
      margin-bottom: 10px;
    }

    footer {
      text-align: center;
      padding: 25px;
      color: #888;
    }

    @media (max-width: 600px) {
      video {
        height: 220px;
      }

      header h1 {
        font-size: 22px;
      }
    }
  </style>
</head>

<body>

  <header>
    <h1>🎵 aarav24*7 steam</h1>
    <p>24/7 Music Live Stream</p>
  </header>

  <main>

    <section class="player-box">

      <span class="live">🔴 LIVE</span>

      <video id="player" controls autoplay>
        <!--
          YAHAN APNI LEGAL STREAM/VIDEO FILE KA URL LAGAO

          Example:
          <source src="https://example.com/live.mp4" type="video/mp4">
        -->
        Your browser does not support video playback.
      </video>

      <div class="buttons">
        <button onclick="playStream()">▶ Play</button>
        <button onclick="pauseStream()">⏸ Pause</button>
        <button onclick="muteStream()">🔇 Mute</button>
        <button onclick="unmuteStream()">🔊 Unmute</button>
        <button onclick="fullscreen()">⛶ Fullscreen</button>
      </div>

    </section>

    <section class="info">
      <h2>🎶 aarav24*7 steam</h2>
      <p>
        Welcome to aarav24*7 steam.
        Enjoy our continuous music stream.
      </p>
    </section>

  </main>

  <footer>
    © 2026 aarav24*7 steam
  </footer>

  <script>
    const player = document.getElementById("player");

    function playStream() {
      player.play();
    }

    function pauseStream() {
      player.pause();
    }

    function muteStream() {
      player.muted = true;
    }

    function unmuteStream() {
      player.muted = false;
    }

    function fullscreen() {
      if (player.requestFullscreen) {
        player.requestFullscreen();
      } else if (player.webkitRequestFullscreen) {
        player.webkitRequestFullscreen();
      }
    }
  </script>

</body>
</html>
