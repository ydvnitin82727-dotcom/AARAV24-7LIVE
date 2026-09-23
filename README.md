<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">

  <title>S1L3NT Music 24×7</title>

  <style>
    * {
      margin: 0;
      padding: 0;
      box-sizing: border-box;
      font-family: Arial, sans-serif;
    }

    body {
      min-height: 100vh;
      background:
        radial-gradient(circle at top, #20202b, #08080c 65%);
      color: white;
      padding: 20px;
    }

    .container {
      width: 100%;
      max-width: 850px;
      margin: auto;
    }

    header {
      text-align: center;
      padding: 25px 10px;
    }

    .logo {
      font-size: 42px;
      font-weight: 900;
      letter-spacing: 4px;
    }

    .tagline {
      color: #aaa;
      margin-top: 8px;
      font-size: 14px;
    }

    .live {
      display: inline-block;
      margin-top: 15px;
      padding: 7px 15px;
      border-radius: 30px;
      background: #251515;
      color: #ff5555;
      font-size: 13px;
    }

    .card {
      background: rgba(25,25,33,.95);
      border: 1px solid #30303a;
      border-radius: 22px;
      padding: 18px;
      box-shadow: 0 20px 70px rgba(0,0,0,.5);
    }

    .video {
      width: 100%;
      aspect-ratio: 16 / 9;
      background: #000;
      border-radius: 16px;
      overflow: hidden;
    }

    iframe {
      width: 100%;
      height: 100%;
      border: 0;
    }

    .now {
      text-align: center;
      padding: 20px 5px;
    }

    .now small {
      display: block;
      color: #999;
      margin-bottom: 7px;
    }

    .now h2 {
      font-size: 20px;
    }

    .controls {
      display: flex;
      justify-content: center;
      gap: 10px;
      flex-wrap: wrap;
      margin-bottom: 20px;
    }

    button {
      border: 0;
      border-radius: 12px;
      padding: 12px 17px;
      background: #292934;
      color: white;
      cursor: pointer;
      font-size: 14px;
      transition: .2s;
    }

    button:hover {
      transform: translateY(-2px);
      background: #3a3a48;
    }

    .main-btn {
      background: white;
      color: black;
      font-weight: bold;
    }

    .add-box {
      display: flex;
      gap: 8px;
      margin-bottom: 20px;
    }

    input {
      width: 100%;
      padding: 14px;
      border: 1px solid #33333d;
      border-radius: 12px;
      background: #111117;
      color: white;
      outline: none;
    }

    input:focus {
      border-color: #777;
    }

    .playlist-title {
      margin-bottom: 10px;
      font-size: 17px;
    }

    .playlist {
      max-height: 330px;
      overflow-y: auto;
    }

    .song {
      display: flex;
      align-items: center;
      justify-content: space-between;
      gap: 10px;
      padding: 13px;
      margin-bottom: 8px;
      border-radius: 12px;
      background: #20202a;
      cursor: pointer;
    }

    .song:hover {
      background: #2a2a36;
    }

    .song.active {
      border: 1px solid #777;
      background: #30303c;
    }

    .song-name {
      overflow: hidden;
      white-space: nowrap;
      text-overflow: ellipsis;
    }

    .delete {
      padding: 7px 10px;
      background: #472323;
    }

    footer {
      text-align: center;
      color: #777;
      padding: 25px 5px;
      font-size: 13px;
    }

    @media (max-width: 600px) {

      body {
        padding: 10px;
      }

      .logo {
        font-size: 32px;
      }

      .card {
        padding: 12px;
      }

      .add-box {
        flex-direction: column;
      }

      button {
        padding: 11px 14px;
      }
    }
  </style>
</head>

<body>

  <div class="container">

    <header>
      <div class="logo">S1L3NT</div>

      <div class="tagline">
        Music • Beats • Vibes — 24×7
      </div>

      <div class="live">
        🔴 LIVE MUSIC
      </div>
    </header>


    <div class="card">

      <!-- YouTube Player -->
      <div class="video">

        <iframe
          id="player"
          src=""
          allow="autoplay; encrypted-media; picture-in-picture"
          allowfullscreen>
        </iframe>

      </div>


      <!-- Current Song -->
      <div class="now">

        <small>NOW PLAYING</small>

        <h2 id="nowPlaying">
          Select a song
        </h2>

      </div>


      <!-- Controls -->
      <div class="controls">

        <button onclick="previousSong()">
          ⏮ Previous
        </button>

        <button
          class="main-btn"
          onclick="nextSong()">
          Next ⏭
        </button>

        <button
          id="shuffleBtn"
          onclick="toggleShuffle()">
          🔀 Shuffle OFF
        </button>

        <button
          id="repeatBtn"
          onclick="toggleRepeat()">
          🔁 Repeat OFF
        </button>

      </div>


      <!-- Add YouTube Song -->
      <div class="add-box">

        <input
          id="youtubeUrl"
          type="text"
          placeholder="Paste YouTube song URL here...">

        <button onclick="addSong()">
          ➕ Add Song
        </button>

      </div>


      <div class="playlist-title">
        🎵 Playlist
      </div>

      <div
        class="playlist"
        id="playlist">
      </div>

    </div>


    <footer>
      © 2026 S1L3NT Music 24×7
    </footer>

  </div>


<script>

  /*
  ========================================
       S1L3NT MUSIC 24×7
       YouTube Music Player
  ========================================
  */


  let songs = [

    {
      id: "dQw4w9WgXcQ",
      name: "Sample Song"
    }

  ];


  let currentIndex = 0;

  let shuffle = false;

  let repeat = false;


  const player =
    document.getElementById("player");

  const nowPlaying =
    document.getElementById("nowPlaying");

  const playlist =
    document.getElementById("playlist");


  // Get YouTube Video ID
  function getYouTubeId(url) {

    try {

      const parsed = new URL(url);

      if (
        parsed.hostname.includes("youtu.be")
      ) {

        return parsed.pathname.substring(1);

      }

      if (
        parsed.hostname.includes("youtube.com")
      ) {

        return parsed.searchParams.get("v");

      }

    } catch (error) {

      return null;

    }

    return null;

  }


  // Load Song
  function loadSong(index) {

    if (!songs.length) return;

    currentIndex = index;

    const song = songs[currentIndex];

    player.src =
      "https://www.youtube.com/embed/" +
      song.id +
      "?autoplay=1&rel=0";

    nowPlaying.textContent =
      song.name;

    renderPlaylist();

  }


  // Next Song
  function nextSong() {

    if (!songs.length) return;


    if (repeat) {

      loadSong(currentIndex);

      return;

    }


    if (
      shuffle &&
      songs.length > 1
    ) {

      let next;

      do {

        next =
          Math.floor(
            Math.random() *
            songs.length
          );

      } while (
        next === currentIndex
      );


      loadSong(next);

    }

    else {

      currentIndex++;

      if (
        currentIndex >=
        songs.length
      ) {

        currentIndex = 0;

      }

      loadSong(currentIndex);

    }

  }


  // Previous Song
  function previousSong() {

    if (!songs.length) return;

    currentIndex--;

    if (currentIndex < 0) {

      currentIndex =
        songs.length - 1;

    }

    loadSong(currentIndex);

  }


  // Shuffle
  function toggleShuffle() {

    shuffle = !shuffle;

    document.getElementById(
      "shuffleBtn"
    ).textContent =
      shuffle
        ? "🔀 Shuffle ON"
        : "🔀 Shuffle OFF";

  }


  // Repeat
  function toggleRepeat() {

    repeat = !repeat;

    document.getElementById(
      "repeatBtn"
    ).textContent =
      repeat
        ? "🔁 Repeat ON"
        : "🔁 Repeat OFF";

  }


  // Add Song
  function addSong() {

    const input =
      document.getElementById(
        "youtubeUrl"
      );

    const url =
      input.value.trim();


    const id =
      getYouTubeId(url);


    if (!id) {

      alert(
        "Please enter a valid YouTube URL."
      );

      return;

    }


    songs.push({

      id: id,

      name:
        "YouTube Song " +
        songs.length

    });


    input.value = "";

    renderPlaylist();


    if (songs.length === 1) {

      loadSong(0);

    }

  }


  // Delete Song
  function deleteSong(index) {

    songs.splice(index, 1);


    if (!songs.length) {

      player.src = "";

      nowPlaying.textContent =
        "Select a song";

      renderPlaylist();

      return;

    }


    if (
      currentIndex >=
      songs.length
    ) {

      currentIndex = 0;

    }


    loadSong(currentIndex);

  }


  // Playlist UI
  function renderPlaylist() {

    playlist.innerHTML = "";


    songs.forEach(
      (song, index) => {

        const div =
          document.createElement(
            "div"
          );


        div.className =
          "song " +
          (
            index === currentIndex
              ? "active"
              : ""
          );


        div.innerHTML = `

          <div class="song-name">
            ${index + 1}. ${song.name}
          </div>

          <button
            class="delete"
            onclick="
              event.stopPropagation();
              deleteSong(${index})
            ">
            🗑
          </button>

        `;


        div.onclick = () =>
          loadSong(index);


        playlist.appendChild(div);

      }
    );

  }


  // Start
  renderPlaylist();

  loadSong(0);


</script>

</body>
</html>
