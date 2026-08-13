<script setup>
import { experience, metrics, profile, projects, stack, strengths } from './resume-data'

function printResume() {
  window.print()
}
</script>

<template>
  <main class="resume-page">
    <header class="resume-header">
      <div class="identity">
        <div class="monogram" aria-hidden="true">ZJ</div>
        <div>
          <p class="resume-overline">PERSONAL RESUME / 2026</p>
          <h1>{{ profile.name }}</h1>
          <p class="resume-role">{{ profile.role }}</p>
        </div>
      </div>

      <div class="resume-contact">
        <span>现任：{{ profile.currentFocus }}</span>
        <a :href="profile.github" target="_blank" rel="noreferrer">GitHub：life2you ↗</a>
        <button class="print-button screen-only" type="button" @click="printResume">打印 / 导出 PDF</button>
      </div>
    </header>

    <section class="profile-panel" aria-labelledby="profile-title">
      <div>
        <p class="panel-kicker">CAREER PROFILE</p>
        <h2 id="profile-title">以工程能力支撑经营决策与团队交付。</h2>
        <p>{{ profile.summary }}</p>
      </div>
      <aside class="focus-panel" aria-label="职业方向">
        <p>FOCUS</p>
        <div class="focus-tags">
          <span>研发管理</span>
          <span>财务系统</span>
          <span>AI 工程化</span>
        </div>
        <small>Java 与企业系统研发 · 2017 — 至今</small>
      </aside>
    </section>

    <section class="resume-section strengths-section" aria-labelledby="strengths-title">
      <div class="section-heading">
        <span>01</span>
        <h2 id="strengths-title">核心能力</h2>
        <p>KEY STRENGTHS</p>
      </div>
      <ul class="strength-list">
        <li v-for="strength in strengths" :key="strength">{{ strength }}</li>
      </ul>
    </section>

    <section class="resume-section" aria-labelledby="experience-title">
      <div class="section-heading">
        <span>02</span>
        <h2 id="experience-title">工作经历</h2>
        <p>EXPERIENCE</p>
      </div>
      <div class="experience-list">
        <article v-for="item in experience" :key="`${item.company}-${item.period}`" class="experience-item" :class="{ 'is-current': item.current }">
          <div class="experience-meta">
            <time>{{ item.period }}</time>
            <span v-if="item.current">CURRENT</span>
          </div>
          <div class="experience-body">
            <div class="item-heading">
              <div>
                <h3>{{ item.company }}</h3>
                <p>{{ item.role }}</p>
              </div>
            </div>
            <p class="item-summary">{{ item.summary }}</p>
            <ul class="detail-list">
              <li v-for="point in item.points" :key="point">{{ point }}</li>
            </ul>
          </div>
        </article>
      </div>
    </section>

    <section class="resume-section achievements-section" aria-labelledby="outcomes-title">
      <div class="section-heading">
        <span>03</span>
        <h2 id="outcomes-title">核心成果</h2>
        <p>SELECTED IMPACT</p>
      </div>
      <div class="metrics-grid">
        <article v-for="metric in metrics" :key="metric.label" class="metric-item">
          <p><strong>{{ metric.value }}</strong><span v-if="metric.suffix">{{ metric.suffix }}</span></p>
          <h3>{{ metric.label }}</h3>
          <small>{{ metric.detail }}</small>
        </article>
      </div>
    </section>

    <section class="resume-section" aria-labelledby="projects-title">
      <div class="section-heading">
        <span>04</span>
        <h2 id="projects-title">代表项目</h2>
        <p>SIGNATURE WORK</p>
      </div>
      <div class="project-list">
        <article v-for="project in projects" :key="project.order" class="project-item">
          <div class="project-number">{{ project.order }}</div>
          <div class="project-content">
            <div class="project-heading">
              <div>
                <p class="project-category">{{ project.eyebrow }}</p>
                <h3>{{ project.title }}</h3>
              </div>
              <p class="project-outcome">{{ project.outcome }}</p>
            </div>
            <p class="item-summary">{{ project.summary }}</p>
            <ul class="detail-list">
              <li v-for="point in project.points" :key="point">{{ point }}</li>
            </ul>
            <div class="project-stack" aria-label="相关技术">
              <span v-for="tag in project.tags" :key="tag">{{ tag }}</span>
            </div>
          </div>
        </article>
      </div>
    </section>

    <section class="resume-section skills-section" aria-labelledby="skills-title">
      <div class="section-heading">
        <span>05</span>
        <h2 id="skills-title">专业技能</h2>
        <p>TECHNOLOGY &amp; TOOLS</p>
      </div>
      <div class="skills-cloud">
        <span v-for="item in stack" :key="item">{{ item }}</span>
      </div>
    </section>

    <footer class="resume-footer">
      <span>赵军 · {{ profile.role }}</span>
      <span>在线简历 / 公开职业概览</span>
    </footer>
  </main>
</template>
