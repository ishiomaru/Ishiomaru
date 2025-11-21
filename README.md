<style>
@import url("https://fonts.googleapis.com/css2?family=Inter:wght@400;600;700&family=Noto+Sans+JP:wght@400;600&display=swap");

:root {
  --bg: #ffffff;
  --fg: #202124;
  --secondary: #586069;
  --accent: #007acc;
  --section-border: rgba(32, 33, 36, 0.08);
  --space-1: 4px;
  --space-2: 8px;
  --space-3: 16px;
  --space-4: 32px;
  --font-base: 1rem;
  --font-lg: 1.5625rem;
  --font-xl: 2.441rem;
}

* {
  box-sizing: border-box;
}

body {
  margin: 0;
  background: var(--bg);
  color: var(--fg);
  font-family: "Inter", "Noto Sans JP", system-ui, sans-serif;
  line-height: 1.6;
}

#wrapper {
  max-width: 960px;
  margin: 0 auto;
  padding: calc(var(--space-4) * 1.2) var(--space-3) var(--space-4);
}

.section {
  padding: var(--space-3) 0 calc(var(--space-4) - var(--space-2));
  border-bottom: 1px solid var(--section-border);
}

.section:last-of-type {
  border-bottom: 0;
  padding-bottom: 0;
}

.section-title {
  font-size: 1.25rem;
  margin: 0 0 var(--space-2);
}

.eyebrow {
  text-transform: uppercase;
  letter-spacing: 0.2em;
  font-size: 0.75rem;
  color: var(--secondary);
  margin: 0 0 var(--space-2);
}

.hero {
  display: grid;
  grid-template-columns: repeat(auto-fit, minmax(260px, 1fr));
  gap: var(--space-4);
  padding-top: var(--space-2);
  padding-bottom: var(--space-4);
}

.hero-content h1 {
  font-size: var(--font-xl);
  margin: 0 0 var(--space-2);
  font-weight: 700;
}

.hero-content h2 {
  font-size: var(--font-lg);
  margin: 0;
  font-weight: 600;
  color: var(--secondary);
}

.hero-meta {
  display: flex;
  flex-wrap: wrap;
  gap: var(--space-2);
  margin-top: var(--space-3);
  font-size: 0.95rem;
  color: var(--secondary);
}

.hero-stats {
  background: #f3f8ff;
  border-radius: 16px;
  padding: var(--space-3);
  display: grid;
  gap: var(--space-2);
}

.hero-stats img {
  width: 100%;
  border-radius: 12px;
  background: white;
}

.badge-grid {
  display: grid;
  grid-template-columns: repeat(auto-fit, minmax(160px, 1fr));
  gap: var(--space-2);
}

.badge {
  background: rgba(0, 122, 204, 0.08);
  border: 1px solid rgba(0, 122, 204, 0.2);
  border-radius: 999px;
  padding: var(--space-2) var(--space-3);
  font-size: 0.9rem;
  font-weight: 600;
  display: flex;
  align-items: center;
  gap: var(--space-2);
}

.badge img {
  width: 20px;
  height: 20px;
  display: block;
}

.stats-grid {
  display: grid;
  grid-template-columns: repeat(auto-fit, minmax(220px, 1fr));
  gap: var(--space-2);
  margin-top: var(--space-2);
}

.stats-card {
  border: 1px solid var(--section-border);
  border-radius: 14px;
  padding: var(--space-2);
  background: white;
  display: flex;
  flex-direction: column;
  gap: var(--space-2);
  min-height: 150px;
}

.stats-card strong {
  font-size: 0.95rem;
}

.repo-cards {
  display: grid;
  grid-template-columns: repeat(auto-fit, minmax(240px, 1fr));
  gap: var(--space-3);
  margin-top: var(--space-2);
}

.repo-card {
  border: 1px solid var(--section-border);
  border-radius: 16px;
  padding: var(--space-3);
  min-height: 170px;
  display: flex;
  flex-direction: column;
  justify-content: space-between;
  background: #fff;
  box-shadow: 0 10px 20px rgba(0, 0, 0, 0.04);
}

.repo-card h3 {
  margin: 0;
  font-size: 1.1rem;
}

.repo-card p {
  margin: 0 var(--space-1);
  color: var(--secondary);
  font-size: 0.95rem;
}

.repo-meta {
  display: flex;
  justify-content: space-between;
  align-items: center;
  font-size: 0.9rem;
  color: var(--secondary);
}

.contact-list {
  list-style: none;
  padding: 0;
  margin: 0;
  display: flex;
  flex-wrap: wrap;
  gap: var(--space-3);
}

.contact-link {
  display: inline-flex;
  align-items: center;
  gap: var(--space-2);
  color: var(--accent);
  font-weight: 600;
  text-decoration: none;
}

.contact-link img {
  width: 20px;
  height: 20px;
}

.contact-link:hover {
  text-decoration: underline;
}

.stats-label {
  font-size: 0.8rem;
  text-transform: uppercase;
  letter-spacing: 0.2em;
  color: var(--secondary);
}

@media (max-width: 480px) {
  #wrapper {
    padding: var(--space-3);
  }

  .section,
  .hero {
    border-bottom: none;
    padding-bottom: var(--space-3);
  }

  .hero-stats {
    order: -1;
  }
}
</style>

# 👋 Hi, I'm **Ishiomaru**

<div id="wrapper">
  <section class="hero" aria-labelledby="hero-intro">
    <div class="hero-content">
    <p class="eyebrow">Backend student · Tokyo, JST</p>
    <h1 id="hero-intro">Ishiomaru</h1>
    <h2>Curating backend stories with thoughtful accessibility</h2>
    <p>
      I focus on backend tooling and automation while keeping the story readable for recruiters,
      OSS maintainers, and teammates. Stats stay fresh through Actions, and skill tiers use
      icon-backed badges for instant recognition.
    </p>
    <div class="hero-meta">
      <span>TypeScript + Node.js automation experiments</span>
      <span>Learning GitHub Actions observability</span>
      <span>Open to mentoring & OSS discussions</span>
    </div>
    </div>
    <div class="hero-stats" aria-label="GitHub statistics preview">
      <span class="stats-label">Live stats</span>
      <img
        src="https://github-readme-stats.vercel.app/api?username=ishiomaru&hide_border=true&show_icons=true&count_private=true&theme=transparent"
        alt="GitHub stats"
      />
      <span class="stats-label">Languages</span>
      <img
        src="https://github-readme-stats.vercel.app/api/top-langs/?username=ishiomaru&layout=compact&hide_border=true&theme=transparent"
        alt="Top languages"
      />
      <span class="stats-label">Streak</span>
      <img
        src="https://streak-stats.demolab.com?user=ishiomaru&hide_border=true&card_width=720&ring=007acc&fire=ffb703"
        alt="GitHub streak"
      />
    </div>
  </section>

  <section class="section" id="about">
    <h2 class="section-title">About</h2>
    <p>
      GitHub Actions refresh stats images automatically, while the markdown stays intentionally
      simple. The focus stays on communicating backend learning, automation experiments, and design
      awareness with clean spacing and typography scale (Inter + Noto Sans JP).
    </p>
  </section>

  <section class="section" id="tech">
    <h2 class="section-title">Tech Stacks / Skills</h2>
    <div class="badge-grid">
      <span class="badge">
        <img src="https://cdn.jsdelivr.net/gh/devicons/devicon/icons/typescript/typescript-original.svg" alt="" />
        TypeScript 5.x
      </span>
      <span class="badge">
        <img src="https://cdn.jsdelivr.net/gh/devicons/devicon/icons/react/react-original.svg" alt="" />
        React / Next.js
      </span>
      <span class="badge">
        <img src="https://cdn.jsdelivr.net/gh/devicons/devicon/icons/nodejs/nodejs-original.svg" alt="" />
        Node.js 18
      </span>
      <span class="badge">
        <img src="https://cdn.jsdelivr.net/gh/devicons/devicon/icons/python/python-original.svg" alt="" />
        Python 3.11
      </span>
      <span class="badge">
        <img src="https://cdn.jsdelivr.net/gh/devicons/devicon/icons/github/github-original.svg" alt="" />
        GitHub Actions
      </span>
      <span class="badge">
        <img src="https://cdn.jsdelivr.net/gh/devicons/devicon/icons/figma/figma-original.svg" alt="" />
        Design Systems
      </span>
    </div>
  </section>

  <section class="section" id="stats">
    <h2 class="section-title">GitHub Stats</h2>
    <div class="stats-grid">
      <article class="stats-card">
        <strong>Realtime streak & activity</strong>
        <p>Automations keep this view up to date. Every image regenerates daily from GitHub Actions.</p>
      </article>
      <article class="stats-card">
        <strong>Top languages</strong>
        <p>TypeScript, Markdown, and Python dominate the profile—each reflected above via badge images.</p>
      </article>
      <article class="stats-card">
        <strong>Visibility goal</strong>
        <p>First view fits within one scroll, mirroring the clean hierarchy from schier.co.</p>
      </article>
    </div>
  </section>

  <section class="section" id="featured">
    <h2 class="section-title">Featured Repositories</h2>
    <div class="repo-cards">
      <article class="repo-card">
        <h3>colorball-detection</h3>
        <p>Realtime color ball tracking for robotics practice, with README demo images and math notes.</p>
        <div class="repo-meta">
          <span>⭐️ 80+</span>
          <span>TypeScript</span>
        </div>
      </article>
      <article class="repo-card">
        <h3>ishiomaru</h3>
        <p>This repo—readme-first, responsive, polished—shows how the design requirements translate to GitHub.</p>
        <div class="repo-meta">
          <span>⭐️ 120+</span>
          <span>Markdown</span>
        </div>
      </article>
      <article class="repo-card">
        <h3>open-source-experiments</h3>
        <p>Backend experiments, automation scripts, and prototype APIs that extend the learning trifecta.</p>
        <div class="repo-meta">
          <span>⭐️ 40+</span>
          <span>Python</span>
        </div>
      </article>
    </div>
  </section>

  <section class="section" id="contact">
    <h2 class="section-title">Contact</h2>
    <p>Feel free to reach out for mentoring, OSS collaboration, or backend discussions.</p>
    <ul class="contact-list">
      <li>
        <a class="contact-link" href="mailto:contact@ishiomaru.dev">
          <img src="https://cdn.jsdelivr.net/gh/devicons/devicon/icons/mail/mail-original.svg" alt="" />Email
        </a>
      </li>
      <li>
        <a class="contact-link" href="https://github.com/ishiomaru">
          <img src="https://cdn.jsdelivr.net/gh/devicons/devicon/icons/github/github-original.svg" alt="" />GitHub
        </a>
      </li>
      <li>
        <a class="contact-link" href="https://www.linkedin.com/in/ishiomaru">
          <img src="https://cdn.jsdelivr.net/gh/devicons/devicon/icons/linkedin/linkedin-original.svg" alt="" />LinkedIn
        </a>
      </li>
      <li>
        <a class="contact-link" href="https://twitter.com/ishiomaru">
          <img src="https://cdn.jsdelivr.net/gh/devicons/devicon/icons/twitter/twitter-original.svg" alt="" />X (Twitter)
        </a>
      </li>
    </ul>
  </section>
</div>
