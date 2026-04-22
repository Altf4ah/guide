<!DOCTYPE html>
<html lang="en">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>EET424 — Energy Management Study Guide</title>
<link href="https://fonts.googleapis.com/css2?family=Syne:wght@400;600;700;800&family=IBM+Plex+Mono:wght@400;500&family=Lora:ital,wght@0,400;0,500;1,400&display=swap" rel="stylesheet">
<style>
  :root {
    --bg: #0d0f14;
    --surface: #141720;
    --surface2: #1c2030;
    --border: #252a3a;
    --accent: #f0a500;
    --accent2: #e05c3a;
    --green: #3ecf8e;
    --blue: #5b9cf6;
    --text: #d8dde8;
    --muted: #7a849a;
    --heading: #eef0f5;
    --red-tag: #e05c3a;
    --yellow-tag: #f0a500;
    --mono: 'IBM Plex Mono', monospace;
    --sans: 'Syne', sans-serif;
    --serif: 'Lora', serif;
  }

  * { margin: 0; padding: 0; box-sizing: border-box; }

  html { scroll-behavior: smooth; }

  body {
    background: var(--bg);
    color: var(--text);
    font-family: var(--serif);
    font-size: 15px;
    line-height: 1.75;
    min-height: 100vh;
  }

  /* ── TOP BAR ── */
  .topbar {
    position: sticky; top: 0; z-index: 100;
    background: rgba(13,15,20,0.92);
    backdrop-filter: blur(12px);
    border-bottom: 1px solid var(--border);
    display: flex; align-items: center; gap: 0;
    overflow-x: auto;
    padding: 0 24px;
  }
  .topbar-brand {
    font-family: var(--sans); font-weight: 800; font-size: 13px;
    color: var(--accent); letter-spacing: .1em; text-transform: uppercase;
    white-space: nowrap; padding: 14px 20px 14px 0;
    border-right: 1px solid var(--border); margin-right: 4px;
  }
  .nav-pill {
    font-family: var(--sans); font-size: 11px; font-weight: 600;
    letter-spacing: .08em; text-transform: uppercase;
    color: var(--muted); text-decoration: none;
    padding: 8px 14px; border-radius: 4px;
    white-space: nowrap; transition: all .2s;
  }
  .nav-pill:hover { color: var(--heading); background: var(--surface2); }
  .nav-pill.active { color: var(--accent); }

  /* ── HERO ── */
  .hero {
    padding: 80px 40px 60px;
    max-width: 900px; margin: 0 auto;
    position: relative;
  }
  .hero::before {
    content: '';
    position: absolute; top: 0; left: 0; right: 0; height: 1px;
    background: linear-gradient(90deg, transparent, var(--accent), transparent);
  }
  .hero-label {
    font-family: var(--mono); font-size: 11px; letter-spacing: .2em;
    text-transform: uppercase; color: var(--accent); margin-bottom: 20px;
    display: flex; align-items: center; gap: 10px;
  }
  .hero-label::before {
    content: ''; display: inline-block; width: 30px; height: 1px;
    background: var(--accent);
  }
  h1 {
    font-family: var(--sans); font-weight: 800; font-size: clamp(32px, 5vw, 56px);
    color: var(--heading); line-height: 1.1; margin-bottom: 20px;
  }
  h1 span { color: var(--accent); }
  .hero-meta {
    display: flex; flex-wrap: wrap; gap: 12px; margin-top: 24px;
  }
  .meta-chip {
    font-family: var(--mono); font-size: 11px;
    background: var(--surface2); border: 1px solid var(--border);
    color: var(--muted); padding: 5px 12px; border-radius: 100px;
  }
  .meta-chip.hi { color: var(--green); border-color: rgba(62,207,142,.3); background: rgba(62,207,142,.05); }

  /* ── LEGEND ── */
  .legend {
    max-width: 900px; margin: 0 auto 40px; padding: 0 40px;
    display: flex; gap: 20px; flex-wrap: wrap;
  }
  .leg-item {
    display: flex; align-items: center; gap: 8px;
    font-family: var(--sans); font-size: 12px; color: var(--muted);
  }
  .dot { width: 10px; height: 10px; border-radius: 50%; flex-shrink: 0; }
  .dot.red { background: var(--red-tag); }
  .dot.yellow { background: var(--yellow-tag); }

  /* ── LAYOUT ── */
  .content { max-width: 900px; margin: 0 auto; padding: 0 40px 80px; }

  /* ── MODULE HEADER ── */
  .module-header {
    margin: 60px 0 32px;
    padding: 28px 32px;
    background: var(--surface);
    border: 1px solid var(--border);
    border-left: 4px solid var(--accent);
    border-radius: 2px;
    position: relative; overflow: hidden;
  }
  .module-header::after {
    content: attr(data-num);
    position: absolute; right: 24px; top: 50%; transform: translateY(-50%);
    font-family: var(--sans); font-weight: 800; font-size: 80px;
    color: rgba(240,165,0,.06); line-height: 1; pointer-events: none;
  }
  .module-label {
    font-family: var(--mono); font-size: 10px; letter-spacing: .2em;
    text-transform: uppercase; color: var(--accent); margin-bottom: 6px;
  }
  .module-title {
    font-family: var(--sans); font-weight: 700; font-size: 20px;
    color: var(--heading);
  }

  /* ── TOPIC CARD ── */
  .topic {
    margin-bottom: 28px;
    border: 1px solid var(--border);
    border-radius: 4px;
    background: var(--surface);
    overflow: hidden;
  }
  .topic-head {
    display: flex; align-items: center; gap: 12px;
    padding: 16px 20px;
    background: var(--surface2);
    border-bottom: 1px solid var(--border);
    cursor: pointer; user-select: none;
  }
  .topic-head:hover { background: #1f2535; }
  .priority-tag {
    font-family: var(--mono); font-size: 10px; font-weight: 500;
    letter-spacing: .1em; text-transform: uppercase;
    padding: 3px 9px; border-radius: 100px; flex-shrink: 0;
  }
  .priority-tag.red {
    background: rgba(224,92,58,.15); color: var(--red-tag);
    border: 1px solid rgba(224,92,58,.3);
  }
  .priority-tag.yellow {
    background: rgba(240,165,0,.12); color: var(--yellow-tag);
    border: 1px solid rgba(240,165,0,.25);
  }
  .topic-num {
    font-family: var(--mono); font-size: 11px; color: var(--muted);
  }
  .topic-title {
    font-family: var(--sans); font-weight: 600; font-size: 14px;
    color: var(--heading); flex: 1;
  }
  .toggle-icon {
    font-family: var(--mono); font-size: 18px; color: var(--muted);
    transition: transform .3s; flex-shrink: 0;
  }
  .topic-body {
    padding: 24px;
    display: none;
  }
  .topic.open .topic-body { display: block; }
  .topic.open .toggle-icon { transform: rotate(45deg); color: var(--accent); }

  /* ── PROSE ── */
  .topic-body p { margin-bottom: 14px; }
  .topic-body strong { color: var(--heading); font-weight: 600; }
  .topic-body em { color: var(--accent); font-style: normal; }

  h3 {
    font-family: var(--sans); font-weight: 700; font-size: 14px;
    color: var(--accent); text-transform: uppercase; letter-spacing: .08em;
    margin: 22px 0 12px; padding-bottom: 6px;
    border-bottom: 1px solid var(--border);
  }
  h4 {
    font-family: var(--sans); font-weight: 600; font-size: 13px;
    color: var(--blue); margin: 18px 0 8px;
  }

  /* ── NUMBERED LIST ── */
  ol { padding-left: 0; list-style: none; counter-reset: ol; }
  ol li {
    counter-increment: ol; position: relative;
    padding: 6px 0 6px 34px; border-bottom: 1px solid rgba(255,255,255,.04);
  }
  ol li:last-child { border-bottom: none; }
  ol li::before {
    content: counter(ol);
    position: absolute; left: 0; top: 8px;
    font-family: var(--mono); font-size: 10px; font-weight: 500;
    color: var(--accent); background: rgba(240,165,0,.12);
    width: 22px; height: 22px; border-radius: 50%;
    display: flex; align-items: center; justify-content: center;
  }

  ul { padding-left: 0; list-style: none; }
  ul li { padding: 5px 0 5px 20px; position: relative; }
  ul li::before {
    content: '—'; position: absolute; left: 0;
    color: var(--muted); font-family: var(--mono);
  }

  /* ── TABLE ── */
  .table-wrap { overflow-x: auto; margin: 16px 0; border-radius: 4px; border: 1px solid var(--border); }
  table { width: 100%; border-collapse: collapse; font-size: 13px; }
  thead th {
    font-family: var(--sans); font-weight: 600; font-size: 11px;
    text-transform: uppercase; letter-spacing: .08em;
    color: var(--accent); background: var(--surface2);
    padding: 10px 14px; text-align: left;
    border-bottom: 1px solid var(--border);
  }
  tbody td {
    padding: 9px 14px; border-bottom: 1px solid rgba(37,42,58,.8);
    vertical-align: top;
  }
  tbody tr:last-child td { border-bottom: none; }
  tbody tr:hover td { background: rgba(255,255,255,.02); }

  /* ── FORMULA ── */
  .formula {
    font-family: var(--mono); font-size: 13px;
    background: var(--surface2); border: 1px solid var(--border);
    border-left: 3px solid var(--blue);
    padding: 14px 18px; border-radius: 2px;
    margin: 14px 0; color: var(--blue);
    overflow-x: auto; white-space: pre-wrap;
  }

  /* ── NUMERICAL BLOCK ── */
  .numerical {
    background: rgba(62,207,142,.04);
    border: 1px solid rgba(62,207,142,.2);
    border-left: 3px solid var(--green);
    border-radius: 2px; padding: 18px 20px;
    margin: 16px 0;
  }
  .numerical .num-label {
    font-family: var(--mono); font-size: 10px; letter-spacing: .15em;
    text-transform: uppercase; color: var(--green); margin-bottom: 12px;
  }
  .numerical p, .numerical ol li, .numerical ul li {
    font-size: 13px; color: #b8d8cc;
  }
  .numerical strong { color: var(--green); }
  .numerical .formula {
    background: rgba(62,207,142,.06); border-color: rgba(62,207,142,.3);
    color: var(--green);
  }

  /* ── CALLOUT ── */
  .callout {
    background: rgba(91,156,246,.06);
    border: 1px solid rgba(91,156,246,.25);
    border-radius: 4px; padding: 14px 18px; margin: 14px 0;
    font-size: 13px; color: #a8bfe8;
  }
  .callout strong { color: var(--blue); }

  /* ── PRIORITY MATRIX ── */
  .matrix-table tbody tr td:last-child { font-weight: 600; text-align: center; }

  /* ── FOOTER ── */
  footer {
    text-align: center; padding: 40px;
    font-family: var(--mono); font-size: 11px; color: var(--muted);
    border-top: 1px solid var(--border);
  }

  /* ── SCROLL TO TOP ── */
  #scroll-top {
    position: fixed; bottom: 28px; right: 28px;
    width: 40px; height: 40px; border-radius: 50%;
    background: var(--accent); color: #000;
    font-size: 18px; border: none; cursor: pointer;
    display: flex; align-items: center; justify-content: center;
    box-shadow: 0 4px 20px rgba(240,165,0,.4);
    transition: transform .2s;
  }
  #scroll-top:hover { transform: scale(1.1); }

  @media (max-width: 600px) {
    .hero, .content { padding-left: 18px; padding-right: 18px; }
    .legend { padding: 0 18px; }
  }
</style>
</head>
<body>

<!-- TOP NAV -->
<nav class="topbar">
  <div class="topbar-brand">EET424</div>
  <a class="nav-pill" href="#mod1">Module 1</a>
  <a class="nav-pill" href="#mod2">Module 2</a>
  <a class="nav-pill" href="#mod3">Module 3</a>
  <a class="nav-pill" href="#mod4">Module 4</a>
  <a class="nav-pill" href="#mod5">Module 5</a>
  <a class="nav-pill" href="#matrix">Priority Matrix</a>
</nav>

<!-- HERO -->
<div class="hero">
  <div class="hero-label">S8 EEE · 2019 Scheme · APJ KTU</div>
  <h1>Energy<br><span>Management</span></h1>
  <p style="color:var(--muted);max-width:560px;font-size:14px;">Complete study guide compiled from PYQ analysis across 6 question papers (2023–2025). Every topic is weighted by frequency of appearance.</p>
  <div class="hero-meta">
    <span class="meta-chip">6 Question Papers Analysed</span>
    <span class="meta-chip">5 Modules</span>
    <span class="meta-chip hi">All Numericals Solved</span>
  </div>
</div>

<div class="legend">
  <div class="leg-item"><div class="dot red"></div><strong style="color:var(--red-tag);font-family:var(--sans);font-size:12px;">HIGH PRIORITY</strong> — appeared in 4–6 papers. Do not skip.</div>
  <div class="leg-item"><div class="dot yellow"></div><strong style="color:var(--yellow-tag);font-family:var(--sans);font-size:12px;">MEDIUM PRIORITY</strong> — appeared in 2–3 papers.</div>
</div>

<div class="content">

<!-- ══════════════════════════════════════════════
     MODULE 1
══════════════════════════════════════════════ -->
<div id="mod1" class="module-header" data-num="01">
  <div class="module-label">Module 1 · 7 Hours</div>
  <div class="module-title">Energy Management — General Principles, Planning & Audit</div>
</div>

<!-- 1.1 -->
<div class="topic open">
  <div class="topic-head" onclick="toggle(this)">
    <span class="priority-tag red">High Priority</span>
    <span class="topic-num">1.1</span>
    <span class="topic-title">General Principles of Energy Management</span>
    <span class="toggle-icon">+</span>
  </div>
  <div class="topic-body">
    <p>The <strong>six general principles</strong> are:</p>
    <ol>
      <li><strong>Top management commitment</strong> — Energy management must be driven from the top with allocated budget and authority.</li>
      <li><strong>Establish a written energy policy</strong> — A formal document stating energy efficiency goals and the organisation's commitment.</li>
      <li><strong>Set measurable targets</strong> — Specific, time-bound energy reduction targets (e.g., 10% reduction in 2 years).</li>
      <li><strong>Energy accounting and auditing</strong> — Regular measurement, metering, and monitoring of all energy streams.</li>
      <li><strong>Training and awareness</strong> — Educate staff at all levels; involve all employees in conservation efforts.</li>
      <li><strong>Continuous improvement</strong> — Regular review and updating of practices using a Plan–Do–Check–Act cycle.</li>
    </ol>
    <div class="callout"><strong>Objectives:</strong> Reduce energy costs · Identify wasteful practices · Improve equipment efficiency · Reduce dependence on fossil fuels · Comply with the Energy Conservation Act 2001 · Reduce GHG emissions.</div>
  </div>
</div>

<!-- 1.2 -->
<div class="topic">
  <div class="topic-head" onclick="toggle(this)">
    <span class="priority-tag red">High Priority</span>
    <span class="topic-num">1.2</span>
    <span class="topic-title">Phases of Energy Management Planning</span>
    <span class="toggle-icon">+</span>
  </div>
  <div class="topic-body">
    <h3>Phase 1 — Recognition</h3>
    <ul>
      <li>Identify the need and obtain <strong>top management commitment</strong>.</li>
      <li>Appoint a dedicated Energy Manager.</li>
      <li>Define scope and allocate budget.</li>
    </ul>
    <h3>Phase 2 — Audit and Analysis</h3>
    <p>The most detailed phase. Information collected:</p>
    <ul>
      <li><strong>Historical energy data</strong> — utility bills, fuel purchase records (past 2–3 years).</li>
      <li><strong>Facility inventory</strong> — floor area, equipment list, production output data.</li>
      <li><strong>Energy-consuming systems</strong> — lighting, HVAC, motors, furnaces, boilers.</li>
      <li><strong>Operating patterns</strong> — shifts, seasonal variation, occupancy schedules.</li>
      <li><strong>Baseline specific energy consumption</strong> — energy per unit of output.</li>
      <li>Identification of wastage areas through walkthrough and detailed audit.</li>
    </ul>
    <div class="callout"><strong>For a technical education building,</strong> collect: lighting kWh/month, HVAC consumption, computer lab load, canteen energy, annual utility bills, occupancy hours per day/week.</div>
    <h3>Phase 3 — Implementation</h3>
    <ul>
      <li>Prioritise Energy Conservation Measures (ECMs) by cost-benefit ratio.</li>
      <li>Implement <strong>no-cost and low-cost measures immediately</strong>.</li>
      <li>Prepare detailed project proposals for capital-intensive measures.</li>
      <li>Monitor and verify savings after implementation.</li>
      <li>Report results to management; update the energy baseline.</li>
    </ul>
  </div>
</div>

<!-- 1.3 -->
<div class="topic">
  <div class="topic-head" onclick="toggle(this)">
    <span class="priority-tag red">High Priority</span>
    <span class="topic-num">1.3</span>
    <span class="topic-title">Energy Audit — Definition, Need, Types & Steps</span>
    <span class="toggle-icon">+</span>
  </div>
  <div class="topic-body">
    <h3>Definition</h3>
    <p>An energy audit is a <strong>systematic examination of energy flows</strong> in a facility to identify where energy is used, how efficiently it is used, and where it can be saved.</p>
    <h3>Need</h3>
    <ol>
      <li>Rising energy costs eat into profit margins.</li>
      <li>Identify specific areas of energy waste with measurements.</li>
      <li>Develop a prioritised list of Energy Conservation Opportunities (ECOs).</li>
      <li>Mandatory under the <strong>Energy Conservation Act 2001</strong> for designated consumers.</li>
      <li>Reduce carbon footprint and meet regulatory requirements.</li>
    </ol>
    <h3>Types</h3>
    <div class="table-wrap">
      <table>
        <thead><tr><th>Type</th><th>Description</th></tr></thead>
        <tbody>
          <tr><td><strong>Preliminary / Walk-through</strong></td><td>Quick visual inspection; identifies obvious wastage; low cost; rough estimate of savings potential.</td></tr>
          <tr><td><strong>Detailed / Diagnostic</strong></td><td>In-depth with measurements and instruments; quantifies energy flows; develops investment-grade proposals.</td></tr>
          <tr><td><strong>Investment-grade</strong></td><td>Highest level; full techno-economic analysis; used for securing project financing.</td></tr>
        </tbody>
      </table>
    </div>
    <h3>Steps in Detailed Energy Audit</h3>
    <ol>
      <li><strong>Pre-audit preparation</strong> — Collect utility bills, plant layout, equipment details.</li>
      <li><strong>Walkthrough survey</strong> — Visual inspection of all energy systems.</li>
      <li><strong>Measurement and monitoring</strong> — Use instruments (energy meters, lux meters, flue gas analysers) to record consumption.</li>
      <li><strong>Data analysis</strong> — Calculate specific energy consumption; compare against benchmarks.</li>
      <li><strong>Identify ECOs</strong> — List all opportunities found during measurement phase.</li>
      <li><strong>Financial analysis</strong> — Payback period, NPV, IRR for each ECO.</li>
      <li><strong>Report preparation</strong> — Present findings, recommendations, and action plan.</li>
      <li><strong>Implementation and follow-up</strong> — Carry out measures; verify and report savings.</li>
    </ol>
  </div>
</div>

<!-- 1.4 Instruments -->
<div class="topic">
  <div class="topic-head" onclick="toggle(this)">
    <span class="priority-tag yellow">Medium Priority</span>
    <span class="topic-num">1.4</span>
    <span class="topic-title">Instruments for Energy Audit</span>
    <span class="toggle-icon">+</span>
  </div>
  <div class="topic-body">
    <div class="table-wrap">
      <table>
        <thead><tr><th>Instrument</th><th>Purpose</th></tr></thead>
        <tbody>
          <tr><td><strong>Digital Energy Meter / Power Analyser</strong></td><td>Measures kW, kVAR, kVA, power factor, harmonics, THD.</td></tr>
          <tr><td><strong>Lux Meter</strong></td><td>Measures illumination level in lux; identifies over/under-lit areas.</td></tr>
          <tr><td><strong>IR Thermometer / Thermal Camera</strong></td><td>Detects heat losses in insulation, electrical connections, furnace walls.</td></tr>
          <tr><td><strong>Flue Gas Analyser</strong></td><td>Measures O₂, CO₂, CO, SO₂ in boiler flue gas; calculates combustion efficiency.</td></tr>
          <tr><td><strong>Ultrasonic Flow Meter</strong></td><td>Measures flow rate of steam, water, compressed air — non-invasive.</td></tr>
          <tr><td><strong>Clamp-on Ammeter</strong></td><td>Measures current on live conductors without breaking circuit.</td></tr>
          <tr><td><strong>Anemometer</strong></td><td>Measures air velocity in HVAC ducts.</td></tr>
          <tr><td><strong>Portable Data Logger</strong></td><td>Records energy parameters over time for load profile analysis.</td></tr>
        </tbody>
      </table>
    </div>
  </div>
</div>

<!-- 1.5 Audit Report -->
<div class="topic">
  <div class="topic-head" onclick="toggle(this)">
    <span class="priority-tag red">High Priority</span>
    <span class="topic-num">1.5</span>
    <span class="topic-title">Energy Audit Report</span>
    <span class="toggle-icon">+</span>
  </div>
  <div class="topic-body">
    <p>The audit report is the <strong>final deliverable</strong> that documents all findings and recommendations.</p>
    <h3>General Format / Contents</h3>
    <ol>
      <li><strong>Executive Summary</strong> — Brief overview of key findings and top recommendations.</li>
      <li><strong>Introduction</strong> — Background, scope, and objectives of the audit.</li>
      <li><strong>Facility description</strong> — Plant/building details, process description, utility systems.</li>
      <li><strong>Energy consumption analysis</strong> — Historical data, specific energy consumption, benchmarking against industry norms.</li>
      <li><strong>Energy Conservation Opportunities (ECOs)</strong> — Detailed description of each opportunity identified.</li>
      <li><strong>Financial analysis</strong> — Capital cost, annual savings, payback period, NPV for each ECO.</li>
      <li><strong>Prioritised action plan</strong> — ECOs ranked by ease of implementation and return on investment.</li>
      <li><strong>Appendices</strong> — Raw data, measurement records, equipment datasheets.</li>
    </ol>
  </div>
</div>

<!-- 1.6 Power Quality Audit -->
<div class="topic">
  <div class="topic-head" onclick="toggle(this)">
    <span class="priority-tag red">High Priority</span>
    <span class="topic-num">1.6</span>
    <span class="topic-title">Power Quality Audit</span>
    <span class="toggle-icon">+</span>
  </div>
  <div class="topic-body">
    <h3>Why It Is Needed</h3>
    <ul>
      <li>Poor power quality causes equipment failure, overheating, and increased losses.</li>
      <li>Affects accuracy of energy consumption measurements.</li>
      <li>Identifies causes of high kVAR demand → penalties on electricity bills.</li>
      <li>Harmonic distortion increases transformer and motor losses.</li>
      <li>Voltage unbalance causes motor overheating and reduced lifespan.</li>
    </ul>
    <h3>Power Quality Parameters</h3>
    <div class="table-wrap">
      <table>
        <thead><tr><th>Parameter</th><th>Definition</th></tr></thead>
        <tbody>
          <tr><td><strong>Voltage Sag/Swell</strong></td><td>Temporary decrease/increase in RMS voltage lasting 0.5–30 cycles.</td></tr>
          <tr><td><strong>Harmonics (THD)</strong></td><td>Distortion of sinusoidal waveform by non-linear loads (VFDs, computers, UPS).</td></tr>
          <tr><td><strong>Power Factor</strong></td><td>Ratio of active power (kW) to apparent power (kVA). Low PF = poor power quality.</td></tr>
          <tr><td><strong>Flicker</strong></td><td>Rapid voltage fluctuations causing light flicker; common near arc furnaces, welding machines.</td></tr>
          <tr><td><strong>Voltage Unbalance</strong></td><td>Unequal magnitude among three phases; causes motor overheating and derating.</td></tr>
          <tr><td><strong>Transients / Spikes</strong></td><td>Short-duration high-voltage events from switching operations or lightning.</td></tr>
          <tr><td><strong>Frequency Deviation</strong></td><td>Deviation from 50 Hz; affects speed of synchronous and induction motors.</td></tr>
        </tbody>
      </table>
    </div>
    <h3>How It Is Carried Out</h3>
    <p>A <strong>Power Quality Analyser</strong> is connected at the main distribution board and records data over 24–48 hours to capture all operating conditions. Results are analysed and corrective measures (harmonic filters, capacitor banks, UPS) are recommended.</p>
    <div class="callout"><strong>Does it improve energy efficiency?</strong> Yes — correcting PF, reducing harmonics (lowers copper and iron losses in transformers/motors), and eliminating unnecessary reactive power all reduce energy waste.</div>
  </div>
</div>

<!-- 1.7 ECBC -->
<div class="topic">
  <div class="topic-head" onclick="toggle(this)">
    <span class="priority-tag red">High Priority</span>
    <span class="topic-num">1.7</span>
    <span class="topic-title">Energy Conservation Building Code (ECBC)</span>
    <span class="toggle-icon">+</span>
  </div>
  <div class="topic-body">
    <p>The ECBC is issued by the <strong>Bureau of Energy Efficiency (BEE)</strong> under the Energy Conservation Act 2001. It applies to new commercial buildings with connected load ≥ 500 kW or contract demand ≥ 600 kVA.</p>
    <h3>Key Aspects</h3>
    <ol>
      <li><strong>Building envelope</strong> — Wall, roof, and glazing U-values (insulation requirements) to reduce heat gain/loss.</li>
      <li><strong>Lighting</strong> — Maximum Lighting Power Density (LPD) in W/m² per space type; mandatory daylighting provisions.</li>
      <li><strong>HVAC</strong> — Minimum COP/EER standards for chillers and air conditioners.</li>
      <li><strong>Electrical systems</strong> — Power factor requirements, transformer efficiency standards.</li>
      <li><strong>Renewable energy</strong> — Encouragement of solar water heating and rooftop solar PV.</li>
    </ol>
    <div class="callout"><strong>ECBC Star Rating:</strong> Buildings can be rated from ECBC Compliant → ECBC+ → Super ECBC based on the percentage energy saved over a baseline reference building.</div>
  </div>
</div>

<!-- 1.8 BMS -->
<div class="topic">
  <div class="topic-head" onclick="toggle(this)">
    <span class="priority-tag yellow">Medium Priority</span>
    <span class="topic-num">1.8</span>
    <span class="topic-title">Building Management System (BMS)</span>
    <span class="toggle-icon">+</span>
  </div>
  <div class="topic-body">
    <p>A BMS is a <strong>computer-based control system</strong> that monitors and controls a building's mechanical, electrical, and environmental systems centrally.</p>
    <h3>Systems Controlled</h3>
    <ul>
      <li>HVAC (heating, ventilation, air conditioning)</li>
      <li>Lighting automation</li>
      <li>Fire and life safety</li>
      <li>Security and access control</li>
      <li>Energy metering and monitoring</li>
    </ul>
    <h3>How BMS Saves Energy</h3>
    <ol>
      <li><strong>Automatic scheduling</strong> — Turns off HVAC and lights when rooms are unoccupied.</li>
      <li><strong>Optimum start/stop</strong> — Calculates the latest possible start time to reach comfort conditions by occupancy time.</li>
      <li><strong>Demand control ventilation</strong> — Adjusts fresh air intake based on CO₂ sensors, avoiding overcooling/heating of unoccupied spaces.</li>
      <li><strong>Real-time monitoring and alerts</strong> — Dashboards with alarms for abnormal consumption spikes.</li>
      <li><strong>System coordination</strong> — Increases chiller setpoint when outdoor temperature is low; reduces simultaneous peak demand.</li>
    </ol>
  </div>
</div>


<!-- ══════════════════════════════════════════════
     MODULE 2
══════════════════════════════════════════════ -->
<div id="mod2" class="module-header" data-num="02">
  <div class="module-label">Module 2 · 9 Hours</div>
  <div class="module-title">Energy Efficiency in Electricity Utilization</div>
</div>

<!-- 2.1 Cascade -->
<div class="topic open">
  <div class="topic-head" onclick="toggle(this)">
    <span class="priority-tag red">High Priority</span>
    <span class="topic-num">2.1</span>
    <span class="topic-title">Cascade Efficiency in Electrical Systems</span>
    <span class="toggle-icon">+</span>
  </div>
  <div class="topic-body">
    <h3>Definition</h3>
    <p>Cascade efficiency is the <strong>overall efficiency of a multi-stage system</strong>, equal to the product of efficiencies of all individual stages:</p>
    <div class="formula">η_cascade = η₁ × η₂ × η₃ × ... × ηn</div>
    <h3>Typical Stages (Generation to Shaft)</h3>
    <div class="table-wrap">
      <table>
        <thead><tr><th>Stage</th><th>Typical Efficiency</th></tr></thead>
        <tbody>
          <tr><td>Thermal power generation</td><td>~35–38%</td></tr>
          <tr><td>Step-up transformer</td><td>~99%</td></tr>
          <tr><td>Transmission line</td><td>~97%</td></tr>
          <tr><td>Step-down transformer</td><td>~98.5%</td></tr>
          <tr><td>Distribution transformer</td><td>~97%</td></tr>
          <tr><td>Motor (end use)</td><td>~90%</td></tr>
          <tr><td><strong>Overall cascade efficiency</strong></td><td><strong>~28%</strong></td></tr>
        </tbody>
      </table>
    </div>
    <h3>How to Improve Cascade Efficiency</h3>
    <ol>
      <li>Use high-efficiency transformers (amorphous core or CRGO).</li>
      <li>Use energy-efficient motors (IE3/IE4 class).</li>
      <li>Maintain high power factor throughout the system to minimise I²R losses.</li>
      <li>Use Variable Frequency Drives (VFDs) for variable-load machines.</li>
      <li>Proper conductor sizing to reduce resistive losses.</li>
      <li>Replace aged, degraded equipment with modern high-efficiency equivalents.</li>
    </ol>
  </div>
</div>

<!-- 2.2 Lighting -->
<div class="topic">
  <div class="topic-head" onclick="toggle(this)">
    <span class="priority-tag red">High Priority</span>
    <span class="topic-num">2.2</span>
    <span class="topic-title">Energy Management in Lighting</span>
    <span class="toggle-icon">+</span>
  </div>
  <div class="topic-body">
    <h3>Efficacy Comparison</h3>
    <p><strong>Efficacy</strong> = Luminous flux (lumens) / Power input (watts)</p>
    <div class="table-wrap">
      <table>
        <thead><tr><th>Light Source</th><th>Efficacy (lm/W)</th><th>Life (hours)</th></tr></thead>
        <tbody>
          <tr><td>Incandescent lamp</td><td>8–15</td><td>1,000</td></tr>
          <tr><td>Fluorescent tube (T8)</td><td>60–80</td><td>10,000–15,000</td></tr>
          <tr><td>CFL</td><td>50–70</td><td>8,000–10,000</td></tr>
          <tr><td><strong>LED</strong></td><td><strong>80–150</strong></td><td><strong>25,000–50,000</strong></td></tr>
          <tr><td>Metal Halide</td><td>80–100</td><td>10,000–20,000</td></tr>
          <tr><td>High Pressure Sodium</td><td>80–150</td><td>12,000–24,000</td></tr>
        </tbody>
      </table>
    </div>
    <h3>Six Methods to Reduce Energy Consumption in Lighting</h3>
    <ol>
      <li><strong>Replace old lamps with LEDs</strong> — 5–10× higher efficacy than incandescent; 25,000–50,000 hr life.</li>
      <li><strong>Occupancy/motion sensors (PIR)</strong> — Automatically switch off lights when rooms are unoccupied.</li>
      <li><strong>Daylighting integration</strong> — Use skylights and automatic dimming controls to reduce artificial lighting during daytime hours.</li>
      <li><strong>Task lighting</strong> — Provide focused lighting only where needed instead of high-level uniform illumination throughout.</li>
      <li><strong>Electronic ballasts</strong> — Replace magnetic ballasts in fluorescent fittings (saves ~25% energy, eliminates flicker, improves PF).</li>
      <li><strong>Lighting automation / DALI / BMS</strong> — Centrally schedule and dim based on time, occupancy, and available daylight.</li>
      <li><strong>Delamping</strong> — Remove excess lamps in over-lit areas (check lux levels first).</li>
      <li><strong>Regular cleaning</strong> — Dirty fixtures lose 20–30% output; clean lamps and reflectors periodically.</li>
    </ol>
  </div>
</div>

<!-- 2.3 Motors -->
<div class="topic">
  <div class="topic-head" onclick="toggle(this)">
    <span class="priority-tag red">High Priority</span>
    <span class="topic-num">2.3</span>
    <span class="topic-title">Energy Management in Electric Motors</span>
    <span class="toggle-icon">+</span>
  </div>
  <div class="topic-body">
    <h3>Features of Energy Efficient Motors (EEM)</h3>
    <ol>
      <li>Reduced stator copper losses — larger conductor cross-section.</li>
      <li>Reduced rotor copper losses — more aluminium or copper in rotor bars.</li>
      <li>Reduced core (iron) losses — premium grade CRGO steel laminations with tighter tolerances.</li>
      <li>Reduced friction and windage losses — better bearings, optimised cooling fan design.</li>
      <li>Classified as IE2 (high), IE3 (premium), IE4 (super premium) per IEC 60034-30.</li>
    </ol>
    <h3>Types of Motor Losses</h3>
    <div class="table-wrap">
      <table>
        <thead><tr><th>Loss Type</th><th>Cause</th><th>Varies with load?</th></tr></thead>
        <tbody>
          <tr><td>Stator copper loss</td><td>I²R in stator windings</td><td>Yes (∝ I²)</td></tr>
          <tr><td>Rotor copper loss</td><td>I²R in rotor bars</td><td>Yes (∝ I²)</td></tr>
          <tr><td>Core (iron) loss</td><td>Hysteresis + eddy currents in stator</td><td>Nearly constant</td></tr>
          <tr><td>Friction & windage</td><td>Bearings and cooling fan</td><td>Nearly constant</td></tr>
          <tr><td>Stray load loss</td><td>Leakage flux and harmonics</td><td>Increases with load</td></tr>
        </tbody>
      </table>
    </div>
    <h3>Techniques to Improve Motor Energy Efficiency</h3>
    <ol>
      <li><strong>Replace with EEMs</strong> — IE3/IE4 motors have 2–5% higher efficiency than standard motors.</li>
      <li><strong>Load matching (right-sizing)</strong> — Motors below 50% load operate at poor efficiency and PF. Select motor so it runs at 75–100% of rated load.</li>
      <li><strong>Variable Frequency Drives (VFDs)</strong> — For fans and pumps: reducing speed by 20% reduces power by ~50% (affinity law: P ∝ N³).</li>
      <li><strong>Power factor correction</strong> — Install capacitors at motor terminals.</li>
      <li><strong>Quality rewinding</strong> — Poor rewinding loses 1–2% efficiency; replace with new EEM instead.</li>
      <li><strong>Regular maintenance</strong> — Lubrication, alignment checks, belt tension.</li>
      <li><strong>Avoid frequent starts</strong> — Use soft starters to reduce inrush current stress.</li>
      <li><strong>Shut down idling motors</strong> — An unloaded motor still consumes 25–35% of full-load power.</li>
    </ol>
  </div>
</div>

<!-- 2.4 Transformers -->
<div class="topic">
  <div class="topic-head" onclick="toggle(this)">
    <span class="priority-tag red">High Priority</span>
    <span class="topic-num">2.4</span>
    <span class="topic-title">Transformer Efficiency & Design Measures</span>
    <span class="toggle-icon">+</span>
  </div>
  <div class="topic-body">
    <h3>Types of Losses</h3>
    <div class="table-wrap">
      <table>
        <thead><tr><th>Loss</th><th>Also called</th><th>Description</th></tr></thead>
        <tbody>
          <tr><td><strong>Core loss</strong></td><td>Iron / No-load loss</td><td>Hysteresis + eddy current loss in the core. <em>Constant regardless of load.</em></td></tr>
          <tr><td><strong>Copper loss</strong></td><td>Winding / Load loss</td><td>I²R loss in windings. <em>Proportional to (load)².</em></td></tr>
        </tbody>
      </table>
    </div>
    <div class="formula">η = P_out / (P_out + P_core + P_copper) × 100%
Maximum efficiency occurs when: P_core = P_copper</div>
    <h3>Design Measures to Increase Efficiency</h3>
    <ol>
      <li><strong>Amorphous metal core</strong> — ~70% lower core loss than CRGO; ideal for distribution transformers.</li>
      <li><strong>CRGO (Cold Rolled Grain Oriented) silicon steel</strong> — Lower hysteresis loss than hot-rolled grain oriented steel.</li>
      <li><strong>Optimum flux density</strong> — Operate below magnetic saturation to minimise core loss.</li>
      <li><strong>Larger conductor cross-section</strong> — Directly reduces I²R copper loss.</li>
      <li><strong>Copper windings</strong> — Lower resistivity than aluminium → lower copper loss for same size.</li>
      <li><strong>Load balancing</strong> — Avoid running transformers at very low load (poor efficiency region); consolidate loads.</li>
      <li><strong>Total Owning Cost (TOC) procurement</strong> — Select transformers based on TOC = capital cost + capitalised losses, not purchase price alone.</li>
    </ol>
    <div class="callout"><strong>BEE Standards:</strong> Distribution transformers (≤200 kVA): minimum efficiency ~98.5–99%. Power transformers (>1 MVA): minimum ~99.3%. BEE "Star-1" and "Star-2" labels indicate higher efficiency bands.</div>
  </div>
</div>


<!-- ══════════════════════════════════════════════
     MODULE 3
══════════════════════════════════════════════ -->
<div id="mod3" class="module-header" data-num="03">
  <div class="module-label">Module 3 · 8 Hours</div>
  <div class="module-title">Demand Side Management & Ancillary Services</div>
</div>

<!-- 3.1 DSM -->
<div class="topic open">
  <div class="topic-head" onclick="toggle(this)">
    <span class="priority-tag red">High Priority</span>
    <span class="topic-num">3.1</span>
    <span class="topic-title">Demand Side Management — Introduction, Benefits & Techniques</span>
    <span class="toggle-icon">+</span>
  </div>
  <div class="topic-body">
    <h3>Introduction</h3>
    <p>DSM refers to <strong>activities that influence the amount and timing of electricity use</strong> by consumers, modifying the load curve to achieve efficiency, reliability, and environmental objectives. It is implemented by utilities, governments, and large consumers.</p>
    <h3>Benefits</h3>
    <ol>
      <li>Reduces peak demand → defers costly new generation capacity investment.</li>
      <li>Lowers electricity bills for consumers.</li>
      <li>Improves load factor of the utility.</li>
      <li>Reduces transmission and distribution losses.</li>
      <li>Reduces environmental impact (less fuel burned at peak).</li>
      <li>Enhances overall energy security.</li>
    </ol>
    <h3>Six Techniques of DSM</h3>
    <ol>
      <li><strong>Peak Clipping</strong> — Direct reduction of peak demand by utilities (e.g., remotely switching off water heaters, ACs during grid-stress periods).</li>
      <li><strong>Valley Filling</strong> — Adding load during off-peak periods (e.g., EV charging at night, water heating) to level the load curve and improve load factor.</li>
      <li><strong>Load Shifting</strong> — Moving loads from peak to off-peak hours without changing total consumption (e.g., batch industrial processes shifted to night shifts).</li>
      <li><strong>Strategic Conservation</strong> — Overall reduction in energy use through efficiency improvements, without shifting time of use (e.g., LED upgrades, EEM installation).</li>
      <li><strong>Strategic Load Growth</strong> — Increasing electricity sales in targeted segments (e.g., promoting heat pumps over gas-fired heaters).</li>
      <li><strong>Flexible Load Shape</strong> — Interruptible/curtailable service contracts; utility can curtail consumer load with prior agreement during emergencies.</li>
    </ol>
    <h3>DSM and Environment</h3>
    <ul>
      <li>Avoids construction of peaking power plants (often inefficient diesel/gas turbines).</li>
      <li>Reduces CO₂, NOx, and SOx emissions.</li>
      <li>Delays need for new transmission lines and substations.</li>
    </ul>
  </div>
</div>

<!-- 3.2 Peak Demand -->
<div class="topic">
  <div class="topic-head" onclick="toggle(this)">
    <span class="priority-tag red">High Priority</span>
    <span class="topic-num">3.2</span>
    <span class="topic-title">Peak Demand Control — Importance & Methods</span>
    <span class="toggle-icon">+</span>
  </div>
  <div class="topic-body">
    <h3>Importance</h3>
    <ul>
      <li>Peak demand charges (Rs/kVA) form a major portion of industrial electricity bills.</li>
      <li>Utilities size their infrastructure (transformers, cables, switchgear) for peak demand.</li>
      <li>Reducing peak demand directly reduces the maximum demand charge and infrastructure investment.</li>
    </ul>
    <h3>Peak Demand Control Methods</h3>
    <ol>
      <li><strong>Load Curve Generation</strong> — Plot daily load curve (kVA vs time). Identify the peak window. All strategies target this window.
        <ul><li>If plotted for 24 hours → daily load curve. Over a month → monthly load curve.</li></ul>
      </li>
      <li><strong>Rescheduling of Loads</strong> — Shift energy-intensive processes/equipment to off-peak hours. Prepare operation flow charts to identify rescheduling opportunities. Improves load factor.</li>
      <li><strong>Storage of Products / Process Utilities</strong> — Build inventory or store process outputs during off-peak hours to reduce peak demand.
        <ul><li><em>Example:</em> Ice bank system in dairy — make ice at night (cheap off-peak power), use ice for cooling during day peak.</li></ul>
      </li>
      <li><strong>Shedding of Non-Essential Loads</strong> — Install a demand controller that sheds non-critical loads (non-critical lighting, water heaters, non-critical ACs) when demand approaches the preset limit. Sophisticated microprocessor systems can: predict demand, give audio/visual alarm, auto-shed and auto-restore loads in a predetermined sequence.</li>
      <li><strong>Operation of DG Sets</strong> — Connect diesel generators during peak periods to supplement grid supply, reducing kVA drawn from utility and minimising maximum demand charges.</li>
      <li><strong>Reactive Power Compensation</strong> — Install capacitor banks / APFC panels to maintain optimum power factor. Higher PF → lower kVA for same kW → lower maximum demand charge.</li>
    </ol>
  </div>
</div>

<!-- 3.3 PF Improvement -->
<div class="topic">
  <div class="topic-head" onclick="toggle(this)">
    <span class="priority-tag red">High Priority</span>
    <span class="topic-num">3.3</span>
    <span class="topic-title">Power Factor Improvement — Theory & Numericals</span>
    <span class="toggle-icon">+</span>
  </div>
  <div class="topic-body">
    <h3>Benefits of Power Factor Improvement</h3>
    <ol>
      <li>Reduction in kVA demand → lower maximum demand charges.</li>
      <li>Reduction in I²R losses in cables (lower current for same kW).</li>
      <li>Reduction in voltage drop across distribution cables.</li>
      <li>Increased kW capacity of existing cables and transformers.</li>
      <li>Reduction in electricity bill (industrial tariffs penalise low PF).</li>
    </ol>
    <h3>Methods to Improve Power Factor</h3>
    <ul>
      <li>Shunt capacitor banks (most common — supplies leading reactive power)</li>
      <li>Synchronous condensers (rotating reactive power compensator)</li>
      <li>Static VAR compensators (SVC)</li>
      <li>Avoid running motors on no-load or light load</li>
      <li>Use of high-PF motors and lighting equipment</li>
    </ul>
    <h3>Key Formulas</h3>
    <div class="formula">Leading kVAR required = kW × (tan φ₁ − tan φ₂)

Most economical PF:    sin φ_opt = C_c / T
where C_c = annual cost per kVAR of capacitor, T = tariff in Rs per kVA per annum</div>

    <div class="numerical">
      <div class="num-label">🔢 Solved Numerical — 800 kW, PF 0.8 → 0.9 (from PYQ Oct 2023 &amp; Apr 2025)</div>
      <p><strong>Given:</strong> P = 800 kW, cos φ₁ = 0.8 lag → cos φ₂ = 0.9 lag | 3000 hr/year | Tariff: Rs 100/kVA + 20 paise/kWh | Capacitor: Rs 60/kVAR, 10% interest &amp; depreciation</p>
      <ol>
        <li>Initial kVA = 800/0.8 = <strong>1000 kVA</strong></li>
        <li>New kVA = 800/0.9 = <strong>888.9 kVA</strong></li>
        <li>Reduction in kVA = 111.1 kVA → Annual saving on kVA charge = 111.1 × 100 = <strong>Rs 11,111</strong></li>
        <li>φ₁ = cos⁻¹(0.8) = 36.87° → tan φ₁ = 0.75 | φ₂ = cos⁻¹(0.9) = 25.84° → tan φ₂ = 0.484</li>
        <li>kVAR required = 800 × (0.75 − 0.484) = 800 × 0.266 = <strong>212.7 kVAR</strong></li>
        <li>Annual cost of capacitors = 212.7 × 60 × 0.10 = <strong>Rs 1,276</strong></li>
        <li><strong>Net annual saving = 11,111 − 1,276 = Rs 9,835</strong></li>
      </ol>
    </div>

    <div class="numerical">
      <div class="num-label">🔢 Solved Numerical — Most Economical PF (from PYQ May 2024)</div>
      <p><strong>Given:</strong> Load = 900 kW at 0.65 pf lag | Tariff: Rs 1000/kVA/year + 80 paise/kWh | Capacitor cost: Rs 2000/kVAR | Annual interest &amp; depreciation: 15%</p>
      <ol>
        <li>C_c = Rs 2000 × 0.15 = Rs 300 per kVAR per annum</li>
        <li>T = Rs 1000 per kVA per annum</li>
        <li>sin φ_opt = C_c / T = 300 / 1000 = 0.3</li>
        <li><strong>cos φ_opt = √(1 − 0.09) = √0.91 = 0.954</strong></li>
        <li>φ₁ = cos⁻¹(0.65) = 49.46° → tan φ₁ = 1.169 | φ_opt: sin = 0.3, tan = 0.3/0.954 = 0.314</li>
        <li>kVAR = 900 × (1.169 − 0.314) = 900 × 0.855 = <strong>769.5 kVAR</strong></li>
      </ol>
    </div>
  </div>
</div>

<!-- 3.4 ToD -->
<div class="topic">
  <div class="topic-head" onclick="toggle(this)">
    <span class="priority-tag yellow">Medium Priority</span>
    <span class="topic-num">3.4</span>
    <span class="topic-title">Time-of-Day Pricing</span>
    <span class="toggle-icon">+</span>
  </div>
  <div class="topic-body">
    <p><strong>Time-of-Day (ToD) pricing</strong> is an electricity tariff where the <strong>price per kWh varies by time of day</strong>:</p>
    <ul>
      <li><strong>Peak hours</strong> (e.g., 6 PM–10 PM): Higher rate.</li>
      <li><strong>Off-peak hours</strong> (e.g., 10 PM–6 AM): Lower rate.</li>
      <li><strong>Shoulder hours</strong>: Intermediate rate.</li>
    </ul>
    <h3>Purpose</h3>
    <ul>
      <li>Incentivises consumers to shift loads away from peak hours.</li>
      <li>Signals the true (marginal) cost of electricity at different times.</li>
      <li>Reduces peak demand on the grid without utility-side curtailment.</li>
    </ul>
    <h3>Multi-utility Power Exchange Model</h3>
    <p>Multiple utilities share generation resources — when utility A has a demand valley, it sells cheap power to utility B which is at peak, and vice versa. This reduces the need for each utility to maintain large standby peaking plants.</p>
  </div>
</div>

<!-- 3.5 Ancillary -->
<div class="topic">
  <div class="topic-head" onclick="toggle(this)">
    <span class="priority-tag red">High Priority</span>
    <span class="topic-num">3.5</span>
    <span class="topic-title">Ancillary Services</span>
    <span class="toggle-icon">+</span>
  </div>
  <div class="topic-body">
    <h3>Definition</h3>
    <p>Ancillary services are <strong>support services provided to a power system</strong> to maintain reliability, security, and power quality of the grid, beyond the main energy supply function.</p>
    <h3>Types of Ancillary Services</h3>
    <ol>
      <li><strong>Frequency Regulation (Regulation Service)</strong> — Maintains grid frequency at 50 Hz. Fast-responding generators that ramp up/down via Automatic Generation Control (AGC) signals.</li>
      <li><strong>Load Following</strong> — Handles slower changes in load over minutes to hours; slower than frequency regulation but manages larger deviations.</li>
      <li><strong>Spinning Reserve</strong> — Generation capacity already synchronised to grid but operating below full output. Can ramp up within 10 minutes to replace a tripped generator.</li>
      <li><strong>Non-Spinning (Supplemental) Reserve</strong> — Generation capacity not currently online but can be started and synchronised within 10–30 minutes.</li>
      <li><strong>Reactive Power / Voltage Support</strong> — Generators, capacitor banks, and STATCOMs that supply/absorb reactive power to maintain voltage profile across the grid.</li>
      <li><strong>Black Start Capability</strong> — Ability of a generator to start without external power supply; used to restore the grid after a blackout.</li>
      <li><strong>Energy Imbalance Service</strong> — Corrects real-time imbalances between scheduled and actual generation/load.</li>
    </ol>
  </div>
</div>


<!-- ══════════════════════════════════════════════
     MODULE 4
══════════════════════════════════════════════ -->
<div id="mod4" class="module-header" data-num="04">
  <div class="module-label">Module 4 · 6 Hours</div>
  <div class="module-title">Energy Management in Industries &amp; Commercial Establishments</div>
</div>

<!-- 4.1 Boiler -->
<div class="topic open">
  <div class="topic-head" onclick="toggle(this)">
    <span class="priority-tag red">High Priority</span>
    <span class="topic-num">4.1</span>
    <span class="topic-title">Energy Conservation in Boilers &amp; Boiler Blowdown</span>
    <span class="toggle-icon">+</span>
  </div>
  <div class="topic-body">
    <h3>Energy Conservation Opportunities</h3>
    <ol>
      <li><strong>Flue gas heat recovery</strong> — Fit an <em>economiser</em> (preheats feedwater) or <em>air preheater</em> (preheats combustion air). Every 6°C drop in flue gas temperature ≈ 1% efficiency improvement.</li>
      <li><strong>Excess air control</strong> — Minimise excess air while maintaining complete combustion. Every 1% reduction in excess air ≈ 0.6% efficiency gain. Use O₂ analyser for automated control.</li>
      <li><strong>Insulation of steam lines and boiler surfaces</strong> — Reduces radiation and convection losses from hot surfaces.</li>
      <li><strong>Feedwater treatment</strong> — Prevents scale formation. 1 mm of scale on heat transfer surface increases fuel consumption by ~2%.</li>
      <li><strong>Steam trap maintenance</strong> — Faulty open traps waste live steam. Regular testing and replacement saves 10–15% of steam generation cost.</li>
      <li><strong>Automatic combustion control</strong> — Optimises fuel/air ratio automatically based on load conditions.</li>
      <li><strong>Reduce steam operating pressure</strong> — Operate at minimum required pressure; lower pressure = less distribution heat loss.</li>
      <li><strong>Flash steam recovery</strong> — Use flash vessels to recover low-pressure steam from condensate, replacing steam from boiler.</li>
    </ol>
    <h3>Boiler Blowdown</h3>
    <p><strong>Need:</strong> Dissolved solids in feedwater concentrate during boiling. If not removed, they cause scale formation and foaming (carryover into steam). Blowdown maintains TDS within permissible limits.</p>
    <p><strong>Two sources of feedwater:</strong> (1) Make-up water from external source, (2) Returned condensate.</p>
    <h4>Types of Blowdown</h4>
    <ol>
      <li><strong>Bottom blowdown (intermittent)</strong> — Opens drain at the bottom to remove sludge and suspended solids. Done periodically (daily).</li>
      <li><strong>Surface / Continuous blowdown</strong> — Removes concentrated water from the surface level continuously; controls dissolved solids (TDS). The blowndown water is sent to a heat recovery system (flash vessel + heat exchanger) to preheat make-up water.</li>
    </ol>
  </div>
</div>

<!-- 4.2 Steam -->
<div class="topic">
  <div class="topic-head" onclick="toggle(this)">
    <span class="priority-tag red">High Priority</span>
    <span class="topic-num">4.2</span>
    <span class="topic-title">Energy Savings in Steam Distribution</span>
    <span class="toggle-icon">+</span>
  </div>
  <div class="topic-body">
    <ol>
      <li><strong>Steam trap maintenance and replacement</strong> — Failed-open traps vent live steam continuously; failed-closed traps cause waterlogging. Survey all traps quarterly using acoustic detectors or temperature methods.</li>
      <li><strong>Proper pipe insulation</strong> — Reduces heat loss from pipe surfaces. Use mineral wool or calcium silicate insulation; repair damaged sections promptly.</li>
      <li><strong>Eliminate steam leaks</strong> — A 3 mm hole at 7 bar pressure wastes ~30 kg/hr of steam. Find leaks using ultrasonic detectors and repair flanges, valve glands, and flanged joints.</li>
      <li><strong>Condensate recovery and return</strong> — Condensate is hot, treated water with valuable heat content. Returning it to the boiler reduces make-up water, fuel consumption, and chemical treatment costs.</li>
      <li><strong>Flash steam utilisation</strong> — When high-pressure condensate passes through a trap/PRV, flash steam forms; use it in low-pressure applications rather than venting to atmosphere.</li>
      <li><strong>Correct pipe sizing</strong> — Oversized pipes have larger surface area → more heat loss. Undersized pipes cause excessive pressure drop and wet steam.</li>
      <li><strong>Pressure reduction</strong> — Supply each process at only the minimum required pressure using Pressure Reducing Valves (PRVs).</li>
    </ol>
  </div>
</div>

<!-- 4.3 Furnace -->
<div class="topic">
  <div class="topic-head" onclick="toggle(this)">
    <span class="priority-tag red">High Priority</span>
    <span class="topic-num">4.3</span>
    <span class="topic-title">Energy Conservation in Furnaces</span>
    <span class="toggle-icon">+</span>
  </div>
  <div class="topic-body">
    <ol>
      <li><strong>Recuperators and regenerators</strong> — Preheat combustion air using flue gases. Preheating air by 100°C saves ~5–6% fuel. Regenerative burners recover 60–70% of flue gas heat.</li>
      <li><strong>Optimise excess air</strong> — Monitor using O₂/CO analysers; minimise excess air to just above stoichiometric for complete combustion.</li>
      <li><strong>Proper furnace insulation</strong> — Use ceramic fibre lining for batch/intermittent furnaces (faster heat-up, lower heat storage). Repair cracks, holes, and damaged refractory.</li>
      <li><strong>Minimise furnace door openings</strong> — Each opening causes significant heat loss (radiation + convection). Reduce frequency and duration.</li>
      <li><strong>Automatic temperature control</strong> — Use thermocouple-based PID controllers; avoid temperature overshoot.</li>
      <li><strong>Maximise furnace loading</strong> — Run with maximum charge per batch to improve specific energy consumption (energy per tonne of product).</li>
      <li><strong>Waste heat recovery from flue gases</strong> — Use waste heat chambers to preheat billets, ingots, or raw material entering the furnace.</li>
      <li><strong>Furnace pressure control</strong> — Maintain slight positive pressure inside to prevent cold air infiltration.</li>
    </ol>
  </div>
</div>

<!-- 4.4 Cogeneration -->
<div class="topic">
  <div class="topic-head" onclick="toggle(this)">
    <span class="priority-tag red">High Priority</span>
    <span class="topic-num">4.4</span>
    <span class="topic-title">Cogeneration — Types &amp; Schemes</span>
    <span class="toggle-icon">+</span>
  </div>
  <div class="topic-body">
    <h3>Definition</h3>
    <p>Cogeneration (Combined Heat and Power — CHP) is the <strong>simultaneous generation of electrical (or mechanical) energy and useful heat from a single fuel source</strong>. Overall fuel utilisation reaches 70–90%, vs ~35% for conventional power plants.</p>
    <h3>Advantages</h3>
    <ul>
      <li>Higher overall fuel efficiency</li>
      <li>Significantly reduced energy costs</li>
      <li>Reduced greenhouse gas emissions</li>
      <li>On-site generation → less grid dependence and better reliability</li>
    </ul>
    <h3>Types of Cogeneration Systems</h3>
    <h4>1. Topping Cycle (most common)</h4>
    <p>Fuel → electricity first → waste heat used for process.</p>
    <ul>
      <li><strong>Gas turbine topping:</strong> Gas turbine drives generator; hot exhaust gas (500–550°C) enters HRSG (Heat Recovery Steam Generator) to produce process steam.</li>
      <li><strong>Steam turbine topping:</strong> High-pressure steam drives turbine for electricity; extracted/exhaust steam used for process heating.</li>
      <li><strong>Reciprocating engine topping:</strong> IC engine drives generator; jacket cooling water + exhaust gas heat recovered for process use.</li>
    </ul>
    <h4>2. Bottoming Cycle</h4>
    <p>Fuel → high-temperature industrial process first → waste heat from process generates electricity. Less common; used in cement, glass, and steel industries.</p>
    <h4>3. Combined Cycle Power Generation</h4>
    <p>Gas turbine generates electricity → exhaust gas into HRSG → steam turbine generates additional electricity. Overall efficiency ~55–60%. Used in large power plants.</p>
  </div>
</div>

<!-- 4.5 HVAC -->
<div class="topic">
  <div class="topic-head" onclick="toggle(this)">
    <span class="priority-tag yellow">Medium Priority</span>
    <span class="topic-num">4.5</span>
    <span class="topic-title">HVAC — COP &amp; Energy Saving Opportunities</span>
    <span class="toggle-icon">+</span>
  </div>
  <div class="topic-body">
    <div class="formula">COP (Refrigerator) = Refrigerating effect (kW) / Work input (kW) = Q_L / W
COP (Heat Pump) = Q_H / W = COP_refrigerator + 1

Note: COP ≠ Efficiency (COP can exceed 1; efficiency cannot)
Capacity measured in Ton of Refrigeration (TR): 1 TR = 3.517 kW</div>
    <h3>Energy Saving Opportunities in HVAC</h3>
    <ol>
      <li><strong>Variable speed drives on pumps and fans</strong> — Reduce speed during part-load; power savings are cubic with speed reduction.</li>
      <li><strong>Raise chiller setpoint temperature</strong> — Every 1°C rise in chilled water supply temperature improves COP by ~2–3%.</li>
      <li><strong>Cooling tower optimisation</strong> — Lower condenser water temperature → lower condenser pressure → higher COP.</li>
      <li><strong>Clean heat exchangers regularly</strong> — Scale/fouling on condenser or evaporator degrades heat transfer and efficiency.</li>
      <li><strong>Building envelope improvement</strong> — Better insulation, double-glazed windows reduce cooling load significantly.</li>
      <li><strong>Night setback</strong> — Raise thermostat setpoint when building is unoccupied at night.</li>
      <li><strong>Free cooling (economiser mode)</strong> — Use cool outdoor air directly when ambient conditions allow.</li>
      <li><strong>Energy recovery from exhaust air</strong> — Use heat exchangers to pre-condition incoming fresh air using outgoing exhaust air.</li>
    </ol>
  </div>
</div>

<!-- 4.6 WHR -->
<div class="topic">
  <div class="topic-head" onclick="toggle(this)">
    <span class="priority-tag yellow">Medium Priority</span>
    <span class="topic-num">4.6</span>
    <span class="topic-title">Waste Heat Recovery Systems</span>
    <span class="toggle-icon">+</span>
  </div>
  <div class="topic-body">
    <h3>Types</h3>
    <h4>1. Recuperator</h4>
    <p>A direct heat exchanger between hot flue gas and incoming cold air/fluid. Countercurrent flow gives best efficiency. Simple, low maintenance. Application: preheat combustion air in furnaces and boilers.</p>
    <h4>2. Regenerator</h4>
    <p>Uses a <strong>heat storage matrix</strong> (ceramic or metallic checkerwork) that absorbs heat from hot gas and releases it to cold incoming gas alternately, switching between two chambers. Recovers 60–70% of waste heat. Application: glass melting furnaces.</p>
    <h4>3. Heat Pipe Heat Exchanger</h4>
    <p>Sealed pipes containing a working fluid that evaporates at the hot end and condenses at the cold end — passive heat transfer with no moving parts, high reliability. Application: air-to-air heat recovery in HVAC.</p>
    <h4>4. Waste Heat Boiler (HRSG)</h4>
    <p>Hot flue gases pass through a boiler to generate steam or hot water. Application: after gas turbines, cement kilns, glass furnaces. Enables cogeneration or combined-cycle generation.</p>
    <h3>Energy Saving Opportunities</h3>
    <ul>
      <li>Preheat combustion air (saves 20–30% fuel in furnaces)</li>
      <li>Preheat feed/charge materials</li>
      <li>Generate steam for process use or for additional electricity generation</li>
      <li>Building space heating and hot water production</li>
    </ul>
  </div>
</div>


<!-- ══════════════════════════════════════════════
     MODULE 5
══════════════════════════════════════════════ -->
<div id="mod5" class="module-header" data-num="05">
  <div class="module-label">Module 5 · 6 Hours</div>
  <div class="module-title">Energy Economics</div>
</div>

<!-- 5.1 Payback -->
<div class="topic open">
  <div class="topic-head" onclick="toggle(this)">
    <span class="priority-tag red">High Priority</span>
    <span class="topic-num">5.1</span>
    <span class="topic-title">Simple Payback Period</span>
    <span class="toggle-icon">+</span>
  </div>
  <div class="topic-body">
    <div class="formula">Payback Period (years) = Capital Investment (Rs) / Net Annual Savings (Rs/year)

Net Annual Savings = Annual Energy Savings − Annual O&M Costs</div>
    <h3>Advantages</h3>
    <ul><li>Simple to calculate and understand.</li><li>Quick first filter for viability comparison.</li></ul>
    <h3>Disadvantages</h3>
    <ul>
      <li>Ignores time value of money.</li>
      <li>Ignores cash flows after the payback period ends.</li>
      <li>Does not account for project life or salvage value.</li>
      <li>Not suitable for comparing projects with very different lives.</li>
    </ul>
    <div class="numerical">
      <div class="num-label">🔢 Solved Numerical (from PYQ June 2023)</div>
      <p>Annual energy saving = Rs 4,86,000 | Annual O&M = Rs 42,000 | Capital cost = Rs 22,20,000</p>
      <ol>
        <li>Net annual saving = 4,86,000 − 42,000 = <strong>Rs 4,44,000</strong></li>
        <li><strong>Payback period = 22,20,000 / 4,44,000 = 5 years</strong></li>
      </ol>
    </div>
  </div>
</div>

<!-- 5.2 NPV -->
<div class="topic">
  <div class="topic-head" onclick="toggle(this)">
    <span class="priority-tag red">High Priority</span>
    <span class="topic-num">5.2</span>
    <span class="topic-title">Net Present Value (NPV) Method</span>
    <span class="toggle-icon">+</span>
  </div>
  <div class="topic-body">
    <h3>Time Value of Money</h3>
    <p>Money available today is worth more than the same amount in the future due to its earning potential.</p>
    <div class="formula">PV of future cash flow = F / (1+i)ⁿ

NPV = Σ [Sₙ / (1+i)ⁿ] − C₀

Where: Sₙ = saving in year n, i = discount rate, C₀ = initial investment, N = project life</div>
    <p><strong>Decision rule:</strong> NPV > 0 → project is viable. Higher NPV = better project when comparing alternatives.</p>
    <h3>Advantages</h3>
    <ul><li>Accounts for time value of money.</li><li>Considers all cash flows over the entire project life.</li><li>Gives absolute value of wealth creation.</li></ul>
    <h3>Disadvantages</h3>
    <ul><li>Requires estimation of discount rate (subjective).</li><li>Difficult to compare projects of very different sizes.</li></ul>

    <div class="numerical">
      <div class="num-label">🔢 Solved Numerical — 5-Year Project (from PYQ — all papers)</div>
      <p>Investment = Rs 10,00,000 | Discount rate = 10% | Cash flows: Y1=2L, Y2=2L, Y3=3L, Y4=3L, Y5=3.5L</p>
      <div class="table-wrap">
        <table>
          <thead><tr><th>Year</th><th>Cash Flow (Rs)</th><th>PV Factor (10%)</th><th>Present Value (Rs)</th></tr></thead>
          <tbody>
            <tr><td>1</td><td>2,00,000</td><td>0.909</td><td>1,81,800</td></tr>
            <tr><td>2</td><td>2,00,000</td><td>0.826</td><td>1,65,200</td></tr>
            <tr><td>3</td><td>3,00,000</td><td>0.751</td><td>2,25,300</td></tr>
            <tr><td>4</td><td>3,00,000</td><td>0.683</td><td>2,04,900</td></tr>
            <tr><td>5</td><td>3,50,000</td><td>0.621</td><td>2,17,350</td></tr>
            <tr><td><strong>Total PV</strong></td><td></td><td></td><td><strong>9,94,550</strong></td></tr>
          </tbody>
        </table>
      </div>
      <p><strong>NPV = 9,94,550 − 10,00,000 = −Rs 5,450</strong> (marginally not viable at 10%)</p>
    </div>

    <div class="numerical">
      <div class="num-label">🔢 Solved Numerical — LED Investment (from PYQ Jan 2024)</div>
      <p>Investment = Rs 400 | Discount rate = 8% | Year 1 saving = Rs 800, Year 2 saving = Rs 600</p>
      <ol>
        <li>PV of Y1 = 800 / 1.08 = Rs 740.7</li>
        <li>PV of Y2 = 600 / 1.08² = 600 / 1.1664 = Rs 514.4</li>
        <li>Total PV = 740.7 + 514.4 = Rs 1255.1</li>
        <li><strong>NPV = 1255.1 − 400 = Rs 855.1 (positive → project is viable)</strong></li>
      </ol>
    </div>
  </div>
</div>

<!-- 5.3 LCC -->
<div class="topic">
  <div class="topic-head" onclick="toggle(this)">
    <span class="priority-tag red">High Priority</span>
    <span class="topic-num">5.3</span>
    <span class="topic-title">Life Cycle Costing (LCC) Approach</span>
    <span class="toggle-icon">+</span>
  </div>
  <div class="topic-body">
    <h3>Definition</h3>
    <p>LCC evaluates the <strong>total cost of ownership</strong> of a project over its entire useful life, including initial cost, operating costs, maintenance costs, and salvage value — all discounted to present value.</p>
    <div class="formula">LCC = C₀ + Σ [C_op,n / (1+i)ⁿ] − [S_N / (1+i)^N]

Where: C₀ = capital cost, C_op = annual operating cost, S_N = salvage value, N = life</div>
    <h3>Steps in LCC for Energy Project Selection</h3>
    <ol>
      <li><strong>Define alternatives</strong> — Identify all competing options (e.g., keep old motor vs buy EEM).</li>
      <li><strong>Determine analysis period</strong> — Usually the expected life of the equipment.</li>
      <li><strong>Estimate all cost elements:</strong>
        <ul>
          <li>Initial capital cost (purchase + installation)</li>
          <li>Annual energy cost = energy consumed × unit price</li>
          <li>Annual maintenance cost</li>
          <li>Salvage value at end of life</li>
        </ul>
      </li>
      <li><strong>Select discount rate</strong> — Based on cost of capital or minimum acceptable rate of return (MARR).</li>
      <li><strong>Calculate present worth</strong> of all future costs and savings using PV factors.</li>
      <li><strong>Calculate total LCC</strong> for each alternative.</li>
      <li><strong>Select alternative with lowest LCC.</strong></li>
    </ol>
    <h3>Advantages</h3>
    <ul>
      <li>Considers total cost over life, not just first cost.</li>
      <li>Accounts for time value of money.</li>
      <li>Enables fair comparison between energy-efficient (high first cost, low running cost) and conventional equipment.</li>
      <li>Justifies premium-priced energy-efficient products on a whole-life basis.</li>
    </ul>
  </div>
</div>

<!-- 5.4 IRR -->
<div class="topic">
  <div class="topic-head" onclick="toggle(this)">
    <span class="priority-tag red">High Priority</span>
    <span class="topic-num">5.4</span>
    <span class="topic-title">Internal Rate of Return (IRR)</span>
    <span class="toggle-icon">+</span>
  </div>
  <div class="topic-body">
    <h3>Definition</h3>
    <p>IRR is the <strong>discount rate at which NPV = 0</strong>. It represents the actual rate of return earned by the project.</p>
    <div class="formula">0 = Σ [Sₙ / (1+IRR)ⁿ] − C₀

Decision: If IRR > MARR → Accept | If IRR < MARR → Reject

Interpolation formula:
IRR = i₁ + [NPV₁ / (NPV₁ − NPV₂)] × (i₂ − i₁)</div>
    <div class="numerical">
      <div class="num-label">🔢 Solved Numerical (from PYQ Oct 2023)</div>
      <p>Cost = Rs 5,00,000 | Life = 10 years | Annual saving = Rs 1,50,000</p>
      <ol>
        <li>Try i = 27%: Annuity factor (27%, 10yr) ≈ 3.33 | PV = 1,50,000 × 3.33 = Rs 4,99,500 ≈ Rs 5,00,000</li>
        <li><strong>IRR ≈ 27%</strong></li>
        <li>If MARR = 20%, then IRR (27%) > MARR → <strong>Project is acceptable</strong></li>
      </ol>
    </div>
  </div>
</div>

<!-- 5.5 ARR -->
<div class="topic">
  <div class="topic-head" onclick="toggle(this)">
    <span class="priority-tag yellow">Medium Priority</span>
    <span class="topic-num">5.5</span>
    <span class="topic-title">Average Rate of Return (ARR)</span>
    <span class="toggle-icon">+</span>
  </div>
  <div class="topic-body">
    <div class="formula">ARR = (Average annual net savings / Average investment) × 100%

Average investment = (Initial investment + Salvage value) / 2</div>
    <p><strong>Advantage:</strong> Simple, easy to compare with target rate of return.</p>
    <p><strong>Disadvantage:</strong> Ignores time value of money; uses accounting figures rather than actual cash flows.</p>
    <div class="numerical">
      <div class="num-label">🔢 Solved Numerical (from PYQ April 2025)</div>
      <p>Initial investment = Rs 1,00,000 | Life = 5 years | Salvage = Rs 25,000 | Net inflows: Y1=20k, Y2=20k, Y3=10k, Y4=10k, Y5=30k</p>
      <ol>
        <li>Total inflows = 20,000+20,000+10,000+10,000+30,000 = Rs 90,000</li>
        <li>Average annual saving = 90,000 / 5 = <strong>Rs 18,000</strong></li>
        <li>Average investment = (1,00,000 + 25,000) / 2 = <strong>Rs 62,500</strong></li>
        <li><strong>ARR = (18,000 / 62,500) × 100 = 28.8%</strong></li>
      </ol>
    </div>
  </div>
</div>

<!-- 5.6 EEM Payback -->
<div class="topic">
  <div class="topic-head" onclick="toggle(this)">
    <span class="priority-tag red">High Priority</span>
    <span class="topic-num">5.6</span>
    <span class="topic-title">EEM Payback Period — Solved Numericals</span>
    <span class="toggle-icon">+</span>
  </div>
  <div class="topic-body">
    <div class="formula">Power input (kW) = Motor rating × % load / (100 × η)
Annual energy (kWh) = Power input × Operating hours
Annual saving (Rs) = (Energy_old − Energy_new) × Cost per kWh
Payback period (years) = Capital investment / Annual saving</div>

    <div class="numerical">
      <div class="num-label">🔢 Solved — 11 kW Motor (from PYQ Oct 2023)</div>
      <p>Rating = 11 kW | Loading = 70% | η_old = 81% | η_new = 84.7% | Investment = Rs 40,000 | Energy cost = Rs 5/kWh | Hours = 8000/year</p>
      <ol>
        <li>Load = 11 × 0.70 = 7.7 kW</li>
        <li>Input power (old) = 7.7 / 0.81 = 9.506 kW</li>
        <li>Input power (new) = 7.7 / 0.847 = 9.091 kW</li>
        <li>Power saving = 9.506 − 9.091 = 0.415 kW</li>
        <li>Annual energy saving = 0.415 × 8000 = 3320 kWh</li>
        <li>Annual cost saving = 3320 × 5 = <strong>Rs 16,600</strong></li>
        <li><strong>Payback = 40,000 / 16,600 = 2.41 years</strong></li>
      </ol>
    </div>

    <div class="numerical">
      <div class="num-label">🔢 Solved — 10 kW Motor (from PYQ Jan 2024)</div>
      <p>Rating = 10 kW | Loading = 75% | η_old = 81% | η_new = 85% | Investment = Rs 35,000 | Energy cost = Rs 5/kWh | Hours = 5000/year</p>
      <ol>
        <li>Load = 10 × 0.75 = 7.5 kW</li>
        <li>Input power (old) = 7.5 / 0.81 = 9.259 kW</li>
        <li>Input power (new) = 7.5 / 0.85 = 8.824 kW</li>
        <li>Power saving = 9.259 − 8.824 = 0.435 kW</li>
        <li>Annual energy saving = 0.435 × 5000 = 2177 kWh</li>
        <li>Annual cost saving = 2177 × 5 = <strong>Rs 10,885</strong></li>
        <li><strong>Payback = 35,000 / 10,885 = 3.22 years</strong></li>
      </ol>
    </div>
  </div>
</div>

<!-- 5.7 EMS -->
<div class="topic">
  <div class="topic-head" onclick="toggle(this)">
    <span class="priority-tag yellow">Medium Priority</span>
    <span class="topic-num">5.7</span>
    <span class="topic-title">Computer Aided Energy Management System (EMS)</span>
    <span class="toggle-icon">+</span>
  </div>
  <div class="topic-body">
    <p>A Computer Aided EMS is a <strong>software platform that monitors, controls, and optimises energy use</strong> in a facility in real time via sensors and communication networks.</p>
    <h3>Key Functions</h3>
    <ol>
      <li><strong>Real-time monitoring</strong> — Continuously monitors energy consumption of all major loads.</li>
      <li><strong>Data logging and trending</strong> — Records historical data for analysis, benchmarking, and reporting.</li>
      <li><strong>Alarm management</strong> — Alerts operators when consumption exceeds preset limits.</li>
      <li><strong>Peak demand control</strong> — Automatically sheds non-critical loads when maximum demand approaches the billing limit.</li>
      <li><strong>Load scheduling</strong> — Staggers equipment startups to avoid simultaneous high-demand spikes.</li>
      <li><strong>Report generation</strong> — Daily, monthly, and annual KPI reports; cost allocation per department.</li>
      <li><strong>Predictive analytics</strong> — Uses historical data to forecast energy demand and flag anomalies before they become costly.</li>
    </ol>
    <div class="callout"><strong>"EMS and SCADA used together":</strong> EMS handles energy optimisation while SCADA manages process control. Integration allows energy-aware process control — a SCADA process alarm automatically triggers EMS to recalculate energy requirements, enabling tighter control and faster, more efficient response.</div>
  </div>
</div>


<!-- ══════════════════════════════════════════════
     PRIORITY MATRIX
══════════════════════════════════════════════ -->
<div id="matrix" class="module-header" data-num="★" style="border-left-color:var(--green);">
  <div class="module-label" style="color:var(--green);">Quick Reference</div>
  <div class="module-title">Topic Priority Matrix</div>
</div>

<div class="topic open">
  <div class="topic-head" onclick="toggle(this)" style="cursor:default;">
    <span class="topic-title" style="color:var(--heading)">All Topics Ranked by Exam Frequency</span>
    <span class="toggle-icon">+</span>
  </div>
  <div class="topic-body">
    <div class="table-wrap">
      <table class="matrix-table">
        <thead>
          <tr><th>Topic</th><th>Module</th><th>Part A</th><th>Part B</th><th>Priority</th></tr>
        </thead>
        <tbody>
          <tr><td>Energy Management Planning (phases)</td><td>1</td><td>★★★</td><td>★★★★★</td><td style="color:var(--red-tag)">🔴 HIGH</td></tr>
          <tr><td>Detailed Energy Audit (steps)</td><td>1</td><td>★★★</td><td>★★★★★</td><td style="color:var(--red-tag)">🔴 HIGH</td></tr>
          <tr><td>Power Quality Audit</td><td>1</td><td>★★★</td><td>★★★★</td><td style="color:var(--red-tag)">🔴 HIGH</td></tr>
          <tr><td>ECBC</td><td>1</td><td>★★★</td><td>★★★</td><td style="color:var(--red-tag)">🔴 HIGH</td></tr>
          <tr><td>Energy Audit Report</td><td>1</td><td>★★</td><td>★★★</td><td style="color:var(--red-tag)">🔴 HIGH</td></tr>
          <tr><td>Instruments for energy audit</td><td>1</td><td>★★</td><td>★★★</td><td style="color:var(--yellow-tag)">🟡 MED</td></tr>
          <tr><td>Building Management System</td><td>1</td><td>★★</td><td>★★★</td><td style="color:var(--yellow-tag)">🟡 MED</td></tr>
          <tr><td>Cascade efficiency</td><td>2</td><td>★★</td><td>★★★★★</td><td style="color:var(--red-tag)">🔴 HIGH</td></tr>
          <tr><td>Lighting energy management</td><td>2</td><td>★★★</td><td>★★★★★</td><td style="color:var(--red-tag)">🔴 HIGH</td></tr>
          <tr><td>Motor energy management + EEM features</td><td>2</td><td>★★★</td><td>★★★★★</td><td style="color:var(--red-tag)">🔴 HIGH</td></tr>
          <tr><td>Transformer design measures</td><td>2</td><td>★★★</td><td>★★★★</td><td style="color:var(--red-tag)">🔴 HIGH</td></tr>
          <tr><td>DSM techniques (all 6)</td><td>3</td><td>★★★</td><td>★★★★★</td><td style="color:var(--red-tag)">🔴 HIGH</td></tr>
          <tr><td>Peak demand control methods</td><td>3</td><td>★★</td><td>★★★★★</td><td style="color:var(--red-tag)">🔴 HIGH</td></tr>
          <tr><td>Power factor improvement + numericals</td><td>3</td><td>★★★</td><td>★★★★★</td><td style="color:var(--red-tag)">🔴 HIGH</td></tr>
          <tr><td>Ancillary services (7 types)</td><td>3</td><td>★★</td><td>★★★★</td><td style="color:var(--red-tag)">🔴 HIGH</td></tr>
          <tr><td>Time-of-day pricing</td><td>3</td><td>★★★</td><td>★★</td><td style="color:var(--yellow-tag)">🟡 MED</td></tr>
          <tr><td>Boiler energy conservation</td><td>4</td><td>★★</td><td>★★★★★</td><td style="color:var(--red-tag)">🔴 HIGH</td></tr>
          <tr><td>Steam distribution energy savings</td><td>4</td><td>★★</td><td>★★★★</td><td style="color:var(--red-tag)">🔴 HIGH</td></tr>
          <tr><td>Furnace energy conservation</td><td>4</td><td>★★</td><td>★★★★</td><td style="color:var(--red-tag)">🔴 HIGH</td></tr>
          <tr><td>Cogeneration types + schemes</td><td>4</td><td>★★★</td><td>★★★★</td><td style="color:var(--red-tag)">🔴 HIGH</td></tr>
          <tr><td>HVAC / COP</td><td>4</td><td>★★★</td><td>★★★</td><td style="color:var(--yellow-tag)">🟡 MED</td></tr>
          <tr><td>Waste heat recovery types</td><td>4</td><td>★★</td><td>★★★</td><td style="color:var(--yellow-tag)">🟡 MED</td></tr>
          <tr><td>Simple payback period + numerical</td><td>5</td><td>★★★</td><td>★★★★★</td><td style="color:var(--red-tag)">🔴 HIGH</td></tr>
          <tr><td>NPV method + numericals</td><td>5</td><td>★★★</td><td>★★★★★</td><td style="color:var(--red-tag)">🔴 HIGH</td></tr>
          <tr><td>LCC approach</td><td>5</td><td>★★★</td><td>★★★★★</td><td style="color:var(--red-tag)">🔴 HIGH</td></tr>
          <tr><td>IRR method + numerical</td><td>5</td><td>★★</td><td>★★★</td><td style="color:var(--red-tag)">🔴 HIGH</td></tr>
          <tr><td>ARR method + numerical</td><td>5</td><td>★★</td><td>★★★</td><td style="color:var(--yellow-tag)">🟡 MED</td></tr>
          <tr><td>Computer Aided EMS</td><td>5</td><td>★★★</td><td>★★★</td><td style="color:var(--yellow-tag)">🟡 MED</td></tr>
          <tr><td>EEM payback period numerical</td><td>2/5</td><td>★</td><td>★★★★</td><td style="color:var(--red-tag)">🔴 HIGH</td></tr>
        </tbody>
      </table>
    </div>
  </div>
</div>

</div><!-- /content -->

<footer>EET424 Energy Management Study Guide · PYQ Analysis: June 2023, Oct 2023, Jan 2024, May 2024, April 2025 · S8 EEE 2019 Scheme · APJ KTU</footer>

<button id="scroll-top" onclick="window.scrollTo({top:0,behavior:'smooth'})">↑</button>

<script>
  function toggle(head) {
    const topic = head.closest('.topic');
    topic.classList.toggle('open');
  }

  // Highlight active nav on scroll
  const sections = document.querySelectorAll('[id^="mod"], #matrix');
  const navLinks = document.querySelectorAll('.nav-pill');
  window.addEventListener('scroll', () => {
    let current = '';
    sections.forEach(s => {
      if (window.scrollY >= s.offsetTop - 80) current = s.id;
    });
    navLinks.forEach(l => {
      l.classList.toggle('active', l.getAttribute('href') === '#' + current);
    });
  });
</script>
</body>
</html>
