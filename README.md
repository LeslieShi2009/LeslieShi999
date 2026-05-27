<!DOCTYPE html>
<html lang="en">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>Leslie Shi — Producer & Music Obsessive</title>
<link rel="preconnect" href="https://fonts.googleapis.com">
<link href="https://fonts.googleapis.com/css2?family=Playfair+Display:ital,wght@0,400;0,700;1,400&family=DM+Mono:wght@300;400&family=DM+Sans:wght@300;400;500&display=swap" rel="stylesheet">
<style>
  :root {
    --cream: #F5F0E8;
    --ink: #1A1510;
    --warm-mid: #8C7B68;
    --accent: #C4572A;
    --accent-light: #E8D5C0;
    --tape: #D4A843;
  }
  * { margin: 0; padding: 0; box-sizing: border-box; }

  body {
    background: var(--ink);
    color: var(--cream);
    font-family: 'DM Sans', sans-serif;
    font-weight: 300;
    overflow-x: hidden;
  }

  /* GRAIN OVERLAY */
  body::before {
    content: '';
    position: fixed;
    inset: 0;
    pointer-events: none;
    z-index: 100;
    opacity: 0.04;
    background-image: url("data:image/svg+xml,%3Csvg viewBox='0 0 256 256' xmlns='http://www.w3.org/2000/svg'%3E%3Cfilter id='noise'%3E%3CfeTurbulence type='fractalNoise' baseFrequency='0.9' numOctaves='4' stitchTiles='stitch'/%3E%3C/filter%3E%3Crect width='100%25' height='100%25' filter='url(%23noise)'/%3E%3C/svg%3E");
    background-repeat: repeat;
    background-size: 256px 256px;
  }

  /* HEADER */
  header {
    min-height: 100vh;
    display: grid;
    grid-template-rows: auto 1fr auto;
    padding: 3rem 4rem;
    position: relative;
    overflow: hidden;
  }

  .header-tape {
    position: absolute;
    top: 0; left: 0; right: 0;
    height: 6px;
    background: repeating-linear-gradient(90deg,
      var(--tape) 0px, var(--tape) 40px,
      var(--ink) 40px, var(--ink) 44px);
  }

  .nav {
    display: flex;
    justify-content: space-between;
    align-items: center;
    font-family: 'DM Mono', monospace;
    font-size: 0.75rem;
    letter-spacing: 0.12em;
    text-transform: uppercase;
    color: var(--warm-mid);
  }
  .nav-links { display: flex; gap: 2.5rem; list-style: none; }
  .nav-links a { color: var(--warm-mid); text-decoration: none; transition: color 0.2s; }
  .nav-links a:hover { color: var(--cream); }

  .hero {
    display: flex;
    flex-direction: column;
    justify-content: center;
    padding: 4rem 0;
  }

  .hero-label {
    font-family: 'DM Mono', monospace;
    font-size: 0.7rem;
    letter-spacing: 0.2em;
    text-transform: uppercase;
    color: var(--accent);
    margin-bottom: 1.5rem;
  }

  h1 {
    font-family: 'Playfair Display', serif;
    font-size: clamp(4rem, 10vw, 9rem);
    font-weight: 400;
    line-height: 0.92;
    letter-spacing: -0.02em;
  }

  h1 em {
    font-style: italic;
    color: var(--accent);
  }

  .hero-sub {
    margin-top: 3rem;
    max-width: 520px;
    font-size: 1.05rem;
    line-height: 1.75;
    color: #B8A99A;
    font-weight: 300;
  }

  .scroll-hint {
    font-family: 'DM Mono', monospace;
    font-size: 0.65rem;
    letter-spacing: 0.15em;
    text-transform: uppercase;
    color: var(--warm-mid);
    display: flex;
    align-items: center;
    gap: 1rem;
  }
  .scroll-hint::after {
    content: '';
    display: block;
    width: 40px;
    height: 1px;
    background: var(--warm-mid);
    animation: lengthen 2s ease-in-out infinite alternate;
  }
  @keyframes lengthen {
    from { width: 20px; opacity: 0.4; }
    to { width: 60px; opacity: 1; }
  }

  /* VINYL GRAPHIC */
  .vinyl {
    position: absolute;
    right: -80px;
    top: 50%;
    transform: translateY(-50%);
    width: 500px;
    height: 500px;
    opacity: 0.12;
    animation: spin 30s linear infinite;
  }
  @keyframes spin { to { transform: translateY(-50%) rotate(360deg); } }

  /* SECTIONS */
  section {
    padding: 6rem 4rem;
    max-width: 1200px;
    margin: 0 auto;
  }

  .section-tag {
    font-family: 'DM Mono', monospace;
    font-size: 0.65rem;
    letter-spacing: 0.2em;
    text-transform: uppercase;
    color: var(--accent);
    margin-bottom: 3rem;
    display: flex;
    align-items: center;
    gap: 1rem;
  }
  .section-tag::before {
    content: '';
    display: block;
    width: 24px;
    height: 1px;
    background: var(--accent);
  }

  /* THREE WORDS */
  .three-words {
    display: grid;
    grid-template-columns: repeat(3, 1fr);
    gap: 2px;
    margin-bottom: 5rem;
  }
  .word-card {
    background: #231E18;
    padding: 2.5rem 2rem;
    border-left: 3px solid var(--accent);
    transition: background 0.3s;
  }
  .word-card:hover { background: #2C261E; }
  .word-num {
    font-family: 'DM Mono', monospace;
    font-size: 0.6rem;
    color: var(--warm-mid);
    letter-spacing: 0.2em;
    margin-bottom: 1rem;
  }
  .word-main {
    font-family: 'Playfair Display', serif;
    font-size: 2rem;
    font-weight: 400;
    margin-bottom: 0.5rem;
  }
  .word-sub {
    font-size: 0.85rem;
    color: var(--warm-mid);
    line-height: 1.6;
  }

  /* MUSIC SECTION */
  .music-grid {
    display: grid;
    grid-template-columns: 1fr 1fr;
    gap: 3rem;
    align-items: start;
  }
  .music-intro {
    font-family: 'Playfair Display', serif;
    font-size: 1.8rem;
    font-weight: 400;
    line-height: 1.4;
    color: var(--cream);
    margin-bottom: 1.5rem;
  }
  .music-body {
    font-size: 0.95rem;
    color: #B8A99A;
    line-height: 1.85;
  }

  /* GENRE TAGS */
  .genre-list { display: flex; flex-direction: column; gap: 1px; }
  .genre-item {
    background: #1E1A14;
    padding: 1.5rem 2rem;
    display: flex;
    justify-content: space-between;
    align-items: center;
    transition: background 0.2s, padding-left 0.3s;
    cursor: default;
  }
  .genre-item:hover { background: #2A231A; padding-left: 2.5rem; }
  .genre-name {
    font-family: 'Playfair Display', serif;
    font-size: 1.3rem;
    font-style: italic;
  }
  .genre-desc {
    font-family: 'DM Mono', monospace;
    font-size: 0.65rem;
    color: var(--warm-mid);
    letter-spacing: 0.1em;
    text-align: right;
    max-width: 180px;
  }

  /* DIVIDER */
  .tape-divider {
    height: 1px;
    background: repeating-linear-gradient(90deg,
      var(--accent) 0px, var(--accent) 8px,
      transparent 8px, transparent 12px);
    margin: 0 4rem;
    opacity: 0.3;
  }

  /* ARTIST LINKS */
  .artists-section { padding: 5rem 4rem; max-width: 1200px; margin: 0 auto; }
  .artists-header {
    font-family: 'Playfair Display', serif;
    font-size: 2.5rem;
    font-weight: 400;
    margin-bottom: 2rem;
  }
  .artists-sub { color: #B8A99A; font-size: 0.9rem; margin-bottom: 3rem; }
  .artist-cards { display: grid; grid-template-columns: repeat(3, 1fr); gap: 2px; }
  .artist-card {
    background: #1E1A14;
    padding: 2.5rem 2rem;
    text-decoration: none;
    color: var(--cream);
    display: flex;
    flex-direction: column;
    gap: 0.75rem;
    transition: background 0.25s;
    position: relative;
    overflow: hidden;
  }
  .artist-card::after {
    content: '↗';
    position: absolute;
    top: 1.5rem;
    right: 1.5rem;
    color: var(--warm-mid);
    font-size: 0.85rem;
    transition: transform 0.2s, color 0.2s;
  }
  .artist-card:hover { background: #2A231A; }
  .artist-card:hover::after { transform: translate(3px, -3px); color: var(--accent); }
  .artist-genre-tag {
    font-family: 'DM Mono', monospace;
    font-size: 0.6rem;
    letter-spacing: 0.15em;
    text-transform: uppercase;
    color: var(--accent);
  }
  .artist-name {
    font-family: 'Playfair Display', serif;
    font-size: 1.4rem;
    font-weight: 400;
  }
  .artist-role { font-size: 0.8rem; color: var(--warm-mid); }

  /* BACKSTAGE */
  .backstage-quote {
    background: #180F08;
    padding: 5rem 6rem;
    margin: 0;
    position: relative;
  }
  .backstage-quote blockquote {
    font-family: 'Playfair Display', serif;
    font-size: clamp(1.6rem, 3vw, 2.8rem);
    font-weight: 400;
    font-style: italic;
    line-height: 1.5;
    color: var(--cream);
    max-width: 800px;
    border-left: 3px solid var(--accent);
    padding-left: 3rem;
  }
  .backstage-quote blockquote span { color: var(--accent); }
  .quote-attr {
    font-family: 'DM Mono', monospace;
    font-size: 0.7rem;
    letter-spacing: 0.15em;
    text-transform: uppercase;
    color: var(--warm-mid);
    margin-top: 2rem;
    padding-left: 3rem;
  }

  /* FOOTER */
  footer {
    padding: 4rem;
    display: flex;
    justify-content: space-between;
    align-items: flex-end;
    border-top: 1px solid #2A231A;
  }
  .footer-name {
    font-family: 'Playfair Display', serif;
    font-size: 1.5rem;
  }
  .footer-meta {
    font-family: 'DM Mono', monospace;
    font-size: 0.65rem;
    color: var(--warm-mid);
    letter-spacing: 0.12em;
    text-align: right;
    line-height: 2;
  }

  /* ANIMATIONS */
  .fade-up {
    opacity: 0;
    transform: translateY(20px);
    transition: opacity 0.7s ease, transform 0.7s ease;
  }
  .fade-up.visible { opacity: 1; transform: translateY(0); }

  @media (max-width: 768px) {
    header, section, .artists-section { padding: 3rem 2rem; }
    .three-words { grid-template-columns: 1fr; }
    .music-grid { grid-template-columns: 1fr; }
    .artist-cards { grid-template-columns: 1fr; }
    .backstage-quote { padding: 3rem 2rem; }
    .backstage-quote blockquote { padding-left: 1.5rem; }
    .quote-attr { padding-left: 1.5rem; }
    footer { flex-direction: column; gap: 2rem; }
    .footer-meta { text-align: left; }
  }
</style>
</head>
<body>

<!-- HEADER -->
<header>
  <div class="header-tape"></div>

  <nav class="nav">
    <span>Leslie Shi</span>
    <ul class="nav-links">
      <li><a href="#about">About</a></li>
      <li><a href="#music">Music</a></li>
      <li><a href="#favorites">Favorites</a></li>
    </ul>
  </nav>

  <div class="hero">
    <p class="hero-label">Show Producer / Music Obsessive</p>
    <h1>Leslie<br><em>Shi.</em></h1>
    <p class="hero-sub">
      Happiest in the shadows — coordinating backstage, watching cue lines sync
      perfectly with the crowd's energy. A translator between sound and light.
    </p>
  </div>

  <div class="scroll-hint">Scroll to explore</div>

  <!-- Vinyl record SVG -->
  <svg class="vinyl" viewBox="0 0 500 500" fill="none" xmlns="http://www.w3.org/2000/svg">
    <circle cx="250" cy="250" r="245" stroke="#F5F0E8" stroke-width="2"/>
    <circle cx="250" cy="250" r="220" stroke="#F5F0E8" stroke-width="0.5"/>
    <circle cx="250" cy="250" r="190" stroke="#F5F0E8" stroke-width="0.5"/>
    <circle cx="250" cy="250" r="160" stroke="#F5F0E8" stroke-width="0.5"/>
    <circle cx="250" cy="250" r="130" stroke="#F5F0E8" stroke-width="0.5"/>
    <circle cx="250" cy="250" r="100" stroke="#F5F0E8" stroke-width="0.5"/>
    <circle cx="250" cy="250" r="70" stroke="#F5F0E8" stroke-width="0.5"/>
    <circle cx="250" cy="250" r="40" stroke="#F5F0E8" stroke-width="1"/>
    <circle cx="250" cy="250" r="15" fill="#F5F0E8"/>
    <circle cx="250" cy="250" r="6" fill="#1A1510"/>
  </svg>
</header>

<!-- ABOUT -->
<section id="about" class="fade-up">
  <div class="section-tag">About</div>
  <div class="three-words">
    <div class="word-card">
      <div class="word-num">01</div>
      <div class="word-main">Curious</div>
      <div class="word-sub">Always asking what makes a moment land — in music, in light, in a crowd's collective exhale.</div>
    </div>
    <div class="word-card">
      <div class="word-num">02</div>
      <div class="word-main">Resilient</div>
      <div class="word-sub">Organising a multi-school music festival from scratch teaches you that no plan survives first contact.</div>
    </div>
    <div class="word-card">
      <div class="word-num">03</div>
      <div class="word-main">Perfectionist</div>
      <div class="word-sub">Behind the scenes. The kind who notices when the cue fires two beats late — and fixes it silently.</div>
    </div>
  </div>
</section>

<div class="tape-divider"></div>

<!-- MUSIC -->
<section id="music" class="fade-up">
  <div class="section-tag">Music & Philosophy</div>
  <div class="music-grid">
    <div>
      <p class="music-intro">Obsessed with the <em>mechanics of euphoria.</em></p>
      <p class="music-body">
        My taste in music is inseparable from how I think about production.
        Each genre has its own grammar of emotion — and a great show producer
        is a translator, someone who knows exactly how to convert sound into
        atmosphere, and atmosphere into feeling.
      </p>
    </div>
    <div class="genre-list">
      <div class="genre-item">
        <span class="genre-name">Jazz</span>
        <span class="genre-desc">Unpredictable, sophisticated textures</span>
      </div>
      <div class="genre-item">
        <span class="genre-name">Rock</span>
        <span class="genre-desc">Raw, high-voltage energy</span>
      </div>
      <div class="genre-item">
        <span class="genre-name">Folk</span>
        <span class="genre-desc">Intimate storytelling warmth</span>
      </div>
    </div>
  </div>
</section>

<div class="tape-divider"></div>

<!-- QUOTE / BACKSTAGE -->
<div class="backstage-quote fade-up">
  <blockquote>
    "While everyone else was enjoying the spotlight, my happiest moments were spent
    <span>hidden in the shadows</span>, coordinating backstage."
  </blockquote>
  <p class="quote-attr">— Leslie Shi, on producing a multi-school music festival</p>
</div>

<!-- ARTISTS -->
<div id="favorites" class="artists-section fade-up">
  <div class="section-tag">Favorite Artists</div>
  <h2 class="artists-header">The holy trinity.</h2>
  <p class="artists-sub">Three artists who shaped how I hear the world.</p>
  <div class="artist-cards">
    <a class="artist-card" href="https://www.bobdylan.com" target="_blank" rel="noopener">
      <span class="artist-genre-tag">Folk</span>
      <span class="artist-name">Bob Dylan</span>
      <span class="artist-role">My favorite folkie — the original storyteller</span>
    </a>
    <a class="artist-card" href="https://billevansofficial.com" target="_blank" rel="noopener">
      <span class="artist-genre-tag">Jazz</span>
      <span class="artist-name">Bill Evans</span>
      <span class="artist-role">My favorite jazzman — architecture in sound</span>
    </a>
    <a class="artist-card" href="https://www.georgeharrison.com" target="_blank" rel="noopener">
      <span class="artist-genre-tag">Rock</span>
      <span class="artist-name">George Harrison</span>
      <span class="artist-role">My favorite rock star — the quiet Beatle</span>
    </a>
  </div>
</div>

<!-- FOOTER -->
<footer>
  <div class="footer-name">Leslie Shi</div>
  <div class="footer-meta">
    Show Producer &amp; Music Obsessive<br>
    Curious · Resilient · Perfectionist
  </div>
</footer>

<script>
  const observer = new IntersectionObserver((entries) => {
    entries.forEach(e => {
      if (e.isIntersecting) { e.target.classList.add('visible'); }
    });
  }, { threshold: 0.1 });

  document.querySelectorAll('.fade-up').forEach(el => observer.observe(el));
</script>
</body>
</html>
