<!DOCTYPE html>
<html lang="en">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>Samuel Siri — README.md</title>
<link href="https://fonts.googleapis.com/css2?family=JetBrains+Mono:ital,wght@0,100..800;1,100..800&family=Fira+Code:wght@300;400;500;600;700&display=swap" rel="stylesheet">
<style>
  :root {
    --bg: #080b10;
    --bg2: #0d1117;
    --bg3: #161b22;
    --surface: #111827;
    --border: #21262d;
    --purple: #a855f7;
    --purple-dim: #7c3aed;
    --purple-glow: rgba(168,85,247,0.15);
    --green: #39d353;
    --cyan: #58d6f0;
    --orange: #f97316;
    --red: #f87171;
    --text: #e6edf3;
    --muted: #8b949e;
    --dim: #484f58;
  }

  * { margin: 0; padding: 0; box-sizing: border-box; }

  body {
    background: var(--bg);
    color: var(--text);
    font-family: 'JetBrains Mono', monospace;
    min-height: 100vh;
    overflow-x: hidden;
  }

  /* GRID NOISE BG */
  body::before {
    content: '';
    position: fixed;
    inset: 0;
    background-image:
      linear-gradient(rgba(168,85,247,0.03) 1px, transparent 1px),
      linear-gradient(90deg, rgba(168,85,247,0.03) 1px, transparent 1px);
    background-size: 40px 40px;
    pointer-events: none;
    z-index: 0;
  }

  /* SCANLINES */
  body::after {
    content: '';
    position: fixed;
    inset: 0;
    background: repeating-linear-gradient(
      0deg,
      transparent,
      transparent 2px,
      rgba(0,0,0,0.07) 2px,
      rgba(0,0,0,0.07) 4px
    );
    pointer-events: none;
    z-index: 0;
  }

  .container {
    max-width: 900px;
    margin: 0 auto;
    padding: 2rem 1.5rem 4rem;
    position: relative;
    z-index: 1;
  }

  /* ── TERMINAL HEADER ── */
  .terminal-bar {
    background: var(--bg3);
    border: 1px solid var(--border);
    border-radius: 10px 10px 0 0;
    padding: 0.6rem 1rem;
    display: flex;
    align-items: center;
    gap: 0.5rem;
  }
  .dot { width: 12px; height: 12px; border-radius: 50%; }
  .dot-r { background: #ff5f57; }
  .dot-y { background: #ffbd2e; }
  .dot-g { background: #28c840; }
  .term-title { color: var(--muted); font-size: 0.75rem; margin-left: auto; margin-right: auto; }

  /* ── ASCII HERO ── */
  .ascii-hero {
    background: var(--bg2);
    border: 1px solid var(--border);
    border-top: none;
    border-radius: 0 0 10px 10px;
    padding: 2rem 1.5rem 1.5rem;
    text-align: center;
    position: relative;
    overflow: hidden;
    margin-bottom: 2rem;
  }

  .ascii-hero::before {
    content: '';
    position: absolute;
    inset: 0;
    background: radial-gradient(ellipse at 50% 0%, rgba(168,85,247,0.12) 0%, transparent 65%);
    pointer-events: none;
  }

  .ascii-art {
    font-size: clamp(0.35rem, 1.1vw, 0.72rem);
    line-height: 1.2;
    color: var(--purple);
    text-shadow: 0 0 20px rgba(168,85,247,0.6);
    white-space: pre;
    font-weight: 700;
    animation: glitch-ascii 8s infinite;
    letter-spacing: 0;
  }

  @keyframes glitch-ascii {
    0%, 92%, 100% { transform: none; filter: none; opacity: 1; }
    93% { transform: translateX(-2px); filter: hue-rotate(90deg); opacity: 0.85; }
    94% { transform: translateX(3px); opacity: 1; }
    95% { transform: translateX(-1px); filter: hue-rotate(-90deg); }
    96% { transform: none; filter: none; }
  }

  /* TYPING BADGE */
  .typing-badge {
    display: inline-block;
    margin-top: 1.2rem;
    padding: 0.4rem 1.2rem;
    border: 1px solid var(--purple-dim);
    border-radius: 4px;
    background: rgba(168,85,247,0.07);
    color: var(--purple);
    font-size: 0.85rem;
    position: relative;
  }
  .typing-badge .cursor {
    display: inline-block;
    width: 2px;
    height: 1em;
    background: var(--purple);
    margin-left: 2px;
    vertical-align: text-bottom;
    animation: blink 1s step-end infinite;
  }
  @keyframes blink { 0%,100% { opacity:1; } 50% { opacity:0; } }

  /* ── SECTION CARDS ── */
  .section {
    margin-bottom: 1.5rem;
    animation: fadeUp 0.6s ease both;
  }
  .section:nth-child(2) { animation-delay: 0.1s; }
  .section:nth-child(3) { animation-delay: 0.2s; }
  .section:nth-child(4) { animation-delay: 0.3s; }
  .section:nth-child(5) { animation-delay: 0.4s; }
  .section:nth-child(6) { animation-delay: 0.5s; }
  .section:nth-child(7) { animation-delay: 0.6s; }
  @keyframes fadeUp {
    from { opacity:0; transform:translateY(20px); }
    to { opacity:1; transform:translateY(0); }
  }

  .card {
    background: var(--bg2);
    border: 1px solid var(--border);
    border-radius: 8px;
    overflow: hidden;
    transition: border-color 0.3s, box-shadow 0.3s;
  }
  .card:hover {
    border-color: var(--purple-dim);
    box-shadow: 0 0 20px rgba(168,85,247,0.08);
  }

  .card-header {
    background: var(--bg3);
    padding: 0.6rem 1rem;
    border-bottom: 1px solid var(--border);
    display: flex;
    align-items: center;
    gap: 0.5rem;
    font-size: 0.75rem;
    color: var(--muted);
  }
  .card-header .icon { color: var(--purple); }
  .card-header .filename { color: var(--text); font-weight: 500; }
  .card-header .badge {
    margin-left: auto;
    background: var(--purple-glow);
    color: var(--purple);
    padding: 0.1rem 0.5rem;
    border-radius: 3px;
    font-size: 0.7rem;
    border: 1px solid rgba(168,85,247,0.3);
  }

  .card-body { padding: 1.25rem 1.5rem; }

  /* ── INTRO SECTION ── */
  .intro-text {
    font-size: 0.88rem;
    line-height: 1.9;
    color: var(--muted);
  }
  .intro-text .highlight { color: var(--purple); font-weight: 600; }
  .intro-text .green { color: var(--green); }
  .intro-text .cyan { color: var(--cyan); }

  .comment { color: #4b5563; font-style: italic; }
  .string { color: var(--green); }
  .keyword { color: var(--purple); }
  .variable { color: var(--cyan); }
  .number { color: var(--orange); }
  .fn { color: #60a5fa; }

  /* ── SKILLS GRID ── */
  .skills-section { padding: 1.25rem 1.5rem; }
  .skills-category {
    margin-bottom: 1.2rem;
  }
  .skills-label {
    font-size: 0.7rem;
    color: var(--muted);
    text-transform: uppercase;
    letter-spacing: 0.1em;
    margin-bottom: 0.6rem;
    display: flex;
    align-items: center;
    gap: 0.5rem;
  }
  .skills-label::after {
    content: '';
    flex: 1;
    height: 1px;
    background: var(--border);
  }

  .pills {
    display: flex;
    flex-wrap: wrap;
    gap: 0.4rem;
  }
  .pill {
    display: inline-flex;
    align-items: center;
    gap: 0.4rem;
    padding: 0.25rem 0.7rem;
    border-radius: 4px;
    font-size: 0.75rem;
    border: 1px solid var(--border);
    background: var(--surface);
    color: var(--muted);
    cursor: default;
    transition: all 0.2s;
    position: relative;
    overflow: hidden;
  }
  .pill::before {
    content: '';
    position: absolute;
    inset: 0;
    background: var(--purple-glow);
    opacity: 0;
    transition: opacity 0.2s;
  }
  .pill:hover::before { opacity: 1; }
  .pill:hover { color: var(--purple); border-color: var(--purple-dim); transform: translateY(-1px); }
  .pill .dot2 { width: 6px; height: 6px; border-radius: 50%; background: var(--purple); opacity: 0.7; }

  /* ── CODE BLOCK ── */
  .code-block {
    background: var(--bg);
    border-radius: 6px;
    padding: 1.2rem 1.5rem;
    font-size: 0.8rem;
    line-height: 1.8;
    position: relative;
    border: 1px solid var(--border);
  }
  .code-block .line-num {
    color: var(--dim);
    user-select: none;
    margin-right: 1.5rem;
    display: inline-block;
    min-width: 1.5rem;
    text-align: right;
  }
  .code-block .line:hover { background: rgba(255,255,255,0.02); border-radius: 2px; }

  /* ── STATS ── */
  .stats-grid {
    display: grid;
    grid-template-columns: repeat(3, 1fr);
    gap: 1rem;
    padding: 1.25rem 1.5rem;
  }
  .stat-card {
    background: var(--bg);
    border: 1px solid var(--border);
    border-radius: 6px;
    padding: 1rem;
    text-align: center;
    transition: all 0.3s;
  }
  .stat-card:hover {
    border-color: var(--purple-dim);
    transform: translateY(-2px);
    box-shadow: 0 8px 20px rgba(168,85,247,0.1);
  }
  .stat-num {
    font-size: 1.5rem;
    font-weight: 700;
    color: var(--purple);
    text-shadow: 0 0 15px rgba(168,85,247,0.4);
  }
  .stat-label { font-size: 0.65rem; color: var(--muted); margin-top: 0.2rem; }

  /* ── ACTIVITY BARS ── */
  .activity { padding: 1.25rem 1.5rem; }
  .activity-row {
    display: flex;
    align-items: center;
    gap: 0.8rem;
    margin-bottom: 0.7rem;
    font-size: 0.78rem;
  }
  .activity-lang { color: var(--muted); min-width: 100px; }
  .activity-bar-wrap {
    flex: 1;
    height: 6px;
    background: var(--bg3);
    border-radius: 3px;
    overflow: hidden;
  }
  .activity-bar {
    height: 100%;
    border-radius: 3px;
    background: linear-gradient(90deg, var(--purple-dim), var(--purple));
    transform-origin: left;
    animation: barIn 1.2s cubic-bezier(0.16,1,0.3,1) both;
  }
  @keyframes barIn { from { transform: scaleX(0); } to { transform: scaleX(1); } }
  .activity-pct { color: var(--muted); font-size: 0.72rem; min-width: 2.5rem; text-align: right; }

  /* ── WHAT I'M UP TO ── */
  .up-to-list { padding: 1.25rem 1.5rem; }
  .up-to-item {
    display: flex;
    align-items: flex-start;
    gap: 0.8rem;
    padding: 0.7rem 0;
    border-bottom: 1px solid rgba(33,38,45,0.6);
    font-size: 0.82rem;
  }
  .up-to-item:last-child { border-bottom: none; }
  .up-to-icon {
    width: 28px;
    height: 28px;
    background: var(--purple-glow);
    border: 1px solid rgba(168,85,247,0.2);
    border-radius: 5px;
    display: flex;
    align-items: center;
    justify-content: center;
    font-size: 0.9rem;
    flex-shrink: 0;
  }
  .up-to-content .title { color: var(--text); font-weight: 500; }
  .up-to-content .desc { color: var(--muted); font-size: 0.75rem; margin-top: 0.15rem; }

  /* ── CONTACT ── */
  .contact-section {
    padding: 1.5rem;
    text-align: center;
  }
  .contact-btn {
    display: inline-flex;
    align-items: center;
    gap: 0.6rem;
    padding: 0.75rem 1.8rem;
    background: transparent;
    border: 1px solid var(--purple-dim);
    border-radius: 6px;
    color: var(--purple);
    font-family: inherit;
    font-size: 0.82rem;
    font-weight: 600;
    cursor: pointer;
    text-decoration: none;
    position: relative;
    overflow: hidden;
    transition: all 0.3s;
  }
  .contact-btn::before {
    content: '';
    position: absolute;
    inset: 0;
    background: var(--purple-glow);
    opacity: 0;
    transition: opacity 0.3s;
  }
  .contact-btn:hover::before { opacity: 1; }
  .contact-btn:hover { box-shadow: 0 0 25px rgba(168,85,247,0.25); transform: translateY(-1px); }

  .contact-tagline {
    margin-top: 1rem;
    font-size: 0.72rem;
    color: var(--dim);
    font-style: italic;
  }

  /* ── FOOTER WAVE ── */
  .footer-wave {
    margin-top: 2rem;
    height: 4px;
    background: linear-gradient(90deg, transparent, var(--purple), var(--cyan), var(--purple), transparent);
    border-radius: 2px;
    animation: wave-shift 4s linear infinite;
    background-size: 200% 100%;
  }
  @keyframes wave-shift {
    0% { background-position: 0% 0; }
    100% { background-position: 200% 0; }
  }

  /* ── GLITCH TAG ── */
  .glitch-tag {
    display: inline-block;
    color: var(--red);
    font-size: 0.7rem;
    animation: micro-glitch 6s infinite;
  }
  @keyframes micro-glitch {
    0%,95%,100% { transform: none; }
    96% { transform: translateX(-1px); color: var(--cyan); }
    97% { transform: translateX(2px); color: var(--red); }
    98% { transform: none; }
  }

  /* ── PULSING ONLINE DOT ── */
  .online-indicator {
    display: inline-flex;
    align-items: center;
    gap: 0.4rem;
    font-size: 0.7rem;
    color: var(--green);
  }
  .pulse-dot {
    width: 7px;
    height: 7px;
    border-radius: 50%;
    background: var(--green);
    box-shadow: 0 0 0 0 rgba(57,211,83,0.4);
    animation: pulse-ring 2s infinite;
  }
  @keyframes pulse-ring {
    0% { box-shadow: 0 0 0 0 rgba(57,211,83,0.4); }
    70% { box-shadow: 0 0 0 6px rgba(57,211,83,0); }
    100% { box-shadow: 0 0 0 0 rgba(57,211,83,0); }
  }

  /* Responsive */
  @media (max-width: 600px) {
    .stats-grid { grid-template-columns: repeat(2, 1fr); }
    .ascii-art { font-size: 0.28rem; }
  }
</style>
</head>
<body>
<div class="container">

  <!-- TERMINAL WINDOW -->
  <div class="terminal-bar">
    <div class="dot dot-r"></div>
    <div class="dot dot-y"></div>
    <div class="dot dot-g"></div>
    <span class="term-title">~/samuel/README.md — bash</span>
    <span class="online-indicator">
      <span class="pulse-dot"></span>
      online
    </span>
  </div>

  <div class="ascii-hero">
    <pre class="ascii-art">
███████╗ █████╗ ███╗   ███╗██╗   ██╗███████╗██╗     
██╔════╝██╔══██╗████╗ ████║██║   ██║██╔════╝██║     
███████╗███████║██╔████╔██║██║   ██║█████╗  ██║     
╚════██║██╔══██║██║╚██╔╝██║██║   ██║██╔══╝  ██║     
███████║██║  ██║██║ ╚═╝ ██║╚██████╔╝███████╗███████╗
╚══════╝╚═╝  ╚═╝╚═╝     ╚═╝ ╚═════╝ ╚══════╝╚══════╝
    </pre>
    <div class="typing-badge">
      <span id="typing-text"></span><span class="cursor"></span>
    </div>
  </div>

  <!-- INTRO -->
  <div class="section">
    <div class="card">
      <div class="card-header">
        <span class="icon">▸</span>
        <span class="filename">about.ts</span>
        <span class="badge">18 y/o dev</span>
      </div>
      <div class="card-body">
        <div style="font-size:0.8rem; line-height:2;">
          <span class="comment">// Hey! 👋 I'm Samuel — caffeine-driven dev from the DR</span><br>
          <span class="keyword">const</span> <span class="variable">samuel</span> <span style="color:var(--text)">= {</span><br>
          &nbsp;&nbsp;<span class="string">"description"</span><span style="color:var(--text)">:</span> <span class="string">"I mass consume coffee and mass produce code ☕"</span><span style="color:var(--text)">,</span><br>
          &nbsp;&nbsp;<span class="string">"mission"</span><span style="color:var(--text)">:</span> <span class="string">"Build my own OS — because 3am algorithm grinding hits different 🏆"</span><span style="color:var(--text)">,</span><br>
          &nbsp;&nbsp;<span class="string">"current_activity"</span><span style="color:var(--text)">:</span> <span class="string">"tweaking Arch + Hyprland for the 47th time"</span><span style="color:var(--text)">,</span><br>
          &nbsp;&nbsp;<span class="string">"fact"</span><span style="color:var(--text)">:</span> <span class="string">"i use arch btw"</span> <span class="comment">// I will never stop saying this</span><br>
          <span style="color:var(--text)">}</span>
        </div>
      </div>
    </div>
  </div>

  <!-- SKILLS -->
  <div class="section">
    <div class="card">
      <div class="card-header">
        <span class="icon">▸</span>
        <span class="filename">tech-stack.json</span>
        <span class="badge">weapons of choice</span>
      </div>
      <div class="skills-section">
        <div class="skills-category">
          <div class="skills-label">languages</div>
          <div class="pills">
            <span class="pill"><span class="dot2"></span>TypeScript</span>
            <span class="pill"><span class="dot2"></span>JavaScript</span>
            <span class="pill"><span class="dot2"></span>C#</span>
            <span class="pill"><span class="dot2"></span>C++</span>
            <span class="pill"><span class="dot2"></span>Python</span>
          </div>
        </div>
        <div class="skills-category">
          <div class="skills-label">backend</div>
          <div class="pills">
            <span class="pill"><span class="dot2"></span>Node.js</span>
            <span class="pill"><span class="dot2"></span>Express</span>
            <span class="pill"><span class="dot2"></span>NestJS</span>
            <span class="pill"><span class="dot2"></span>.NET</span>
          </div>
        </div>
        <div class="skills-category">
          <div class="skills-label">frontend</div>
          <div class="pills">
            <span class="pill"><span class="dot2"></span>React</span>
            <span class="pill"><span class="dot2"></span>Next.js</span>
            <span class="pill"><span class="dot2"></span>Tailwind</span>
            <span class="pill"><span class="dot2"></span>HTML/CSS</span>
          </div>
        </div>
        <div class="skills-category">
          <div class="skills-label">devops & databases</div>
          <div class="pills">
            <span class="pill"><span class="dot2"></span>Linux</span>
            <span class="pill"><span class="dot2"></span>Docker</span>
            <span class="pill"><span class="dot2"></span>PostgreSQL</span>
            <span class="pill"><span class="dot2"></span>MySQL</span>
            <span class="pill"><span class="dot2"></span>MongoDB</span>
            <span class="pill"><span class="dot2"></span>Redis</span>
          </div>
        </div>
        <div class="skills-category" style="margin-bottom:0">
          <div class="skills-label">can't live without</div>
          <div class="pills">
            <span class="pill"><span class="dot2"></span>Git</span>
            <span class="pill"><span class="dot2"></span>Neovim</span>
            <span class="pill"><span class="dot2"></span>Arch</span>
            <span class="pill"><span class="dot2"></span>VSCode</span>
          </div>
        </div>
      </div>
    </div>
  </div>

  <!-- CODE SNIPPET -->
  <div class="section">
    <div class="card">
      <div class="card-header">
        <span class="icon">▸</span>
        <span class="filename">vibe.js</span>
        <span class="glitch-tag">▲ [LIVE]</span>
      </div>
      <div class="card-body">
        <div class="code-block">
          <div class="line"><span class="line-num">1</span><span class="keyword">const</span> <span class="variable">samuel</span> <span style="color:var(--text)">=</span> {</div>
          <div class="line"><span class="line-num">2</span>&nbsp;&nbsp;<span class="variable">mass_using</span><span style="color:var(--text)">:</span> [<span class="string">"TypeScript"</span>, <span class="string">"React"</span>, <span class="string">"Node.js"</span>, <span class="string">"C++"</span>, <span class="string">"C"</span>],</div>
          <div class="line"><span class="line-num">3</span>&nbsp;&nbsp;<span class="variable">mass_learning</span><span style="color:var(--text)">:</span> [<span class="string">"Algorithms"</span>, <span class="string">"System Design"</span>],</div>
          <div class="line"><span class="line-num">4</span>&nbsp;&nbsp;<span class="variable">mass_avoiding</span><span style="color:var(--text)">:</span> [<span class="string">"Sleep"</span>, <span class="string">"Going outside"</span>],</div>
          <div class="line"><span class="line-num">5</span></div>
          <div class="line"><span class="line-num">6</span>&nbsp;&nbsp;<span class="variable">setup</span><span style="color:var(--text)">:</span> {</div>
          <div class="line"><span class="line-num">7</span>&nbsp;&nbsp;&nbsp;&nbsp;<span class="variable">os</span><span style="color:var(--text)">:</span> <span class="string">"Arch btw"</span>,</div>
          <div class="line"><span class="line-num">8</span>&nbsp;&nbsp;&nbsp;&nbsp;<span class="variable">wm</span><span style="color:var(--text)">:</span> <span class="string">"Hyprland"</span>,</div>
          <div class="line"><span class="line-num">9</span>&nbsp;&nbsp;&nbsp;&nbsp;<span class="variable">editor</span><span style="color:var(--text)">:</span> <span class="string">"Neovim (I use it to feel superior)"</span>,</div>
          <div class="line"><span class="line-num">10</span>&nbsp;&nbsp;&nbsp;&nbsp;<span class="variable">theme</span><span style="color:var(--text)">:</span> <span class="string">"Dark everything, always"</span></div>
          <div class="line"><span class="line-num">11</span>&nbsp;&nbsp;},</div>
          <div class="line"><span class="line-num">12</span></div>
          <div class="line"><span class="line-num">13</span>&nbsp;&nbsp;<span class="variable">goal_2026</span><span style="color:var(--text)">:</span> <span class="string">"Making my own Operating System xd"</span>,</div>
          <div class="line"><span class="line-num">14</span>&nbsp;&nbsp;<span class="variable">coffee_today</span><span style="color:var(--text)">:</span> <span class="number">Infinity</span></div>
          <div class="line"><span class="line-num">15</span>};</div>
        </div>
      </div>
    </div>
  </div>

  <!-- LANG USAGE -->
  <div class="section">
    <div class="card">
      <div class="card-header">
        <span class="icon">▸</span>
        <span class="filename">language-usage.log</span>
        <span class="badge">2025 commits</span>
      </div>
      <div class="activity">
        <div class="activity-row">
          <span class="activity-lang">TypeScript</span>
          <div class="activity-bar-wrap">
            <div class="activity-bar" style="width:72%; animation-delay:0.1s;"></div>
          </div>
          <span class="activity-pct">72%</span>
        </div>
        <div class="activity-row">
          <span class="activity-lang">C++</span>
          <div class="activity-bar-wrap">
            <div class="activity-bar" style="width:55%; animation-delay:0.2s; background: linear-gradient(90deg, #0369a1, #38bdf8);"></div>
          </div>
          <span class="activity-pct">55%</span>
        </div>
        <div class="activity-row">
          <span class="activity-lang">C#</span>
          <div class="activity-bar-wrap">
            <div class="activity-bar" style="width:40%; animation-delay:0.3s; background: linear-gradient(90deg, #065f46, #34d399);"></div>
          </div>
          <span class="activity-pct">40%</span>
        </div>
        <div class="activity-row">
          <span class="activity-lang">Python</span>
          <div class="activity-bar-wrap">
            <div class="activity-bar" style="width:25%; animation-delay:0.4s; background: linear-gradient(90deg, #92400e, #f59e0b);"></div>
          </div>
          <span class="activity-pct">25%</span>
        </div>
        <div class="activity-row">
          <span class="activity-lang">Other</span>
          <div class="activity-bar-wrap">
            <div class="activity-bar" style="width:15%; animation-delay:0.5s; background: linear-gradient(90deg, #581c87, #c084fc);"></div>
          </div>
          <span class="activity-pct">15%</span>
        </div>
      </div>
    </div>
  </div>

  <!-- WHAT I'M UP TO -->
  <div class="section">
    <div class="card">
      <div class="card-header">
        <span class="icon">▸</span>
        <span class="filename">current-tasks.md</span>
        <span class="badge">status: grinding</span>
      </div>
      <div class="up-to-list">
        <div class="up-to-item">
          <div class="up-to-icon">🌐</div>
          <div class="up-to-content">
            <div class="title">Building web apps</div>
            <div class="desc">Full-stack stuff — from pretty UIs to APIs that don't crash (most of the time)</div>
          </div>
        </div>
        <div class="up-to-item">
          <div class="up-to-icon">🧩</div>
          <div class="up-to-content">
            <div class="title">Competitive programming</div>
            <div class="desc">Grinding Codeforces and mass solving problems at 3am</div>
          </div>
        </div>
        <div class="up-to-item">
          <div class="up-to-icon">🎨</div>
          <div class="up-to-content">
            <div class="title">Ricing my setup</div>
            <div class="desc">Arch + Hyprland tweaks #47 — obviously more important than actual work</div>
          </div>
        </div>
        <div class="up-to-item">
          <div class="up-to-icon">🏆</div>
          <div class="up-to-content">
            <div class="title">Goal 2026: Create an OS</div>
            <div class="desc">Because apparently I enjoy suffering at 3am. This is fine. 🔥</div>
          </div>
        </div>
      </div>
    </div>
  </div>

  <!-- CONTACT -->
  <div class="section">
    <div class="card">
      <div class="card-header">
        <span class="icon">▸</span>
        <span class="filename">contact.sh</span>
      </div>
      <div class="contact-section">
        <p style="font-size:0.8rem; color:var(--muted); margin-bottom:1rem;">
          <span class="comment">$ ./reach_out.sh --email --no-spam</span>
        </p>
        <a href="mailto:xamuelacostasiri@gmail.com" class="contact-btn">
          <span>✉</span> xamuelacostasiri@gmail.com
        </a>
        <p class="contact-tagline">Mass shipping code. Mass breaking prod. Mass fixing bugs at 3am.</p>
      </div>
    </div>
  </div>

  <div class="footer-wave"></div>

</div>

<script>
  // Typing effect
  const phrases = [
    "Web Developer",
    "Competitive Programmer",
    "i use arch btw",
    "OS builder (soon™)",
    "3am bug fixer",
  ];
  let phraseIdx = 0, charIdx = 0, deleting = false;
  const el = document.getElementById('typing-text');

  function type() {
    const current = phrases[phraseIdx];
    if (!deleting) {
      el.textContent = current.slice(0, ++charIdx);
      if (charIdx === current.length) {
        deleting = true;
        setTimeout(type, 1800);
        return;
      }
    } else {
      el.textContent = current.slice(0, --charIdx);
      if (charIdx === 0) {
        deleting = false;
        phraseIdx = (phraseIdx + 1) % phrases.length;
      }
    }
    setTimeout(type, deleting ? 50 : 85);
  }
  type();

  // Animate bars on scroll
  const bars = document.querySelectorAll('.activity-bar');
  const observer = new IntersectionObserver((entries) => {
    entries.forEach(e => {
      if (e.isIntersecting) {
        e.target.style.animationPlayState = 'running';
      }
    });
  }, { threshold: 0.3 });
  bars.forEach(b => {
    b.style.animationPlayState = 'paused';
    observer.observe(b);
  });
</script>
</body>
</html>
