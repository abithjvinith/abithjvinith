<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0, user-scalable=no">
  <title>Abith | Full Stack Hacker | Dev Portfolio</title>
  <!-- Google Fonts + Font Awesome -->
  <link href="https://fonts.googleapis.com/css2?family=Space+Grotesk:wght@300;400;500;600;700&family=Space+Mono:wght@400;700&display=swap" rel="stylesheet">
  <link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/6.0.0-beta3/css/all.min.css">
  <!-- Animate.css for smooth entrance -->
  <link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/animate.css/4.1.1/animate.min.css">
  <style>
    * {
      margin: 0;
      padding: 0;
      box-sizing: border-box;
    }

    body {
      background: radial-gradient(circle at 20% 30%, #0a0f1f, #03060c);
      font-family: 'Space Grotesk', 'Space Mono', monospace;
      display: flex;
      justify-content: center;
      align-items: center;
      min-height: 100vh;
      padding: 2rem;
      position: relative;
      overflow-x: hidden;
    }

    /* animated matrix rain effect (background vibe) */
    .matrix-bg {
      position: fixed;
      top: 0;
      left: 0;
      width: 100%;
      height: 100%;
      z-index: 0;
      pointer-events: none;
      opacity: 0.2;
      font-family: 'Space Mono', monospace;
      font-size: 14px;
      color: #0f0;
    }

    /* main hacker-card */
    .hacker-card {
      position: relative;
      z-index: 10;
      max-width: 1300px;
      width: 100%;
      background: rgba(5, 10, 20, 0.65);
      backdrop-filter: blur(12px);
      border-radius: 2rem;
      border: 1px solid rgba(0, 255, 255, 0.3);
      box-shadow: 0 25px 45px rgba(0, 0, 0, 0.5), 0 0 20px rgba(0, 255, 255, 0.2);
      overflow: hidden;
      transition: all 0.3s ease;
      animation: glitch-border 4s infinite;
    }

    @keyframes glitch-border {
      0%, 100% { border-color: rgba(0, 255, 255, 0.3); box-shadow: 0 0 15px rgba(0, 255, 255, 0.2);}
      50% { border-color: rgba(0, 255, 100, 0.8); box-shadow: 0 0 25px rgba(0, 255, 150, 0.5);}
    }

    .card-inner {
      padding: 2rem 2.5rem;
    }

    /* glitch line animation */
    .scan-line {
      position: absolute;
      top: 0;
      left: 0;
      width: 100%;
      height: 4px;
      background: linear-gradient(90deg, transparent, #0ff, #0f0, #0ff, transparent);
      animation: scanMove 3s linear infinite;
      opacity: 0.6;
      z-index: 20;
    }

    @keyframes scanMove {
      0% { transform: translateX(-100%); }
      100% { transform: translateX(100%); }
    }

    /* header section */
    .header-glitch {
      display: flex;
      flex-wrap: wrap;
      justify-content: space-between;
      align-items: center;
      margin-bottom: 2rem;
      border-bottom: 1px dashed #0ff;
      padding-bottom: 1rem;
    }

    .title-glow h1 {
      font-size: 3rem;
      font-weight: 700;
      background: linear-gradient(135deg, #aaffff, #2aff9e);
      -webkit-background-clip: text;
      background-clip: text;
      color: transparent;
      letter-spacing: -0.02em;
      text-shadow: 0 0 8px rgba(0,255,200,0.4);
      animation: textPulse 2s infinite alternate;
    }

    @keyframes textPulse {
      0% { text-shadow: 0 0 2px #0ff; opacity: 0.9;}
      100% { text-shadow: 0 0 12px #0ff, 0 0 6px #0f0; opacity: 1;}
    }

    .badge-container {
      display: flex;
      gap: 15px;
    }

    .badge {
      background: #0a1a1f;
      padding: 0.4rem 1rem;
      border-radius: 40px;
      font-size: 0.8rem;
      font-weight: 500;
      font-family: 'Space Mono', monospace;
      color: #0ff;
      border: 1px solid #0ff;
      backdrop-filter: blur(4px);
      transition: 0.2s;
    }

    .badge i {
      margin-right: 6px;
    }

    .badge:hover {
      transform: scale(1.05);
      background: #0ff11a20;
      box-shadow: 0 0 12px #0ff;
    }

    /* profile row */
    .profile-row {
      display: flex;
      flex-wrap: wrap;
      gap: 2rem;
      margin-bottom: 2rem;
    }

    .coding-gif {
      flex: 1;
      min-width: 280px;
      border-radius: 20px;
      overflow: hidden;
      border: 1px solid #0ff;
      box-shadow: 0 10px 25px -5px rgba(0,0,0,0.5);
      transition: transform 0.3s;
      animation: floatGlow 3s ease-in-out infinite;
    }

    @keyframes floatGlow {
      0% { transform: translateY(0px); box-shadow: 0 0 5px #0ff;}
      50% { transform: translateY(-5px); box-shadow: 0 0 20px #0ff;}
      100% { transform: translateY(0px);}
    }

    .coding-gif img {
      width: 100%;
      height: auto;
      display: block;
      filter: brightness(1.05) contrast(1.1);
    }

    .info-panel {
      flex: 1.5;
      background: rgba(0, 20, 20, 0.5);
      backdrop-filter: blur(8px);
      border-radius: 1.5rem;
      padding: 1.2rem 1.5rem;
      border: 1px solid rgba(0, 255, 200, 0.4);
    }

    .terminal-lines p {
      font-family: 'Space Mono', monospace;
      margin: 12px 0;
      font-size: 1rem;
      color: #bcffee;
      display: flex;
      align-items: center;
      gap: 12px;
      flex-wrap: wrap;
    }

    .terminal-lines i {
      width: 28px;
      color: #0fa;
      font-size: 1.2rem;
    }

    .badge-link {
      background: #0f212e;
      padding: 5px 12px;
      border-radius: 20px;
      font-size: 0.8rem;
      transition: all 0.2s;
    }
    .badge-link a {
      color: #9efff0;
      text-decoration: none;
    }
    .badge-link:hover {
      background: #0ff33;
    }

    .social-links {
      display: flex;
      gap: 20px;
      margin: 1rem 0 0.5rem;
    }

    .social-icon {
      font-size: 1.8rem;
      color: #d0f0ff;
      transition: 0.2s;
    }
    .social-icon:hover {
      color: #0ff;
      transform: translateY(-4px) scale(1.1);
      text-shadow: 0 0 10px #0ff;
    }

    /* Skills matrix */
    .skills-section {
      margin: 2rem 0;
    }

    .skills-title {
      font-size: 1.5rem;
      letter-spacing: 2px;
      border-left: 4px solid #0ff;
      padding-left: 1rem;
      margin-bottom: 1.8rem;
      color: #b5ffea;
      font-weight: 600;
    }

    .skills-grid {
      display: flex;
      flex-wrap: wrap;
      gap: 12px;
      justify-content: center;
    }

    .skill-badge {
      background: #111a22;
      border: 1px solid #2aff9e;
      border-radius: 30px;
      padding: 8px 20px;
      font-weight: 500;
      font-family: 'Space Mono', monospace;
      font-size: 0.9rem;
      color: #ccffdd;
      backdrop-filter: blur(2px);
      transition: 0.2s;
      cursor: default;
      display: inline-flex;
      align-items: center;
      gap: 8px;
    }

    .skill-badge i {
      font-size: 1.1rem;
      color: #0ff;
    }

    .skill-badge:hover {
      transform: translateY(-3px);
      background: #1f3a44;
      border-color: #0ff;
      box-shadow: 0 0 12px rgba(0,255,255,0.4);
    }

    /* Stats and promotion */
    .stats-row {
      display: flex;
      flex-wrap: wrap;
      gap: 2rem;
      margin-top: 2rem;
      background: rgba(0, 10, 15, 0.6);
      border-radius: 1.5rem;
      padding: 1.5rem;
    }

    .stats-card {
      flex: 1;
      text-align: center;
      border-right: 1px dashed #1f8a7a;
    }
    .stats-card:last-child {
      border-right: none;
    }
    .stat-number {
      font-size: 2rem;
      font-weight: 700;
      font-family: 'Space Mono', monospace;
      color: #0ff;
      letter-spacing: 2px;
    }
    .stat-label {
      font-size: 0.8rem;
      color: #9df;
      text-transform: uppercase;
    }

    .promo-marquee {
      background: #050f16;
      border-radius: 40px;
      margin-top: 1.8rem;
      padding: 0.7rem;
      border: 1px solid #0ff;
      overflow: hidden;
    }

    .marquee-text {
      display: inline-block;
      white-space: nowrap;
      animation: scrollMarquee 12s linear infinite;
      font-family: 'Space Mono', monospace;
      font-weight: bold;
      color: #abf7ff;
    }

    @keyframes scrollMarquee {
      0% { transform: translateX(100%); }
      100% { transform: translateX(-100%); }
    }

    .footer-note {
      margin-top: 2rem;
      text-align: center;
      font-size: 0.7rem;
      color: #4f9f9f;
    }

    @media (max-width: 780px) {
      .card-inner { padding: 1.2rem; }
      .title-glow h1 { font-size: 2rem; }
    }

    /* typing cursor effect */
    .cursor-blink {
      background: #0ff;
      width: 2px;
      display: inline-block;
      margin-left: 3px;
      animation: blink 1s infinite;
    }

    @keyframes blink {
      0%,100%{ opacity: 1; } 50%{ opacity: 0; }
    }
  </style>
</head>
<body>

<div class="matrix-bg" id="matrixCanvas"></div>

<div class="hacker-card animate__animated animate__fadeInUp">
  <div class="scan-line"></div>
  <div class="card-inner">
    <!-- Header with glitch effect -->
    <div class="header-glitch">
      <div class="title-glow">
        <h1>&gt; ABITH_DEV<span class="cursor-blink"></span></h1>
        <div style="font-family: 'Space Mono'; font-size: 0.9rem; color: #0fa;">{ FullStack Architect | Cyber native }</div>
      </div>
      <div class="badge-container">
        <div class="badge"><i class="fas fa-code-branch"></i> 0x3F3</div>
        <div class="badge"><i class="fas fa-shield-alt"></i> ETH-hacker</div>
        <div class="badge"><i class="fas fa-terminal"></i> root@abith:~#</div>
      </div>
    </div>

    <!-- Profile + GIF row -->
    <div class="profile-row">
      <div class="coding-gif">
        <img src="https://camo.githubusercontent.com/61491d59e71fec5c794945fed916a4a682b6c0404fc31f30b08a0d919c558404/68747470733a2f2f696d616765732e73717561726573706163652d63646e2e636f6d2f636f6e74656e742f76312f3537363966633430316236333162616231616464623261622f313534313538303631313632342d5445363451474b524a4738535741495553374e532f6b6531375a77644742546f6464493870446d34386b506f73776c7a6a53564d4d2d53784f703743563539425a772d7a505067646e346a557756634a45315a7657515578776b6d794578676c4e714770304976544a5a616d574c49327a76595748384b332d735f3479737a63703272795449304871544f6161556f68724938504936465879386339505774426c7141566c555335697a7064634958445a71445976707252715a32395077306f2f636f64696e672d667265616b2e676966" alt="hacker coding">
      </div>
      <div class="info-panel">
        <div class="terminal-lines">
          <p><i class="fas fa-map-marker-alt"></i> <span class="badge-link">📍 India / Remote</span>  <i class="fas fa-globe"></i> <span class="badge-link">UTC+5:30</span></p>
          <p><i class="fas fa-envelope"></i> <span class="badge-link">abithjvinith@gmail.com</span> <i class="fas fa-lock"></i> <span class="badge-link">PGP Available</span></p>
          <p><i class="fas fa-brain"></i> <span style="color:#aff;">"Full-stack alchemy | React • Python • Cloud Native"</span></p>
          <p><i class="fas fa-code"></i> Currently diving into <span class="badge-link">React internals & AI agents</span></p>
          <p><i class="fas fa-comment-dots"></i> Ask me about: <span class="badge-link">React, Django, Tailwind, Microservices</span></p>
        </div>
        <div class="social-links">
          <a href="https://twitter.com/abithjvinith" target="_blank" class="social-icon"><i class="fab fa-twitter"></i></a>
          <a href="https://linkedin.com/in/abithjerivinth" target="_blank" class="social-icon"><i class="fab fa-linkedin-in"></i></a>
          <a href="https://instagram.com/shifter_vr46" target="_blank" class="social-icon"><i class="fab fa-instagram"></i></a>
          <a href="#" class="social-icon"><i class="fab fa-github"></i></a>
        </div>
        <div style="margin-top: 12px;">
          <span class="badge-link"><i class="fas fa-eye"></i> Profile Views: 2.7k+ </span>
          <span class="badge-link"><i class="fab fa-twitter"></i> Follow @abithjvinith</span>
        </div>
      </div>
    </div>

    <!-- Tools & Languages - Advanced grid -->
    <div class="skills-section">
      <div class="skills-title"><i class="fas fa-microchip"></i> // TOOLKIT & TECHSTACK</div>
      <div class="skills-grid">
        <div class="skill-badge"><i class="fab fa-python"></i> Python</div>
        <div class="skill-badge"><i class="fab fa-react"></i> React.js</div>
        <div class="skill-badge"><i class="fab fa-js"></i> JavaScript/TS</div>
        <div class="skill-badge"><i class="fab fa-node-js"></i> Node.js</div>
        <div class="skill-badge"><i class="fas fa-database"></i> MongoDB</div>
        <div class="skill-badge"><i class="fas fa-database"></i> MySQL</div>
        <div class="skill-badge"><i class="fab fa-laravel"></i> Laravel</div>
        <div class="skill-badge"><i class="fab fa-php"></i> PHP</div>
        <div class="skill-badge"><i class="fab fa-bootstrap"></i> Bootstrap</div>
        <div class="skill-badge"><i class="fab fa-css3-alt"></i> Tailwind</div>
        <div class="skill-badge"><i class="fab fa-figma"></i> Figma</div>
        <div class="skill-badge"><i class="fas fa-fire"></i> Firebase</div>
        <div class="skill-badge"><i class="fab fa-android"></i> Android</div>
        <div class="skill-badge"><i class="fas fa-mobile-alt"></i> Flutter</div>
        <div class="skill-badge"><i class="fab fa-unity"></i> Unity</div>
        <div class="skill-badge"><i class="fab fa-linux"></i> Linux</div>
        <div class="skill-badge"><i class="fas fa-code-branch"></i> Git/GitHub</div>
        <div class="skill-badge"><i class="fas fa-chart-line"></i> Pandas</div>
        <div class="skill-badge"><i class="fas fa-cube"></i> Next.js</div>
        <div class="skill-badge"><i class="fas fa-leaf"></i> NestJS</div>
      </div>
    </div>

    <!-- Stats + Promotion animation -->
    <div class="stats-row">
      <div class="stats-card">
        <div class="stat-number"><i class="fas fa-code"></i> 48+</div>
        <div class="stat-label">Projects shipped</div>
      </div>
      <div class="stats-card">
        <div class="stat-number"><i class="fab fa-github-alt"></i> 1.2k+</div>
        <div class="stat-label">Commits (2024)</div>
      </div>
      <div class="stats-card">
        <div class="stat-number"><i class="fas fa-rocket"></i> 12</div>
        <div class="stat-label">Production apps</div>
      </div>
      <div class="stats-card">
        <div class="stat-number"><i class="fas fa-certificate"></i> 7</div>
        <div class="stat-label">Certifications</div>
      </div>
    </div>

    <!-- Promo marquee / Hacker announcement -->
    <div class="promo-marquee">
      <div class="marquee-text">
        ⚡ $> OPEN FOR COLLABORATIONS • REACT / FULLSTACK •  FREELANCE MODE ACTIVE •  LET'S BUILD THE FUTURE  ⚡ &nbsp;&nbsp;||&nbsp;&nbsp;  #AI #Web3 #EdgeComputing  &nbsp;&nbsp;||&nbsp;&nbsp;  abithjvinith@gmail.com — DM for opportunities
      </div>
    </div>

    <!-- Top Languages Stats (styled like original but modern) -->
    <div style="margin-top: 2rem; display: flex; flex-wrap: wrap; justify-content: space-between; align-items: center; gap: 1rem;">
      <div style="background: rgba(0,20,20,0.6); padding: 1rem; border-radius: 20px; flex:1; text-align: center;">
        <i class="fas fa-chart-simple" style="color:#0ff;"></i>
        <span style="font-family:'Space Mono'; margin-left: 8px;">TOP LANGUAGES</span>
        <div style="display: flex; justify-content: center; gap: 20px; margin-top: 12px; flex-wrap: wrap;">
          <span class="badge-link">Python 38%</span>
          <span class="badge-link">JavaScript 32%</span>
          <span class="badge-link">PHP 12%</span>
          <span class="badge-link">Dart 8%</span>
          <span class="badge-link">C++ 10%</span>
        </div>
      </div>
      <!-- visitor counter interactive style -->
      <div style="background: #010f1a; padding: 0.8rem 1.5rem; border-radius: 40px; border: 1px solid cyan;">
        <i class="fas fa-user-astronaut"></i> <span id="visitorGlitch">[ VISITOR: 0x9A3F ]</span>
      </div>
    </div>

    <div class="footer-note">
      <i class="fas fa-shield-haltered"></i>  // encrypted terminal output || root@abith:~$ 'Full Stack Hacker Mode' active
    </div>
  </div>
</div>

<script>
  // Animated Matrix background effect (simple canvas)
  const canvas = document.createElement('canvas');
  const ctx = canvas.getContext('2d');
  const matrixDiv = document.getElementById('matrixCanvas');
  matrixDiv.appendChild(canvas);
  canvas.style.width = '100%';
  canvas.style.height = '100%';
  canvas.style.position = 'fixed';
  canvas.style.top = '0';
  canvas.style.left = '0';
  canvas.style.pointerEvents = 'none';
  
  function resizeCanvas() {
    canvas.width = window.innerWidth;
    canvas.height = window.innerHeight;
  }
  window.addEventListener('resize', resizeCanvas);
  resizeCanvas();

  const chars = "アイウエオカキクケコサシスセソタチツテトナニヌネノハヒフヘホマミムメモヤユヨラリルレロワヲン0123456789ABCDEFGHIJKLMNOPQRSTUVWXYZ!@#$%^&*()_+{}:<>?";
  const columns = Math.floor(canvas.width / 20);
  let drops = [];
  for (let i = 0; i < columns; i++) {
    drops[i] = Math.floor(Math.random() * canvas.height / 20);
  }
  function drawMatrix() {
    ctx.fillStyle = "rgba(0, 3, 10, 0.05)";
    ctx.fillRect(0, 0, canvas.width, canvas.height);
    ctx.fillStyle = "#0f8";
    ctx.font = "16px 'Space Mono'";
    for (let i = 0; i < drops.length; i++) {
      const text = chars[Math.floor(Math.random() * chars.length)];
      ctx.fillText(text, i * 20, drops[i] * 20);
      if (drops[i] * 20 > canvas.height && Math.random() > 0.975) {
        drops[i] = 0;
      }
      drops[i]++;
    }
  }
  setInterval(drawMatrix, 45);
  
  // add random glitch to visitor counter
  const visitorSpan = document.getElementById('visitorGlitch');
  let glitchInterval = setInterval(() => {
    const prefixes = ["0x", "#", "$", ">"];
    const val = Math.floor(Math.random() * 9999).toString(16).toUpperCase();
    visitorSpan.innerHTML = `[ VISITOR: ${prefixes[Math.floor(Math.random()*prefixes.length)]}${val} ]`;
  }, 3500);
  
  // Stop glitch on hover to keep readability
  if(visitorSpan) {
    visitorSpan.addEventListener('mouseenter', () => clearInterval(glitchInterval));
    visitorSpan.addEventListener('mouseleave', () => {
      glitchInterval = setInterval(() => {
        const prefixes = ["0x", "#", "$", ">"];
        const val = Math.floor(Math.random() * 9999).toString(16).toUpperCase();
        visitorSpan.innerHTML = `[ VISITOR: ${prefixes[Math.floor(Math.random()*prefixes.length)]}${val} ]`;
      }, 3500);
    });
  }
  
  // simulate terminal cursor blink
  const cursor = document.querySelector('.cursor-blink');
  if(cursor) setInterval(() => {
    cursor.style.opacity = (cursor.style.opacity === '0' ? '1' : '0');
  }, 550);
  
  // dynamic badge animation: add tiny vibration on hover for hacker vibe
  const badges = document.querySelectorAll('.skill-badge, .badge');
  badges.forEach(b => {
    b.addEventListener('mouseenter', (e) => {
      e.target.style.transform = 'translateY(-3px) rotate(0.5deg)';
      setTimeout(() => { if(e.target) e.target.style.transform = ''; }, 200);
    });
  });
  
  // extra "promo" dynamic message rotation
  const marqueeDiv = document.querySelector('.marquee-text');
  const messages = [
    "⚡ $> OPEN FOR COLLABORATIONS • REACT / FULLSTACK •  FREELANCE MODE ACTIVE  ⚡",
    "🚀 >_ BUILDING NEXT-GEN WEB APPS | LET'S HACK THE CODE 🚀",
    "🐍 Python • React Native • DevOps • AI integrations — Let's innovate!",
    "💻 Currently learning: Advanced System Design & WebGPU"
  ];
  let idx = 0;
  setInterval(() => {
    if(marqueeDiv) {
      idx = (idx+1) % messages.length;
      marqueeDiv.style.animation = 'none';
      marqueeDiv.innerHTML = messages[idx] + ' &nbsp;&nbsp;||&nbsp;&nbsp;  #innovation  &nbsp;&nbsp;||&nbsp;&nbsp;  abithjvinith@gmail.com';
      setTimeout(() => { marqueeDiv.style.animation = 'scrollMarquee 12s linear infinite'; }, 10);
    }
  }, 8000);
</script>
</body>
</html>
