<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8" />
  <meta name="viewport" content="width=device-width, initial-scale=1.0"/>
  <title>Tshering Dorji | Frontend Developer</title>
  <link rel="preconnect" href="https://fonts.googleapis.com">
  <link href="https://fonts.googleapis.com/css2?family=Fira+Code:wght@400;500;600&family=Inter:wght@300;400;500;600;700&display=swap" rel="stylesheet">
  <style>
    *, *::before, *::after { box-sizing: border-box; margin: 0; padding: 0; }

    :root {
      --yellow: #F7C948;
      --yellow-dim: #c9a52c;
      --dark: #0D1117;
      --dark2: #161B22;
      --dark3: #21262D;
      --text: #E6EDF3;
      --muted: #8B949E;
      --border: #30363D;
      --radius: 12px;
    }

    html { scroll-behavior: smooth; }

    body {
      font-family: 'Inter', sans-serif;
      background: var(--dark);
      color: var(--text);
      line-height: 1.7;
    }

    /* NAV */
    nav {
      position: fixed; top: 0; left: 0; right: 0; z-index: 100;
      background: rgba(13,17,23,0.92);
      backdrop-filter: blur(12px);
      border-bottom: 1px solid var(--border);
      display: flex; align-items: center; justify-content: space-between;
      padding: 0 2rem; height: 64px;
    }
    .nav-logo { font-family: 'Fira Code', monospace; font-size: 1.1rem; color: var(--yellow); font-weight: 600; }
    .nav-links { display: flex; gap: 2rem; list-style: none; }
    .nav-links a { color: var(--muted); text-decoration: none; font-size: 0.9rem; transition: color 0.2s; }
    .nav-links a:hover { color: var(--yellow); }

    /* HERO */
    .hero {
      min-height: 100vh;
      display: flex; align-items: center; justify-content: center;
      text-align: center; padding: 6rem 2rem 4rem;
      position: relative; overflow: hidden;
    }
    .hero::before {
      content: '';
      position: absolute; inset: 0;
      background: radial-gradient(ellipse 60% 50% at 50% 30%, rgba(247,201,72,0.07) 0%, transparent 70%);
      pointer-events: none;
    }
    .hero-tag {
      display: inline-block;
      font-family: 'Fira Code', monospace;
      font-size: 0.85rem; color: var(--yellow);
      border: 1px solid rgba(247,201,72,0.3);
      padding: 0.35rem 1rem; border-radius: 100px;
      margin-bottom: 1.5rem;
    }
    .hero h1 {
      font-size: clamp(2.4rem, 6vw, 4rem);
      font-weight: 700; line-height: 1.15;
      margin-bottom: 1rem;
    }
    .hero h1 span { color: var(--yellow); }
    .hero p {
      max-width: 560px; margin: 0 auto 2.5rem;
      color: var(--muted); font-size: 1.05rem;
    }
    .hero-btns { display: flex; gap: 1rem; justify-content: center; flex-wrap: wrap; }
    .btn-primary {
      background: var(--yellow); color: var(--dark);
      padding: 0.75rem 1.75rem; border-radius: var(--radius);
      font-weight: 600; font-size: 0.95rem; text-decoration: none;
      transition: transform 0.15s, box-shadow 0.15s;
    }
    .btn-primary:hover { transform: translateY(-2px); box-shadow: 0 8px 24px rgba(247,201,72,0.3); }
    .btn-ghost {
      border: 1px solid var(--border); color: var(--text);
      padding: 0.75rem 1.75rem; border-radius: var(--radius);
      font-size: 0.95rem; text-decoration: none;
      transition: border-color 0.2s, color 0.2s;
    }
    .btn-ghost:hover { border-color: var(--yellow); color: var(--yellow); }

    /* SECTIONS */
    section { padding: 5rem 2rem; max-width: 1000px; margin: 0 auto; }
    .section-label {
      font-family: 'Fira Code', monospace;
      font-size: 0.8rem; color: var(--yellow);
      letter-spacing: 0.12em; text-transform: uppercase;
      margin-bottom: 0.5rem;
    }
    .section-title {
      font-size: clamp(1.6rem, 4vw, 2.2rem);
      font-weight: 700; margin-bottom: 3rem;
    }
    .divider { width: 48px; height: 3px; background: var(--yellow); margin: 1rem 0 3rem; border-radius: 2px; }

    /* ABOUT */
    .about-grid { display: grid; grid-template-columns: 1fr 1fr; gap: 3rem; align-items: center; }
    .about-text p { color: var(--muted); margin-bottom: 1rem; }
    .about-text p strong { color: var(--text); }
    .about-facts { display: grid; gap: 0.75rem; margin-top: 1.5rem; }
    .fact {
      display: flex; align-items: center; gap: 0.75rem;
      font-size: 0.9rem;
    }
    .fact-icon { color: var(--yellow); font-size: 1.1rem; flex-shrink: 0; }
    .about-avatar {
      background: var(--dark2); border: 1px solid var(--border);
      border-radius: 20px; padding: 3rem 2rem;
      text-align: center;
    }
    .avatar-circle {
      width: 100px; height: 100px; border-radius: 50%;
      background: linear-gradient(135deg, var(--yellow) 0%, var(--yellow-dim) 100%);
      display: flex; align-items: center; justify-content: center;
      font-size: 2.5rem; font-weight: 700; color: var(--dark);
      margin: 0 auto 1rem;
    }
    .avatar-name { font-size: 1.1rem; font-weight: 600; margin-bottom: 0.25rem; }
    .avatar-role { font-size: 0.85rem; color: var(--muted); }
    .available-badge {
      display: inline-flex; align-items: center; gap: 0.4rem;
      background: rgba(63,185,80,0.15); border: 1px solid rgba(63,185,80,0.3);
      color: #3fb950; font-size: 0.78rem; padding: 0.3rem 0.75rem;
      border-radius: 100px; margin-top: 1rem;
    }
    .available-badge::before {
      content: ''; width: 7px; height: 7px; border-radius: 50%;
      background: #3fb950; animation: pulse 2s ease-in-out infinite;
    }
    @keyframes pulse { 0%,100% { opacity: 1; } 50% { opacity: 0.4; } }

    /* SKILLS */
    .skills-grid { display: grid; grid-template-columns: repeat(auto-fill, minmax(280px, 1fr)); gap: 1.25rem; }
    .skill-card {
      background: var(--dark2); border: 1px solid var(--border);
      border-radius: var(--radius); padding: 1.5rem;
      transition: border-color 0.2s, transform 0.2s;
    }
    .skill-card:hover { border-color: rgba(247,201,72,0.4); transform: translateY(-3px); }
    .skill-card-title {
      font-size: 0.8rem; font-weight: 600; color: var(--yellow);
      text-transform: uppercase; letter-spacing: 0.1em; margin-bottom: 1rem;
    }
    .badges { display: flex; flex-wrap: wrap; gap: 0.5rem; }
    .badge {
      font-size: 0.78rem; padding: 0.3rem 0.7rem; border-radius: 6px;
      background: var(--dark3); border: 1px solid var(--border);
      color: var(--muted); font-family: 'Fira Code', monospace;
    }

    /* PROJECTS */
    .projects-grid { display: grid; grid-template-columns: repeat(auto-fill, minmax(300px, 1fr)); gap: 1.25rem; }
    .project-card {
      background: var(--dark2); border: 1px solid var(--border);
      border-radius: var(--radius); padding: 1.5rem;
      display: flex; flex-direction: column; gap: 0.75rem;
      transition: border-color 0.2s, transform 0.2s;
    }
    .project-card:hover { border-color: rgba(247,201,72,0.4); transform: translateY(-3px); }
    .project-icon { font-size: 1.8rem; }
    .project-title { font-size: 1.05rem; font-weight: 600; }
    .project-desc { font-size: 0.88rem; color: var(--muted); flex: 1; }
    .project-tags { display: flex; flex-wrap: wrap; gap: 0.4rem; }
    .project-tag {
      font-size: 0.72rem; padding: 0.2rem 0.55rem; border-radius: 4px;
      background: rgba(247,201,72,0.1); color: var(--yellow);
      border: 1px solid rgba(247,201,72,0.2);
    }
    .project-links { display: flex; gap: 1rem; margin-top: 0.5rem; }
    .project-links a {
      font-size: 0.82rem; color: var(--muted); text-decoration: none;
      display: flex; align-items: center; gap: 0.3rem;
      transition: color 0.2s;
    }
    .project-links a:hover { color: var(--yellow); }

    /* CONTACT */
    .contact-card {
      background: var(--dark2); border: 1px solid var(--border);
      border-radius: 20px; padding: 3rem; text-align: center;
    }
    .contact-card h3 { font-size: 1.8rem; font-weight: 700; margin-bottom: 0.75rem; }
    .contact-card p { color: var(--muted); max-width: 460px; margin: 0 auto 2rem; }
    .contact-links { display: flex; gap: 1rem; justify-content: center; flex-wrap: wrap; }
    .contact-link {
      display: flex; align-items: center; gap: 0.5rem;
      background: var(--dark3); border: 1px solid var(--border);
      color: var(--text); text-decoration: none;
      padding: 0.65rem 1.25rem; border-radius: var(--radius);
      font-size: 0.88rem; transition: border-color 0.2s, color 0.2s;
    }
    .contact-link:hover { border-color: var(--yellow); color: var(--yellow); }

    /* FOOTER */
    footer {
      text-align: center; padding: 2rem;
      border-top: 1px solid var(--border);
      font-size: 0.82rem; color: var(--muted);
    }
    footer span { color: var(--yellow); }

    @media (max-width: 640px) {
      .about-grid { grid-template-columns: 1fr; }
      nav .nav-links { display: none; }
    }
  </style>
</head>
<body>

<nav>
  <div class="nav-logo">&lt;TsheringDorji /&gt;</div>
  <ul class="nav-links">
    <li><a href="#about">About</a></li>
    <li><a href="#skills">Skills</a></li>
    <li><a href="#projects">Projects</a></li>
    <li><a href="#contact">Contact</a></li>
  </ul>
</nav>

<!-- HERO -->
<div class="hero">
  <div>
    <div class="hero-tag">🇧🇹 Based in Bhutan</div>
    <h1>Hi, I'm <span>Tshering Dorji</span><br/>Frontend Developer</h1>
    <p>I craft responsive, accessible, and visually delightful web experiences — turning ideas into pixel-perfect interfaces.</p>
    <div class="hero-btns">
      <a href="#projects" class="btn-primary">View My Work</a>
      <a href="#contact" class="btn-ghost">Get In Touch</a>
    </div>
  </div>
</div>

<!-- ABOUT -->
<section id="about">
  <div class="section-label">// who am i</div>
  <h2 class="section-title">About Me</h2>
  <div class="divider"></div>
  <div class="about-grid">
    <div class="about-text">
      <p>I'm a <strong>passionate Frontend Developer</strong> from the Kingdom of Bhutan 🇧🇹, with a love for building clean, intuitive, and high-performance web applications.</p>
      <p>With hands-on experience in <strong>React, Next.js, Tailwind CSS</strong> and modern JavaScript, I specialize in turning designs into fully functional products that users love.</p>
      <p>I believe great software is not just about code — it's about creating experiences that feel natural and effortless for every user.</p>
      <div class="about-facts">
        <div class="fact"><span class="fact-icon">🎯</span> Goal: Becoming a remote Frontend Engineer</div>
        <div class="fact"><span class="fact-icon">🌱</span> Currently learning: TypeScript & advanced React patterns</div>
        <div class="fact"><span class="fact-icon">🤝</span> Open to: Remote collaboration & freelance</div>
        <div class="fact"><span class="fact-icon">📫</span> tsheringdorji@gmail.com</div>
        <div class="fact"><span class="fact-icon">🐙</span> github.com/TsheringDorji23</div>
      </div>
    </div>
    <div class="about-avatar">
      <div class="avatar-circle">TD</div>
      <div class="avatar-name">Tshering Dorji</div>
      <div class="avatar-role">Frontend Developer · Bhutan 🇧🇹</div>
      <div class="available-badge">Open to opportunities</div>
    </div>
  </div>
</section>

<!-- SKILLS -->
<section id="skills">
  <div class="section-label">// what i use</div>
  <h2 class="section-title">Tech Stack & Tools</h2>
  <div class="divider"></div>
  <div class="skills-grid">
    <div class="skill-card">
      <div class="skill-card-title">🚀 Languages</div>
      <div class="badges">
        <span class="badge">JavaScript</span>
        <span class="badge">TypeScript</span>
        <span class="badge">HTML5</span>
        <span class="badge">CSS3</span>
        <span class="badge">Python</span>
      </div>
    </div>
    <div class="skill-card">
      <div class="skill-card-title">🛠️ Frameworks</div>
      <div class="badges">
        <span class="badge">React</span>
        <span class="badge">Next.js</span>
        <span class="badge">Vue.js</span>
        <span class="badge">Tailwind CSS</span>
        <span class="badge">Node.js</span>
        <span class="badge">Express</span>
      </div>
    </div>
    <div class="skill-card">
      <div class="skill-card-title">🗄️ Databases</div>
      <div class="badges">
        <span class="badge">MongoDB</span>
        <span class="badge">PostgreSQL</span>
        <span class="badge">MySQL</span>
      </div>
    </div>
    <div class="skill-card">
      <div class="skill-card-title">☁️ DevOps & Tools</div>
      <div class="badges">
        <span class="badge">Git</span>
        <span class="badge">GitHub</span>
        <span class="badge">Docker</span>
        <span class="badge">Figma</span>
        <span class="badge">VS Code</span>
        <span class="badge">Linux</span>
      </div>
    </div>
  </div>
</section>

<!-- PROJECTS -->
<section id="projects">
  <div class="section-label">// what i've built</div>
  <h2 class="section-title">Featured Projects</h2>
  <div class="divider"></div>
  <div class="projects-grid">
    <div class="project-card">
      <div class="project-icon">🛒</div>
      <div class="project-title">E-Commerce Dashboard</div>
      <div class="project-desc">A full-featured admin dashboard for managing products, orders, and analytics — built with React and Tailwind CSS.</div>
      <div class="project-tags">
        <span class="project-tag">React</span>
        <span class="project-tag">Tailwind</span>
        <span class="project-tag">Node.js</span>
      </div>
      <div class="project-links">
        <a href="https://github.com/TsheringDorji23" target="_blank">⭐ GitHub</a>
        <a href="#" target="_blank">🚀 Live Demo</a>
      </div>
    </div>
    <div class="project-card">
      <div class="project-icon">🌤️</div>
      <div class="project-title">Weather App</div>
      <div class="project-desc">A beautiful, responsive weather application with location-based forecasts and animated weather icons.</div>
      <div class="project-tags">
        <span class="project-tag">JavaScript</span>
        <span class="project-tag">API</span>
        <span class="project-tag">CSS3</span>
      </div>
      <div class="project-links">
        <a href="https://github.com/TsheringDorji23" target="_blank">⭐ GitHub</a>
        <a href="#" target="_blank">🚀 Live Demo</a>
      </div>
    </div>
    <div class="project-card">
      <div class="project-icon">📝</div>
      <div class="project-title">Task Manager</div>
      <div class="project-desc">A productivity app with drag-and-drop task management, categories, and due date reminders.</div>
      <div class="project-tags">
        <span class="project-tag">Next.js</span>
        <span class="project-tag">MongoDB</span>
        <span class="project-tag">TypeScript</span>
      </div>
      <div class="project-links">
        <a href="https://github.com/TsheringDorji23" target="_blank">⭐ GitHub</a>
        <a href="#" target="_blank">🚀 Live Demo</a>
      </div>
    </div>
  </div>
</section>

<!-- CONTACT -->
<section id="contact">
  <div class="contact-card">
    <h3>Let's Work Together 🤝</h3>
    <p>I'm currently open to remote frontend roles and freelance projects. If you have an opportunity or just want to say hi, my inbox is always open!</p>
    <a href="mailto:tsheringdorji@gmail.com" class="btn-primary" style="display:inline-block; margin-bottom: 2rem;">Say Hello 👋</a>
    <div class="contact-links">
      <a href="https://github.com/TsheringDorji23" target="_blank" class="contact-link">🐙 GitHub</a>
      <a href="https://linkedin.com/in/TsheringDorji23" target="_blank" class="contact-link">💼 LinkedIn</a>
      <a href="https://twitter.com/TsheringDorji23" target="_blank" class="contact-link">🐦 Twitter</a>
      <a href="https://dev.to/TsheringDorji23" target="_blank" class="contact-link">📝 Dev.to</a>
    </div>
  </div>
</section>

<footer>
  <p>Designed & built by <span>Tshering Dorji</span> · 🇧🇹 Bhutan · 2025</p>
</footer>

</body>
</html>
<h1 align="center">Hi 👋, I'm Tshering Dorji</h1>

<h3 align="center">
Frontend Developer | Angular | React | TypeScript
</h3>

<p align="center">
<img src="https://readme-typing-svg.demolab.com?font=Poppins&size=24&duration=3000&pause=1000&center=true&vCenter=true&width=700&lines=Frontend+Developer;Angular+Developer;React+Developer;TypeScript+Developer;Always+Learning+New+Technologies🚀" />
</p>

---

# 👨‍💻 About Me

- 💼 Frontend Developer at **NGN Technologies**
- ⚖️ Supporting the **G2C Judiciary Project**
- 🌱 Learning **Angular**, **Three.js**, and **React**
- 📍 Thimphu, Bhutan
- 🎯 Goal: Become a Senior Frontend Engineer

---

# 🚀 Tech Stack

<p align="center">

<img src="https://skillicons.dev/icons?i=angular,react,ts,js,html,css,bootstrap,nodejs,express,postgres,mysql,git,github,vscode,postman" />

</p>

---

# 📊 GitHub Stats

<p align="center">

<img height="170" src="https://github-readme-stats.vercel.app/api?username=TsheringDorji23&show_icons=true&theme=tokyonight"/>

<img height="170" src="https://github-readme-stats.vercel.app/api/top-langs/?username=TsheringDorji23&layout=compact&theme=tokyonight"/>

</p>

---

# 🔥 GitHub Streak

<p align="center">

<img src="https://github-readme-streak-stats.herokuapp.com/?user=TsheringDorji23&theme=tokyonight"/>

</p>

---

# 🏆 GitHub Trophy

<p align="center">

<img src="https://github-profile-trophy.vercel.app/?username=TsheringDorji23&theme=tokyonight&row=1&column=6"/>

</p>

---

# 📈 Visitor Count

<p align="center">

<img src="https://komarev.com/ghpvc/?username=TsheringDorji23&label=Visitors&color=blue&style=flat"/>

</p>

---

# 📫 Connect with Me

📧 Email: your-email@example.com

💼 LinkedIn: Coming Soon

🌐 Portfolio: Coming Soon

![snake gif](https://github.com/Platane/snk/raw/output/github-contribution-grid-snake.svg)
