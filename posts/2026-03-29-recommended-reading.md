---
layout: post
title: Recommended Reading
date: 2026-03-29
description: A place to collect papers, blog posts, books, and resource links worth revisiting.
---

# Recommended Reading

平时看到很多有价值的内容，临时收藏容易遗忘它为什么值得读，也不容易在需要时找回来。这里整理的每一条推荐，都会写上推荐理由和个人笔记——不只是存一个链接。

积累到一定程度后，某些方向会单独拆成专题文章，比如 Digital Human 推荐阅读、3D Vision 推荐阅读、值得反复看的技术博客等。

<p class="appendix-hint">记录格式参见文末 <a href="#format-guide">附录</a>。</p>

---

## Claude Code

### 代码规范

<div class="reading-card">
  <div class="reading-card-header">
    <span class="reading-badge reading-badge--guide">Guide</span>
    <span class="reading-tags">Engineering · Research · Code Quality</span>
  </div>
  <h4><a href="https://goodresearch.dev/" target="_blank" rel="noreferrer">The Good Research Code Handbook</a></h4>
  <p class="reading-reason">面向研究者的代码规范手册，强调可读性、可复现性和项目结构。不是通用工程规范的翻版，而是专门针对学术项目的现实约束来写的，适合养成研究代码的良好习惯。</p>
</div>

<div class="reading-card">
  <div class="reading-card-header">
    <span class="reading-badge reading-badge--guide">Guide</span>
    <span class="reading-tags">Engineering · Code Quality</span>
  </div>
  <h4><a href="https://claude.ai/public/artifacts/5fd3148e-0e30-401a-bf4a-01078736e629" target="_blank" rel="noreferrer">30 Code Quality Best Practices</a></h4>
  <p class="reading-reason">30 条代码质量实践的精炼清单，条目短且可操作，适合直接当作 code review 或日常写代码时的自查 checklist。</p>
</div>

### 如何使用 Claude

<div class="reading-card">
  <div class="reading-card-header">
    <span class="reading-badge reading-badge--repo">Repo</span>
    <span class="reading-tags">Claude Code · Workflow · Prompt</span>
  </div>
  <h4><a href="https://github.com/shanraisshan/claude-code-best-practice" target="_blank" rel="noreferrer">claude-code-best-practice</a></h4>
  <p class="reading-reason">社区整理的 Claude Code 使用最佳实践，涵盖常见的 prompt 模式、工作流配置和避坑经验。适合刚开始系统使用 Claude Code 的阶段通读一遍。</p>
</div>

### Skills 与工具

<div class="reading-card">
  <div class="reading-card-header">
    <span class="reading-badge reading-badge--tool">Tool</span>
    <span class="reading-tags">Claude Code · Skills</span>
  </div>
  <h4><a href="https://github.com/lijigang/ljg-skills" target="_blank" rel="noreferrer">ljg-skills</a></h4>
  <p class="reading-reason">一套结构清晰的 Claude Code skill 集合，包含多个实用场景的 skill 定义方式。适合学习如何为自己的工作流定制 skill。</p>
</div>

<div class="reading-card">
  <div class="reading-card-header">
    <span class="reading-badge reading-badge--framework">Framework</span>
    <span class="reading-tags">Claude Code · Agentic · Methodology</span>
  </div>
  <h4><a href="https://github.com/obra/superpowers" target="_blank" rel="noreferrer">Superpowers — Agentic Skills Framework</a></h4>
  <p class="reading-reason">提出了一套 agentic skills 框架和软件开发方法论，把 AI 协作工作流结构化。对理解 Claude Code 的深度用法和整体心智模型有帮助。</p>
</div>

<div class="reading-card">
  <div class="reading-card-header">
    <span class="reading-badge reading-badge--tool">Tool</span>
    <span class="reading-tags">Claude Code · Research · Skills</span>
  </div>
  <h4><a href="https://github.com/mvanhorn/last30days-skill" target="_blank" rel="noreferrer">last30days-skill</a></h4>
  <p class="reading-reason">跨多平台（Reddit、X、YouTube、HN、Polymarket 等）做话题研究的 Claude skill，输出带来源引用的合成摘要。适合快速了解某个方向最近 30 天的动态。</p>
</div>

<div class="reading-card">
  <div class="reading-card-header">
    <span class="reading-badge reading-badge--tool">Tool</span>
    <span class="reading-tags">Claude Code · Skills · AI Builders</span>
  </div>
  <h4><a href="https://github.com/zarazhangrui/follow-builders/blob/main/README.zh-CN.md" target="_blank" rel="noreferrer">follow-builders</a></h4>
  <p class="reading-reason">追踪顶级 AI builder 在 X 和 YouTube 上内容的 Claude skill，自动整理成可读摘要。比手动刷信息流效率高很多。</p>
</div>

---

## Model Learning

<div class="reading-card">
  <div class="reading-card-header">
    <span class="reading-badge reading-badge--blog">Blog</span>
    <span class="reading-tags">Transformer · Foundation Model · Visualization</span>
  </div>
  <h4><a href="https://www.vizuaranewsletter.com/p/the-transformers" target="_blank" rel="noreferrer">The Transformers — Vizuara Newsletter</a></h4>
  <p class="reading-reason">对 Transformer 架构的直观视觉化解读，图文并茂，注重建立几何和流程上的直觉。适合在深读原论文之前先建立一个整体印象。</p>
</div>

<div class="reading-card">
  <div class="reading-card-header">
    <span class="reading-badge reading-badge--tutorial">Tutorial</span>
    <span class="reading-tags">Diffusion · Generative Model · Math</span>
  </div>
  <h4><a href="https://the-principles-of-diffusion-models.github.io/#/blog" target="_blank" rel="noreferrer">The Principles of Diffusion Models</a></h4>
  <p class="reading-reason">系统梳理扩散模型数学原理的网页教程，从 score matching 到 DDPM 都有覆盖，兼顾直觉和推导。适合想系统补扩散模型基础的阶段。</p>
</div>

---

<div id="format-guide" class="appendix-block">
  <details>
    <summary>附录：记录格式参考</summary>
    <div class="appendix-content">
      <p>以后新增的每一条推荐尽量按下面这个格式来写：</p>
      <pre><code>### 资源标题

- Type: Paper / Blog / Book / Tutorial / Tool / Framework / Repo / Course
- Link: https://...
- Why: 用 1～3 句话说明推荐理由
- Note: 自己的理解、疑问或启发
- Tags: tag1, tag2, tag3</code></pre>
      <p>类型徽章与 <code>Type</code> 字段对应，标签用于后续按主题归类。不需要记录阅读状态。</p>
    </div>
  </details>
</div>
