<!DOCTYPE html>

<html lang="en">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0, maximum-scale=1.0">
<meta name="theme-color" content="#0a0a0a">
<meta name="apple-mobile-web-app-capable" content="yes">
<meta name="apple-mobile-web-app-status-bar-style" content="black-translucent">
<title>DE CRM</title>
<link rel="manifest" href="#" id="manifest-link">
<style>
  @import url('https://fonts.googleapis.com/css2?family=IBM+Plex+Mono:wght@400;500&family=IBM+Plex+Sans:wght@300;400;500&display=swap');

:root {
–bg: #0d0d0d;
–bg2: #161616;
–bg3: #1f1f1f;
–border: #2a2a2a;
–border2: #383838;
–text: #e8e4dc;
–text2: #9a9690;
–text3: #5a5652;
–accent: #c8a96e;
–accent2: #8fb87a;
–danger: #c46a5a;
–warn: #d4935a;
–info: #5a8fc4;
–lead: #5a8fc4;
–bid: #9a78c8;
–awarded: #c8a96e;
–scheduled: #d4935a;
–complete: #8fb87a;
–radius: 4px;
–font-mono: ‘IBM Plex Mono’, monospace;
–font-sans: ‘IBM Plex Sans’, sans-serif;
}

- { box-sizing: border-box; margin: 0; padding: 0; -webkit-tap-highlight-color: transparent; }

body {
background: var(–bg);
color: var(–text);
font-family: var(–font-sans);
font-size: 14px;
min-height: 100vh;
max-width: 480px;
margin: 0 auto;
}

/* HEADER */
.app-header {
position: sticky;
top: 0;
z-index: 100;
background: var(–bg);
border-bottom: 1px solid var(–border);
padding: 12px 16px 10px;
display: flex;
align-items: center;
justify-content: space-between;
}
.app-logo {
font-family: var(–font-mono);
font-size: 13px;
font-weight: 500;
letter-spacing: 0.08em;
color: var(–accent);
text-transform: uppercase;
}
.app-logo span { color: var(–text3); }
.header-right { display: flex; gap: 8px; align-items: center; }

/* TABS */
.tabs {
display: flex;
border-bottom: 1px solid var(–border);
background: var(–bg);
position: sticky;
top: 45px;
z-index: 99;
}
.tab {
flex: 1;
padding: 10px 4px;
text-align: center;
font-family: var(–font-mono);
font-size: 10px;
letter-spacing: 0.06em;
text-transform: uppercase;
color: var(–text3);
cursor: pointer;
border-bottom: 2px solid transparent;
transition: all 0.15s;
position: relative;
}
.tab.active { color: var(–accent); border-bottom-color: var(–accent); }
.tab .badge {
position: absolute;
top: 6px;
right: calc(50% - 20px);
background: var(–danger);
color: #fff;
font-size: 9px;
min-width: 14px;
height: 14px;
border-radius: 7px;
display: flex;
align-items: center;
justify-content: center;
padding: 0 3px;
}

/* VIEWS */
.view { display: none; padding: 12px 16px 80px; }
.view.active { display: block; }

/* SECTION HEADER */
.section-header {
display: flex;
align-items: center;
justify-content: space-between;
margin-bottom: 12px;
}
.section-title {
font-family: var(–font-mono);
font-size: 10px;
letter-spacing: 0.1em;
text-transform: uppercase;
color: var(–text3);
}

/* BUTTONS */
.btn {
font-family: var(–font-mono);
font-size: 11px;
letter-spacing: 0.04em;
padding: 6px 14px;
border-radius: var(–radius);
border: 1px solid var(–border2);
background: var(–bg3);
color: var(–text);
cursor: pointer;
transition: all 0.12s;
}
.btn:active { opacity: 0.7; transform: scale(0.97); }
.btn-accent { background: var(–accent); color: #0d0d0d; border-color: var(–accent); font-weight: 500; }
.btn-sm { padding: 4px 10px; font-size: 10px; }
.btn-danger { border-color: var(–danger); color: var(–danger); background: transparent; }
.btn-ghost { background: transparent; border-color: transparent; color: var(–text2); }

/* CLIENT CARD */
.client-card {
background: var(–bg2);
border: 1px solid var(–border);
border-radius: var(–radius);
padding: 14px;
margin-bottom: 8px;
cursor: pointer;
transition: border-color 0.12s;
position: relative;
}
.client-card:active { border-color: var(–border2); }
.client-card.overdue { border-left: 3px solid var(–danger); }
.client-card-top {
display: flex;
align-items: flex-start;
justify-content: space-between;
margin-bottom: 8px;
}
.client-name {
font-size: 15px;
font-weight: 500;
color: var(–text);
line-height: 1.2;
}
.client-meta {
font-family: var(–font-mono);
font-size: 11px;
color: var(–text2);
margin-top: 3px;
}
.client-card-bottom {
display: flex;
align-items: center;
justify-content: space-between;
margin-top: 10px;
}

/* TAGS / BADGES */
.tag {
display: inline-flex;
align-items: center;
font-family: var(–font-mono);
font-size: 10px;
letter-spacing: 0.04em;
padding: 2px 8px;
border-radius: 2px;
text-transform: uppercase;
}
.tag-type-homeowner { background: #1a2030; color: var(–info); border: 1px solid #253050; }
.tag-type-gc { background: #201a30; color: #a08cd4; border: 1px solid #352550; }
.tag-type-municipality { background: #1a2820; color: var(–accent2); border: 1px solid #253c28; }
.tag-type-lead { background: #2a2a20; color: var(–accent); border: 1px solid #3a3828; }

/* PIPELINE STATUS */
.status-pill {
display: inline-flex;
align-items: center;
font-family: var(–font-mono);
font-size: 10px;
letter-spacing: 0.03em;
padding: 3px 9px;
border-radius: 2px;
text-transform: uppercase;
gap: 5px;
}
.status-pill::before {
content: ‘’;
width: 5px;
height: 5px;
border-radius: 50%;
flex-shrink: 0;
}
.status-Lead { background: #151e2a; color: var(–lead); border: 1px solid #1e2e3d; }
.status-Lead::before { background: var(–lead); }
.status-Bid-Sent { background: #1e1828; color: var(–bid); border: 1px solid #2e2040; }
.status-Bid-Sent::before { background: var(–bid); }
.status-Awarded { background: #28220f; color: var(–awarded); border: 1px solid #3a3015; }
.status-Awarded::before { background: var(–awarded); }
.status-Scheduled { background: #281d10; color: var(–scheduled); border: 1px solid #3a2a15; }
.status-Scheduled::before { background: var(–scheduled); }
.status-Complete { background: #182218; color: var(–complete); border: 1px solid #223022; }
.status-Complete::before { background: var(–complete); }

/* CALLBACK FLAG */
.callback-flag {
display: flex;
align-items: center;
gap: 5px;
font-family: var(–font-mono);
font-size: 10px;
color: var(–text3);
}
.callback-flag.overdue { color: var(–danger); }
.callback-flag.today { color: var(–warn); }
.callback-flag.upcoming { color: var(–text2); }

/* PIPELINE VIEW */
.pipeline-stage {
margin-bottom: 20px;
}
.pipeline-stage-header {
display: flex;
align-items: center;
gap: 8px;
margin-bottom: 8px;
padding-bottom: 6px;
border-bottom: 1px solid var(–border);
}
.stage-dot {
width: 7px;
height: 7px;
border-radius: 50%;
flex-shrink: 0;
}
.stage-label {
font-family: var(–font-mono);
font-size: 10px;
letter-spacing: 0.08em;
text-transform: uppercase;
color: var(–text2);
flex: 1;
}
.stage-count {
font-family: var(–font-mono);
font-size: 10px;
color: var(–text3);
}

/* CALLBACKS VIEW */
.callback-item {
background: var(–bg2);
border: 1px solid var(–border);
border-radius: var(–radius);
padding: 12px 14px;
margin-bottom: 8px;
display: flex;
align-items: center;
gap: 12px;
}
.callback-item.overdue { border-left: 3px solid var(–danger); background: #1a1210; }
.callback-item.today { border-left: 3px solid var(–warn); background: #1a1510; }
.callback-left { flex: 1; min-width: 0; }
.callback-name { font-size: 14px; font-weight: 500; color: var(–text); margin-bottom: 2px; }
.callback-reason { font-size: 12px; color: var(–text2); white-space: nowrap; overflow: hidden; text-overflow: ellipsis; }
.callback-date-label {
font-family: var(–font-mono);
font-size: 11px;
text-align: right;
line-height: 1.4;
flex-shrink: 0;
}
.callback-actions { display: flex; gap: 6px; flex-shrink: 0; }

/* MODAL */
.modal-overlay {
display: none;
position: fixed;
inset: 0;
background: rgba(0,0,0,0.75);
z-index: 200;
align-items: flex-end;
justify-content: center;
}
.modal-overlay.open { display: flex; }
.modal {
background: var(–bg2);
border-top: 1px solid var(–border2);
border-radius: 8px 8px 0 0;
width: 100%;
max-width: 480px;
max-height: 92vh;
overflow-y: auto;
padding: 0 0 32px;
animation: slideUp 0.2s ease;
}
@keyframes slideUp { from { transform: translateY(60px); opacity: 0; } to { transform: translateY(0); opacity: 1; } }
.modal-drag { width: 36px; height: 4px; background: var(–border2); border-radius: 2px; margin: 10px auto 14px; }
.modal-title {
font-family: var(–font-mono);
font-size: 11px;
letter-spacing: 0.08em;
text-transform: uppercase;
color: var(–text3);
padding: 0 16px 12px;
border-bottom: 1px solid var(–border);
margin-bottom: 16px;
}

/* FORMS */
.form-section { padding: 0 16px; margin-bottom: 20px; }
.form-label {
display: block;
font-family: var(–font-mono);
font-size: 10px;
letter-spacing: 0.07em;
text-transform: uppercase;
color: var(–text3);
margin-bottom: 6px;
}
.form-input, .form-select, .form-textarea {
width: 100%;
background: var(–bg3);
border: 1px solid var(–border);
border-radius: var(–radius);
color: var(–text);
font-family: var(–font-sans);
font-size: 14px;
padding: 9px 12px;
outline: none;
transition: border-color 0.12s;
appearance: none;
}
.form-input:focus, .form-select:focus, .form-textarea:focus { border-color: var(–accent); }
.form-textarea { resize: vertical; min-height: 72px; line-height: 1.5; }
.form-select { background-image: url(“data:image/svg+xml,%3Csvg xmlns=‘http://www.w3.org/2000/svg’ width=‘10’ height=‘6’ fill=‘none’%3E%3Cpath d=‘M1 1l4 4 4-4’ stroke=’%235a5652’ stroke-width=‘1.5’ stroke-linecap=‘round’/%3E%3C/svg%3E”); background-repeat: no-repeat; background-position: right 12px center; padding-right: 32px; }
.form-row { display: grid; grid-template-columns: 1fr 1fr; gap: 10px; }
.form-actions { padding: 0 16px; display: flex; gap: 8px; margin-top: 8px; }
.form-actions .btn { flex: 1; padding: 11px; text-align: center; }

/* DETAIL MODAL */
.detail-field { margin-bottom: 14px; }
.detail-field-label {
font-family: var(–font-mono);
font-size: 10px;
letter-spacing: 0.07em;
text-transform: uppercase;
color: var(–text3);
margin-bottom: 4px;
}
.detail-field-value { font-size: 14px; color: var(–text); line-height: 1.5; }
.detail-actions { display: flex; flex-wrap: wrap; gap: 8px; padding: 0 16px 4px; }

/* NOTES */
.note-item {
background: var(–bg3);
border-radius: var(–radius);
padding: 10px 12px;
margin-bottom: 6px;
}
.note-text { font-size: 13px; color: var(–text); line-height: 1.5; margin-bottom: 4px; }
.note-ts { font-family: var(–font-mono); font-size: 10px; color: var(–text3); }

/* STAT CARDS */
.stats-row {
display: grid;
grid-template-columns: repeat(3, minmax(0, 1fr));
gap: 8px;
margin-bottom: 16px;
}
.stat-card {
background: var(–bg2);
border: 1px solid var(–border);
border-radius: var(–radius);
padding: 10px 12px;
text-align: center;
}
.stat-num {
font-family: var(–font-mono);
font-size: 22px;
font-weight: 500;
color: var(–text);
line-height: 1.1;
}
.stat-label {
font-family: var(–font-mono);
font-size: 9px;
letter-spacing: 0.06em;
text-transform: uppercase;
color: var(–text3);
margin-top: 3px;
}
.stat-accent { border-color: #3a3015; }
.stat-accent .stat-num { color: var(–accent); }

/* EMPTY STATE */
.empty-state {
text-align: center;
padding: 40px 20px;
color: var(–text3);
font-family: var(–font-mono);
font-size: 12px;
letter-spacing: 0.04em;
}

/* SYNC STATUS */
.sync-bar {
font-family: var(–font-mono);
font-size: 10px;
color: var(–text3);
text-align: center;
padding: 6px;
letter-spacing: 0.04em;
}
.sync-bar.syncing { color: var(–accent); }
.sync-bar.error { color: var(–danger); }

/* FAB */
.fab {
position: fixed;
bottom: 24px;
right: 20px;
width: 52px;
height: 52px;
border-radius: 50%;
background: var(–accent);
color: #0d0d0d;
font-size: 24px;
font-weight: 300;
border: none;
cursor: pointer;
display: flex;
align-items: center;
justify-content: center;
box-shadow: 0 4px 16px rgba(200,169,110,0.3);
transition: transform 0.12s, opacity 0.12s;
z-index: 50;
line-height: 1;
}
.fab:active { transform: scale(0.93); }

/* SEARCH */
.search-wrap { margin-bottom: 12px; position: relative; }
.search-input {
width: 100%;
background: var(–bg2);
border: 1px solid var(–border);
border-radius: var(–radius);
color: var(–text);
font-family: var(–font-sans);
font-size: 14px;
padding: 9px 12px 9px 34px;
outline: none;
}
.search-input:focus { border-color: var(–border2); }
.search-icon {
position: absolute;
left: 11px;
top: 50%;
transform: translateY(-50%);
color: var(–text3);
font-size: 14px;
pointer-events: none;
}

/* DIVIDER */
.divider { height: 1px; background: var(–border); margin: 14px 0; }

/* PHONE LINK */
a.phone-link { color: var(–info); text-decoration: none; font-family: var(–font-mono); font-size: 13px; }

/* PROGRESS BAR */
.progress-bar-wrap {
margin-top: 10px;
background: var(–bg3);
border-radius: 2px;
height: 4px;
overflow: hidden;
}
.progress-bar-fill {
height: 100%;
border-radius: 2px;
background: var(–accent2);
transition: width 0.3s ease;
}
.progress-label {
font-family: var(–font-mono);
font-size: 10px;
color: var(–text3);
margin-top: 4px;
display: flex;
justify-content: space-between;
}

/* PROGRESS CHECKLIST */
.progress-stage {
border: 1px solid var(–border);
border-radius: var(–radius);
margin-bottom: 6px;
overflow: hidden;
background: var(–bg3);
}
.progress-stage-header {
display: flex;
align-items: center;
gap: 10px;
padding: 10px 12px;
cursor: pointer;
}
.progress-stage-header:active { opacity: 0.8; }
.progress-check {
width: 20px;
height: 20px;
border-radius: 50%;
border: 1.5px solid var(–border2);
display: flex;
align-items: center;
justify-content: center;
flex-shrink: 0;
transition: all 0.15s;
font-size: 11px;
color: transparent;
}
.progress-check.done {
background: var(–accent2);
border-color: var(–accent2);
color: #0d0d0d;
}
.progress-stage-label {
flex: 1;
font-size: 13px;
color: var(–text);
line-height: 1.2;
}
.progress-stage-label.done { color: var(–text3); text-decoration: line-through; }
.progress-stage-ts {
font-family: var(–font-mono);
font-size: 9px;
color: var(–text3);
text-align: right;
flex-shrink: 0;
}
.progress-stage-body {
border-top: 1px solid var(–border);
padding: 8px 12px;
display: none;
background: var(–bg2);
}
.progress-stage-body.open { display: block; }
.progress-stage-note {
font-size: 12px;
color: var(–text2);
line-height: 1.5;
margin-bottom: 8px;
font-style: italic;
}
.progress-note-input-row {
display: flex;
gap: 6px;
}

/* PROGRESS VIEW (tab) */
.progress-client-card {
background: var(–bg2);
border: 1px solid var(–border);
border-radius: var(–radius);
padding: 12px 14px;
margin-bottom: 8px;
cursor: pointer;
}
.progress-client-card:active { border-color: var(–border2); }
.pccard-top { display: flex; align-items: center; justify-content: space-between; margin-bottom: 6px; }
.pccard-name { font-size: 14px; font-weight: 500; color: var(–text); }
.pccard-pct { font-family: var(–font-mono); font-size: 12px; color: var(–accent2); }
.pccard-stage { font-family: var(–font-mono); font-size: 10px; color: var(–text3); margin-top: 4px; }

/* PDF EXPORT */
@media print {
body { background: #fff !important; color: #000 !important; max-width: 100%; font-family: ‘IBM Plex Sans’, sans-serif; }
.app-header, .tabs, .fab, .detail-actions, .progress-note-input-row, .btn, #noteInput_x { display: none !important; }
.modal-overlay { position: static !important; background: none !important; display: block !important; }
.modal { border-radius: 0 !important; border: none !important; max-height: none !important; padding: 0 !important; }
.pdf-export-sheet { display: block !important; }
* { color: #000 !important; background: #fff !important; border-color: #ccc !important; }
.pdf-header { border-bottom: 2px solid #000 !important; margin-bottom: 16px; padding-bottom: 12px; }
.pdf-section-title { font-weight: bold; font-size: 11px; letter-spacing: 0.1em; text-transform: uppercase; border-bottom: 1px solid #ccc; padding-bottom: 4px; margin: 16px 0 8px; }
.pdf-field { margin-bottom: 8px; font-size: 13px; }
.pdf-field-label { font-weight: bold; font-size: 10px; text-transform: uppercase; letter-spacing: 0.05em; color: #666 !important; }
.pdf-stage-row { display: flex; align-items: flex-start; gap: 10px; padding: 6px 0; border-bottom: 1px solid #eee; font-size: 12px; }
.pdf-check { width: 14px; height: 14px; border: 1.5px solid #999; border-radius: 50%; flex-shrink: 0; margin-top: 1px; display: flex; align-items: center; justify-content: center; font-size: 10px; }
.pdf-check.done { background: #000 !important; color: #fff !important; border-color: #000 !important; }
.pdf-note-item { background: #f8f8f8 !important; border-left: 3px solid #ccc !important; padding: 6px 10px; margin-bottom: 6px; font-size: 12px; }
}
.pdf-export-sheet { display: none; }

.overdue-banner {
background: #1f1008;
border: 1px solid #3a2015;
border-radius: var(–radius);
padding: 10px 14px;
margin-bottom: 12px;
display: flex;
align-items: center;
gap: 10px;
cursor: pointer;
}
.overdue-dot { width: 8px; height: 8px; border-radius: 50%; background: var(–danger); flex-shrink: 0; animation: pulse 1.5s infinite; }
@keyframes pulse { 0%,100%{opacity:1} 50%{opacity:0.4} }
.overdue-text { font-family: var(–font-mono); font-size: 11px; color: var(–warn); flex: 1; }
.overdue-arrow { color: var(–text3); font-size: 12px; }
</style>

</head>
<body>

<header class="app-header">
  <div class="app-logo">DE<span>/</span>CRM</div>
  <div class="header-right">
    <div class="sync-bar" id="syncStatus">local</div>
    <button class="btn btn-sm" id="syncBtn" onclick="manualSync()" title="Sync to Sheets">⇅</button>
    <button class="btn btn-sm" onclick="openSettings()">⚙</button>
  </div>
</header>

<nav class="tabs">
  <div class="tab active" data-tab="clients" onclick="switchTab('clients')">Clients</div>
  <div class="tab" data-tab="pipeline" onclick="switchTab('pipeline')">Pipeline</div>
  <div class="tab" data-tab="callbacks" onclick="switchTab('callbacks')">Callbacks <span class="badge" id="callbackBadge" style="display:none">0</span></div>
  <div class="tab" data-tab="progress" onclick="switchTab('progress')">Progress</div>
</nav>

<!-- CLIENTS VIEW -->

<div class="view active" id="view-clients">
  <div class="search-wrap">
    <span class="search-icon">⌕</span>
    <input class="search-input" type="text" id="clientSearch" placeholder="Search clients..." oninput="renderClients()">
  </div>
  <div id="overdueBanner" style="display:none" class="overdue-banner" onclick="switchTab('callbacks')">
    <div class="overdue-dot"></div>
    <div class="overdue-text" id="overdueBannerText"></div>
    <div class="overdue-arrow">→</div>
  </div>
  <div class="stats-row" id="statsRow"></div>
  <div id="clientsList"></div>
</div>

<!-- PIPELINE VIEW -->

<div class="view" id="view-pipeline">
  <div id="pipelineView"></div>
</div>

<!-- CALLBACKS VIEW -->

<div class="view" id="view-callbacks">
  <div class="section-header">
    <div class="section-title">Pending Callbacks</div>
    <button class="btn btn-sm btn-accent" onclick="openEmailAll()">Email All Overdue</button>
  </div>
  <div id="callbacksList"></div>
</div>

<!-- PROGRESS VIEW -->

<div class="view" id="view-progress">
  <div class="section-header">
    <div class="section-title">Job Progress</div>
    <div style="font-family:var(--font-mono);font-size:10px;color:var(--text3)">Tap job to update</div>
  </div>
  <div id="progressList"></div>
</div>

<button class="fab" onclick="openAddClient()">+</button>

<!-- ADD/EDIT CLIENT MODAL -->

<div class="modal-overlay" id="clientModal">
  <div class="modal">
    <div class="modal-drag"></div>
    <div class="modal-title" id="clientModalTitle">New Client</div>
    <div class="form-section">
      <label class="form-label">Name</label>
      <input class="form-input" type="text" id="f_name" placeholder="Full name or company">
    </div>
    <div class="form-section">
      <div class="form-row">
        <div>
          <label class="form-label">Type</label>
          <select class="form-select" id="f_type">
            <option>Homeowner</option>
            <option>GC</option>
            <option>Municipality</option>
            <option>Lead</option>
          </select>
        </div>
        <div>
          <label class="form-label">Status</label>
          <select class="form-select" id="f_status">
            <option>Lead</option>
            <option>Bid Sent</option>
            <option>Awarded</option>
            <option>Scheduled</option>
            <option>Complete</option>
          </select>
        </div>
      </div>
    </div>
    <div class="form-section">
      <label class="form-label">Phone</label>
      <input class="form-input" type="tel" id="f_phone" placeholder="701-000-0000">
    </div>
    <div class="form-section">
      <label class="form-label">Email</label>
      <input class="form-input" type="email" id="f_email" placeholder="email@example.com">
    </div>
    <div class="form-section">
      <label class="form-label">Location / Job Site</label>
      <input class="form-input" type="text" id="f_location" placeholder="Township, county, or address">
    </div>
    <div class="form-section">
      <label class="form-label">Job Description</label>
      <textarea class="form-textarea" id="f_jobdesc" placeholder="Septic install, excavation, waterline, etc."></textarea>
    </div>
    <div class="form-section">
      <label class="form-label">Callback Date</label>
      <input class="form-input" type="date" id="f_callback">
    </div>
    <div class="form-section">
      <label class="form-label">Callback Reason</label>
      <input class="form-input" type="text" id="f_callbackReason" placeholder="Follow up on bid, confirm schedule, etc.">
    </div>
    <div class="form-section">
      <label class="form-label">Estimated Value ($)</label>
      <input class="form-input" type="number" id="f_value" placeholder="0">
    </div>
    <div class="form-section">
      <label class="form-label">Note</label>
      <textarea class="form-textarea" id="f_note" placeholder="Add a note (optional)"></textarea>
    </div>
    <div class="form-actions">
      <button class="btn" onclick="closeModal('clientModal')">Cancel</button>
      <button class="btn btn-accent" id="clientSaveBtn" onclick="saveClient()">Save Client</button>
    </div>
  </div>
</div>

<!-- CLIENT DETAIL MODAL -->

<div class="modal-overlay" id="detailModal">
  <div class="modal">
    <div class="modal-drag"></div>
    <div id="detailContent"></div>
  </div>
</div>

<!-- REMINDER PICKER MODAL -->

<div class="modal-overlay" id="reminderModal">
  <div class="modal">
    <div class="modal-drag"></div>
    <div class="modal-title">Schedule Reminder</div>
    <div class="form-section">
      <div id="reminderClientName" style="font-size:15px;font-weight:500;color:var(--text);margin-bottom:14px"></div>
      <label class="form-label">Date</label>
      <input class="form-input" type="date" id="r_date" style="margin-bottom:12px">
      <label class="form-label">Time</label>
      <input class="form-input" type="time" id="r_time" value="08:00">
      <p style="font-family:var(--font-mono);font-size:10px;color:var(--text3);margin-top:8px;line-height:1.6">
        Adds to Apple Calendar with an 8:00 AM alert on the day of the reminder.
      </p>
    </div>
    <div class="form-actions">
      <button class="btn" onclick="closeModal('reminderModal')">Cancel</button>
      <button class="btn btn-accent" onclick="generateICS()">Add to Calendar</button>
    </div>
  </div>
</div>

<!-- SETTINGS MODAL -->

<div class="modal-overlay" id="settingsModal">
  <div class="modal">
    <div class="modal-drag"></div>
    <div class="modal-title">Settings</div>
    <div class="form-section">
      <label class="form-label">Google Sheets Web App URL</label>
      <input class="form-input" type="url" id="s_sheetUrl" placeholder="https://script.google.com/macros/s/...">
      <p style="font-family:var(--font-mono);font-size:10px;color:var(--text3);margin-top:6px;line-height:1.5;">Paste your Apps Script deployment URL to enable Sheets sync.</p>
    </div>
    <div class="form-section">
      <label class="form-label">Your Email (for callback reminders)</label>
      <input class="form-input" type="email" id="s_email" placeholder="you@example.com">
    </div>
    <div class="form-actions">
      <button class="btn" onclick="closeModal('settingsModal')">Cancel</button>
      <button class="btn btn-accent" onclick="saveSettings()">Save</button>
    </div>
  </div>
</div>

<script>
// ─── DATA LAYER ────────────────────────────────────────────────────────────
let clients = [];
let editingId = null;
const STAGES = ['Lead','Bid Sent','Awarded','Scheduled','Complete'];
const STAGE_COLORS = {
  'Lead': '#5a8fc4',
  'Bid Sent': '#9a78c8',
  'Awarded': '#c8a96e',
  'Scheduled': '#d4935a',
  'Complete': '#8fb87a'
};

function load() {
  try { clients = JSON.parse(localStorage.getItem('de_crm_clients') || '[]'); } catch(e) { clients = []; }
}
function save() {
  localStorage.setItem('de_crm_clients', JSON.stringify(clients));
  syncToSheets();
}

// ─── HARDCODED CONFIG ──────────────────────────────────────────────────────
const DEFAULT_SHEET_URL = 'https://script.google.com/macros/s/AKfycbyFZtb59RLkeTjfUA8WsL9c0X_SV0DgTRzwKvB6uI5igQ1piRWLwljdYvj9zpUEJrg7/exec';
const DEFAULT_EMAIL     = 'Info@dakotaearthworks.com';

function getSettings() {
  try {
    const s = JSON.parse(localStorage.getItem('de_crm_settings') || '{}');
    return {
      sheetUrl: s.sheetUrl || DEFAULT_SHEET_URL,
      email:    s.email    || DEFAULT_EMAIL
    };
  } catch(e) {
    return { sheetUrl: DEFAULT_SHEET_URL, email: DEFAULT_EMAIL };
  }
}
function saveSettings() {
  const s = { sheetUrl: document.getElementById('s_sheetUrl').value.trim() || DEFAULT_SHEET_URL, email: document.getElementById('s_email').value.trim() || DEFAULT_EMAIL };
  localStorage.setItem('de_crm_settings', JSON.stringify(s));
  closeModal('settingsModal');
  setSyncStatus('saved');
}
function openSettings() {
  const s = getSettings();
  document.getElementById('s_sheetUrl').value = s.sheetUrl;
  document.getElementById('s_email').value = s.email;
  openModal('settingsModal');
}

// ─── SHEETS SYNC ───────────────────────────────────────────────────────────
async function syncToSheets() {
  const s = getSettings();
  if (!s.sheetUrl) return;
  setSyncStatus('syncing');
  try {
    await fetch(s.sheetUrl, {
      method: 'POST',
      mode: 'no-cors',
      headers: { 'Content-Type': 'application/json' },
      body: JSON.stringify({ action: 'sync', clients: clients })
    });
    setSyncStatus('synced');
    localStorage.setItem('de_crm_last_sync', new Date().toISOString());
  } catch(e) {
    setSyncStatus('error');
  }
}
async function manualSync() {
  const btn = document.getElementById('syncBtn');
  btn.disabled = true;
  await syncToSheets();
  btn.disabled = false;
}
function setSyncStatus(state) {
  const el = document.getElementById('syncStatus');
  el.className = 'sync-bar';
  if (state === 'syncing') { el.textContent = 'syncing…'; el.classList.add('syncing'); }
  else if (state === 'synced') { el.textContent = '✓ synced'; setTimeout(()=>{ el.textContent='local'; }, 2500); }
  else if (state === 'error') { el.textContent = 'sync err'; el.classList.add('error'); }
  else { el.textContent = 'local'; }
}

// ─── UTILS ─────────────────────────────────────────────────────────────────
function uid() { return Date.now().toString(36) + Math.random().toString(36).slice(2,6); }
function today() { return new Date().toISOString().split('T')[0]; }
function fmtDate(d) {
  if (!d) return '';
  const [y,m,day] = d.split('-');
  return `${m}/${day}/${y.slice(2)}`;
}
function callbackStatus(dateStr) {
  if (!dateStr) return null;
  const t = today();
  if (dateStr < t) return 'overdue';
  if (dateStr === t) return 'today';
  return 'upcoming';
}
function daysUntil(dateStr) {
  if (!dateStr) return null;
  const diff = Math.round((new Date(dateStr) - new Date(today())) / 86400000);
  return diff;
}

// ─── TABS ──────────────────────────────────────────────────────────────────
function switchTab(tab) {
  document.querySelectorAll('.tab').forEach(t => t.classList.toggle('active', t.dataset.tab === tab));
  document.querySelectorAll('.view').forEach(v => v.classList.toggle('active', v.id === 'view-' + tab));
  if (tab === 'clients') renderClients();
  if (tab === 'pipeline') renderPipeline();
  if (tab === 'progress') renderProgressView();
}

// ─── CLIENTS VIEW ──────────────────────────────────────────────────────────
function renderClients() {
  const q = document.getElementById('clientSearch').value.toLowerCase();
  let list = clients.filter(c =>
    c.name.toLowerCase().includes(q) ||
    (c.location||'').toLowerCase().includes(q) ||
    (c.type||'').toLowerCase().includes(q)
  );
  list = list.slice().sort((a,b) => {
    const ao = callbackStatus(a.callback) === 'overdue' ? 0 : 1;
    const bo = callbackStatus(b.callback) === 'overdue' ? 0 : 1;
    return ao - bo || a.name.localeCompare(b.name);
  });

  // Stats
  const active = clients.filter(c => c.status !== 'Complete').length;
  const awarded = clients.filter(c => c.status === 'Awarded' || c.status === 'Scheduled').length;
  const totalVal = clients.filter(c => c.status !== 'Complete').reduce((s,c) => s + (parseFloat(c.value)||0), 0);
  document.getElementById('statsRow').innerHTML = `
    <div class="stat-card"><div class="stat-num">${clients.length}</div><div class="stat-label">Clients</div></div>
    <div class="stat-card"><div class="stat-num">${active}</div><div class="stat-label">Active</div></div>
    <div class="stat-card stat-accent"><div class="stat-num">$${totalVal >= 1000 ? (totalVal/1000).toFixed(0)+'k' : totalVal.toFixed(0)}</div><div class="stat-label">Pipeline</div></div>
  `;

  // Overdue banner
  const overdue = clients.filter(c => callbackStatus(c.callback) === 'overdue');
  const banner = document.getElementById('overdueBanner');
  if (overdue.length) {
    banner.style.display = 'flex';
    document.getElementById('overdueBannerText').textContent = `${overdue.length} overdue callback${overdue.length > 1 ? 's' : ''} — tap to review`;
  } else {
    banner.style.display = 'none';
  }

  // Badge
  const allPending = clients.filter(c => callbackStatus(c.callback) === 'overdue' || callbackStatus(c.callback) === 'today');
  const badge = document.getElementById('callbackBadge');
  if (allPending.length) { badge.style.display = 'flex'; badge.textContent = allPending.length; } else { badge.style.display = 'none'; }

  // List
  const el = document.getElementById('clientsList');
  if (!list.length) { el.innerHTML = '<div class="empty-state">No clients yet.<br>Tap + to add one.</div>'; return; }
  el.innerHTML = list.map(c => {
    const cs = callbackStatus(c.callback);
    const statusClass = c.status.replace(' ','-');
    let cbHtml = '';
    if (cs === 'overdue') cbHtml = `<div class="callback-flag overdue">⚑ Overdue ${fmtDate(c.callback)}</div>`;
    else if (cs === 'today') cbHtml = `<div class="callback-flag today">⚑ Today</div>`;
    else if (cs === 'upcoming') cbHtml = `<div class="callback-flag upcoming">↻ ${fmtDate(c.callback)}</div>`;
    return `
    <div class="client-card ${cs === 'overdue' ? 'overdue' : ''}" onclick="openDetail('${c.id}')">
      <div class="client-card-top">
        <div>
          <div class="client-name">${c.name}</div>
          <div class="client-meta">${c.location || '—'}</div>
        </div>
        <span class="tag tag-type-${c.type.toLowerCase()}">${c.type}</span>
      </div>
      ${c.jobdesc ? `<div style="font-size:12px;color:var(--text2);margin-bottom:8px;line-height:1.4">${c.jobdesc}</div>` : ''}
      ${(() => { const pct = jobProgressPct(c); return pct > 0 ? `<div class="progress-bar-wrap"><div class="progress-bar-fill" style="width:${pct}%"></div></div><div class="progress-label"><span>${nextStageName(c)}</span><span>${pct}%</span></div>` : ''; })()}
      <div class="client-card-bottom">
        <span class="status-pill status-${statusClass}">${c.status}</span>
        ${cbHtml}
        ${c.value ? `<span style="font-family:var(--font-mono);font-size:11px;color:var(--text3)">$${Number(c.value).toLocaleString()}</span>` : ''}
      </div>
    </div>`;
  }).join('');
}

// ─── PIPELINE VIEW ─────────────────────────────────────────────────────────
function renderPipeline() {
  const el = document.getElementById('pipelineView');
  const totalActive = clients.filter(c => c.status !== 'Complete');
  const totalVal = totalActive.reduce((s,c) => s + (parseFloat(c.value)||0), 0);
  let html = `<div class="stats-row" style="grid-template-columns:1fr 1fr;margin-bottom:16px">
    <div class="stat-card"><div class="stat-num">${totalActive.length}</div><div class="stat-label">Active Jobs</div></div>
    <div class="stat-card stat-accent"><div class="stat-num">$${totalVal >= 1000 ? (totalVal/1000).toFixed(0)+'k' : totalVal.toFixed(0)}</div><div class="stat-label">Total Value</div></div>
  </div>`;
  STAGES.forEach(stage => {
    const group = clients.filter(c => c.status === stage);
    const color = STAGE_COLORS[stage];
    html += `<div class="pipeline-stage">
      <div class="pipeline-stage-header">
        <div class="stage-dot" style="background:${color}"></div>
        <div class="stage-label">${stage}</div>
        <div class="stage-count">${group.length}</div>
      </div>`;
    if (!group.length) {
      html += `<div style="font-family:var(--font-mono);font-size:10px;color:var(--text3);padding:8px 0 4px">—</div>`;
    } else {
      group.forEach(c => {
        html += `<div class="client-card" onclick="openDetail('${c.id}')" style="margin-bottom:6px;padding:10px 14px">
          <div style="display:flex;align-items:center;justify-content:space-between">
            <div>
              <div class="client-name" style="font-size:14px">${c.name}</div>
              <div class="client-meta">${c.location||'—'}</div>
            </div>
            ${c.value ? `<span style="font-family:var(--font-mono);font-size:12px;color:var(--accent)">$${Number(c.value).toLocaleString()}</span>` : ''}
          </div>
        </div>`;
      });
    }
    html += '</div>';
  });
  el.innerHTML = html;
}

// ─── CALLBACKS VIEW ────────────────────────────────────────────────────────
function renderCallbacks() {
  const pending = clients
    .filter(c => c.callback && callbackStatus(c.callback) !== null)
    .sort((a,b) => a.callback.localeCompare(b.callback));
  const el = document.getElementById('callbacksList');
  if (!pending.length) { el.innerHTML = '<div class="empty-state">No pending callbacks.</div>'; return; }
  el.innerHTML = pending.map(c => {
    const cs = callbackStatus(c.callback);
    const d = daysUntil(c.callback);
    const dateLabel = cs === 'overdue'
      ? `<span style="color:var(--danger)">${fmtDate(c.callback)}</span><br><span style="color:var(--danger);font-size:9px">${Math.abs(d)}d overdue</span>`
      : cs === 'today'
      ? `<span style="color:var(--warn)">Today</span>`
      : `<span style="color:var(--text2)">${fmtDate(c.callback)}</span><br><span style="color:var(--text3);font-size:9px">in ${d}d</span>`;
    const phoneBtn = c.phone ? `<a href="tel:${c.phone}" class="btn btn-sm" onclick="event.stopPropagation()">Call</a>` : '';
    const emailBtn = c.email ? `<button class="btn btn-sm" onclick="event.stopPropagation();emailCallback('${c.id}')">Email</button>` : '';
    return `<div class="callback-item ${cs}" onclick="openDetail('${c.id}')">
      <div class="callback-left">
        <div class="callback-name">${c.name}</div>
        <div class="callback-reason">${c.callbackReason || c.jobdesc || 'Follow up'}</div>
        <div style="margin-top:6px;display:flex;gap:6px">${phoneBtn}${emailBtn}</div>
      </div>
      <div class="callback-date-label" style="font-family:var(--font-mono)">${dateLabel}</div>
    </div>`;
  }).join('');
}

function emailCallback(id) {
  const c = clients.find(x => x.id === id);
  if (!c || !c.email) return;
  const sub = encodeURIComponent(`Dakota Earthworks — Follow Up`);
  const body = encodeURIComponent(`Hi ${c.name.split(' ')[0]},\n\nJust following up on ${c.jobdesc || 'your project'}. Please give me a call at 701-773-DIRT or reply to this email.\n\nThanks,\nNate\nDakota Earthworks\n701-773-DIRT`);
  window.location.href = `mailto:${c.email}?subject=${sub}&body=${body}`;
}

function openEmailAll() {
  const overdue = clients.filter(c => callbackStatus(c.callback) === 'overdue' && c.email);
  if (!overdue.length) { alert('No overdue clients with email addresses.'); return; }
  const to = overdue.map(c => c.email).join(',');
  const sub = encodeURIComponent('Dakota Earthworks — Following Up');
  const body = encodeURIComponent('Hi,\n\nFollowing up on your project. Please give us a call at 701-773-DIRT.\n\nThanks,\nNate\nDakota Earthworks');
  window.location.href = `mailto:${to}?subject=${sub}&body=${body}`;
}

// ─── DETAIL MODAL ──────────────────────────────────────────────────────────
function openDetail(id) {
  const c = clients.find(x => x.id === id);
  if (!c) return;
  const statusClass = c.status.replace(' ','-');
  const cs = callbackStatus(c.callback);
  let cbLine = c.callback ? `${fmtDate(c.callback)}${cs === 'overdue' ? ' — <span style="color:var(--danger)">OVERDUE</span>' : cs === 'today' ? ' — <span style="color:var(--warn)">Today</span>' : ''}` : '—';
  const notes = (c.notes||[]).slice().reverse();
  document.getElementById('detailContent').innerHTML = `
    <div class="modal-title" style="display:flex;align-items:center;justify-content:space-between">
      <span>${c.name}</span>
      <span class="tag tag-type-${c.type.toLowerCase()}">${c.type}</span>
    </div>
    <div class="form-section">
      <div style="margin-bottom:12px"><span class="status-pill status-${statusClass}">${c.status}</span></div>
      ${c.phone ? `<div class="detail-field"><div class="detail-field-label">Phone</div><div class="detail-field-value"><a class="phone-link" href="tel:${c.phone}">${c.phone}</a></div></div>` : ''}
      ${c.email ? `<div class="detail-field"><div class="detail-field-label">Email</div><div class="detail-field-value" style="color:var(--info)">${c.email}</div></div>` : ''}
      ${c.location ? `<div class="detail-field"><div class="detail-field-label">Location</div><div class="detail-field-value">${c.location}</div></div>` : ''}
      ${c.jobdesc ? `<div class="detail-field"><div class="detail-field-label">Job</div><div class="detail-field-value">${c.jobdesc}</div></div>` : ''}
      ${c.value ? `<div class="detail-field"><div class="detail-field-label">Est. Value</div><div class="detail-field-value" style="color:var(--accent);font-family:var(--font-mono)">$${Number(c.value).toLocaleString()}</div></div>` : ''}
      <div class="detail-field"><div class="detail-field-label">Callback</div><div class="detail-field-value">${cbLine}</div></div>
      ${c.callbackReason ? `<div class="detail-field"><div class="detail-field-label">Callback Reason</div><div class="detail-field-value">${c.callbackReason}</div></div>` : ''}
    </div>
    <div class="detail-actions">
      <button class="btn btn-sm btn-accent" onclick="editClient('${c.id}')">Edit</button>
      ${c.phone ? `<a class="btn btn-sm" href="tel:${c.phone}">Call</a>` : ''}
      ${c.email ? `<button class="btn btn-sm" onclick="emailCallback('${c.id}')">Email</button>` : ''}
      <button class="btn btn-sm" onclick="openReminderPicker('${c.id}')">+ Reminder</button>
      <button class="btn btn-sm" onclick="exportPDF('${c.id}')">PDF</button>
      <button class="btn btn-sm btn-danger" onclick="deleteClient('${c.id}')">Delete</button>
    </div>
    <div class="divider" style="margin:12px 16px 0"></div>
    <div class="form-section" style="margin-top:12px">
      <div class="section-header"><div class="section-title">Job Progress</div><div style="font-family:var(--font-mono);font-size:10px;color:var(--accent2)">${jobProgressPct(c)}% complete</div></div>
      <div class="progress-bar-wrap" style="margin-bottom:14px"><div class="progress-bar-fill" style="width:${jobProgressPct(c)}%"></div></div>
      <div id="progressChecklist_${c.id}">
        ${renderProgressChecklist(c)}
      </div>
    </div>
    <div class="divider" style="margin:12px 16px 0"></div>
      <div style="display:flex;gap:8px;margin-bottom:10px">
        <input class="form-input" type="text" id="noteInput_${c.id}" placeholder="Add a note…" style="flex:1">
        <button class="btn btn-sm btn-accent" onclick="addNote('${c.id}')">Add</button>
      </div>
      <div id="notesList_${c.id}">
        ${notes.length ? notes.map(n => `<div class="note-item"><div class="note-text">${n.text}</div><div class="note-ts">${n.ts}</div></div>`).join('') : '<div style="font-family:var(--font-mono);font-size:11px;color:var(--text3)">No notes yet.</div>'}
      </div>
    </div>
  `;
  openModal('detailModal');
}

function addNote(id) {
  const input = document.getElementById(`noteInput_${id}`);
  const text = input.value.trim();
  if (!text) return;
  const c = clients.find(x => x.id === id);
  if (!c) return;
  if (!c.notes) c.notes = [];
  const now = new Date();
  c.notes.push({ text, ts: now.toLocaleDateString('en-US',{month:'short',day:'numeric',year:'numeric'}) + ' ' + now.toLocaleTimeString('en-US',{hour:'numeric',minute:'2-digit'}) });
  save();
  openDetail(id);
}

// ─── ADD / EDIT ────────────────────────────────────────────────────────────
function openAddClient() {
  editingId = null;
  document.getElementById('clientModalTitle').textContent = 'New Client';
  document.getElementById('clientSaveBtn').textContent = 'Save Client';
  ['f_name','f_phone','f_email','f_location','f_jobdesc','f_callback','f_callbackReason','f_value','f_note'].forEach(id => document.getElementById(id).value = '');
  document.getElementById('f_type').value = 'Homeowner';
  document.getElementById('f_status').value = 'Lead';
  document.getElementById('f_callback').value = '';
  openModal('clientModal');
}

function editClient(id) {
  const c = clients.find(x => x.id === id);
  if (!c) return;
  editingId = id;
  closeModal('detailModal');
  document.getElementById('clientModalTitle').textContent = 'Edit Client';
  document.getElementById('clientSaveBtn').textContent = 'Update';
  document.getElementById('f_name').value = c.name || '';
  document.getElementById('f_type').value = c.type || 'Homeowner';
  document.getElementById('f_status').value = c.status || 'Lead';
  document.getElementById('f_phone').value = c.phone || '';
  document.getElementById('f_email').value = c.email || '';
  document.getElementById('f_location').value = c.location || '';
  document.getElementById('f_jobdesc').value = c.jobdesc || '';
  document.getElementById('f_callback').value = c.callback || '';
  document.getElementById('f_callbackReason').value = c.callbackReason || '';
  document.getElementById('f_value').value = c.value || '';
  document.getElementById('f_note').value = '';
  openModal('clientModal');
}

function saveClient() {
  const name = document.getElementById('f_name').value.trim();
  if (!name) { document.getElementById('f_name').focus(); return; }
  const noteText = document.getElementById('f_note').value.trim();
  const now = new Date();
  const tsStr = now.toLocaleDateString('en-US',{month:'short',day:'numeric',year:'numeric'}) + ' ' + now.toLocaleTimeString('en-US',{hour:'numeric',minute:'2-digit'});
  if (editingId) {
    const c = clients.find(x => x.id === editingId);
    if (c) {
      c.name = name;
      c.type = document.getElementById('f_type').value;
      c.status = document.getElementById('f_status').value;
      c.phone = document.getElementById('f_phone').value.trim();
      c.email = document.getElementById('f_email').value.trim();
      c.location = document.getElementById('f_location').value.trim();
      c.jobdesc = document.getElementById('f_jobdesc').value.trim();
      c.callback = document.getElementById('f_callback').value;
      c.callbackReason = document.getElementById('f_callbackReason').value.trim();
      c.value = document.getElementById('f_value').value;
      if (noteText) { if (!c.notes) c.notes = []; c.notes.push({ text: noteText, ts: tsStr }); }
    }
  } else {
    const notes = noteText ? [{ text: noteText, ts: tsStr }] : [];
    clients.push({
      id: uid(),
      name,
      type: document.getElementById('f_type').value,
      status: document.getElementById('f_status').value,
      phone: document.getElementById('f_phone').value.trim(),
      email: document.getElementById('f_email').value.trim(),
      location: document.getElementById('f_location').value.trim(),
      jobdesc: document.getElementById('f_jobdesc').value.trim(),
      callback: document.getElementById('f_callback').value,
      callbackReason: document.getElementById('f_callbackReason').value.trim(),
      value: document.getElementById('f_value').value,
      created: today(),
      notes
    });
  }
  save();
  closeModal('clientModal');
  renderClients();
}

function deleteClient(id) {
  if (!confirm('Delete this client? This cannot be undone.')) return;
  clients = clients.filter(x => x.id !== id);
  save();
  closeModal('detailModal');
  renderClients();
}

// ─── JOB PROGRESS ─────────────────────────────────────────────────────────
const JOB_STAGES = [
  'Mobilized',
  'Topsoil Stripped',
  'Excavation Complete',
  'Utilities / Pipe Set',
  'Backfill',
  'Compaction Return',
  'Finish Grade',
  'Cleanup / Demob',
  'Inspection Passed'
];

function initProgress(c) {
  if (!c.progress) {
    c.progress = JOB_STAGES.map(name => ({ name, done: false, note: '', ts: '' }));
  } else {
    // ensure any new stages added later get appended
    JOB_STAGES.forEach(name => {
      if (!c.progress.find(s => s.name === name)) {
        c.progress.push({ name, done: false, note: '', ts: '' });
      }
    });
  }
  return c.progress;
}

function jobProgressPct(c) {
  if (!c.progress) return 0;
  const done = c.progress.filter(s => s.done).length;
  return Math.round((done / JOB_STAGES.length) * 100);
}

function nextStageName(c) {
  if (!c.progress) return '';
  const next = c.progress.find(s => !s.done);
  return next ? 'Next: ' + next.name : 'Complete';
}

function renderProgressChecklist(c) {
  initProgress(c);
  return c.progress.map((s, i) => {
    const safeNote = (s.note||'').replace(/'/g, '&#39;');
    return `
    <div class="progress-stage" id="pstage_${c.id}_${i}">
      <div class="progress-stage-header" onclick="toggleStageBody('${c.id}',${i})">
        <div class="progress-check ${s.done ? 'done' : ''}" onclick="event.stopPropagation();toggleStage('${c.id}',${i})">✓</div>
        <div class="progress-stage-label ${s.done ? 'done' : ''}">${s.name}</div>
        <div class="progress-stage-ts">${s.ts || ''}</div>
      </div>
      <div class="progress-stage-body" id="psbody_${c.id}_${i}">
        ${s.note ? `<div class="progress-stage-note">${s.note}</div>` : ''}
        <div class="progress-note-input-row">
          <input class="form-input" type="text" id="psnote_${c.id}_${i}" placeholder="Add note for this stage…" value="${safeNote}" style="flex:1;font-size:12px;padding:6px 10px">
          <button class="btn btn-sm btn-accent" onclick="saveStageNote('${c.id}',${i})">Save</button>
        </div>
      </div>
    </div>`;
  }).join('');
}

function toggleStageBody(clientId, idx) {
  const body = document.getElementById(`psbody_${clientId}_${idx}`);
  if (body) body.classList.toggle('open');
}

function toggleStage(clientId, idx) {
  const c = clients.find(x => x.id === clientId);
  if (!c) return;
  initProgress(c);
  const s = c.progress[idx];
  s.done = !s.done;
  if (s.done) {
    const now = new Date();
    s.ts = now.toLocaleDateString('en-US',{month:'short',day:'numeric'});
  } else {
    s.ts = '';
  }
  save();
  // re-render checklist and progress bar in-place without closing modal
  const cl = document.getElementById(`progressChecklist_${clientId}`);
  if (cl) cl.innerHTML = renderProgressChecklist(c);
  // update pct label
  const pct = jobProgressPct(c);
  document.querySelectorAll('.progress-bar-fill').forEach(el => el.style.width = pct + '%');
  renderClients();
  if (document.getElementById('view-progress').classList.contains('active')) renderProgressView();
}

function saveStageNote(clientId, idx) {
  const c = clients.find(x => x.id === clientId);
  if (!c) return;
  initProgress(c);
  const input = document.getElementById(`psnote_${clientId}_${idx}`);
  if (input) c.progress[idx].note = input.value.trim();
  save();
  const cl = document.getElementById(`progressChecklist_${clientId}`);
  if (cl) cl.innerHTML = renderProgressChecklist(c);
}

// ─── PROGRESS TAB VIEW ─────────────────────────────────────────────────────
function renderProgressView() {
  const active = clients.filter(c => c.status !== 'Lead' && c.status !== 'Bid Sent');
  const el = document.getElementById('progressList');
  if (!active.length) {
    el.innerHTML = '<div class="empty-state">No active jobs yet.<br>Jobs appear here once Awarded or beyond.</div>';
    return;
  }
  const sorted = active.slice().sort((a, b) => jobProgressPct(a) - jobProgressPct(b));
  el.innerHTML = sorted.map(c => {
    initProgress(c);
    const pct = jobProgressPct(c);
    const next = c.progress.find(s => !s.done);
    const lastDone = [...c.progress].reverse().find(s => s.done);
    return `<div class="progress-client-card" onclick="openDetailProgress('${c.id}')">
      <div class="pccard-top">
        <div class="pccard-name">${c.name}</div>
        <div class="pccard-pct">${pct}%</div>
      </div>
      <div style="font-size:12px;color:var(--text2);margin-bottom:8px">${c.jobdesc || c.location || '—'}</div>
      <div class="progress-bar-wrap"><div class="progress-bar-fill" style="width:${pct}%"></div></div>
      <div class="progress-label">
        <span>${next ? 'Next: ' + next.name : '✓ All stages complete'}</span>
        <span>${c.progress.filter(s=>s.done).length}/${JOB_STAGES.length} stages</span>
      </div>
      ${lastDone ? `<div class="pccard-stage" style="margin-top:6px">Last: ${lastDone.name}${lastDone.ts ? ' · '+lastDone.ts : ''}</div>` : ''}
    </div>`;
  }).join('');
}

function openDetailProgress(id) {
  openDetail(id);
  // auto-scroll to progress section after modal opens
  setTimeout(() => {
    const cl = document.getElementById(`progressChecklist_${id}`);
    if (cl) cl.scrollIntoView({ behavior: 'smooth', block: 'start' });
  }, 250);
}

// ─── MODALS ─────────────────────────────────────────────────────────────────
function openModal(id) { document.getElementById(id).classList.add('open'); }
function closeModal(id) { document.getElementById(id).classList.remove('open'); }
document.querySelectorAll('.modal-overlay').forEach(overlay => {
  overlay.addEventListener('click', e => { if (e.target === overlay) overlay.classList.remove('open'); });
});

// ─── CALENDAR REMINDER ─────────────────────────────────────────────────────
let reminderClientId = null;

function openReminderPicker(id) {
  const c = clients.find(x => x.id === id);
  if (!c) return;
  reminderClientId = id;
  document.getElementById('reminderClientName').textContent = c.name;
  // Pre-fill date from callback if set, otherwise today
  document.getElementById('r_date').value = c.callback || today();
  document.getElementById('r_time').value = '08:00';
  openModal('reminderModal');
}

function generateICS() {
  const c = clients.find(x => x.id === reminderClientId);
  if (!c) return;
  const dateVal = document.getElementById('r_date').value;
  const timeVal = document.getElementById('r_time').value || '08:00';
  if (!dateVal) { document.getElementById('r_date').focus(); return; }

  // Build datetime strings in ICS format (local time, no Z)
  const [yr, mo, dy] = dateVal.split('-');
  const [hr, mn] = timeVal.split(':');

  // Event start/end (1 hour block)
  const dtStart = `${yr}${mo}${dy}T${hr}${mn}00`;
  const endHr = String(parseInt(hr) + 1).padStart(2, '0');
  const dtEnd = `${yr}${mo}${dy}T${endHr}${mn}00`;

  // 8 AM alert on same day
  const alarmDt = `${yr}${mo}${dy}T080000`;

  const title = `DE Callback — ${c.name}`;
  const reason = c.callbackReason || c.jobdesc || 'Follow up';
  const desc = [
    reason,
    c.phone ? `Phone: ${c.phone}` : '',
    c.location ? `Location: ${c.location}` : '',
    c.status ? `Status: ${c.status}` : '',
    'Dakota Earthworks · 701-773-DIRT'
  ].filter(Boolean).join('\\n');

  const uid = `de-crm-${c.id}-${Date.now()}@dakotaearthworks`;

  const ics = [
    'BEGIN:VCALENDAR',
    'VERSION:2.0',
    'PRODID:-//Dakota Earthworks CRM//EN',
    'CALSCALE:GREGORIAN',
    'METHOD:PUBLISH',
    'BEGIN:VEVENT',
    `UID:${uid}`,
    `DTSTART;TZID=America/Chicago:${dtStart}`,
    `DTEND;TZID=America/Chicago:${dtEnd}`,
    `SUMMARY:${title}`,
    `DESCRIPTION:${desc}`,
    'BEGIN:VALARM',
    'TRIGGER;VALUE=DATE-TIME:' + alarmDt,
    'ACTION:DISPLAY',
    `DESCRIPTION:${title}`,
    'END:VALARM',
    'END:VEVENT',
    'END:VCALENDAR'
  ].join('\r\n');

  // Trigger download — iOS will prompt "Add to Calendar"
  const blob = new Blob([ics], { type: 'text/calendar;charset=utf-8' });
  const url = URL.createObjectURL(blob);
  const a = document.createElement('a');
  a.href = url;
  a.download = `DE-Callback-${c.name.replace(/\s+/g,'-')}.ics`;
  document.body.appendChild(a);
  a.click();
  document.body.removeChild(a);
  setTimeout(() => URL.revokeObjectURL(url), 1000);
  closeModal('reminderModal');
}

// ─── PDF EXPORT ────────────────────────────────────────────────────────────
function exportPDF(id) {
  const c = clients.find(x => x.id === id);
  if (!c) return;
  initProgress(c);
  const pct = jobProgressPct(c);
  const now = new Date().toLocaleDateString('en-US',{month:'long',day:'numeric',year:'numeric'});
  const stagesHtml = c.progress.map(s => `
    <div class="pdf-stage-row">
      <div class="pdf-check ${s.done ? 'done' : ''}">${s.done ? '✓' : ''}</div>
      <div style="flex:1">
        <div style="font-weight:${s.done?'500':'400'};text-decoration:${s.done?'none':'none'}">${s.name}</div>
        ${s.note ? `<div style="font-size:11px;color:#555;margin-top:2px">${s.note}</div>` : ''}
      </div>
      <div style="font-size:11px;color:#888;flex-shrink:0;padding-left:8px">${s.ts || ''}</div>
    </div>`).join('');

  const notesHtml = (c.notes||[]).length
    ? (c.notes||[]).slice().reverse().map(n => `<div class="pdf-note-item"><div>${n.text}</div><div style="font-size:10px;color:#888;margin-top:3px">${n.ts}</div></div>`).join('')
    : '<div style="font-size:12px;color:#888">No notes.</div>';

  const printWin = window.open('', '_blank', 'width=800,height=900');
  printWin.document.write(`<!DOCTYPE html><html><head>
    <meta charset="UTF-8">
    <title>DE Job Summary — ${c.name}</title>
    <link rel="stylesheet" href="https://fonts.googleapis.com/css2?family=IBM+Plex+Sans:wght@300;400;500&family=IBM+Plex+Mono:wght@400;500&display=swap">
    <style>
      body { font-family: 'IBM Plex Sans', sans-serif; font-size: 13px; color: #111; max-width: 720px; margin: 32px auto; padding: 0 24px; }
      .pdf-header { display: flex; justify-content: space-between; align-items: flex-start; border-bottom: 2px solid #111; padding-bottom: 14px; margin-bottom: 20px; }
      .pdf-logo { font-family: 'IBM Plex Mono', monospace; font-size: 13px; font-weight: 500; letter-spacing: 0.08em; text-transform: uppercase; }
      .pdf-logo span { color: #888; }
      .pdf-date { font-family: 'IBM Plex Mono', monospace; font-size: 11px; color: #888; }
      .pdf-client-name { font-size: 22px; font-weight: 500; margin-bottom: 4px; }
      .pdf-section-title { font-family: 'IBM Plex Mono', monospace; font-weight: 500; font-size: 10px; letter-spacing: 0.1em; text-transform: uppercase; color: #888; border-bottom: 1px solid #ddd; padding-bottom: 5px; margin: 20px 0 10px; }
      .pdf-fields { display: grid; grid-template-columns: 1fr 1fr; gap: 10px 24px; }
      .pdf-field-label { font-size: 10px; text-transform: uppercase; letter-spacing: 0.06em; color: #888; margin-bottom: 2px; font-family: 'IBM Plex Mono', monospace; }
      .pdf-field-value { font-size: 13px; }
      .pdf-progress-bar-wrap { background: #eee; border-radius: 2px; height: 6px; margin: 8px 0 4px; }
      .pdf-progress-bar-fill { height: 100%; border-radius: 2px; background: #8fb87a; }
      .pdf-pct { font-family: 'IBM Plex Mono', monospace; font-size: 11px; color: #555; }
      .pdf-stage-row { display: flex; align-items: flex-start; gap: 10px; padding: 7px 0; border-bottom: 1px solid #f0f0f0; font-size: 12px; }
      .pdf-check { width: 16px; height: 16px; border: 1.5px solid #bbb; border-radius: 50%; flex-shrink: 0; margin-top: 1px; display: flex; align-items: center; justify-content: center; font-size: 10px; }
      .pdf-check.done { background: #3a6b2a; color: #fff; border-color: #3a6b2a; }
      .pdf-note-item { background: #f9f9f9; border-left: 3px solid #ddd; padding: 7px 10px; margin-bottom: 6px; font-size: 12px; }
      .tag { display: inline-block; font-family: 'IBM Plex Mono', monospace; font-size: 10px; padding: 2px 8px; border-radius: 2px; text-transform: uppercase; background: #f0f0f0; color: #555; margin-right: 6px; }
      .status-tag { display: inline-block; font-family: 'IBM Plex Mono', monospace; font-size: 10px; padding: 3px 10px; border-radius: 2px; text-transform: uppercase; background: #e8f0e8; color: #3a6b2a; }
      @media print { body { margin: 16px; } }
    </style>

  </head><body>
    <div class="pdf-header">
      <div>
        <div class="pdf-logo">DE<span>/</span>CRM &nbsp;·&nbsp; Job Summary</div>
        <div class="pdf-client-name" style="margin-top:10px">${c.name}</div>
        <div style="margin-top:4px"><span class="tag">${c.type}</span><span class="status-tag">${c.status}</span></div>
      </div>
      <div class="pdf-date" style="text-align:right">
        Printed ${now}<br>
        <span style="font-size:10px;color:#aaa">Dakota Earthworks · 701-773-DIRT</span>
      </div>
    </div>

```
<div class="pdf-section-title">Job Details</div>
<div class="pdf-fields">
  ${c.phone ? `<div><div class="pdf-field-label">Phone</div><div class="pdf-field-value">${c.phone}</div></div>` : ''}
  ${c.email ? `<div><div class="pdf-field-label">Email</div><div class="pdf-field-value">${c.email}</div></div>` : ''}
  ${c.location ? `<div><div class="pdf-field-label">Location</div><div class="pdf-field-value">${c.location}</div></div>` : ''}
  ${c.value ? `<div><div class="pdf-field-label">Est. Value</div><div class="pdf-field-value">$${Number(c.value).toLocaleString()}</div></div>` : ''}
  ${c.callback ? `<div><div class="pdf-field-label">Callback</div><div class="pdf-field-value">${fmtDate(c.callback)}${c.callbackReason ? ' — ' + c.callbackReason : ''}</div></div>` : ''}
  ${c.created ? `<div><div class="pdf-field-label">Created</div><div class="pdf-field-value">${fmtDate(c.created)}</div></div>` : ''}
</div>
${c.jobdesc ? `<div style="margin-top:12px"><div class="pdf-field-label">Job Description</div><div class="pdf-field-value" style="margin-top:3px;line-height:1.5">${c.jobdesc}</div></div>` : ''}

<div class="pdf-section-title">Job Progress — ${pct}% Complete</div>
<div class="pdf-progress-bar-wrap"><div class="pdf-progress-bar-fill" style="width:${pct}%"></div></div>
<div class="pdf-pct">${c.progress.filter(s=>s.done).length} of ${c.progress.length} stages complete</div>
<div style="margin-top:12px">${stagesHtml}</div>

<div class="pdf-section-title">Notes</div>
${notesHtml}

<div style="margin-top:32px;padding-top:12px;border-top:1px solid #ddd;font-family:'IBM Plex Mono',monospace;font-size:10px;color:#aaa;text-align:center">
  Dakota Earthworks · Washburn, ND · 701-773-DIRT · dakotaearthworks.com
</div>
```

  </body></html>`);
  printWin.document.close();
  printWin.focus();
  setTimeout(() => printWin.print(), 600);
}

// ─── INIT ──────────────────────────────────────────────────────────────────
load();
renderClients();
</script>

</body>
</html>
