<!DOCTYPE html>
<html lang="en">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<meta name="description" content="Lakshmi — BCA student and aspiring developer. Portfolio of projects, skills, and a walkthrough video.">
<link rel="icon" href="data:image/svg+xml,%3Csvg xmlns='http://www.w3.org/2000/svg' viewBox='0 0 100 100'%3E%3Ctext y='.9em' font-size='90'%3E%F0%9F%92%BB%3C/text%3E%3C/svg%3E">
<title>Lakshmi — Portfolio</title>
<link rel="preconnect" href="https://fonts.googleapis.com">
<link rel="preconnect" href="https://fonts.gstatic.com" crossorigin>
<link href="https://fonts.googleapis.com/css2?family=Space+Mono:wght@400;700&family=Manrope:wght@400;500;600;700;800&display=swap" rel="stylesheet">
<style>
  :root {
    --bg: #12101c;
    --bg-alt: #1b1730;
    --surface: #201c38;
    --surface-2: #262143;
    --text: #f2eee6;
    --muted: #9089ad;
    --accent: #f2b807;
    --accent-2: #6fe7dd;
    --dot-red: #ff6b6b;
    --font-display: 'Space Mono', monospace;
    --font-body: 'Manrope', sans-serif;
    --radius: 10px;
  }

  * { box-sizing: border-box; }

  html { scroll-behavior: smooth; }

  body {
    margin: 0;
    font-family: var(--font-body);
    background: var(--bg);
    color: var(--text);
    line-height: 1.6;
    position: relative;
    overflow-x: hidden;
  }

  .bg-grid {
    position: fixed;
    inset: 0;
    z-index: -1;
    background-image:
      linear-gradient(rgba(242, 238, 230, 0.035) 1px, transparent 1px),
      linear-gradient(90deg, rgba(242, 238, 230, 0.035) 1px, transparent 1px);
    background-size: 42px 42px;
    -webkit-mask-image: radial-gradient(ellipse 80% 60% at 50% 0%, #000 40%, transparent 90%);
            mask-image: radial-gradient(ellipse 80% 60% at 50% 0%, #000 40%, transparent 90%);
  }

  a { color: inherit; }

  /* ---------- Preloader ---------- */
  .preloader {
    position: fixed;
    inset: 0;
    z-index: 200;
    display: flex;
    align-items: center;
    justify-content: center;
    background: var(--bg);
    transition: opacity 0.5s ease, visibility 0.5s ease;
  }

  .preloader.done { opacity: 0; visibility: hidden; pointer-events: none; }

  .preloader-line {
    font-family: var(--font-display);
    font-size: 14px;
    color: var(--accent-2);
    margin: 0 0 14px;
    text-align: center;
  }

  .preloader-dots { display: inline-block; width: 1.5em; }

  .preloader-bar {
    width: 220px;
    height: 4px;
    border-radius: 4px;
    background: var(--surface-2);
    overflow: hidden;
  }

  .preloader-fill {
    height: 100%;
    width: 0%;
    background: linear-gradient(90deg, var(--accent), var(--accent-2));
    animation: loadfill 1.1s ease forwards;
  }

  @keyframes loadfill { to { width: 100%; } }

  @media (prefers-reduced-motion: reduce) {
    .preloader { display: none; }
  }

  /* ---------- Scroll progress ---------- */
  .scroll-progress {
    position: fixed;
    top: 0; left: 0;
    width: 100%;
    height: 3px;
    background: rgba(242, 238, 230, 0.06);
    z-index: 90;
  }

  .scroll-progress-fill {
    height: 100%;
    width: 0%;
    background: linear-gradient(90deg, var(--accent), var(--accent-2));
  }

  /* ---------- Back to top ---------- */
  .back-to-top {
    position: fixed;
    right: 20px;
    bottom: 20px;
    width: 42px;
    height: 42px;
    border-radius: 50%;
    background: var(--surface);
    border: 1px solid rgba(242, 238, 230, 0.12);
    color: var(--accent-2);
    font-size: 18px;
    cursor: pointer;
    z-index: 80;
    opacity: 0;
    transform: translateY(10px);
    pointer-events: none;
    transition: opacity 0.25s ease, transform 0.25s ease, border-color 0.2s ease;
  }

  .back-to-top.show { opacity: 1; transform: translateY(0); pointer-events: auto; }
  .back-to-top:hover { border-color: var(--accent-2); }

  /* ---------- Hero / Terminal ---------- */
  .hero {
    padding: 48px 20px 0;
    display: flex;
    flex-direction: column;
    align-items: center;
    position: relative;
    overflow: hidden;
  }

  .hero::before {
    content: '';
    position: absolute;
    inset: 0;
    pointer-events: none;
    background: radial-gradient(320px circle at var(--mx, 50%) var(--my, 0%), rgba(111, 231, 221, 0.12), transparent 70%);
    z-index: 0;
  }

  .hero > * { position: relative; z-index: 1; }

  .terminal-window {
    width: 100%;
    max-width: 720px;
    background: var(--surface);
    border: 1px solid rgba(242, 238, 230, 0.08);
    border-radius: var(--radius);
    box-shadow: 0 30px 60px -20px rgba(0,0,0,0.6);
    overflow: hidden;
    opacity: 0;
    transform: translateY(16px);
    animation: risein 0.7s ease forwards 0.1s;
  }

  @keyframes risein {
    to { opacity: 1; transform: translateY(0); }
  }

  .terminal-bar {
    display: flex;
    align-items: center;
    gap: 8px;
    padding: 12px 16px;
    background: var(--bg-alt);
    border-bottom: 1px solid rgba(242, 238, 230, 0.06);
  }

  .dot { width: 11px; height: 11px; border-radius: 50%; display: inline-block; }
  .dot.red { background: var(--dot-red); }
  .dot.yellow { background: var(--accent); }
  .dot.green { background: var(--accent-2); }

  .terminal-title {
    margin-left: 8px;
    font-family: var(--font-display);
    font-size: 12px;
    color: var(--muted);
  }

  .terminal-body { padding: 28px 28px 32px; }

  .prompt-line {
    font-family: var(--font-display);
    font-size: 14px;
    color: var(--accent-2);
    margin: 0 0 24px;
    min-height: 1.4em;
  }

  .prompt { color: var(--muted); margin-right: 8px; }

  .cursor {
    display: inline-block;
    color: var(--accent);
    animation: blink 1s steps(1) infinite;
  }

  @keyframes blink { 50% { opacity: 0; } }

  .hero-content {
    display: flex;
    align-items: center;
    gap: 24px;
    flex-wrap: wrap;
  }

  .profile-frame {
    margin: 0;
    flex-shrink: 0;
    width: 108px;
    height: 108px;
    border-radius: 50%;
    padding: 3px;
    background: conic-gradient(from 0deg, var(--accent), var(--accent-2), var(--accent));
    animation: spin 6s linear infinite;
  }

  @media (prefers-reduced-motion: reduce) {
    .profile-frame { animation: none; }
  }

  @keyframes spin { to { transform: rotate(360deg); } }

  .profile-frame img {
    width: 100%;
    height: 100%;
    object-fit: cover;
    border-radius: 50%;
    border: 3px solid var(--surface);
    display: block;
  }

  .hero-text h1 {
    margin: 0;
    font-family: var(--font-display);
    font-size: 34px;
    letter-spacing: -0.5px;
  }

  .hero-text .role {
    margin: 6px 0 0;
    color: var(--muted);
    font-size: 15px;
  }

  .hero-actions {
    display: flex;
    align-items: center;
    flex-wrap: wrap;
    gap: 14px;
    margin-top: 22px;
    padding-top: 20px;
    border-top: 1px solid rgba(242, 238, 230, 0.08);
  }

  .btn-resume {
    font-family: var(--font-display);
    font-size: 13px;
    text-decoration: none;
    padding: 10px 18px;
    border-radius: 6px;
    background: var(--accent-2);
    color: var(--bg);
    transition: transform 0.15s ease, box-shadow 0.15s ease;
  }

  .btn-resume:hover {
    transform: translateY(-2px);
    box-shadow: 0 10px 24px -8px rgba(111, 231, 221, 0.5);
  }

  .social-row { display: flex; gap: 8px; }

  .social-badge {
    width: 34px;
    height: 34px;
    border-radius: 50%;
    display: flex;
    align-items: center;
    justify-content: center;
    font-family: var(--font-display);
    font-size: 12px;
    text-decoration: none;
    color: var(--muted);
    border: 1px solid rgba(242, 238, 230, 0.15);
    transition: color 0.2s ease, border-color 0.2s ease, transform 0.2s ease;
  }

  .social-badge:hover {
    color: var(--accent-2);
    border-color: var(--accent-2);
    transform: translateY(-2px);
  }

  .stats-strip {
    width: 100%;
    max-width: 720px;
    display: flex;
    justify-content: center;
    gap: 40px;
    flex-wrap: wrap;
    margin-top: 20px;
    padding: 18px 0 0;
  }

  .stat { display: flex; flex-direction: column; align-items: center; gap: 2px; }

  .stat-num {
    font-family: var(--font-display);
    font-size: 26px;
    color: var(--accent);
  }

  .stat-label {
    font-size: 12px;
    color: var(--muted);
    letter-spacing: 0.3px;
  }

  .stat-label.status { display: flex; align-items: center; gap: 6px; color: var(--accent-2); font-family: var(--font-display); }

  .status-dot {
    width: 7px; height: 7px;
    border-radius: 50%;
    background: var(--accent-2);
    animation: pulse 1.6s ease-in-out infinite;
  }

  @keyframes pulse {
    0%, 100% { opacity: 1; box-shadow: 0 0 0 0 rgba(111,231,221,0.5); }
    50% { opacity: 0.6; box-shadow: 0 0 0 5px rgba(111,231,221,0); }
  }

  @media (prefers-reduced-motion: reduce) {
    .status-dot { animation: none; }
  }

  /* ---------- Tab nav ---------- */
  .tab-nav {
    margin-top: 22px;
    width: 100%;
    max-width: 720px;
  }

  .tab-nav ul {
    list-style: none;
    display: flex;
    flex-wrap: wrap;
    gap: 6px;
    margin: 0;
    padding: 0;
  }

  .tab-link {
    font-family: var(--font-display);
    font-size: 13px;
    text-decoration: none;
    color: var(--muted);
    background: var(--surface);
    border: 1px solid rgba(242, 238, 230, 0.08);
    border-bottom: none;
    padding: 10px 16px;
    border-radius: 8px 8px 0 0;
    display: inline-block;
    transition: color 0.2s ease, background 0.2s ease;
  }

  .tab-link:hover { color: var(--text); }

  .tab-link.active {
    color: var(--bg);
    background: var(--accent-2);
  }

  /* ---------- Main / sections ---------- */
  main {
    max-width: 720px;
    margin: 0 auto;
    padding: 0 20px 40px;
  }

  section {
    background: var(--surface);
    border: 1px solid rgba(242, 238, 230, 0.08);
    border-radius: 0 var(--radius) var(--radius) var(--radius);
    padding: 32px 28px;
    margin-top: -1px;
    scroll-margin-top: 24px;
  }

  section + section { margin-top: 28px; border-radius: var(--radius); }

  .file-label {
    font-family: var(--font-display);
    font-size: 12px;
    color: var(--accent);
    letter-spacing: 0.5px;
    margin: 0 0 6px;
  }

  section h2 {
    font-family: var(--font-display);
    font-size: 22px;
    margin: 0 0 16px;
  }

  section p { color: var(--text); }

  .reveal {
    opacity: 0;
    transform: translateY(24px);
    transition: opacity 0.6s ease, transform 0.6s ease;
  }

  .reveal.in-view { opacity: 1; transform: translateY(0); }

  @media (prefers-reduced-motion: reduce) {
    .reveal { transition: opacity 0.2s ease; transform: none; }
  }

  /* ---------- Education ---------- */
  .edu-item {
    display: flex;
    gap: 16px;
  }

  .edu-dot {
    flex-shrink: 0;
    width: 10px;
    height: 10px;
    border-radius: 50%;
    background: var(--accent);
    margin-top: 8px;
  }

  .edu-item h3 {
    font-family: var(--font-display);
    font-size: 16px;
    margin: 0 0 6px;
  }

  .edu-meta {
    font-size: 13px;
    color: var(--muted);
    margin: 0 0 8px;
  }

  /* ---------- Skills ---------- */
  .skill-tags {
    list-style: none;
    display: flex;
    flex-wrap: wrap;
    gap: 10px;
    margin: 0;
    padding: 0;
  }

  .skill-tags li {
    font-family: var(--font-display);
    font-size: 13px;
    background: var(--surface-2);
    border: 1px solid rgba(111, 231, 221, 0.25);
    color: var(--accent-2);
    padding: 8px 14px;
    border-radius: 999px;
    opacity: 0;
    transform: translateY(10px) scale(0.9);
    transition: opacity 0.4s ease, transform 0.4s ease, border-color 0.2s ease, background 0.2s ease;
    transition-delay: calc(var(--i) * 70ms);
  }

  .in-view .skill-tags li {
    opacity: 1;
    transform: translateY(0) scale(1);
  }

  .skill-tags li:hover {
    background: var(--accent-2);
    color: var(--bg);
    border-color: var(--accent-2);
  }

  /* ---------- Projects ---------- */
  .project-grid {
    display: grid;
    grid-template-columns: 1fr 1fr;
    gap: 18px;
  }

  @media (max-width: 620px) {
    .project-grid { grid-template-columns: 1fr; }
  }

  .project-card {
    background: var(--bg-alt);
    border: 1px solid rgba(242, 238, 230, 0.08);
    border-radius: 8px;
    overflow: hidden;
    transition: transform 0.25s ease, box-shadow 0.25s ease, border-color 0.25s ease;
  }

  .project-card:hover {
    transform: translateY(-6px);
    border-color: var(--accent);
    box-shadow: 0 16px 32px -16px rgba(242, 184, 7, 0.35);
  }

  .card-bar {
    display: flex;
    gap: 6px;
    padding: 10px 12px;
    background: rgba(0,0,0,0.15);
  }

  .card-bar .dot { width: 8px; height: 8px; }

  .project-card h3 {
    font-family: var(--font-display);
    font-size: 15px;
    margin: 14px 16px 6px;
  }

  .project-card p {
    font-size: 14px;
    color: var(--muted);
    margin: 0 16px 16px;
  }

  /* ---------- Video demo ---------- */
  .video-frame {
    background: var(--bg-alt);
    border: 1px solid rgba(242, 238, 230, 0.08);
    border-radius: 8px;
    overflow: hidden;
    max-width: 340px;
    transition: transform 0.25s ease, box-shadow 0.25s ease, border-color 0.25s ease;
  }

  .video-frame:hover {
    transform: translateY(-6px);
    border-color: var(--accent-2);
    box-shadow: 0 16px 32px -16px rgba(111, 231, 221, 0.35);
  }

  .video-embed {
    position: relative;
    width: 100%;
    aspect-ratio: 16 / 9;
  }

  .video-embed iframe {
    position: absolute;
    inset: 0;
    width: 100%;
    height: 100%;
    border: 0;
  }

  /* ---------- Contact ---------- */
  form { display: flex; flex-direction: column; gap: 20px; max-width: 480px; }

  .field { display: flex; flex-direction: column; gap: 6px; }

  label {
    font-family: var(--font-display);
    font-size: 12px;
    color: var(--muted);
  }

  input, textarea {
    background: var(--bg-alt);
    border: 1px solid rgba(242, 238, 230, 0.12);
    border-radius: 6px;
    padding: 12px 14px;
    color: var(--text);
    font-family: var(--font-body);
    font-size: 14px;
    transition: border-color 0.2s ease, box-shadow 0.2s ease;
  }

  input:focus, textarea:focus {
    outline: none;
    border-color: var(--accent-2);
    box-shadow: 0 0 0 3px rgba(111, 231, 221, 0.15);
  }

  .btn-row { display: flex; gap: 12px; }

  button {
    font-family: var(--font-display);
    font-size: 13px;
    padding: 12px 22px;
    border-radius: 6px;
    border: 1px solid transparent;
    cursor: pointer;
    transition: transform 0.15s ease, box-shadow 0.15s ease, background 0.2s ease;
  }

  button[type="submit"] {
    background: var(--accent-2);
    color: var(--bg);
  }

  button[type="submit"]:hover {
    box-shadow: 0 10px 24px -8px rgba(111, 231, 221, 0.5);
    transform: translateY(-2px);
  }

  button[type="reset"] {
    background: transparent;
    color: var(--muted);
    border-color: rgba(242, 238, 230, 0.15);
  }

  button[type="reset"]:hover { color: var(--text); border-color: var(--muted); }

  .form-success {
    font-family: var(--font-display);
    font-size: 13px;
    color: var(--accent-2);
    background: rgba(111, 231, 221, 0.08);
    border: 1px solid rgba(111, 231, 221, 0.3);
    border-radius: 6px;
    padding: 12px 14px;
    margin: 0;
    opacity: 0;
    transform: translateY(-6px);
    max-height: 0;
    overflow: hidden;
    transition: opacity 0.35s ease, transform 0.35s ease, max-height 0.35s ease, padding 0.35s ease, margin 0.35s ease;
  }

  .form-success.show {
    opacity: 1;
    transform: translateY(0);
    max-height: 60px;
    margin-top: 4px;
  }

  footer {
    text-align: center;
    padding: 28px 20px 40px;
    color: var(--muted);
    font-family: var(--font-display);
    font-size: 12px;
  }
</style>
</head>
<body>
  <div id="preloader" class="preloader" aria-hidden="true">
    <div>
      <p class="preloader-line"><span class="prompt">$</span> booting portfolio<span class="preloader-dots">...</span></p>
      <div class="preloader-bar"><div class="preloader-fill"></div></div>
    </div>
  </div>

  <div class="scroll-progress" aria-hidden="true"><div id="scroll-progress-fill" class="scroll-progress-fill"></div></div>

  <div class="bg-grid" aria-hidden="true"></div>

  <header class="hero">
    <div class="terminal-window">
      <div class="terminal-bar">
        <span class="dot red"></span><span class="dot yellow"></span><span class="dot green"></span>
        <span class="terminal-title">portfolio.sh</span>
      </div>
      <div class="terminal-body">
        <p class="prompt-line"><span class="prompt">$</span><span id="typewriter"></span><span class="cursor">▌</span></p>
        <div class="hero-content">
          <figure class="profile-frame">
            <img src="https://encrypted-tbn0.gstatic.com/images?q=tbn:ANd9GcT-JyRFAKSmCZSwGepLGMxADMcUE7mMphiyBZpPnKW0Ew&s" alt="Lakshmi's profile photo">
          </figure>
          <div class="hero-text">
            <h1>Lakshmi</h1>
            <p class="role">BCA student &middot; aspiring developer</p>
          </div>
        </div>
        <div class="hero-actions">
          <a class="btn-resume" href="#" download>Download Résumé</a>
          <div class="social-row">
            <a href="#" class="social-badge" aria-label="GitHub">GH</a>
            <a href="#" class="social-badge" aria-label="LinkedIn">in</a>
            <a href="mailto:youremail@example.com" class="social-badge" aria-label="Email">@</a>
          </div>
        </div>
      </div>
    </div>

    <div class="stats-strip">
      <div class="stat"><span class="stat-num" data-target="2">0</span><span class="stat-label">Projects Built</span></div>
      <div class="stat"><span class="stat-num" data-target="5">0</span><span class="stat-label">Core Skills</span></div>
      <div class="stat"><span class="stat-label status"><span class="status-dot"></span>Open to opportunities</span></div>
    </div>

    <nav class="tab-nav">
      <ul>
        <li><a href="#about" class="tab-link active" data-section="about">01 / about.md</a></li>
        <li><a href="#education" class="tab-link" data-section="education">02 / education.md</a></li>
        <li><a href="#skills" class="tab-link" data-section="skills">03 / skills.json</a></li>
        <li><a href="#projects" class="tab-link" data-section="projects">04 / projects</a></li>
        <li><a href="#demo" class="tab-link" data-section="demo">05 / demo.mp4</a></li>
        <li><a href="#contact" class="tab-link" data-section="contact">06 / contact.js</a></li>
      </ul>
    </nav>
  </header>

  <main>
    <section id="about" class="reveal">
      <p class="file-label">01 / about.md</p>
      <h2>About Me</h2>
      <p>Hi, I'm Lakshmi, a passionate BCA student aspiring to become a skilled developer.<br><br>This portfolio showcases my journey, skills, and projects that reflect my dedication to the world of technology.</p>
    </section>

    <section id="education" class="reveal">
      <p class="file-label">02 / education.md</p>
      <h2>Education</h2>
      <div class="edu-item">
        <div class="edu-dot"></div>
        <div>
          <h3>Bachelor of Computer Applications (BCA)</h3>
          <p class="edu-meta">[Your College/University Name] &middot; [Start Year]–[End Year]</p>
          <p>Coursework in programming fundamentals, web development, and database management — the foundation behind the projects on this page.</p>
        </div>
      </div>
    </section>

    <section id="skills" class="reveal">
      <p class="file-label">03 / skills.json</p>
      <h2>Skills</h2>
      <ul class="skill-tags">
        <li style="--i:0">HTML</li>
        <li style="--i:1">CSS</li>
        <li style="--i:2">JavaScript</li>
        <li style="--i:3">Python</li>
        <li style="--i:4">Database Management</li>
      </ul>
    </section>

    <section id="projects" class="reveal">
      <p class="file-label">04 / projects</p>
      <h2>Projects</h2>
      <div class="project-grid">
        <article class="project-card">
          <div class="card-bar"><span class="dot red"></span><span class="dot yellow"></span><span class="dot green"></span></div>
          <h3>Student Registration System</h3>
          <p>A web application that allows students to register for courses, view their schedules, and manage their academic profiles.</p>
        </article>
        <article class="project-card">
          <div class="card-bar"><span class="dot red"></span><span class="dot yellow"></span><span class="dot green"></span></div>
          <h3>E-commerce Website</h3>
          <p>A fully functional e-commerce platform for buying and selling products online.</p>
        </article>
      </div>
    </section>

    <section id="demo" class="reveal">
      <p class="file-label">05 / demo.mp4</p>
      <h2>Portfolio Walkthrough</h2>
      <p style="margin-bottom:18px;">A short video walking through this project.</p>
      <div class="video-frame">
        <div class="card-bar"><span class="dot red"></span><span class="dot yellow"></span><span class="dot green"></span></div>
        <div class="video-embed">
          <iframe src="https://www.youtube.com/embed/hveh4SkP_3c?si=FKvZERfPjYVAkiu0" title="Portfolio walkthrough video" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture; web-share" referrerpolicy="strict-origin-when-cross-origin" allowfullscreen></iframe>
        </div>
      </div>
    </section>

    <section id="contact" class="reveal">
      <p class="file-label">06 / contact.js</p>
      <h2>Contact Me</h2>
      <form id="contact-form">
        <div class="field">
          <label for="name">Name</label>
          <input type="text" id="name" name="name" required>
        </div>
        <div class="field">
          <label for="email">Email</label>
          <input type="email" id="email" name="email" required>
        </div>
        <div class="field">
          <label for="message">Message</label>
          <textarea id="message" name="message" rows="4" required></textarea>
        </div>
        <div class="btn-row">
          <button type="submit">Submit</button>
          <button type="reset">Reset</button>
        </div>
        <p id="form-success" class="form-success" role="status" aria-live="polite">
          <span class="prompt">$</span> your portfolio is successfully submitted
        </p>
      </form>
    </section>
  </main>

  <footer>
    <div class="social-row" style="justify-content:center; margin-bottom:14px;">
      <a href="#" class="social-badge" aria-label="GitHub">GH</a>
      <a href="#" class="social-badge" aria-label="LinkedIn">in</a>
      <a href="mailto:youremail@example.com" class="social-badge" aria-label="Email">@</a>
    </div>
    &copy; 2023 Lakshmi. All rights reserved.
  </footer>

  <button id="back-to-top" class="back-to-top" aria-label="Back to top">↑</button>

  <script>
    const prefersReducedMotion = window.matchMedia('(prefers-reduced-motion: reduce)').matches;

    // Preloader
    const preloader = document.getElementById('preloader');
    window.addEventListener('load', () => {
      setTimeout(() => preloader.classList.add('done'), prefersReducedMotion ? 0 : 1000);
    });

    // Scroll progress bar
    const progressFill = document.getElementById('scroll-progress-fill');
    function updateProgress() {
      const scrollTop = window.scrollY;
      const docHeight = document.documentElement.scrollHeight - window.innerHeight;
      const pct = docHeight > 0 ? (scrollTop / docHeight) * 100 : 0;
      progressFill.style.width = pct + '%';
    }
    window.addEventListener('scroll', updateProgress);
    updateProgress();

    // Cursor glow in hero
    const heroEl = document.querySelector('.hero');
    if (!prefersReducedMotion) {
      heroEl.addEventListener('mousemove', (e) => {
        const rect = heroEl.getBoundingClientRect();
        heroEl.style.setProperty('--mx', (e.clientX - rect.left) + 'px');
        heroEl.style.setProperty('--my', (e.clientY - rect.top) + 'px');
      });
    }

    // Stat counters
    document.querySelectorAll('.stat-num').forEach((el) => {
      const target = parseInt(el.dataset.target, 10);
      if (prefersReducedMotion) { el.textContent = target; return; }
      let current = 0;
      const step = Math.max(1, Math.round(target / 30));
      function tick() {
        current += step;
        if (current >= target) { el.textContent = target; return; }
        el.textContent = current;
        requestAnimationFrame(tick);
      }
      setTimeout(tick, 900);
    });

    // Back to top
    const backToTop = document.getElementById('back-to-top');
    window.addEventListener('scroll', () => {
      backToTop.classList.toggle('show', window.scrollY > 400);
    });
    backToTop.addEventListener('click', () => {
      window.scrollTo({ top: 0, behavior: prefersReducedMotion ? 'auto' : 'smooth' });
    });

    // Typewriter effect in the hero terminal
    const text = 'whoami  →  "Lakshmi — BCA student, aspiring developer"';
    const el = document.getElementById('typewriter');
    let i = 0;
    function type() {
      if (i <= text.length) {
        el.textContent = text.slice(0, i);
        i++;
        setTimeout(type, 28);
      }
    }
    if (window.matchMedia('(prefers-reduced-motion: reduce)').matches) {
      el.textContent = text;
    } else {
      type();
    }

    // Scroll-reveal for sections
    const revealEls = document.querySelectorAll('.reveal');
    const revealObserver = new IntersectionObserver((entries) => {
      entries.forEach(entry => {
        if (entry.isIntersecting) {
          entry.target.classList.add('in-view');
          revealObserver.unobserve(entry.target);
        }
      });
    }, { threshold: 0.2 });
    revealEls.forEach(el => revealObserver.observe(el));

    // Contact form: show success message on submit (no backend wired up)
    const contactForm = document.getElementById('contact-form');
    const formSuccess = document.getElementById('form-success');
    contactForm.addEventListener('submit', (e) => {
      e.preventDefault();
      if (!contactForm.checkValidity()) {
        contactForm.reportValidity();
        return;
      }
      formSuccess.classList.add('show');
      contactForm.reset();
    });
    contactForm.addEventListener('reset', () => {
      formSuccess.classList.remove('show');
    });

    // Scrollspy for tab nav
    const tabLinks = document.querySelectorAll('.tab-link');
    const sections = document.querySelectorAll('main section');
    const spyObserver = new IntersectionObserver((entries) => {
      entries.forEach(entry => {
        if (entry.isIntersecting) {
          const id = entry.target.getAttribute('id');
          tabLinks.forEach(link => {
            link.classList.toggle('active', link.dataset.section === id);
          });
        }
      });
    }, { rootMargin: '-40% 0px -50% 0px' });
    sections.forEach(sec => spyObserver.observe(sec));
  </script>
</body>
</html>
