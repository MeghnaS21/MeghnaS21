<!DOCTYPE html>
<html lang="en">
<head>
<meta charset="UTF-8"/>
<meta name="viewport" content="width=device-width, initial-scale=1.0"/>
<title>Meghna Srivastava — DevOps Engineer</title>
<link href="https://fonts.googleapis.com/css2?family=JetBrains+Mono:wght@300;400;600;700&family=Syne:wght@400;600;800&display=swap" rel="stylesheet"/>
<style>
  :root {
    --bg: #050a0e;
    --surface: #0d1117;
    --card: #0f1923;
    --border: #1e3a5f;
    --accent: #00d4ff;
    --accent2: #7c3aed;
    --accent3: #10b981;
    --text: #e2e8f0;
    --muted: #64748b;
    --glow: 0 0 20px rgba(0,212,255,0.3);
  }

  * { margin: 0; padding: 0; box-sizing: border-box; }

  body {
    background: var(--bg);
    color: var(--text);
    font-family: 'JetBrains Mono', monospace;
    overflow-x: hidden;
    cursor: none;
  }

  /* Custom cursor */
  .cursor {
    width: 12px; height: 12px;
    background: var(--accent);
    border-radius: 50%;
    position: fixed;
    pointer-events: none;
    z-index: 9999;
    transition: transform 0.1s;
    box-shadow: 0 0 10px var(--accent), 0 0 30px var(--accent);
  }
  .cursor-ring {
    width: 36px; height: 36px;
    border: 1px solid rgba(0,212,255,0.4);
    border-radius: 50%;
    position: fixed;
    pointer-events: none;
    z-index: 9998;
    transition: all 0.15s ease;
  }

  /* Animated background grid */
  .bg-grid {
    position: fixed;
    inset: 0;
    background-image:
      linear-gradient(rgba(0,212,255,0.03) 1px, transparent 1px),
      linear-gradient(90deg, rgba(0,212,255,0.03) 1px, transparent 1px);
    background-size: 50px 50px;
    animation: gridMove 20s linear infinite;
    z-index: 0;
  }
  @keyframes gridMove {
    0% { transform: translateY(0); }
    100% { transform: translateY(50px); }
  }

  /* Floating particles */
  .particles { position: fixed; inset: 0; z-index: 0; overflow: hidden; }
  .particle {
    position: absolute;
    width: 2px; height: 2px;
    background: var(--accent);
    border-radius: 50%;
    animation: float linear infinite;
    opacity: 0;
  }
  @keyframes float {
    0% { transform: translateY(100vh) translateX(0); opacity: 0; }
    10% { opacity: 1; }
    90% { opacity: 1; }
    100% { transform: translateY(-10vh) translateX(100px); opacity: 0; }
  }

  /* Main layout */
  .container {
    position: relative;
    z-index: 1;
    max-width: 900px;
    margin: 0 auto;
    padding: 40px 24px;
  }

  /* Hero section */
  .hero {
    text-align: center;
    padding: 60px 0 40px;
    position: relative;
  }

  .hero-tag {
    display: inline-block;
    font-size: 11px;
    letter-spacing: 4px;
    color: var(--accent);
    border: 1px solid rgba(0,212,255,0.3);
    padding: 6px 16px;
    border-radius: 2px;
    margin-bottom: 24px;
    animation: fadeSlideDown 0.8s ease forwards;
    opacity: 0;
    text-transform: uppercase;
  }

  .hero-name {
    font-family: 'Syne', sans-serif;
    font-size: clamp(42px, 8vw, 80px);
    font-weight: 800;
    line-height: 1;
    margin-bottom: 12px;
    animation: fadeSlideDown 0.8s 0.2s ease forwards;
    opacity: 0;
    background: linear-gradient(135deg, #ffffff 0%, var(--accent) 50%, var(--accent2) 100%);
    -webkit-background-clip: text;
    -webkit-text-fill-color: transparent;
    background-clip: text;
  }

  .hero-role {
    font-size: 14px;
    color: var(--muted);
    letter-spacing: 2px;
    margin-bottom: 32px;
    animation: fadeSlideDown 0.8s 0.4s ease forwards;
    opacity: 0;
  }

  .hero-role span { color: var(--accent3); }

  /* Terminal window */
  .terminal {
    background: #0a0e13;
    border: 1px solid var(--border);
    border-radius: 10px;
    overflow: hidden;
    margin: 40px 0;
    animation: fadeSlideUp 0.8s 0.6s ease forwards;
    opacity: 0;
    box-shadow: 0 0 40px rgba(0,212,255,0.08), 0 20px 60px rgba(0,0,0,0.5);
  }

  .terminal-bar {
    background: #111827;
    padding: 12px 16px;
    display: flex;
    align-items: center;
    gap: 8px;
    border-bottom: 1px solid var(--border);
  }

  .dot { width: 12px; height: 12px; border-radius: 50%; }
  .dot-red { background: #ff5f57; }
  .dot-yellow { background: #ffbd2e; }
  .dot-green { background: #28c941; }

  .terminal-title {
    flex: 1;
    text-align: center;
    font-size: 11px;
    color: var(--muted);
    letter-spacing: 1px;
  }

  .terminal-body {
    padding: 24px;
    font-size: 13px;
    line-height: 2;
  }

  .prompt { color: var(--accent3); }
  .cmd { color: var(--accent); }
  .key { color: #f472b6; }
  .val { color: #fbbf24; }
  .comment { color: #4b5563; }
  .string { color: var(--accent3); }

  .typing-line {
    overflow: hidden;
    white-space: nowrap;
    animation: typing 0.5s steps(40) forwards;
    opacity: 0;
  }
  .typing-line:nth-child(1) { animation-delay: 1.2s; }
  .typing-line:nth-child(2) { animation-delay: 1.5s; }
  .typing-line:nth-child(3) { animation-delay: 1.7s; }
  .typing-line:nth-child(4) { animation-delay: 1.9s; }
  .typing-line:nth-child(5) { animation-delay: 2.1s; }
  .typing-line:nth-child(6) { animation-delay: 2.3s; }
  .typing-line:nth-child(7) { animation-delay: 2.5s; }
  .typing-line:nth-child(8) { animation-delay: 2.7s; }
  .typing-line:nth-child(9) { animation-delay: 2.9s; }
  .typing-line:nth-child(10) { animation-delay: 3.1s; }
  .typing-line:nth-child(11) { animation-delay: 3.3s; }
  .typing-line:nth-child(12) { animation-delay: 3.5s; }
  .typing-line:nth-child(13) { animation-delay: 3.7s; }

  @keyframes typing {
    from { opacity: 0; max-width: 0; }
    to { opacity: 1; max-width: 100%; }
  }

  .cursor-blink {
    display: inline-block;
    width: 8px; height: 14px;
    background: var(--accent);
    animation: blink 1s step-end infinite;
    vertical-align: middle;
    margin-left: 2px;
  }
  @keyframes blink { 50% { opacity: 0; } }

  /* Social links */
  .socials {
    display: flex;
    flex-wrap: wrap;
    gap: 12px;
    justify-content: center;
    margin: 32px 0;
    animation: fadeSlideUp 0.8s 0.8s ease forwards;
    opacity: 0;
  }

  .social-btn {
    display: flex;
    align-items: center;
    gap: 8px;
    padding: 10px 20px;
    border: 1px solid var(--border);
    border-radius: 4px;
    text-decoration: none;
    color: var(--text);
    font-size: 12px;
    letter-spacing: 1px;
    transition: all 0.3s ease;
    background: rgba(255,255,255,0.02);
    position: relative;
    overflow: hidden;
  }

  .social-btn::before {
    content: '';
    position: absolute;
    inset: 0;
    background: linear-gradient(90deg, transparent, rgba(0,212,255,0.08), transparent);
    transform: translateX(-100%);
    transition: transform 0.5s ease;
  }

  .social-btn:hover::before { transform: translateX(100%); }
  .social-btn:hover {
    border-color: var(--accent);
    color: var(--accent);
    box-shadow: var(--glow);
    transform: translateY(-2px);
  }

  .social-icon { font-size: 16px; }

  /* Section styles */
  .section {
    margin: 48px 0;
    animation: fadeSlideUp 0.8s ease forwards;
    opacity: 0;
  }
  .section:nth-child(1) { animation-delay: 0.9s; }
  .section:nth-child(2) { animation-delay: 1.1s; }
  .section:nth-child(3) { animation-delay: 1.3s; }
  .section:nth-child(4) { animation-delay: 1.5s; }

  .section-label {
    display: flex;
    align-items: center;
    gap: 12px;
    margin-bottom: 20px;
    font-size: 11px;
    letter-spacing: 3px;
    text-transform: uppercase;
    color: var(--accent);
  }
  .section-label::after {
    content: '';
    flex: 1;
    height: 1px;
    background: linear-gradient(90deg, var(--border), transparent);
  }

  /* Tech badges grid */
  .tech-grid {
    display: flex;
    flex-wrap: wrap;
    gap: 10px;
  }

  .tech-badge {
    display: flex;
    align-items: center;
    gap: 8px;
    padding: 8px 16px;
    border: 1px solid var(--border);
    border-radius: 4px;
    font-size: 12px;
    color: var(--muted);
    background: rgba(255,255,255,0.02);
    transition: all 0.3s ease;
    cursor: default;
  }

  .tech-badge:hover {
    border-color: var(--accent);
    color: var(--text);
    background: rgba(0,212,255,0.05);
    transform: translateY(-3px);
    box-shadow: 0 8px 20px rgba(0,0,0,0.3), 0 0 15px rgba(0,212,255,0.1);
  }

  .badge-dot {
    width: 6px; height: 6px;
    border-radius: 50%;
    background: var(--accent3);
    animation: pulse 2s ease-in-out infinite;
  }

  @keyframes pulse {
    0%, 100% { opacity: 1; transform: scale(1); }
    50% { opacity: 0.5; transform: scale(0.8); }
  }

  /* Stats cards */
  .stats-grid {
    display: grid;
    grid-template-columns: repeat(auto-fit, minmax(200px, 1fr));
    gap: 16px;
  }

  .stat-card {
    background: var(--card);
    border: 1px solid var(--border);
    border-radius: 8px;
    padding: 24px;
    text-align: center;
    position: relative;
    overflow: hidden;
    transition: all 0.3s ease;
  }

  .stat-card::before {
    content: '';
    position: absolute;
    top: 0; left: 0; right: 0;
    height: 2px;
    background: linear-gradient(90deg, var(--accent2), var(--accent), var(--accent3));
  }

  .stat-card:hover {
    transform: translateY(-4px);
    border-color: rgba(0,212,255,0.3);
    box-shadow: 0 20px 40px rgba(0,0,0,0.4), 0 0 20px rgba(0,212,255,0.08);
  }

  .stat-number {
    font-family: 'Syne', sans-serif;
    font-size: 36px;
    font-weight: 800;
    color: var(--accent);
    display: block;
    margin-bottom: 4px;
  }

  .stat-label {
    font-size: 11px;
    letter-spacing: 2px;
    color: var(--muted);
    text-transform: uppercase;
  }

  /* Contribution bar */
  .contrib-bar {
    height: 6px;
    background: var(--surface);
    border-radius: 3px;
    overflow: hidden;
    margin: 8px 0 4px;
  }

  .contrib-fill {
    height: 100%;
    border-radius: 3px;
    animation: fillBar 1.5s ease forwards;
    width: 0;
  }

  @keyframes fillBar {
    to { width: var(--fill-pct); }
  }

  /* Quote */
  .quote-block {
    border-left: 2px solid var(--accent);
    padding: 16px 24px;
    background: rgba(0,212,255,0.03);
    border-radius: 0 8px 8px 0;
    font-style: italic;
    color: var(--muted);
    font-size: 14px;
    line-height: 1.8;
    margin: 32px 0;
  }

  .quote-block em { color: var(--accent); font-style: normal; }

  /* Footer */
  .footer {
    text-align: center;
    padding: 40px 0 20px;
    font-size: 11px;
    color: var(--muted);
    letter-spacing: 2px;
    animation: fadeSlideUp 0.8s 2s ease forwards;
    opacity: 0;
  }

  .footer-line {
    width: 60px;
    height: 1px;
    background: var(--border);
    margin: 16px auto;
  }

  /* Animations */
  @keyframes fadeSlideDown {
    from { opacity: 0; transform: translateY(-20px); }
    to { opacity: 1; transform: translateY(0); }
  }
  @keyframes fadeSlideUp {
    from { opacity: 0; transform: translateY(20px); }
    to { opacity: 1; transform: translateY(0); }
  }

  /* Scanline effect */
  .scanline {
    position: fixed;
    inset: 0;
    background: repeating-linear-gradient(
      0deg,
      transparent,
      transparent 2px,
      rgba(0,0,0,0.03) 2px,
      rgba(0,0,0,0.03) 4px
    );
    pointer-events: none;
    z-index: 999;
  }

  /* Glow orbs */
  .orb {
    position: fixed;
    border-radius: 50%;
    filter: blur(80px);
    opacity: 0.12;
    pointer-events: none;
    z-index: 0;
    animation: orbFloat 8s ease-in-out infinite;
  }
  .orb-1 { width: 400px; height: 400px; background: var(--accent2); top: -100px; right: -100px; }
  .orb-2 { width: 300px; height: 300px; background: var(--accent); bottom: 100px; left: -80px; animation-delay: -4s; }

  @keyframes orbFloat {
    0%, 100% { transform: translateY(0) scale(1); }
    50% { transform: translateY(30px) scale(1.05); }
  }

  /* Note banner */
  .note-banner {
    background: rgba(124,58,237,0.1);
    border: 1px solid rgba(124,58,237,0.3);
    border-radius: 6px;
    padding: 12px 20px;
    font-size: 11px;
    color: #a78bfa;
    letter-spacing: 1px;
    margin-bottom: 32px;
    text-align: center;
  }
</style>
</head>
<body>

<div class="cursor" id="cursor"></div>
<div class="cursor-ring" id="cursorRing"></div>
<div class="scanline"></div>
<div class="bg-grid"></div>
<div class="orb orb-1"></div>
<div class="orb orb-2"></div>

<!-- Particles -->
<div class="particles" id="particles"></div>

<div class="container">

  <!-- Note -->
  <div class="note-banner" style="opacity:0;animation:fadeSlideDown 0.6s 0.1s forwards">
    ✦ This is an animated HTML preview of the GitHub README — paste the README.md into your GitHub profile repo
  </div>

  <!-- Hero -->
  <div class="hero">
    <div class="hero-tag">Software · DevOps Engineer · 3 yrs 8 mos</div>
    <div class="hero-name">Meghna Srivastava</div>
    <div class="hero-role">she/her &nbsp;·&nbsp; <span>automating the world, one pipeline at a time</span></div>
  </div>

  <!-- Social Buttons -->
  <div class="socials">
    <a class="social-btn" href="https://twitter.com/MeghnaS21" target="_blank">
      <span class="social-icon">🐦</span> Twitter
    </a>
    <a class="social-btn" href="https://www.linkedin.com/in/meghna-srivastava-34571b172/" target="_blank">
      <span class="social-icon">💼</span> LinkedIn
    </a>
    <a class="social-btn" href="https://github.com/MeghnaS21" target="_blank">
      <span class="social-icon">🐙</span> GitHub
    </a>
    <a class="social-btn" href="https://youtube.com/channel/UCCJX1akyAIyW0oWN26531fg" target="_blank">
      <span class="social-icon">▶️</span> YouTube
    </a>
    <a class="social-btn" href="mailto:meghnasrivastava2000@gmail.com">
      <span class="social-icon">📧</span> Email
    </a>
  </div>

  <!-- Terminal -->
  <div class="terminal">
    <div class="terminal-bar">
      <div class="dot dot-red"></div>
      <div class="dot dot-yellow"></div>
      <div class="dot dot-green"></div>
      <div class="terminal-title">meghna@devops ~ about_me.yaml</div>
    </div>
    <div class="terminal-body">
      <div class="typing-line"><span class="prompt">❯</span> <span class="cmd">cat</span> <span class="string">about_me.yaml</span></div>
      <div class="typing-line">&nbsp;</div>
      <div class="typing-line"><span class="key">name</span><span class="comment">:</span>       <span class="val">"Meghna Srivastava"</span></div>
      <div class="typing-line"><span class="key">role</span><span class="comment">:</span>       <span class="val">"DevOps Engineer 🛠️"</span></div>
      <div class="typing-line"><span class="key">experience</span><span class="comment">:</span> <span class="val">"3 years, 8 months"</span></div>
      <div class="typing-line"><span class="key">pronouns</span><span class="comment">:</span>  <span class="val">"she / her"</span></div>
      <div class="typing-line">&nbsp;</div>
      <div class="typing-line"><span class="key">focus</span><span class="comment">:</span></div>
      <div class="typing-line">&nbsp; <span class="comment">-</span> <span class="string">CI/CD Pipelines &amp; Infrastructure Automation</span></div>
      <div class="typing-line">&nbsp; <span class="comment">-</span> <span class="string">Competitive Problem Solving</span></div>
      <div class="typing-line">&nbsp; <span class="comment">-</span> <span class="string">YouTube Collaborations</span></div>
      <div class="typing-line">&nbsp;</div>
      <div class="typing-line"><span class="key">fun_fact</span><span class="comment">:</span> <span class="val">"Traded binge-watching for terminal sessions. No regrets. 😄"</span></div>
      <div class="typing-line"><span class="prompt">❯</span> <span class="cursor-blink"></span></div>
    </div>
  </div>

  <!-- Tech Stack -->
  <div class="section">
    <div class="section-label">⚙️ &nbsp;Tech Stack</div>
    <div class="tech-grid">
      <div class="tech-badge"><div class="badge-dot" style="background:#FCC624"></div>Linux</div>
      <div class="tech-badge"><div class="badge-dot" style="background:#2496ED"></div>Docker</div>
      <div class="tech-badge"><div class="badge-dot" style="background:#326CE5"></div>Kubernetes</div>
      <div class="tech-badge"><div class="badge-dot" style="background:#D24939"></div>Jenkins</div>
      <div class="tech-badge"><div class="badge-dot" style="background:#2088FF"></div>GitHub Actions</div>
      <div class="tech-badge"><div class="badge-dot" style="background:#7B42BC"></div>Terraform</div>
      <div class="tech-badge"><div class="badge-dot" style="background:#EE0000"></div>Ansible</div>
      <div class="tech-badge"><div class="badge-dot" style="background:#FF9900"></div>AWS</div>
      <div class="tech-badge"><div class="badge-dot" style="background:#00599C"></div>C++</div>
      <div class="tech-badge"><div class="badge-dot" style="background:#3776AB"></div>Python</div>
      <div class="tech-badge"><div class="badge-dot" style="background:#4EAA25"></div>Bash</div>
      <div class="tech-badge"><div class="badge-dot" style="background:#F05032"></div>Git</div>
      <div class="tech-badge"><div class="badge-dot" style="background:#007ACC"></div>VS Code</div>
    </div>
  </div>

  <!-- Stats -->
  <div class="section">
    <div class="section-label">📊 &nbsp;At A Glance</div>
    <div class="stats-grid">
      <div class="stat-card">
        <span class="stat-number">3.8</span>
        <span class="stat-label">Years Experience</span>
      </div>
      <div class="stat-card">
        <span class="stat-number" style="color:var(--accent3)">∞</span>
        <span class="stat-label">Pipelines Shipped</span>
      </div>
      <div class="stat-card">
        <span class="stat-number" style="color:#f472b6">24/7</span>
        <span class="stat-label">Systems Uptime Goal</span>
      </div>
    </div>
  </div>

  <!-- Skills proficiency -->
  <div class="section">
    <div class="section-label">📈 &nbsp;Proficiency</div>
    <div style="display:flex;flex-direction:column;gap:16px">
      <div>
        <div style="display:flex;justify-content:space-between;font-size:12px;margin-bottom:4px">
          <span>DevOps & CI/CD</span><span style="color:var(--accent)">92%</span>
        </div>
        <div class="contrib-bar"><div class="contrib-fill" style="background:linear-gradient(90deg,var(--accent2),var(--accent));--fill-pct:92%"></div></div>
      </div>
      <div>
        <div style="display:flex;justify-content:space-between;font-size:12px;margin-bottom:4px">
          <span>Cloud & Infrastructure</span><span style="color:var(--accent)">85%</span>
        </div>
        <div class="contrib-bar"><div class="contrib-fill" style="background:linear-gradient(90deg,var(--accent2),var(--accent));--fill-pct:85%"></div></div>
      </div>
      <div>
        <div style="display:flex;justify-content:space-between;font-size:12px;margin-bottom:4px">
          <span>C++ / Problem Solving</span><span style="color:var(--accent3)">80%</span>
        </div>
        <div class="contrib-bar"><div class="contrib-fill" style="background:linear-gradient(90deg,var(--accent3),#34d399);--fill-pct:80%"></div></div>
      </div>
      <div>
        <div style="display:flex;justify-content:space-between;font-size:12px;margin-bottom:4px">
          <span>Scripting (Bash/Python)</span><span style="color:#f472b6">78%</span>
        </div>
        <div class="contrib-bar"><div class="contrib-fill" style="background:linear-gradient(90deg,#7c3aed,#f472b6);--fill-pct:78%"></div></div>
      </div>
    </div>
  </div>

  <!-- Quote -->
  <div class="quote-block" style="opacity:0;animation:fadeSlideUp 0.8s 1.8s forwards">
    <em>"In a world full of GUIs, be a CLI."</em><br/>
    Always learning · Always shipping · Always automating.
  </div>

  <!-- Footer -->
  <div class="footer">
    <div class="footer-line"></div>
    MEGHNA SRIVASTAVA &nbsp;·&nbsp; DEVOPS ENGINEER &nbsp;·&nbsp; meghnasrivastava2000@gmail.com
    <div class="footer-line"></div>
  </div>

</div>

<script>
  // Custom cursor
  const cursor = document.getElementById('cursor');
  const ring = document.getElementById('cursorRing');
  let mx = 0, my = 0, rx = 0, ry = 0;

  document.addEventListener('mousemove', e => {
    mx = e.clientX; my = e.clientY;
    cursor.style.left = (mx - 6) + 'px';
    cursor.style.top = (my - 6) + 'px';
  });

  function animRing() {
    rx += (mx - rx - 18) * 0.12;
    ry += (my - ry - 18) * 0.12;
    ring.style.left = rx + 'px';
    ring.style.top = ry + 'px';
    requestAnimationFrame(animRing);
  }
  animRing();

  document.querySelectorAll('a, .tech-badge, .stat-card').forEach(el => {
    el.addEventListener('mouseenter', () => {
      cursor.style.transform = 'scale(2)';
      ring.style.transform = 'scale(1.5)';
      ring.style.borderColor = 'rgba(0,212,255,0.8)';
    });
    el.addEventListener('mouseleave', () => {
      cursor.style.transform = 'scale(1)';
      ring.style.transform = 'scale(1)';
      ring.style.borderColor = 'rgba(0,212,255,0.4)';
    });
  });

  // Particles
  const container = document.getElementById('particles');
  for (let i = 0; i < 30; i++) {
    const p = document.createElement('div');
    p.className = 'particle';
    p.style.left = Math.random() * 100 + 'vw';
    p.style.animationDuration = (8 + Math.random() * 12) + 's';
    p.style.animationDelay = (-Math.random() * 20) + 's';
    p.style.width = p.style.height = (Math.random() > 0.7 ? 3 : 2) + 'px';
    if (Math.random() > 0.7) p.style.background = '#7c3aed';
    container.appendChild(p);
  }
</script>

</body>
</html>
