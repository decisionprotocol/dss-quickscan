[index (1).html](https://github.com/user-attachments/files/29114260/index.1.html)
<!DOCTYPE html>
<html lang="en">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>Crisis IQ Assessment — Decision Protocol</title>
<link href="https://fonts.googleapis.com/css2?family=Playfair+Display:ital,wght@0,400;0,700;0,900;1,400&family=DM+Mono:wght@300;400;500&family=DM+Sans:wght@300;400;500;600&display=swap" rel="stylesheet">
<style>
  :root {
    --black: #080808;
    --dark: #111111;
    --panel: #161616;
    --border: #242424;
    --mid: #383838;
    --muted: #606060;
    --light: #909090;
    --white: #F2F2ED;
    --accent: #C4B06A;
    --accent-dim: rgba(196,176,106,0.12);
    --red: #8B2E2E;
    --green: #2E6B4F;
  }

  * { margin:0; padding:0; box-sizing:border-box; }

  body {
    background: var(--black);
    color: var(--white);
    font-family: 'DM Sans', sans-serif;
    font-size: 14px;
    line-height: 1.6;
    min-height: 100vh;
  }

  /* SCREENS */
  .screen { display: none; min-height: 100vh; }
  .screen.active { display: flex; flex-direction: column; }

  /* INTRO SCREEN */
  #screen-intro {
    padding: 80px 60px;
    max-width: 900px;
    margin: 0 auto;
    width: 100%;
  }

  .intro-brand {
    display: flex;
    align-items: center;
    gap: 12px;
    margin-bottom: 80px;
  }

  .brand-squares { display: flex; gap: 3px; }
  .bsq { width: 8px; height: 8px; background: var(--white); }
  .bsq:nth-child(2) { background: var(--muted); }
  .bsq:nth-child(3) { background: var(--border); }

  .brand-text {
    font-family: 'DM Mono', monospace;
    font-size: 10px;
    letter-spacing: 0.25em;
    color: var(--muted);
    text-transform: uppercase;
  }

  .intro-eyebrow {
    font-family: 'DM Mono', monospace;
    font-size: 10px;
    letter-spacing: 0.3em;
    color: var(--accent);
    text-transform: uppercase;
    margin-bottom: 24px;
  }

  .intro-title {
    font-family: 'Playfair Display', serif;
    font-size: 64px;
    font-weight: 900;
    line-height: 1.05;
    color: var(--white);
    margin-bottom: 32px;
  }

  .intro-title span { color: var(--accent); }

  .intro-sub {
    font-size: 16px;
    color: var(--light);
    line-height: 1.7;
    max-width: 560px;
    margin-bottom: 48px;
  }

  .intro-meta {
    display: grid;
    grid-template-columns: repeat(3, 1fr);
    gap: 1px;
    background: var(--border);
    margin-bottom: 56px;
    max-width: 560px;
  }

  .meta-item {
    background: var(--panel);
    padding: 20px 24px;
  }

  .meta-label {
    font-family: 'DM Mono', monospace;
    font-size: 9px;
    color: var(--muted);
    letter-spacing: 0.2em;
    text-transform: uppercase;
    margin-bottom: 6px;
  }

  .meta-val {
    font-size: 13px;
    color: var(--white);
    font-weight: 500;
  }

  .intro-warning {
    background: var(--panel);
    border-left: 2px solid var(--accent);
    padding: 20px 24px;
    margin-bottom: 48px;
    max-width: 560px;
    font-size: 12px;
    color: var(--light);
    line-height: 1.6;
  }

  .intro-warning strong { color: var(--white); }

  .btn-start {
    display: inline-flex;
    align-items: center;
    gap: 16px;
    background: var(--white);
    color: var(--black);
    padding: 18px 40px;
    font-family: 'DM Mono', monospace;
    font-size: 11px;
    letter-spacing: 0.2em;
    text-transform: uppercase;
    cursor: pointer;
    border: none;
    font-weight: 500;
    transition: opacity 0.2s;
  }

  .btn-start:hover { opacity: 0.85; }

  /* QUESTION SCREEN */
  #screen-question {
    flex-direction: column;
  }

  .q-header {
    padding: 24px 60px;
    border-bottom: 1px solid var(--border);
    display: flex;
    justify-content: space-between;
    align-items: center;
    background: var(--dark);
    position: sticky;
    top: 0;
    z-index: 10;
  }

  .q-brand {
    display: flex;
    align-items: center;
    gap: 10px;
  }

  .q-brand-name {
    font-family: 'DM Mono', monospace;
    font-size: 9px;
    color: var(--muted);
    letter-spacing: 0.2em;
    text-transform: uppercase;
  }

  .q-progress-wrap {
    display: flex;
    align-items: center;
    gap: 20px;
  }

  .q-progress-num {
    font-family: 'DM Mono', monospace;
    font-size: 11px;
    color: var(--muted);
  }

  .q-progress-bar {
    width: 200px;
    height: 2px;
    background: var(--border);
    position: relative;
  }

  .q-progress-fill {
    height: 100%;
    background: var(--accent);
    transition: width 0.4s ease;
  }

  .q-dim-label {
    font-family: 'DM Mono', monospace;
    font-size: 9px;
    color: var(--accent);
    letter-spacing: 0.2em;
    text-transform: uppercase;
  }

  .q-body {
    flex: 1;
    display: flex;
    flex-direction: column;
    justify-content: center;
    padding: 60px;
    max-width: 900px;
    margin: 0 auto;
    width: 100%;
  }

  .q-type-tag {
    font-family: 'DM Mono', monospace;
    font-size: 9px;
    letter-spacing: 0.25em;
    color: var(--muted);
    text-transform: uppercase;
    margin-bottom: 20px;
  }

  .q-text {
    font-family: 'Playfair Display', serif;
    font-size: 26px;
    font-weight: 700;
    color: var(--white);
    line-height: 1.35;
    margin-bottom: 12px;
  }

  .q-context {
    font-size: 13px;
    color: var(--muted);
    margin-bottom: 48px;
    line-height: 1.6;
    max-width: 680px;
    font-style: italic;
  }

  .q-options {
    display: flex;
    flex-direction: column;
    gap: 10px;
    max-width: 700px;
  }

  .q-option {
    display: flex;
    align-items: flex-start;
    gap: 16px;
    padding: 20px 24px;
    background: var(--panel);
    border: 1px solid var(--border);
    cursor: pointer;
    transition: all 0.15s;
    text-align: left;
  }

  .q-option:hover {
    border-color: var(--mid);
    background: #1C1C1C;
  }

  .q-option.selected {
    border-color: var(--accent);
    background: var(--accent-dim);
  }

  .opt-letter {
    font-family: 'DM Mono', monospace;
    font-size: 10px;
    color: var(--muted);
    min-width: 16px;
    margin-top: 2px;
    letter-spacing: 0.1em;
  }

  .q-option.selected .opt-letter { color: var(--accent); }

  .opt-text {
    font-size: 13px;
    color: var(--light);
    line-height: 1.6;
  }

  .q-option.selected .opt-text { color: var(--white); }

  .q-nav {
    display: flex;
    justify-content: space-between;
    align-items: center;
    padding: 32px 60px;
    border-top: 1px solid var(--border);
    background: var(--dark);
  }

  .btn-nav {
    display: inline-flex;
    align-items: center;
    gap: 10px;
    padding: 14px 28px;
    font-family: 'DM Mono', monospace;
    font-size: 10px;
    letter-spacing: 0.15em;
    text-transform: uppercase;
    cursor: pointer;
    border: 1px solid var(--border);
    background: transparent;
    color: var(--muted);
    transition: all 0.2s;
  }

  .btn-nav:hover { border-color: var(--mid); color: var(--white); }
  .btn-nav:disabled { opacity: 0.3; cursor: default; }

  .btn-nav-primary {
    background: var(--white);
    color: var(--black);
    border-color: var(--white);
  }

  .btn-nav-primary:hover { opacity: 0.85; color: var(--black); }
  .btn-nav-primary:disabled { opacity: 0.3; }

  .nav-warn {
    font-size: 11px;
    color: var(--red);
    font-style: italic;
    display: none;
  }

  .nav-warn.visible { display: block; }

  /* RESULTS SCREEN */
  #screen-results {
    padding: 60px;
    max-width: 960px;
    margin: 0 auto;
    width: 100%;
  }

  .results-header {
    border-bottom: 1px solid var(--border);
    padding-bottom: 40px;
    margin-bottom: 48px;
  }

  .results-eyebrow {
    font-family: 'DM Mono', monospace;
    font-size: 10px;
    letter-spacing: 0.25em;
    color: var(--accent);
    text-transform: uppercase;
    margin-bottom: 16px;
  }

  .results-name-row {
    display: flex;
    justify-content: space-between;
    align-items: flex-end;
  }

  .results-title {
    font-family: 'Playfair Display', serif;
    font-size: 42px;
    font-weight: 900;
    color: var(--white);
    line-height: 1.1;
  }

  .results-date {
    font-family: 'DM Mono', monospace;
    font-size: 10px;
    color: var(--muted);
    letter-spacing: 0.15em;
  }

  /* BIG SCORE */
  .score-hero {
    display: grid;
    grid-template-columns: auto 1fr;
    gap: 48px;
    align-items: center;
    margin-bottom: 48px;
    padding: 48px;
    background: var(--panel);
    border: 1px solid var(--border);
  }

  .score-number {
    font-family: 'Playfair Display', serif;
    font-size: 120px;
    font-weight: 900;
    color: var(--white);
    line-height: 1;
  }

  .score-number span {
    font-size: 40px;
    color: var(--muted);
    font-weight: 400;
  }

  .score-right {}

  .score-band {
    font-family: 'DM Mono', monospace;
    font-size: 10px;
    letter-spacing: 0.25em;
    text-transform: uppercase;
    margin-bottom: 8px;
    padding: 4px 10px;
    display: inline-block;
  }

  .score-archetype {
    font-family: 'Playfair Display', serif;
    font-size: 32px;
    font-weight: 700;
    color: var(--white);
    margin-bottom: 12px;
  }

  .score-archetype-sub {
    font-size: 13px;
    color: var(--light);
    line-height: 1.6;
    max-width: 440px;
    margin-bottom: 20px;
  }

  .score-percentile {
    font-family: 'DM Mono', monospace;
    font-size: 11px;
    color: var(--muted);
    letter-spacing: 0.1em;
  }

  /* DIMENSION BREAKDOWN */
  .dim-grid {
    display: grid;
    grid-template-columns: 1fr 1fr;
    gap: 2px;
    background: var(--border);
    margin-bottom: 48px;
  }

  .dim-card {
    background: var(--panel);
    padding: 32px;
  }

  .dim-card-label {
    font-family: 'DM Mono', monospace;
    font-size: 9px;
    letter-spacing: 0.2em;
    color: var(--muted);
    text-transform: uppercase;
    margin-bottom: 6px;
  }

  .dim-card-name {
    font-family: 'Playfair Display', serif;
    font-size: 18px;
    font-weight: 700;
    color: var(--white);
    margin-bottom: 16px;
  }

  .dim-score-row {
    display: flex;
    align-items: baseline;
    gap: 8px;
    margin-bottom: 12px;
  }

  .dim-score-num {
    font-family: 'DM Mono', monospace;
    font-size: 36px;
    font-weight: 500;
    color: var(--white);
  }

  .dim-score-max {
    font-family: 'DM Mono', monospace;
    font-size: 14px;
    color: var(--muted);
  }

  .dim-bar {
    height: 3px;
    background: var(--border);
    margin-bottom: 16px;
    position: relative;
  }

  .dim-bar-fill {
    height: 100%;
    background: var(--accent);
    transition: width 1s ease;
  }

  .dim-insight {
    font-size: 12px;
    color: var(--light);
    line-height: 1.6;
  }

  .dim-insight strong { color: var(--white); font-weight: 500; }

  /* SUB SCORES */
  .sub-grid {
    display: grid;
    grid-template-columns: repeat(4, 1fr);
    gap: 2px;
    margin-top: 16px;
  }

  .sub-item {
    background: var(--dark);
    padding: 12px 14px;
  }

  .sub-name {
    font-family: 'DM Mono', monospace;
    font-size: 8px;
    color: var(--muted);
    letter-spacing: 0.1em;
    text-transform: uppercase;
    margin-bottom: 6px;
    line-height: 1.4;
  }

  .sub-pips {
    display: flex;
    gap: 2px;
    margin-bottom: 4px;
  }

  .sub-pip {
    width: 8px;
    height: 3px;
    background: var(--border);
  }

  .sub-pip.on { background: var(--accent); }

  /* ARCHETYPE DEEP DIVE */
  .archetype-section {
    margin-bottom: 48px;
    padding: 40px;
    background: var(--panel);
    border: 1px solid var(--border);
    border-left: 3px solid var(--accent);
  }

  .arch-label {
    font-family: 'DM Mono', monospace;
    font-size: 9px;
    letter-spacing: 0.25em;
    color: var(--accent);
    text-transform: uppercase;
    margin-bottom: 16px;
  }

  .arch-name {
    font-family: 'Playfair Display', serif;
    font-size: 28px;
    font-weight: 700;
    color: var(--white);
    margin-bottom: 16px;
  }

  .arch-desc {
    font-size: 13px;
    color: var(--light);
    line-height: 1.7;
    margin-bottom: 28px;
    max-width: 680px;
  }

  .arch-cols {
    display: grid;
    grid-template-columns: 1fr 1fr;
    gap: 24px;
  }

  .arch-col-label {
    font-family: 'DM Mono', monospace;
    font-size: 9px;
    letter-spacing: 0.2em;
    color: var(--muted);
    text-transform: uppercase;
    margin-bottom: 12px;
  }

  .arch-col-items {
    display: flex;
    flex-direction: column;
    gap: 8px;
  }

  .arch-col-item {
    display: flex;
    gap: 10px;
    font-size: 12px;
    color: var(--light);
    line-height: 1.5;
  }

  .arch-col-item::before {
    content: '—';
    color: var(--muted);
    flex-shrink: 0;
  }

  /* DEVELOPMENT PLAN */
  .dev-plan {
    margin-bottom: 48px;
  }

  .dev-plan-header {
    display: flex;
    align-items: baseline;
    gap: 20px;
    margin-bottom: 24px;
  }

  .dev-plan-title {
    font-family: 'Playfair Display', serif;
    font-size: 22px;
    font-weight: 700;
    color: var(--white);
  }

  .dev-plan-sub {
    font-size: 12px;
    color: var(--muted);
  }

  .dev-grid {
    display: grid;
    grid-template-columns: repeat(3, 1fr);
    gap: 2px;
    background: var(--border);
  }

  .dev-phase {
    background: var(--panel);
    padding: 28px;
  }

  .dev-phase-label {
    font-family: 'DM Mono', monospace;
    font-size: 9px;
    color: var(--muted);
    letter-spacing: 0.2em;
    text-transform: uppercase;
    margin-bottom: 6px;
  }

  .dev-phase-title {
    font-size: 14px;
    font-weight: 600;
    color: var(--white);
    margin-bottom: 16px;
  }

  .dev-items {
    display: flex;
    flex-direction: column;
    gap: 10px;
  }

  .dev-item {
    font-size: 12px;
    color: var(--light);
    line-height: 1.5;
    padding-left: 16px;
    border-left: 1px solid var(--border);
  }

  .dev-item strong { color: var(--white); font-weight: 500; display: block; margin-bottom: 2px; }

  /* NEXT STEPS */
  .next-steps {
    background: var(--panel);
    border: 1px solid var(--border);
    padding: 40px;
    margin-bottom: 48px;
  }

  .next-label {
    font-family: 'DM Mono', monospace;
    font-size: 9px;
    letter-spacing: 0.25em;
    color: var(--muted);
    text-transform: uppercase;
    margin-bottom: 20px;
  }

  .next-title {
    font-family: 'Playfair Display', serif;
    font-size: 22px;
    font-weight: 700;
    color: var(--white);
    margin-bottom: 12px;
  }

  .next-sub {
    font-size: 13px;
    color: var(--light);
    line-height: 1.6;
    margin-bottom: 32px;
    max-width: 580px;
  }

  .next-options {
    display: grid;
    grid-template-columns: repeat(3, 1fr);
    gap: 2px;
    background: var(--border);
  }

  .next-opt {
    background: var(--dark);
    padding: 24px;
  }

  .next-opt-num {
    font-family: 'DM Mono', monospace;
    font-size: 24px;
    font-weight: 300;
    color: var(--border);
    margin-bottom: 12px;
  }

  .next-opt-title {
    font-size: 13px;
    font-weight: 600;
    color: var(--white);
    margin-bottom: 6px;
  }

  .next-opt-price {
    font-family: 'DM Mono', monospace;
    font-size: 10px;
    color: var(--accent);
    letter-spacing: 0.1em;
    margin-bottom: 10px;
  }

  .next-opt-desc {
    font-size: 11px;
    color: var(--muted);
    line-height: 1.5;
  }

  .btn-cta {
    display: inline-flex;
    align-items: center;
    gap: 12px;
    background: var(--white);
    color: var(--black);
    padding: 16px 36px;
    font-family: 'DM Mono', monospace;
    font-size: 10px;
    letter-spacing: 0.2em;
    text-transform: uppercase;
    cursor: pointer;
    border: none;
    font-weight: 500;
    margin-top: 32px;
    transition: opacity 0.2s;
  }

  .btn-cta:hover { opacity: 0.85; }

  /* FOOTER */
  .results-footer {
    padding-top: 32px;
    border-top: 1px solid var(--border);
    display: flex;
    justify-content: space-between;
    align-items: center;
  }

  .rf-brand {
    font-family: 'DM Mono', monospace;
    font-size: 9px;
    color: var(--muted);
    letter-spacing: 0.2em;
    text-transform: uppercase;
  }

  .rf-note {
    font-size: 10px;
    color: var(--muted);
    font-style: italic;
  }

  /* UTIL */
  .divider {
    height: 1px;
    background: var(--border);
    margin: 40px 0;
  }

  @keyframes fadeIn {
    from { opacity: 0; transform: translateY(12px); }
    to { opacity: 1; transform: translateY(0); }
  }

  .fade-in { animation: fadeIn 0.4s ease forwards; }
</style>
</head>
<body>

<!-- ===== INTRO SCREEN ===== -->
<div id="screen-intro" class="screen active">
  <div class="intro-brand">
    <div class="brand-squares">
      <div class="bsq"></div><div class="bsq"></div><div class="bsq"></div>
    </div>
    <div class="brand-text">Decision Protocol</div>
  </div>

  <div class="intro-eyebrow">Individual Assessment — Version 1.0</div>

  <div class="intro-title">Crisis<br>IQ<span>™</span></div>

  <div class="intro-sub">
    Most intelligence tests measure how well you think. Crisis IQ measures how well you think when everything is pushing you not to.
    <br><br>
    This assessment produces a score from 0 to 160 and an archetype profile — mapping your decision performance under pressure across four dimensions.
  </div>

  <div class="intro-meta">
    <div class="meta-item">
      <div class="meta-label">Questions</div>
      <div class="meta-val">60</div>
    </div>
    <div class="meta-item">
      <div class="meta-label">Duration</div>
      <div class="meta-val">20-25 min</div>
    </div>
    <div class="meta-item">
      <div class="meta-label">Output</div>
      <div class="meta-val">Score + Profile</div>
    </div>
  </div>

  <div class="intro-warning">
    <strong>Before you begin:</strong> Answer based on how you actually behave under pressure — not how you aspire to behave. The assessment is designed to detect the difference. There are no right or wrong answers, only accurate and inaccurate ones.
  </div>

  <button class="btn-start" onclick="startAssessment()">
    Begin Assessment →
  </button>
</div>

<!-- ===== QUESTION SCREEN ===== -->
<div id="screen-question" class="screen">
  <div class="q-header">
    <div class="q-brand">
      <div class="brand-squares">
        <div class="bsq"></div><div class="bsq"></div><div class="bsq"></div>
      </div>
      <div class="q-brand-name">Crisis IQ™ — Decision Protocol</div>
    </div>
    <div class="q-progress-wrap">
      <div class="q-dim-label" id="dim-label">—</div>
      <div class="q-progress-bar">
        <div class="q-progress-fill" id="progress-fill" style="width:0%"></div>
      </div>
      <div class="q-progress-num" id="progress-num">1 / 60</div>
    </div>
  </div>

  <div class="q-body fade-in" id="q-body">
    <div class="q-type-tag" id="q-type">—</div>
    <div class="q-text" id="q-text">—</div>
    <div class="q-context" id="q-context"></div>
    <div class="q-options" id="q-options"></div>
  </div>

  <div class="q-nav">
    <button class="btn-nav" id="btn-prev" onclick="prevQ()" disabled>← Previous</button>
    <div class="nav-warn" id="nav-warn">Select an answer to continue</div>
    <button class="btn-nav btn-nav-primary" id="btn-next" onclick="nextQ()">Next →</button>
  </div>
</div>

<!-- ===== RESULTS SCREEN ===== -->
<div id="screen-results" class="screen">
  <!-- Dynamically populated -->
</div>

<script>
// ============================================================
// QUESTIONS DATABASE
// Format: { dim, sub, type, q, context, options: [{text, score}] }
// dim: 1=CognStab 2=EmotArch 3=TempIntel 4=SystAware
// sub: sub-dimension index within dim (1-4)
// score: 1-4 (4=highest Crisis IQ)
// ============================================================

const questions = [

// ── DIMENSION 1: COGNITIVE STABILITY UNDER PRESSURE ──────────

// Sub 1.1: Signal/Noise Separation
{dim:1,sub:1,type:"SCENARIO",
q:"You receive twelve urgent messages simultaneously during a high-stakes situation. Your instinct is:",
context:"A client crisis, a board decision, and a regulatory deadline all land at once.",
options:[
  {text:"Address them in the order they arrived — first in, first out",score:1},
  {text:"Answer the ones from the most senior people first",score:2},
  {text:"Pause, identify which one actually determines the outcome of the others, and start there",score:4},
  {text:"Delegate all of them and buy time",score:2}
]},

{dim:1,sub:1,type:"RETROSPECTIVE",
q:"Think of the last time you were in an information overload situation. What actually happened to your decision quality?",
context:"",
options:[
  {text:"It stayed consistent — I perform the same regardless of volume",score:4},
  {text:"I made faster decisions but I'm not sure they were better",score:2},
  {text:"I focused on what felt most urgent, which wasn't always what mattered most",score:2},
  {text:"It deteriorated noticeably — I missed things I would normally catch",score:1}
]},

{dim:1,sub:1,type:"PREFERENCE",
q:"When building a case for a decision, you instinctively:",
context:"",
options:[
  {text:"Gather as much information as possible before deciding",score:1},
  {text:"Identify the three facts that would change your decision if wrong, and focus there",score:4},
  {text:"Trust your experience to tell you what's relevant",score:2},
  {text:"Follow the process — whatever the standard procedure requires",score:2}
]},

// Sub 1.2: Cognitive Narrowing Resistance
{dim:1,sub:2,type:"SCENARIO",
q:"You are forty minutes into a high-pressure negotiation that is not going well. You notice your options feel limited. You:",
context:"Three offers have been rejected. The other party seems immovable.",
options:[
  {text:"Push harder on the position that's closest to working",score:1},
  {text:"Recognize the narrowing and deliberately ask: what options am I not seeing?",score:4},
  {text:"Take a brief break and return with the same approach but more energy",score:2},
  {text:"Escalate to someone more senior",score:1}
]},

{dim:1,sub:2,type:"RETROSPECTIVE",
q:"After a decision that didn't go well, how often do you discover there were options you didn't consider at the time?",
context:"",
options:[
  {text:"Rarely — I'm thorough in considering options before deciding",score:4},
  {text:"Sometimes — I usually see one or two things I missed",score:3},
  {text:"Often — in retrospect there were usually better paths I didn't see",score:2},
  {text:"Almost always — hindsight consistently reveals major blind spots",score:1}
]},

{dim:1,sub:2,type:"SCENARIO",
q:"A situation you've been managing for three weeks suddenly changes. New information contradicts your entire strategy. You:",
context:"Significant effort and political capital have already been invested.",
options:[
  {text:"Reframe the new information to fit the existing strategy if at all possible",score:1},
  {text:"Acknowledge the change but make only minimal adjustments to avoid disruption",score:2},
  {text:"Stop, reassess from first principles, and rebuild the strategy if necessary",score:4},
  {text:"Present both the old and new strategy to stakeholders and let them decide",score:2}
]},

// Sub 1.3: Working Memory Integrity
{dim:1,sub:3,type:"PREFERENCE",
q:"During a complex meeting where multiple decisions are being made simultaneously, you:",
context:"",
options:[
  {text:"Track everything mentally and rely on your memory",score:2},
  {text:"Take detailed notes on everything",score:3},
  {text:"Capture only decision points and the logic behind them — not everything",score:4},
  {text:"Focus on following the conversation — notes come after",score:1}
]},

{dim:1,sub:3,type:"SCENARIO",
q:"You are presenting a complex position when you are interrupted with a challenging question. After answering, you:",
context:"The question took the discussion in a different direction for several minutes.",
options:[
  {text:"Continue with the point you were making before the interruption",score:4},
  {text:"Ask where you were before the interruption",score:2},
  {text:"Adjust your presentation based on what emerged from the interruption",score:3},
  {text:"Summarize what's been covered so far and continue from there",score:3}
]},

{dim:1,sub:3,type:"RETROSPECTIVE",
q:"When managing multiple high-stakes situations simultaneously, what happens to the quality of your thinking?",
context:"",
options:[
  {text:"I compartmentalize effectively — each situation gets full attention when I'm in it",score:4},
  {text:"There's some bleed between them but I manage",score:3},
  {text:"My attention splits and I'm less sharp on each individual situation",score:2},
  {text:"I lose track of details across situations regularly",score:1}
]},

// Sub 1.4: Decision Fatigue Threshold
{dim:1,sub:4,type:"PREFERENCE",
q:"By the end of a day that has involved twelve significant decisions, your decision quality:",
context:"",
options:[
  {text:"Remains consistent — I don't experience meaningful fatigue",score:4},
  {text:"Declines slightly but I'm aware of it and compensate",score:3},
  {text:"Declines noticeably — I default to simpler options later in the day",score:2},
  {text:"Declines significantly — I avoid making important decisions late in the day",score:1}
]},

{dim:1,sub:4,type:"SCENARIO",
q:"You have been in back-to-back high-stakes conversations for six hours. An urgent decision arrives that cannot wait. You:",
context:"",
options:[
  {text:"Make the decision now — waiting is also a decision with consequences",score:3},
  {text:"Make the decision but document your reasoning more carefully than usual, knowing you may be fatigued",score:4},
  {text:"Delay the decision by the minimum time necessary to reset",score:3},
  {text:"Delegate the decision entirely",score:1}
]},

{dim:1,sub:4,type:"RETROSPECTIVE",
q:"Think of a poor decision you made. What was your state at the time?",
context:"",
options:[
  {text:"Fresh — the decision quality was unrelated to my state",score:4},
  {text:"Under time pressure but not particularly fatigued",score:3},
  {text:"Tired or stressed in a way that probably influenced my judgment",score:2},
  {text:"Significantly depleted — I knew I shouldn't be deciding but felt I had no choice",score:1}
]},

// Sub 1.5: Additional
{dim:1,sub:1,type:"PREFERENCE",
q:"When someone presents you with a compelling argument under pressure, your instinct is to:",
context:"",
options:[
  {text:"Accept it if it sounds logical and comes from a credible source",score:1},
  {text:"Ask what they're not telling you",score:4},
  {text:"Compare it against your existing position",score:3},
  {text:"Buy time before responding",score:2}
]},

{dim:1,sub:2,type:"SCENARIO",
q:"Three advisors give you three contradictory recommendations. You have one hour to decide. You:",
context:"All three are credible. All three have relevant expertise.",
options:[
  {text:"Go with the most senior person's recommendation",score:1},
  {text:"Go with the recommendation that aligns with your existing instinct",score:2},
  {text:"Identify the one factual question whose answer would resolve the contradiction",score:4},
  {text:"Split the difference between the three positions",score:1}
]},

{dim:1,sub:3,type:"PREFERENCE",
q:"When you realize mid-decision that you are missing critical information, you:",
context:"",
options:[
  {text:"Decide anyway — waiting for perfect information is rarely possible",score:2},
  {text:"Pause and explicitly map what you know versus what you're assuming",score:4},
  {text:"Make a provisional decision that can be reversed",score:3},
  {text:"Escalate to avoid deciding with incomplete information",score:1}
]},

// ── DIMENSION 2: EMOTIONAL ARCHITECTURE ──────────────────────

// Sub 2.1: Onset Recognition
{dim:2,sub:1,type:"PREFERENCE",
q:"You become aware that you are in an altered emotional state during a critical meeting. This awareness arrives:",
context:"",
options:[
  {text:"After the meeting, in retrospect",score:1},
  {text:"While acting from the emotion — I notice it once I've already responded",score:2},
  {text:"Before I respond — I feel the shift and catch it",score:4},
  {text:"I rarely notice emotional shifts during decisions",score:1}
]},

{dim:2,sub:1,type:"SCENARIO",
q:"A client says something in a meeting that irritates you significantly. What happens next?",
context:"The comment was dismissive of work you've invested months in.",
options:[
  {text:"I respond professionally in the moment — I don't register the irritation until later",score:2},
  {text:"I notice the irritation, take a brief internal pause, and choose my response deliberately",score:4},
  {text:"The irritation shows in my tone even if my words are professional",score:2},
  {text:"I address it directly — I believe in naming what's happening in the room",score:3}
]},

{dim:2,sub:1,type:"RETROSPECTIVE",
q:"Think of a high-stakes conversation where you were emotionally activated. When did you first become aware of it?",
context:"",
options:[
  {text:"I was aware from the start — I could feel it coming",score:4},
  {text:"During the conversation, once it was already affecting me",score:3},
  {text:"After the conversation, when I reflected on what happened",score:2},
  {text:"When someone else pointed it out to me",score:1}
]},

// Sub 2.2: Emotion-Decision Separation
{dim:2,sub:2,type:"SCENARIO",
q:"You are in a negotiation and realize you desperately want to close this deal — more than the terms justify. You:",
context:"The emotional pressure is real and you're aware of it.",
options:[
  {text:"Trust that my professionalism will prevent the emotion from influencing the outcome",score:2},
  {text:"Name it internally and actively hold the line on the terms, using the awareness as a check",score:4},
  {text:"Push for a quick close before the emotion distorts my judgment further",score:1},
  {text:"Step back from the negotiation and let a colleague take over",score:3}
]},

{dim:2,sub:2,type:"PREFERENCE",
q:"When you feel strongly that a decision is right — but cannot fully articulate why — you:",
context:"",
options:[
  {text:"Trust the feeling. Experience-based intuition is data",score:2},
  {text:"Discount the feeling until I can articulate the reasoning",score:2},
  {text:"Separate the feeling from the decision and test both independently",score:4},
  {text:"Seek external validation before proceeding",score:2}
]},

{dim:2,sub:2,type:"RETROSPECTIVE",
q:"How often do you later discover that an emotion was driving a decision you believed was rational at the time?",
context:"",
options:[
  {text:"Rarely — I'm generally accurate in distinguishing emotional from rational drivers",score:4},
  {text:"Occasionally — usually with significant decisions",score:3},
  {text:"Often — emotions influence my decisions more than I prefer to admit",score:2},
  {text:"Very often — in retrospect my decisions are frequently emotionally driven",score:1}
]},

// Sub 2.3: Escalation Resistance
{dim:2,sub:3,type:"SCENARIO",
q:"A counterpart in a high-stakes meeting becomes aggressive and personal in their criticism. Your natural response is:",
context:"",
options:[
  {text:"Match the energy — I don't accept being treated that way",score:1},
  {text:"Become quieter and more withdrawn",score:2},
  {text:"Maintain my position and tone — their behavior doesn't change my approach",score:4},
  {text:"Address the behavior directly before continuing the substantive discussion",score:3}
]},

{dim:2,sub:3,type:"PREFERENCE",
q:"When a situation escalates beyond what you expected, you typically:",
context:"",
options:[
  {text:"Escalate my own response proportionally",score:1},
  {text:"Become more deliberate and measured as the stakes rise",score:4},
  {text:"Focus on de-escalating the situation before addressing the substance",score:3},
  {text:"Withdraw and reassess",score:2}
]},

{dim:2,sub:3,type:"RETROSPECTIVE",
q:"In your most challenging professional confrontations, what happened to the quality of your thinking?",
context:"",
options:[
  {text:"It sharpened — I perform better under confrontational pressure",score:3},
  {text:"It stayed consistent — confrontation doesn't affect my reasoning",score:4},
  {text:"It declined somewhat — the emotional charge affected my clarity",score:2},
  {text:"It declined significantly — I struggle to think clearly when in direct conflict",score:1}
]},

// Sub 2.4: Recovery Speed
{dim:2,sub:4,type:"PREFERENCE",
q:"After a significant professional setback or failure, how long before you are fully operational at your normal decision quality?",
context:"",
options:[
  {text:"Hours — I process quickly and move forward",score:4},
  {text:"A day or two — I need to decompress before I'm fully sharp again",score:3},
  {text:"Several days — setbacks affect me for longer than I'd prefer",score:2},
  {text:"It varies significantly depending on the nature of the setback",score:3}
]},

{dim:2,sub:4,type:"SCENARIO",
q:"A major decision you made and championed publicly turns out to be wrong. The next significant decision arrives within 24 hours. You:",
context:"People are watching how you handle it.",
options:[
  {text:"Make the next decision with full clarity — the previous failure doesn't carry forward",score:4},
  {text:"Make the decision but with more caution than usual",score:3},
  {text:"Find it difficult to be decisive — the previous failure is affecting my confidence",score:2},
  {text:"Delay if possible — I need more time to recover my perspective",score:1}
]},

{dim:2,sub:4,type:"RETROSPECTIVE",
q:"After a destabilizing event — a major loss, a public failure, a significant betrayal — how do others describe your decision-making in the period that follows?",
context:"",
options:[
  {text:"Unchanged — I've been told I'm impressively consistent",score:4},
  {text:"Slightly more cautious but still effective",score:3},
  {text:"Noticeably affected — they can tell I've been destabilized",score:2},
  {text:"Significantly impaired — my decision quality drops visibly after setbacks",score:1}
]},

// Additional Dim 2
{dim:2,sub:1,type:"PREFERENCE",
q:"Which statement best describes your relationship with professional anxiety?",
context:"",
options:[
  {text:"I rarely experience it in professional settings",score:3},
  {text:"I experience it but it typically sharpens my performance",score:4},
  {text:"I experience it and it sometimes works against my performance",score:2},
  {text:"It significantly affects my performance in high-stakes situations",score:1}
]},

{dim:2,sub:2,type:"SCENARIO",
q:"You strongly dislike one of the people on the other side of a critical negotiation. The dislike is personal and visceral. You:",
context:"You've had a difficult history.",
options:[
  {text:"Manage it professionally — personal feelings don't affect my approach",score:3},
  {text:"Acknowledge it internally, actively monitor for it, and correct when I notice it influencing me",score:4},
  {text:"Try to minimize direct interaction with that person",score:2},
  {text:"It affects my approach more than I'd like — I find it difficult to fully separate",score:1}
]},

// ── DIMENSION 3: TEMPORAL INTELLIGENCE ───────────────────────

// Sub 3.1: Urgency Calibration
{dim:3,sub:1,type:"SCENARIO",
q:"A client calls demanding an immediate decision on a complex matter. The real deadline is actually three days away. You:",
context:"The urgency is emotional, not factual.",
options:[
  {text:"Match their urgency — if they feel it's urgent, treat it as urgent",score:1},
  {text:"Respond to the emotion immediately but clarify the actual timeline before deciding",score:4},
  {text:"Push back on the urgency and restate the actual timeline",score:3},
  {text:"Buy time diplomatically and address it on the real schedule",score:3}
]},

{dim:3,sub:1,type:"PREFERENCE",
q:"When multiple urgent items compete for your attention, how do you decide what is actually urgent?",
context:"",
options:[
  {text:"Whatever has the closest deadline",score:1},
  {text:"Whatever is causing the most pressure from the most people",score:1},
  {text:"Whatever has the most irreversible consequences if delayed",score:4},
  {text:"Whatever I can complete fastest and clear off the list",score:2}
]},

{dim:3,sub:1,type:"RETROSPECTIVE",
q:"How often do decisions you treated as urgent turn out to have had more time than you thought?",
context:"",
options:[
  {text:"Rarely — my urgency calibration is generally accurate",score:4},
  {text:"Sometimes — I occasionally overestimate urgency",score:3},
  {text:"Often — I tend to treat many things as more urgent than they are",score:2},
  {text:"Very often — urgency pressure frequently distorts my assessment of actual deadlines",score:1}
]},

// Sub 3.2: Irreversibility Awareness
{dim:3,sub:2,type:"PREFERENCE",
q:"Before making any significant decision, do you explicitly identify which elements of the decision are reversible and which are not?",
context:"",
options:[
  {text:"Yes — this is a deliberate step in my decision process",score:4},
  {text:"Sometimes — when the stakes are high enough",score:3},
  {text:"Rarely — I focus on making the best decision rather than its reversibility",score:2},
  {text:"No — I generally treat all decisions as reversible until they're not",score:1}
]},

{dim:3,sub:2,type:"SCENARIO",
q:"You are about to make a decision that is 70% right. Waiting would give you 90% clarity but costs time. The decision is irreversible. You:",
context:"",
options:[
  {text:"Decide now — 70% is good enough and time has value",score:2},
  {text:"Identify what specific information would move you from 70% to 90% and pursue only that",score:4},
  {text:"Wait for 90% clarity — irreversible decisions require maximum confidence",score:3},
  {text:"Make a provisional decision while continuing to gather information",score:2}
]},

{dim:3,sub:2,type:"RETROSPECTIVE",
q:"Think of the worst decision you've made professionally. Was the irreversibility of that decision clear to you at the time?",
context:"",
options:[
  {text:"Yes — I knew it was irreversible and decided anyway",score:3},
  {text:"Partially — I underestimated how permanent the consequences would be",score:2},
  {text:"No — the irreversibility only became clear in retrospect",score:1},
  {text:"The decision was reversible — the poor outcome came from something else",score:4}
]},

// Sub 3.3: Long-Horizon Maintenance
{dim:3,sub:3,type:"SCENARIO",
q:"You are under intense short-term pressure to accept a deal that compromises your long-term positioning. You:",
context:"Refusing creates immediate pain. Accepting solves the immediate problem but costs you later.",
options:[
  {text:"Accept — certain short-term relief is worth uncertain long-term cost",score:1},
  {text:"Refuse — long-term positioning is non-negotiable",score:3},
  {text:"Negotiate specifically on the elements that compromise your long-term position",score:4},
  {text:"Delay the decision to see if the short-term pressure resolves itself",score:2}
]},

{dim:3,sub:3,type:"PREFERENCE",
q:"When you're in a crisis, how present is the long-term consequence of your decisions in your thinking?",
context:"",
options:[
  {text:"Very present — I actively protect long-term positioning even under acute pressure",score:4},
  {text:"Present but subordinated to immediate priorities",score:3},
  {text:"Largely absent — the immediate crisis dominates my thinking",score:2},
  {text:"Completely absent — survival mode eliminates long-term thinking",score:1}
]},

{dim:3,sub:3,type:"RETROSPECTIVE",
q:"Looking back at decisions you made under significant pressure, how often did those decisions compromise your long-term position in ways you later regretted?",
context:"",
options:[
  {text:"Rarely — I protect long-term positioning even under pressure",score:4},
  {text:"Occasionally — a few decisions I've made under pressure cost me later",score:3},
  {text:"Often — pressure consistently moves me toward short-term decisions",score:2},
  {text:"Very often — short-term pressure is my most consistent decision bias",score:1}
]},

// Sub 3.4: Pause Competence
{dim:3,sub:4,type:"PREFERENCE",
q:"The ability to deliberately stop a decision-making process you're already in motion on — how available is this ability to you?",
context:"",
options:[
  {text:"Fully available — I can stop any process when I choose to",score:4},
  {text:"Available with effort — I can do it but there's resistance",score:3},
  {text:"Difficult — once I'm in motion it's hard to stop voluntarily",score:2},
  {text:"Very difficult — I tend to complete decisions once I've started them regardless",score:1}
]},

{dim:3,sub:4,type:"SCENARIO",
q:"In the middle of a critical negotiation you realize you need more time than you have. The correct move is to pause. But stopping now carries social and relational cost. You:",
context:"Everyone is waiting for you to continue.",
options:[
  {text:"Continue — the social cost of stopping is too high",score:1},
  {text:"Push through as quickly as possible to minimize the damage from moving too fast",score:2},
  {text:"Stop, absorb the social cost, and create the time you need",score:4},
  {text:"Find a procedural justification to pause that doesn't expose your need for time",score:3}
]},

{dim:3,sub:4,type:"RETROSPECTIVE",
q:"When you have paused a decision process that was moving too fast, what happened?",
context:"",
options:[
  {text:"The outcome improved — the pause created better decisions",score:4},
  {text:"Mixed results — sometimes better, sometimes the delay cost me",score:3},
  {text:"I rarely pause decision processes once they're in motion",score:2},
  {text:"I don't have a clear pattern around this",score:2}
]},

// Additional Dim 3
{dim:3,sub:1,type:"PREFERENCE",
q:"A deadline that was set artificially to create pressure. How quickly do you typically recognize this?",
context:"",
options:[
  {text:"Immediately — I distinguish real deadlines from artificial ones reliably",score:4},
  {text:"Usually — I catch most artificial deadlines but not all",score:3},
  {text:"Sometimes — artificial deadlines often work on me before I recognize them",score:2},
  {text:"Rarely — deadline pressure reliably activates my urgency response regardless",score:1}
]},

// ── DIMENSION 4: SYSTEMIC AWARENESS ──────────────────────────

// Sub 4.1: Room Reading
{dim:4,sub:1,type:"PREFERENCE",
q:"When you enter a high-stakes meeting, how quickly do you form an accurate read of the emotional and political dynamics in the room?",
context:"",
options:[
  {text:"Within minutes — I read rooms quickly and accurately",score:4},
  {text:"During the first exchange — I need to hear people speak before I can read them",score:3},
  {text:"Gradually — it takes time to build an accurate picture",score:2},
  {text:"I focus on the content rather than the dynamics",score:1}
]},

{dim:4,sub:1,type:"SCENARIO",
q:"You are presenting a proposal and notice that one person in the room — who has not spoken — is visibly disengaged. You:",
context:"They are senior. Their support matters.",
options:[
  {text:"Continue the presentation — one person's engagement doesn't derail me",score:2},
  {text:"Adjust the presentation in real time to re-engage them",score:3},
  {text:"Name it directly: 'I want to make sure this is landing — what's your reaction so far?'",score:4},
  {text:"Address it after the meeting",score:1}
]},

{dim:4,sub:1,type:"RETROSPECTIVE",
q:"How accurate is your in-the-moment assessment of what other people in a decision room are actually thinking versus what they're saying?",
context:"",
options:[
  {text:"Very accurate — I reliably read the gap between stated and actual positions",score:4},
  {text:"Generally accurate — I catch most of what's not being said",score:3},
  {text:"Partially accurate — I miss things regularly",score:2},
  {text:"Not reliable — I tend to take what people say at face value",score:1}
]},

// Sub 4.2: Influence Mapping
{dim:4,sub:2,type:"PREFERENCE",
q:"Before a high-stakes decision meeting, do you explicitly map who influences whom — not just who holds formal authority?",
context:"",
options:[
  {text:"Always — informal influence mapping is a standard part of my preparation",score:4},
  {text:"For major decisions — when the stakes justify the preparation",score:3},
  {text:"Occasionally — when something about the situation signals I should",score:2},
  {text:"Rarely — I focus on the decision itself rather than the politics around it",score:1}
]},

{dim:4,sub:2,type:"SCENARIO",
q:"The formal decision-maker in a room agrees with you. But you sense that someone else in the room holds the actual influence over the outcome. You:",
context:"The formal and informal authority don't align.",
options:[
  {text:"Focus on the formal decision-maker — that's the legitimate authority",score:1},
  {text:"Win over both — address the formal decision-maker while also engaging the informal authority",score:4},
  {text:"Focus on the informal authority — that's where the real decision will be made",score:3},
  {text:"Name the dynamic directly",score:3}
]},

{dim:4,sub:2,type:"RETROSPECTIVE",
q:"Think of a decision that didn't go the way you expected despite having the right arguments. What happened?",
context:"",
options:[
  {text:"I had misread the informal influence dynamics — the decision was made before the meeting",score:3},
  {text:"Someone I didn't expect had more influence than was visible",score:3},
  {text:"My arguments were right but my read of the room was wrong",score:2},
  {text:"I'm genuinely not sure — the failure analysis wasn't clear",score:1}
]},

// Sub 4.3: Cascade Anticipation
{dim:4,sub:3,type:"PREFERENCE",
q:"When making a significant decision, how far ahead do you typically model the second and third-order consequences?",
context:"",
options:[
  {text:"Consistently far — I routinely think three or more moves ahead",score:4},
  {text:"For the most significant decisions — when stakes justify it",score:3},
  {text:"One move ahead — I focus on the immediate consequences",score:2},
  {text:"I focus on the decision at hand — consequences reveal themselves",score:1}
]},

{dim:4,sub:3,type:"SCENARIO",
q:"You are about to send a message to a client that solves the immediate problem but will likely create a different problem in six weeks. You:",
context:"The six-week problem is real but not certain.",
options:[
  {text:"Send it — the immediate problem is certain, the future problem is speculative",score:1},
  {text:"Solve the immediate problem in a way that doesn't create the future problem, even if it's harder",score:4},
  {text:"Send it and prepare to manage the future problem when it arrives",score:2},
  {text:"Flag both problems to the client and let them choose",score:3}
]},

{dim:4,sub:3,type:"RETROSPECTIVE",
q:"How often do decisions you make create problems you genuinely did not anticipate at the time?",
context:"",
options:[
  {text:"Rarely — I anticipate most downstream consequences before deciding",score:4},
  {text:"Occasionally — some unanticipated consequences appear but they're manageable",score:3},
  {text:"Often — unforeseen consequences are a regular feature of my decisions",score:2},
  {text:"Very often — I'm frequently surprised by what my decisions set in motion",score:1}
]},

// Sub 4.4: Decision Environment Assessment
{dim:4,sub:4,type:"PREFERENCE",
q:"Before committing to a position in a high-stakes meeting, do you assess the emotional and cognitive state of the other decision-makers in the room?",
context:"",
options:[
  {text:"Yes — it's as important as assessing the merits of the decision itself",score:4},
  {text:"Sometimes — when the relationship dynamic signals I should",score:3},
  {text:"Rarely — I focus on the substance rather than the state of the people",score:2},
  {text:"No — people's states are their own responsibility to manage",score:1}
]},

{dim:4,sub:4,type:"SCENARIO",
q:"You realize the person you're about to ask to make a critical decision is visibly stressed and cognitively overloaded. You:",
context:"The decision cannot wait more than 24 hours.",
options:[
  {text:"Proceed — the decision needs to be made and their state is not my responsibility",score:1},
  {text:"Simplify your presentation to reduce their cognitive load as much as possible",score:3},
  {text:"Explicitly name what you observe: 'This seems like a difficult moment — do you want to take 20 minutes first?'",score:4},
  {text:"Take the decision off their plate entirely and decide yourself within your mandate",score:2}
]},

{dim:4,sub:4,type:"RETROSPECTIVE",
q:"Think of a situation where a decision went wrong because the person making it was not in a state to make it well. Did you see that coming?",
context:"",
options:[
  {text:"Yes — I saw it and acted on it",score:4},
  {text:"Yes — I saw it but didn't act on it",score:2},
  {text:"Partially — I sensed something was off but didn't diagnose it clearly",score:2},
  {text:"No — I only recognized the state problem in retrospect",score:1}
]},

// Additional Dim 4
{dim:4,sub:1,type:"PREFERENCE",
q:"When you walk out of a meeting, how complete and accurate is your understanding of what each person in that meeting actually wanted — not just what they said?",
context:"",
options:[
  {text:"Very complete — I usually leave with a clear picture of everyone's actual agenda",score:4},
  {text:"Fairly complete — I get most of it but miss some nuances",score:3},
  {text:"Partial — I understand the stated positions but often miss the underlying ones",score:2},
  {text:"Basic — I focus on what was said rather than what was meant",score:1}
]},

{dim:4,sub:3,type:"SCENARIO",
q:"You are in a room where the decision being made will affect people who are not present. You:",
context:"The absent parties have legitimate stakes in the outcome.",
options:[
  {text:"Focus on the people present — they hold the mandate for this decision",score:1},
  {text:"Represent the absent parties' interests as part of your contribution to the decision",score:3},
  {text:"Explicitly name that the absent parties need to be considered before the decision is finalized",score:4},
  {text:"Make a note to communicate the decision to the absent parties once made",score:2}
]}

];

// ============================================================
// ARCHETYPE DEFINITIONS
// ============================================================

const archetypes = [
  {
    name: "The Anchor",
    range: [130, 160],
    band: "Exceptional Crisis IQ",
    bandColor: "#2E6B4F",
    percentile: "Top 2%",
    desc: "You stabilize rooms through presence alone. You process rapidly, decide clearly, and maintain perspective when others lose it. Your crisis performance is not a function of the conditions — it's a function of your architecture.",
    strengths: [
      "Maintains full cognitive capacity under extreme pressure",
      "Reads emotional and political dynamics in real time",
      "Separates urgency from importance instinctively",
      "Decisions hold up under retrospective scrutiny",
      "Others are more stable when you are present"
    ],
    vulnerabilities: [
      "Can underestimate how destabilized others are — your baseline is not theirs",
      "May move to decision before others in the room are ready to receive it",
      "High tolerance for pressure can mask the need for rest and reset",
      "Others may project infallibility onto you — a dangerous expectation"
    ]
  },
  {
    name: "The Navigator",
    range: [110, 129],
    band: "High Crisis IQ",
    bandColor: "#4A7A3A",
    percentile: "Top 15%",
    desc: "You read rooms with exceptional accuracy and maintain systemic awareness most professionals never develop. Your decision quality under pressure is consistently above average — with one specific vulnerability.",
    strengths: [
      "Exceptional influence mapping and room reading",
      "Strong cascade anticipation — sees downstream consequences others miss",
      "Calibrates urgency accurately in most situations",
      "Maintains long-term perspective under short-term pressure"
    ],
    vulnerabilities: [
      "Decision quality can drop when operating without the room's input",
      "Systemic awareness can slow individual decisions when speed is required",
      "Social sensitivity sometimes overrides pure decision logic",
      "Needs to be careful not to over-engineer simple decisions"
    ]
  },
  {
    name: "The Analyst",
    range: [90, 109],
    band: "Above Average Crisis IQ",
    bandColor: "#7A7A2A",
    percentile: "Top 35%",
    desc: "Your cognitive architecture is strong. You process clearly, separate signal from noise, and maintain working memory integrity under significant load. The gap is emotional: you believe you're deciding rationally when the data shows otherwise.",
    strengths: [
      "Strong signal/noise separation",
      "Maintains cognitive clarity under significant information load",
      "Good irreversibility awareness",
      "Decisions are well-reasoned and articulable"
    ],
    vulnerabilities: [
      "Emotional blind spots: emotional drivers are often invisible to you",
      "Tend to construct rational justifications for emotionally-driven decisions",
      "Room reading is underdeveloped relative to analytical capacity",
      "Can be slow to recognize destabilization in others"
    ]
  },
  {
    name: "The Stoic",
    range: [80, 99],
    band: "Average Crisis IQ",
    bandColor: "#8B6B2E",
    percentile: "Middle 30%",
    desc: "You maintain impressive personal stability under pressure. You don't destabilize easily. But this stability can create a specific blind spot: you assume the room is more rational than it is, and you make decisions as if others are as stable as you.",
    strengths: [
      "Personal emotional stability is a genuine asset",
      "Doesn't escalate under confrontation",
      "Consistent recovery speed after setbacks",
      "Reliable under sustained pressure over time"
    ],
    vulnerabilities: [
      "Systemic awareness gap: you miss the emotional state of others",
      "Decisions are made as if the decision environment is neutral when it rarely is",
      "Can be perceived as cold or disconnected in high-emotion situations",
      "Urgency calibration is sometimes too conservative"
    ]
  },
  {
    name: "The Reactor",
    range: [60, 79],
    band: "Below Average Crisis IQ",
    bandColor: "#8B4A2E",
    percentile: "Bottom 20%",
    desc: "You are fast, energetic, and decisive — qualities that work well in stable conditions. Under genuine crisis pressure, these same qualities become liabilities. You make decisions to reduce discomfort rather than to maximize outcomes.",
    strengths: [
      "High decisiveness — you don't freeze",
      "Energizes rooms in low-pressure situations",
      "Fast action when speed genuinely matters",
      "Resilient — you don't dwell on past decisions"
    ],
    vulnerabilities: [
      "Decision quality drops significantly under emotional pressure",
      "Urgency pressure consistently distorts your assessment of timelines",
      "Long-horizon thinking disappears under acute pressure",
      "Often unaware of your own emotional state while in it"
    ]
  },
  {
    name: "The Frozen",
    range: [0, 59],
    band: "Crisis Vulnerable",
    bandColor: "#8B2E2E",
    percentile: "Bottom 5%",
    desc: "High intelligence, strong knowledge base — and a decision-making architecture that fails under pressure. The crisis conditions that reveal Crisis IQ are exactly the conditions where your capacity is most compromised. This is trainable.",
    strengths: [
      "Intellectual capacity is intact and often exceptional",
      "Careful and thorough in stable conditions",
      "Low risk of impulsive decisions",
      "Often excellent at retrospective analysis"
    ],
    vulnerabilities: [
      "Paralysis under time pressure — waiting for information that won't come",
      "High emotional reactivity to setbacks affects subsequent decisions",
      "Urgency pressure reliably distorts both assessment and response",
      "Significant gap between decision quality in stable vs. crisis conditions"
    ]
  }
];

// ============================================================
// STATE
// ============================================================

let current = 0;
let answers = new Array(questions.length).fill(null);

const dimNames = {
  1: "Cognitive Stability",
  2: "Emotional Architecture",
  3: "Temporal Intelligence",
  4: "Systemic Awareness"
};

// ============================================================
// NAVIGATION
// ============================================================

function startAssessment() {
  document.getElementById('screen-intro').classList.remove('active');
  document.getElementById('screen-question').classList.add('active');
  renderQuestion();
}

function renderQuestion() {
  const q = questions[current];
  const pct = Math.round((current / questions.length) * 100);

  document.getElementById('dim-label').textContent = dimNames[q.dim];
  document.getElementById('progress-fill').style.width = pct + '%';
  document.getElementById('progress-num').textContent = (current + 1) + ' / ' + questions.length;
  document.getElementById('q-type').textContent = q.type;
  document.getElementById('q-text').textContent = q.q;
  document.getElementById('q-context').textContent = q.context || '';
  document.getElementById('q-context').style.display = q.context ? 'block' : 'none';

  const opts = document.getElementById('q-options');
  opts.innerHTML = '';
  const letters = ['A','B','C','D'];

  q.options.forEach((opt, i) => {
    const div = document.createElement('div');
    div.className = 'q-option' + (answers[current] === i ? ' selected' : '');
    div.innerHTML = `<div class="opt-letter">${letters[i]}</div><div class="opt-text">${opt.text}</div>`;
    div.onclick = () => selectAnswer(i);
    opts.appendChild(div);
  });

  document.getElementById('btn-prev').disabled = current === 0;
  document.getElementById('nav-warn').classList.remove('visible');

  const body = document.getElementById('q-body');
  body.classList.remove('fade-in');
  void body.offsetWidth;
  body.classList.add('fade-in');
}

function selectAnswer(idx) {
  answers[current] = idx;
  document.querySelectorAll('.q-option').forEach((el, i) => {
    el.classList.toggle('selected', i === idx);
  });
  document.getElementById('nav-warn').classList.remove('visible');
}

function nextQ() {
  if (answers[current] === null) {
    document.getElementById('nav-warn').classList.add('visible');
    return;
  }
  if (current < questions.length - 1) {
    current++;
    renderQuestion();
  } else {
    showResults();
  }
}

function prevQ() {
  if (current > 0) { current--; renderQuestion(); }
}

// ============================================================
// SCORING
// ============================================================

function calcScores() {
  let dimScores = {1:0, 2:0, 3:0, 4:0};
  let dimMax = {1:0, 2:0, 3:0, 4:0};

  questions.forEach((q, i) => {
    if (answers[i] !== null) {
      dimScores[q.dim] += q.options[answers[i]].score;
      dimMax[q.dim] += 4;
    }
  });

  // Scale each dimension to 40
  let scaled = {};
  let total = 0;
  [1,2,3,4].forEach(d => {
    scaled[d] = dimMax[d] > 0 ? Math.round((dimScores[d] / dimMax[d]) * 40) : 0;
    total += scaled[d];
  });

  return { dims: scaled, total };
}

function getArchetype(score) {
  return archetypes.find(a => score >= a.range[0] && score <= a.range[1]) || archetypes[archetypes.length-1];
}

// ============================================================
// RESULTS
// ============================================================

function showResults() {
  document.getElementById('screen-question').classList.remove('active');
  const rs = document.getElementById('screen-results');
  rs.classList.add('active');

  const {dims, total} = calcScores();
  const arch = getArchetype(total);
  const now = new Date().toLocaleDateString('en-GB', {day:'numeric',month:'long',year:'numeric'});

  // Sub-scores (approximate from answer patterns)
  function subPips(dim, count) {
    const q = questions.filter(q => q.dim === dim);
    const dimAns = q.map((q,i) => {
      const globalIdx = questions.indexOf(q);
      return answers[globalIdx] !== null ? q.options[answers[globalIdx]].score : 2;
    });
    const avg = dimAns.reduce((a,b)=>a+b,0) / dimAns.length;
    const pips = Math.round((avg / 4) * 5);
    return Array.from({length:5}, (_,i) =>
      `<div class="sub-pip ${i < pips ? 'on' : ''}"></div>`
    ).join('');
  }

  rs.innerHTML = `
    <div class="results-header">
      <div class="intro-brand" style="margin-bottom:24px">
        <div class="brand-squares"><div class="bsq"></div><div class="bsq"></div><div class="bsq"></div></div>
        <div class="brand-text">Decision Protocol — Crisis IQ™</div>
      </div>
      <div class="results-eyebrow">Individual Assessment Report</div>
      <div class="results-name-row">
        <div class="results-title">Your Crisis IQ™<br>Results</div>
        <div class="results-date">${now}</div>
      </div>
    </div>

    <div class="score-hero">
      <div>
        <div class="score-number">${total}<span>/160</span></div>
      </div>
      <div class="score-right">
        <div class="score-band" style="background:${arch.bandColor}22;color:${arch.bandColor}">${arch.band}</div>
        <div class="score-archetype">${arch.name}</div>
        <div class="score-archetype-sub">${arch.desc}</div>
        <div class="score-percentile">Benchmark position: ${arch.percentile} of assessed professionals</div>
      </div>
    </div>

    <div class="dim-grid">
      ${[1,2,3,4].map(d => {
        const pct = Math.round((dims[d]/40)*100);
        return `
        <div class="dim-card">
          <div class="dim-card-label">Dimension ${d}</div>
          <div class="dim-card-name">${dimNames[d]}</div>
          <div class="dim-score-row">
            <div class="dim-score-num">${dims[d]}</div>
            <div class="dim-score-max">/40</div>
          </div>
          <div class="dim-bar"><div class="dim-bar-fill" style="width:${pct}%"></div></div>
          <div class="dim-insight">${getDimInsight(d, dims[d])}</div>
        </div>`;
      }).join('')}
    </div>

    <div class="archetype-section">
      <div class="arch-label">Your Archetype — Detailed Profile</div>
      <div class="arch-name">${arch.name}</div>
      <div class="arch-desc">${arch.desc}</div>
      <div class="arch-cols">
        <div>
          <div class="arch-col-label">Core Strengths</div>
          <div class="arch-col-items">
            ${arch.strengths.map(s => `<div class="arch-col-item">${s}</div>`).join('')}
          </div>
        </div>
        <div>
          <div class="arch-col-label">Development Areas</div>
          <div class="arch-col-items">
            ${arch.vulnerabilities.map(v => `<div class="arch-col-item">${v}</div>`).join('')}
          </div>
        </div>
      </div>
    </div>

    <div class="dev-plan">
      <div class="dev-plan-header">
        <div class="dev-plan-title">90-Day Development Plan</div>
        <div class="dev-plan-sub">Based on your lowest-scoring dimensions</div>
      </div>
      <div class="dev-grid">
        ${getDevPlan(dims)}
      </div>
    </div>

    <div class="next-steps">
      <div class="next-label">Next Steps</div>
      <div class="next-title">This is your baseline. Now build on it.</div>
      <div class="next-sub">Crisis IQ is trainable. Your score today is the starting point, not the ceiling. Three paths forward — each designed for a different level of commitment.</div>
      <div class="next-options">
        <div class="next-opt">
          <div class="next-opt-num">01</div>
          <div class="next-opt-title">Crisis IQ 360</div>
          <div class="next-opt-price">€650 — €950</div>
          <div class="next-opt-desc">See yourself through others' eyes. Multi-source assessment reveals the gap between your self-perception and your observed performance under pressure.</div>
        </div>
        <div class="next-opt">
          <div class="next-opt-num">02</div>
          <div class="next-opt-title">Crisis IQ Simulation</div>
          <div class="next-opt-price">€1.500 — €2.500</div>
          <div class="next-opt-desc">Your Crisis IQ observed in real conditions. Scenario-based full-day simulation with live scoring and a complete development debrief.</div>
        </div>
        <div class="next-opt">
          <div class="next-opt-num">03</div>
          <div class="next-opt-title">Decision Protocol Program</div>
          <div class="next-opt-price">By engagement</div>
          <div class="next-opt-desc">The complete Decision Stabilization program for individuals and organizations. Structured training with measurable Crisis IQ improvement over 90 days.</div>
        </div>
      </div>
      <button class="btn-cta" onclick="alert('Contact: decisionprotocol.com')">Book a 20-Minute Conversation →</button>
    </div>

    <div class="results-footer">
      <div class="rf-brand">Decision Protocol — © 2026</div>
      <div class="rf-note">Crisis IQ™ is a proprietary assessment. Results are confidential.</div>
    </div>
  `;

  // Animate bars after render
  setTimeout(() => {
    document.querySelectorAll('.dim-bar-fill').forEach(el => {
      el.style.transition = 'width 1s ease';
    });
  }, 100);
}

function getDimInsight(dim, score) {
  const pct = Math.round((score/40)*100);
  const insights = {
    1: {
      high: "<strong>Strong.</strong> You maintain cognitive clarity under significant information load. Signal/noise separation is a reliable capability.",
      mid: "<strong>Developing.</strong> Your analytical capacity holds under moderate pressure but shows signs of narrowing under extreme load.",
      low: "<strong>Priority area.</strong> Cognitive narrowing under pressure is significantly affecting your decision quality. This is your highest-leverage development opportunity."
    },
    2: {
      high: "<strong>Strong.</strong> The architecture between your emotional state and your decisions is well-developed. You feel without being governed by feeling.",
      mid: "<strong>Developing.</strong> Emotional drivers influence your decisions more than you currently recognize. The gap between perceived and actual emotional influence is worth examining.",
      low: "<strong>Priority area.</strong> Emotional states are significantly shaping decisions in ways that are largely invisible to you in the moment. High-impact development area."
    },
    3: {
      high: "<strong>Strong.</strong> Urgency calibration, irreversibility awareness, and pause competence are all well-developed. You manage time under pressure with discipline.",
      mid: "<strong>Developing.</strong> Short-term pressure consistently distorts your time horizon. You're aware of long-term consequences but struggle to protect them under acute pressure.",
      low: "<strong>Priority area.</strong> Temporal distortion under pressure is a consistent pattern. Urgency overrides importance, and irreversibility receives insufficient weight."
    },
    4: {
      high: "<strong>Strong.</strong> You read rooms, map influence, and anticipate cascades with accuracy that most professionals never develop. Your decisions account for the system, not just the problem.",
      mid: "<strong>Developing.</strong> You pick up on some systemic dynamics but miss others. Influence mapping and cascade anticipation have meaningful room for development.",
      low: "<strong>Priority area.</strong> Decision environment assessment is underdeveloped. You focus on the decision itself while the system around it — which often determines the outcome — receives insufficient attention."
    }
  };
  const level = pct >= 70 ? 'high' : pct >= 45 ? 'mid' : 'low';
  return insights[dim][level];
}

function getDevPlan(dims) {
  // Sort dims by score ascending to prioritize lowest
  const sorted = [1,2,3,4].sort((a,b) => dims[a]-dims[b]);
  const phases = [
    {label:"Days 1—30", title:"Foundation: Awareness", items:[
      {title:`${dimNames[sorted[0]]} — Primary Focus`, desc:`Your lowest dimension. Build awareness of when ${dimNames[sorted[0]].toLowerCase()} is failing you in real situations. Keep a decision log.`},
      {title:"Daily Baseline Check", desc:"5-minute morning check: rate your cognitive and emotional state before your first high-stakes interaction. Track patterns over 30 days."}
    ]},
    {label:"Days 31—60", title:"Practice: Intervention", items:[
      {title:`${dimNames[sorted[1]]} — Secondary Focus`, desc:`Target your second-lowest dimension with deliberate practice scenarios. One simulated high-pressure decision per week.`},
      {title:"Structured Pause Practice", desc:"In every non-critical decision, practice explicit pausing before responding. Build the muscle for when it matters."}
    ]},
    {label:"Days 61—90", title:"Integration: Performance", items:[
      {title:"Full Assessment Retest", desc:"Retake the Crisis IQ assessment. Expect meaningful improvement in primary focus areas. Identify the next development cycle."},
      {title:"360 Calibration", desc:"Ask two colleagues to assess your crisis decision performance. Compare against your self-assessment. Close the gap."}
    ]}
  ];

  return phases.map(p => `
    <div class="dev-phase">
      <div class="dev-phase-label">${p.label}</div>
      <div class="dev-phase-title">${p.title}</div>
      <div class="dev-items">
        ${p.items.map(i => `<div class="dev-item"><strong>${i.title}</strong>${i.desc}</div>`).join('')}
      </div>
    </div>
  `).join('');
}
</script>
</body>
</html>
