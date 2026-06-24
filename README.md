<!DOCTYPE html>
<html lang="pt-BR">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>Unblock Games - Jogue Agora</title>
  <style>
    * { margin: 0; padding: 0; box-sizing: border-box; }
    body {
      font-family: 'Segoe UI', sans-serif;
      background: linear-gradient(135deg, #0f0c29, #302b63, #24243e);
      color: white;
      min-height: 100vh;
    }
    header {
      background: rgba(0,0,0,0.8);
      padding: 1rem 0;
      position: sticky;
      top: 0;
      z-index: 100;
      border-bottom: 2px solid #00ff88;
    }
    .nav {
      max-width: 1200px;
      margin: 0 auto;
      display: flex;
      justify-content: space-between;
      align-items: center;
      padding: 0 20px;
    }
    .logo {
      font-size: 2rem;
      font-weight: bold;
      color: #00ff88;
      text-shadow: 0 0 10px #00ff88;
    }
    .search {
      padding: 12px 20px;
      width: 350px;
      border-radius: 50px;
      border: none;
      background: #1a1a2e;
      color: white;
      font-size: 1rem;
    }
    .hero {
      text-align: center;
      padding: 80px 20px;
      background: url('https://images.unsplash.com/photo-1616588587683-0e5e0c7f0e0e?ixlib=rb-4.0.3') center/cover;
      background-attachment: fixed;
    }
    .hero h1 {
      font-size: 3.5rem;
      margin-bottom: 20px;
      text-shadow: 0 0 20px #00ff88;
    }
    .container {
      max-width: 1200px;
      margin: 0 auto;
      padding: 20px;
    }
    .section-title {
      font-size: 2rem;
      margin: 40px 0 20px;
      border-left: 5px solid #00ff88;
      padding-left: 15px;
    }
    .games-grid {
      display: grid;
      grid-template-columns: repeat(auto-fill, minmax(220px, 1fr));
      gap: 20px;
    }
    .game-card {
      background: #1a1a2e;
      border-radius: 15px;
      overflow: hidden;
      transition: all 0.3s;
      cursor: pointer;
    }
    .game-card:hover {
      transform: translateY(-10px);
      box-shadow: 0 0 30px rgba(0, 255, 136, 0.5);
    }
    .game-card img {
      width: 100%;
      height: 160px;
      object-fit: cover;
    }
    .game-info {
      padding: 15px;
      text-align: center;
    }
    .game-info h3 {
      margin-bottom: 8px;
      color: #00ff88;
    }
    .play-btn {
      background: #00ff88;
      color: black;
      border: none;
      padding: 8px 20px;
      border-radius: 50px;
      font-weight: bold;
      margin-top: 10px;
      cursor: pointer;
    }
    footer {
      text-align: center;
      padding: 30px;
      background: rgba(0,0,0,0.7);
      margin-top: 50px;
    }
  </style>
</head>
<body>

  <header>
    <div class="nav">
      <div class="logo">UNBLOCK GAMES</div>
      <input type="text" class="search" placeholder="Buscar jogos... (ex: slope, minecraft)" onkeyup="searchGames()">
    </div>
  </header>

  <div class="hero">
    <h1>Jogue Qualquer Coisa</h1>
    <p style="font-size:1.3rem;">Sem bloqueios • Sem downloads • 100% Grátis</p>
  </div>

  <div class="container">

    <h2 class="section-title">🎮 Destaques</h2>
    <div class="games-grid" id="gamesGrid">
      <!-- Jogos serão inseridos aqui via JavaScript -->
    </div>

  </div>

  <footer>
    <p>Unblock Games © 2026 - Feito para você jogar em qualquer lugar</p>
  </footer>

  <script>
    const games = [
      {
        name: "Slope",
        img: "https://images.unsplash.com/photo-1611996575749-79a3ae4d3f9a",
        url: "https://slope-game.github.io/"
      },
      {
        name: "2048",
        img: "https://source.unsplash.com/random/300x200/?number",
        url: "https://play2048.co/"
      },
      {
        name: "Tetris",
        img: "https://source.unsplash.com/random/300x200/?tetris",
        url: "https://tetris.com/play-tetris"
      },
      {
        name: "Subway Surfers",
        img: "https://source.unsplash.com/random/300x200/?runner",
        url: "https://subway-surfers.github.io/"
      },
      {
        name: "Snake",
        img: "https://source.unsplash.com/random/300x200/?snake",
        url: "#snake"
      },
      {
        name: "Flappy Bird",
        img: "https://source.unsplash.com/random/300x200/?bird",
        url: "https://flappybird.io/"
      },
      {
        name: "Minecraft Classic",
        img: "https://source.unsplash.com/random/300x200/?minecraft",
        url: "https://classic.minecraft.net/"
      },
      {
        name: "Cookie Clicker",
        img: "https://source.unsplash.com/random/300x200/?cookie",
        url: "https://orteil.dashnet.org/cookieclicker/"
      }
    ];

    function renderGames(filteredGames = games) {
      const grid = document.getElementById('gamesGrid');
      grid.innerHTML = '';

      filteredGames.forEach(game => {
        const card = document.createElement('div');
        card.className = 'game-card';
        card.innerHTML = `
          <img src="${game.img}" alt="${game.name}">
          <div class="game-info">
            <h3>${game.name}</h3>
            <button class="play-btn" onclick="playGame('${game.url}')">JOGAR AGORA</button>
          </div>
        `;
        grid.appendChild(card);
      });
    }

    function playGame(url) {
      if (url === "#snake") {
        alert("🐍 Jogo Snake em breve! Enquanto isso, experimente os outros jogos.");
      } else {
        window.open(url, '_blank');
      }
    }

    function searchGames() {
      const term = document.querySelector('.search').value.toLowerCase();
      const filtered = games.filter(game => 
        game.name.toLowerCase().includes(term)
      );
      renderGames(filtered);
    }

    // Inicializa
    renderGames();
  </script>

</body>
</html>
