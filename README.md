<!DOCTYPE html>
<html lang="ro">
<head>
  <meta charset="UTF-8" />
  <meta name="viewport" content="width=device-width, initial-scale=1" />
  <title>CerAlex – Lumânări parfumate & produse din ceară</title>
  <meta name="description" content="CerAlex – lumânări parfumate, aranjamente florale din ceară și blocuri de ceară parfumată, realizate manual cu suflet și culoare." />
  <style>
    :root {
      --primary: #6c2bd9;   /* mov intens */
      --accent: #ff3d7f;    /* roz puternic */
      --mint: #2dd4bf;      /* turcoaz */
      --sun:  #fbbf24;      /* galben cald */
      --dark: #0f172a;      /* albastru foarte închis */
      --text: #334155;
      --bg1:  #fef3c7;
      --bg2:  #e9d5ff;
      --bg3:  #cffafe;
      --white:#ffffff;
    }

    /* Fundal cu gradient animat */
    body {
      margin: 0;
      font-family: "Poppins", system-ui, -apple-system, Segoe UI, Roboto, Ubuntu, Cantarell, "Helvetica Neue", Arial, sans-serif;
      color: var(--dark);
      background: linear-gradient(135deg, var(--bg1), var(--bg2), var(--bg3));
      background-size: 200% 200%;
      animation: bgShift 12s ease-in-out infinite;
      min-height: 100vh;
    }
    @keyframes bgShift {
      0%   { background-position: 0% 50%; }
      50%  { background-position: 100% 50%; }
      100% { background-position: 0% 50%; }
    }

    /* Header centrat cu logo */
    header {
      position: sticky;
      top: 0;
      backdrop-filter: blur(8px);
      background: rgba(255,255,255,0.7);
      border-bottom: 1px solid rgba(15,23,42,0.08);
      z-index: 100;
    }
    .topbar {
      max-width: 1100px;
      margin: 0 auto;
      padding: 14px 24px;
      display: flex;
      flex-direction: column;
      align-items: center;
      gap: 10px;
    }
    .logo img {
      height: 64px; /* înlocuiește logo.jpg cu emblema brandului */
      width: auto;
      display: block;
      border-radius: 8px;
    }
    .logo-text {
      font-weight: 900;
      font-size: 24px;
      letter-spacing: 0.6px;
      background: linear-gradient(90deg, var(--primary), var(--accent));
      -webkit-background-clip: text;
      background-clip: text;
      color: transparent;
    }
    .nav {
      display: flex;
      gap: 10px;
      flex-wrap: wrap;
      justify-content: center;
    }
    .nav a {
      text-decoration: none;
      color: #0b1020;
      background: rgba(255,255,255,0.9);
      border: 1px solid rgba(15, 23, 42, 0.08);
      border-radius: 999px;
      padding: 8px 12px;
      font-size: 14px;
      transition: transform 0.15s ease, box-shadow 0.2s ease;
    }
    .nav a:hover {
      transform: translateY(-2px);
      box-shadow: 0 6px 16px rgba(15,23,42,0.12);
      background: #fff;
    }

    /* Container principal */
    .container { max-width: 1100px; margin: 0 auto; padding: 24px; }

    /* Secțiune hero cu poveste */
    .hero {
      margin-top: 18px;
      background: linear-gradient(135deg, rgba(108, 43, 217, 0.12), rgba(255, 61, 127, 0.12));
      border: 1px solid rgba(108, 43, 217, 0.25);
      border-radius: 20px;
      padding: 32px;
      backdrop-filter: blur(6px);
      box-shadow: 0 10px 30px rgba(15, 23, 42, 0.12);
      overflow: hidden;
      position: relative;
    }
    .hero .brand {
      display: inline-block;
      font-weight: 800;
      font-size: 34px;
      letter-spacing: 0.5px;
      background: linear-gradient(90deg, var(--primary), var(--accent));
      -webkit-background-clip: text;
      background-clip: text;
      color: transparent;
    }
    .tagline { margin-top: 8px; font-size: 18px; color: var(--text); }
    .flare {
      position: absolute; inset: -40px;
      background:
        radial-gradient(600px 300px at 10% 0%, rgba(255, 61, 127, 0.2), transparent 60%),
        radial-gradient(600px 300px at 90% 10%, rgba(45, 212, 191, 0.2), transparent 60%);
      pointer-events: none;
    }

    /* Tabs categorii */
    .tabs {
      margin-top: 26px;
      display: flex;
      gap: 10px;
      flex-wrap: wrap;
    }
    .tab-btn {
      border: 1px solid rgba(15, 23, 42, 0.12);
      background: #fff;
      color: #0b1020;
      border-radius: 10px;
      padding: 10px 14px;
      cursor: pointer;
      font-weight: 600;
      transition: all 0.2s ease;
    }
    .tab-btn.active {
      background: linear-gradient(90deg, var(--mint), var(--sun));
      color: #0b1020;
      box-shadow: 0 6px 16px rgba(251,191,36,0.25);
      transform: translateY(-1px);
    }

    /* Grilă carduri produse */
    h2 { margin: 32px 0 16px; font-size: 26px; color: #1f2937; }
    .grid { display: grid; grid-template-columns: repeat(12, 1fr); gap: 18px; }
    .card {
      grid-column: span 12;
      background: rgba(255, 255, 255, 0.94);
      border: 1px solid rgba(15, 23, 42, 0.08);
      border-radius: 16px;
      padding: 16px;
      box-shadow: 0 6px 20px rgba(15, 23, 42, 0.08);
      transition: transform 160ms ease, box-shadow 0.2s ease;
      opacity: 0; transform: translateY(10px); /* pentru animația de reveal */
    }
    .card.reveal {
      opacity: 1; transform: translateY(0);
      transition: opacity 0.5s ease, transform 0.5s ease;
    }
    @media (min-width: 720px) { .card { grid-column: span 6; } }
    .card-header {
      display: flex; align-items: center; justify-content: space-between; gap: 10px;
    }
    .card h3 { margin: 0; font-size: 20px; color: var(--primary); }
    .badge {
      display: inline-block; margin: 6px 0 0 0; padding: 6px 10px;
      background: linear-gradient(90deg, var(--mint), var(--sun));
      color: #0b1020; border-radius: 999px; font-size: 12px; font-weight: 600;
      box-shadow: 0 4px 12px rgba(251, 191, 36, 0.25);
    }
    .fav {
      border: none; background: transparent; cursor: pointer; font-size: 20px;
      transition: transform 0.15s ease; color: #cbd5e1;
    }
    .fav.active { color: var(--accent); transform: scale(1.15); }
    .card p { margin: 8px 0 10px; color: var(--text); }

    /* Slot imagine simplă */
    .img-slot {
      width: 100%; border-radius: 12px; overflow: hidden; position: relative;
      border: 2px solid #e9d5ff;
    }
    .img-slot img {
      width: 100%; height: auto; display: block;
      transition: transform 0.4s ease;
    }
    .img-slot:hover img { transform: scale(1.03); }

    /* Două imagini în același chenar (galerie simplă) */
    .img-double {
      display: grid; grid-template-columns: 1fr 1fr; gap: 10px;
      border: 2px solid #e9d5ff; border-radius: 12px; padding: 10px; background: #fff;
    }
    .img-double img {
      width: 100%; border-radius: 8px; display: block; cursor: zoom-in;
    }

    /* Slider mic pentru mai multe imagini */
    .slider { position: relative; border: 2px solid #e9d5ff; border-radius: 12px; overflow: hidden; }
    .slides { display: flex; transition: transform 0.4s ease; }
    .slides img { width: 100%; flex: 0 0 100%; display: block; }
    .slider .controls {
      position: absolute; inset: auto 0 8px 0; display: flex; justify-content: center; gap: 8px;
    }
    .dot {
      width: 8px; height: 8px; border-radius: 50%; background: #c4b5fd; border: 1px solid #7c3aed;
      cursor: pointer; opacity: 0.8;
    }
    .dot.active { background: #7c3aed; opacity: 1; }

    /* Prețul produsului */
    .price { margin-top: 8px; font-weight: 800; color: var(--accent); font-size: 16px; }
    .cta {
      margin-top: 10px; display: inline-flex; align-items: center; gap: 8px;
      background: linear-gradient(90deg, var(--primary), var(--accent));
      color: #fff; border: none; padding: 10px 14px; border-radius: 12px; cursor: pointer;
      box-shadow: 0 8px 20px rgba(108, 43, 217, 0.25);
      transition: transform 0.12s ease, box-shadow 0.2s ease;
    }
    .cta:hover { transform: translateY(-1px); box-shadow: 0 12px 28px rgba(108, 43, 217, 0.35); }

    /* Info box */
    .info {
      background: rgba(255,255,255,0.9);
      border: 1px solid rgba(15,23,42,0.08);
      border-radius: 16px;
      padding: 18px;
      box-shadow: 0 6px 20px rgba(15,23,42,0.08);
    }

    /* Footer cu contor animat */
    footer {
      margin-top: 36px;
      background: linear-gradient(135deg, rgba(45,212,191,0.16), rgba(251,191,36,0.16));
      border: 1px solid rgba(45,212,191,0.35);
      border-radius: 16px;
      padding: 24px;
      text-align: center;
    }
    .counter { font-size: 28px; font-weight: 800; color: var(--accent); }
    footer p { margin: 10px 0 0 0; color: var(--text); }

    /* Lightbox pentru imagini mari */
    .lightbox {
      position: fixed; inset: 0; background: rgba(0,0,0,0.7);
      display: none; align-items: center; justify-content: center; z-index: 200;
    }
    .lightbox.open { display: flex; }
    .lightbox img {
      max-width: 90vw; max-height: 80vh; border-radius: 12px; box-shadow: 0 12px 36px rgba(0,0,0,0.5);
    }
    .lightbox .close {
      position: absolute; top: 16px; right: 16px; background: #fff; border: none; border-radius: 999px;
      width: 36px; height: 36px; cursor: pointer; font-weight: 800;
    }
  </style>
</head>
<body>
  <!-- Header centrat cu logo -->
  <header>
    <div class="topbar">
      <div class="logo">
        <!-- Încarcă emblema brandului ca Emblema.jpg sau schimbă numele fișierului -->
        <img src="Emblema.jpg" alt="Logo CerAlex" />
      </div>
      <div class="logo-text">CerAlex</div>
      <nav class="nav">
        <a href="#acasa">Acasă</a>
        <a href="#florale">Aranjamente florale</a>
        <a href="#blocuri">Blocuri de ceară</a>
        <a href="#iarna">Sărbătorile de iarnă</a>
        <a href="#despre">Despre CerAlex</a>
        <a href="#contact">Contact</a>
        <a href="#livrari">Livrări</a>
      </nav>
    </div>
  </header>

  <div class="container">
    <!-- Poveste de început -->
    <section class="hero" id="acasa">
      <div class="flare" aria-hidden="true"></div>
      <span class="brand">Magia CerAlex</span>
      <p class="tagline">
        Lumânări parfumate și aranjamente din ceară, turnate manual, cu culori vii și arome alese. Fiecare piesă spune o poveste caldă.
      </p>

      <!-- Tabs categorii (butonare rapidă) -->
      <div class="tabs" aria-label="Categorii produse">
        <button class="tab-btn active" data-tab="florale">Aranjamente florale</button>
        <button class="tab-btn" data-tab="blocuri">Blocuri din ceară parfumată</button>
        <button class="tab-btn" data-tab="iarna">Sărbătorile de iarnă</button>
      </div>
    </section>

    <!-- Categorie 1: Aranjamente florale -->
    <section id="florale" class="tab-panel">
      <h2>Aranjamente florale</h2>
      <div class="grid">
        <article class="card">
          <div class="card-header">
            <h3>Floricele simple</h3>
            <button class="fav" aria-label="Favorite">♡</button>
          </div>
          <span class="badge">Delicate & parfumate</span>
          <p>Accente colorate care aduc prospețime în orice colț al casei.</p>
          <!-- Imagine simplă -->
          <div class="img-slot">
            <img src="Model-floare.1jpg.jpg" alt="Floricele simple" loading="lazy" />
          </div>
          <div class="price">Preț: 7 RON</div>
          <button class="cta">Detalii</button>
        </article>

        <article class="card">
          <div class="card-header">
            <h3>Coșulețe cu floricele</h3>
            <button class="fav" aria-label="Favorite">♡</button>
          </div>
          <span class="badge">Cadouri elegante</span>
          <p>Combinații de culori și arome, atent îmbinate.</p>
          <!-- Două imagini în același chenar -->
          <div class="img-double">
            <img src="Cos1.jpg" alt="Coșuleț cu floricele - vedere 1" loading="lazy" />
            <img src="cos2.jpg" alt="Coșuleț cu floricele - vedere 2" loading="lazy" />
          </div>
          <div class="price">Preț: 70 RON</div>
          <button class="cta">Detalii</button>
        </article>

        <article class="card">
          <div class="card-header">
            <h3>Floricele parfumate</h3>
            <button class="fav" aria-label="Favorite">♡</button>
          </div>
          <span class="badge">Experiență senzorială</span>
          <p>Frumusețe vizuală cu mirosuri încântătoare.</p>
          <!-- Slider cu 3 imagini -->
          <div class="slider" data-index="0">
            <div class="slides">
              <img src="Model-floare.jpg" alt="Floricele parfumate – imagine 1" loading="lazy" />
              <img src="poze.jpg" alt="Floricele parfumate – imagine 2" loading="lazy" />
              <img src="poze.jpg" alt="Floricele parfumate – imagine 3" loading="lazy" />
            </div>
            <div class="controls">
              <span class="dot active" aria-label="Imagine 1"></span>
              <span class="dot" aria-label="Imagine 2"></span>
              <span class="dot" aria-label="Imagine 3"></span>
            </div>
          </div>
          <div class="price">Preț: 7 RON</div>
          <button class="cta">Detalii</button>
        </article>
      </div>
    </section>

    <!-- Categorie 2: Blocuri din ceară parfumată -->
    <section id="blocuri" class="tab-panel" hidden>
      <h2>Blocuri din ceară parfumată</h2>
      <div class="grid">
        <article class="card">
          <div class="card-header">
            <h3>Forme variate</h3>
            <button class="fav" aria-label="Favorite">♡</button>
          </div>
          <span class="badge">Culori tari</span>
          <p>Blocuri turnate manual în forme jucăușe.</p>
          <div class="img-slot">
            <img src="Bloc-ceara.jpg" alt="Bloc de ceară – forme variate" loading="lazy" />
          </div>
          <div class="price">Preț: 15 RON</div>
          <button class="cta">Detalii</button>
        </article>

        <article class="card">
          <div class="card-header">
            <h3>Arome intense</h3>
            <button class="fav" aria-label="Favorite">♡</button>
          </div>
          <span class="badge">Relaxare rapidă</span>
          <p>Se topesc ușor și eliberează parfum plăcut.</p>
          <div class="img-double">
            <img src="Bloc-ceara.jpg" alt="Bloc de ceară – aromă 1" loading="lazy" />
            <img src="poze.jpg" alt="Bloc de ceară – aromă 2" loading="lazy" />
          </div>
          <div class="price">Preț: 20 RON</div>
          <button class="cta">Detalii</button>
        </article>
      </div>
    </section>

    <!-- Categorie 3: Sărbătorile de iarnă -->
    <section id="iarna" class="tab-panel" hidden>
      <h2>Sărbătorile de iarnă</h2>
      <div class="grid">
        <article class="card">
          <div class="card-header">
            <h3>Lumânări de sezon</h3>
            <button class="fav" aria-label="Favorite">♡</button>
          </div>
          <span class="badge">Scorțișoară • Vanilie • Brad</span>
          <p>Inspirate din magia iernii.</p>
          <div class="img-slot">
            <img src="poze.jpg" alt="Lumânare de sezon" loading="lazy" />
          </div>
          <div class="price">Preț: 30 RON</div>
          <button class="cta">Detalii</button>
        </article>

        <article class="card">
          <div class="card-header">
            <h3>Aranjamente de sezon</h3>
            <button class="fav" aria-label="Favorite">♡</button>
          </div>
          <span class="badge">Festiv & cald</span>
          <p>Culori bogate și detalii jucăușe.</p>
          <div class="slider" data-index="0">
            <div class="slides">
              <img src="3.jpg" alt="Aranjament de sezon – imagine 1" loading="lazy" />
              <img src="Brad.jpg" alt="Aranjament de sezon – imagine 2" loading="lazy" />
            </div>
            <div class="controls">
              <span class="dot active" aria-label="Imagine 1"></span>
              <span class="dot" aria-label="Imagine 2"></span>
            </div>
          </div>
          <div class="price">Preț: 25 RON</div>
          <button class="cta">Detalii</button>
        </article>
      </div>
    </section>

    <!-- Despre CerAlex -->
    <h2 id="despre">Despre CerAlex</h2>
    <section class="info">
      <p>
        CerAlex s-a născut din pasiunea pentru culoare și parfum. Îmbin forme îndrăznețe cu arome calde,
        pentru produse care aduc bucurie în casele oamenilor. Fiecare creație este turnată manual, cu grijă pentru detalii.
      </p>
    </section>

    <!-- Contact -->
    <h2 id="contact">Contact</h2>
    <section class="info">
      <p>Ai întrebări sau vrei o comandă personalizată? Scrie-mi și îți răspund cu drag.</p>
      <div class="nav" aria-label="Linkuri contact">
        <a href="https://www.facebook.com/people/Ceralex/100069947412328/?mibextid=wwXIfr&rdid=qJ5MxJXuccJH2E9D&share_url=https%3A%2F%2Fwww.facebook.com%2Fshare%2F16MhW5B9Tk%2F%3Fmibextid%3DwwXIfr" aria-label="Facebook">Facebook</a>
        <a href="https://wa.me/40700000000" target="_blank" rel="noopener" aria-label="WhatsApp">WhatsApp</a>
        <a href="tel:+40700000000" aria-label="Telefon">Telefon</a>
        <a href="https://www.instagram.com/cera_lex3/?igsh=MTlwcTJmZnR6bnZmYg%3D%3D#" target="_blank" rel="noopener" aria-label="Instagram">Instagram</a>
      </div>
    </section>

    <!-- Livrări -->
    <footer id="livrari">
      <div class="counter">Livrări efectuate: <span id="count">0</span></div>
      <p>Fiecare pachet este pregătit cu grijă, ca magia lumânărilor să ajungă la tine în siguranță.</p>
      <p>© CerAlex – Handmade cu pasiune</p>
    </footer>
  </div>

  <!-- Lightbox -->
  <div class="lightbox" id="lightbox" aria-hidden="true">
    <button class="close" aria-label="Închide">×</button>
    <img src="" alt="Imagine mărită" />
  </div>

  <script>
    // Tabs pentru categorii
    const tabs = document.querySelectorAll('.tab-btn');
    const panels = document.querySelectorAll('.tab-panel');
    tabs.forEach(btn => {
      btn.addEventListener('click', () => {
        tabs.forEach(b => b.classList.remove('active'));
        btn.classList.add('active');
        const id = btn.dataset.tab;
        panels.forEach(p => {
          p.hidden = p.id !== id;
        });
        // Scroll la secțiunea activă
        const panel = document.getElementById(id);
        panel.scrollIntoView({ behavior: 'smooth', block: 'start' });
      });
    });

    // Animație reveal la scroll
    const observer = new IntersectionObserver(entries => {
      entries.forEach(entry => {
        if (entry.isIntersecting) entry.target.classList.add('reveal');
      });
    }, { threshold: 0.1 });
    document.querySelectorAll('.card').forEach(el => observer.observe(el));

    // Favorite (inimioară) vizual
    document.querySelectorAll('.fav').forEach(btn => {
      btn.addEventListener('click', () => btn.classList.toggle('active'));
    });

    // Slider simplu cu puncte (dots)
    document.querySelectorAll('.slider').forEach(slider => {
      const slides = slider.querySelector('.slides');
      const dots = slider.querySelectorAll('.dot');
      dots.forEach((dot, i) => {
        dot.addEventListener('click', () => {
          dots.forEach(d => d.classList.remove('active'));
          dot.classList.add('active');
          slides.style.transform = `translateX(-${i * 100}%)`;
        });
      });
    });

    // Lightbox: click pe imagini pentru a mări
    const lightbox = document.getElementById('lightbox');
    const lbImg = lightbox.querySelector('img');
    document.querySelectorAll('.img-slot img, .img-double img, .slides img').forEach(img => {
      img.addEventListener('click', () => {
        lbImg.src = img.src;
        lightbox.classList.add('open');
        lightbox.setAttribute('aria-hidden', 'false');
      });
    });
    lightbox.querySelector('.close').addEventListener('click', () => {
      lightbox.classList.remove('open');
      lightbox.setAttribute('aria-hidden', 'true');
      lbImg.src = '';
    });
    lightbox.addEventListener('click', (e) => {
      if (e.target === lightbox) {
        lightbox.classList.remove('open');
        lightbox.setAttribute('aria-hidden', 'true');
        lbImg.src = '';
      }
    });

    // Contor livrări animat
    function animateCount(el, to = 128, duration = 1200) {
      const start = 0;
      const startTime = performance.now();
      function update(now) {
        const progress = Math.min((now - startTime) / duration, 1);
        const value = Math.floor(start + (to - start) * progress);
        el.textContent = value;
        if (progress < 1) requestAnimationFrame(update);
      }
      requestAnimationFrame(update);
    }
    animateCount(document.getElementById('count'), 128);

    // Navigație din meniu către secțiuni
    document.querySelectorAll('nav.nav a').forEach(a => {
      a.addEventListener('click', (e) => {
        const href = a.getAttribute('href');
        if (href.startsWith('#')) {
          e.preventDefault();
          const target = document.querySelector(href);
          if (!target) return;
          target.scrollIntoView({ behavior: 'smooth', block: 'start' });
        }
      });
    });
  </script>
</body>
</html>
