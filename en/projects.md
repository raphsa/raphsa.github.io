---
layout: default
title: Projects
lang: en
permalink: /en/projects/
---

<style>
  .projects-section {
    margin-top: 2rem;
  }

  .projects-section h2 {
    font-size: 1.1rem;
    font-weight: 700;
    margin-bottom: 0.85rem;
    display: flex;
    align-items: center;
    gap: 0.5rem;
    letter-spacing: 0.01em;
  }

  .section-dot {
    display: inline-block;
    width: 10px;
    height: 10px;
    border-radius: 50%;
    flex-shrink: 0;
  }

  .section-dot.wip {
    background-color: #f59e0b;
    box-shadow: 0 0 0 3px rgba(245, 158, 11, 0.2);
    animation: pulse 2s infinite;
  }

  .section-dot.done {
    background-color: #2a9d8f;
  }

  @keyframes pulse {
    0%, 100% { box-shadow: 0 0 0 3px rgba(245, 158, 11, 0.2); }
    50%       { box-shadow: 0 0 0 6px rgba(245, 158, 11, 0.08); }
  }

  .projects-grid {
    display: grid;
    grid-template-columns: repeat(auto-fill, minmax(300px, 1fr));
    align-items: start;
    gap: 1.1rem;
  }

  /* Every card is the same fixed height, laid out as a column so the
     buttons always sit flush at the bottom regardless of how much
     text is above them — no more per-card size drift. */
  .project-card {
    display: flex;
    flex-direction: column;
    min-height: 300px;
    border-radius: 8px;
    padding: 1.1rem 1.25rem 1rem 1.25rem;
    cursor: pointer;
    transition: box-shadow 0.2s, transform 0.2s;
    background-color: #E0E0E0;
    color: #222832;
    box-shadow: 0px 4px 10px rgba(0, 0, 0, 0.2);
  }

  body.dark-theme .project-card {
    background-color: #222832;
    color: #E0E0E0;
    box-shadow: none;
    border: 1px solid rgba(255,255,255,0.06);
  }

  .project-card:hover {
    transform: translateY(-2px);
    box-shadow: 0px 6px 16px rgba(0, 0, 0, 0.25);
  }

  body.dark-theme .project-card:hover {
    box-shadow: 0px 4px 14px rgba(0,0,0,0.5);
  }

  /* Title + description share one fixed-height block, so every card is the
     same size — but the title always renders in full (never truncated) and
     takes whatever space it needs; the description just fills what's left,
     down to nothing if a long title uses the whole block. */
  .project-card-preview {
    height: 9rem;
    overflow: hidden;
  }

  .project-card-title {
    margin: 0 0 0.4rem 0;
    font-size: 1.05rem;
    color: inherit;
  }

  /* Line-clamped to 4 as an upper bound for the common case (gives a clean "…"
     instead of a hard cut mid-line); the parent's fixed height is what actually
     enforces the title-takes-priority behavior when the title runs long. */
  .project-description-preview {
    font-size: 0.92rem;
    line-height: 1.6;
    margin: 0;
    color: inherit;
    opacity: 0.85;
    display: -webkit-box;
    -webkit-line-clamp: 4;
    -webkit-box-orient: vertical;
    overflow: hidden;
  }

  .project-tags {
    display: flex;
    flex-wrap: wrap;
    gap: 0.35rem;
    margin-top: 0.65rem;
  }

  .project-tag {
    font-size: 0.75rem;
    padding: 0.15rem 0.55rem;
    border-radius: 4px;
    font-weight: 500;
    background-color: #dbeafe;
    color: #1d4ed8;
    border: 1px solid rgba(29, 78, 216, 0.2);
  }

  body.dark-theme .project-tag {
    background-color: rgba(29, 78, 216, 0.2);
    color: #93c5fd;
    border-color: rgba(147, 197, 253, 0.25);
  }

  .project-tag-more {
    background-color: transparent;
    color: inherit;
    opacity: 0.65;
    border-color: rgba(0,0,0,0.15);
  }

  body.dark-theme .project-tag-more {
    border-color: rgba(255,255,255,0.2);
  }

  /* Pushed to the bottom of the flex column, so it always lines up
     across cards no matter how much text sits above it. */
  .project-footer {
    display: flex;
    align-items: center;
    justify-content: flex-end;
    flex-wrap: wrap;
    gap: 0.5rem;
    margin-top: auto;
    padding-top: 0.75rem;
  }

  .project-buttons {
    display: flex;
    gap: 0.6rem;
    flex-wrap: wrap;
  }

  /* .btn styles now live in _layouts/default.html so they can be reused site-wide */

  .divider {
    border: none;
    border-top: 1px solid rgba(0,0,0,0.1);
    margin: 2rem 0 0 0;
  }

  body.dark-theme .divider {
    border-color: rgba(255,255,255,0.08);
  }

  /* Modal — opened on card click, sits on top of the page so the grid never reflows */
  .project-modal-overlay {
    position: fixed;
    inset: 0;
    background: rgba(0,0,0,0.5);
    display: flex;
    align-items: center;
    justify-content: center;
    padding: 20px;
    opacity: 0;
    pointer-events: none;
    transition: opacity 0.25s ease;
    z-index: 1000;
  }

  .project-modal-overlay.open {
    opacity: 1;
    pointer-events: auto;
  }

  .project-modal {
    position: relative;
    background-color: #E0E0E0;
    color: #222832;
    border-radius: 10px;
    max-width: 640px;
    width: 100%;
    max-height: 85vh;
    overflow-y: auto;
    padding: 1.75rem;
    box-shadow: 0 20px 50px rgba(0,0,0,0.3);
    transform: translateY(12px);
    transition: transform 0.25s ease;
    text-align: left;
  }

  .project-modal-overlay.open .project-modal {
    transform: translateY(0);
  }

  body.dark-theme .project-modal {
    background-color: #222832;
    color: #E0E0E0;
  }

  .project-modal-close {
    position: absolute;
    top: 0.9rem;
    right: 0.9rem;
    background: none;
    border: none;
    font-size: 1.1rem;
    cursor: pointer;
    color: inherit;
    opacity: 0.6;
    padding: 0.3rem;
    line-height: 1;
  }

  .project-modal-close:hover {
    opacity: 1;
  }

  .project-modal h2 {
    margin: 0 0 0.9rem 0;
    padding-right: 1.5rem;
    font-size: 1.25rem;
  }

  .project-modal .project-description {
    font-size: 0.95rem;
    line-height: 1.65;
    opacity: 0.9;
    margin: 0 0 1.1rem 0;
  }

  .project-modal .project-tags {
    margin-top: 0;
    margin-bottom: 1.1rem;
  }

  .project-modal .project-footer {
    margin-top: 0;
    padding-top: 0;
    justify-content: flex-start;
  }
</style>

# Projects

{% assign wip_projects = site.data.projects | where: "status", "wip" %}
{% assign done_projects = site.data.projects | where: "status", "done" %}

{% if wip_projects.size > 0 %}
<div class="projects-section">
  <h2><span class="section-dot wip"></span> In Progress</h2>
  <div class="projects-grid">
    {% for project in wip_projects %}
      {% include project-card.html project=project type="wip" %}
    {% endfor %}
  </div>
</div>
{% endif %}

{% if done_projects.size > 0 %}
{% if wip_projects.size > 0 %}<hr class="divider">{% endif %}
<div class="projects-section">
  <h2><span class="section-dot done"></span> Completed</h2>
  <div class="projects-grid">
    {% for project in done_projects %}
      {% include project-card.html project=project type="done" %}
    {% endfor %}
  </div>
</div>
{% endif %}

<div class="project-modal-overlay" id="projectModalOverlay" onclick="closeProjectModal()">
  <div class="project-modal" onclick="event.stopPropagation()">
    <button class="project-modal-close" onclick="closeProjectModal()" aria-label="Close">✕</button>
    <div id="projectModalBody"></div>
  </div>
</div>

<script>
  function openProjectModal(id) {
    const tpl = document.getElementById('modal-content-' + id);
    if (!tpl) return;
    document.getElementById('projectModalBody').innerHTML = tpl.innerHTML;
    document.getElementById('projectModalOverlay').classList.add('open');
    document.body.style.overflow = 'hidden';
  }

  function closeProjectModal() {
    document.getElementById('projectModalOverlay').classList.remove('open');
    document.body.style.overflow = '';
  }

  document.addEventListener('keydown', function (e) {
    if (e.key === 'Escape') closeProjectModal();
  });
</script>
