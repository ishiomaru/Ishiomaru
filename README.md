<div class="profile-root">

<style>
@import url('https://fonts.googleapis.com/css2?family=Inter:wght@400;600&family=Noto+Sans+JP:wght@400;600&display=swap');
:root {
  --bg: #ffffff;
  --fg: #202124;
  --accent: #007acc;
  --secondary: #586069;
  --card: #f7f9fc;
  --border: #e0e7f1;
  --space-1: 4px;
  --space-2: 8px;
  --space-3: 16px;
  --space-4: 32px;
  --space-5: 48px;
  --font-base: 1rem;
  --font-lg: 1.5625rem;
  --font-xl: 2.441rem;
}

.profile-root {
  font-family: "Inter", "Noto Sans JP", system-ui, -apple-system, BlinkMacSystemFont, "Segoe UI", sans-serif;
  color: var(--fg);
  background: var(--bg);
  line-height: 1.65;
  max-width: 920px;
  margin: 0 auto;
  padding: var(--space-5) var(--space-3);
}

.card {
  background: var(--card);
  border: 1px solid var(--border);
  border-radius: 18px;
  padding: var(--space-4);
  margin-bottom: var(--space-4);
  box-shadow: 0 15px 45px rgba(0, 32, 63, 0.08);
}

.hero h1 {
  font-size: var(--font-xl);
  margin-bottom: var(--space-2);
}

.hero p {
  color: var(--secondary);
  margin-bottom: var(--space-3);
}

.hero-icons {
  display: flex;
  gap: var(--space-2);
  margin-bottom: var(--space-3);
}

.hero-icons a {
  width: 40px;
  height: 40px;
  border-radius: 12px;
  border: 1px solid var(--border);
  display: flex;
  align-items: center;
  justify-content: center;
  color: var(--accent);
  background: var(--bg);
  text-decoration: none;
  transition: transform 0.2s ease;
}

.hero-icons a:hover {
  transform: translateY(-2px);
}

.meta-grid {
  display: grid;
  grid-template-columns: repeat(auto-fit, minmax(180px, 1fr));
  gap: var(--space-3);
}

.meta-grid div {
  background: var(--bg);
  border-radius: 12px;
  padding: var(--space-3);
  border: 1px solid var(--border);
}

.meta-grid span {
  display: block;
}

.meta-grid .label {
  font-size: 0.8rem;
  letter-spacing: 0.08em;
  text-transform: uppercase;
  color: var(--secondary);
}

.section-title {
  font-size: var(--font-lg);
  margin-bottom: var(--space-2);
}

.stack-grid {
  display: grid;
  grid-template-columns: repeat(auto-fit, minmax(140px, 1fr));
  gap: var(--space-2);
}

.stack-card {
  display: flex;
  align-items: center;
  gap: var(--space-2);
  padding: var(--space-2);
  border: 1px solid var(--border);
  border-radius: 12px;
  background: var(--bg);
}

.stack-card img {
  width: 32px;
  height: 32px;
}

.stats-table,
.stats-table td {
  border: none;
}

.stats-table td {
  padding: var(--space-2);
}

.featured-grid {
  display: grid;
  grid-template-columns: repeat(auto-fit, minmax(240px, 1fr));
  gap: var(--space-3);
  text-align: center;
}

.featured-grid img {
  width: 100%;
}

.contact-links {
  display: grid;
  grid-template-columns: repeat(auto-fit, minmax(220px, 1fr));
  gap: var(--space-2);
}

.icon-pill {
  display: flex;
  align-items: center;
  gap: var(--space-2);
  padding: var(--space-2);
  border-radius: 14px;
  border: 1px solid var(--border);
  text-decoration: none;
  color: var(--fg);
  background: var(--bg);
  transition: border-color 0.2s ease, transform 0.2s ease;
}

.icon-pill:hover {
  border-color: var(--accent);
  transform: translateY(-2px);
}

.icon-pill svg {
  width: 20px;
  height: 20px;
  color: var(--accent);
}

@media (max-width: 480px) {
  .profile-root {
    padding: var(--space-4) var(--space-2);
  }

  .hero h1 {
    font-size: 2rem;
  }

  .meta-grid {
    grid-template-columns: 1fr;
  }

  .stats-table img {
    width: 100%;
  }
}
</style>

<section class="card hero" id="hero">
  <h1>👋 Hi, I'm <strong>Ishiomaru</strong></h1>
  <p>採用・OSS の読者が 1 スクロール以内で人物像と最新成果を把握できるように設計しています。</p>
  <div class="hero-icons">
    <a href="https://github.com/ishiomaru" aria-label="GitHub">
      <svg role="img" viewBox="0 0 24 24" fill="currentColor" xmlns="http://www.w3.org/2000/svg"><path d="M12 .297c-6.63 0-12 5.373-12 12 0 5.302 3.438 9.8 8.205 11.385.6.113.82-.258.82-.577 0-.285-.01-1.04-.015-2.04-3.338.724-4.042-1.61-4.042-1.61-.546-1.387-1.333-1.757-1.333-1.757-1.089-.745.084-.73.084-.73 1.205.084 1.84 1.237 1.84 1.237 1.07 1.835 2.807 1.305 3.492.998.108-.776.418-1.305.762-1.605-2.665-.305-5.466-1.332-5.466-5.93 0-1.31.469-2.38 1.236-3.22-.124-.303-.536-1.523.117-3.176 0 0 1.008-.322 3.301 1.23a11.52 11.52 0 0 1 3.003-.404c1.02.005 2.045.138 3.003.404 2.291-1.552 3.297-1.23 3.297-1.23.655 1.653.243 2.873.12 3.176.77.84 1.235 1.91 1.235 3.22 0 4.61-2.807 5.624-5.479 5.921.43.372.823 1.102.823 2.222 0 1.606-.014 2.898-.014 3.293 0 .323.216.697.825.578C20.565 22.092 24 17.592 24 12.297 24 5.67 18.627.297 12 .297z"/></svg>
    </a>
    <a href="mailto:contact@ishiomaru.dev" aria-label="Email">
      <svg role="img" viewBox="0 0 24 24" fill="currentColor" xmlns="http://www.w3.org/2000/svg"><path d="M1.5 4.5h21a1 1 0 0 1 1 1v13a1 1 0 0 1-1 1h-21a1 1 0 0 1-1-1v-13a1 1 0 0 1 1-1zm.5 2.118V18h20V6.618l-10 6.25z"/></svg>
    </a>
    <a href="https://www.linkedin.com/in/ishiomaru" aria-label="LinkedIn">
      <svg role="img" viewBox="0 0 24 24" fill="currentColor" xmlns="http://www.w3.org/2000/svg"><path d="M20.447 20.452h-3.554v-5.569c0-1.328-.027-3.036-1.852-3.036-1.853 0-2.136 1.448-2.136 2.944v5.661H9.352V9h3.414v1.561h.049c.476-.9 1.637-1.852 3.37-1.852 3.601 0 4.267 2.37 4.267 5.455v6.288zM5.337 7.433a2.062 2.062 0 1 1 0-4.124 2.062 2.062 0 0 1 0 4.124zM3.559 20.452h3.554V9H3.559z"/></svg>
    </a>
  </div>
  <div class="meta-grid">
    <div><span class="label">Role</span><span class="value">Full-stack Engineer</span></div>
    <div><span class="label">Focus</span><span class="value">Hiring readiness / OSS contributions</span></div>
    <div><span class="label">Location</span><span class="value">Tokyo, Japan (JST)</span></div>
    <div><span class="label">Availability</span><span class="value">Open to collaborations</span></div>
  </div>
</section>

<section class="card" id="about">
  <h2 class="section-title">💫 About Me</h2>
  <ul>
    <li>フロントエンド / フルスタック領域を中心に、個人・OSS・業務での開発経験を横断的に蓄積。</li>
    <li>GitHub special repository を活用し、私の変遷やアカウント横断の活動履歴を 1 ページで俯瞰できるよう情報設計。</li>
    <li>採用強化、技術ブランディング、コミュニティ連携の 3 本柱で価値提供することが現在のテーマ。</li>
  </ul>
</section>

<section class="card" id="tech">
  <h2 class="section-title">🛠 Tech Stacks / Skills</h2>
  <div class="stack-grid">
    <div class="stack-card">
      <img src="https://cdn.jsdelivr.net/gh/devicons/devicon/icons/typescript/typescript-original.svg" alt="TypeScript" />
      <div>
        <strong>TypeScript</strong>
        <div>5.x / Application Core</div>
      </div>
    </div>
    <div class="stack-card">
      <img src="https://cdn.jsdelivr.net/gh/devicons/devicon/icons/react/react-original.svg" alt="React" />
      <div>
        <strong>React / Next.js</strong>
        <div>SPA & Edge Rendering</div>
      </div>
    </div>
    <div class="stack-card">
      <img src="https://cdn.jsdelivr.net/gh/devicons/devicon/icons/nodejs/nodejs-original.svg" alt="Node.js" />
      <div>
        <strong>Node.js</strong>
        <div>API・ワークフロー</div>
      </div>
    </div>
    <div class="stack-card">
      <img src="https://cdn.jsdelivr.net/gh/devicons/devicon/icons/python/python-original.svg" alt="Python" />
      <div>
        <strong>Python</strong>
        <div>ML / Automation</div>
      </div>
    </div>
    <div class="stack-card">
      <img src="https://cdn.jsdelivr.net/gh/devicons/devicon/icons/github/github-original.svg" alt="GitHub Actions" />
      <div>
        <strong>GitHub Actions</strong>
        <div>CI/CD & Stats Update</div>
      </div>
    </div>
    <div class="stack-card">
      <img src="https://cdn.jsdelivr.net/gh/devicons/devicon/icons/figma/figma-original.svg" alt="Design" />
      <div>
        <strong>Design System</strong>
        <div>Light Tritanopia Palette</div>
      </div>
    </div>
  </div>
</section>

<section class="card" id="stats">
  <h2 class="section-title">📊 GitHub Stats</h2>
  <table class="stats-table" align="center">
    <tr>
      <td colspan="2"><img src="https://streak-stats.demolab.com?user=ishiomaru&hide_border=true&card_width=720&ring=007acc&fire=ffb703" alt="GitHub Streak" /></td>
    </tr>
    <tr>
      <td><img src="https://github-readme-stats.vercel.app/api?username=ishiomaru&hide_border=true&show_icons=true&count_private=true&theme=transparent" alt="GitHub Stats" /></td>
      <td><img src="https://github-readme-stats.vercel.app/api/top-langs/?username=ishiomaru&layout=compact&hide_border=true&theme=transparent" alt="Top Languages" /></td>
    </tr>
  </table>
</section>

<section class="card" id="repos">
  <h2 class="section-title">⭐ Featured Repositories</h2>
  <div class="featured-grid">
    <a href="https://github.com/ishiomaru/colorball-detection">
      <img src="https://github-readme-stats.vercel.app/api/pin/?username=ishiomaru&repo=colorball-detection&hide_border=true&theme=transparent" alt="colorball-detection" />
    </a>
    <a href="https://github.com/ishiomaru/ishiomaru">
      <img src="https://github-readme-stats.vercel.app/api/pin/?username=ishiomaru&repo=ishiomaru&hide_border=true&theme=transparent" alt="ishiomaru" />
    </a>
  </div>
</section>

<section class="card" id="contact">
  <h2 class="section-title">📫 Contact / Social Links</h2>
  <div class="contact-links">
    <a class="icon-pill" href="mailto:contact@ishiomaru.dev" target="_blank" rel="noreferrer" aria-label="Email">
      <svg viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round"><path d="M4 4h16v16H4z"/><path d="M4 8l8 5 8-5"/></svg>
      <span>contact@ishiomaru.dev</span>
    </a>
    <a class="icon-pill" href="https://github.com/ishiomaru" target="_blank" rel="noreferrer" aria-label="GitHub">
      <svg role="img" viewBox="0 0 24 24" fill="currentColor" xmlns="http://www.w3.org/2000/svg"><path d="M12 .297c-6.63 0-12 5.373-12 12 0 5.302 3.438 9.8 8.205 11.385.6.113.82-.258.82-.577 0-.285-.01-1.04-.015-2.04-3.338.724-4.042-1.61-4.042-1.61-.546-1.387-1.333-1.757-1.333-1.757-1.089-.745.084-.73.084-.73 1.205.084 1.84 1.237 1.84 1.237 1.07 1.835 2.807 1.305 3.492.998.108-.776.418-1.305.762-1.605-2.665-.305-5.466-1.332-5.466-5.93 0-1.31.469-2.38 1.236-3.22-.124-.303-.536-1.523.117-3.176 0 0 1.008-.322 3.301 1.23a11.52 11.52 0 0 1 3.003-.404c1.02.005 2.045.138 3.003.404 2.291-1.552 3.297-1.23 3.297-1.23.655 1.653.243 2.873.12 3.176.77.84 1.235 1.91 1.235 3.22 0 4.61-2.807 5.624-5.479 5.921.43.372.823 1.102.823 2.222 0 1.606-.014 2.898-.014 3.293 0 .323.216.697.825.578C20.565 22.092 24 17.592 24 12.297 24 5.67 18.627.297 12 .297z"/></svg>
      <span>@ishiomaru</span>
    </a>
    <a class="icon-pill" href="https://www.linkedin.com/in/ishiomaru" target="_blank" rel="noreferrer" aria-label="LinkedIn">
      <svg role="img" viewBox="0 0 24 24" fill="currentColor" xmlns="http://www.w3.org/2000/svg"><path d="M20.447 20.452h-3.554v-5.569c0-1.328-.027-3.036-1.852-3.036-1.853 0-2.136 1.448-2.136 2.944v5.661H9.352V9h3.414v1.561h.049c.476-.9 1.637-1.852 3.37-1.852 3.601 0 4.267 2.37 4.267 5.455v6.288zM5.337 7.433a2.062 2.062 0 1 1 0-4.124 2.062 2.062 0 0 1 0 4.124zM3.559 20.452h3.554V9H3.559z"/></svg>
      <span>LinkedIn / ishiomaru</span>
    </a>
    <a class="icon-pill" href="https://twitter.com/ishiomaru" target="_blank" rel="noreferrer" aria-label="X / Twitter">
      <svg viewBox="0 0 24 24" fill="currentColor" xmlns="http://www.w3.org/2000/svg"><path d="M18.244 2.25h3.308l-7.227 8.26 8.502 11.24H16.17l-4.743-6.211-5.428 6.211H2.691l7.732-8.85L2.25 2.25h7.006l4.29 5.617z"/></svg>
      <span>@ishiomaru</span>
    </a>
  </div>
</section>

</div>
