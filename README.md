<!DOCTYPE html>
<html lang="en">
<head>
<meta charset="UTF-8" />
<meta name="viewport" content="width=device-width, initial-scale=1.0"/>
<title>Ritesh Kanara — GitHub Profile</title>
<link href="https://fonts.googleapis.com/css2?family=Syne:wght@400;600;700;800&family=DM+Mono:wght@300;400;500&family=Fraunces:ital,wght@0,300;0,700;1,300&display=swap" rel="stylesheet"/>
<style>
  :root {
    --bg: #080c10;
    --surface: #0d1117;
    --card: #111720;
    --border: #1e2d3d;
    --blue: #58a6ff;
    --cyan: #39d0d8;
    --green: #3fb950;
    --orange: #f0883e;
    --pink: #f778ba;
    --purple: #bc8cff;
    --text: #e6edf3;
    --muted: #7d8590;
    --dimmed: #30363d;
  }
  * { margin: 0; padding: 0; box-sizing: border-box; }

  body {
    background: var(--bg);
    color: var(--text);
    font-family: 'DM Mono', monospace;
    overflow-x: hidden;
    cursor: none;
  }

  /* CUSTOM CURSOR */
  .cursor {
    position: fixed; width: 12px; height: 12px;
    background: var(--blue); border-radius: 50%;
    pointer-events: none; z-index: 9999;
    transform: translate(-50%,-50%);
    transition: transform 0.1s, background 0.2s;
    mix-blend-mode: screen;
  }
  .cursor-ring {
    position: fixed; width: 36px; height: 36px;
    border: 1px solid var(--blue); border-radius: 50%;
    pointer-events: none; z-index: 9998;
    transform: translate(-50%,-50%);
    transition: all 0.15s ease;
    opacity: 0.5;
  }

  /* PARTICLE CANVAS */
  #particles { position: fixed; inset: 0; z-index: 0; opacity: 0.4; pointer-events: none; }

  .container { max-width: 960px; margin: 0 auto; padding: 0 24px; position: relative; z-index: 1; }

  /* ── HERO ── */
  .hero {
    min-height: 100vh;
    display: flex; flex-direction: column; align-items: center; justify-content: center;
    text-align: center; position: relative; padding: 80px 24px 60px;
  }

  .hero-badge {
    display: inline-flex; align-items: center; gap: 8px;
    background: rgba(88,166,255,0.08); border: 1px solid rgba(88,166,255,0.25);
    border-radius: 999px; padding: 6px 16px; font-size: 11px;
    color: var(--blue); letter-spacing: 2px; text-transform: uppercase;
    margin-bottom: 32px;
    animation: fadeSlideUp 0.6s ease both;
  }
  .hero-badge::before { content: ''; width: 6px; height: 6px; background: var(--green); border-radius: 50%; animation: pulse 2s infinite; }

  @keyframes pulse { 0%,100%{box-shadow:0 0 0 0 rgba(63,185,80,0.6)} 50%{box-shadow:0 0 0 6px rgba(63,185,80,0)} }

  .hero-name {
    font-family: 'Syne', sans-serif;
    font-size: clamp(52px, 8vw, 96px);
    font-weight: 800;
    line-height: 0.95;
    background: linear-gradient(135deg, #fff 0%, var(--blue) 40%, var(--cyan) 100%);
    -webkit-background-clip: text; -webkit-text-fill-color: transparent;
    background-clip: text;
    animation: fadeSlideUp 0.7s 0.1s ease both;
    letter-spacing: -2px;
  }

  .hero-sub {
    font-family: 'Fraunces', serif;
    font-size: clamp(16px, 2.5vw, 22px);
    color: var(--muted); font-style: italic;
    margin: 16px 0 40px;
    animation: fadeSlideUp 0.7s 0.2s ease both;
    font-weight: 300;
  }

  .hero-pills {
    display: flex; flex-wrap: wrap; gap: 10px; justify-content: center;
    animation: fadeSlideUp 0.7s 0.3s ease both;
    margin-bottom: 48px;
  }
  .pill {
    display: flex; align-items: center; gap: 6px;
    background: var(--card); border: 1px solid var(--border);
    border-radius: 8px; padding: 8px 14px; font-size: 12px; color: var(--text);
    transition: all 0.2s; text-decoration: none;
  }
  .pill:hover { border-color: var(--blue); color: var(--blue); transform: translateY(-2px); box-shadow: 0 8px 24px rgba(88,166,255,0.15); }
  .pill img { width: 16px; height: 16px; border-radius: 2px; }

  .hero-social {
    display: flex; gap: 12px; justify-content: center;
    animation: fadeSlideUp 0.7s 0.4s ease both;
  }
  .social-btn {
    display: flex; align-items: center; gap: 8px;
    padding: 10px 20px; border-radius: 10px;
    font-size: 12px; font-family: 'DM Mono', monospace;
    text-decoration: none; transition: all 0.25s; border: 1px solid var(--border);
    background: var(--card); color: var(--text);
  }
  .social-btn:hover { transform: translateY(-3px); box-shadow: 0 12px 32px rgba(0,0,0,0.4); }
  .social-btn.gh:hover { border-color: #fff; color: #fff; }
  .social-btn.li:hover { border-color: #0077B5; color: #0077B5; }
  .social-btn.lc:hover { border-color: #FFA116; color: #FFA116; }
  .social-btn.em:hover { border-color: #EA4335; color: #EA4335; }

  /* SCROLL INDICATOR */
  .scroll-hint {
    position: absolute; bottom: 32px; left: 50%; transform: translateX(-50%);
    display: flex; flex-direction: column; align-items: center; gap: 8px;
    opacity: 0.4; font-size: 10px; letter-spacing: 2px; text-transform: uppercase;
    animation: fadeSlideUp 1s 1s ease both;
  }
  .scroll-line { width: 1px; height: 48px; background: linear-gradient(to bottom, var(--blue), transparent); animation: scrollLine 1.5s infinite; }
  @keyframes scrollLine { 0%{transform:scaleY(0);transform-origin:top} 50%{transform:scaleY(1);transform-origin:top} 51%{transform-origin:bottom} 100%{transform:scaleY(0);transform-origin:bottom} }

  /* ── SECTION WRAPPER ── */
  .section { padding: 80px 0; }
  .section-label {
    display: flex; align-items: center; gap: 12px;
    font-size: 10px; letter-spacing: 3px; text-transform: uppercase;
    color: var(--blue); margin-bottom: 40px;
  }
  .section-label::after { content: ''; flex: 1; height: 1px; background: var(--border); }

  .section-title {
    font-family: 'Syne', sans-serif;
    font-size: clamp(28px, 4vw, 42px); font-weight: 700;
    line-height: 1.1; margin-bottom: 8px;
  }

  /* ── TECH STACK ── */
  .stack-grid {
    display: grid; gap: 20px; grid-template-columns: 1fr 1fr;
  }
  @media(max-width:600px){ .stack-grid { grid-template-columns: 1fr; } }

  .stack-card {
    background: var(--card); border: 1px solid var(--border);
    border-radius: 16px; padding: 24px;
    transition: all 0.3s; position: relative; overflow: hidden;
  }
  .stack-card::before {
    content: ''; position: absolute; inset: 0; border-radius: 16px;
    background: linear-gradient(135deg, rgba(88,166,255,0.06), transparent);
    opacity: 0; transition: opacity 0.3s;
  }
  .stack-card:hover { border-color: var(--blue); transform: translateY(-4px); box-shadow: 0 20px 48px rgba(88,166,255,0.1); }
  .stack-card:hover::before { opacity: 1; }

  .stack-cat {
    font-size: 10px; letter-spacing: 2px; text-transform: uppercase;
    color: var(--muted); margin-bottom: 16px;
  }
  .tech-icons {
    display: flex; flex-wrap: wrap; gap: 10px; align-items: center;
  }
  .tech-icon {
    display: flex; flex-direction: column; align-items: center; gap: 5px;
    padding: 8px 10px; border-radius: 10px; background: var(--surface);
    border: 1px solid var(--dimmed); transition: all 0.2s; cursor: default;
    min-width: 52px;
  }
  .tech-icon:hover { border-color: var(--blue); transform: scale(1.1); background: rgba(88,166,255,0.08); }
  .tech-icon img { width: 28px; height: 28px; }
  .tech-icon span { font-size: 9px; color: var(--muted); white-space: nowrap; }

  /* ── STATS ── */
  .stats-grid {
    display: grid; grid-template-columns: repeat(3, 1fr); gap: 16px;
    margin-bottom: 32px;
  }
  @media(max-width:600px){ .stats-grid { grid-template-columns: 1fr 1fr; } }

  .stat-card {
    background: var(--card); border: 1px solid var(--border);
    border-radius: 16px; padding: 24px 20px; text-align: center;
    transition: all 0.3s; position: relative; overflow: hidden;
  }
  .stat-card::after {
    content: ''; position: absolute; bottom: 0; left: 0; right: 0;
    height: 2px; background: linear-gradient(90deg, var(--blue), var(--cyan));
    transform: scaleX(0); transition: transform 0.3s; transform-origin: left;
  }
  .stat-card:hover { border-color: var(--blue); transform: translateY(-3px); }
  .stat-card:hover::after { transform: scaleX(1); }

  .stat-icon { font-size: 28px; margin-bottom: 10px; display: block; }
  .stat-num {
    font-family: 'Syne', sans-serif; font-size: 36px; font-weight: 800;
    background: linear-gradient(135deg, var(--blue), var(--cyan));
    -webkit-background-clip: text; -webkit-text-fill-color: transparent;
    background-clip: text;
  }
  .stat-label { font-size: 10px; color: var(--muted); letter-spacing: 1px; margin-top: 4px; }

  /* GITHUB IMG STATS */
  .gh-stats-row {
    display: grid; grid-template-columns: 1fr 1fr; gap: 16px; margin-bottom: 16px;
  }
  @media(max-width:600px){ .gh-stats-row { grid-template-columns: 1fr; } }
  .gh-stats-row img, .gh-stats-full img {
    width: 100%; border-radius: 12px; border: 1px solid var(--border);
    transition: all 0.3s;
  }
  .gh-stats-row img:hover, .gh-stats-full img:hover { border-color: var(--blue); transform: scale(1.01); }
  .gh-stats-full { margin-bottom: 16px; }

  .lc-card {
    background: var(--card); border: 1px solid var(--border);
    border-radius: 16px; padding: 24px; text-align: center;
  }
  .lc-card img { width: 100%; border-radius: 8px; }

  /* ── PROJECT ── */
  .project-card {
    background: var(--card); border: 1px solid var(--border);
    border-radius: 20px; padding: 32px; margin-bottom: 20px;
    transition: all 0.3s; position: relative; overflow: hidden;
  }
  .project-card::before {
    content: ''; position: absolute; top: 0; left: 0; right: 0; height: 3px;
    background: linear-gradient(90deg, var(--blue), var(--cyan), var(--purple));
  }
  .project-card:hover { border-color: var(--blue); transform: translateY(-4px); box-shadow: 0 24px 64px rgba(88,166,255,0.12); }

  .project-header { display: flex; align-items: flex-start; justify-content: space-between; gap: 16px; margin-bottom: 16px; }
  .project-title-wrap { flex: 1; }
  .project-title {
    font-family: 'Syne', sans-serif; font-size: 22px; font-weight: 700; margin-bottom: 6px;
  }
  .project-year { font-size: 11px; color: var(--muted); }
  .project-links { display: flex; gap: 8px; flex-shrink: 0; }
  .proj-link {
    display: flex; align-items: center; gap: 6px; padding: 7px 14px;
    border-radius: 8px; border: 1px solid var(--border); background: var(--surface);
    font-size: 11px; color: var(--text); text-decoration: none; transition: all 0.2s;
    white-space: nowrap;
  }
  .proj-link:hover { border-color: var(--blue); color: var(--blue); }

  .project-desc { color: var(--muted); font-size: 13px; line-height: 1.7; margin-bottom: 20px; }

  .tag-list { display: flex; flex-wrap: wrap; gap: 8px; margin-bottom: 20px; }
  .tag {
    background: rgba(88,166,255,0.08); border: 1px solid rgba(88,166,255,0.2);
    border-radius: 6px; padding: 4px 10px; font-size: 11px; color: var(--blue);
  }

  .feature-list { list-style: none; display: grid; gap: 8px; }
  .feature-list li {
    display: flex; align-items: flex-start; gap: 10px; font-size: 12px; color: var(--muted); line-height: 1.6;
  }
  .feature-list li::before { content: '›'; color: var(--blue); font-size: 16px; line-height: 1.3; flex-shrink: 0; }

  /* ── ACHIEVEMENTS ── */
  .ach-grid { display: grid; grid-template-columns: repeat(2, 1fr); gap: 16px; }
  @media(max-width:600px){ .ach-grid { grid-template-columns: 1fr; } }
  .ach-card {
    background: var(--card); border: 1px solid var(--border);
    border-radius: 16px; padding: 24px; display: flex; gap: 16px;
    align-items: flex-start; transition: all 0.3s;
  }
  .ach-card:hover { border-color: var(--orange); transform: translateY(-3px); }
  .ach-icon { font-size: 32px; flex-shrink: 0; }
  .ach-title { font-family: 'Syne', sans-serif; font-weight: 700; font-size: 15px; margin-bottom: 6px; }
  .ach-desc { font-size: 12px; color: var(--muted); line-height: 1.6; }

  /* ── ABOUT / TERMINAL ── */
  .terminal {
    background: #0a0e13; border: 1px solid var(--border);
    border-radius: 16px; overflow: hidden;
    box-shadow: 0 24px 64px rgba(0,0,0,0.5);
  }
  .term-bar {
    background: #161b22; padding: 12px 16px;
    display: flex; align-items: center; gap: 8px;
    border-bottom: 1px solid var(--border);
  }
  .term-dot { width: 12px; height: 12px; border-radius: 50%; }
  .term-title { font-size: 11px; color: var(--muted); margin-left: 8px; letter-spacing: 1px; }
  .term-body { padding: 24px 28px; font-size: 13px; line-height: 2; }
  .term-cmd { color: var(--blue); }
  .term-out { color: var(--text); }
  .term-green { color: var(--green); }
  .term-orange { color: var(--orange); }
  .term-pink { color: var(--pink); }
  .term-cyan { color: var(--cyan); }
  .term-muted { color: var(--muted); }
  .blink { animation: blink 1.2s step-end infinite; }
  @keyframes blink { 0%,100%{opacity:1} 50%{opacity:0} }

  /* ── EDUCATION ── */
  .edu-card {
    background: var(--card); border: 1px solid var(--border);
    border-radius: 16px; padding: 28px; display: flex; gap: 20px; align-items: center;
  }
  .edu-icon { font-size: 40px; flex-shrink: 0; }
  .edu-uni { font-family: 'Syne', sans-serif; font-weight: 700; font-size: 18px; }
  .edu-deg { color: var(--blue); font-size: 13px; margin: 4px 0; }
  .edu-meta { color: var(--muted); font-size: 12px; }
  .cgpa-badge {
    margin-left: auto; background: rgba(63,185,80,0.1); border: 1px solid rgba(63,185,80,0.3);
    border-radius: 10px; padding: 10px 16px; text-align: center; flex-shrink: 0;
  }
  .cgpa-num { font-family: 'Syne', sans-serif; font-size: 24px; font-weight: 800; color: var(--green); }
  .cgpa-label { font-size: 10px; color: var(--muted); }

  /* ── FOOTER ── */
  .footer {
    border-top: 1px solid var(--border); padding: 48px 0 32px;
    text-align: center;
  }
  .footer-quote {
    font-family: 'Fraunces', serif; font-style: italic;
    font-size: 18px; color: var(--muted); margin-bottom: 24px;
  }
  .footer-quote span { color: var(--text); }
  .footer-meta { font-size: 11px; color: var(--dimmed); }

  /* ANIMATIONS */
  @keyframes fadeSlideUp { from{opacity:0;transform:translateY(24px)} to{opacity:1;transform:translateY(0)} }

  .reveal {
    opacity: 0; transform: translateY(32px);
    transition: opacity 0.7s ease, transform 0.7s ease;
  }
  .reveal.visible { opacity: 1; transform: translateY(0); }

  /* DIVIDER */
  .divider {
    height: 1px; background: linear-gradient(90deg, transparent, var(--border), transparent);
    margin: 0;
  }

  /* PROGRESS BARS */
  .skill-bars { display: grid; gap: 12px; margin-top: 16px; }
  .skill-row { display: flex; flex-direction: column; gap: 6px; }
  .skill-head { display: flex; justify-content: space-between; font-size: 11px; }
  .skill-name { color: var(--text); }
  .skill-pct { color: var(--muted); }
  .skill-track { height: 4px; background: var(--dimmed); border-radius: 4px; overflow: hidden; }
  .skill-fill {
    height: 100%; border-radius: 4px;
    background: linear-gradient(90deg, var(--blue), var(--cyan));
    width: 0%; transition: width 1.2s cubic-bezier(0.4,0,0.2,1);
  }

</style>
</head>
<body>

<canvas id="particles"></canvas>
<div class="cursor" id="cursor"></div>
<div class="cursor-ring" id="cursorRing"></div>

<!-- ══════════════ HERO ══════════════ -->
<section class="hero">
  <div class="hero-badge">
    <span>Available for Internships &amp; Full-time</span>
  </div>

  <h1 class="hero-name">Ritesh<br/>Kanara</h1>

  <p class="hero-sub">Full Stack Developer &nbsp;·&nbsp; MERN Stack Engineer &nbsp;·&nbsp; Java &amp; DSA</p>

  <div class="hero-pills">
    <span class="pill">
      <img src="https://skillicons.dev/icons?i=react&theme=dark" alt=""/>
      React
    </span>
    <span class="pill">
      <img src="https://skillicons.dev/icons?i=nodejs&theme=dark" alt=""/>
      Node.js
    </span>
    <span class="pill">
      <img src="https://skillicons.dev/icons?i=mongodb&theme=dark" alt=""/>
      MongoDB
    </span>
    <span class="pill">
      <img src="https://skillicons.dev/icons?i=java&theme=dark" alt=""/>
      Java
    </span>
    <span class="pill">
      <img src="https://skillicons.dev/icons?i=aws&theme=dark" alt=""/>
      AWS
    </span>
    <span class="pill">📍 Gandhinagar, Gujarat, India</span>
  </div>

  <div class="hero-social">
    <a href="https://github.com/Riteshkanara" class="social-btn gh" target="_blank">
      <svg width="16" height="16" viewBox="0 0 24 24" fill="currentColor"><path d="M12 0C5.37 0 0 5.37 0 12c0 5.31 3.435 9.795 8.205 11.385.6.105.825-.255.825-.57 0-.285-.015-1.23-.015-2.235-3.015.555-3.795-.735-4.035-1.41-.135-.345-.72-1.41-1.23-1.695-.42-.225-1.02-.78-.015-.795.945-.015 1.62.87 1.845 1.23 1.08 1.815 2.805 1.305 3.495.99.105-.78.42-1.305.765-1.605-2.67-.3-5.46-1.335-5.46-5.925 0-1.305.465-2.385 1.23-3.225-.12-.3-.54-1.53.12-3.18 0 0 1.005-.315 3.3 1.23.96-.27 1.98-.405 3-.405s2.04.135 3 .405c2.295-1.56 3.3-1.23 3.3-1.23.66 1.65.24 2.88.12 3.18.765.84 1.23 1.905 1.23 3.225 0 4.605-2.805 5.625-5.475 5.925.435.375.81 1.095.81 2.22 0 1.605-.015 2.895-.015 3.3 0 .315.225.69.825.57A12.02 12.02 0 0 0 24 12c0-6.63-5.37-12-12-12z"/></svg>
      GitHub
    </a>
    <a href="https://www.linkedin.com/in/ritesh-kanara-ahir-966677244" class="social-btn li" target="_blank">
      <svg width="16" height="16" viewBox="0 0 24 24" fill="currentColor"><path d="M20.447 20.452h-3.554v-5.569c0-1.328-.027-3.037-1.852-3.037-1.853 0-2.136 1.445-2.136 2.939v5.667H9.351V9h3.414v1.561h.046c.477-.9 1.637-1.85 3.37-1.85 3.601 0 4.267 2.37 4.267 5.455v6.286zM5.337 7.433a2.062 2.062 0 0 1-2.063-2.065 2.064 2.064 0 1 1 2.063 2.065zm1.782 13.019H3.555V9h3.564v11.452zM22.225 0H1.771C.792 0 0 .774 0 1.729v20.542C0 23.227.792 24 1.771 24h20.451C23.2 24 24 23.227 24 22.271V1.729C24 .774 23.2 0 22.222 0h.003z"/></svg>
      LinkedIn
    </a>
    <a href="https://leetcode.com/u/Ritesh-Kanara" class="social-btn lc" target="_blank">
      <svg width="16" height="16" viewBox="0 0 24 24" fill="currentColor"><path d="M13.483 0a1.374 1.374 0 0 0-.961.438L7.116 6.226l-3.854 4.126a5.266 5.266 0 0 0-1.209 2.104 5.35 5.35 0 0 0-.125.513 5.527 5.527 0 0 0 .062 2.362 5.83 5.83 0 0 0 .349 1.017 5.938 5.938 0 0 0 1.271 1.818l4.277 4.193.039.038c2.248 2.165 5.852 2.133 8.063-.074l2.396-2.392c.54-.54.54-1.414.003-1.955a1.378 1.378 0 0 0-1.951-.003l-2.396 2.392a3.021 3.021 0 0 1-4.205.038l-.02-.019-4.276-4.193c-.652-.64-.972-1.469-.948-2.263a2.68 2.68 0 0 1 .066-.523 2.545 2.545 0 0 1 .619-1.164L9.13 8.114c1.058-1.134 3.204-1.27 4.43-.278l3.501 2.831c.593.48 1.461.387 1.94-.207a1.384 1.384 0 0 0-.207-1.943l-3.5-2.831c-.8-.647-1.766-1.045-2.774-1.202l2.015-2.158A1.384 1.384 0 0 0 13.483 0zm-2.866 12.815a1.38 1.38 0 0 0-1.38 1.382 1.38 1.38 0 0 0 1.38 1.382H20.79a1.38 1.38 0 0 0 1.38-1.382 1.38 1.38 0 0 0-1.38-1.382z"/></svg>
      LeetCode
    </a>
    <a href="mailto:riteshkanara7777@gmail.com" class="social-btn em" target="_blank">
      <svg width="16" height="16" viewBox="0 0 24 24" fill="currentColor"><path d="M24 5.457v13.909c0 .904-.732 1.636-1.636 1.636h-3.819V11.73L12 16.64l-6.545-4.91v9.273H1.636A1.636 1.636 0 0 1 0 19.366V5.457c0-2.023 2.309-3.178 3.927-1.964L5.455 4.64 12 9.548l6.545-4.91 1.528-1.145C21.69 2.28 24 3.434 24 5.457z"/></svg>
      Email
    </a>
  </div>

  <div class="scroll-hint">
    <span>scroll</span>
    <div class="scroll-line"></div>
  </div>
</section>

<div class="divider"></div>

<!-- ══════════════ ABOUT / TERMINAL ══════════════ -->
<section class="section">
  <div class="container reveal">
    <div class="section-label">01 &nbsp; about</div>
    <div class="terminal">
      <div class="term-bar">
        <div class="term-dot" style="background:#ff5f57"></div>
        <div class="term-dot" style="background:#febc2e"></div>
        <div class="term-dot" style="background:#28c840"></div>
        <span class="term-title">ritesh@dev ~ profile.sh</span>
      </div>
      <div class="term-body">
        <div><span class="term-cmd">$</span> <span class="term-green">whoami</span></div>
        <div class="term-out">&nbsp;&nbsp;→ <span class="term-cyan">Ritesh Kanara</span> — Results-driven Full Stack Developer</div>
        <br/>
        <div><span cl