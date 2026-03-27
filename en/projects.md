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
    display: flex;
    flex-direction: column;
    gap: 1rem;
  }

  .project-card {
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

  .project-card h3 {
    margin: 0 0 0.5rem 0;
    font-size: 1.05rem;
    display: flex;
    align-items: center;
    justify-content: space-between;
    color: inherit;
  }

  .project-toggle {
    font-size: 0.75rem;
    color: #888;
    transition: transform 0.25s;
    flex-shrink: 0;
    margin-left: 0.75rem;
  }

  body.dark-theme .project-toggle { color: #aaa; }

  .project-card.open .project-toggle {
    transform: rotate(180deg);
  }

  .project-description-wrapper {
    position: relative;
    overflow: hidden;
    max-height: 1.55em;
    transition: max-height 0.35s ease;
  }

  .project-card.open .project-description-wrapper {
    max-height: 600px;
  }

  .project-description {
    font-size: 0.92rem;
    line-height: 1.6;
    margin: 0;
    color: inherit;
    opacity: 0.85;
  }

  .project-fade {
    position: absolute;
    bottom: 0; left: 0; right: 0;
    height: 1.55em;
    background: linear-gradient(to bottom, rgba(224,224,224,0) 0%, rgba(224,224,224,1) 100%);
    pointer-events: none;
    transition: opacity 0.25s;
  }

  body.dark-theme .project-fade {
    background: linear-gradient(to bottom, rgba(34,40,50,0) 0%, rgba(34,40,50,1) 100%);
  }

  .project-card.open .project-fade { opacity: 0; }

  /* Tags — always visible */
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

  .project-footer {
    display: flex;
    align-items: center;
    justify-content: flex-end;
    flex-wrap: wrap;
    gap: 0.5rem;
    margin-top: 0.75rem;
  }

  .project-buttons {
    display: flex;
    gap: 0.6rem;
    flex-wrap: wrap;
  }

  /* All buttons — teal */
  .btn {
    display: inline-flex;
    align-items: center;
    gap: 0.3rem;
    padding: 0.38rem 0.9rem;
    border-radius: 5px;
    font-size: 0.84rem;
    font-weight: 600;
    text-decoration: none;
    transition: background-color 0.2s, color 0.2s, border-color 0.2s;
    background-color: rgba(42, 157, 143, 0.15);
    color: #1a7a6e;
    border: 1.5px solid rgba(42, 157, 143, 0.4);
  }

  .btn:hover {
    text-decoration: none;
    background-color: #2a9d8f;
    color: #fff !important;
    border-color: #2a9d8f;
  }

  body.dark-theme .btn {
    background-color: rgba(42, 157, 143, 0.18);
    color: #5ecfc3;
    border-color: rgba(94, 207, 195, 0.35);
  }

  body.dark-theme .btn:hover {
    background-color: #2a9d8f;
    color: #fff !important;
    border-color: #2a9d8f;
  }

  .divider {
    border: none;
    border-top: 1px solid rgba(0,0,0,0.1);
    margin: 2rem 0 0 0;
  }

  body.dark-theme .divider {
    border-color: rgba(255,255,255,0.08);
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
    <div class="project-card" id="project-{{ project.id }}" onclick="toggleProject('{{ project.id }}')">
      <h3>
        {{ project.title }}
        <span class="project-toggle">▼</span>
      </h3>
      <div class="project-description-wrapper">
        <p class="project-description" style="white-space: pre-line;">{{ project.description }}</p>
        <div class="project-fade"></div>
      </div>
      {% if project.tags %}
      <div class="project-tags">
        {% for tag in project.tags %}<span class="project-tag">{{ tag }}</span>{% endfor %}
      </div>
      {% endif %}
      <div class="project-footer">
        <div class="project-buttons">
          {% if project.credits_url and project.credits_url != "" %}
            <a class="btn" href="{{ project.credits_url }}" target="_blank" rel="noopener noreferrer" onclick="event.stopPropagation()">📄 Credits</a>
          {% endif %}
          {% if project.repo_url and project.repo_url != "" %}
            <a class="btn" href="{{ project.repo_url }}" target="_blank" rel="noopener noreferrer" onclick="event.stopPropagation()">🐙 Repository</a>
          {% endif %}
          {% if project.dataset_url and project.dataset_url != "" %}
            <a class="btn" href="{{ project.dataset_url }}" target="_blank" rel="noopener noreferrer" onclick="event.stopPropagation()">🗄️ Dataset</a>
          {% endif %}
        </div>
      </div>
    </div>
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
    <div class="project-card" id="project-{{ project.id }}" onclick="toggleProject('{{ project.id }}')">
      <h3>
        {{ project.title }}
        <span class="project-toggle">▼</span>
      </h3>
      <div class="project-description-wrapper">
        <p class="project-description" style="white-space: pre-line;">{{ project.description }}</p>
        <div class="project-fade"></div>
      </div>
      {% if project.tags %}
      <div class="project-tags">
        {% for tag in project.tags %}<span class="project-tag">{{ tag }}</span>{% endfor %}
      </div>
      {% endif %}
      <div class="project-footer">
        <div class="project-buttons">
          {% if project.report_url and project.report_url != "" %}
            <a class="btn" href="{{ project.report_url }}" target="_blank" rel="noopener noreferrer" onclick="event.stopPropagation()">📄 Report</a>
          {% endif %}
          {% if project.repo_url and project.repo_url != "" %}
            <a class="btn" href="{{ project.repo_url }}" target="_blank" rel="noopener noreferrer" onclick="event.stopPropagation()">🐙 Repository</a>
          {% endif %}
        </div>
      </div>
    </div>
    {% endfor %}
  </div>
</div>
{% endif %}

<script>
  function toggleProject(id) {
    const card = document.getElementById('project-' + id);
    card.classList.toggle('open');
  }
</script>