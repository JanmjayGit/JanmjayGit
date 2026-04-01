<!DOCTYPE html>
<html lang="en">
<head>
<meta charset="UTF-8" />
<meta name="viewport" content="width=device-width, initial-scale=1.0"/>
<title>Janmjay Prajapati — Portfolio</title>
<link href="https://fonts.googleapis.com/css2?family=Syne:wght@400;700;800&family=DM+Mono:wght@300;400;500&family=Outfit:wght@300;400;600&display=swap" rel="stylesheet"/>
<style>
  :root {
    --bg: #060810;
    --surface: #0d1120;
    --accent1: #00f5c4;
    --accent2: #6366f1;
    --accent3: #f59e0b;
    --text: #e8eaf0;
    --muted: #6b7280;
    --border: rgba(99,102,241,0.18);
    --glow1: rgba(0,245,196,0.12);
    --glow2: rgba(99,102,241,0.12);
  }

  *, *::before, *::after { box-sizing: border-box; margin: 0; padding: 0; }

  html { scroll-behavior: smooth; }

  body {
    background: var(--bg);
    color: var(--text);
    font-family: 'Outfit', sans-serif;
    overflow-x: hidden;
    cursor: none;
  }

  /* Custom cursor */
  .cursor {
    position: fixed; width: 12px; height: 12px;
    background: var(--accent1); border-radius: 50%;
    pointer-events: none; z-index: 9999;
    transform: translate(-50%, -50%);
    transition: transform 0.1s ease, background 0.3s;
    mix-blend-mode: difference;
  }
  .cursor-ring {
    position: fixed; width: 36px; height: 36px;
    border: 1.5px solid var(--accent2); border-radius: 50%;
    pointer-events: none; z-index: 9998;
    transform: translate(-50%, -50%);
    transition: all 0.18s ease;
  }

  /* ── CANVAS BG ── */
  #bg-canvas {
    position: fixed; inset: 0; z-index: 0;
    pointer-events: none;
  }

  /* ── LAYOUT ── */
  .page { position: relative; z-index: 1; max-width: 960px; margin: 0 auto; padding: 0 28px 80px; }

  /* ── HERO ── */
  .hero {
    min-height: 100vh;
    display: flex; flex-direction: column;
    justify-content: center;
    padding-top: 60px;
    position: relative;
  }

  .hero-tag {
    font-family: 'DM Mono', monospace;
    font-size: 0.78rem; letter-spacing: 0.18em;
    color: var(--accent1);
    margin-bottom: 24px;
    opacity: 0; animation: fadeUp 0.6s 0.3s ease forwards;
    display: flex; align-items: center; gap: 10px;
  }
  .hero-tag::before {
    content: ''; display: inline-block;
    width: 32px; height: 1px; background: var(--accent1);
  }

  .hero-name {
    font-family: 'Syne', sans-serif;
    font-size: clamp(3.2rem, 9vw, 7.2rem);
    font-weight: 800;
    line-height: 0.95;
    letter-spacing: -0.03em;
    margin-bottom: 28px;
    opacity: 0; animation: fadeUp 0.7s 0.45s ease forwards;
    position: relative;
  }

  /* 3D Name effect */
  .hero-name .word {
    display: inline-block;
    position: relative;
    transition: transform 0.3s ease;
    transform-style: preserve-3d;
  }
  .hero-name .word:hover {
    transform: rotateX(-12deg) rotateY(6deg) scale(1.04);
    cursor: default;
  }

  .name-janmjay {
    display: block;
    background: linear-gradient(135deg, #fff 30%, var(--accent1) 70%);
    -webkit-background-clip: text; -webkit-text-fill-color: transparent;
    background-clip: text;
    filter: drop-shadow(0 0 40px rgba(0,245,196,0.25));
  }
  .name-prajapati {
    display: block;
    background: linear-gradient(135deg, var(--accent2) 10%, #a78bfa 60%, #c4b5fd 90%);
    -webkit-background-clip: text; -webkit-text-fill-color: transparent;
    background-clip: text;
    filter: drop-shadow(0 0 40px rgba(99,102,241,0.3));
  }

  /* Glitch on hover */
  .name-janmjay:hover {
    animation: glitch 0.4s ease;
  }
  @keyframes glitch {
    0%   { text-shadow: none; transform: none; }
    20%  { text-shadow: -3px 0 #f59e0b, 3px 0 #6366f1; transform: skewX(-4deg); }
    40%  { text-shadow: 3px 0 #00f5c4, -3px 0 #f59e0b; transform: skewX(2deg); }
    60%  { text-shadow: -2px 0 #6366f1; transform: skewX(-1deg); }
    80%  { text-shadow: 2px 0 #00f5c4; transform: none; }
    100% { text-shadow: none; }
  }

  .hero-role {
    font-family: 'DM Mono', monospace;
    font-size: 1.05rem; color: var(--muted);
    margin-bottom: 24px;
    opacity: 0; animation: fadeUp 0.7s 0.6s ease forwards;
    display: flex; align-items: center; gap: 8px; flex-wrap: wrap;
  }
  .role-pill {
    background: linear-gradient(135deg, var(--accent2) 0%, #818cf8 100%);
    color: #fff; font-family: 'Outfit', sans-serif;
    font-size: 0.8rem; font-weight: 600;
    padding: 3px 12px; border-radius: 100px;
    letter-spacing: 0.04em;
  }

  .hero-bio {
    max-width: 520px;
    font-size: 1.05rem; line-height: 1.75;
    color: #9ca3af;
    opacity: 0; animation: fadeUp 0.7s 0.75s ease forwards;
    margin-bottom: 40px;
  }
  .hero-bio strong { color: var(--accent1); font-weight: 600; }

  .hero-cta {
    display: flex; gap: 16px; flex-wrap: wrap;
    opacity: 0; animation: fadeUp 0.7s 0.9s ease forwards;
  }
  .btn {
    font-family: 'Outfit', sans-serif; font-weight: 600;
    font-size: 0.9rem; padding: 13px 28px;
    border-radius: 8px; border: none; cursor: pointer;
    text-decoration: none; display: inline-flex;
    align-items: center; gap: 8px;
    transition: transform 0.2s, box-shadow 0.2s;
    letter-spacing: 0.04em;
  }
  .btn-primary {
    background: linear-gradient(135deg, var(--accent1), #00c9a0);
    color: #060810;
  }
  .btn-primary:hover {
    transform: translateY(-2px);
    box-shadow: 0 12px 32px rgba(0,245,196,0.35);
  }
  .btn-outline {
    background: transparent;
    color: var(--text);
    border: 1.5px solid var(--border);
    backdrop-filter: blur(6px);
  }
  .btn-outline:hover {
    transform: translateY(-2px);
    border-color: var(--accent2);
    box-shadow: 0 8px 24px rgba(99,102,241,0.2);
  }

  /* Floating badge */
  .float-badge {
    position: absolute; right: 0; top: 50%;
    transform: translateY(-50%);
    width: 160px; height: 160px;
    display: flex; align-items: center; justify-content: center;
    animation: floatBadge 6s ease-in-out infinite, fadeUp 1s 1s ease forwards;
    opacity: 0;
  }
  .float-badge svg { width: 100%; animation: spinSlow 18s linear infinite; }
  .float-badge .badge-center {
    position: absolute; font-family: 'Syne', sans-serif;
    font-size: 2rem; font-weight: 800;
    background: linear-gradient(135deg, var(--accent1), var(--accent2));
    -webkit-background-clip: text; -webkit-text-fill-color: transparent;
    background-clip: text;
  }
  @keyframes floatBadge {
    0%,100% { transform: translateY(-50%) translateY(-8px); }
    50%      { transform: translateY(-50%) translateY(8px); }
  }
  @keyframes spinSlow { to { transform: rotate(360deg); } }

  /* Scroll indicator */
  .scroll-hint {
    position: absolute; bottom: 36px; left: 0;
    display: flex; align-items: center; gap: 10px;
    font-family: 'DM Mono', monospace; font-size: 0.72rem;
    color: var(--muted); letter-spacing: 0.12em;
    opacity: 0; animation: fadeUp 0.6s 1.4s ease forwards;
  }
  .scroll-line {
    width: 40px; height: 1px; background: var(--muted);
    position: relative; overflow: hidden;
  }
  .scroll-line::after {
    content: ''; position: absolute; inset: 0;
    background: var(--accent1);
    animation: scanline 2s ease-in-out infinite;
  }
  @keyframes scanline {
    0%   { transform: translateX(-100%); }
    100% { transform: translateX(100%); }
  }

  /* ── SECTION GENERIC ── */
  section { padding: 80px 0; border-top: 1px solid var(--border); }
  .section-label {
    font-family: 'DM Mono', monospace; font-size: 0.72rem;
    letter-spacing: 0.2em; color: var(--accent1); margin-bottom: 14px;
    display: flex; align-items: center; gap: 8px;
  }
  .section-label::after {
    content: ''; flex: 1; max-width: 80px; height: 1px; background: var(--border);
  }
  .section-title {
    font-family: 'Syne', sans-serif; font-size: clamp(1.8rem, 4vw, 2.8rem);
    font-weight: 800; letter-spacing: -0.02em; margin-bottom: 44px;
    line-height: 1.1;
  }

  /* ── TECH STACK ── */
  .stack-grid {
    display: grid;
    grid-template-columns: repeat(auto-fill, minmax(130px, 1fr));
    gap: 14px;
  }
  .stack-card {
    background: var(--surface);
    border: 1px solid var(--border);
    border-radius: 10px;
    padding: 18px 14px;
    text-align: center;
    position: relative; overflow: hidden;
    transition: transform 0.25s, border-color 0.25s, box-shadow 0.25s;
    cursor: default;
  }
  .stack-card::before {
    content: ''; position: absolute; inset: 0;
    background: linear-gradient(135deg, var(--glow1), var(--glow2));
    opacity: 0; transition: opacity 0.3s;
  }
  .stack-card:hover { transform: translateY(-5px) scale(1.03); border-color: var(--accent1); box-shadow: 0 16px 40px rgba(0,245,196,0.12); }
  .stack-card:hover::before { opacity: 1; }
  .stack-icon { font-size: 1.7rem; margin-bottom: 8px; display: block; }
  .stack-name { font-family: 'DM Mono', monospace; font-size: 0.73rem; color: var(--muted); letter-spacing: 0.06em; position: relative; }

  /* ── CURRENTLY ── */
  .current-card {
    background: var(--surface);
    border: 1px solid var(--border);
    border-radius: 16px;
    padding: 32px;
    display: flex; gap: 24px; align-items: flex-start;
    position: relative; overflow: hidden;
  }
  .current-card::after {
    content: ''; position: absolute;
    top: -60px; right: -60px;
    width: 200px; height: 200px;
    background: radial-gradient(circle, rgba(0,245,196,0.08), transparent 70%);
    pointer-events: none;
  }
  .current-dot {
    width: 12px; height: 12px;
    background: var(--accent1);
    border-radius: 50%; margin-top: 5px; flex-shrink: 0;
    box-shadow: 0 0 0 0 rgba(0,245,196,0.6);
    animation: pulse 2s ease-in-out infinite;
  }
  @keyframes pulse {
    0%,100% { box-shadow: 0 0 0 0 rgba(0,245,196,0.6); }
    50%      { box-shadow: 0 0 0 10px rgba(0,245,196,0); }
  }
  .current-label {
    font-family: 'DM Mono', monospace; font-size: 0.72rem;
    color: var(--accent1); letter-spacing: 0.12em; margin-bottom: 8px;
  }
  .current-title {
    font-family: 'Syne', sans-serif; font-size: 1.35rem;
    font-weight: 700; margin-bottom: 8px;
  }
  .current-desc { color: var(--muted); font-size: 0.95rem; line-height: 1.6; }

  /* ── SOCIALS ── */
  .socials-row { display: flex; gap: 16px; flex-wrap: wrap; }
  .social-link {
    display: inline-flex; align-items: center; gap: 10px;
    background: var(--surface); border: 1px solid var(--border);
    border-radius: 10px; padding: 14px 22px;
    font-family: 'DM Mono', monospace; font-size: 0.82rem;
    color: var(--muted); text-decoration: none;
    transition: all 0.22s;
  }
  .social-link:hover { color: var(--text); border-color: var(--accent2); transform: translateY(-3px); box-shadow: 0 10px 28px rgba(99,102,241,0.18); }
  .social-link svg { width: 18px; height: 18px; }

  /* ── STATS ── */
  .stats-row { display: grid; grid-template-columns: repeat(auto-fill, minmax(200px, 1fr)); gap: 16px; }
  .stat-card {
    background: var(--surface); border: 1px solid var(--border);
    border-radius: 12px; padding: 28px 24px;
    position: relative; overflow: hidden;
    transition: transform 0.22s, border-color 0.22s;
  }
  .stat-card:hover { transform: translateY(-4px); border-color: var(--accent2); }
  .stat-card img { width: 100%; border-radius: 8px; display: block; }
  .stat-card .stat-label { font-family: 'DM Mono', monospace; font-size: 0.72rem; color: var(--muted); letter-spacing: 0.12em; margin-bottom: 12px; }

  /* ── FOOTER ── */
  footer {
    border-top: 1px solid var(--border);
    padding: 40px 0;
    text-align: center;
    font-family: 'DM Mono', monospace; font-size: 0.75rem;
    color: var(--muted); letter-spacing: 0.08em;
  }
  footer span { color: var(--accent1); }

  /* ── ANIMATIONS ── */
  @keyframes fadeUp {
    from { opacity: 0; transform: translateY(24px); }
    to   { opacity: 1; transform: translateY(0); }
  }

  .reveal {
    opacity: 0; transform: translateY(30px);
    transition: opacity 0.6s ease, transform 0.6s ease;
  }
  .reveal.visible { opacity: 1; transform: translateY(0); }

  /* Typewriter cursor blink on role */
  .typed-text::after {
    content: '|'; color: var(--accent1);
    animation: blink 1s step-end infinite;
  }
  @keyframes blink { 50% { opacity: 0; } }

  /* ── RESPONSIVE ── */
  @media (max-width: 620px) {
    .float-badge { display: none; }
    .hero-name { font-size: clamp(2.6rem, 14vw, 4rem); }
  }
</style>
</head>
<body>

<!-- Custom cursor -->
<div class="cursor" id="cursor"></div>
<div class="cursor-ring" id="cursor-ring"></div>

<!-- Particle canvas -->
<canvas id="bg-canvas"></canvas>

<div class="page">

  <!-- ═══════════ HERO ═══════════ -->
  <section class="hero">

    <div class="hero-tag">FULL-STACK DEVELOPER</div>

    <h1 class="hero-name">
      <span class="word name-janmjay">Janmjay</span>
      <span class="word name-prajapati">Prajapati</span>
    </h1>

    <div class="hero-role">
      <span class="typed-text" id="typed"></span>
      <span class="role-pill">Open to Work</span>
    </div>

    <p class="hero-bio">
      🎓 CS Engineering student at <strong>Chandigarh University</strong> — passionate about
      building <strong>scalable backend systems</strong> and polished web applications
      with Java, Spring Boot &amp; React.js.
    </p>

    <div class="hero-cta">
      <a class="btn btn-primary" href="mailto:janmjayprajapati.dev@gmail.com">
        ✉ Hire Me
      </a>
      <a class="btn btn-outline" href="https://www.linkedin.com/in/janmjay-prajapati-b7b96524a/" target="_blank">
        LinkedIn ↗
      </a>
      <a class="btn btn-outline" href="https://github.com/JanmjayGit" target="_blank">
        GitHub ↗
      </a>
    </div>

    <!-- Floating 3D badge -->
    <div class="float-badge">
      <svg viewBox="0 0 160 160" fill="none" xmlns="http://www.w3.org/2000/svg">
        <defs>
          <path id="circle-path" d="M 80,80 m -60,0 a 60,60 0 1,1 120,0 a 60,60 0 1,1 -120,0"/>
        </defs>
        <circle cx="80" cy="80" r="72" stroke="rgba(99,102,241,0.25)" stroke-width="1"/>
        <circle cx="80" cy="80" r="60" stroke="rgba(0,245,196,0.15)" stroke-width="1" stroke-dasharray="4 8"/>
        <text font-family="DM Mono, monospace" font-size="11" fill="#6b7280" letter-spacing="4">
          <textPath href="#circle-path">JAVA • SPRING BOOT • REACT.JS • REST API • </textPath>
        </text>
      </svg>
      <span class="badge-center">JP</span>
    </div>

    <div class="scroll-hint">
      <div class="scroll-line"></div>
      SCROLL TO EXPLORE
    </div>

  </section>

  <!-- ═══════════ CURRENTLY BUILDING ═══════════ -->
  <section class="reveal">
    <div class="section-label">STATUS</div>
    <h2 class="section-title">Currently<br><em style="color:var(--accent1);font-style:normal;">Building</em></h2>
    <div class="current-card">
      <div class="current-dot"></div>
      <div>
        <div class="current-label">ACTIVE PROJECT</div>
        <div class="current-title">🗺 Smart Tourism Guide App</div>
        <div class="current-desc">
          A full-stack platform connecting travellers with intelligent, location-aware tourism insights.
          Built with Spring Boot microservices on the backend and a snappy React.js SPA on the front.
        </div>
      </div>
    </div>
  </section>

  <!-- ═══════════ TECH STACK ═══════════ -->
  <section class="reveal">
    <div class="section-label">ARSENAL</div>
    <h2 class="section-title">Tech<br><em style="color:var(--accent2);font-style:normal;">Stack</em></h2>
    <div class="stack-grid" id="stack-grid"></div>
  </section>

  <!-- ═══════════ GITHUB STATS ═══════════ -->
  <section class="reveal">
    <div class="section-label">ACTIVITY</div>
    <h2 class="section-title">GitHub<br><em style="color:var(--accent3);font-style:normal;">Stats</em></h2>
    <div class="stats-row">
      <div class="stat-card">
        <div class="stat-label">OVERVIEW</div>
        <img src="https://github-readme-stats.vercel.app/api?username=JanmjayGit&show_icons=true&theme=transparent&hide_border=true&title_color=00f5c4&icon_color=6366f1&text_color=e8eaf0" alt="GitHub Stats"/>
      </div>
      <div class="stat-card">
        <div class="stat-label">TOP LANGUAGES</div>
        <img src="https://github-readme-stats.vercel.app/api/top-langs/?username=JanmjayGit&layout=compact&theme=transparent&hide_border=true&title_color=00f5c4&text_color=e8eaf0" alt="Top Languages"/>
      </div>
      <div class="stat-card">
        <div class="stat-label">STREAK</div>
        <img src="https://streak-stats.demolab.com?user=JanmjayGit&theme=transparent&hide_border=true&ring=00f5c4&fire=f59e0b&currStreakLabel=6366f1&sideLabels=6b7280&dates=6b7280&stroke=0d1120" alt="Streak"/>
      </div>
    </div>
  </section>

  <!-- ═══════════ CONNECT ═══════════ -->
  <section class="reveal">
    <div class="section-label">REACH OUT</div>
    <h2 class="section-title">Let's<br><em style="color:var(--accent1);font-style:normal;">Connect</em></h2>
    <div class="socials-row">
      <a class="social-link" href="mailto:janmjayprajapati.dev@gmail.com">
        <svg viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2"><rect x="2" y="4" width="20" height="16" rx="2"/><path d="m2 7 10 7 10-7"/></svg>
        Email
      </a>
      <a class="social-link" href="https://www.linkedin.com/in/janmjay-prajapati-b7b96524a/" target="_blank">
        <svg viewBox="0 0 24 24" fill="currentColor"><path d="M16 8a6 6 0 0 1 6 6v7h-4v-7a2 2 0 0 0-2-2 2 2 0 0 0-2 2v7h-4v-7a6 6 0 0 1 6-6z"/><rect x="2" y="9" width="4" height="12"/><circle cx="4" cy="4" r="2"/></svg>
        LinkedIn
      </a>
      <a class="social-link" href="https://github.com/JanmjayGit" target="_blank">
        <svg viewBox="0 0 24 24" fill="currentColor"><path d="M9 19c-5 1.5-5-2.5-7-3m14 6v-3.87a3.37 3.37 0 0 0-.94-2.61c3.14-.35 6.44-1.54 6.44-7A5.44 5.44 0 0 0 20 4.77 5.07 5.07 0 0 0 19.91 1S18.73.65 16 2.48a13.38 13.38 0 0 0-7 0C6.27.65 5.09 1 5.09 1A5.07 5.07 0 0 0 5 4.77a5.44 5.44 0 0 0-1.5 3.78c0 5.42 3.3 6.61 6.44 7A3.37 3.37 0 0 0 9 18.13V22"/></svg>
        GitHub
      </a>
      <a class="social-link" href="https://instagram.com/hey_janmjay" target="_blank">
        <svg viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2"><rect x="2" y="2" width="20" height="20" rx="5"/><path d="M16 11.37A4 4 0 1 1 12.63 8 4 4 0 0 1 16 11.37z"/><line x1="17.5" y1="6.5" x2="17.51" y2="6.5"/></svg>
        Instagram
      </a>
    </div>
  </section>

</div>

<!-- ═══════════ FOOTER ═══════════ -->
<footer>
  Crafted with <span>♥</span> by Janmjay Prajapati · CS @ Chandigarh University
</footer>

<script>
/* ── Cursor ── */
const cursor = document.getElementById('cursor');
const ring = document.getElementById('cursor-ring');
let mx = 0, my = 0, rx = 0, ry = 0;
document.addEventListener('mousemove', e => { mx = e.clientX; my = e.clientY; });
(function animCursor(){
  rx += (mx - rx) * 0.14;
  ry += (my - ry) * 0.14;
  cursor.style.left = mx + 'px'; cursor.style.top = my + 'px';
  ring.style.left = rx + 'px'; ring.style.top = ry + 'px';
  requestAnimationFrame(animCursor);
})();
document.querySelectorAll('a,button,.stack-card').forEach(el => {
  el.addEventListener('mouseenter', () => { cursor.style.transform = 'translate(-50%,-50%) scale(2)'; ring.style.transform = 'translate(-50%,-50%) scale(1.6)'; });
  el.addEventListener('mouseleave', () => { cursor.style.transform = 'translate(-50%,-50%) scale(1)'; ring.style.transform = 'translate(-50%,-50%) scale(1)'; });
});

/* ── Particle canvas ── */
const canvas = document.getElementById('bg-canvas');
const ctx = canvas.getContext('2d');
let W, H, particles = [];
function resize(){ W = canvas.width = window.innerWidth; H = canvas.height = window.innerHeight; }
resize(); window.addEventListener('resize', resize);

class Particle {
  constructor(){
    this.x = Math.random()*W; this.y = Math.random()*H;
    this.r = Math.random()*1.4+0.3;
    this.dx = (Math.random()-0.5)*0.3; this.dy = (Math.random()-0.5)*0.3;
    this.a = Math.random()*0.5+0.08;
    this.color = Math.random() > 0.5 ? '0,245,196' : '99,102,241';
  }
  update(){
    this.x += this.dx; this.y += this.dy;
    if(this.x<0||this.x>W) this.dx*=-1;
    if(this.y<0||this.y>H) this.dy*=-1;
  }
  draw(){
    ctx.beginPath();
    ctx.arc(this.x, this.y, this.r, 0, Math.PI*2);
    ctx.fillStyle = `rgba(${this.color},${this.a})`;
    ctx.fill();
  }
}
for(let i=0;i<110;i++) particles.push(new Particle());

function connectParticles(){
  for(let i=0;i<particles.length;i++){
    for(let j=i+1;j<particles.length;j++){
      const dx = particles[i].x - particles[j].x;
      const dy = particles[i].y - particles[j].y;
      const dist = Math.sqrt(dx*dx+dy*dy);
      if(dist < 120){
        ctx.beginPath();
        ctx.strokeStyle = `rgba(99,102,241,${0.08*(1-dist/120)})`;
        ctx.lineWidth = 0.5;
        ctx.moveTo(particles[i].x, particles[i].y);
        ctx.lineTo(particles[j].x, particles[j].y);
        ctx.stroke();
      }
    }
  }
}
(function loop(){
  ctx.clearRect(0,0,W,H);
  particles.forEach(p=>{ p.update(); p.draw(); });
  connectParticles();
  requestAnimationFrame(loop);
})();

/* ── Typewriter ── */
const roles = ['Java Full-Stack Developer', 'Spring Boot Engineer', 'React.js Builder', 'System Design Learner'];
let ri=0, ci=0, del=false;
const typed = document.getElementById('typed');
function typewriter(){
  const target = roles[ri];
  typed.textContent = del ? target.slice(0,ci--) : target.slice(0,ci++);
  if(!del && ci>target.length){ del=true; setTimeout(typewriter,1400); return; }
  if(del && ci<0){ del=false; ri=(ri+1)%roles.length; ci=0; setTimeout(typewriter,400); return; }
  setTimeout(typewriter, del?45:80);
}
typewriter();

/* ── Tech stack data ── */
const stack = [
  { icon:'☕', name:'Java' },
  { icon:'🌱', name:'Spring Boot' },
  { icon:'⚛️', name:'React.js' },
  { icon:'🔌', name:'REST APIs' },
  { icon:'🐬', name:'MySQL' },
  { icon:'🍃', name:'MongoDB' },
  { icon:'🐘', name:'PostgreSQL' },
  { icon:'⚡', name:'Redis' },
  { icon:'🔷', name:'TypeScript' },
  { icon:'🌐', name:'JavaScript' },
  { icon:'🎨', name:'TailwindCSS' },
  { icon:'⚙️', name:'Hibernate' },
  { icon:'📦', name:'Maven' },
  { icon:'🐳', name:'Docker' },
  { icon:'🌩', name:'Netlify' },
  { icon:'🔐', name:'JWT' },
  { icon:'🗄', name:'Supabase' },
  { icon:'🚀', name:'Vite' },
];
const grid = document.getElementById('stack-grid');
stack.forEach((s, i) => {
  const d = document.createElement('div');
  d.className = 'stack-card';
  d.style.animationDelay = `${i*0.04}s`;
  d.innerHTML = `<span class="stack-icon">${s.icon}</span><div class="stack-name">${s.name}</div>`;
  grid.appendChild(d);
});

/* ── Scroll reveal ── */
const reveals = document.querySelectorAll('.reveal');
const obs = new IntersectionObserver(entries => {
  entries.forEach(e => { if(e.isIntersecting){ e.target.classList.add('visible'); obs.unobserve(e.target); } });
}, { threshold: 0.12 });
reveals.forEach(r => obs.observe(r));
</script>
</body>
</html>
