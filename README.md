<!DOCTYPE html>
<html lang="en">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>Ahmed Nasir — Full-Stack Architect</title>
<meta name="description" content="Ahmed Nasir — Full-Stack Developer, Mobile Engineer, ML/AI Enthusiast. Building cross-platform apps with React Native & Next.js.">
<meta property="og:title" content="Ahmed Nasir — Full-Stack Architect">
<meta property="og:description" content="Full-Stack Developer · Mobile Engineer · ML/AI Enthusiast">
<meta property="og:type" content="website">
<link rel="preconnect" href="https://fonts.googleapis.com">
<link rel="preconnect" href="https://fonts.gstatic.com" crossorigin>
<link href="https://fonts.googleapis.com/css2?family=Space+Mono:ital,wght@0,400;0,700;1,400&family=Syne:wght@400;700;800&display=swap" rel="stylesheet">
<style>
  *, *::before, *::after { box-sizing: border-box; margin: 0; padding: 0; }

  :root {
    --pink: #F72585;
    --blue: #0A66C2;
    --green: #28c840;
    --bg: #000000;
    --bg2: #070707;
    --bg3: #0a0a0a;
    --border: #1a1a1a;
    --border2: #111111;
    --text: #e8e8e8;
    --muted: #444444;
    --dim: #222222;
  }

  html { scroll-behavior: smooth; }

  body {
    font-family: 'Space Mono', monospace;
    background: var(--bg);
    color: var(--text);
    min-height: 100vh;
    overflow-x: hidden;
    cursor: crosshair;
  }

  /* SCROLLBAR */
  ::-webkit-scrollbar { width: 4px; }
  ::-webkit-scrollbar-track { background: var(--bg); }
  ::-webkit-scrollbar-thumb { background: var(--pink); }

  /* CANVAS BACKGROUND */
  #bg {
    position: fixed;
    top: 0; left: 0;
    width: 100%; height: 100%;
    z-index: 0;
    opacity: 0.4;
    pointer-events: none;
  }

  /* SCANLINES */
  .scanlines {
    position: fixed;
    top: 0; left: 0;
    width: 100%; height: 100%;
    background: repeating-linear-gradient(
      0deg,
      transparent,
      transparent 2px,
      rgba(0,0,0,0.04) 2px,
      rgba(0,0,0,0.04) 4px
    );
    pointer-events: none;
    z-index: 1;
  }

  /* NOISE OVERLAY */
  .noise {
    position: fixed;
    top: -50%; left: -50%;
    width: 200%; height: 200%;
    opacity: 0.018;
    z-index: 1;
    pointer-events: none;
    background-image: url("data:image/svg+xml,%3Csvg viewBox='0 0 256 256' xmlns='http://www.w3.org/2000/svg'%3E%3Cfilter id='noise'%3E%3CfeTurbulence type='fractalNoise' baseFrequency='0.9' numOctaves='4' stitchTiles='stitch'/%3E%3C/filter%3E%3Crect width='100%25' height='100%25' filter='url(%23noise)'/%3E%3C/svg%3E");
    animation: noise 0.5s steps(1) infinite;
  }
  @keyframes noise {
    0%   { transform: translate(0,0) }
    10%  { transform: translate(-2%,-3%) }
    20%  { transform: translate(3%,1%) }
    30%  { transform: translate(-1%,4%) }
    40%  { transform: translate(4%,-2%) }
    50%  { transform: translate(-3%,3%) }
    60%  { transform: translate(2%,-4%) }
    70%  { transform: translate(-4%,1%) }
    80%  { transform: translate(1%,3%) }
    90%  { transform: translate(3%,-1%) }
    100% { transform: translate(-2%,2%) }
  }

  /* MAIN LAYOUT */
  .page {
    position: relative;
    z-index: 2;
    max-width: 860px;
    margin: 0 auto;
    padding: 0 1.5rem 6rem;
  }

  /* NAV */
  nav {
    position: fixed;
    top: 0; left: 0; right: 0;
    z-index: 100;
    display: flex;
    align-items: center;
    justify-content: space-between;
    padding: 1rem 2rem;
    background: rgba(0,0,0,0.85);
    backdrop-filter: blur(12px);
    border-bottom: 1px solid var(--border2);
  }
  .nav-logo {
    font-family: 'Syne', sans-serif;
    font-weight: 800;
    font-size: 1rem;
    letter-spacing: 0.05em;
    color: var(--text);
    text-decoration: none;
  }
  .nav-logo span { color: var(--pink); }
  .nav-links {
    display: flex;
    gap: 2rem;
    list-style: none;
  }
  .nav-links a {
    font-size: 11px;
    letter-spacing: 0.15em;
    color: var(--muted);
    text-decoration: none;
    text-transform: uppercase;
    transition: color 0.2s;
  }
  .nav-links a:hover { color: var(--pink); }

  /* HERO */
  .hero {
    padding: 9rem 0 4rem;
    text-align: center;
    position: relative;
  }

  .hero-eyebrow {
    font-size: 11px;
    letter-spacing: 0.25em;
    color: var(--pink);
    text-transform: uppercase;
    margin-bottom: 1.5rem;
    display: flex;
    align-items: center;
    justify-content: center;
    gap: 12px;
  }
  .hero-eyebrow::before, .hero-eyebrow::after {
    content: '';
    flex: 1;
    max-width: 80px;
    height: 1px;
    background: linear-gradient(90deg, transparent, var(--pink));
  }
  .hero-eyebrow::after { background: linear-gradient(90deg, var(--pink), transparent); }

  .hero-name {
    font-family: 'Syne', sans-serif;
    font-size: clamp(3.5rem, 12vw, 7rem);
    font-weight: 800;
    line-height: 0.95;
    letter-spacing: -0.04em;
    margin-bottom: 0.6rem;
    position: relative;
    display: inline-block;
  }
  .hero-name .grad {
    background: linear-gradient(135deg, #ffffff 0%, #F72585 45%, #0A66C2 100%);
    -webkit-background-clip: text;
    -webkit-text-fill-color: transparent;
    background-clip: text;
  }
  .hero-surname {
    font-family: 'Syne', sans-serif;
    font-size: clamp(1.2rem, 4vw, 2.2rem);
    font-weight: 800;
    letter-spacing: 0.5em;
    color: var(--dim);
    text-transform: uppercase;
    margin-bottom: 1.5rem;
  }

  .hero-role {
    font-size: 13px;
    color: var(--muted);
    letter-spacing: 0.12em;
    margin-bottom: 2.5rem;
    line-height: 2;
  }
  .hero-role .accent { color: var(--pink); }

  .status-row {
    display: flex;
    gap: 8px;
    justify-content: center;
    flex-wrap: wrap;
    margin-bottom: 3rem;
  }
  .pill {
    padding: 6px 16px;
    border-radius: 2px;
    font-size: 10px;
    letter-spacing: 0.12em;
    text-transform: uppercase;
    display: flex;
    align-items: center;
    gap: 7px;
    border: 1px solid;
    transition: all 0.2s;
  }
  .pill:hover { transform: translateY(-1px); }
  .pill-pink { border-color: var(--pink); color: var(--pink); background: rgba(247,37,133,0.05); }
  .pill-blue { border-color: var(--blue); color: var(--blue); background: rgba(10,102,194,0.05); }
  .pill-green { border-color: var(--green); color: var(--green); background: rgba(40,200,64,0.05); }
  .pill-dot {
    width: 5px; height: 5px;
    border-radius: 50%;
    background: currentColor;
    animation: blink 1.5s ease-in-out infinite;
  }

  .hero-cta {
    display: flex;
    gap: 12px;
    justify-content: center;
    flex-wrap: wrap;
  }
  .btn {
    padding: 10px 28px;
    font-family: 'Space Mono', monospace;
    font-size: 11px;
    letter-spacing: 0.15em;
    text-transform: uppercase;
    text-decoration: none;
    border-radius: 2px;
    transition: all 0.2s;
    display: inline-flex;
    align-items: center;
    gap: 8px;
  }
  .btn-primary {
    background: var(--pink);
    color: #fff;
    border: 1px solid var(--pink);
  }
  .btn-primary:hover { background: transparent; color: var(--pink); }
  .btn-outline {
    background: transparent;
    color: var(--muted);
    border: 1px solid var(--border);
  }
  .btn-outline:hover { border-color: var(--muted); color: var(--text); }

  /* GLITCH */
  .glitch {
    position: relative;
    display: inline-block;
  }
  .glitch::before, .glitch::after {
    content: attr(data-text);
    position: absolute;
    top: 0; left: 0;
    width: 100%; height: 100%;
    background: linear-gradient(135deg, #ffffff 0%, #F72585 45%, #0A66C2 100%);
    -webkit-background-clip: text;
    -webkit-text-fill-color: transparent;
    background-clip: text;
  }
  .glitch::before {
    animation: glitch1 4s infinite;
    clip-path: polygon(0 15%, 100% 15%, 100% 35%, 0 35%);
  }
  .glitch::after {
    animation: glitch2 4s infinite;
    clip-path: polygon(0 65%, 100% 65%, 100% 80%, 0 80%);
  }

  /* DIVIDER */
  .divider {
    height: 1px;
    background: var(--border2);
    margin: 0;
  }

  /* SECTION */
  .section {
    padding: 4rem 0;
    border-bottom: 1px solid var(--border2);
  }
  .section:last-child { border-bottom: none; }

  .sec-header {
    display: flex;
    align-items: center;
    gap: 16px;
    margin-bottom: 2.5rem;
  }
  .sec-num {
    font-size: 10px;
    color: var(--pink);
    letter-spacing: 0.2em;
    flex-shrink: 0;
  }
  .sec-title {
    font-family: 'Syne', sans-serif;
    font-size: 1rem;
    font-weight: 700;
    letter-spacing: 0.15em;
    text-transform: uppercase;
    flex-shrink: 0;
  }
  .sec-line {
    flex: 1;
    height: 1px;
    background: var(--border2);
  }

  /* CODE BLOCK */
  .code-block {
    background: var(--bg2);
    border: 1px solid var(--border);
    border-radius: 3px;
    overflow: hidden;
    margin-bottom: 2rem;
  }
  .code-bar {
    background: var(--bg3);
    padding: 9px 16px;
    display: flex;
    align-items: center;
    gap: 8px;
    border-bottom: 1px solid var(--border2);
  }
  .dot { width: 10px; height: 10px; border-radius: 50%; }
  .dot-r { background: #ff5f57; }
  .dot-y { background: #febc2e; }
  .dot-g { background: #28c840; }
  .code-filename { font-size: 10px; color: var(--muted); margin-left: auto; letter-spacing: 0.08em; }
  .code-body {
    padding: 1.5rem 1.8rem;
    font-size: 13px;
    line-height: 2;
    overflow-x: auto;
  }
  .kw { color: var(--pink); }
  .str { color: #98d8a8; }
  .prop { color: #79b8ff; }
  .num { color: #d2a8ff; }
  .comment { color: #2e2e2e; font-style: italic; }
  .obj { color: var(--text); }

  /* STATS */
  .stats-grid {
    display: grid;
    grid-template-columns: repeat(3, 1fr);
    gap: 1px;
    background: var(--border2);
    border: 1px solid var(--border2);
    margin-bottom: 1px;
  }
  .stat-card {
    background: var(--bg);
    padding: 1.8rem 1rem;
    text-align: center;
    transition: background 0.2s;
  }
  .stat-card:hover { background: var(--bg2); }
  .stat-num {
    font-family: 'Syne', sans-serif;
    font-size: 2.4rem;
    font-weight: 800;
    background: linear-gradient(135deg, var(--pink), var(--blue));
    -webkit-background-clip: text;
    -webkit-text-fill-color: transparent;
    background-clip: text;
    line-height: 1;
    margin-bottom: 8px;
  }
  .stat-label {
    font-size: 9px;
    color: var(--muted);
    letter-spacing: 0.18em;
    text-transform: uppercase;
  }

  /* SKILL GRID */
  .skill-grid {
    display: grid;
    grid-template-columns: repeat(auto-fill, minmax(150px, 1fr));
    gap: 1px;
    background: var(--border2);
    border: 1px solid var(--border2);
  }
  .skill-item {
    background: var(--bg);
    padding: 1.2rem 1rem;
    display: flex;
    flex-direction: column;
    gap: 8px;
    transition: background 0.15s;
    cursor: default;
  }
  .skill-item:hover { background: var(--bg2); }
  .skill-cat {
    font-size: 9px;
    color: var(--muted);
    letter-spacing: 0.18em;
    text-transform: uppercase;
  }
  .skill-name {
    font-size: 14px;
    font-weight: 700;
    color: var(--text);
  }
  .skill-bar-bg {
    height: 2px;
    background: var(--border2);
  }
  .skill-bar-fill {
    height: 2px;
    background: linear-gradient(90deg, var(--pink), var(--blue));
    width: 0;
    transition: width 1.2s cubic-bezier(0.16, 1, 0.3, 1);
  }

  /* LANG BAR */
  .lang-bar {
    display: flex;
    height: 8px;
    background: var(--bg3);
    border: 1px solid var(--border2);
    overflow: hidden;
    margin-bottom: 14px;
  }
  .lang-seg {
    height: 100%;
    width: 0;
    transition: width 1.2s cubic-bezier(0.16, 1, 0.3, 1);
  }
  .lang-legend {
    display: flex;
    flex-wrap: wrap;
    gap: 16px;
  }
  .lang-item {
    display: flex;
    align-items: center;
    gap: 7px;
    font-size: 11px;
    color: var(--muted);
  }
  .lang-dot {
    width: 8px; height: 8px;
    border-radius: 0;
  }

  /* TERMINAL */
  .terminal {
    background: var(--bg2);
    border: 1px solid var(--border);
    border-radius: 3px;
    overflow: hidden;
  }
  .term-header {
    background: var(--bg3);
    padding: 8px 16px;
    display: flex;
    align-items: center;
    gap: 8px;
    border-bottom: 1px solid var(--border2);
  }
  .term-title {
    font-size: 10px;
    color: var(--muted);
    margin-left: 4px;
    letter-spacing: 0.08em;
  }
  .term-title span { color: var(--pink); }
  .term-body {
    padding: 1.5rem 1.8rem;
    font-size: 13px;
    line-height: 2.2;
  }
  .t-prompt { color: var(--pink); }
  .t-path { color: var(--blue); }
  .t-cmd { color: var(--text); }
  .t-out { color: #383838; font-style: italic; }
  .t-success { color: var(--green); }
  .cursor {
    display: inline-block;
    width: 8px;
    height: 14px;
    background: var(--pink);
    margin-left: 4px;
    vertical-align: -3px;
    animation: blink 1s step-end infinite;
  }

  /* FOCUS CARD */
  .focus-card {
    border: 1px solid var(--border);
    padding: 1.5rem 1.8rem;
    background: var(--bg2);
    display: flex;
    gap: 18px;
    align-items: flex-start;
  }
  .focus-icon { font-size: 1.8rem; flex-shrink: 0; margin-top: 2px; }
  .focus-label {
    font-size: 9px;
    letter-spacing: 0.2em;
    color: var(--pink);
    text-transform: uppercase;
    margin-bottom: 6px;
  }
  .focus-text {
    font-size: 13px;
    color: #555;
    line-height: 1.9;
  }
  .focus-text strong { color: var(--text); font-weight: 700; }

  /* CONNECT GRID */
  .connect-grid {
    display: grid;
    grid-template-columns: repeat(5, 1fr);
    gap: 1px;
    background: var(--border2);
    border: 1px solid var(--border2);
  }
  .connect-item {
    background: var(--bg);
    padding: 1.5rem 1rem;
    text-align: center;
    text-decoration: none;
    color: var(--muted);
    font-size: 10px;
    letter-spacing: 0.12em;
    text-transform: uppercase;
    display: flex;
    flex-direction: column;
    align-items: center;
    gap: 8px;
    transition: all 0.2s;
  }
  .connect-item:hover { background: var(--bg2); color: var(--text); }
  .connect-item:hover .connect-icon { transform: translateY(-3px); }
  .connect-icon {
    font-size: 22px;
    transition: transform 0.2s;
    display: block;
  }

  /* FOOTER QUOTE */
  .footer-quote {
    padding: 5rem 0 3rem;
    text-align: center;
    border-top: 1px solid var(--border2);
  }
  .quote-big {
    font-family: 'Syne', sans-serif;
    font-size: clamp(1.8rem, 6vw, 3.5rem);
    font-weight: 800;
    line-height: 1.2;
    letter-spacing: -0.02em;
    color: var(--dim);
    margin-bottom: 0.3rem;
  }
  .quote-big .hi {
    background: linear-gradient(90deg, var(--pink), var(--blue));
    -webkit-background-clip: text;
    -webkit-text-fill-color: transparent;
    background-clip: text;
  }
  .footer-meta {
    font-size: 10px;
    color: #1e1e1e;
    letter-spacing: 0.2em;
    margin-top: 2rem;
    text-transform: uppercase;
  }

  /* ANIMATIONS */
  @keyframes glitch1 {
    0%, 88%, 100% { transform: translate(0); opacity: 1; }
    90% { transform: translate(-4px, 1px); opacity: 0.8; }
    92% { transform: translate(4px, -1px); opacity: 0.8; }
    94% { transform: translate(-2px, 2px); opacity: 0.9; }
    96% { transform: translate(0); opacity: 1; }
  }
  @keyframes glitch2 {
    0%, 83%, 100% { transform: translate(0); opacity: 1; }
    85% { transform: translate(4px, -2px); opacity: 0.8; }
    87% { transform: translate(-4px, 1px); opacity: 0.8; }
    89% { transform: translate(2px, -2px); opacity: 0.9; }
    91% { transform: translate(0); opacity: 1; }
  }
  @keyframes blink { 0%, 100% { opacity: 1; } 50% { opacity: 0; } }
  @keyframes fadeUp {
    from { opacity: 0; transform: translateY(24px); }
    to   { opacity: 1; transform: translateY(0); }
  }
  @keyframes fadeIn {
    from { opacity: 0; }
    to   { opacity: 1; }
  }

  .fade-up { opacity: 0; animation: fadeUp 0.7s ease forwards; }
  .delay-1 { animation-delay: 0.1s; }
  .delay-2 { animation-delay: 0.2s; }
  .delay-3 { animation-delay: 0.3s; }
  .delay-4 { animation-delay: 0.4s; }
  .delay-5 { animation-delay: 0.5s; }

  /* RESPONSIVE */
  @media (max-width: 640px) {
    .stats-grid { grid-template-columns: repeat(2, 1fr); }
    .connect-grid { grid-template-columns: repeat(3, 1fr); }
    nav .nav-links { display: none; }
    .hero { padding: 7rem 0 3rem; }
  }
  @media (max-width: 400px) {
    .connect-grid { grid-template-columns: repeat(2, 1fr); }
  }
</style>
</head>
<body>

<canvas id="bg"></canvas>
<div class="scanlines"></div>
<div class="noise"></div>

<!-- NAV -->
<nav>
  <a href="#" class="nav-logo">AN<span>.</span></a>
  <ul class="nav-links">
    <li><a href="#about">About</a></li>
    <li><a href="#skills">Skills</a></li>
    <li><a href="#terminal">Terminal</a></li>
    <li><a href="#connect">Connect</a></li>
  </ul>
</nav>

<div class="page">

  <!-- HERO -->
  <section class="hero" id="about">
    <div class="hero-eyebrow fade-up">⟨ README.md ⟩</div>
    <h1 class="fade-up delay-1">
      <div class="hero-name">
        <span class="grad glitch" data-text="AHMED">AHMED</span>
      </div>
      <div class="hero-surname">Nasir</div>
    </h1>
    <p class="hero-role fade-up delay-2">
      Full-Stack Architect &nbsp;·&nbsp; Mobile Engineer &nbsp;·&nbsp; <span class="accent">ML/AI Enthusiast</span><br>
      Lahore, PK &nbsp;·&nbsp; Building things that make people say <span class="accent">wow</span>
    </p>
    <div class="status-row fade-up delay-3">
      <div class="pill pill-pink"><span class="pill-dot"></span>Available for Projects</div>
      <div class="pill pill-blue"><span class="pill-dot" style="animation-delay:0.5s"></span>React Native + Next.js</div>
      <div class="pill pill-green"><span class="pill-dot" style="animation-delay:1s"></span>Brain.mode = ON</div>
    </div>
    <div class="hero-cta fade-up delay-4">
      <a href="https://github.com/AhmedNasir7" class="btn btn-primary">⬡ View GitHub</a>
      <a href="mailto:your-email@example.com" class="btn btn-outline">✉ Get In Touch</a>
    </div>
  </section>

  <div class="divider"></div>

  <!-- ABOUT CODE -->
  <section class="section">
    <div class="sec-header">
      <span class="sec-num">// 01</span>
      <span class="sec-title">Identity</span>
      <div class="sec-line"></div>
    </div>
    <div class="code-block">
      <div class="code-bar">
        <div class="dot dot-r"></div>
        <div class="dot dot-y"></div>
        <div class="dot dot-g"></div>
        <span class="code-filename">ahmed.config.ts</span>
      </div>
      <div class="code-body">
        <div><span class="kw">const</span> <span class="obj">ahmed</span> <span class="kw">=</span> {</div>
        <div>&nbsp;&nbsp;<span class="prop">codename</span>: <span class="str">"Full-Stack Architect"</span>,</div>
        <div>&nbsp;&nbsp;<span class="prop">stack</span>: {</div>
        <div>&nbsp;&nbsp;&nbsp;&nbsp;<span class="prop">system</span>: [<span class="str">"C++"</span>, <span class="str">"C"</span>, <span class="str">"Assembly"</span>, <span class="str">"Java"</span>],</div>
        <div>&nbsp;&nbsp;&nbsp;&nbsp;<span class="prop">web</span>: [<span class="str">"React"</span>, <span class="str">"Next.js 14"</span>, <span class="str">"TypeScript"</span>, <span class="str">"Tailwind"</span>],</div>
        <div>&nbsp;&nbsp;&nbsp;&nbsp;<span class="prop">mobile</span>: [<span class="str">"React Native"</span>, <span class="str">"Expo"</span>, <span class="str">"Kotlin"</span>, <span class="str">"Jetpack Compose"</span>],</div>
        <div>&nbsp;&nbsp;&nbsp;&nbsp;<span class="prop">ai</span>: [<span class="str">"TensorFlow"</span>, <span class="str">"PyTorch"</span>, <span class="str">"Scikit-learn"</span>, <span class="str">"Pandas"</span>],</div>
        <div>&nbsp;&nbsp;&nbsp;&nbsp;<span class="prop">backend</span>: [<span class="str">"Node.js"</span>, <span class="str">"Supabase"</span>, <span class="str">"PostgreSQL"</span>, <span class="str">"Firebase"</span>],</div>
        <div>&nbsp;&nbsp;},</div>
        <div>&nbsp;&nbsp;<span class="prop">currentMission</span>: <span class="str">"Cross-platform apps that feel like magic"</span>,</div>
        <div>&nbsp;&nbsp;<span class="prop">learning</span>: [<span class="str">"Advanced ML"</span>, <span class="str">"iOS Swift"</span>, <span class="str">"GraphQL"</span>, <span class="str">"AWS"</span>],</div>
        <div>&nbsp;&nbsp;<span class="prop">caffeine</span>: <span class="num">Infinity</span>, <span class="comment">// ☕ required to compile</span></div>
        <div>&nbsp;&nbsp;<span class="prop">philosophy</span>: <span class="str">"Code is poetry written in logic"</span>,</div>
        <div>&nbsp;&nbsp;<span class="prop">funFact</span>: <span class="str">"I speak binary, but prefer coffee"</span></div>
        <div>}</div>
      </div>
    </div>

    <div class="focus-card">
      <div class="focus-icon">⚡</div>
      <div>
        <div class="focus-label">Current Focus</div>
        <div class="focus-text">
          Building <strong>cross-platform apps</strong> with React Native & Next.js 14 — obsessed with making mobile feel like magic.
          Next: diving deep into <strong>Advanced ML Algorithms</strong>, <strong>iOS Swift</strong>, and <strong>AWS</strong>.
        </div>
      </div>
    </div>
  </section>

  <!-- STATS -->
  <section class="section" id="skills">
    <div class="sec-header">
      <span class="sec-num">// 02</span>
      <span class="sec-title">Activity Matrix</span>
      <div class="sec-line"></div>
    </div>
    <div class="stats-grid">
      <div class="stat-card"><div class="stat-num" data-target="847" id="sn1">0</div><div class="stat-label">Commits This Year</div></div>
      <div class="stat-card"><div class="stat-num" data-target="34" id="sn2">0</div><div class="stat-label">Repositories</div></div>
      <div class="stat-card"><div class="stat-num" data-target="203" id="sn3">0</div><div class="stat-label">Pull Requests</div></div>
    </div>
    <div class="stats-grid" style="margin-top:1px">
      <div class="stat-card"><div class="stat-num" data-target="512" id="sn4">0</div><div class="stat-label">Stars Earned</div></div>
      <div class="stat-card"><div class="stat-num" data-target="11" id="sn5">0</div><div class="stat-label">Languages</div></div>
      <div class="stat-card"><div class="stat-num" data-target="24" id="sn6" data-suffix="+">0</div><div class="stat-label">Frameworks</div></div>
    </div>
  </section>

  <!-- TECH ARSENAL -->
  <section class="section">
    <div class="sec-header">
      <span class="sec-num">// 03</span>
      <span class="sec-title">Tech Arsenal</span>
      <div class="sec-line"></div>
    </div>
    <div class="skill-grid" id="skillGrid"></div>
  </section>

  <!-- LANGUAGE BREAKDOWN -->
  <section class="section">
    <div class="sec-header">
      <span class="sec-num">// 04</span>
      <span class="sec-title">Language Split</span>
      <div class="sec-line"></div>
    </div>
    <div class="lang-bar" id="langBar"></div>
    <div class="lang-legend" id="langLegend"></div>
  </section>

  <!-- TERMINAL -->
  <section class="section" id="terminal">
    <div class="sec-header">
      <span class="sec-num">// 05</span>
      <span class="sec-title">Terminal</span>
      <div class="sec-line"></div>
    </div>
    <div class="terminal">
      <div class="term-header">
        <div class="dot dot-r"></div>
        <div class="dot dot-y"></div>
        <div class="dot dot-g"></div>
        <span class="term-title">bash — <span>ahmed@devmachine</span> — 80×24</span>
      </div>
      <div class="term-body">
        <div><span class="t-prompt">ahmed@dev</span>:<span class="t-path">~</span>$ <span class="t-cmd">whoami</span></div>
        <div class="t-out">→ Full-Stack Developer | Mobile Engineer | ML/AI Enthusiast</div>
        <br>
        <div><span class="t-prompt">ahmed@dev</span>:<span class="t-path">~</span>$ <span class="t-cmd">cat fun_fact.txt</span></div>
        <div class="t-out">→ I speak binary, but prefer coffee ☕</div>
        <br>
        <div><span class="t-prompt">ahmed@dev</span>:<span class="t-path">~</span>$ <span class="t-cmd">git log --oneline -4</span></div>
        <div class="t-out"><span class="t-success">a7f3c2e</span>&nbsp; feat: shipped cross-platform magic ✨</div>
        <div class="t-out"><span class="t-success">4e8b9d0</span>&nbsp; fix: converted caffeine to clean code</div>
        <div class="t-out"><span class="t-success">b1d5f7a</span>&nbsp; refactor: neural net hits 97.3% accuracy</div>
        <div class="t-out"><span class="t-success">1a2c3f4</span>&nbsp; init: brain.mode = ON 🧠</div>
        <br>
        <div><span class="t-prompt">ahmed@dev</span>:<span class="t-path">~</span>$ <span class="t-cmd">npm run passion --watch</span></div>
        <div class="t-out">→ watching for changes...<span class="cursor"></span></div>
      </div>
    </div>
  </section>

  <!-- CONNECT -->
  <section class="section" id="connect">
    <div class="sec-header">
      <span class="sec-num">// 06</span>
      <span class="sec-title">Connect</span>
      <div class="sec-line"></div>
    </div>
    <div class="connect-grid">
      <a href="https://your-portfolio.com" class="connect-item" target="_blank" rel="noopener">
        <span class="connect-icon">🌐</span>Portfolio
      </a>
      <a href="https://linkedin.com/in/your-profile" class="connect-item" target="_blank" rel="noopener">
        <span class="connect-icon">💼</span>LinkedIn
      </a>
      <a href="https://twitter.com/your-handle" class="connect-item" target="_blank" rel="noopener">
        <span class="connect-icon">𝕏</span>Twitter
      </a>
      <a href="https://github.com/AhmedNasir7" class="connect-item" target="_blank" rel="noopener">
        <span class="connect-icon">⬡</span>GitHub
      </a>
      <a href="mailto:your-email@example.com" class="connect-item">
        <span class="connect-icon">✉</span>Email
      </a>
    </div>
  </section>

  <!-- FOOTER -->
  <div class="footer-quote">
    <div class="quote-big"><span class="hi">Code.</span> Create.</div>
    <div class="quote-big">Innovate. <span class="hi">Repeat.</span></div>
    <div class="footer-meta">AhmedNasir7 &nbsp;·&nbsp; github.com/AhmedNasir7 &nbsp;·&nbsp; Lahore, PK</div>
  </div>

</div><!-- /page -->

<script>
/* ─── PARTICLE CANVAS ─── */
const canvas = document.getElementById('bg');
const ctx = canvas.getContext('2d');
let W, H, pts = [];

function resize() {
  W = canvas.width = window.innerWidth;
  H = canvas.height = window.innerHeight;
}
resize();
window.addEventListener('resize', resize);

function Pt() {
  this.x = Math.random() * W;
  this.y = Math.random() * H;
  this.vx = (Math.random() - 0.5) * 0.5;
  this.vy = (Math.random() - 0.5) * 0.5;
  this.r = Math.random() * 1.5 + 0.3;
  this.a = Math.random() * 0.5 + 0.1;
  this.c = Math.random() > 0.65 ? '#F72585' : '#0A66C2';
}
Pt.prototype.tick = function() {
  this.x += this.vx; this.y += this.vy;
  if (this.x < 0) this.x = W; if (this.x > W) this.x = 0;
  if (this.y < 0) this.y = H; if (this.y > H) this.y = 0;
};
Pt.prototype.draw = function() {
  ctx.beginPath();
  ctx.arc(this.x, this.y, this.r, 0, Math.PI * 2);
  ctx.fillStyle = this.c;
  ctx.globalAlpha = this.a;
  ctx.fill();
  ctx.globalAlpha = 1;
};

for (let i = 0; i < 110; i++) pts.push(new Pt());

function frame() {
  ctx.clearRect(0, 0, W, H);
  for (let i = 0; i < pts.length; i++) {
    for (let j = i + 1; j < pts.length; j++) {
      const dx = pts[i].x - pts[j].x;
      const dy = pts[i].y - pts[j].y;
      const d = Math.sqrt(dx * dx + dy * dy);
      if (d < 110) {
        ctx.beginPath();
        ctx.moveTo(pts[i].x, pts[i].y);
        ctx.lineTo(pts[j].x, pts[j].y);
        ctx.strokeStyle = '#F72585';
        ctx.globalAlpha = (1 - d / 110) * 0.07;
        ctx.lineWidth = 0.5;
        ctx.stroke();
        ctx.globalAlpha = 1;
      }
    }
    pts[i].tick();
    pts[i].draw();
  }
  requestAnimationFrame(frame);
}
frame();

/* ─── COUNT-UP ─── */
function countUp(el, target, dur, suffix) {
  const s = performance.now();
  function step(ts) {
    const p = Math.min((ts - s) / dur, 1);
    const e = 1 - Math.pow(1 - p, 3);
    el.textContent = Math.round(e * target) + (suffix || '');
    if (p < 1) requestAnimationFrame(step);
  }
  requestAnimationFrame(step);
}

const statEls = [
  { id: 'sn1', target: 847, dur: 1600 },
  { id: 'sn2', target: 34,  dur: 1200 },
  { id: 'sn3', target: 203, dur: 1500 },
  { id: 'sn4', target: 512, dur: 1700 },
  { id: 'sn5', target: 11,  dur: 900  },
  { id: 'sn6', target: 24,  dur: 1100, suffix: '+' },
];

const statsObserver = new IntersectionObserver(entries => {
  entries.forEach(e => {
    if (e.isIntersecting) {
      statEls.forEach(s => {
        const el = document.getElementById(s.id);
        if (el) countUp(el, s.target, s.dur, s.suffix || '');
      });
      statsObserver.disconnect();
    }
  });
}, { threshold: 0.3 });
const statsSection = document.querySelector('.stats-grid');
if (statsSection) statsObserver.observe(statsSection);

/* ─── SKILLS ─── */
const skills = [
  { cat: 'SYSTEM',  name: 'C++',         pct: 90 },
  { cat: 'SYSTEM',  name: 'C',           pct: 82 },
  { cat: 'SYSTEM',  name: 'Assembly',    pct: 65 },
  { cat: 'WEB',     name: 'React',       pct: 95 },
  { cat: 'WEB',     name: 'Next.js',     pct: 92 },
  { cat: 'WEB',     name: 'TypeScript',  pct: 88 },
  { cat: 'MOBILE',  name: 'React Native',pct: 91 },
  { cat: 'MOBILE',  name: 'Kotlin',      pct: 80 },
  { cat: 'MOBILE',  name: 'Jetpack',     pct: 75 },
  { cat: 'ML / AI', name: 'TensorFlow',  pct: 78 },
  { cat: 'ML / AI', name: 'PyTorch',     pct: 73 },
  { cat: 'ML / AI', name: 'Scikit-learn',pct: 80 },
  { cat: 'BACKEND', name: 'Node.js',     pct: 88 },
  { cat: 'BACKEND', name: 'Supabase',    pct: 85 },
  { cat: 'BACKEND', name: 'PostgreSQL',  pct: 82 },
  { cat: 'TOOLS',   name: 'Docker',      pct: 72 },
  { cat: 'TOOLS',   name: 'Linux',       pct: 85 },
  { cat: 'TOOLS',   name: 'Figma',       pct: 78 },
];

const grid = document.getElementById('skillGrid');
skills.forEach((s, i) => {
  const d = document.createElement('div');
  d.className = 'skill-item';
  d.innerHTML = `
    <div class="skill-cat">${s.cat}</div>
    <div class="skill-name">${s.name}</div>
    <div class="skill-bar-bg"><div class="skill-bar-fill" id="sb${i}"></div></div>
  `;
  grid.appendChild(d);
});

const skillsObserver = new IntersectionObserver(entries => {
  entries.forEach(e => {
    if (e.isIntersecting) {
      skills.forEach((s, i) => {
        setTimeout(() => {
          const bar = document.getElementById('sb' + i);
          if (bar) bar.style.width = s.pct + '%';
        }, i * 40);
      });
      skillsObserver.disconnect();
    }
  });
}, { threshold: 0.2 });
if (grid) skillsObserver.observe(grid);

/* ─── LANGUAGE BAR ─── */
const langs = [
  { name: 'JavaScript', pct: 32, color: '#F7DF1E' },
  { name: 'Python',     pct: 22, color: '#3776AB' },
  { name: 'TypeScript', pct: 18, color: '#007ACC' },
  { name: 'Kotlin',     pct: 12, color: '#7F52FF' },
  { name: 'C++',        pct: 10, color: '#F72585' },
  { name: 'Other',      pct:  6, color: '#2a2a2a' },
];

const langBar = document.getElementById('langBar');
const langLegend = document.getElementById('langLegend');

langs.forEach(l => {
  const seg = document.createElement('div');
  seg.className = 'lang-seg';
  seg.style.background = l.color;
  seg.title = `${l.name}: ${l.pct}%`;
  langBar.appendChild(seg);

  const li = document.createElement('div');
  li.className = 'lang-item';
  li.innerHTML = `<div class="lang-dot" style="background:${l.color}"></div>${l.name} <span style="color:#2a2a2a">${l.pct}%</span>`;
  langLegend.appendChild(li);
});

const langObserver = new IntersectionObserver(entries => {
  entries.forEach(e => {
    if (e.isIntersecting) {
      langs.forEach((l, i) => {
        setTimeout(() => {
          const seg = langBar.children[i];
          if (seg) seg.style.width = l.pct + '%';
        }, i * 80);
      });
      langObserver.disconnect();
    }
  });
}, { threshold: 0.4 });
if (langBar) langObserver.observe(langBar);

/* ─── SCROLL REVEAL ─── */
const revealEls = document.querySelectorAll('.section, .focus-card, .terminal, .connect-grid');
const revealObserver = new IntersectionObserver(entries => {
  entries.forEach(e => {
    if (e.isIntersecting) {
      e.target.style.opacity = '1';
      e.target.style.transform = 'translateY(0)';
    }
  });
}, { threshold: 0.1 });

revealEls.forEach(el => {
  el.style.opacity = '0';
  el.style.transform = 'translateY(20px)';
  el.style.transition = 'opacity 0.7s ease, transform 0.7s ease';
  revealObserver.observe(el);
});
</script>
</body>
</html>
