# facupiccolella-png.github.io
<!DOCTYPE html>
<html lang="es">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>Kahuak · Informe de Creativos · 30 días</title>
<link href="https://fonts.googleapis.com/css2?family=DM+Sans:ital,opsz,wght@0,9..40,300;0,9..40,400;0,9..40,500;0,9..40,600;1,9..40,300&family=DM+Mono:wght@400;500&display=swap" rel="stylesheet">
<script src="https://cdnjs.cloudflare.com/ajax/libs/Chart.js/4.4.1/chart.umd.js"></script>
<style>
  :root {
    --red:     #CC1111;
    --dark:    #111110;
    --mid:     #3d3d3a;
    --muted:   #73726c;
    --faint:   #a8a89f;
    --border:  #e4e4df;
    --bg:      #f8f8f5;
    --bg2:     #f0f0eb;
    --white:   #ffffff;
    --green:   #1d9e75;
    --green-bg:#eaf3de;
    --green-fg:#27500a;
    --amber:   #ef9f27;
    --amber-bg:#faeeda;
    --amber-fg:#633806;
    --red-bg:  #fcebeb;
    --red-fg:  #791f1f;
    --blue:    #3266ad;
    --blue-bg: #e6f1fb;
    --blue-fg: #0c447c;
    --pink:    #ff3fa4;
  }

  *, *::before, *::after { box-sizing: border-box; margin: 0; padding: 0; }

  body {
    font-family: 'DM Sans', sans-serif;
    background: var(--bg);
    color: var(--dark);
    min-height: 100vh;
    font-size: 14px;
    line-height: 1.5;
  }

  /* ── HEADER ── */
  header {
    background: var(--dark);
    padding: 0 48px;
    display: flex;
    align-items: center;
    justify-content: space-between;
    height: 64px;
    position: sticky;
    top: 0;
    z-index: 100;
  }

  .logo-wrap {
    display: flex;
    align-items: center;
    gap: 14px;
  }

  .logo-text {
    font-size: 18px;
    font-weight: 600;
    letter-spacing: 0.06em;
    color: var(--red);
  }

  .logo-sub {
    font-size: 11px;
    color: #666;
    letter-spacing: 0.08em;
    text-transform: uppercase;
  }

  .logo-divider {
    width: 1px;
    height: 28px;
    background: #333;
  }

  .header-meta {
    font-size: 12px;
    color: #555;
    letter-spacing: 0.02em;
    display: flex;
    align-items: center;
    gap: 20px;
  }

  .header-badge {
    background: #1a1a18;
    border: 1px solid #333;
    padding: 4px 12px;
    border-radius: 20px;
    font-size: 11px;
    color: #888;
    font-family: 'DM Mono', monospace;
  }

  .iso-pink {
    width: 28px;
    height: 28px;
    background: var(--pink);
    border-radius: 50%;
    display: flex;
    align-items: center;
    justify-content: center;
    font-size: 16px;
    font-weight: 800;
    color: #000;
    font-family: 'DM Sans', sans-serif;
    flex-shrink: 0;
  }

  /* ── HERO STRIP ── */
  .hero {
    background: var(--dark);
    padding: 40px 48px 48px;
    border-bottom: 1px solid #222;
  }

  .hero-label {
    font-size: 11px;
    letter-spacing: 0.12em;
    text-transform: uppercase;
    color: var(--faint);
    margin-bottom: 8px;
    font-family: 'DM Mono', monospace;
  }

  .hero-title {
    font-size: clamp(28px, 4vw, 42px);
    font-weight: 300;
    color: #fff;
    line-height: 1.15;
    margin-bottom: 6px;
  }

  .hero-title strong {
    font-weight: 600;
    color: var(--red);
  }

  .hero-subtitle {
    font-size: 14px;
    color: #555;
    margin-bottom: 36px;
  }

  /* KPI row */
  .kpi-row {
    display: grid;
    grid-template-columns: repeat(4, 1fr);
    gap: 1px;
    background: #222;
    border: 1px solid #222;
    border-radius: 10px;
    overflow: hidden;
  }

  .kpi {
    background: #161614;
    padding: 20px 24px;
  }

  .kpi-val {
    font-size: 32px;
    font-weight: 500;
    color: #fff;
    line-height: 1;
    margin-bottom: 6px;
    font-variant-numeric: tabular-nums;
  }

  .kpi-label {
    font-size: 11px;
    text-transform: uppercase;
    letter-spacing: 0.08em;
    color: #555;
    margin-bottom: 4px;
    font-family: 'DM Mono', monospace;
  }

  .kpi-delta {
    font-size: 12px;
    display: flex;
    align-items: center;
    gap: 4px;
  }

  .delta-good { color: var(--green); }
  .delta-bad  { color: #e24b4a; }
  .delta-neu  { color: #555; }

  /* ── TABS ── */
  .tabs-wrap {
    background: var(--white);
    border-bottom: 1px solid var(--border);
    padding: 0 48px;
    position: sticky;
    top: 64px;
    z-index: 90;
  }

  .tabs {
    display: flex;
    gap: 0;
  }

  .tab {
    padding: 16px 20px;
    font-size: 13px;
    font-weight: 500;
    color: var(--muted);
    cursor: pointer;
    border-bottom: 2px solid transparent;
    transition: color .15s, border-color .15s;
    background: none;
    border-top: none;
    border-left: none;
    border-right: none;
    white-space: nowrap;
  }

  .tab:hover { color: var(--dark); }
  .tab.active { color: var(--dark); border-bottom-color: var(--dark); }

  /* ── CONTENT ── */
  .content {
    max-width: 1100px;
    margin: 0 auto;
    padding: 40px 48px;
  }

  .panel { display: none; }
  .panel.active { display: block; }

  .section-label {
    font-size: 10px;
    font-family: 'DM Mono', monospace;
    letter-spacing: 0.12em;
    text-transform: uppercase;
    color: var(--faint);
    margin-bottom: 12px;
    margin-top: 32px;
  }

  .section-label:first-child { margin-top: 0; }

  /* ── AD TABLE ── */
  .ad-table {
    width: 100%;
    border-collapse: collapse;
    background: var(--white);
    border-radius: 10px;
    overflow: hidden;
    border: 1px solid var(--border);
  }

  .ad-table thead th {
    background: var(--bg2);
    padding: 10px 16px;
    font-size: 10px;
    font-family: 'DM Mono', monospace;
    letter-spacing: 0.08em;
    text-transform: uppercase;
    color: var(--muted);
    text-align: left;
    font-weight: 500;
    border-bottom: 1px solid var(--border);
  }

  .ad-table thead th:not(:first-child) { text-align: right; }
  .ad-table thead th:last-child { text-align: center; }

  .ad-table tbody tr {
    border-bottom: 1px solid var(--border);
    transition: background .1s;
  }

  .ad-table tbody tr:last-child { border-bottom: none; }
  .ad-table tbody tr:hover { background: var(--bg); }

  .ad-table td {
    padding: 12px 16px;
    vertical-align: middle;
  }

  .ad-table td:not(:first-child) { text-align: right; }
  .ad-table td:last-child { text-align: center; }

  .ad-name { font-weight: 500; font-size: 13px; color: var(--dark); }
  .ad-camp { font-size: 11px; color: var(--faint); margin-top: 1px; }

  .num-good { color: var(--green); font-weight: 500; font-family: 'DM Mono', monospace; }
  .num-mid  { color: var(--amber); font-weight: 500; font-family: 'DM Mono', monospace; }
  .num-bad  { color: #e24b4a;      font-weight: 500; font-family: 'DM Mono', monospace; }
  .num      { font-family: 'DM Mono', monospace; font-size: 13px; }

  .badge {
    display: inline-block;
    font-size: 10px;
    font-weight: 600;
    font-family: 'DM Mono', monospace;
    letter-spacing: 0.06em;
    padding: 3px 8px;
    border-radius: 4px;
  }

  .bg { background: var(--green-bg); color: var(--green-fg); }
  .br { background: var(--red-bg);   color: var(--red-fg); }
  .ba { background: var(--amber-bg); color: var(--amber-fg); }
  .bb { background: var(--blue-bg);  color: var(--blue-fg); }

  .no-conv { background: #fcebeb33; }

  /* ── CHART WRAPPERS ── */
  .chart-card {
    background: var(--white);
    border: 1px solid var(--border);
    border-radius: 10px;
    padding: 24px;
  }

  .chart-title {
    font-size: 13px;
    font-weight: 500;
    color: var(--dark);
    margin-bottom: 4px;
  }

  .chart-sub {
    font-size: 12px;
    color: var(--muted);
    margin-bottom: 20px;
  }

  .charts-grid {
    display: grid;
    grid-template-columns: 1fr 1fr;
    gap: 16px;
  }

  .chart-full { grid-column: 1 / -1; }

  /* ── COMPARISON ── */
  .cmp-grid {
    display: grid;
    grid-template-columns: repeat(2, 1fr);
    gap: 12px;
    margin-bottom: 12px;
  }

  .cmp-card {
    background: var(--white);
    border: 1px solid var(--border);
    border-radius: 10px;
    padding: 18px 20px;
  }

  .cmp-period {
    font-size: 10px;
    font-family: 'DM Mono', monospace;
    letter-spacing: 0.1em;
    text-transform: uppercase;
    color: var(--faint);
    margin-bottom: 6px;
  }

  .cmp-val {
    font-size: 26px;
    font-weight: 500;
    line-height: 1;
    margin-bottom: 4px;
  }

  .cmp-label { font-size: 12px; color: var(--muted); margin-bottom: 8px; }

  .bar-bg { height: 4px; background: var(--bg2); border-radius: 2px; }
  .bar-fill { height: 4px; border-radius: 2px; }

  .cmp-section-title {
    font-size: 14px;
    font-weight: 500;
    color: var(--dark);
    margin: 28px 0 12px;
    padding-bottom: 8px;
    border-bottom: 1px solid var(--border);
  }

  /* ── INSIGHTS ── */
  .insight {
    border-radius: 10px;
    padding: 18px 20px;
    margin-bottom: 12px;
    line-height: 1.65;
    font-size: 13.5px;
  }

  .insight strong { display: block; margin-bottom: 6px; font-size: 14px; }

  .ins-green { background: var(--green-bg); border-left: 3px solid var(--green); color: var(--green-fg); }
  .ins-amber { background: var(--amber-bg); border-left: 3px solid var(--amber); color: var(--amber-fg); }
  .ins-red   { background: var(--red-bg);   border-left: 3px solid #e24b4a;     color: var(--red-fg); }
  .ins-blue  { background: var(--blue-bg);  border-left: 3px solid var(--blue);  color: var(--blue-fg); }

  .priorities {
    background: var(--dark);
    border-radius: 10px;
    padding: 24px 28px;
    margin-top: 20px;
    color: #fff;
  }

  .priorities h3 {
    font-size: 12px;
    font-family: 'DM Mono', monospace;
    letter-spacing: 0.1em;
    text-transform: uppercase;
    color: #555;
    margin-bottom: 16px;
  }

  .priority-item {
    display: flex;
    align-items: flex-start;
    gap: 14px;
    padding: 12px 0;
    border-bottom: 1px solid #222;
    font-size: 13px;
    color: #ccc;
    line-height: 1.5;
  }

  .priority-item:last-child { border-bottom: none; }

  .priority-num {
    width: 24px;
    height: 24px;
    border-radius: 50%;
    background: #222;
    display: flex;
    align-items: center;
    justify-content: center;
    font-size: 11px;
    font-family: 'DM Mono', monospace;
    color: #555;
    flex-shrink: 0;
    margin-top: 1px;
  }

  .priority-item strong { color: #fff; }

  /* ── FOOTER ── */
  footer {
    background: var(--dark);
    padding: 24px 48px;
    display: flex;
    align-items: center;
    justify-content: space-between;
    margin-top: 60px;
  }

  footer .footer-left {
    display: flex;
    align-items: center;
    gap: 12px;
  }

  footer .footer-logo { font-size: 14px; font-weight: 600; color: var(--red); letter-spacing: 0.06em; }
  footer .footer-meta { font-size: 11px; color: #444; }

  .footer-badge {
    font-size: 10px;
    font-family: 'DM Mono', monospace;
    color: #444;
    letter-spacing: 0.06em;
  }

  /* ── RESPONSIVE ── */
  @media (max-width: 768px) {
    header { padding: 0 20px; }
    .hero { padding: 28px 20px 32px; }
    .kpi-row { grid-template-columns: repeat(2, 1fr); }
    .tabs-wrap { padding: 0 20px; overflow-x: auto; }
    .content { padding: 28px 20px; }
    .charts-grid { grid-template-columns: 1fr; }
    .cmp-grid { grid-template-columns: 1fr; }
    footer { padding: 20px; flex-direction: column; gap: 12px; text-align: center; }
  }

  /* ── ANIMATIONS ── */
  @keyframes fadeUp {
    from { opacity: 0; transform: translateY(12px); }
    to   { opacity: 1; transform: translateY(0); }
  }

  .panel.active > * {
    animation: fadeUp .25s ease both;
  }

  .panel.active > *:nth-child(2) { animation-delay: .05s; }
  .panel.active > *:nth-child(3) { animation-delay: .10s; }
  .panel.active > *:nth-child(4) { animation-delay: .15s; }
  .panel.active > *:nth-child(5) { animation-delay: .20s; }
</style>
</head>
<body>

<!-- HEADER -->
<header>
  <div class="logo-wrap">
    <div>
      <div class="logo-text">KAHUAK</div>
      <div class="logo-sub">mendoza turismo</div>
    </div>
    <div class="logo-divider"></div>
    <div style="font-size:13px;color:#444;font-weight:300;">Informe de Creativos</div>
  </div>
  <div class="header-meta">
    <span class="header-badge">26 feb – 26 mar 2026</span>
    <span class="header-badge">Meta Ads</span>
    <div class="iso-pink">b</div>
  </div>
</header>

<!-- HERO -->
<div class="hero">
  <div class="hero-label">Análisis de performance · Últimos 30 días</div>
  <h1 class="hero-title">Creativos que <strong>convierten</strong><br>y creativos que hay que pausar</h1>
  <p class="hero-subtitle">Cuenta 379224961876128 · Campañas activas · Comparado con período de 90 días</p>

  <div class="kpi-row">
    <div class="kpi">
      <div class="kpi-label">Conversaciones</div>
      <div class="kpi-val">378</div>
      <div class="kpi-delta delta-neu">últimos 30 días</div>
    </div>
    <div class="kpi">
      <div class="kpi-label">Mejor CPConv</div>
      <div class="kpi-val">$377</div>
      <div class="kpi-delta delta-good">↓ mejor que $438 en 90d</div>
    </div>
    <div class="kpi">
      <div class="kpi-label">Gasto total</div>
      <div class="kpi-val">$206K</div>
      <div class="kpi-delta delta-neu">ARS · 13 anuncios</div>
    </div>
    <div class="kpi">
      <div class="kpi-label">CPConv promedio</div>
      <div class="kpi-val">$618</div>
      <div class="kpi-delta delta-neu">cuenta general</div>
    </div>
  </div>
</div>

<!-- TABS -->
<div class="tabs-wrap">
  <div class="tabs">
    <button class="tab active" onclick="showTab('resumen')">Resumen</button>
    <button class="tab" onclick="showTab('ranking')">Ranking de anuncios</button>
    <button class="tab" onclick="showTab('comparativa')">30 vs 90 días</button>
    <button class="tab" onclick="showTab('conclusiones')">Conclusiones y acción</button>
  </div>
</div>

<!-- CONTENT -->
<div class="content">

  <!-- ── PANEL RESUMEN ── -->
  <div id="panel-resumen" class="panel active">

    <div class="section-label">Conversaciones por anuncio</div>
    <div class="chart-card">
      <div class="chart-title">Conversaciones generadas — últimos 30 días</div>
      <div class="chart-sub">Anuncios con al menos 1 conversación vía WhatsApp</div>
      <div style="position:relative;height:220px;"><canvas id="conv30Chart"></canvas></div>
    </div>

    <div class="section-label" style="margin-top:28px;">Todos los anuncios activos</div>
    <table class="ad-table">
      <thead>
        <tr>
          <th>Anuncio</th>
          <th>Conv.</th>
          <th>CPConv ARS</th>
          <th>Gasto ARS</th>
          <th>CTR</th>
          <th>Estado</th>
        </tr>
      </thead>
      <tbody>
        <tr>
          <td><div class="ad-name">UGC marti · Aconcagua Advantage+</div><div class="ad-camp">Advantage+ · Activo</div></td>
          <td><span class="num" style="font-weight:600">179</span></td>
          <td><span class="num-good">$432</span></td>
          <td><span class="num">$77.371</span></td>
          <td><span class="num">1,27%</span></td>
          <td><span class="badge bg">REPLICAR</span></td>
        </tr>
        <tr>
          <td><div class="ad-name">Rafting 5</div><div class="ad-camp">AD SET 2 / Rafting · Activo</div></td>
          <td><span class="num" style="font-weight:600">155</span></td>
          <td><span class="num-mid">$602</span></td>
          <td><span class="num">$93.346</span></td>
          <td><span class="num">1,46%</span></td>
          <td><span class="badge bb">MANTENER</span></td>
        </tr>
        <tr>
          <td><div class="ad-name">Rafting 6</div><div class="ad-camp">AD SET 2 / Rafting · Activo</div></td>
          <td><span class="num" style="font-weight:600">21</span></td>
          <td><span class="num-good">$517</span></td>
          <td><span class="num">$10.861</span></td>
          <td><span class="num">0,56%</span></td>
          <td><span class="badge bb">MANTENER</span></td>
        </tr>
        <tr>
          <td><div class="ad-name">Carrusel publi Aconcagua · Advantage+</div><div class="ad-camp">Advantage+ · Activo</div></td>
          <td><span class="num" style="font-weight:600">5</span></td>
          <td><span class="num-good">$377</span></td>
          <td><span class="num">$1.883</span></td>
          <td><span class="num">2,16%</span></td>
          <td><span class="badge ba">ESCALAR</span></td>
        </tr>
        <tr>
          <td><div class="ad-name">Clásico tour · Aconcagua Advantage+</div><div class="ad-camp">Advantage+ · Activo</div></td>
          <td><span class="num" style="font-weight:600">2</span></td>
          <td><span class="num-mid">$477</span></td>
          <td><span class="num">$954</span></td>
          <td><span class="num">2,37%</span></td>
          <td><span class="badge bb">MANTENER</span></td>
        </tr>
        <tr>
          <td><div class="ad-name">Mejores · Aconcagua Advantage+</div><div class="ad-camp">Advantage+ · Activo</div></td>
          <td><span class="num" style="font-weight:600">2</span></td>
          <td><span class="num-mid">$580</span></td>
          <td><span class="num">$1.161</span></td>
          <td><span class="num">3,04%</span></td>
          <td><span class="badge ba">REVISAR</span></td>
        </tr>
        <tr>
          <td><div class="ad-name">Rafting 7</div><div class="ad-camp">AD SET 2 / Rafting · Activo</div></td>
          <td><span class="num" style="font-weight:600">9</span></td>
          <td><span class="num-bad">$1.103</span></td>
          <td><span class="num">$9.931</span></td>
          <td><span class="num">0,63%</span></td>
          <td><span class="badge br">PAUSAR</span></td>
        </tr>
        <tr>
          <td><div class="ad-name">Clásico tour · Intereses</div><div class="ad-camp">AD SET / Intereses · Pausado</div></td>
          <td><span class="num" style="font-weight:600">5</span></td>
          <td><span class="num-bad">$1.321</span></td>
          <td><span class="num">$6.603</span></td>
          <td><span class="num">3,23%</span></td>
          <td><span class="badge br">PAUSAR</span></td>
        </tr>
        <tr class="no-conv">
          <td><div class="ad-name">Reel genérico 1 (ambos ad sets)</div><div class="ad-camp">Advantage+ e Intereses · $2.188 gastados</div></td>
          <td><span class="num-bad">0</span></td>
          <td><span class="num" style="color:var(--faint)">—</span></td>
          <td><span class="num">$2.188</span></td>
          <td><span class="num">3,91%</span></td>
          <td><span class="badge br">ELIMINAR</span></td>
        </tr>
        <tr class="no-conv">
          <td><div class="ad-name">Reel genérico 2 · Advantage+</div><div class="ad-camp">Advantage+ · $616 gastados</div></td>
          <td><span class="num-bad">0</span></td>
          <td><span class="num" style="color:var(--faint)">—</span></td>
          <td><span class="num">$616</span></td>
          <td><span class="num">3,39%</span></td>
          <td><span class="badge br">PAUSAR</span></td>
        </tr>
      </tbody>
    </table>

    <div class="section-label" style="margin-top:28px;">Distribución del gasto</div>
    <div class="charts-grid">
      <div class="chart-card">
        <div class="chart-title">Gasto por anuncio</div>
        <div class="chart-sub">2 anuncios concentran el 83% del presupuesto</div>
        <div style="position:relative;height:200px;"><canvas id="spendDonut"></canvas></div>
      </div>
      <div class="chart-card">
        <div class="chart-title">Advantage+ vs Targeting manual</div>
        <div class="chart-sub">CPConv promedio por tipo de audiencia</div>
        <div style="position:relative;height:200px;"><canvas id="targetingChart"></canvas></div>
      </div>
    </div>
  </div>

  <!-- ── PANEL RANKING ── -->
  <div id="panel-ranking" class="panel">

    <div class="section-label">Ranking por eficiencia</div>
    <div class="chart-card chart-full">
      <div class="chart-title">CPConv ARS por anuncio — menor es mejor</div>
      <div class="chart-sub">Solo anuncios con conversaciones. Verde = excelente · Naranja = aceptable · Rojo = ineficiente</div>
      <div style="position:relative;height:300px;"><canvas id="rankChart"></canvas></div>
    </div>

    <div class="section-label" style="margin-top:28px;">Volumen vs Eficiencia</div>
    <div class="chart-card">
      <div class="chart-title">Conversaciones vs CPConv</div>
      <div class="chart-sub">Arriba a la izquierda = mejor (más conv, menor costo)</div>
      <div style="position:relative;height:280px;"><canvas id="bubbleChart"></canvas></div>
    </div>
  </div>

  <!-- ── PANEL COMPARATIVA ── -->
  <div id="panel-comparativa" class="panel">

    <div class="section-label">Evolución entre períodos</div>
    <div class="chart-card chart-full">
      <div class="chart-title">CPConv por anuncio — 90 días vs últimos 30 días</div>
      <div class="chart-sub">Las barras más cortas a la derecha = mejora de eficiencia en el último mes</div>
      <div style="position:relative;height:260px;"><canvas id="cmpChart"></canvas></div>
    </div>

    <div class="cmp-section-title">UGC Marti · Aconcagua Advantage+ — sin fatiga, mejorando</div>
    <div class="cmp-grid">
      <div class="cmp-card">
        <div class="cmp-period">90 días</div>
        <div class="cmp-val">$438</div>
        <div class="cmp-label">CPConv · 190 conversaciones</div>
        <div class="bar-bg"><div class="bar-fill" style="width:100%;background:var(--blue);"></div></div>
      </div>
      <div class="cmp-card">
        <div class="cmp-period">30 días</div>
        <div class="cmp-val" style="color:var(--green)">$432</div>
        <div class="cmp-label">CPConv · 179 conversaciones — mejorando</div>
        <div class="bar-bg"><div class="bar-fill" style="width:98%;background:var(--green);"></div></div>
      </div>
    </div>

    <div class="cmp-section-title">Carrusel publi Aconcagua · Advantage+ — la gran sorpresa del mes</div>
    <div class="cmp-grid">
      <div class="cmp-card">
        <div class="cmp-period">90 días</div>
        <div class="cmp-val" style="color:#e24b4a">$956</div>
        <div class="cmp-label">CPConv promedio — parecía candidato a eliminar</div>
        <div class="bar-bg"><div class="bar-fill" style="width:100%;background:#e24b4a;"></div></div>
      </div>
      <div class="cmp-card">
        <div class="cmp-period">30 días</div>
        <div class="cmp-val" style="color:var(--green)">$377</div>
        <div class="cmp-label">CPConv — el más bajo de toda la cuenta</div>
        <div class="bar-bg"><div class="bar-fill" style="width:39%;background:var(--green);"></div></div>
      </div>
    </div>

    <div class="cmp-section-title">Reels genéricos — caída crítica en el último mes</div>
    <div class="cmp-grid">
      <div class="cmp-card">
        <div class="cmp-period">90 días · Reel genérico 1</div>
        <div class="cmp-val">196 conv</div>
        <div class="cmp-label">$155K · CPConv $793</div>
      </div>
      <div class="cmp-card">
        <div class="cmp-period">30 días · Reel genérico 1</div>
        <div class="cmp-val" style="color:#e24b4a">0 conv</div>
        <div class="cmp-label">$2.2K gastados · Sin ninguna conversación</div>
      </div>
    </div>

    <div class="cmp-section-title">Rafting 7 — empeorando</div>
    <div class="cmp-grid">
      <div class="cmp-card">
        <div class="cmp-period">90 días</div>
        <div class="cmp-val" style="color:var(--amber)">$780</div>
        <div class="cmp-label">CPConv · 26 conversaciones</div>
        <div class="bar-bg"><div class="bar-fill" style="width:59%;background:var(--amber);"></div></div>
      </div>
      <div class="cmp-card">
        <div class="cmp-period">30 días</div>
        <div class="cmp-val" style="color:#e24b4a">$1.103</div>
        <div class="cmp-label">CPConv — 41% más caro que en 90 días</div>
        <div class="bar-bg"><div class="bar-fill" style="width:83%;background:#e24b4a;"></div></div>
      </div>
    </div>
  </div>

  <!-- ── PANEL CONCLUSIONES ── -->
  <div id="panel-conclusiones" class="panel">

    <div class="section-label">Hallazgos del período</div>

    <div class="insight ins-green">
      <strong>✓ UGC Marti sigue siendo el creativo #1 — y está mejorando</strong>
      En los últimos 30 días generó 179 conversaciones con CPConv de $432, levemente mejor que los $438 del período de 90 días. El anuncio <em>no muestra fatiga</em>: el algoritmo Advantage+ sigue encontrando audiencia nueva y convirtiendo con eficiencia creciente. Representa el 47% de todas las conversaciones del mes con el 37% del presupuesto.
    </div>

    <div class="insight ins-green">
      <strong>✓ Carrusel publi Aconcagua (Advantage+) es la gran sorpresa del mes</strong>
      En 90 días tenía un CPConv de $956 — parecía candidato a pausar. En los últimos 30 días su CPConv bajó a <strong>$377</strong>, el más bajo de toda la cuenta, superando incluso al UGC Marti. Con solo $1.9K de gasto y 5 conversaciones el volumen es bajo, pero la señal de eficiencia es muy positiva. Hay que escalar y monitorear.
    </div>

    <div class="insight ins-amber">
      <strong>⚠ Rafting 5 concentra el 45% del presupuesto — riesgo de dependencia</strong>
      $93.3K gastados con 155 conversaciones y CPConv de $602. Es estable y genera volumen, pero concentrar casi la mitad del presupuesto en un solo anuncio es un riesgo: si empieza a fatigarse no hay reemplazo listo. La eficiencia no mejoró respecto a los 90 días ($607 → $602). Hay que diversificar hacia UGC Marti y el carrusel Aconcagua.
    </div>

    <div class="insight ins-red">
      <strong>✕ Los reels genéricos colapsaron en el último mes</strong>
      Reel genérico 1 pasó de 196 conversaciones en 90 días a 0 en los últimos 30, con $2.2K gastados sin resultado. Reel genérico 2 también en 0 conversaciones. CTR sigue siendo alto (3.5–4%), lo que indica que el anuncio todavía genera clics, pero los usuarios llegan al WhatsApp y no convierten — o el algoritmo está mostrando el anuncio a personas menos calificadas. Pausar los dos formatos.
    </div>

    <div class="insight ins-red">
      <strong>✕ Rafting 7 empeoró significativamente</strong>
      CPConv de $1.103 en 30 días vs $780 en 90 días. Con 9 conversaciones y $9.9K de gasto, consume presupuesto que rendiría mucho mejor redirigido al UGC Marti o el carrusel Aconcagua. Pausar.
    </div>

    <div class="insight ins-blue">
      <strong>→ Patrón central: Advantage+ gana, targeting manual pierde — y la brecha se amplió</strong>
      Los 4 anuncios activos en Advantage+ tienen CPConv de $377–$580. Los anuncios en Intereses tienen CPConv de $1.103–$1.321. En el período de 90 días la diferencia era significativa; en los últimos 30 días se amplió todavía más. Meta está favoreciendo claramente Advantage+ en esta cuenta. Los ad sets de Intereses deberían migrarse o cerrarse.
    </div>

    <div class="priorities">
      <h3>Prioridades para los próximos 7 días</h3>
      <div class="priority-item">
        <div class="priority-num">1</div>
        <div><strong>Pausar Rafting 7, Reel genérico 1 y Reel genérico 2.</strong> Están consumiendo presupuesto sin generar conversaciones.</div>
      </div>
      <div class="priority-item">
        <div class="priority-num">2</div>
        <div><strong>Aumentar presupuesto de UGC Marti (Advantage+) en 30–40%.</strong> Es el anuncio más eficiente y no muestra fatiga.</div>
      </div>
      <div class="priority-item">
        <div class="priority-num">3</div>
        <div><strong>Escalar Carrusel publi Aconcagua (Advantage+) y monitorear 7 días.</strong> $377 de CPConv con poco volumen — hay que confirmar que se sostiene.</div>
      </div>
      <div class="priority-item">
        <div class="priority-num">4</div>
        <div><strong>Producir 2–3 nuevas variantes UGC</strong> para reemplazar los reels colapsados y reducir dependencia en Rafting 5.</div>
      </div>
    </div>

  </div>
</div>

<!-- FOOTER -->
<footer>
  <div class="footer-left">
    <div class="footer-logo">KAHUAK</div>
    <div class="footer-meta">mendoza turismo · Informe de Creativos · Meta Ads</div>
  </div>
  <div class="footer-badge">26 feb – 26 mar 2026 · Windsor.ai · Meta Ads API</div>
</footer>

<script>
// Tab switching
function showTab(name) {
  const tabs = ['resumen','ranking','comparativa','conclusiones'];
  document.querySelectorAll('.tab').forEach((t,i) => t.classList.toggle('active', tabs[i]===name));
  document.querySelectorAll('.panel').forEach(p => p.classList.remove('active'));
  document.getElementById('panel-'+name).classList.add('active');
  renderCharts(name);
}

const rendered = {};

function renderCharts(tab) {
  if (rendered[tab]) return;
  rendered[tab] = true;

  if (tab === 'resumen') {
    // Conv bar
    new Chart(document.getElementById('conv30Chart'), {
      type: 'bar',
      data: {
        labels: ['UGC marti Adv+','Rafting 5','Rafting 6','Rafting 7','Carrusel\nAconc. Adv+','Clásico Int.','Clásico Adv+','Mejores Adv+'],
        datasets: [{
          data: [179, 155, 21, 9, 5, 5, 2, 2],
          backgroundColor: ['#1d9e75','#ef9f27','#ef9f2799','#e24b4a','#1d9e7599','#e24b4a99','#73726c','#73726c'],
          borderRadius: 5, borderSkipped: false
        }]
      },
      options: {
        responsive: true, maintainAspectRatio: false,
        plugins: { legend: { display: false }, tooltip: { callbacks: { label: ctx => ' '+ctx.raw+' conversaciones' } } },
        scales: {
          x: { ticks: { font: { size: 11 }, color: '#73726c' }, grid: { display: false } },
          y: { ticks: { font: { size: 11 }, color: '#73726c' }, grid: { color: 'rgba(0,0,0,0.05)' } }
        }
      }
    });

    // Spend donut
    new Chart(document.getElementById('spendDonut'), {
      type: 'doughnut',
      data: {
        labels: ['Rafting 5','UGC marti Adv+','Rafting 7','Rafting 6','Clásico Int.','Resto'],
        datasets: [{ data: [93346,77371,9931,10861,6603,8217], backgroundColor: ['#ef9f27','#3266ad','#e24b4a','#ef9f2755','#e24b4a55','#73726c55'], borderWidth: 0 }]
      },
      options: {
        responsive: true, maintainAspectRatio: false, cutout: '62%',
        plugins: {
          legend: { position: 'right', labels: { font: { size: 11 }, color: '#73726c', boxWidth: 10, padding: 8 } },
          tooltip: { callbacks: { label: ctx => ' $'+Math.round(ctx.raw/1000)+'K ARS' } }
        }
      }
    });

    // Targeting comparison
    new Chart(document.getElementById('targetingChart'), {
      type: 'bar',
      data: {
        labels: ['Advantage+', 'Intereses / Manual'],
        datasets: [{
          label: 'CPConv promedio ARS',
          data: [468, 1212],
          backgroundColor: ['#1d9e75','#e24b4a'],
          borderRadius: 6, borderSkipped: false
        }]
      },
      options: {
        responsive: true, maintainAspectRatio: false,
        plugins: { legend: { display: false }, tooltip: { callbacks: { label: ctx => ' $'+ctx.raw+' CPConv' } } },
        scales: {
          x: { ticks: { font: { size: 12 }, color: '#73726c' }, grid: { display: false } },
          y: { ticks: { font: { size: 11 }, color: '#73726c', callback: v => '$'+v }, grid: { color: 'rgba(0,0,0,0.05)' } }
        }
      }
    });
  }

  if (tab === 'ranking') {
    new Chart(document.getElementById('rankChart'), {
      type: 'bar',
      data: {
        labels: ['Carrusel Aconc.\nAdv+ $377','UGC marti\nAdv+ $432','Clásico\nAdv+ $477','Rafting 6\n$517','Mejores\nAdv+ $580','Rafting 5\n$602','Rafting 7\n$1.103','Clásico\nIntereses $1.321'],
        datasets: [{
          data: [377,432,477,517,580,602,1103,1321],
          backgroundColor: ['#1d9e75','#1d9e75','#73726c','#73726c','#ef9f27','#ef9f27','#e24b4a','#e24b4a'],
          borderRadius: 5, borderSkipped: false
        }]
      },
      options: {
        responsive: true, maintainAspectRatio: false, indexAxis: 'y',
        plugins: { legend: { display: false }, tooltip: { callbacks: { label: ctx => ' $'+ctx.raw+' ARS por conversación' } } },
        scales: {
          x: { ticks: { font: { size: 11 }, color: '#73726c', callback: v => '$'+v }, grid: { color: 'rgba(0,0,0,0.05)' } },
          y: { ticks: { font: { size: 11 }, color: '#73726c' }, grid: { display: false } }
        }
      }
    });

    new Chart(document.getElementById('bubbleChart'), {
      type: 'bubble',
      data: {
        datasets: [
          { label: 'UGC marti Adv+',        data: [{ x: 432,  y: 179, r: 22 }], backgroundColor: '#1d9e7588', borderColor: '#1d9e75', borderWidth: 2 },
          { label: 'Rafting 5',              data: [{ x: 602,  y: 155, r: 18 }], backgroundColor: '#ef9f2788', borderColor: '#ef9f27', borderWidth: 2 },
          { label: 'Rafting 6',              data: [{ x: 517,  y: 21,  r: 9  }], backgroundColor: '#ef9f2755', borderColor: '#ef9f27', borderWidth: 2 },
          { label: 'Carrusel Aconc. Adv+',  data: [{ x: 377,  y: 5,   r: 7  }], backgroundColor: '#1d9e7555', borderColor: '#1d9e75', borderWidth: 2 },
          { label: 'Rafting 7',              data: [{ x: 1103, y: 9,   r: 8  }], backgroundColor: '#e24b4a88', borderColor: '#e24b4a', borderWidth: 2 },
          { label: 'Clásico Intereses',      data: [{ x: 1321, y: 5,   r: 7  }], backgroundColor: '#e24b4a55', borderColor: '#e24b4a', borderWidth: 2 },
        ]
      },
      options: {
        responsive: true, maintainAspectRatio: false,
        plugins: {
          legend: { position: 'bottom', labels: { font: { size: 11 }, color: '#73726c', boxWidth: 10, padding: 10 } },
          tooltip: { callbacks: { label: ctx => ctx.dataset.label + ' · CPConv $'+ctx.parsed.x+' · '+ctx.parsed.y+' conv' } }
        },
        scales: {
          x: {
            title: { display: true, text: 'CPConv ARS (menor = mejor)', font: { size: 11 }, color: '#73726c' },
            ticks: { font: { size: 11 }, color: '#73726c', callback: v => '$'+v }, grid: { color: 'rgba(0,0,0,0.05)' },
            min: 300, max: 1450
          },
          y: {
            title: { display: true, text: 'Conversaciones', font: { size: 11 }, color: '#73726c' },
            ticks: { font: { size: 11 }, color: '#73726c' }, grid: { color: 'rgba(0,0,0,0.05)' }
          }
        }
      }
    });
  }

  if (tab === 'comparativa') {
    new Chart(document.getElementById('cmpChart'), {
      type: 'bar',
      data: {
        labels: ['UGC marti\nAdv+','Rafting 5','Carrusel\nAconc. Adv+','Rafting 7','Clásico\nIntereses'],
        datasets: [
          { label: '90 días', data: [438,607,956,780,1458], backgroundColor: '#3266ad33', borderColor: '#3266ad', borderWidth: 1.5, borderRadius: 4, borderSkipped: false },
          { label: '30 días', data: [432,602,377,1103,1321],
            backgroundColor: ['#1d9e7566','#ef9f2766','#1d9e7566','#e24b4a66','#e24b4a66'],
            borderColor: ['#1d9e75','#ef9f27','#1d9e75','#e24b4a','#e24b4a'],
            borderWidth: 1.5, borderRadius: 4, borderSkipped: false }
        ]
      },
      options: {
        responsive: true, maintainAspectRatio: false,
        plugins: {
          legend: { position: 'bottom', labels: { font: { size: 11 }, color: '#73726c', boxWidth: 10 } },
          tooltip: { callbacks: { label: ctx => ' $'+ctx.raw+' CPConv' } }
        },
        scales: {
          x: { ticks: { font: { size: 11 }, color: '#73726c' }, grid: { display: false } },
          y: { ticks: { font: { size: 11 }, color: '#73726c', callback: v => '$'+v }, grid: { color: 'rgba(0,0,0,0.05)' } }
        }
      }
    });
  }
}

// Render resumen charts on load
renderCharts('resumen');
</script>
</body>
</html>
