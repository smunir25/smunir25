<!DOCTYPE html>
<html lang="en">
<head>
<meta charset="UTF-8" />
<meta name="viewport" content="width=device-width, initial-scale=1.0"/>
<title>Saad Munir — AI Engineer</title>
<link href="https://fonts.googleapis.com/css2?family=Space+Mono:ital,wght@0,400;0,700;1,400&family=Syne:wght@400;700;800&display=swap" rel="stylesheet"/>
<style>
  :root {
    --bg: #060610;
    --surface: #0d0d1f;
    --border: #1e1e3f;
    --accent1: #7fdbff;
    --accent2: #ff4ecd;
    --accent3: #39ff9f;
    --accent4: #ffcc00;
    --text: #e2e2f0;
    --muted: #6b6b9a;
    --glow1: rgba(127,219,255,0.15);
    --glow2: rgba(255,78,205,0.15);
  }

  *, *::before, *::after { box-sizing: border-box; margin: 0; padding: 0; }

  html { scroll-behavior: smooth; }

  body {
    background: var(--bg);
    color: var(--text);
    font-family: 'Space Mono', monospace;
    min-height: 100vh;
    overflow-x: hidden;
    cursor: crosshair;
  }

  /* ── GRID BACKGROUND ── */
  body::before {
    content: '';
    position: fixed;
    inset: 0;
    background-image:
      linear-gradient(rgba(127,219,255,0.03) 1px, transparent 1px),
      linear-gradient(90deg, rgba(127,219,255,0.03) 1px, transparent 1px);
    background-size: 40px 40px;
    pointer-events: none;
    z-index: 0;
  }

  /* ── SCAN LINE ── */
  body::after {
    content: '';
    position: fixed;
    top: -100%;
    left: 0;
    width: 100%;
    height: 3px;
    background: linear-gradient(90deg, transparent, var(--accent1), transparent);
    animation: scan 6s linear infinite;
    pointer-events: none;
    z-index: 999;
    opacity: 0.4;
  }
  @keyframes scan { to { top: 110%; } }

  .container {
    max-width: 900px;
    margin: 0 auto;
    padding: 60px 24px;
    position: relative;
    z-index: 1;
  }

  /* ── HERO ── */
  .hero {
    text-align: center;
    padding: 60px 0 40px;
    position: relative;
  }

  .hero-badge {
    display: inline-block;
    font-size: 11px;
    letter-spacing: 0.2em;
    text-transform: uppercase;
    color: var(--accent3);
    border: 1px solid var(--accent3);
    padding: 4px 14px;
    border-radius: 2px;
    margin-bottom: 24px;
    animation: fadeUp 0.6s ease both;
  }

  .hero h1 {
    font-family: 'Syne', sans-serif;
    font-size: clamp(2.8rem, 7vw, 5.5rem);
    font-weight: 800;
    line-height: 1;
    background: linear-gradient(135deg, #fff 0%, var(--accent1) 50%, var(--accent2) 100%);
    -webkit-background-clip: text;
    -webkit-text-fill-color: transparent;
    background-clip: text;
    animation: fadeUp 0.6s 0.1s ease both;
    letter-spacing: -0.02em;
  }

  .hero-sub {
    font-size: 13px;
    color: var(--muted);
    margin-top: 14px;
    letter-spacing: 0.1em;
    animation: fadeUp 0.6s 0.2s ease both;
  }

  .hero-sub span { color: var(--accent1); }

  .hero-tagline {
    font-size: 13px;
    color: var(--accent4);
    font-style: italic;
    margin-top: 20px;
    animation: fadeUp 0.6s 0.3s ease both;
  }

  .hero-orb {
    position: absolute;
    width: 400px;
    height: 400px;
    border-radius: 50%;
    background: radial-gradient(circle, var(--glow1) 0%, transparent 70%);
    top: 50%;
    left: 50%;
    transform: translate(-50%,-50%);
    pointer-events: none;
    animation: pulse 4s ease-in-out infinite;
  }
  @keyframes pulse { 0%,100%{opacity:0.5;transform:translate(-50%,-50%) scale(1)} 50%{opacity:1;transform:translate(-50%,-50%) scale(1.1)} }

  /* ── BADGES ── */
  .badges {
    display: flex;
    justify-content: center;
    gap: 12px;
    flex-wrap: wrap;
    margin: 30px 0;
    animation: fadeUp 0.6s 0.4s ease both;
  }
  .badge {
    display: flex;
    align-items: center;
    gap: 8px;
    padding: 8px 16px;
    border: 1px solid var(--border);
    border-radius: 3px;
    font-size: 12px;
    color: var(--muted);
    background: var(--surface);
    text-decoration: none;
    transition: all 0.2s;
    letter-spacing: 0.05em;
  }
  .badge:hover { border-color: var(--accent1); color: var(--accent1); box-shadow: 0 0 12px var(--glow1); }
  .badge .dot { width: 7px; height: 7px; border-radius: 50%; }

  /* ── SECTION ── */
  .section {
    margin: 50px 0;
    animation: fadeUp 0.6s ease both;
  }
  .section-header {
    display: flex;
    align-items: center;
    gap: 12px;
    margin-bottom: 24px;
  }
  .section-header h2 {
    font-family: 'Syne', sans-serif;
    font-size: 13px;
    font-weight: 700;
    letter-spacing: 0.2em;
    text-transform: uppercase;
    color: var(--text);
  }
  .section-line {
    flex: 1;
    height: 1px;
    background: linear-gradient(90deg, var(--border), transparent);
  }
  .section-num {
    font-size: 11px;
    color: var(--accent2);
    font-family: 'Space Mono', monospace;
  }

  /* ── TERMINAL CARD ── */
  .terminal {
    background: var(--surface);
    border: 1px solid var(--border);
    border-radius: 6px;
    overflow: hidden;
  }
  .terminal-bar {
    display: flex;
    align-items: center;
    gap: 7px;
    padding: 10px 16px;
    background: rgba(255,255,255,0.03);
    border-bottom: 1px solid var(--border);
  }
  .terminal-bar .dot-r { background:#ff5f57; }
  .terminal-bar .dot-y { background:#ffbd2e; }
  .terminal-bar .dot-g { background:#28ca41; }
  .terminal-bar span { width:12px;height:12px;border-radius:50%;display:inline-block; }
  .terminal-title { font-size: 11px; color: var(--muted); margin-left: 8px; letter-spacing: 0.1em; }
  .terminal-body { padding: 22px; font-size: 13px; line-height: 2; }
  .t-key { color: var(--accent2); }
  .t-val { color: var(--accent3); }
  .t-str { color: var(--accent4); }
  .t-bracket { color: var(--muted); }
  .t-comment { color: #3d3d60; font-style: italic; }
  .t-prompt { color: var(--accent1); }

  /* ── SKILLS GRID ── */
  .skills-grid {
    display: grid;
    grid-template-columns: repeat(auto-fill, minmax(130px, 1fr));
    gap: 10px;
  }
  .skill-chip {
    padding: 10px 14px;
    border: 1px solid var(--border);
    border-radius: 4px;
    font-size: 11px;
    color: var(--muted);
    background: var(--surface);
    letter-spacing: 0.08em;
    transition: all 0.2s;
    position: relative;
    overflow: hidden;
    text-align: center;
  }
  .skill-chip::before {
    content: '';
    position: absolute;
    bottom: 0; left: 0;
    height: 2px;
    width: 0;
    background: var(--accent1);
    transition: width 0.3s ease;
  }
  .skill-chip:hover { border-color: var(--accent1); color: var(--accent1); box-shadow: 0 0 10px var(--glow1); }
  .skill-chip:hover::before { width: 100%; }
  .skill-chip.pink:hover { border-color: var(--accent2); color: var(--accent2); }
  .skill-chip.pink::before { background: var(--accent2); }
  .skill-chip.green:hover { border-color: var(--accent3); color: var(--accent3); }
  .skill-chip.green::before { background: var(--accent3); }
  .skill-chip.yellow:hover { border-color: var(--accent4); color: var(--accent4); }
  .skill-chip.yellow::before { background: var(--accent4); }

  /* ── PROJECTS ── */
  .projects-grid {
    display: grid;
    grid-template-columns: 1fr 1fr;
    gap: 14px;
  }
  @media(max-width:600px){ .projects-grid { grid-template-columns: 1fr; } }
  .project-card {
    background: var(--surface);
    border: 1px solid var(--border);
    border-radius: 6px;
    padding: 22px;
    transition: all 0.25s;
    position: relative;
    overflow: hidden;
  }
  .project-card::after {
    content: '';
    position: absolute;
    inset: 0;
    opacity: 0;
    background: radial-gradient(circle at 30% 30%, var(--glow1), transparent 60%);
    transition: opacity 0.3s;
  }
  .project-card:hover { border-color: var(--accent1); transform: translateY(-3px); box-shadow: 0 12px 40px rgba(0,0,0,0.4); }
  .project-card:hover::after { opacity: 1; }
  .project-icon { font-size: 22px; margin-bottom: 12px; }
  .project-title {
    font-family: 'Syne', sans-serif;
    font-size: 14px;
    font-weight: 700;
    color: var(--text);
    margin-bottom: 8px;
  }
  .project-desc { font-size: 11px; color: var(--muted); line-height: 1.7; }
  .project-tag {
    display: inline-block;
    margin-top: 12px;
    font-size: 10px;
    color: var(--accent3);
    border: 1px solid rgba(57,255,159,0.3);
    padding: 2px 8px;
    border-radius: 2px;
    letter-spacing: 0.1em;
  }

  /* ── STATS ── */
  .stats-row {
    display: flex;
    justify-content: center;
    flex-wrap: wrap;
    gap: 14px;
    margin: 10px 0;
  }
  .stat-box {
    flex: 1;
    min-width: 140px;
    background: var(--surface);
    border: 1px solid var(--border);
    border-radius: 6px;
    padding: 22px 16px;
    text-align: center;
    transition: all 0.2s;
  }
  .stat-box:hover { border-color: var(--accent2); box-shadow: 0 0 20px var(--glow2); }
  .stat-num {
    font-family: 'Syne', sans-serif;
    font-size: 2rem;
    font-weight: 800;
    background: linear-gradient(135deg, var(--accent1), var(--accent2));
    -webkit-background-clip: text;
    -webkit-text-fill-color: transparent;
    background-clip: text;
  }
  .stat-label { font-size: 11px; color: var(--muted); margin-top: 4px; letter-spacing: 0.1em; }

  /* ── TIMELINE ── */
  .timeline { position: relative; padding-left: 24px; }
  .timeline::before {
    content: '';
    position: absolute;
    left: 0; top: 4px; bottom: 4px;
    width: 1px;
    background: linear-gradient(to bottom, var(--accent1), var(--accent2), transparent);
  }
  .tl-item { position: relative; margin-bottom: 28px; }
  .tl-item::before {
    content: '';
    position: absolute;
    left: -28px; top: 5px;
    width: 9px; height: 9px;
    border-radius: 50%;
    background: var(--accent1);
    box-shadow: 0 0 8px var(--accent1);
  }
  .tl-year { font-size: 11px; color: var(--accent3); letter-spacing: 0.1em; margin-bottom: 4px; }
  .tl-title { font-family: 'Syne', sans-serif; font-size: 14px; font-weight: 700; color: var(--text); }
  .tl-org { font-size: 11px; color: var(--accent1); margin-top: 2px; }
  .tl-desc { font-size: 11px; color: var(--muted); margin-top: 6px; line-height: 1.7; }

  /* ── CONNECT ── */
  .connect-grid {
    display: grid;
    grid-template-columns: 1fr 1fr;
    gap: 12px;
  }
  @media(max-width:500px){ .connect-grid { grid-template-columns: 1fr; } }
  .connect-card {
    display: flex;
    align-items: center;
    gap: 14px;
    padding: 18px;
    background: var(--surface);
    border: 1px solid var(--border);
    border-radius: 6px;
    text-decoration: none;
    transition: all 0.2s;
  }
  .connect-card:hover { border-color: var(--accent2); box-shadow: 0 0 16px var(--glow2); transform: translateX(4px); }
  .connect-icon { font-size: 20px; }
  .connect-label { font-size: 12px; color: var(--muted); letter-spacing: 0.05em; }
  .connect-val { font-size: 13px; color: var(--text); margin-top: 2px; }

  /* ── FOOTER ── */
  .footer {
    text-align: center;
    padding: 40px 0 60px;
    font-size: 11px;
    color: var(--muted);
    letter-spacing: 0.1em;
    border-top: 1px solid var(--border);
    margin-top: 60px;
  }
  .footer span { color: var(--accent2); }

  @keyframes fadeUp {
    from { opacity: 0; transform: translateY(16px); }
    to { opacity: 1; transform: translateY(0); }
  }

  .blink { animation: blink 1s step-end infinite; }
  @keyframes blink { 0%,100%{opacity:1} 50%{opacity:0} }

  /* stagger sections */
  .s1 { animation-delay: 0.1s; }
  .s2 { animation-delay: 0.2s; }
  .s3 { animation-delay: 0.3s; }
  .s4 { animation-delay: 0.4s; }
  .s5 { animation-delay: 0.5s; }
</style>
</head>
<body>
<div class="container">

  <!-- HERO -->
  <div class="hero">
    <div class="hero-orb"></div>
    <div class="hero-badge">Senior AI Engineer · Islamabad, PK</div>
    <h1>Saad Munir</h1>
    <div class="hero-sub">
      <span>@QLU.ai</span> &nbsp;·&nbsp; Deep Learning · NLP · LLMs · Voice AI · Agentic Systems
    </div>
    <div class="hero-tagline">"Engineering impact through AI — one real-world challenge at a time."</div>
  </div>

  <!-- BADGES -->
  <div class="badges">
    <a href="https://linkedin.com/in/saadmunir" class="badge" target="_blank">
      <span class="dot" style="background:#0A66C2"></span> LinkedIn
    </a>
    <a href="mailto:saad@email.com" class="badge">
      <span class="dot" style="background:#EA4335"></span> Email
    </a>
    <a href="#" class="badge">
      <span class="dot" style="background:var(--accent3)"></span> QLU.ai
    </a>
    <a href="#" class="badge">
      <span class="dot" style="background:var(--accent4)"></span> Published Paper
    </a>
  </div>

  <!-- ABOUT — TERMINAL -->
  <div class="section s1">
    <div class="section-header">
      <span class="section-num">01</span>
      <h2>About</h2>
      <div class="section-line"></div>
    </div>
    <div class="terminal">
      <div class="terminal-bar">
        <span class="dot-r"></span>
        <span class="dot-y"></span>
        <span class="dot-g"></span>
        <span class="terminal-title">saad@qlu.ai ~ profile.py</span>
      </div>
      <div class="terminal-body">
        <div><span class="t-comment"># Senior AI Engineer building real-world intelligent systems</span></div>
        <div>&nbsp;</div>
        <div><span class="t-key">profile</span> <span class="t-bracket">=</span> <span class="t-bracket">{</span></div>
        <div>&nbsp;&nbsp;<span class="t-str">"name"</span>       : <span class="t-val">"Saad Munir"</span>,</div>
        <div>&nbsp;&nbsp;<span class="t-str">"role"</span>       : <span class="t-val">"Senior AI Engineer @ QLU.ai"</span>,</div>
        <div>&nbsp;&nbsp;<span class="t-str">"location"</span>   : <span class="t-val">"Islamabad, Pakistan 🇵🇰"</span>,</div>
        <div>&nbsp;&nbsp;<span class="t-str">"focus"</span>      : <span class="t-bracket">[</span><span class="t-val">"LLMs"</span>, <span class="t-val">"NLP"</span>, <span class="t-val">"Voice AI"</span>, <span class="t-val">"Agentic AI"</span><span class="t-bracket">]</span>,</div>
        <div>&nbsp;&nbsp;<span class="t-str">"published"</span>  : <span class="t-val">"BiL-FaND @ Int'l Journal of ML & Cybernetics"</span>,</div>
        <div>&nbsp;&nbsp;<span class="t-str">"languages"</span>  : <span class="t-bracket">[</span><span class="t-val">"English"</span>, <span class="t-val">"Urdu"</span><span class="t-bracket">]</span>,</div>
        <div>&nbsp;&nbsp;<span class="t-str">"superpower"</span> : <span class="t-val">"Breaking complexity barriers 💥"</span></div>
        <div><span class="t-bracket">}</span></div>
        <div>&nbsp;</div>
        <div><span class="t-prompt">▶</span> <span class="t-comment">ready to collaborate</span><span class="blink">_</span></div>
      </div>
    </div>
  </div>

  <!-- STATS -->
  <div class="section s2">
    <div class="stats-row">
      <div class="stat-box">
        <div class="stat-num">5+</div>
        <div class="stat-label">Years in AI</div>
      </div>
      <div class="stat-box">
        <div class="stat-num">1</div>
        <div class="stat-label">Published Paper</div>
      </div>
      <div class="stat-box">
        <div class="stat-num">3+</div>
        <div class="stat-label">Voice AI Systems</div>
      </div>
      <div class="stat-box">
        <div class="stat-num">2</div>
        <div class="stat-label">Degrees</div>
      </div>
    </div>
  </div>

  <!-- SKILLS -->
  <div class="section s2">
    <div class="section-header">
      <span class="section-num">02</span>
      <h2>Skills & Tools</h2>
      <div class="section-line"></div>
    </div>
    <div class="skills-grid">
      <div class="skill-chip">Python</div>
      <div class="skill-chip">SQL</div>
      <div class="skill-chip pink">PyTorch</div>
      <div class="skill-chip pink">TensorFlow</div>
      <div class="skill-chip pink">FastAPI</div>
      <div class="skill-chip green">LLMs</div>
      <div class="skill-chip green">NLP</div>
      <div class="skill-chip green">Transformers</div>
      <div class="skill-chip green">Gen AI</div>
      <div class="skill-chip">Computer Vision</div>
      <div class="skill-chip yellow">ASR / TTS</div>
      <div class="skill-chip yellow">VAD</div>
      <div class="skill-chip">Elasticsearch</div>
      <div class="skill-chip">Vector DBs</div>
      <div class="skill-chip pink">Semantic Search</div>
      <div class="skill-chip green">Agentic AI</div>
    </div>
  </div>

  <!-- PROJECTS -->
  <div class="section s3">
    <div class="section-header">
      <span class="section-num">03</span>
      <h2>Featured Projects</h2>
      <div class="section-line"></div>
    </div>
    <div class="projects-grid">
      <div class="project-card">
        <div class="project-icon">🤖</div>
        <div class="project-title">Recruitment Automation</div>
        <div class="project-desc">LLM-powered candidate matching & semantic search pipelines at scale. Transformed executive recruitment with intelligent automation.</div>
        <span class="project-tag">QLU.ai</span>
      </div>
      <div class="project-card">
        <div class="project-icon">📝</div>
        <div class="project-title">Prescriptions Digitization</div>
        <div class="project-desc">Led end-to-end AI system converting handwritten prescriptions to structured digital data. Mentored cross-functional teams @ DataInsight.</div>
        <span class="project-tag">DataInsight</span>
      </div>
      <div class="project-card">
        <div class="project-icon">🔬</div>
        <div class="project-title">BiL-FaND</div>
        <div class="project-desc">Fake News Detection research published in the International Journal of Machine Learning & Cybernetics. Bilingual approach.</div>
        <span class="project-tag">Published</span>
      </div>
      <div class="project-card">
        <div class="project-icon">🎙️</div>
        <div class="project-title">Voice AI Systems</div>
        <div class="project-desc">Engineered production-grade ASR, TTS & VAD modules for scalable automation platforms. Full speech pipeline from scratch.</div>
        <span class="project-tag">Voice · Speech</span>
      </div>
    </div>
  </div>

  <!-- EDUCATION TIMELINE -->
  <div class="section s4">
    <div class="section-header">
      <span class="section-num">04</span>
      <h2>Education & Certs</h2>
      <div class="section-line"></div>
    </div>
    <div class="timeline">
      <div class="tl-item">
        <div class="tl-year">MS DEGREE</div>
        <div class="tl-title">Artificial Intelligence</div>
        <div class="tl-org">National University of Computer & Emerging Sciences</div>
      </div>
      <div class="tl-item">
        <div class="tl-year">BS DEGREE</div>
        <div class="tl-title">Software Engineering</div>
        <div class="tl-org">COMSATS Institute of Information and Technology</div>
      </div>
      <div class="tl-item">
        <div class="tl-year">CERT</div>
        <div class="tl-title">Scrum Fundamentals Certified</div>
        <div class="tl-org">SCRUMstudy</div>
      </div>
      <div class="tl-item">
        <div class="tl-year">CERT</div>
        <div class="tl-title">ClickUp Expert Certificate</div>
        <div class="tl-org">ClickUp University</div>
      </div>
    </div>
  </div>

  <!-- CONNECT -->
  <div class="section s5">
    <div class="section-header">
      <span class="section-num">05</span>
      <h2>Connect</h2>
      <div class="section-line"></div>
    </div>
    <div class="connect-grid">
      <a href="https://linkedin.com/in/saadmunir" class="connect-card" target="_blank">
        <div class="connect-icon">💼</div>
        <div>
          <div class="connect-label">LinkedIn</div>
          <div class="connect-val">linkedin.com/in/saadmunir</div>
        </div>
      </a>
      <a href="mailto:saad@email.com" class="connect-card">
        <div class="connect-icon">📧</div>
        <div>
          <div class="connect-label">Email</div>
          <div class="connect-val">saad@email.com</div>
        </div>
      </a>
    </div>
  </div>

  <!-- FOOTER -->
  <div class="footer">
    <div>Built with <span>♥</span> and Python · Open to collaboration & opportunities</div>
    <div style="margin-top:8px;">Let's build the future of intelligent systems.</div>
  </div>

</div>
</body>
</html>
