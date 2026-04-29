<!DOCTYPE html>
<html lang="es">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>CareerPath — Tu coach de empleabilidad UTP</title>
<link href="https://fonts.googleapis.com/css2?family=DM+Sans:ital,opsz,wght@0,9..40,300;0,9..40,400;0,9..40,500;0,9..40,600;1,9..40,300&family=DM+Mono:wght@400;500&display=swap" rel="stylesheet">
<style>
  :root {
    --green: #12B76A;
    --green-dark: #0A7A47;
    --green-light: #D1FAE5;
    --green-mid: #34D399;
    --amber: #F59E0B;
    --amber-light: #FEF3C7;
    --red: #EF4444;
    --red-light: #FEE2E2;
    --blue: #3B82F6;
    --blue-light: #EFF6FF;
    --purple: #8B5CF6;
    --purple-light: #EDE9FE;
    --bg: #F9FAFB;
    --surface: #FFFFFF;
    --border: #E5E7EB;
    --border-light: #F3F4F6;
    --text: #111827;
    --text-2: #374151;
    --text-3: #6B7280;
    --text-4: #9CA3AF;
    --font: 'DM Sans', sans-serif;
    --mono: 'DM Mono', monospace;
    --radius: 10px;
    --radius-sm: 6px;
    --radius-lg: 16px;
    --shadow: 0 1px 3px rgba(0,0,0,0.08), 0 1px 2px rgba(0,0,0,0.04);
    --shadow-md: 0 4px 12px rgba(0,0,0,0.08), 0 2px 4px rgba(0,0,0,0.04);
  }

  * { box-sizing: border-box; margin: 0; padding: 0; }

  body {
    font-family: var(--font);
    background: var(--bg);
    color: var(--text);
    min-height: 100vh;
    display: flex;
    flex-direction: column;
  }

  /* ── TOPBAR ── */
  .topbar {
    background: var(--surface);
    border-bottom: 1px solid var(--border);
    padding: 0 24px;
    display: flex;
    align-items: center;
    gap: 0;
    height: 56px;
    position: sticky;
    top: 0;
    z-index: 100;
    box-shadow: var(--shadow);
  }
  .logo {
    font-size: 17px;
    font-weight: 600;
    color: var(--green-dark);
    letter-spacing: -0.02em;
    margin-right: 32px;
    flex-shrink: 0;
  }
  .logo span { color: var(--text); }
  .logo sup {
    font-size: 9px;
    background: var(--green);
    color: #fff;
    border-radius: 3px;
    padding: 1px 4px;
    margin-left: 2px;
    vertical-align: super;
    font-weight: 500;
    letter-spacing: 0;
  }
  .nav {
    display: flex;
    gap: 2px;
    flex: 1;
  }
  .nav-item {
    padding: 6px 12px;
    font-size: 13px;
    color: var(--text-3);
    border-radius: var(--radius-sm);
    cursor: pointer;
    transition: all 0.15s;
    display: flex;
    align-items: center;
    gap: 6px;
    font-weight: 400;
    border: none;
    background: none;
    font-family: var(--font);
  }
  .nav-item:hover { background: var(--border-light); color: var(--text-2); }
  .nav-item.active {
    background: var(--green-light);
    color: var(--green-dark);
    font-weight: 500;
  }
  .nav-item .icon { font-size: 15px; }
  .avatar {
    width: 32px; height: 32px;
    border-radius: 50%;
    background: linear-gradient(135deg, var(--green-light), var(--green));
    display: flex; align-items: center; justify-content: center;
    font-size: 12px; font-weight: 600;
    color: var(--green-dark);
    flex-shrink: 0;
    margin-left: 12px;
    cursor: pointer;
  }

  /* ── LAYOUT ── */
  .layout {
    display: flex;
    flex: 1;
    min-height: calc(100vh - 56px);
  }

  /* ── SIDEBAR ── */
  .sidebar {
    width: 200px;
    background: var(--surface);
    border-right: 1px solid var(--border);
    padding: 20px 12px;
    flex-shrink: 0;
    display: flex;
    flex-direction: column;
    gap: 2px;
  }
  .sidebar-label {
    font-size: 10px;
    font-weight: 500;
    color: var(--text-4);
    letter-spacing: 0.08em;
    text-transform: uppercase;
    padding: 4px 8px;
    margin-top: 12px;
    margin-bottom: 2px;
  }
  .sidebar-label:first-child { margin-top: 0; }
  .sidebar-item {
    display: flex;
    align-items: center;
    gap: 10px;
    padding: 8px 10px;
    border-radius: var(--radius-sm);
    font-size: 13px;
    color: var(--text-3);
    cursor: pointer;
    transition: all 0.15s;
    border: none;
    background: none;
    font-family: var(--font);
    width: 100%;
    text-align: left;
  }
  .sidebar-item:hover { background: var(--border-light); color: var(--text-2); }
  .sidebar-item.active {
    background: var(--green-light);
    color: var(--green-dark);
    font-weight: 500;
  }
  .sidebar-item .si-icon { font-size: 16px; width: 20px; text-align: center; flex-shrink: 0; }
  .sidebar-badge {
    margin-left: auto;
    background: var(--green);
    color: #fff;
    font-size: 10px;
    font-weight: 600;
    padding: 1px 6px;
    border-radius: 99px;
  }

  /* ── MAIN CONTENT ── */
  .main {
    flex: 1;
    padding: 28px;
    overflow-y: auto;
    min-width: 0;
  }

  /* ── SCREENS ── */
  .screen { display: none; }
  .screen.active { display: block; animation: fadeIn 0.2s ease; }
  @keyframes fadeIn { from { opacity: 0; transform: translateY(6px); } to { opacity: 1; transform: translateY(0); } }

  /* ── PAGE HEADER ── */
  .page-header { margin-bottom: 24px; }
  .page-title { font-size: 22px; font-weight: 600; color: var(--text); letter-spacing: -0.02em; margin-bottom: 4px; }
  .page-sub { font-size: 14px; color: var(--text-3); }

  /* ── CARDS ── */
  .card {
    background: var(--surface);
    border: 1px solid var(--border);
    border-radius: var(--radius-lg);
    padding: 20px;
    box-shadow: var(--shadow);
  }
  .card + .card { margin-top: 14px; }
  .card-title {
    font-size: 13px;
    font-weight: 500;
    color: var(--text-3);
    text-transform: uppercase;
    letter-spacing: 0.06em;
    margin-bottom: 14px;
    display: flex;
    align-items: center;
    gap: 6px;
  }

  /* ── METRICS ── */
  .metric-row { display: grid; grid-template-columns: repeat(3, 1fr); gap: 12px; margin-bottom: 16px; }
  .metric {
    background: var(--surface);
    border: 1px solid var(--border);
    border-radius: var(--radius);
    padding: 16px;
    box-shadow: var(--shadow);
  }
  .metric-label { font-size: 12px; color: var(--text-3); margin-bottom: 6px; }
  .metric-value { font-size: 28px; font-weight: 600; color: var(--text); letter-spacing: -0.03em; line-height: 1; }
  .metric-sub { font-size: 11px; color: var(--text-4); margin-top: 4px; }
  .metric-tag { font-size: 11px; font-weight: 500; margin-top: 6px; display: inline-block; }
  .metric-tag.up { color: var(--green); }
  .metric-tag.warn { color: var(--amber); }

  /* ── BADGES ── */
  .badge {
    display: inline-flex; align-items: center; gap: 4px;
    font-size: 11px; font-weight: 500;
    padding: 3px 8px; border-radius: 99px;
  }
  .badge-green { background: var(--green-light); color: var(--green-dark); }
  .badge-amber { background: var(--amber-light); color: #92400E; }
  .badge-red { background: var(--red-light); color: #991B1B; }
  .badge-blue { background: var(--blue-light); color: #1D4ED8; }
  .badge-purple { background: var(--purple-light); color: #5B21B6; }
  .badge-gray { background: var(--border-light); color: var(--text-3); }

  /* ── PROGRESS BAR ── */
  .pbar-wrap { background: var(--border-light); border-radius: 99px; height: 6px; flex: 1; overflow: hidden; }
  .pbar-fill { height: 100%; border-radius: 99px; transition: width 0.6s ease; }

  /* ── SKILL ROWS ── */
  .skill-row { display: flex; align-items: center; gap: 10px; margin-bottom: 12px; }
  .skill-row:last-child { margin-bottom: 0; }
  .skill-name { font-size: 13px; color: var(--text-2); width: 120px; flex-shrink: 0; }
  .skill-pct { font-size: 12px; font-weight: 500; color: var(--text); width: 34px; text-align: right; flex-shrink: 0; font-family: var(--mono); }

  /* ── JOBS ── */
  .job-item { display: flex; align-items: flex-start; gap: 12px; padding: 14px 0; border-bottom: 1px solid var(--border-light); }
  .job-item:first-child { padding-top: 0; }
  .job-item:last-child { border-bottom: none; padding-bottom: 0; }
  .job-logo {
    width: 40px; height: 40px;
    border-radius: var(--radius-sm);
    background: var(--bg);
    border: 1px solid var(--border);
    display: flex; align-items: center; justify-content: center;
    font-size: 12px; font-weight: 600;
    color: var(--text-3);
    flex-shrink: 0;
    font-family: var(--mono);
  }
  .job-body { flex: 1; min-width: 0; }
  .job-title { font-size: 14px; font-weight: 500; color: var(--text); margin-bottom: 2px; }
  .job-company { font-size: 12px; color: var(--text-3); margin-bottom: 8px; }
  .job-tags { display: flex; gap: 5px; flex-wrap: wrap; }
  .job-cta {
    background: var(--green);
    color: #fff;
    border: none;
    border-radius: var(--radius-sm);
    padding: 7px 14px;
    font-size: 12px;
    font-weight: 500;
    cursor: pointer;
    font-family: var(--font);
    flex-shrink: 0;
    align-self: center;
    transition: background 0.15s;
  }
  .job-cta:hover { background: var(--green-dark); }

  /* ── ROADMAP ── */
  .road-step { display: flex; gap: 14px; margin-bottom: 0; }
  .road-dot-col { display: flex; flex-direction: column; align-items: center; padding-top: 3px; }
  .road-dot { width: 14px; height: 14px; border-radius: 50%; flex-shrink: 0; }
  .road-line { width: 2px; flex: 1; background: var(--border); min-height: 28px; margin: 4px 0; }
  .road-content { flex: 1; padding-bottom: 20px; }
  .road-title { font-size: 14px; font-weight: 500; color: var(--text); margin-bottom: 4px; }
  .road-desc { font-size: 13px; color: var(--text-3); line-height: 1.55; margin-bottom: 6px; }
  .road-week { font-size: 11px; color: var(--text-4); display: flex; align-items: center; gap: 8px; }

  /* ── CV SCORE ── */
  .cv-score-ring {
    width: 96px; height: 96px;
    border-radius: 50%;
    border: 5px solid var(--green);
    display: flex; flex-direction: column;
    align-items: center; justify-content: center;
    background: var(--green-light);
    flex-shrink: 0;
  }
  .cv-score-num { font-size: 26px; font-weight: 600; color: var(--green-dark); letter-spacing: -0.04em; font-family: var(--mono); }
  .cv-score-lbl { font-size: 10px; color: var(--text-3); font-weight: 400; }

  .sug-row { display: flex; gap: 12px; align-items: flex-start; padding: 12px 0; border-bottom: 1px solid var(--border-light); }
  .sug-row:last-child { border-bottom: none; padding-bottom: 0; }
  .sug-row:first-child { padding-top: 0; }
  .sug-icon { width: 28px; height: 28px; border-radius: var(--radius-sm); display: flex; align-items: center; justify-content: center; flex-shrink: 0; font-size: 14px; }
  .sug-body { flex: 1; }
  .sug-tag { font-size: 12px; font-weight: 500; margin-bottom: 2px; }
  .sug-text { font-size: 13px; color: var(--text-3); line-height: 1.55; }

  /* ── ONBOARDING ── */
  .onboard-wrap { max-width: 480px; margin: 0 auto; padding: 16px 0; }
  .onboard-logo { text-align: center; margin-bottom: 32px; }
  .onboard-logo .name { font-size: 26px; font-weight: 600; color: var(--green-dark); letter-spacing: -0.03em; }
  .onboard-logo .name span { color: var(--text); }
  .onboard-logo .sub { font-size: 14px; color: var(--text-3); margin-top: 4px; }
  .onboard-step {
    display: flex; gap: 14px; align-items: center;
    padding: 16px;
    border: 1px solid var(--border);
    border-radius: var(--radius);
    margin-bottom: 10px;
    background: var(--surface);
    box-shadow: var(--shadow);
  }
  .onboard-step.active-step { border-color: var(--green); box-shadow: 0 0 0 2px rgba(18,183,106,0.12); }
  .step-num {
    width: 34px; height: 34px; border-radius: 50%;
    background: var(--green-light); color: var(--green-dark);
    font-size: 14px; font-weight: 600;
    display: flex; align-items: center; justify-content: center;
    flex-shrink: 0;
  }
  .step-num.done { background: var(--green); color: #fff; }
  .step-num.pending { background: var(--border-light); color: var(--text-4); }
  .step-title { font-size: 14px; font-weight: 500; color: var(--text); }
  .step-desc { font-size: 12px; color: var(--text-3); margin-top: 2px; }
  .form-section { margin-top: 24px; }
  .form-label { font-size: 13px; color: var(--text-2); margin-bottom: 8px; font-weight: 400; }
  .tags-pick { display: flex; flex-wrap: wrap; gap: 6px; margin-bottom: 16px; }
  .tag-pick {
    padding: 6px 12px; border-radius: 99px; font-size: 13px;
    border: 1px solid var(--border); cursor: pointer;
    background: var(--surface); color: var(--text-3);
    transition: all 0.15s; font-family: var(--font);
  }
  .tag-pick.selected { background: var(--green-light); border-color: var(--green); color: var(--green-dark); font-weight: 500; }
  .tag-pick:hover:not(.selected) { border-color: var(--text-4); color: var(--text-2); }
  .form-input {
    width: 100%;
    background: var(--bg);
    border: 1px solid var(--border);
    border-radius: var(--radius-sm);
    padding: 10px 14px;
    font-size: 14px;
    color: var(--text-3);
    font-family: var(--font);
    outline: none;
    transition: border-color 0.15s;
  }
  .form-input:focus { border-color: var(--green); }

  /* ── BUTTONS ── */
  .btn-primary {
    background: var(--green);
    color: #fff; border: none;
    border-radius: var(--radius-sm);
    padding: 11px 20px;
    font-size: 14px; font-weight: 500;
    cursor: pointer; width: 100%;
    font-family: var(--font);
    transition: background 0.15s;
    letter-spacing: -0.01em;
  }
  .btn-primary:hover { background: var(--green-dark); }
  .btn-secondary {
    background: var(--surface);
    color: var(--text-2);
    border: 1px solid var(--border);
    border-radius: var(--radius-sm);
    padding: 10px 20px;
    font-size: 14px; font-weight: 400;
    cursor: pointer;
    font-family: var(--font);
    transition: all 0.15s;
  }
  .btn-secondary:hover { border-color: var(--text-4); }

  /* ── GRID ── */
  .two-col { display: grid; grid-template-columns: 1fr 1fr; gap: 14px; margin-bottom: 14px; }
  .two-col .card { margin: 0; }

  /* ── MINI PROGRESS ── */
  .mini-prog { display: flex; align-items: center; gap: 10px; }
  .mini-prog-bar { flex: 1; height: 6px; background: var(--border-light); border-radius: 99px; overflow: hidden; }
  .mini-prog-fill { height: 100%; border-radius: 99px; background: var(--green); }

  /* ── UPLOAD ZONE ── */
  .upload-zone {
    border: 2px dashed var(--border);
    border-radius: var(--radius);
    padding: 32px;
    text-align: center;
    cursor: pointer;
    transition: all 0.15s;
    background: var(--bg);
    margin-bottom: 16px;
  }
  .upload-zone:hover { border-color: var(--green); background: var(--green-light); }
  .upload-icon { font-size: 32px; margin-bottom: 8px; }
  .upload-text { font-size: 14px; color: var(--text-3); }
  .upload-sub { font-size: 12px; color: var(--text-4); margin-top: 4px; }

  /* ── GREETING ── */
  .greeting { margin-bottom: 24px; }
  .greeting-name { font-size: 22px; font-weight: 600; color: var(--text); letter-spacing: -0.02em; }
  .greeting-sub { font-size: 14px; color: var(--text-3); margin-top: 3px; }

  /* ── OVERALL PROGRESS BAR (big) ── */
  .big-prog-wrap { background: var(--surface); border: 1px solid var(--border); border-radius: var(--radius-lg); padding: 20px; margin-bottom: 14px; box-shadow: var(--shadow); }
  .big-prog-header { display: flex; justify-content: space-between; align-items: baseline; margin-bottom: 10px; }
  .big-prog-label { font-size: 14px; font-weight: 500; color: var(--text); }
  .big-prog-pct { font-size: 22px; font-weight: 600; color: var(--green-dark); font-family: var(--mono); }
  .big-pbar { height: 10px; background: var(--border-light); border-radius: 99px; overflow: hidden; }
  .big-pbar-fill { height: 100%; background: linear-gradient(90deg, var(--green), var(--green-mid)); border-radius: 99px; }
  .big-prog-stages { display: flex; justify-content: space-between; margin-top: 10px; }
  .prog-stage { font-size: 11px; color: var(--text-4); }
  .prog-stage.done { color: var(--green); font-weight: 500; }

</style>
</head>
<body>

<!-- ── TOPBAR ── -->
<div class="topbar">
  <div class="logo">Career<span>Path</span><sup>UTP</sup></div>
  <nav class="nav" id="topnav">
    <button class="nav-item active" onclick="goScreen('dashboard')" data-screen="dashboard"><span class="icon">⊞</span> Dashboard</button>
    <button class="nav-item" onclick="goScreen('brechas')" data-screen="brechas"><span class="icon">◎</span> Brechas</button>
    <button class="nav-item" onclick="goScreen('roadmap')" data-screen="roadmap"><span class="icon">↗</span> Roadmap</button>
    <button class="nav-item" onclick="goScreen('cv')" data-screen="cv"><span class="icon">◻</span> Analizador CV</button>
    <button class="nav-item" onclick="goScreen('jobs')" data-screen="jobs"><span class="icon">◈</span> Empleos</button>
  </nav>
  <div class="avatar" title="Andrea Campos">AC</div>
</div>

<div class="layout">

  <!-- ── SIDEBAR ── -->
  <aside class="sidebar">
    <div class="sidebar-label">Menú</div>
    <button class="sidebar-item active" onclick="goScreen('dashboard')" data-sb="dashboard"><span class="si-icon">⊞</span> Dashboard</button>
    <button class="sidebar-item" onclick="goScreen('brechas')" data-sb="brechas"><span class="si-icon">◎</span> Mis brechas</button>
    <button class="sidebar-item" onclick="goScreen('roadmap')" data-sb="roadmap"><span class="si-icon">↗</span> Roadmap</button>
    <button class="sidebar-item" onclick="goScreen('cv')" data-sb="cv"><span class="si-icon">◻</span> Analizador CV</button>
    <button class="sidebar-item" onclick="goScreen('jobs')" data-sb="jobs"><span class="si-icon">◈</span> Empleos <span class="sidebar-badge">14</span></button>
    <div class="sidebar-label">Cuenta</div>
    <button class="sidebar-item" onclick="goScreen('onboard')" data-sb="onboard"><span class="si-icon">◷</span> Mi perfil</button>
  </aside>

  <!-- ── MAIN ── -->
  <main class="main">

    <!-- ──────────────── ONBOARDING ──────────────── -->
    <div class="screen" id="screen-onboard">
      <div class="onboard-wrap">
        <div class="onboard-logo">
          <div class="name">Career<span>Path</span></div>
          <div class="sub">Tu coach de empleabilidad UTP — Configura tu perfil</div>
        </div>
        <div class="onboard-step">
          <div class="step-num done">✓</div>
          <div>
            <div class="step-title">Tu perfil universitario</div>
            <div class="step-desc">Carrera, ciclo y sede completados</div>
          </div>
          <span class="badge badge-green" style="margin-left:auto;">Listo</span>
        </div>
        <div class="onboard-step active-step">
          <div class="step-num">2</div>
          <div>
            <div class="step-title">Tus habilidades actuales</div>
            <div class="step-desc">Dinos qué sabes hacer hoy</div>
          </div>
        </div>
        <div class="onboard-step">
          <div class="step-num pending">3</div>
          <div>
            <div class="step-title">Tu meta laboral</div>
            <div class="step-desc">¿A qué puesto apuntas?</div>
          </div>
        </div>
        <div class="form-section">
          <div class="form-label">¿Qué habilidades tienes? (selecciona las que apliquen)</div>
          <div class="tags-pick">
            <button class="tag-pick selected" onclick="toggleTag(this)">HTML/CSS</button>
            <button class="tag-pick selected" onclick="toggleTag(this)">JavaScript</button>
            <button class="tag-pick selected" onclick="toggleTag(this)">SQL</button>
            <button class="tag-pick" onclick="toggleTag(this)">React</button>
            <button class="tag-pick" onclick="toggleTag(this)">Python</button>
            <button class="tag-pick" onclick="toggleTag(this)">Figma</button>
            <button class="tag-pick" onclick="toggleTag(this)">Power BI</button>
            <button class="tag-pick" onclick="toggleTag(this)">Git/GitHub</button>
            <button class="tag-pick" onclick="toggleTag(this)">TypeScript</button>
            <button class="tag-pick" onclick="toggleTag(this)">Node.js</button>
          </div>
          <div class="form-label" style="margin-top:8px;">Meta laboral</div>
          <input class="form-input" value="Desarrollador frontend junior" style="margin-bottom:20px;">
          <button class="btn-primary" onclick="goScreen('dashboard')">Generar mi diagnóstico →</button>
        </div>
      </div>
    </div>

    <!-- ──────────────── DASHBOARD ──────────────── -->
    <div class="screen active" id="screen-dashboard">
      <div class="greeting">
        <div class="greeting-name">Hola, Andrea 👋</div>
        <div class="greeting-sub">Ing. de Sistemas · 8vo ciclo · UTP Lima Norte</div>
      </div>

      <div class="metric-row">
        <div class="metric">
          <div class="metric-label">Perfil completado</div>
          <div class="metric-value">72<span style="font-size:16px;color:var(--text-3);">%</span></div>
          <div class="metric-tag up">↑ +8% esta semana</div>
        </div>
        <div class="metric">
          <div class="metric-label">Score de CV</div>
          <div class="metric-value">68<span style="font-size:16px;color:var(--text-3);">/100</span></div>
          <div class="metric-tag warn">Mejorable</div>
        </div>
        <div class="metric">
          <div class="metric-label">Empleos compatibles</div>
          <div class="metric-value">14</div>
          <div class="metric-tag up">nuevos esta semana</div>
        </div>
      </div>

      <div class="two-col">
        <div class="card">
          <div class="card-title">↗ Próximo paso del roadmap</div>
          <div style="font-size:15px;font-weight:500;margin-bottom:4px;">Completar curso de React</div>
          <div style="font-size:13px;color:var(--text-3);margin-bottom:12px;">Semana 2 de 8 · Udemy</div>
          <div class="mini-prog">
            <div class="mini-prog-bar"><div class="mini-prog-fill" style="width:25%;"></div></div>
            <span style="font-size:12px;color:var(--text-3);">25%</span>
          </div>
        </div>
        <div class="card">
          <div class="card-title">⚠ Brecha crítica</div>
          <div style="font-size:15px;font-weight:500;margin-bottom:4px;">React.js</div>
          <div style="font-size:13px;color:var(--text-3);margin-bottom:10px;">Requerido en 89% de ofertas frontend</div>
          <span class="badge badge-amber">Alta prioridad</span>
        </div>
      </div>

      <div class="card">
        <div class="card-title">◈ Empleos recomendados hoy</div>
        <div class="job-item">
          <div class="job-logo">GL</div>
          <div class="job-body">
            <div class="job-title">Practicante Frontend Developer</div>
            <div class="job-company">Globant · Lima · S/. 1,200 – 1,800</div>
            <div class="job-tags">
              <span class="badge badge-green">85% compatible</span>
              <span class="badge badge-blue">Prácticas</span>
              <span class="badge badge-gray">React · JS</span>
            </div>
          </div>
          <button class="job-cta">Postular</button>
        </div>
        <div class="job-item">
          <div class="job-logo">IN</div>
          <div class="job-body">
            <div class="job-title">Junior React Developer</div>
            <div class="job-company">Intercorp Tech · Lima · S/. 2,000 – 2,800</div>
            <div class="job-tags">
              <span class="badge badge-green">71% compatible</span>
              <span class="badge badge-purple">Full-time</span>
              <span class="badge badge-gray">React · Git</span>
            </div>
          </div>
          <button class="job-cta">Postular</button>
        </div>
        <button class="btn-secondary" style="margin-top:14px;" onclick="goScreen('jobs')">Ver todos los empleos →</button>
      </div>
    </div>

    <!-- ──────────────── BRECHAS ──────────────── -->
    <div class="screen" id="screen-brechas">
      <div class="page-header">
        <div class="page-title">Diagnóstico de brechas</div>
        <div class="page-sub">Comparado con 240 ofertas de Desarrollador Frontend en Lima</div>
      </div>

      <div class="card">
        <div class="card-title">Habilidades técnicas</div>
        <div class="skill-row">
          <div class="skill-name">HTML / CSS</div>
          <div class="pbar-wrap"><div class="pbar-fill" style="width:90%;background:var(--green);"></div></div>
          <div class="skill-pct">90%</div>
          <span class="badge badge-green">Fuerte</span>
        </div>
        <div class="skill-row">
          <div class="skill-name">JavaScript</div>
          <div class="pbar-wrap"><div class="pbar-fill" style="width:75%;background:var(--green);"></div></div>
          <div class="skill-pct">75%</div>
          <span class="badge badge-green">Bueno</span>
        </div>
        <div class="skill-row">
          <div class="skill-name">React.js</div>
          <div class="pbar-wrap"><div class="pbar-fill" style="width:20%;background:var(--amber);"></div></div>
          <div class="skill-pct">20%</div>
          <span class="badge badge-amber">Brecha</span>
        </div>
        <div class="skill-row">
          <div class="skill-name">Git / GitHub</div>
          <div class="pbar-wrap"><div class="pbar-fill" style="width:55%;background:var(--amber);"></div></div>
          <div class="skill-pct">55%</div>
          <span class="badge badge-amber">Mejorar</span>
        </div>
        <div class="skill-row">
          <div class="skill-name">TypeScript</div>
          <div class="pbar-wrap"><div class="pbar-fill" style="width:5%;background:var(--red);"></div></div>
          <div class="skill-pct">5%</div>
          <span class="badge badge-red">Crítico</span>
        </div>
        <div class="skill-row">
          <div class="skill-name">Node.js / APIs</div>
          <div class="pbar-wrap"><div class="pbar-fill" style="width:10%;background:var(--red);"></div></div>
          <div class="skill-pct">10%</div>
          <span class="badge badge-red">Crítico</span>
        </div>
      </div>

      <div class="card">
        <div class="card-title">Habilidades blandas</div>
        <div class="skill-row">
          <div class="skill-name">Trabajo en equipo</div>
          <div class="pbar-wrap"><div class="pbar-fill" style="width:80%;background:var(--green);"></div></div>
          <div class="skill-pct">80%</div>
          <span class="badge badge-green">Fuerte</span>
        </div>
        <div class="skill-row">
          <div class="skill-name">Inglés técnico</div>
          <div class="pbar-wrap"><div class="pbar-fill" style="width:40%;background:var(--amber);"></div></div>
          <div class="skill-pct">40%</div>
          <span class="badge badge-amber">Mejorar</span>
        </div>
        <div class="skill-row">
          <div class="skill-name">Comunicación</div>
          <div class="pbar-wrap"><div class="pbar-fill" style="width:70%;background:var(--green);"></div></div>
          <div class="skill-pct">70%</div>
          <span class="badge badge-green">Bueno</span>
        </div>
      </div>

      <button class="btn-primary" onclick="goScreen('roadmap')">Generar roadmap basado en mis brechas →</button>
    </div>

    <!-- ──────────────── ROADMAP ──────────────── -->
    <div class="screen" id="screen-roadmap">
      <div class="page-header">
        <div class="page-title">Tu roadmap personalizado</div>
        <div class="page-sub">Meta: Desarrollador Frontend Junior · 12 semanas</div>
      </div>

      <div class="big-prog-wrap">
        <div class="big-prog-header">
          <span class="big-prog-label">Progreso general</span>
          <span class="big-prog-pct">20%</span>
        </div>
        <div class="big-pbar"><div class="big-pbar-fill" style="width:20%;"></div></div>
        <div class="big-prog-stages">
          <span class="prog-stage done">Semana 1</span>
          <span class="prog-stage done">Semana 2</span>
          <span class="prog-stage">Semana 5</span>
          <span class="prog-stage">Semana 8</span>
          <span class="prog-stage">Semana 12</span>
        </div>
      </div>

      <div class="card">
        <div class="road-step">
          <div class="road-dot-col">
            <div class="road-dot" style="background:var(--green);border:2px solid var(--green-dark);"></div>
            <div class="road-line"></div>
          </div>
          <div class="road-content">
            <div class="road-title">Reforzar JavaScript avanzado</div>
            <div class="road-desc">Closures, promesas, async/await. Recurso: JavaScript.info (gratis)</div>
            <div class="road-week"><span class="badge badge-green">✓ Completado</span> Semana 1</div>
          </div>
        </div>
        <div class="road-step">
          <div class="road-dot-col">
            <div class="road-dot" style="background:var(--amber);"></div>
            <div class="road-line"></div>
          </div>
          <div class="road-content">
            <div class="road-title">Curso de React.js desde cero</div>
            <div class="road-desc">Hooks, estado, componentes. Recurso: Udemy — React · La guía completa</div>
            <div class="road-week"><span class="badge badge-amber">En curso</span> Semanas 2–5</div>
          </div>
        </div>
        <div class="road-step">
          <div class="road-dot-col">
            <div class="road-dot" style="background:var(--border);"></div>
            <div class="road-line"></div>
          </div>
          <div class="road-content">
            <div class="road-title">Proyecto personal con React + API</div>
            <div class="road-desc">Construir una app con consumo de API pública. Subir a GitHub con README.</div>
            <div class="road-week"><span class="badge badge-gray">Pendiente</span> Semana 6</div>
          </div>
        </div>
        <div class="road-step">
          <div class="road-dot-col">
            <div class="road-dot" style="background:var(--border);"></div>
            <div class="road-line"></div>
          </div>
          <div class="road-content">
            <div class="road-title">Git avanzado + GitHub portfolio</div>
            <div class="road-desc">Ramas, pull requests, código limpio. Perfil GitHub listo para recruiters.</div>
            <div class="road-week"><span class="badge badge-gray">Pendiente</span> Semana 7</div>
          </div>
        </div>
        <div class="road-step">
          <div class="road-dot-col">
            <div class="road-dot" style="background:var(--border);"></div>
          </div>
          <div class="road-content" style="padding-bottom:0;">
            <div class="road-title">Optimizar CV con IA + postular</div>
            <div class="road-desc">Usar CareerPath CV Score, aplicar a 5 posiciones compatibles del feed.</div>
            <div class="road-week"><span class="badge badge-gray">Pendiente</span> Semanas 8–12</div>
          </div>
        </div>
      </div>
    </div>

    <!-- ──────────────── CV ANALYZER ──────────────── -->
    <div class="screen" id="screen-cv">
      <div class="page-header">
        <div class="page-title">Analizador de CV con IA</div>
        <div class="page-sub">Sube tu CV y recibe feedback inmediato</div>
      </div>

      <div class="upload-zone">
        <div class="upload-icon">📄</div>
        <div class="upload-text">Arrastra tu CV aquí o haz clic para seleccionar</div>
        <div class="upload-sub">PDF · máx. 5 MB</div>
      </div>

      <div class="card">
        <div style="display:flex;align-items:center;gap:18px;margin-bottom:18px;">
          <div class="cv-score-ring">
            <div class="cv-score-num">68</div>
            <div class="cv-score-lbl">CV Score</div>
          </div>
          <div>
            <div style="font-size:16px;font-weight:600;margin-bottom:3px;">Andrea Campos Ríos</div>
            <div style="font-size:13px;color:var(--text-3);margin-bottom:10px;">CV analizado · hace 2 horas</div>
            <span class="badge badge-amber">Mejorable — 68/100</span>
          </div>
        </div>

        <div style="border-top:1px solid var(--border-light);padding-top:16px;">
          <div class="card-title" style="margin-bottom:12px;">Sugerencias de mejora</div>
          <div class="sug-row" style="padding-top:0;">
            <div class="sug-icon" style="background:var(--red-light);color:var(--red);">!</div>
            <div class="sug-body">
              <div class="sug-tag" style="color:var(--red);">Crítico · Sección de proyectos</div>
              <div class="sug-text">No tienes proyectos listados. Los reclutadores técnicos lo buscan primero. Añade al menos 2 proyectos con links a GitHub.</div>
            </div>
          </div>
          <div class="sug-row">
            <div class="sug-icon" style="background:var(--amber-light);color:var(--amber);">~</div>
            <div class="sug-body">
              <div class="sug-tag" style="color:#92400E;">Mejorar · Descripción de experiencia</div>
              <div class="sug-text">Usa verbos de acción y cuantifica logros. Cambia "Ayudé en el desarrollo" por "Desarrollé módulo X que redujo el tiempo de carga en 30%".</div>
            </div>
          </div>
          <div class="sug-row">
            <div class="sug-icon" style="background:var(--green-light);color:var(--green);">✓</div>
            <div class="sug-body">
              <div class="sug-tag" style="color:var(--green-dark);">Bueno · Formato</div>
              <div class="sug-text">El formato es limpio y legible. Mantén máximo 1 página para posiciones junior.</div>
            </div>
          </div>
        </div>
      </div>
      <button class="btn-primary" style="margin-top:14px;">Subir nueva versión del CV</button>
    </div>

    <!-- ──────────────── EMPLEOS ──────────────── -->
    <div class="screen" id="screen-jobs">
      <div class="page-header">
        <div class="page-title">Empleos para ti</div>
        <div class="page-sub">14 oportunidades compatibles con tu perfil</div>
      </div>

      <div class="card">
        <div class="job-item">
          <div class="job-logo">GL</div>
          <div class="job-body">
            <div class="job-title">Practicante Frontend Developer</div>
            <div class="job-company">Globant · Lima · S/. 1,200 – 1,800</div>
            <div class="job-tags">
              <span class="badge badge-green">85% compatible</span>
              <span class="badge badge-blue">Prácticas</span>
              <span class="badge badge-gray">React · JS</span>
            </div>
          </div>
          <button class="job-cta">Postular</button>
        </div>
        <div class="job-item">
          <div class="job-logo">IN</div>
          <div class="job-body">
            <div class="job-title">Junior React Developer</div>
            <div class="job-company">Intercorp Tech · Lima · S/. 2,000 – 2,800</div>
            <div class="job-tags">
              <span class="badge badge-green">71% compatible</span>
              <span class="badge badge-purple">Full-time</span>
              <span class="badge badge-gray">React · Git</span>
            </div>
          </div>
          <button class="job-cta">Postular</button>
        </div>
        <div class="job-item">
          <div class="job-logo">PF</div>
          <div class="job-body">
            <div class="job-title">Practicante Web · Equipo Digital</div>
            <div class="job-company">Pacífico Seguros · Lima · S/. 1,000 – 1,400</div>
            <div class="job-tags">
              <span class="badge badge-green">68% compatible</span>
              <span class="badge badge-blue">Prácticas</span>
              <span class="badge badge-gray">JS · CSS</span>
            </div>
          </div>
          <button class="job-cta">Postular</button>
        </div>
        <div class="job-item">
          <div class="job-logo">BCP</div>
          <div class="job-body">
            <div class="job-title">Trainee Desarrollador Frontend</div>
            <div class="job-company">BCP · Lima · S/. 1,500 – 2,200</div>
            <div class="job-tags">
              <span class="badge badge-green">61% compatible</span>
              <span class="badge badge-purple">Trainee</span>
              <span class="badge badge-gray">React · API</span>
            </div>
          </div>
          <button class="job-cta">Postular</button>
        </div>
        <div class="job-item">
          <div class="job-logo">NE</div>
          <div class="job-body">
            <div class="job-title">Frontend Intern</div>
            <div class="job-company">Netzun · Remoto · S/. 900 – 1,200</div>
            <div class="job-tags">
              <span class="badge badge-green">58% compatible</span>
              <span class="badge badge-blue">Prácticas</span>
              <span class="badge badge-gray">Vue · CSS</span>
            </div>
          </div>
          <button class="job-cta">Postular</button>
        </div>
      </div>

      <button class="btn-secondary" style="margin-top:14px;width:100%;">Cargar más empleos compatibles</button>
    </div>

  </main>
</div>

<script>
  function goScreen(id) {
    document.querySelectorAll('.screen').forEach(s => s.classList.remove('active'));
    document.getElementById('screen-' + id).classList.add('active');
    document.querySelectorAll('[data-screen]').forEach(b => {
      b.classList.toggle('active', b.dataset.screen === id);
    });
    document.querySelectorAll('[data-sb]').forEach(b => {
      b.classList.toggle('active', b.dataset.sb === id);
    });
  }

  function toggleTag(el) {
    el.classList.toggle('selected');
  }
</script>
</body>
</html>
