# wildfire<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8" />
  <meta name="viewport" content="width=device-width, initial-scale=1.0" />
  <title>Wildfire Game Store</title>
  <style>
    * {
      box-sizing: border-box;
      margin: 0;
      padding: 0;
      font-family: Arial, Helvetica, sans-serif;
    }

    body {
      background-color: #0b0c10;
      color: #c5c6c7;
    }

    a {
      color: inherit;
      text-decoration: none;
    }

    header {
      background: #1f2833;
      padding: 10px 20px;
      display: flex;
      align-items: center;
      justify-content: space-between;
      position: sticky;
      top: 0;
      z-index: 10;
    }

    .logo {
      display: flex;
      align-items: center;
      gap: 8px;
    }

    .logo-icon {
      width: 28px;
      height: 28px;
      border-radius: 4px;
      background: linear-gradient(135deg, #66fcf1, #45a29e);
    }

    .logo-text {
      font-size: 1.2rem;
      font-weight: bold;
      color: #66fcf1;
    }

    nav {
      display: flex;
      gap: 15px;
      font-size: 0.95rem;
    }

    nav a {
      opacity: 0.8;
    }

    nav a:hover {
      opacity: 1;
    }

    .search-bar {
      display: flex;
      align-items: center;
      gap: 8px;
      background: #0b0c10;
      padding: 6px 10px;
      border-radius: 4px;
    }

    .search-bar input {
      border: none;
      background: transparent;
      color: #c5c6c7;
      outline: none;
      min-width: 160px;
    }

    .search-icon {
      width: 16px;
      height: 16px;
      border-radius: 50%;
      border: 2px solid #c5c6c7;
      position: relative;
    }

    .search-icon::after {
      content: "";
      position: absolute;
      width: 8px;
      height: 2px;
      background: #c5c6c7;
      transform: rotate(45deg);
      right: -5px;
      bottom: -2px;
    }

    main {
      max-width: 1200px;
      margin: 20px auto;
      padding: 0 16px 40px;
    }

    .hero {
      background: linear-gradient(120deg, #1f2833, #0b0c10);
      padding: 18px 20px;
      border-radius: 8px;
      display: flex;
      flex-wrap: wrap;
      align-items: center;
      gap: 16px;
      margin-bottom: 26px;
    }

    .hero-text {
      flex: 1 1 260px;
    }

    .hero-title {
      font-size: 1.8rem;
      color: #66fcf1;
      margin-bottom: 8px;
    }

    .hero-subtitle {
      font-size: 0.95rem;
      max-width: 480px;
      line-height: 1.4;
    }

    .hero-button {
      margin-top: 12px;
      display: inline-block;
      padding: 8px 18px;
      background: #45a29e;
      color: #0b0c10;
      border-radius: 4px;
      font-weight: bold;
      font-size: 0.9rem;
    }

    .hero-button:hover {
      background: #66fcf1;
    }

    .hero-badge {
      padding: 6px 10px;
      border-radius: 4px;
      background: rgba(102, 252, 241, 0.1);
      border: 1px solid rgba(102, 252, 241, 0.4);
      font-size: 0.8rem;
      color: #66fcf1;
      margin-bottom: 8px;
      display: inline-block;
    }

    .hero-image {
      flex: 0 1 280px;
      height: 160px;
      border-radius: 8px;
      background: radial-gradient(circle at top, #66fcf1 0, #1f2833 40%, #0b0c10 80%);
      position: relative;
      overflow: hidden;
    }

    .hero-image::before,
    .hero-image::after {
      content: "";
      position: absolute;
      border-radius: 50%;
      border: 1px solid rgba(102, 252, 241, 0.3);
    }

    .hero-image::before {
      width: 120px;
      height: 120px;
      top: 10px;
      left: 18px;
    }

    .hero-image::after {
      width: 80px;
      height: 80px;
      bottom: 10px;
      right: 26px;
    }

    .section-header {
      display: flex;
      justify-content: space-between;
      align-items: center;
      margin-bottom: 12px;
    }

    .section-title {
      font-size: 1.2rem;
      color: #c5c6c7;
    }

    .section-subtitle {
      font-size: 0.8rem;
      opacity: 0.7;
    }

    .filters {
      display: flex;
      gap: 8px;
      margin-bottom: 16px;
      flex-wrap: wrap;
    }

    .filter-btn {
      border: none;
      padding: 6px 10px;
      border-radius: 999px;
      background: #1f2833;
      color: #c5c6c7;
      font-size: 0.8rem;
      cursor: pointer;
      opacity: 0.8;
    }

    .filter-btn.active,
    .filter-btn:hover {
      opacity: 1;
      background: #45a29e;
      color: #0b0c10;
    }

    .game-grid {
      display: grid;
      grid-template-columns: repeat(auto-fit, minmax(220px, 1fr));
      gap: 16px;
    }

    .game-card {
      background: #1f2833;
      border-radius: 6px;
      overflow: hidden;
      display: flex;
      flex-direction: column;
      min-height: 260px;
      transition: transform 0.15s ease, box-shadow 0.15s ease;
      cursor: pointer;
    }

    .game-card:hover {
      transform: translateY(-3px);
      box-shadow: 0 8px 16px rgba(0, 0, 0, 0.6);
    }

    .game-cover {
      height: 120px;
      background-size: cover;
      background-position: center;
      background-repeat: no-repeat;
    }

    .game-content {
      padding: 10px 12px 12px;
      display: flex;
      flex-direction: column;
      gap: 6px;
      flex: 1;
    }

    .game-title-row {
      display: flex;
      justify-content: space-between;
      align-items: center;
      gap: 8px;
    }

    .game-title {
      font-size: 0.98rem;
      font-weight: bold;
      color: #e5e5e5;
    }

    .game-price {
      font-size: 0.85rem;
      font-weight: bold;
      color: #66fcf1;
      white-space: nowrap;
    }

    .game-meta {
      display: flex;
      justify-content: space-between;
      align-items: center;
      font-size: 0.75rem;
      opacity: 0.8;
    }

    .tags {
      display: flex;
      flex-wrap: wrap;
      gap: 4px;
      margin-top: 4px;
    }

    .tag {
      font-size: 0.7rem;
      padding: 2px 6px;
      border-radius: 999px;
      background: #0b0c10;
      opacity: 0.85;
    }

    .game-description {
      margin-top: 4px;
      font-size: 0.78rem;
      line-height: 1.3;
      opacity: 0.86;
      flex: 1;
    }

    .game-footer {
      display: flex;
      justify-content: space-between;
      align-items: center;
      margin-top: 8px;
      font-size: 0.75rem;
      opacity: 0.9;
    }

    .add-btn {
      border: none;
      padding: 4px 10px;
      border-radius: 999px;
      background: #45a29e;
      color: #0b0c10;
      font-size: 0.72rem;
      font-weight: bold;
      cursor: pointer;
    }

    .add-btn:hover {
      background: #66fcf1;
    }

    .pill {
      padding: 2px 6px;
      border-radius: 999px;
      background: #0b0c10;
      font-size: 0.72rem;
    }

    footer {
      max-width: 1200px;
      margin: 0 auto 20px;
      padding: 0 16px;
      font-size: 0.75rem;
      opacity: 0.7;
      display: flex;
      justify-content: space-between;
      flex-wrap: wrap;
      gap: 8px;
    }

    @media (max-width: 600px) {
      header {
        flex-wrap: wrap;
        gap: 8px;
      }
      nav {
        display: none;
      }
      .hero {
        padding: 14px;
      }
      .hero-title {
        font-size: 1.4rem;
      }
      .hero-image {
        flex: 1 1 100%;
      }
    }
  </style>
</head>
<body>
  <header>
    <div class="logo">
      <div class="logo-icon"></div>
      <div class="logo-text">Wildfire</div>
    </div>

    <nav>
      <a href="#">Store</a>
      <a href="#">Library</a>
      <a href="#">Community</a>
      <a href="#">Support</a>
    </nav>

    <div class="search-bar">
      <div class="search-icon"></div>
      <input
        type="text"
        id="searchInput"
        placeholder="Search games..."
        aria-label="Search games"
      />
    </div>
  </header>

  <main>
    <section class="hero">
      <div class="hero-text">
        <span class="hero-badge">Featured on Wildfire</span>
        <h1 class="hero-title">Discover the most popular PC games</h1>
        <p class="hero-subtitle">
          Browse a curated selection of top‑rated and trending PC titles. Filter by
          genre, search by name, and build your dream library — all in one clean,
          Steam‑inspired interface.
        </p>
        <a href="#games" class="hero-button">Browse popular games</a>
      </div>
      <div class="hero-image" aria-hidden="true"></div>
    </section>

    <section id="games">
      <div class="section-header">
        <div>
          <h2 class="section-title">Popular on Wildfire</h2>
          <div class="section-subtitle">Showing cross‑platform PC hits, including Overgrowth</div>
        </div>
        <div class="section-subtitle" id="resultsInfo"></div>
      </div>

      <div class="filters">
        <button class="filter-btn active" data-genre="all">All</button>
        <button class="filter-btn" data-genre="action">Action</button>
        <button class="filter-btn" data-genre="adventure">Adventure</button>
        <button class="filter-btn" data-genre="rpg">RPG</button>
        <button class="filter-btn" data-genre="shooter">Shooter</button>
        <button class="filter-btn" data-genre="indie">Indie</button>
        <button class="filter-btn" data-genre="strategy">Strategy</button>
      </div>

      <div class="game-grid" id="gameGrid"></div>
    </section>
  </main>

  <footer>
    <div>Wildfire &copy; 2026 — A demo game store UI inspired by Steam.</div>
    <div>All game names & assets belong to their respective owners.</div>
  </footer>

  <script>
    // Static game data (example). Includes Overgrowth.
    const games = [
      {
        title: "Overgrowth",
        id: "overgrowth",
        genres: ["action", "indie"],
        tags: ["Parkour", "Martial Arts", "Physics"],
        price: "$29.99",
        rating: 83,
        reviews: "Very Positive",
        platforms: ["Windows", "Linux"],
        description:
          "A third‑person action game featuring fast, physics‑based parkour and brutal hand‑to‑hand combat.",
        cover: "https://images.igdb.com/igdb/image/upload/t_screenshot_huge/sc9nql.jpg", // placeholder image URL
      },
      {
        title: "Counter‑Strike 2",
        id: "cs2",
        genres: ["shooter", "action"],
        tags: ["Competitive", "Multiplayer", "Tactical"],
        price: "Free to Play",
        rating: 89,
        reviews: "Mostly Positive",
        platforms: ["Windows"],
        description:
          "Valve's tactical FPS, evolving the classic Counter‑Strike formula with modern tech and updated maps.",
        cover: "https://images.igdb.com/igdb/image/upload/t_screenshot_huge/scg8yx.jpg",
      },
      {
        title: "Elden Ring",
        id: "elden-ring",
        genres: ["rpg", "action"],
        tags: ["Open World", "Souls‑like", "Fantasy"],
        price: "$59.99",
        rating: 94,
        reviews: "Overwhelmingly Positive",
        platforms: ["Windows"],
        description:
          "Explore a massive, dark fantasy world filled with challenging bosses and deep RPG systems.",
        cover: "https://images.igdb.com/igdb/image/upload/t_screenshot_huge/scg6wq.jpg",
      },
      {
        title: "Hades",
        id: "hades",
        genres: ["action", "indie", "rpg"],
        tags: ["Roguelike", "Isometric", "Story Rich"],
        price: "$24.99",
        rating: 93,
        reviews: "Overwhelmingly Positive",
        platforms: ["Windows", "macOS"],
        description:
          "Battle out of the Underworld in this fast‑paced rogue‑like dungeon crawler with a strong narrative.",
        cover: "https://images.igdb.com/igdb/image/upload/t_screenshot_huge/scf3t3.jpg",
      },
      {
        title: "Baldur's Gate 3",
        id: "bg3",
        genres: ["rpg", "adventure"],
        tags: ["Party‑Based", "Turn‑Based", "D&D"],
        price: "$59.99",
        rating: 96,
        reviews: "Overwhelmingly Positive",
        platforms: ["Windows", "macOS"],
        description:
          "A cinematic story‑driven RPG set in the Dungeons & Dragons universe with deep choices and consequences.",
        cover: "https://images.igdb.com/igdb/image/upload/t_screenshot_huge/scg0h4.jpg",
      },
      {
        title: "Stardew Valley",
        id: "stardew-valley",
        genres: ["indie", "rpg"],
        tags: ["Farming", "Relaxing", "Pixel Graphics"],
        price: "$14.99",
        rating: 91,
        reviews: "Overwhelmingly Positive",
        platforms: ["Windows", "macOS", "Linux"],
        description:
          "Build the farm of your dreams, befriend villagers, and explore caves in this beloved indie classic.",
        cover: "https://images.igdb.com/igdb/image/upload/t_screenshot_huge/sc6d9r.jpg",
      },
      {
        title: "Apex Legends",
        id: "apex-legends",
        genres: ["shooter", "action"],
        tags: ["Battle Royale", "Team‑Based", "Hero Shooter"],
        price: "Free to Play",
        rating: 88,
        reviews: "Very Positive",
        platforms: ["Windows"],
        description:
          "A hero‑based battle royale with fast movement, tight gunplay, and squad‑focused tactics.",
        cover: "https://images.igdb.com/igdb/image/upload/t_screenshot_huge/sc6m0z.jpg",
      },
      {
        title: "Terraria",
        id: "terraria",
        genres: ["indie", "adventure"],
        tags: ["Sandbox", "Crafting", "2D"],
        price: "$9.99",
        rating: 90,
        reviews: "Overwhelmingly Positive",
        platforms: ["Windows", "macOS", "Linux"],
        description:
          "Dig, fight, build, and explore a vibrant 2D sandbox filled with bosses, loot, and secrets.",
        cover: "https://images.igdb.com/igdb/image/upload/t_screenshot_huge/sc6d6t.jpg",
      },
    ];

    const gameGrid = document.getElementById("gameGrid");
    const resultsInfo = document.getElementById("resultsInfo");
    const searchInput = document.getElementById("searchInput");
    const filterButtons = document.querySelectorAll(".filter-btn");

    let activeGenre = "all";
    let searchQuery = "";

    function createGameCard(game) {
      const card = document.createElement("article");
      card.className = "game-card";

      const cover = document.createElement("div");
      cover.className = "game-cover";
      cover.style.backgroundImage = `url(${game.cover})`;
      card.appendChild(cover);

      const content = document.createElement("div");
      content.className = "game-content";

      const titleRow = document.createElement("div");
      titleRow.className = "game-title-row";

      const title = document.createElement("h3");
      title.className = "game-title";
      title.textContent = game.title;

      const price = document.createElement("div");
      price.className = "game-price";
      price.textContent = game.price;

      titleRow.appendChild(title);
      titleRow.appendChild(price);

      const meta = document.createElement("div");
      meta.className = "game-meta";
      meta.innerHTML = `<span>${game.genres.join(", ")}</span><span>Score: ${
        game.rating
      }/100</span>`;

      const tags = document.createElement("div");
      tags.className = "tags";
      game.tags.forEach((t) => {
        const tag = document.createElement("span");
        tag.className = "tag";
        tag.textContent = t;
        tags.appendChild(tag);
      });

      const description = document.createElement("p");
      description.className = "game-description";
      description.textContent = game.description;

      const footer = document.createElement("div");
      footer.className = "game-footer";

      const left = document.createElement("div");
      left.innerHTML = `<span class="pill">${game.reviews}</span>`;

      const right = document.createElement("button");
      right.className = "add-btn";
      right.textContent = "Add to Library";
      right.addEventListener("click", (e) => {
        e.stopPropagation();
        alert(`'${game.title}' added to your (fake) Wildfire library!`);
      });

      footer.appendChild(left);
      footer.appendChild(right);

      content.appendChild(titleRow);
      content.appendChild(meta);
      content.appendChild(tags);
      content.appendChild(description);
      content.appendChild(footer);

      card.appendChild(content);

      card.addEventListener("click", () => {
        alert(
          `${game.title} is a popular game on Wildfire. In a real store, this would open the game's details page or Steam page.`
        );
      });

      return card;
    }

    function applyFilters() {
      const normalizedQuery = searchQuery.trim().toLowerCase();
      let filtered = games.filter((g) => {
        const matchesGenre =
          activeGenre === "all" || g.genres.includes(activeGenre);
        const matchesSearch =
          !normalizedQuery ||
          g.title.toLowerCase().includes(normalizedQuery) ||
          g.tags.join(" ").toLowerCase().includes(normalizedQuery);
        return matchesGenre && matchesSearch;
      });

      renderGames(filtered);
    }

    function renderGames(list) {
      gameGrid.innerHTML = "";
      if (list.length === 0) {
        gameGrid.innerHTML =
          '<div style="opacity:0.8;font-size:0.9rem;">No games found. Try a different search or genre.</div>';
      } else {
        list.forEach((game) => {
          const card = createGameCard(game);
          gameGrid.appendChild(card);
        });
      }

      resultsInfo.textContent = `${list.length} game${
        list.length === 1 ? "" : "s"
      } shown`;
    }

    filterButtons.forEach((btn) => {
      btn.addEventListener("click", () => {
        filterButtons.forEach((b) => b.classList.remove("active"));
        btn.classList.add("active");
        activeGenre = btn.dataset.genre;
        applyFilters();
      });
    });

    searchInput.addEventListener("input", (e) => {
      searchQuery = e.target.value;
      applyFilters();
    });

    // Initial render
    renderGames(games);
  </script>
</body>
</html>
