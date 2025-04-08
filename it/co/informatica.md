---
layout: default
title: Corsi
lang: it
permalink: /it/courses/co/informatica
---

<ol>
  <li>
    <button class="toggle-btn" onclick="toggleSection('section1')"> Introduzione al laboratorio
    </button>
    <div id="section1" class="collapsible">
      <p>In lavorazione</p>
    </div>
  </li>
  <li>
    <button class="toggle-btn" onclick="toggleSection('section2')">Le <b>funzioni</b></button>
    <div id="section2" class="collapsible">
      <p>In lavorazione</p>
    </div>
  </li>
  <li>
    <button class="toggle-btn" onclick="toggleSection('section3')"><b>Selezione</b> e <b>Input</b></button>
    <div id="section3" class="collapsible">
      <p>In lavorazione</p>
    </div>
  </li>
  <li>
    <button class="toggle-btn" onclick="toggleSection('section4')">Le <b>sequenze</b></button>
    <div id="section4" class="collapsible">
      <p>In lavorazione</p>
    </div>
  </li>
  <li>
    <button class="toggle-btn" onclick="toggleSection('section5')">Il <b>for</b></button>
    <div id="section5" class="collapsible">
      <p>In lavorazione</p>
    </div>
  </li>
  <li>
    <button class="toggle-btn" onclick="toggleSection('section6')">Il ciclo <b>while</b></button>
    <div id="section6" class="collapsible">
      <p>In lavorazione</p>
    </div>
  </li>
  <li>
    <button class="toggle-btn" onclick="toggleSection('section7')">Il <b>debug</b></button>
    <div id="section7" class="collapsible">
      <p>In lavorazione</p>
    </div>
  </li>
  <li>
    <button class="toggle-btn" onclick="toggleSection('section8')">Le <b>liste</b></button>
    <div id="section8" class="collapsible">
      <p>In lavorazione</p>
    </div>
  </li>
  <li>
    <button class="toggle-btn" onclick="toggleSection('section9')">La <b>ricorsione</b></button>
    <div id="section9" class="collapsible">
      <p>In lavorazione</p>
    </div>
  </li>
  <li>
    <button class="toggle-btn" onclick="toggleSection('section10')">La <b>complessità computazionale</b></button>
    <div id="section10" class="collapsible">
      <p>In lavorazione</p>
    </div>
  </li>
  <li>
    <button class="toggle-btn" onclick="toggleSection('section11')">I <b>dizionari</b></button>
    <div id="section11" class="collapsible">
      <p>In lavorazione</p>
    </div>
  </li>
  <li>
    <button class="toggle-btn" onclick="toggleSection('section12')"><b>Classi</b> e <b>Oggetti</b></button>
    <div id="section12" class="collapsible">
      <p>In lavorazione</p>
    </div>
  </li>
  <li>
    <button class="toggle-btn" onclick="toggleSection('section13')">Le <b>eccezioni</b></button>
    <div id="section13" class="collapsible">
      <p>In lavorazione</p>
    </div>
  </li>
  <li>
    <button class="toggle-btn" onclick="toggleSection('section14')">Il linguaggio <b>R</b></button>
    <div id="section14" class="collapsible">
      <p>In lavorazione</p>
    </div>
  </li>
  <li>
    <button class="toggle-btn" onclick="toggleSection('section15')">Gli <b>alberi binari</b></button>
    <div id="section15" class="collapsible">
      <p>In lavorazione</p>
    </div>
  </li>
  <li>
    <button class="toggle-btn" onclick="toggleSection('section16')">La <b>comprehension</b></button>
    <div id="section16" class="collapsible">
      <p>In lavorazione</p>
    </div>
  </li>
</ol>

<style>
  .toggle-btn {
    background: none;
    border: none;
    font-weight: bold;
    font-size: 1.3em;
    color: inherit;
    cursor: pointer;
    text-align: left;
    width: 100%;
    padding: 8px 0;
    transition: color 0.3s;
  }

  .toggle-btn:hover {
    color: #9c5ffd;
    text-decoration: underline;
  }

  .collapsible {
    display: none;
    margin-top: 5px;
    margin-bottom: 15px;
    padding-left: 20px;
  }
</style>

<script>
  // to check whether 
  function toggleSection(id) {
    const section = document.getElementById(id);
    if (section.style.display === "block") {
      section.style.display = "none";
    } else {
      section.style.display = "block";
    }
  }
</script>