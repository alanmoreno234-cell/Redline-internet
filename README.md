
<!DOCTYPE html>
<html lang="es">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>Redline Internet — Conectividad de Alta Performance</title>
<link href="https://fonts.googleapis.com/css2?family=Bebas+Neue&family=Outfit:wght@300;400;500;600;700&display=swap" rel="stylesheet">
<style>
  *, *::before, *::after { box-sizing: border-box; margin: 0; padding: 0; }

  :root {
    --navy: #0a1628;
    --navy-mid: #0f2044;
    --teal: #00c4cc;
    --teal-light: #4de8ef;
    --blue: #1565c0;
    --blue-mid: #1e88e5;
    --white: #f0f4f8;
    --gray: #8ba3c1;
    --line: rgba(0,196,204,0.15);
  }

  html { scroll-behavior: smooth; }

  body {
    background: var(--navy);
    color: var(--white);
    font-family: 'Outfit', sans-serif;
    font-weight: 400;
    overflow-x: hidden;
  }

  /* ─── GRID BACKGROUND ─── */
  body::before {
    content: '';
    position: fixed;
    inset: 0;
    background-image:
      linear-gradient(var(--line) 1px, transparent 1px),
      linear-gradient(90deg, var(--line) 1px, transparent 1px);
    background-size: 60px 60px;
    pointer-events: none;
    z-index: 0;
  }

  /* ─── NAV ─── */
  nav {
    position: fixed;
    top: 0; left: 0; right: 0;
    z-index: 100;
    display: flex;
    align-items: center;
    justify-content: space-between;
    padding: 20px 60px;
    background: rgba(10,22,40,0.85);
    backdrop-filter: blur(16px);
    border-bottom: 1px solid var(--line);
  }

  .nav-logo {
    display: flex;
    align-items: center;
    gap: 14px;
  }

  .logo-hex {
    width: 44px;
    height: 44px;
  }

  .logo-text {
    display: flex;
    flex-direction: column;
    line-height: 1;
  }

  .logo-text strong {
    font-family: 'Bebas Neue', sans-serif;
    font-size: 26px;
    letter-spacing: 3px;
    background: linear-gradient(90deg, #fff 40%, var(--teal));
    -webkit-background-clip: text;
    -webkit-text-fill-color: transparent;
  }

  .logo-text span {
    font-size: 10px;
    letter-spacing: 4px;
    color: var(--gray);
    text-transform: uppercase;
    margin-top: 2px;
  }

  .nav-links {
    display: flex;
    gap: 40px;
    list-style: none;
  }

  .nav-links a {
    text-decoration: none;
    color: var(--gray);
    font-size: 13px;
    letter-spacing: 1.5px;
    text-transform: uppercase;
    font-weight: 500;
    transition: color .3s;
  }

  .nav-links a:hover { color: var(--teal); }

  .nav-cta {
    background: linear-gradient(135deg, var(--teal), var(--blue-mid));
    color: var(--navy) !important;
    padding: 10px 24px;
    border-radius: 4px;
    font-weight: 600 !important;
    color: #fff !important;
  }

  /* ─── HERO ─── */
  .hero {
    position: relative;
    min-height: 100vh;
    display: flex;
    align-items: center;
    padding: 120px 60px 80px;
    overflow: hidden;
    z-index: 1;
  }

  .hero-glow {
    position: absolute;
    width: 700px;
    height: 700px;
    border-radius: 50%;
    background: radial-gradient(circle, rgba(0,196,204,0.12) 0%, transparent 70%);
    top: -100px;
    right: -100px;
    pointer-events: none;
  }

  .hero-glow2 {
    position: absolute;
    width: 500px;
    height: 500px;
    border-radius: 50%;
    background: radial-gradient(circle, rgba(21,101,192,0.15) 0%, transparent 70%);
    bottom: 0;
    left: 20%;
    pointer-events: none;
  }

  .hero-content {
    max-width: 700px;
    position: relative;
    z-index: 2;
    animation: fadeUp .9s ease both;
  }

  .hero-badge {
    display: inline-flex;
    align-items: center;
    gap: 8px;
    background: rgba(0,196,204,0.08);
    border: 1px solid rgba(0,196,204,0.3);
    border-radius: 100px;
    padding: 6px 16px;
    font-size: 12px;
    letter-spacing: 2px;
    text-transform: uppercase;
    color: var(--teal);
    margin-bottom: 32px;
    font-weight: 500;
  }

  .hero-badge::before {
    content: '';
    width: 6px;
    height: 6px;
    border-radius: 50%;
    background: var(--teal);
    animation: pulse 2s infinite;
  }

  .hero h1 {
    font-family: 'Bebas Neue', sans-serif;
    font-size: clamp(60px, 8vw, 110px);
    line-height: 0.95;
    letter-spacing: 2px;
    margin-bottom: 28px;
  }

  .hero h1 .line-teal {
    display: block;
    background: linear-gradient(90deg, var(--teal), var(--teal-light));
    -webkit-background-clip: text;
    -webkit-text-fill-color: transparent;
  }

  .hero p {
    font-size: 18px;
    line-height: 1.7;
    color: var(--gray);
    max-width: 520px;
    margin-bottom: 48px;
    font-weight: 300;
  }

  .hero-actions {
    display: flex;
    gap: 16px;
    flex-wrap: wrap;
  }

  .btn-primary {
    display: inline-flex;
    align-items: center;
    gap: 10px;
    background: linear-gradient(135deg, var(--teal), var(--blue-mid));
    color: #fff;
    text-decoration: none;
    padding: 16px 36px;
    border-radius: 4px;
    font-weight: 600;
    font-size: 15px;
    letter-spacing: 0.5px;
    transition: transform .2s, box-shadow .2s;
    box-shadow: 0 0 30px rgba(0,196,204,0.3);
  }

  .btn-primary:hover {
    transform: translateY(-2px);
    box-shadow: 0 0 50px rgba(0,196,204,0.5);
  }

  .btn-outline {
    display: inline-flex;
    align-items: center;
    gap: 10px;
    border: 1px solid rgba(255,255,255,0.2);
    color: var(--white);
    text-decoration: none;
    padding: 16px 36px;
    border-radius: 4px;
    font-weight: 500;
    font-size: 15px;
    transition: border-color .2s, background .2s;
  }

  .btn-outline:hover {
    border-color: var(--teal);
    background: rgba(0,196,204,0.06);
  }

  /* ─── STATS BAR ─── */
  .stats-bar {
    position: relative;
    z-index: 1;
    display: grid;
    grid-template-columns: repeat(4, 1fr);
    border-top: 1px solid var(--line);
    border-bottom: 1px solid var(--line);
    background: rgba(15,32,68,0.6);
    backdrop-filter: blur(10px);
  }

  .stat-item {
    padding: 40px 50px;
    border-right: 1px solid var(--line);
    animation: fadeUp .6s ease both;
  }

  .stat-item:last-child { border-right: none; }

  .stat-num {
    font-family: 'Bebas Neue', sans-serif;
    font-size: 52px;
    line-height: 1;
    background: linear-gradient(135deg, var(--white), var(--teal));
    -webkit-background-clip: text;
    -webkit-text-fill-color: transparent;
    margin-bottom: 6px;
  }

  .stat-label {
    font-size: 12px;
    letter-spacing: 2px;
    text-transform: uppercase;
    color: var(--gray);
    font-weight: 500;
  }

  /* ─── SECTION GENERIC ─── */
  section {
    position: relative;
    z-index: 1;
    padding: 100px 60px;
  }

  .section-tag {
    font-size: 11px;
    letter-spacing: 3px;
    text-transform: uppercase;
    color: var(--teal);
    font-weight: 600;
    margin-bottom: 16px;
    display: block;
  }

  .section-title {
    font-family: 'Bebas Neue', sans-serif;
    font-size: clamp(40px, 5vw, 64px);
    letter-spacing: 1.5px;
    line-height: 1.05;
    margin-bottom: 20px;
  }

  .section-sub {
    font-size: 17px;
    color: var(--gray);
    font-weight: 300;
    line-height: 1.7;
    max-width: 520px;
  }

  /* ─── SERVICES ─── */
  .services-grid {
    display: grid;
    grid-template-columns: repeat(3, 1fr);
    gap: 2px;
    margin-top: 64px;
    border: 1px solid var(--line);
  }

  .service-card {
    background: rgba(15,32,68,0.5);
    padding: 48px 40px;
    border-right: 1px solid var(--line);
    border-bottom: 1px solid var(--line);
    position: relative;
    overflow: hidden;
    transition: background .3s;
  }

  .service-card::before {
    content: '';
    position: absolute;
    top: 0; left: 0; right: 0;
    height: 2px;
    background: linear-gradient(90deg, transparent, var(--teal), transparent);
    opacity: 0;
    transition: opacity .3s;
  }

  .service-card:hover::before { opacity: 1; }
  .service-card:hover { background: rgba(0,196,204,0.04); }

  .service-icon {
    width: 52px;
    height: 52px;
    background: rgba(0,196,204,0.08);
    border: 1px solid rgba(0,196,204,0.2);
    border-radius: 10px;
    display: flex;
    align-items: center;
    justify-content: center;
    margin-bottom: 24px;
    font-size: 22px;
  }

  .service-card h3 {
    font-size: 20px;
    font-weight: 600;
    margin-bottom: 12px;
    letter-spacing: 0.5px;
  }

  .service-card p {
    font-size: 14px;
    color: var(--gray);
    line-height: 1.7;
    font-weight: 300;
  }

  /* ─── PLANS ─── */
  .plans-section {
    background: rgba(15,32,68,0.3);
  }

  .plans-grid {
    display: grid;
    grid-template-columns: repeat(3, 1fr);
    gap: 20px;
    margin-top: 64px;
  }

  .plan-card {
    border: 1px solid var(--line);
    border-radius: 8px;
    padding: 44px 36px;
    background: rgba(10,22,40,0.6);
    position: relative;
    transition: transform .3s, box-shadow .3s;
  }

  .plan-card:hover {
    transform: translateY(-6px);
    box-shadow: 0 20px 60px rgba(0,0,0,0.4);
  }

  .plan-card.featured {
    border-color: rgba(0,196,204,0.5);
    background: rgba(0,196,204,0.04);
    box-shadow: 0 0 40px rgba(0,196,204,0.1);
  }

  .plan-badge {
    position: absolute;
    top: -14px;
    left: 50%;
    transform: translateX(-50%);
    background: linear-gradient(135deg, var(--teal), var(--blue-mid));
    color: #fff;
    font-size: 11px;
    letter-spacing: 2px;
    text-transform: uppercase;
    padding: 5px 18px;
    border-radius: 100px;
    font-weight: 600;
    white-space: nowrap;
  }

  .plan-name {
    font-size: 13px;
    letter-spacing: 3px;
    text-transform: uppercase;
    color: var(--gray);
    margin-bottom: 12px;
    font-weight: 500;
  }

  .plan-speed {
    font-family: 'Bebas Neue', sans-serif;
    font-size: 72px;
    line-height: 1;
    color: var(--white);
    margin-bottom: 4px;
  }

  .plan-unit {
    font-size: 14px;
    color: var(--teal);
    letter-spacing: 2px;
    text-transform: uppercase;
    margin-bottom: 28px;
    font-weight: 500;
  }

  .plan-price {
    font-size: 28px;
    font-weight: 700;
    margin-bottom: 28px;
    color: var(--white);
  }

  .plan-price span {
    font-size: 14px;
    color: var(--gray);
    font-weight: 300;
  }

  .plan-features {
    list-style: none;
    margin-bottom: 36px;
  }

  .plan-features li {
    font-size: 14px;
    color: var(--gray);
    padding: 9px 0;
    border-bottom: 1px solid var(--line);
    display: flex;
    align-items: center;
    gap: 10px;
    font-weight: 300;
  }

  .plan-features li::before {
    content: '✓';
    color: var(--teal);
    font-weight: 700;
    font-size: 12px;
    flex-shrink: 0;
  }

  .plan-btn {
    display: block;
    text-align: center;
    padding: 14px;
    border-radius: 4px;
    text-decoration: none;
    font-size: 14px;
    font-weight: 600;
    letter-spacing: 1px;
    text-transform: uppercase;
    transition: all .2s;
  }

  .plan-btn-outline {
    border: 1px solid rgba(255,255,255,0.2);
    color: var(--white);
  }

  .plan-btn-outline:hover { border-color: var(--teal); color: var(--teal); }

  .plan-btn-solid {
    background: linear-gradient(135deg, var(--teal), var(--blue-mid));
    color: #fff;
    box-shadow: 0 0 30px rgba(0,196,204,0.25);
  }

  .plan-btn-solid:hover { box-shadow: 0 0 50px rgba(0,196,204,0.45); }

  /* ─── WHY US ─── */
  .why-grid {
    display: grid;
    grid-template-columns: 1fr 1fr;
    gap: 80px;
    align-items: center;
    margin-top: 80px;
  }

  .why-items { display: flex; flex-direction: column; gap: 32px; }

  .why-item {
    display: flex;
    gap: 20px;
    align-items: flex-start;
  }

  .why-icon {
    width: 46px;
    height: 46px;
    border-radius: 8px;
    background: rgba(0,196,204,0.1);
    border: 1px solid rgba(0,196,204,0.2);
    display: flex;
    align-items: center;
    justify-content: center;
    font-size: 18px;
    flex-shrink: 0;
    margin-top: 2px;
  }

  .why-text h4 {
    font-size: 17px;
    font-weight: 600;
    margin-bottom: 6px;
  }

  .why-text p {
    font-size: 14px;
    color: var(--gray);
    line-height: 1.6;
    font-weight: 300;
  }

  .why-visual {
    position: relative;
    height: 480px;
    border: 1px solid var(--line);
    border-radius: 12px;
    background: rgba(15,32,68,0.5);
    display: flex;
    align-items: center;
    justify-content: center;
    overflow: hidden;
  }

  .why-visual::before {
    content: '';
    position: absolute;
    inset: 0;
    background: radial-gradient(circle at 50% 50%, rgba(0,196,204,0.08), transparent 70%);
  }

  .speed-ring {
    position: relative;
    width: 220px;
    height: 220px;
  }

  .speed-ring svg {
    width: 100%;
    height: 100%;
    transform: rotate(-90deg);
  }

  .speed-ring-center {
    position: absolute;
    inset: 0;
    display: flex;
    flex-direction: column;
    align-items: center;
    justify-content: center;
  }

  .speed-ring-center strong {
    font-family: 'Bebas Neue', sans-serif;
    font-size: 52px;
    line-height: 1;
    background: linear-gradient(135deg, var(--teal), var(--white));
    -webkit-background-clip: text;
    -webkit-text-fill-color: transparent;
  }

  .speed-ring-center span {
    font-size: 11px;
    letter-spacing: 3px;
    color: var(--gray);
    text-transform: uppercase;
  }

  .ping-dot {
    position: absolute;
    bottom: 60px;
    left: 50%;
    transform: translateX(-50%);
    text-align: center;
  }

  .ping-val {
    font-family: 'Bebas Neue', sans-serif;
    font-size: 28px;
    color: var(--teal);
  }

  .ping-label {
    font-size: 10px;
    letter-spacing: 2px;
    color: var(--gray);
    text-transform: uppercase;
  }

  /* ─── CONTACT ─── */
  .contact-section {
    background: rgba(15,32,68,0.4);
    border-top: 1px solid var(--line);
  }

  .contact-grid {
    display: grid;
    grid-template-columns: 1fr 1fr;
    gap: 80px;
    margin-top: 64px;
  }

  .contact-items {
    display: flex;
    flex-direction: column;
    gap: 28px;
  }

  .contact-item {
    display: flex;
    gap: 18px;
    align-items: center;
  }

  .contact-icon {
    width: 48px;
    height: 48px;
    border-radius: 8px;
    background: rgba(0,196,204,0.08);
    border: 1px solid rgba(0,196,204,0.2);
    display: flex;
    align-items: center;
    justify-content: center;
    font-size: 20px;
    flex-shrink: 0;
  }

  .contact-info p:first-child {
    font-size: 12px;
    letter-spacing: 2px;
    text-transform: uppercase;
    color: var(--gray);
    margin-bottom: 4px;
    font-weight: 500;
  }

  .contact-info p:last-child {
    font-size: 17px;
    font-weight: 500;
    color: var(--white);
  }

  .contact-form {
    display: flex;
    flex-direction: column;
    gap: 16px;
  }

  .form-row { display: grid; grid-template-columns: 1fr 1fr; gap: 16px; }

  .form-group { display: flex; flex-direction: column; gap: 8px; }

  .form-group label {
    font-size: 12px;
    letter-spacing: 1.5px;
    text-transform: uppercase;
    color: var(--gray);
    font-weight: 500;
  }

  .form-group input,
  .form-group select,
  .form-group textarea {
    background: rgba(255,255,255,0.04);
    border: 1px solid var(--line);
    border-radius: 4px;
    padding: 14px 18px;
    color: var(--white);
    font-family: 'Outfit', sans-serif;
    font-size: 15px;
    outline: none;
    transition: border-color .2s;
  }

  .form-group input::placeholder,
  .form-group textarea::placeholder { color: rgba(139,163,193,0.4); }

  .form-group input:focus,
  .form-group select:focus,
  .form-group textarea:focus { border-color: rgba(0,196,204,0.5); }

  .form-group select option { background: var(--navy-mid); }

  .form-group textarea { resize: vertical; min-height: 110px; }

  /* ─── FOOTER ─── */
  footer {
    position: relative;
    z-index: 1;
    padding: 40px 60px;
    border-top: 1px solid var(--line);
    display: flex;
    align-items: center;
    justify-content: space-between;
    background: rgba(10,22,40,0.8);
  }

  .footer-left {
    display: flex;
    align-items: center;
    gap: 14px;
  }

  .footer-copy {
    font-size: 13px;
    color: var(--gray);
    font-weight: 300;
  }

  .footer-links {
    display: flex;
    gap: 28px;
    list-style: none;
  }

  .footer-links a {
    font-size: 12px;
    color: var(--gray);
    text-decoration: none;
    letter-spacing: 1px;
    text-transform: uppercase;
    transition: color .2s;
  }

  .footer-links a:hover { color: var(--teal); }

  /* ─── ANIMATIONS ─── */
  @keyframes fadeUp {
    from { opacity: 0; transform: translateY(30px); }
    to   { opacity: 1; transform: translateY(0); }
  }

  @keyframes pulse {
    0%,100% { opacity: 1; transform: scale(1); }
    50%      { opacity: 0.4; transform: scale(1.5); }
  }

  @keyframes spin {
    to { stroke-dashoffset: 0; }
  }

  .animate {
    opacity: 0;
    transform: translateY(24px);
    transition: opacity .7s ease, transform .7s ease;
  }

  .animate.visible {
    opacity: 1;
    transform: none;
  }
</style>
</head>
<body>

<!-- NAV -->
<nav>
  <div class="nav-logo">
    <svg class="logo-hex" viewBox="0 0 60 60" fill="none">
      <polygon points="30,4 54,17 54,43 30,56 6,43 6,17" fill="none" stroke="url(#hg)" stroke-width="2"/>
      <polygon points="30,14 46,23 46,41 30,50 14,41 14,23" fill="none" stroke="url(#hg)" stroke-width="1.5" opacity=".5"/>
      <circle cx="30" cy="30" r="6" fill="url(#hg)" opacity=".9"/>
      <defs>
        <linearGradient id="hg" x1="0" y1="0" x2="60" y2="60" gradientUnits="userSpaceOnUse">
          <stop stop-color="#00c4cc"/>
          <stop offset="1" stop-color="#1e88e5"/>
        </linearGradient>
      </defs>
    </svg>
    <div class="logo-text">
      <strong>REDLINE</strong>
      <span>Internet</span>
    </div>
  </div>
  <ul class="nav-links">
    <li><a href="#servicios">Servicios</a></li>
    <li><a href="#planes">Planes</a></li>
    <li><a href="#nosotros">Nosotros</a></li>
    <li><a href="#contacto" class="nav-cta">Contratar</a></li>
  </ul>
</nav>

<!-- HERO -->
<section class="hero">
  <div class="hero-glow"></div>
  <div class="hero-glow2"></div>
  <div class="hero-content">
    <div class="hero-badge">Red activa · Servicio 24/7</div>
    <h1>
      CONECTIVIDAD<br>
      <span class="line-teal">DE ALTO</span><br>
      RENDIMIENTO
    </h1>
    <p>Soluciones de internet empresarial y residencial con tecnología de punta. Velocidades simétricas, latencia mínima y soporte técnico permanente.</p>
    <div class="hero-actions">
      <a href="#planes" class="btn-primary">
        Ver Planes
        <svg width="16" height="16" fill="none" viewBox="0 0 24 24" stroke="currentColor" stroke-width="2"><path d="M5 12h14M12 5l7 7-7 7"/></svg>
      </a>
      <a href="#contacto" class="btn-outline">Consultar</a>
    </div>
  </div>
</section>

<!-- STATS -->
<div class="stats-bar">
  <div class="stat-item">
    <div class="stat-num">1G</div>
    <div class="stat-label">Velocidad Máxima</div>
  </div>
  <div class="stat-item" style="animation-delay:.1s">
    <div class="stat-num">99.9%</div>
    <div class="stat-label">Uptime Garantizado</div>
  </div>
  <div class="stat-item" style="animation-delay:.2s">
    <div class="stat-num">+5K</div>
    <div class="stat-label">Clientes Activos</div>
  </div>
  <div class="stat-item" style="animation-delay:.3s">
    <div class="stat-num">24/7</div>
    <div class="stat-label">Soporte Técnico</div>
  </div>
</div>

<!-- SERVICIOS -->
<section id="servicios">
  <span class="section-tag animate">Lo que ofrecemos</span>
  <h2 class="section-title animate">SERVICIOS<br>CORPORATIVOS</h2>
  <p class="section-sub animate">Infraestructura diseñada para empresas que no pueden permitirse interrupciones.</p>

  <div class="services-grid animate">
    <div class="service-card">
      <div class="service-icon">🌐</div>
      <h3>Fibra Óptica</h3>
      <p>Conexión simétrica de hasta 1 Gbps con red propia y sin contención. Ideal para oficinas y pymes.</p>
    </div>
    <div class="service-card">
      <div class="service-icon">📡</div>
      <h3>Enlace Dedicado</h3>
      <p>Ancho de banda garantizado exclusivo para tu empresa, con SLA documentado y IP fija