[invitation (2).html](https://github.com/user-attachments/files/27505149/invitation.2.html)
# -<!DOCTYPE html>
<html lang="kk">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>Айман — Cloud9 Кешкі Ас</title>
<link href="https://fonts.googleapis.com/css2?family=Cormorant+Garamond:ital,wght@0,300;0,400;0,600;1,300;1,400&family=Montserrat:wght@300;400;500&display=swap" rel="stylesheet">
<style>
  *, *::before, *::after { box-sizing: border-box; margin: 0; padding: 0; }

  :root {
    --gold: #C9A96E;
    --gold-light: #E8D5A3;
    --rose: #D4A0A0;
    --dark: #0D0A0E;
    --dark2: #130F14;
    --dark3: #1C1620;
    --text: #F5EDE0;
    --muted: #A08878;
  }

  html { scroll-behavior: smooth; }

  body {
    background: var(--dark);
    color: var(--text);
    font-family: 'Montserrat', sans-serif;
    font-weight: 300;
    min-height: 100vh;
    overflow-x: hidden;
  }

  canvas#petals {
    position: fixed;
    top: 0; left: 0;
    width: 100%; height: 100%;
    pointer-events: none;
    z-index: 0;
    opacity: 0.35;
  }

  .page { position: relative; z-index: 1; }

  /* ── HERO ── */
  .hero {
    min-height: 100vh;
    display: flex;
    flex-direction: column;
    align-items: center;
    justify-content: center;
    text-align: center;
    padding: 3rem 2rem;
    background: radial-gradient(ellipse at 50% 60%, #2a1a2e 0%, var(--dark) 70%);
  }

  .hero-pre {
    font-family: 'Montserrat', sans-serif;
    font-size: 0.65rem;
    letter-spacing: 0.35em;
    text-transform: uppercase;
    color: var(--gold);
    margin-bottom: 2rem;
    opacity: 0;
    animation: fadeUp 1s 0.3s forwards;
  }

  .hero-name {
    font-family: 'Cormorant Garamond', serif;
    font-size: clamp(4rem, 15vw, 8rem);
    font-weight: 300;
    font-style: italic;
    color: var(--text);
    line-height: 1;
    letter-spacing: -0.02em;
    opacity: 0;
    animation: fadeUp 1.2s 0.6s forwards;
  }

  .hero-divider {
    width: 80px;
    height: 1px;
    background: linear-gradient(90deg, transparent, var(--gold), transparent);
    margin: 2rem auto;
    opacity: 0;
    animation: fadeUp 1s 0.9s forwards;
  }

  .hero-date {
    font-family: 'Cormorant Garamond', serif;
    font-size: clamp(1.2rem, 4vw, 1.8rem);
    font-weight: 300;
    letter-spacing: 0.15em;
    color: var(--gold-light);
    opacity: 0;
    animation: fadeUp 1s 1.1s forwards;
  }

  .hero-sub {
    font-size: 0.7rem;
    letter-spacing: 0.25em;
    text-transform: uppercase;
    color: var(--muted);
    margin-top: 0.75rem;
    opacity: 0;
    animation: fadeUp 1s 1.3s forwards;
  }

  .scroll-hint {
    position: absolute;
    bottom: 2rem;
    left: 50%;
    transform: translateX(-50%);
    display: flex;
    flex-direction: column;
    align-items: center;
    gap: 8px;
    opacity: 0;
    animation: fadeUp 1s 2s forwards;
  }

  .scroll-hint span {
    font-size: 0.6rem;
    letter-spacing: 0.3em;
    text-transform: uppercase;
    color: var(--muted);
  }

  .scroll-line {
    width: 1px;
    height: 40px;
    background: linear-gradient(to bottom, var(--gold), transparent);
    animation: scrollLine 2s 2s infinite;
  }

  /* ── COUNTDOWN ── */
  .section {
    padding: 5rem 2rem;
    max-width: 680px;
    margin: 0 auto;
    text-align: center;
  }

  .section-label {
    font-size: 0.6rem;
    letter-spacing: 0.4em;
    text-transform: uppercase;
    color: var(--gold);
    margin-bottom: 2.5rem;
  }

  .countdown {
    display: flex;
    justify-content: center;
    gap: 1.5rem;
    flex-wrap: wrap;
  }

  .countdown-unit {
    display: flex;
    flex-direction: column;
    align-items: center;
    gap: 0.4rem;
  }

  .countdown-num {
    font-family: 'Cormorant Garamond', serif;
    font-size: clamp(3rem, 10vw, 4.5rem);
    font-weight: 300;
    color: var(--text);
    line-height: 1;
    min-width: 80px;
    border: 1px solid rgba(201,169,110,0.2);
    padding: 0.8rem 1rem;
    background: rgba(201,169,110,0.04);
  }

  .countdown-label {
    font-size: 0.55rem;
    letter-spacing: 0.3em;
    text-transform: uppercase;
    color: var(--muted);
  }

  /* ── DETAILS ── */
  .details-grid {
    display: grid;
    grid-template-columns: 1fr 1fr;
    gap: 1px;
    background: rgba(201,169,110,0.15);
    border: 1px solid rgba(201,169,110,0.15);
    margin: 2rem 0;
  }

  .detail-cell {
    background: var(--dark2);
    padding: 2rem 1.5rem;
    text-align: center;
  }

  .detail-icon {
    font-size: 1.4rem;
    margin-bottom: 0.75rem;
    filter: sepia(1) hue-rotate(10deg) saturate(0.8) brightness(1.2);
  }

  .detail-title {
    font-size: 0.6rem;
    letter-spacing: 0.3em;
    text-transform: uppercase;
    color: var(--gold);
    margin-bottom: 0.5rem;
  }

  .detail-value {
    font-family: 'Cormorant Garamond', serif;
    font-size: 1.15rem;
    font-weight: 400;
    color: var(--text);
    line-height: 1.4;
  }

  /* ── DRESS CODE ── */
  .dresscode-wrap {
    background: var(--dark3);
    border: 1px solid rgba(201,169,110,0.15);
    padding: 3rem 2rem;
    margin: 1rem 0;
  }

  .dresscode-title {
    font-family: 'Cormorant Garamond', serif;
    font-size: 2rem;
    font-weight: 300;
    letter-spacing: 0.3em;
    text-transform: uppercase;
    color: var(--gold-light);
    margin-bottom: 2.5rem;
  }

  .dresscode-col {
    text-align: left;
    margin-bottom: 2rem;
  }

  .dresscode-col-title {
    font-size: 0.6rem;
    letter-spacing: 0.3em;
    text-transform: uppercase;
    color: var(--gold);
    margin-bottom: 1rem;
    padding-bottom: 0.5rem;
    border-bottom: 1px solid rgba(201,169,110,0.2);
  }

  .dresscode-list {
    list-style: none;
    display: flex;
    flex-direction: column;
    gap: 0.6rem;
  }

  .dresscode-list li {
    font-size: 0.8rem;
    line-height: 1.6;
    color: #c0b0a8;
    padding-left: 1rem;
    position: relative;
  }

  .dresscode-list li::before {
    content: '';
    position: absolute;
    left: 0;
    top: 0.55em;
    width: 4px;
    height: 1px;
    background: var(--gold);
  }

  .dresscode-list.allowed li::before { background: #8ab87a; }
  .dresscode-list.forbidden li::before { background: #b87a7a; }

  /* ── MAP BUTTON ── */
  .map-btn {
    display: inline-block;
    margin-top: 2rem;
    padding: 1rem 2.5rem;
    border: 1px solid var(--gold);
    color: var(--gold);
    text-decoration: none;
    font-size: 0.65rem;
    letter-spacing: 0.35em;
    text-transform: uppercase;
    font-family: 'Montserrat', sans-serif;
    font-weight: 400;
    transition: background 0.3s, color 0.3s;
  }

  .map-btn:hover {
    background: var(--gold);
    color: var(--dark);
  }

  /* ── FOOTER ── */
  .footer {
    padding: 4rem 2rem;
    text-align: center;
    border-top: 1px solid rgba(201,169,110,0.1);
  }

  .footer-quote {
    font-family: 'Cormorant Garamond', serif;
    font-size: clamp(1.3rem, 4vw, 1.8rem);
    font-style: italic;
    font-weight: 300;
    color: var(--text);
    line-height: 1.6;
    max-width: 500px;
    margin: 0 auto 1.5rem;
  }

  .footer-sig {
    font-size: 0.6rem;
    letter-spacing: 0.3em;
    text-transform: uppercase;
    color: var(--muted);
  }

  /* ── ANIMATIONS ── */
  @keyframes fadeUp {
    from { opacity: 0; transform: translateY(20px); }
    to   { opacity: 1; transform: translateY(0); }
  }

  @keyframes scrollLine {
    0%   { transform: scaleY(0); transform-origin: top; }
    50%  { transform: scaleY(1); transform-origin: top; }
    51%  { transform: scaleY(1); transform-origin: bottom; }
    100% { transform: scaleY(0); transform-origin: bottom; }
  }

  .reveal {
    opacity: 0;
    transform: translateY(30px);
    transition: opacity 0.8s ease, transform 0.8s ease;
  }

  .reveal.visible {
    opacity: 1;
    transform: none;
  }

  @media (max-width: 480px) {
    .details-grid { grid-template-columns: 1fr; }
    .countdown-num { min-width: 60px; font-size: 2.8rem; padding: 0.6rem 0.8rem; }
  }
</style>
</head>
<body>

<canvas id="petals"></canvas>

<div class="page">

  <!-- HERO -->
  <section class="hero" style="position:relative;">
    <p class="hero-pre">Құрметті</p>
    <h1 class="hero-name">Айман</h1>
    <div class="hero-divider"></div>
    <p class="hero-date">9 Мамыр · 2026</p>
    <p class="hero-sub">Cloud9 Dine &amp; Wine · Астана</p>
    <div class="scroll-hint">
      <span>Төмен</span>
      <div class="scroll-line"></div>
    </div>
  </section>

  <!-- COUNTDOWN -->
  <section class="section reveal">
    <p class="section-label">Қалған уақыт</p>
    <div class="countdown">
      <div class="countdown-unit">
        <div class="countdown-num" id="cd-days">00</div>
        <div class="countdown-label">Күн</div>
      </div>
      <div class="countdown-unit">
        <div class="countdown-num" id="cd-hours">00</div>
        <div class="countdown-label">Сағат</div>
      </div>
      <div class="countdown-unit">
        <div class="countdown-num" id="cd-min">00</div>
        <div class="countdown-label">Минут</div>
      </div>
      <div class="countdown-unit">
        <div class="countdown-num" id="cd-sec">00</div>
        <div class="countdown-label">Секунд</div>
      </div>
    </div>
  </section>

  <!-- DETAILS -->
  <section class="section reveal" style="padding-top:0;">
    <p class="section-label">Мәліметтер</p>
    <div class="details-grid">
      <div class="detail-cell">
        <div class="detail-icon">🕯️</div>
        <div class="detail-title">Күні</div>
        <div class="detail-value">9 Мамыр<br>2026</div>
      </div>
      <div class="detail-cell">
        <div class="detail-icon">🍷</div>
        <div class="detail-title">Уақыты</div>
        <div class="detail-value">Кешкі 19:00</div>
      </div>
      <div class="detail-cell">
        <div class="detail-icon">🏨</div>
        <div class="detail-title">Мекенжай</div>
        <div class="detail-value">Hilton Astana<br>9-қабат</div>
      </div>
      <div class="detail-cell">
        <div class="detail-icon">📍</div>
        <div class="detail-title">Көше</div>
        <div class="detail-value">14 Heydar Aliyev St<br>Астана</div>
      </div>
    </div>
    <a href="https://maps.google.com/?q=Hilton+Astana+14+Heydar+Aliyev" target="_blank" class="map-btn">Картада ашу</a>
  </section>

  <!-- DRESS CODE -->
  <section class="section reveal" style="max-width:680px;">
    <div class="dresscode-wrap">
      <div class="dresscode-title">Dress Code</div>

      <div class="dresscode-col">
        <div class="dresscode-col-title" style="color:#b87a7a;">❌ &nbsp;Тыйым салынады</div>
        <ul class="dresscode-list forbidden">
          <li>Тәпішке, жағажай аяқ киімі және ашық аяқ киім</li>
          <li>Купальниктер мен шомылуға арналған шолақ шалбарлар</li>
          <li>Спорттық киім, жаттығуға арналған костюмдер, белсенді киім</li>
          <li>Халаттар мен spa-накидкалар</li>
          <li>Тамақ, сусын және тіскебасар алып кіру</li>
          <li>Үй жануарларымен кіру</li>
          <li>21 жасқа дейінгі қонақтарға қамқоршысыз кіруге болмайды</li>
        </ul>
      </div>

      <div class="dresscode-col" style="margin-bottom:0;">
        <div class="dresscode-col-title" style="color:#8ab87a;">✓ &nbsp;Рұқсат етіледі</div>
        <ul class="dresscode-list allowed">
          <li>Қалың матадан тігілген классикалық, қатаң пішінді шалбарлар (smart casual)</li>
          <li>Ашық балетка және классикалық үлгідегі аяқ киім</li>
          <li>21 жасқа дейінгі қонақтар тек қамқоршының ертуімен кіре алады</li>
        </ul>
      </div>
    </div>
  </section>

  <!-- FOOTER -->
  <footer class="footer reveal">
    <p class="footer-quote">P.S. Nursultan</p>
    <p class="footer-sig">Cloud9 Dine &amp; Wine · Hilton Astana</p>
  </footer>

</div>

<script>
/* Petal particles */
const canvas = document.getElementById('petals');
const ctx = canvas.getContext('2d');
let W, H, petals = [];

function resize() {
  W = canvas.width = window.innerWidth;
  H = canvas.height = window.innerHeight;
}
resize();
window.addEventListener('resize', resize);

function createPetal() {
  return {
    x: Math.random() * W,
    y: -10,
    r: Math.random() * 4 + 2,
    speed: Math.random() * 0.6 + 0.3,
    drift: Math.random() * 0.5 - 0.25,
    opacity: Math.random() * 0.5 + 0.2,
    rotation: Math.random() * Math.PI * 2,
    rotSpeed: (Math.random() - 0.5) * 0.04,
    hue: Math.random() > 0.5 ? '#C9A96E' : '#D4A0A0'
  };
}

for (let i = 0; i < 40; i++) {
  const p = createPetal();
  p.y = Math.random() * H;
  petals.push(p);
}

function drawPetal(p) {
  ctx.save();
  ctx.translate(p.x, p.y);
  ctx.rotate(p.rotation);
  ctx.globalAlpha = p.opacity;
  ctx.fillStyle = p.hue;
  ctx.beginPath();
  ctx.ellipse(0, 0, p.r * 2, p.r, 0, 0, Math.PI * 2);
  ctx.fill();
  ctx.restore();
}

function animate() {
  ctx.clearRect(0, 0, W, H);
  petals.forEach(p => {
    p.y += p.speed;
    p.x += p.drift;
    p.rotation += p.rotSpeed;
    if (p.y > H + 10) Object.assign(p, createPetal());
    drawPetal(p);
  });
  requestAnimationFrame(animate);
}
animate();

/* Countdown */
function updateCountdown() {
  const target = new Date('2026-05-09T19:00:00');
  const now = new Date();
  const diff = target - now;
  if (diff <= 0) {
    ['days','hours','min','sec'].forEach(u => document.getElementById('cd-'+u).textContent = '00');
    return;
  }
  const d = Math.floor(diff / 86400000);
  const h = Math.floor((diff % 86400000) / 3600000);
  const m = Math.floor((diff % 3600000) / 60000);
  const s = Math.floor((diff % 60000) / 1000);
  document.getElementById('cd-days').textContent  = String(d).padStart(2,'0');
  document.getElementById('cd-hours').textContent = String(h).padStart(2,'0');
  document.getElementById('cd-min').textContent   = String(m).padStart(2,'0');
  document.getElementById('cd-sec').textContent   = String(s).padStart(2,'0');
}
updateCountdown();
setInterval(updateCountdown, 1000);

/* Scroll reveal */
const observer = new IntersectionObserver(entries => {
  entries.forEach(e => { if (e.isIntersecting) e.target.classList.add('visible'); });
}, { threshold: 0.12 });
document.querySelectorAll('.reveal').forEach(el => observer.observe(el));
</script>

</body>
</html>
