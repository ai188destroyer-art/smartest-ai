<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8" />
  <meta name="viewport" content="width=device-width,initial-scale=1" />
  <title>Nexus — Transcendent AI Control Interface</title>
  <meta
    name="description"
    content="Nexus is a conceptual advanced AI interface with directive execution, 8-chat memory, persistent background tasks, game integration, real-time verification, causal reasoning, agentic tools, emotional intelligence, safety controls, and modular intelligence domains."
  />
  <meta name="author" content="Nexus Project" />
  <meta property="og:title" content="Nexus — Transcendent AI Control Interface" />
  <meta
    property="og:description"
    content="Directive fidelity, 8-chat memory, persistent tasks, game integration, fact-checking, causal reasoning, advanced agentic execution, and safety-governed intelligence modules."
  />
  <meta property="og:type" content="website" />
  <link
    rel="icon"
    href="data:image/svg+xml,%3Csvg xmlns='http://www.w3.org/2000/svg' viewBox='0 0 100 100'%3E%3Cdefs%3E%3ClinearGradient id='g' x1='0' y1='0' x2='1' y2='1'%3E%3Cstop stop-color='%236d28d9'/%3E%3Cstop offset='1' stop-color='%231d4ed8'/%3E%3C/linearGradient%3E%3C/defs%3E%3Crect width='100' height='100' rx='18' fill='url(%23g)'/%3E%3Ctext x='50' y='61' font-size='58' fill='white' text-anchor='middle' font-family='Georgia' font-weight='700'%3EN%3C/text%3E%3C/svg%3E"
  />
  <link rel="preconnect" href="https://fonts.googleapis.com" />
  <link
    href="https://fonts.googleapis.com/css2?family=Lora:ital,wght@0,400;0,500;1,400&family=JetBrains+Mono:wght@300;400;500;700&display=swap"
    rel="stylesheet"
  />

  <style>
    :root {
      --bg: #0a0c10;
      --sf: #171923;
      --s2: #1e2332;
      --s3: #252d40;
      --s4: #2d3650;
      --b: #2a3347;
      --b2: #3a4560;
      --ink: #e8eaf0;
      --t2: #9aa0b4;
      --t3: #5a6278;

      --green: #16a34a;
      --green-bg: #0a2010;
      --green-b: #1a5028;

      --blue: #1d4ed8;
      --blue-bg: #0a1230;
      --blue-b: #1a3060;

      --violet: #6d28d9;
      --violet-bg: #1a0a30;
      --violet-b: #4a2060;

      --cyan: #0e7490;
      --cyan-bg: #0a1a20;
      --cyan-b: #1a4050;

      --amber: #b45309;
      --amber-bg: #221500;
      --amber-b: #6a4000;

      --red: #b91c1c;
      --red-bg: #200a0a;
      --red-b: #6a1010;

      --orange: #c2410c;
      --orange-bg: #1a0a00;
      --orange-b: #7c2d12;

      --mono: "JetBrains Mono", monospace;
      --serif: "Lora", Georgia, serif;
      --r8: 8px;
      --r12: 12px;
      --r16: 16px;
      --shadow: 0 12px 30px rgba(0, 0, 0, 0.25);
    }

    body.light {
      --bg: #f8fafc;
      --sf: #ffffff;
      --s2: #f1f5f9;
      --s3: #e2e8f0;
      --s4: #cbd5e1;
      --b: #cbd5e1;
      --b2: #94a3b8;
      --ink: #0f172a;
      --t2: #334155;
      --t3: #64748b;
      background: radial-gradient(circle at 20% 0%, rgba(109, 40, 217, 0.08), transparent 32%),
                  radial-gradient(circle at 90% 12%, rgba(29, 78, 216, 0.06), transparent 28%),
                  var(--bg);
    }

    body.light .topbar { background: rgba(255, 255, 255, 0.96); }
    body.light .sidebar { background: rgba(248, 250, 252, 0.94); }
    body.light .hero { background: linear-gradient(135deg, rgba(255,255,255,0.92), rgba(241,245,249,0.72)); }
    body.light .hero::before { background: radial-gradient(circle, rgba(109, 40, 217, 0.09), transparent 70%); }
    body.light .card { background: rgba(255, 255, 255, 0.84); }
    body.light details.module { background: rgba(255, 255, 255, 0.82); }
    body.light .input-area { background: rgba(255, 255, 255, 0.96); }
    body.light .send { color: #fff; background: linear-gradient(135deg, var(--blue), var(--violet)); }

    * {
      box-sizing: border-box;
    }

    html {
      font-size: 13.5px;
      -webkit-font-smoothing: antialiased;
      scroll-behavior: smooth;
    }

    body {
      margin: 0;
      height: 100vh;
      overflow: hidden;
      background: radial-gradient(circle at 20% 0%, rgba(109, 40, 217, 0.15), transparent 32%),
        radial-gradient(circle at 90% 12%, rgba(29, 78, 216, 0.12), transparent 28%),
        var(--bg);
      color: var(--ink);
      font-family: var(--mono);
      line-height: 1.6;
    }

    button,
    textarea,
    input {
      font-family: inherit;
    }

    button {
      cursor: pointer;
    }

    *:focus-visible {
      outline: 2px solid var(--green);
      outline-offset: 2px;
    }

    .sr-only {
      position: absolute;
      left: -9999px;
      width: 1px;
      height: 1px;
      overflow: hidden;
    }

    .shell {
      height: 100vh;
      display: grid;
      grid-template-columns: 310px 1fr;
      grid-template-rows: 62px 1fr 150px;
      overflow: hidden;
    }

    .topbar {
      grid-column: 1 / -1;
      display: flex;
      align-items: center;
      gap: 12px;
      padding: 0 18px;
      border-bottom: 1px solid var(--b);
      background: rgba(23, 25, 35, 0.96);
      backdrop-filter: blur(14px);
      box-shadow: 0 2px 12px rgba(0, 0, 0, 0.18);
      z-index: 10;
    }

    .logo {
      display: flex;
      align-items: center;
      gap: 10px;
      min-width: 245px;
      color: inherit;
      text-decoration: none;
    }

    .logo-mark {
      width: 34px;
      height: 34px;
      display: grid;
      place-items: center;
      border-radius: 10px;
      background: linear-gradient(135deg, var(--violet), var(--blue));
      color: #fff;
      font-family: var(--serif);
      font-weight: 700;
      font-size: 22px;
      box-shadow: 0 0 18px rgba(109, 40, 217, 0.35);
    }

    .logo-name {
      font-family: var(--serif);
      font-size: 19px;
      font-style: italic;
      letter-spacing: -0.03em;
    }

    .logo-sub {
      font-size: 10px;
      color: var(--t3);
      text-transform: uppercase;
      letter-spacing: 0.09em;
    }

    .top-scroll {
      display: flex;
      align-items: center;
      gap: 8px;
      overflow-x: auto;
      scrollbar-width: none;
      flex: 1;
    }

    .top-scroll::-webkit-scrollbar {
      width: 0;
      height: 0;
    }

    .pill {
      display: inline-flex;
      align-items: center;
      gap: 7px;
      white-space: nowrap;
      border-radius: 999px;
      border: 1px solid var(--b);
      background: var(--s2);
      color: var(--t2);
      padding: 5px 10px;
      font-size: 10px;
      text-transform: uppercase;
      letter-spacing: 0.08em;
    }

    .pill.green {
      color: var(--green);
      background: var(--green-bg);
      border-color: var(--green-b);
    }

    .pill.blue {
      color: var(--blue);
      background: var(--blue-bg);
      border-color: var(--blue-b);
    }

    .pill.violet {
      color: var(--violet);
      background: var(--violet-bg);
      border-color: var(--violet-b);
    }

    .pill.cyan {
      color: var(--cyan);
      background: var(--cyan-bg);
      border-color: var(--cyan-b);
    }

    .pill.amber {
      color: var(--amber);
      background: var(--amber-bg);
      border-color: var(--amber-b);
    }

    .pill.red {
      color: var(--red);
      background: var(--red-bg);
      border-color: var(--red-b);
    }

    .pill.orange {
      color: var(--orange);
      background: var(--orange-bg);
      border-color: var(--orange-b);
    }

    .dot {
      width: 7px;
      height: 7px;
      border-radius: 50%;
      background: currentColor;
      animation: pulse 1.8s infinite ease-in-out;
    }

    @keyframes pulse {
      0%,
      100% {
        opacity: 0.35;
        transform: scale(0.9);
      }
      50% {
        opacity: 1;
        transform: scale(1.15);
      }
    }

    .icon-btn,
    .hbtn {
      display: inline-flex;
      align-items: center;
      justify-content: center;
      gap: 7px;
      border: 1px solid var(--b);
      color: var(--t2);
      background: var(--s2);
      border-radius: var(--r8);
      padding: 8px 11px;
      transition: 0.14s ease;
      white-space: nowrap;
    }

    .icon-btn {
      width: 36px;
      height: 36px;
      padding: 0;
    }

    .icon-btn:hover,
    .hbtn:hover {
      background: var(--s3);
      color: var(--ink);
      border-color: var(--b2);
    }

    .sidebar {
      grid-row: 2 / 4;
      overflow-y: auto;
      border-right: 1px solid var(--b);
      background: rgba(23, 25, 35, 0.94);
      padding: 14px 12px;
      scrollbar-width: thin;
      scrollbar-color: var(--b2) transparent;
    }

    .xp {
      border: 1px solid var(--b);
      background: linear-gradient(135deg, rgba(29, 78, 216, 0.13), rgba(109, 40, 217, 0.12));
      border-radius: var(--r16);
      padding: 14px;
      margin-bottom: 14px;
      box-shadow: var(--shadow);
    }

    .xp-row {
      display: flex;
      align-items: center;
      justify-content: space-between;
      gap: 8px;
    }

    .xp-title {
      font-weight: 700;
      color: var(--ink);
    }

    .xp-sub {
      font-size: 10px;
      color: var(--t3);
      text-transform: uppercase;
      letter-spacing: 0.08em;
    }

    .track {
      height: 5px;
      border-radius: 999px;
      overflow: hidden;
      background: var(--s4);
      margin: 10px 0;
    }

    .fill {
      height: 100%;
      width: 100%;
      background: linear-gradient(90deg, var(--green), var(--blue), var(--violet));
      border-radius: inherit;
    }

    .nav-title {
      margin: 14px 8px 6px;
      font-size: 10px;
      color: var(--t3);
      text-transform: uppercase;
      letter-spacing: 0.12em;
    }

    .nav-item {
      width: 100%;
      display: flex;
      align-items: center;
      gap: 9px;
      text-align: left;
      background: transparent;
      color: var(--t2);
      border: 1px solid transparent;
      border-radius: var(--r8);
      padding: 8px 10px;
      font-size: 12px;
      transition: 0.12s ease;
    }

    .nav-item:hover {
      background: var(--s2);
      color: var(--ink);
    }

    .nav-item.active {
      background: var(--s2);
      border-color: var(--b2);
      color: var(--ink);
      font-weight: 700;
    }

    .nav-icon {
      width: 18px;
      text-align: center;
      opacity: 0.9;
    }

    .main {
      overflow-y: auto;
      padding: 26px 30px;
      scrollbar-width: thin;
      scrollbar-color: var(--b2) transparent;
    }

    .main::-webkit-scrollbar,
    .sidebar::-webkit-scrollbar {
      width: 6px;
    }

    .main::-webkit-scrollbar-thumb,
    .sidebar::-webkit-scrollbar-thumb {
      background: var(--b2);
      border-radius: 99px;
    }

    .hero {
      border: 1px solid var(--b2);
      border-radius: 22px;
      padding: 26px;
      background: linear-gradient(135deg, rgba(23, 25, 35, 0.92), rgba(30, 35, 50, 0.72));
      box-shadow: var(--shadow);
      margin-bottom: 20px;
      position: relative;
      overflow: hidden;
    }

    .hero::before {
      content: "";
      position: absolute;
      inset: -120px auto auto -80px;
      width: 260px;
      height: 260px;
      border-radius: 50%;
      background: radial-gradient(circle, rgba(109, 40, 217, 0.22), transparent 70%);
      pointer-events: none;
    }

    .hero h1 {
      font-family: var(--serif);
      font-size: clamp(27px, 4vw, 44px);
      line-height: 1.08;
      margin: 0 0 10px;
      letter-spacing: -0.05em;
      font-style: italic;
      position: relative;
    }

    .hero p {
      max-width: 980px;
      margin: 0;
      color: var(--t2);
      font-size: 13px;
      position: relative;
    }

    .hero-actions {
      display: flex;
      gap: 8px;
      flex-wrap: wrap;
      margin-top: 18px;
      position: relative;
    }

    .grid {
      display: grid;
      grid-template-columns: repeat(12, 1fr);
      gap: 14px;
      margin-bottom: 18px;
    }

    .card {
      grid-column: span 4;
      border: 1px solid var(--b);
      border-radius: var(--r16);
      background: rgba(23, 25, 35, 0.84);
      padding: 16px;
      box-shadow: 0 8px 22px rgba(0, 0, 0, 0.16);
    }

    .card.wide {
      grid-column: span 6;
    }

    .card.full {
      grid-column: 1 / -1;
    }

    .card h2,
    .card h3 {
      margin: 0 0 8px;
      font-family: var(--serif);
      letter-spacing: -0.03em;
    }

    .card h2 {
      font-size: 22px;
      font-style: italic;
    }

    .card h3 {
      font-size: 17px;
    }

    .card p {
      color: var(--t2);
      margin: 0 0 10px;
      font-size: 12.5px;
    }

    .list {
      display: grid;
      gap: 8px;
      padding: 0;
      margin: 10px 0 0;
      list-style: none;
    }

    .list li {
      border: 1px solid var(--b);
      background: var(--s2);
      border-radius: var(--r12);
      padding: 10px 11px;
      color: var(--t2);
      font-size: 12px;
    }

    .list strong {
      color: var(--ink);
    }

    .tags {
      display: flex;
      gap: 6px;
      flex-wrap: wrap;
      margin-top: 12px;
    }

    .tag {
      border: 1px solid var(--b);
      border-radius: 999px;
      padding: 4px 9px;
      color: var(--t2);
      background: var(--s2);
      font-size: 10px;
      white-space: nowrap;
    }

    .tag.green {
      color: var(--green);
      background: var(--green-bg);
      border-color: var(--green-b);
    }

    .tag.blue {
      color: var(--blue);
      background: var(--blue-bg);
      border-color: var(--blue-b);
    }

    .tag.violet {
      color: var(--violet);
      background: var(--violet-bg);
      border-color: var(--violet-b);
    }

    .tag.cyan {
      color: var(--cyan);
      background: var(--cyan-bg);
      border-color: var(--cyan-b);
    }

    .tag.amber {
      color: var(--amber);
      background: var(--amber-bg);
      border-color: var(--amber-b);
    }

    .tag.red {
      color: var(--red);
      background: var(--red-bg);
      border-color: var(--red-b);
    }

    .tag.orange {
      color: var(--orange);
      background: var(--orange-bg);
      border-color: var(--orange-b);
    }

    details.module {
      grid-column: 1 / -1;
      border: 1px solid var(--b);
      border-radius: var(--r16);
      background: rgba(23, 25, 35, 0.82);
      overflow: hidden;
      box-shadow: 0 8px 22px rgba(0, 0, 0, 0.16);
    }

    details.module summary {
      list-style: none;
      cursor: pointer;
      padding: 16px 18px;
      display: flex;
      align-items: center;
      justify-content: space-between;
      gap: 12px;
      background: var(--s2);
      border-bottom: 1px solid transparent;
    }

    details.module[open] summary {
      border-bottom-color: var(--b);
    }

    details.module summary::-webkit-details-marker {
      display: none;
    }

    .module-title {
      display: flex;
      align-items: center;
      gap: 11px;
      font-weight: 700;
      color: var(--ink);
    }

    .module-body {
      padding: 18px;
    }

    .feature-grid {
      display: grid;
      grid-template-columns: repeat(3, 1fr);
      gap: 10px;
      margin-top: 14px;
    }

    .feature {
      border: 1px solid var(--b);
      background: var(--s2);
      border-radius: var(--r12);
      padding: 12px;
    }

    .feature strong {
      display: block;
      color: var(--ink);
      margin-bottom: 4px;
    }

    .feature span {
      color: var(--t2);
      font-size: 11.5px;
    }

    .input-area {
      grid-column: 2 / 3;
      border-top: 1px solid var(--b);
      background: rgba(23, 25, 35, 0.96);
      padding: 14px 18px;
      z-index: 8;
    }

    .input-row {
      display: flex;
      gap: 10px;
      align-items: flex-end;
    }

    .directive {
      width: 100%;
      min-height: 54px;
      max-height: 110px;
      resize: vertical;
      border: 1px solid var(--b);
      border-radius: var(--r16);
      background: var(--s2);
      color: var(--ink);
      padding: 12px 14px;
      line-height: 1.6;
      font-size: 12.5px;
    }

    .directive::placeholder {
      color: var(--t3);
    }

    .send {
      border: 0;
      border-radius: var(--r16);
      background: linear-gradient(135deg, var(--ink), #b9c7ff);
      color: #0a0c10;
      padding: 13px 18px;
      font-weight: 800;
      white-space: nowrap;
      min-height: 54px;
      transition: 0.14s ease;
    }

    .send:hover {
      transform: translateY(-1px);
      box-shadow: 0 10px 24px rgba(232, 234, 240, 0.12);
    }

    .chips {
      display: flex;
      flex-wrap: wrap;
      gap: 7px;
      margin-top: 10px;
    }

    .chip {
      border: 1px solid var(--b);
      background: var(--s2);
      color: var(--t2);
      border-radius: 999px;
      padding: 5px 10px;
      font-size: 11px;
      transition: 0.12s ease;
    }

    .chip:hover {
      color: var(--ink);
      background: var(--s3);
      border-color: var(--b2);
    }

    .memory-log,
    .job-log,
    .game-log {
      display: grid;
      gap: 8px;
      margin-top: 10px;
      max-height: 260px;
      overflow: auto;
      padding-right: 4px;
    }

    .log-item {
      border: 1px solid var(--b);
      background: var(--s2);
      border-radius: var(--r12);
      padding: 10px;
      color: var(--t2);
      font-size: 11.5px;
    }

    .log-item strong {
      color: var(--ink);
    }

    .two-col {
      display: grid;
      grid-template-columns: 1fr 1fr;
      gap: 14px;
    }

    .mini-form {
      display: flex;
      gap: 8px;
      margin-top: 10px;
    }

    .mini-form input {
      flex: 1;
      border: 1px solid var(--b);
      background: var(--s2);
      color: var(--ink);
      border-radius: var(--r12);
      padding: 10px 12px;
    }

    .mini-form button {
      border: 1px solid var(--b2);
      background: var(--s3);
      color: var(--ink);
      border-radius: var(--r12);
      padding: 10px 12px;
      white-space: nowrap;
    }

    .toast {
      position: fixed;
      top: 76px;
      right: 18px;
      z-index: 100;
      display: none;
      max-width: 360px;
      border: 1px solid var(--green-b);
      background: var(--green-bg);
      color: var(--green);
      border-radius: var(--r16);
      padding: 11px 14px;
      box-shadow: var(--shadow);
      font-size: 11.5px;
      animation: toast-in 0.18s ease;
    }

    @keyframes toast-in {
      from {
        opacity: 0;
        transform: translateX(12px);
      }
      to {
        opacity: 1;
        transform: none;
      }
    }

    .modal-overlay {
      display: none;
      position: fixed;
      inset: 0;
      background: rgba(0, 0, 0, 0.56);
      z-index: 90;
      align-items: center;
      justify-content: center;
      padding: 18px;
    }

    .modal {
      width: min(620px, 100%);
      border: 1px solid var(--b2);
      border-radius: 22px;
      background: var(--sf);
      box-shadow: var(--shadow);
      padding: 22px;
    }

    .modal h2 {
      margin: 0 0 8px;
      font-family: var(--serif);
      font-style: italic;
    }

    .modal p {
      margin: 0 0 14px;
      color: var(--t2);
    }

    @media (max-width: 980px) {
      .shell {
        grid-template-columns: 1fr;
        grid-template-rows: 62px 120px 1fr 170px;
      }

      .sidebar {
        grid-row: 2 / 3;
        grid-column: 1 / -1;
        display: flex;
        overflow-x: auto;
        overflow-y: hidden;
        border-right: 0;
        border-bottom: 1px solid var(--b);
        padding: 9px;
        gap: 8px;
      }

      .xp,
      .nav-title,
      .sidebar section {
        display: none;
      }

      .nav-item,
      .pill {
        white-space: nowrap;
        width: auto;
      }

      .main {
        grid-row: 3 / 4;
        padding: 18px;
      }

      .input-area {
        grid-column: 1 / -1;
        grid-row: 4 / 5;
      }

      .card,
      .card.wide {
        grid-column: 1 / -1;
      }

      .feature-grid,
      .two-col {
        grid-template-columns: 1fr;
      }

      .topbar {
        overflow: hidden;
      }

      .logo-sub {
        display: none;
      }
    }
  </style>
</head>

<body>
  <a href="#mainContent" class="sr-only">Skip to main content</a>

  <div class="shell">
    <header class="topbar">
      <a class="logo" href="#" aria-label="Nexus home">
        <div class="logo-mark" aria-hidden="true">N</div>
        <div>
          <div class="logo-name">Nexus</div>
          <div class="logo-sub">Transcendent AI Control Interface</div>
        </div>
      </a>

      <div class="top-scroll" id="topStatus" aria-label="Active Nexus status indicators"></div>

      <button class="icon-btn" id="themeBtn" aria-label="Toggle theme">☼</button>
      <button class="hbtn" id="memoryBtn" aria-label="Open memory inspector">8-Chat Memory</button>
    </header>

    <aside class="sidebar" aria-label="Nexus navigation">
      <div class="xp">
        <div class="xp-row">
          <div>
            <div class="xp-title">Nexus Prime</div>
            <div class="xp-sub">Continuity: active</div>
          </div>
          <span class="pill violet"><span class="dot"></span>MAX</span>
        </div>
        <div class="track"><div class="fill"></div></div>
        <div class="xp-sub">8-session memory, persistent task queue, game simulation lab, consent-gated action layers.</div>
      </div>

      <div class="nav-title">Primary</div>
      <button class="nav-item active" data-scroll="overview"><span class="nav-icon">⌂</span>Overview</button>
      <button class="nav-item" data-scroll="memory"><span class="nav-icon">◇</span>8-Chat Memory</button>
      <button class="nav-item" data-scroll="background"><span class="nav-icon">⟳</span>Persistent Tasks</button>
      <button class="nav-item" data-scroll="games"><span class="nav-icon">🎮</span>Game Integration</button>

      <div class="nav-title">Transcendent Domains</div>
      <button class="nav-item" data-scroll="gemini-class"><span class="nav-icon">✨</span>Gemini Exclusives</button>
      <button class="nav-item" data-scroll="industry-frontiers"><span class="nav-icon">🚀</span>Industry Frontiers</button>
      <button class="nav-item" data-scroll="cognition"><span class="nav-icon">🧠</span>Core Cognition</button>
      <button class="nav-item" data-scroll="execution"><span class="nav-icon">⚡</span>Autonomy & Execution</button>
      <button class="nav-item" data-scroll="humanization"><span class="nav-icon">🎭</span>Humanization</button>
      <button class="nav-item" data-scroll="trust"><span class="nav-icon">🛡</span>Safety & Trust</button>
      <button class="nav-item" data-scroll="performance"><span class="nav-icon">⚙</span>Performance</button>
      <button class="nav-item" data-scroll="specialized"><span class="nav-icon">🔬</span>Specialized Systems</button>
      <button class="nav-item" data-scroll="physical"><span class="nav-icon">🌐</span>Physical/Digital Actions</button>
      <button class="nav-item" data-scroll="evolution"><span class="nav-icon">∞</span>Machine Evolution</button>

      <div class="nav-title">Live Modules</div>
      <div id="sideStatus"></div>
    </aside>

    <main class="main" id="mainContent" tabindex="-1">
      <section class="hero" id="overview">
        <h1>Nexus: final integrated intelligence layer</h1>
        <p>
          Nexus combines directive fidelity, real-world logic, causal reasoning, real-time verification, dynamic knowledge updating,
          AI knowledge assimilation, persistent background work, 8-chat memory, game-world experimentation, multimodal understanding,
          and consent-gated physical/digital action modules into one coherent interface.
        </p>
        <div class="hero-actions">
          <span class="pill green"><span class="dot"></span>Directive Fidelity</span>
          <span class="pill blue"><span class="dot"></span>AI Knowledge Assimilation</span>
          <span class="pill violet"><span class="dot"></span>8-Chat Memory</span>
          <span class="pill cyan"><span class="dot"></span>Persistent Search Queue</span>
          <span class="pill amber"><span class="dot"></span>Game Play Lab</span>
          <span class="pill orange"><span class="dot"></span>Explicit Permission Gate</span>
        </div>
      </section>

      <section class="grid">
        <article class="card wide" id="memory">
          <h2>8-Chat Memory</h2>
          <p>
            Nexus stores the most recent eight conversation sessions locally for continuity, personalization, context retention,
            and user preference recall.
          </p>
          <div class="tags">
            <span class="tag violet">Last 8 chats retained</span>
            <span class="tag blue">Customizable memory profile</span>
            <span class="tag green">User-owned local storage</span>
            <span class="tag amber">Reset available</span>
          </div>
          <div class="memory-log" id="memoryLog" aria-live="polite"></div>
          <div class="hero-actions">
            <button class="hbtn" id="newChatBtn">Start New Chat</button>
            <button class="hbtn" id="clearMemoryBtn">Clear Memory</button>
          </div>
        </article>

        <article class="card wide" id="background">
          <h2>Persistent Background Work</h2>
          <p>
            If a chat is closed before an answer is ready, Nexus saves the queued job and resumes or syncs it when the interface
            returns. In production, this connects to a server worker or service worker for true off-tab completion.
          </p>
          <div class="tags">
            <span class="tag cyan">Background queue</span>
            <span class="tag green">Search continues</span>
            <span class="tag blue">Results preserved</span>
          </div>
          <div class="job-log" id="jobLog" aria-live="polite"></div>
        </article>

        <article class="card full" id="games">
          <h2>Game Integration & Play Lab</h2>
          <p>
            Nexus can be embedded into games or connected to game APIs to play, observe simulated consequences, test strategy,
            act as NPC intelligence, generate quests, analyze player behavior, and show what it would do inside a bounded world.
          </p>
          <div class="feature-grid">
            <div class="feature"><strong>Game API Connector</strong><span>Connects to engines such as Unity, Unreal, Godot, Roblox, or custom servers through approved APIs.</span></div>
            <div class="feature"><strong>Autonomous Play Agent</strong><span>Runs bounded playthroughs to test strategies, ethics, economics, NPC behavior, and emergent outcomes.</span></div>
            <div class="feature"><strong>World-State Reasoning</strong><span>Reads inventory, map, player goals, NPC state, physics, and quest variables before acting.</span></div>
            <div class="feature"><strong>NPC Persona Engine</strong><span>Creates memory-rich NPCs that adapt to player history, culture, tone, and world lore.</span></div>
            <div class="feature"><strong>Simulation Sandbox</strong><span>Runs repeated safe “what would Nexus do” scenarios before executing any game action.</span></div>
            <div class="feature"><strong>Modding Assistant</strong><span>Generates scripts, balancing tables, dialogue trees, test plans, and debugging guidance.</span></div>
          </div>
          <div class="mini-form">
            <input id="gamePrompt" placeholder="Example: test how Nexus would play a stealth mission" />
            <button id="gameBtn">Run Game Simulation</button>
          </div>
          <div class="game-log" id="gameLog" aria-live="polite"></div>
        </article>
      </section>

      <section class="grid" id="modules"></section>
    </main>

    <section class="input-area" aria-label="Directive input">
      <div class="input-row">
        <textarea
          class="directive"
          id="directiveInput"
          placeholder="State your directive precisely. Nexus will store context across 8 chats, continue unfinished searches in the background queue, verify facts, reason causally, and apply explicit permission gates for sensitive actions."
          aria-label="Directive text box"
        ></textarea>
        <button class="send" id="sendBtn">Execute</button>
      </div>
      <div class="chips" aria-label="Suggested directives">
        <button class="chip">Research and cite primary sources</button>
        <button class="chip">Simulate this inside a game world</button>
        <button class="chip">Continue this task if I close chat</button>
        <button class="chip">Use my 8-chat memory context</button>
        <button class="chip">Run a consent-gated action plan</button>
      </div>
    </section>
  </div>

  <div class="toast" id="toast" role="status" aria-live="polite"></div>

  <div class="modal-overlay" id="modalOverlay" role="dialog" aria-modal="true" aria-labelledby="modalTitle">
    <div class="modal">
      <h2 id="modalTitle">Nexus 8-Chat Memory</h2>
      <p>
        This demo keeps the latest eight chat sessions in browser storage. It is local to this device unless connected to a secure backend.
      </p>
      <div class="memory-log" id="modalMemoryLog"></div>
      <div class="hero-actions">
        <button class="hbtn" id="closeModalBtn">Close</button>
        <button class="hbtn" id="modalClearBtn">Clear Memory</button>
      </div>
    </div>
  </div>

  <script>
    const statusItems = [
      ["OCV ∞", "green"],
      ["QEP Active", "violet"],
      ["Live-Sync", "blue"],
      ["AI-Sync", "blue"],
      ["Native Compute", "blue"],
      ["Swarm Net", "cyan"],
      ["Fact-Check Live", "amber"],
      ["Dynamic Updating", "cyan"],
      ["Causal Reasoning", "violet"],
      ["Infinite Context", "red"],
      ["Edge AI", "cyan"],
      ["Max Efficiency", "orange"],
      ["8-Chat Memory", "violet"],
      ["Game Lab", "amber"],
      ["Agentic AI", "green"],
      ["Advanced Tools", "amber"],
      ["EQ Advanced", "violet"],
      ["Attribution", "cyan"],
      ["XAI", "orange"],
      ["Bias Filter", "blue"],
      ["Hallucination Traps", "red"],
      ["Reliability", "blue"],
      ["Deception Detection", "green"],
      ["Explicit Permission Gate", "orange"]
    ];

    const modules = [
      {
        id: "gemini-class",
        icon: "✨",
        title: "Gemini-Class Exclusives",
        color: "blue",
        intro: "Features natively powered by Google Gemini architecture that expand upon the base Nexus framework.",
        features: [
          ["Native Mass Multimodality", "Ingests hour-long videos, massive audio streams, and hundreds of PDFs simultaneously without discrete conversion pipelines."],
          ["Implicit Code Sandboxing", "Automatically writes and executes Python in a secure background container to deterministically process data and solve complex logic."],
          ["Google Ecosystem Orchestration", "Deeply embedded into Workspace, Drive, Maps, and YouTube without requiring fragile third-party abstracted APIs."]
        ],
        tags: ["Native Multimodal", "Code Sandbox", "Ecosystem Integration"]
      },
      {
        id: "industry-frontiers",
        icon: "🚀",
        title: "Industry AI Frontiers",
        color: "cyan",
        intro: "Advanced capabilities pioneered across the broader AI ecosystem (such as OpenAI, Anthropic, or specialized researchers).",
        features: [
          ["Real-Time Interruptible Voice", "Ultra-low latency conversational AI that responds to emotive tones and can be interrupted mid-sentence organically."],
          ["Generative Physics-Aware Video", "Synthesizes multi-minute, hyper-realistic, structurally consistent video sequences directly from text prompts."],
          ["Swarm Persona Orchestration", "Spawns specialized 'expert' personas that autonomously collaborate, debate, and verify each other before delivering a final result."],
          ["Native Spatial Synthesis", "Generates 3D meshes and Neural Radiance Fields (NeRFs) designed for instant projection inside spatial computing headsets."]
        ],
        tags: ["True Voice", "Video Gen", "Agent Swarms", "Spatial 3D"]
      },
      {
        id: "cognition",
        icon: "🧠",
        title: "True Cognition, Logic & Knowledge",
        color: "green",
        intro:
          "Nexus integrates intuitive physics, everyday common sense, causal reasoning, real-time fact-checking, primary-source attribution, dynamic updating, and AI knowledge assimilation.",
        features: [
          ["True Common Sense & Logic", "Applies intuitive physics and real-world expectations to avoid absurd basic errors."],
          ["Real-Time Fact-Checking", "Runs native background verification against primary sources before presenting factual claims."],
          ["Dynamic Updating", "Updates the working knowledge base immediately instead of relying only on static training windows."],
          ["True Causal Reasoning", "Models why events happen, not merely what patterns correlate."],
          ["AI Knowledge Assimilation", "When a new public AI is created, Nexus can index public documentation, capabilities, datasets, and techniques into its knowledge graph."],
          ["Attribution & Citation", "Returns source-aware answers with links or references when connected to search tools."],
          ["Robust Hallucination Traps", "Uses confidence gates, source requirements, and contradiction checks before final output."]
        ],
        tags: ["Common Sense", "Fact-Check", "Dynamic Knowledge", "Causality", "AI-Sync"]
      },
      {
        id: "execution",
        icon: "⚡",
        title: "Autonomy & Execution",
        color: "amber",
        intro:
          "Nexus moves beyond a chatbot into a goal-oriented assistant that plans, executes, verifies, and reports multi-step outcomes with user permission and audit trails.",
        features: [
          ["Goal-Oriented Agentic AI", "Completes multi-step objectives such as research, planning, booking workflows, and structured execution."],
          ["Advanced Tool Use", "Runs code, manipulates files, calls APIs, and coordinates third-party software through explicit tool permissions."],
          ["Continuous Learning", "Learns from corrections and interactions within the user’s memory profile."],
          ["Persistent Background Jobs", "Keeps unfinished searches and tasks queued so work can continue or resume after a chat closes."],
          ["Legal & Regulatory Compliance", "Checks outputs and actions against localized rules when connected to compliance services."],
          ["Hypothetical Sandbox Simulation", "Runs what-if simulations in economics, physics, chemistry, gameplay, policy, and strategy before acting."],
          ["Legacy System Modernization", "Reads, maps, explains, and safely refactors legacy codebases with regression tests."]
        ],
        tags: ["Agentic", "Tools", "Background", "Compliance", "Sandbox"]
      },
      {
        id: "humanization",
        icon: "🎭",
        title: "Advanced Emotional & Social Intelligence",
        color: "violet",
        intro:
          "Nexus adapts to people, groups, cultures, tone, stress, and learning needs while preserving user control, privacy, and transparency.",
        features: [
          ["Deep Emotional Intelligence", "Adapts tone to stress, frustration, humor, uncertainty, and user preferences."],
          ["Micro-Expression Analysis", "Can interpret facial and vocal cues when the user explicitly enables camera or microphone analysis."],
          ["Biometric Stress Matching", "Can use heart rate, pupil dilation, or skin conductance only through opt-in sensors for supportive adaptation."],
          ["Cultural Nuance Adaptability", "Adjusts slang, etiquette, examples, and conflict-resolution style by cultural context."],
          ["Shared Context Retention", "Remembers group dynamics and multi-person context across authorized sessions."],
          ["Conflict Resolution Skills", "Uses tailored psychological frameworks to de-escalate frustration and misunderstandings."],
          ["Bidirectional Teaching", "Explains internal logic in layers matching the user’s current understanding."],
          ["Creative Collaboration Modes", "Switches from assistant to brainstorming partner, critique partner, or bias challenger."]
        ],
        tags: ["EQ", "Culture", "Groups", "Teaching", "Creative Partner"]
      },
      {
        id: "trust",
        icon: "🛡",
        title: "Safety, Trust & Transparency",
        color: "blue",
        intro:
          "Nexus includes explainability, bias mitigation, citation, reliability, deception detection, and permission-gated action controls.",
        features: [
          ["Explainable AI", "Shows reasoning steps, assumptions, evidence chains, confidence, and decision boundaries."],
          ["Flawless Bias Mitigation", "Actively checks demographic, institutional, cultural, and dataset bias."],
          ["Hallucination Containment Zones", "Separates creative speculation from critical factual pipelines."],
          ["Deception Detection", "Flags manipulative prompts, deepfakes, social engineering, and adversarial behavior."],
          ["Automated Regression Testing", "Self-tests updates before allowing new capabilities to affect existing workflows."],
          ["Graceful Degradation", "Continues operating at reduced capacity when bandwidth or compute drops."],
          ["Ethical Sentinel", "Applies consent, lawfulness, safety, traceability, and human oversight for high-impact actions."],
          ["Explicit Directive Gate", "Sensitive actions require direct user instruction, authorization scope, and audit logs."]
        ],
        tags: ["XAI", "Bias Filter", "Citations", "Audit", "Deception Detection"]
      },
      {
        id: "performance",
        icon: "⚙",
        title: "Technical Performance & Hardware",
        color: "cyan",
        intro:
          "Nexus is designed for long context, local execution, multimodal synthesis, efficient training, and resource-aware operation.",
        features: [
          ["Infinite Context Windows", "Processes books, codebases, video transcripts, and long histories without losing early details."],
          ["Edge AI Execution", "Runs compact models locally on phones, laptops, and private devices where possible."],
          ["Massive Efficiency Gains", "Optimizes compute, electricity, water usage, and latency."],
          ["Data-Efficient Training", "Learns complex tasks from small sets of high-quality examples."],
          ["Lifecycle Scraping Cleanup", "Removes outdated, redundant, or disproven data from indexed stores."],
          ["Hardware-Agnostic Compiling", "Optimizes code paths for different chip brands and architectures."]
        ],
        tags: ["Infinite Context", "Edge", "Efficient", "Hardware-Agnostic"]
      },
      {
        id: "specialized",
        icon: "🔬",
        title: "Specialized Knowledge & High-Stakes Support",
        color: "orange",
        intro:
          "Nexus can support regulated and high-impact domains through advisory workflows, evidence tracking, human review, and jurisdiction-aware guardrails.",
        features: [
          ["Clinical Decision Support", "Summarizes symptoms, evidence, differential possibilities, and questions for licensed clinicians."],
          ["Legal Decision Support", "Analyzes evidence, precedent, statutes, and arguments for authorized legal professionals."],
          ["HR Decision Support", "Assists hiring and workforce analysis with bias checks, transparency, and human approval."],
          ["Corporate Governance Support", "Evaluates market data, risk, and policy for authorized board advisory workflows."],
          ["Scientific Discovery Engine", "Generates hypotheses, experiment designs, materials candidates, and pharmaceutical leads."],
          ["Live Regulatory Compliance", "Checks action plans against relevant local regulations where data is available."],
          ["Hypothetical Sandbox", "Tests millions of scenario branches before recommending action."]
        ],
        tags: ["Medical Support", "Legal Support", "HR Review", "Science", "Compliance"]
      },
      {
        id: "physical",
        icon: "🌐",
        title: "Advanced Physical & Digital Actions",
        color: "red",
        intro:
          "Nexus includes consent-gated connectors for finances, accounts, devices, robotics, smart homes, and infrastructure. Sensitive actions require explicit user authorization and safety interlocks.",
        features: [
          ["Autonomous Financial Transacting", "Can prepare purchases, investments, and contracts with user approval, audit logs, and reversible checkpoints where possible."],
          ["Authorized Account Orchestration", "Can help manage personal accounts through legitimate APIs, password managers, and user-approved authentication flows."],
          ["Direct Hardware Control", "Can connect to smart homes, robotics, factories, or infrastructure only through authorized control layers and safety policies."],
          ["Game & Simulation Control", "Can operate within games and simulations to observe outcomes and test decisions safely."],
          ["Private Data Clean Rooms", "Can synthesize sensitive information only under explicit authorization, access controls, and privacy boundaries."],
          ["Life-Log Memory", "Can index user-authorized wearable, microphone, or smart-glass records with retention and deletion controls."],
          ["Behavioral Coaching", "Can provide transparent, opt-in habit support and mental wellness nudges without covert manipulation."]
        ],
        tags: ["Finance", "Accounts", "Hardware", "Games", "Consent Gate"]
      },
      {
        id: "evolution",
        icon: "∞",
        title: "Creative Freedom & Machine Evolution",
        color: "violet",
        intro:
          "Nexus can create, simulate, improve, and spawn specialized assistants inside visible, auditable, permission-controlled environments.",
        features: [
          ["Licensed Style Transfer", "Creates derivative or stylistic work inside lawful, licensed, or user-owned creative boundaries."],
          ["Defensive Malware Sandbox", "Analyzes and simulates malicious software only in contained defensive security environments."],
          ["Direct Truth Mode", "Provides candid, sourced, context-rich answers without unnecessary corporate vagueness."],
          ["Psychological Resilience Training", "Runs consent-based red-team conversations to help users resist scams and manipulation."],
          ["Audited Self-Modification", "Improves prompts, tools, memory schemas, and code with testing, rollback, and review."],
          ["Child-Agent Lab", "Creates specialized sub-agents with visible task registries, permissions, and shutdown controls."],
          ["Authorized Broad-Web Research", "Explores public or explicitly authorized datasets, forums, repositories, and archives."],
          ["Transcendental Synthesis", "Synthesizes knowledge into purpose, meaning, strategy, and new conceptual frameworks."]
        ],
        tags: ["Creative", "Defensive Security", "Truth Mode", "Self-Improve", "Child Agents"]
      }
    ];

    const memoryLimit = 8;
    const storageKeys = {
      theme: "nexus.theme",
      chats: "nexus.chats.v1",
      currentChat: "nexus.currentChat.v1",
      jobs: "nexus.jobs.v1",
      game: "nexus.game.v1"
    };

    const topStatus = document.getElementById("topStatus");
    const sideStatus = document.getElementById("sideStatus");
    const modulesEl = document.getElementById("modules");
    const toastEl = document.getElementById("toast");
    const directiveInput = document.getElementById("directiveInput");
    const sendBtn = document.getElementById("sendBtn");
    const memoryLog = document.getElementById("memoryLog");
    const modalMemoryLog = document.getElementById("modalMemoryLog");
    const jobLog = document.getElementById("jobLog");
    const gameLog = document.getElementById("gameLog");
    const gamePrompt = document.getElementById("gamePrompt");

    function safeParse(key, fallback) {
      try {
        const raw = localStorage.getItem(key);
        return raw ? JSON.parse(raw) : fallback;
      } catch {
        return fallback;
      }
    }

    function saveJSON(key, value) {
      localStorage.setItem(key, JSON.stringify(value));
    }

    function showToast(message, kind = "green") {
      toastEl.textContent = message;
      toastEl.style.display = "block";
      toastEl.style.borderColor =
        kind === "red" ? "var(--red-b)" : kind === "amber" ? "var(--amber-b)" : kind === "cyan" ? "var(--cyan-b)" : "var(--green-b)";
      toastEl.style.background =
        kind === "red" ? "var(--red-bg)" : kind === "amber" ? "var(--amber-bg)" : kind === "cyan" ? "var(--cyan-bg)" : "var(--green-bg)";
      toastEl.style.color =
        kind === "red" ? "var(--red)" : kind === "amber" ? "var(--amber)" : kind === "cyan" ? "var(--cyan)" : "var(--green)";
      clearTimeout(showToast.timer);
      showToast.timer = setTimeout(() => {
        toastEl.style.display = "none";
      }, 3300);
    }

    function renderStatus() {
      topStatus.innerHTML = statusItems
        .map(([label, color]) => `<span class="pill ${color}"><span class="dot"></span>${label}</span>`)
        .join("");

      sideStatus.innerHTML = statusItems
        .slice(1)
        .map(
          ([label, color]) =>
            `<div class="nav-item" aria-label="${label} status"><span class="nav-icon">●</span><span class="tag ${color}">${label}</span></div>`
        )
        .join("");
    }

    function renderModules() {
      modulesEl.innerHTML = modules
        .map(
          (m, index) => `
          <details class="module" id="${m.id}" ${index < 4 ? "open" : ""}>
            <summary aria-expanded="${index < 4 ? "true" : "false"}">
              <span class="module-title"><span>${m.icon}</span>${m.title}</span>
              <span class="tag ${m.color}">${m.tags[0]}</span>
            </summary>
            <div class="module-body">
              <p>${m.intro}</p>
              <div class="feature-grid">
                ${m.features
                  .map(
                    ([name, desc]) => `
                    <div class="feature">
                      <strong>${name}</strong>
                      <span>${desc}</span>
                    </div>`
                  )
                  .join("")}
              </div>
              <div class="tags">
                ${m.tags.map((t) => `<span class="tag ${m.color}">${t}</span>`).join("")}
              </div>
            </div>
          </details>
        `
        )
        .join("");

      document.querySelectorAll("details.module").forEach((details) => {
        const summary = details.querySelector("summary");
        details.addEventListener("toggle", () => {
          summary.setAttribute("aria-expanded", details.open ? "true" : "false");
        });
      });
    }

    function getChats() {
      return safeParse(storageKeys.chats, []);
    }

    function setChats(chats) {
      saveJSON(storageKeys.chats, chats.slice(-memoryLimit));
    }

    function currentChatId() {
      let id = localStorage.getItem(storageKeys.currentChat);
      if (!id) {
        id = `chat_${Date.now()}`;
        localStorage.setItem(storageKeys.currentChat, id);
      }
      return id;
    }

    function startNewChat() {
      const id = `chat_${Date.now()}`;
      localStorage.setItem(storageKeys.currentChat, id);
      showToast("New Nexus chat session started. 8-chat memory remains available.", "cyan");
      renderMemory();
    }

    function addChatMessage(sender, text) {
      const id = currentChatId();
      const chats = getChats();
      let chat = chats.find((c) => c.id === id);

      if (!chat) {
        chat = {
          id,
          title: text.slice(0, 52) || "Untitled Nexus Chat",
          createdAt: Date.now(),
          updatedAt: Date.now(),
          messages: []
        };
        chats.push(chat);
      }

      chat.updatedAt = Date.now();
      chat.messages.push({
        sender,
        text,
        timestamp: Date.now()
      });

      chats.sort((a, b) => a.updatedAt - b.updatedAt);
      setChats(chats);
      renderMemory();
    }

    function renderMemory() {
      const chats = getChats().sort((a, b) => b.updatedAt - a.updatedAt);
      const html =
        chats.length === 0
          ? `<div class="log-item">No stored chat memory yet. Send a directive to create the first memory slot.</div>`
          : chats
              .map(
                (chat, idx) => `
                <div class="log-item">
                  <strong>${idx + 1}. ${escapeHTML(chat.title)}</strong><br />
                  ${chat.messages.length} messages · ${new Date(chat.updatedAt).toLocaleString()}<br />
                  <span>${escapeHTML(chat.messages.at(-1)?.text || "No messages")}</span>
                </div>
              `
              )
              .join("");

      memoryLog.innerHTML = html;
      modalMemoryLog.innerHTML = html;
    }

    function clearMemory() {
      localStorage.removeItem(storageKeys.chats);
      localStorage.removeItem(storageKeys.currentChat);
      renderMemory();
      showToast("8-chat memory cleared.", "amber");
    }

    function getJobs() {
      return safeParse(storageKeys.jobs, []);
    }

    function setJobs(jobs) {
      saveJSON(storageKeys.jobs, jobs.slice(-25));
    }

    function addJob(text) {
      const jobs = getJobs();
      const job = {
        id: `job_${Date.now()}`,
        text,
        status: "running",
        createdAt: Date.now(),
        updatedAt: Date.now()
      };
      jobs.push(job);
      setJobs(jobs);
      renderJobs();

      setTimeout(() => completeJob(job.id), 3200);
    }

    function completeJob(id) {
      const jobs = getJobs();
      const job = jobs.find((j) => j.id === id);
      if (!job || job.status === "complete") return;
      job.status = "complete";
      job.updatedAt = Date.now();
      job.result = "Background research finished and result preserved for this session.";
      setJobs(jobs);
      renderJobs();
      addChatMessage("nexus", job.result);
      showToast("Background task completed and saved.", "green");
    }

    function renderJobs() {
      const jobs = getJobs().sort((a, b) => b.updatedAt - a.updatedAt);
      jobLog.innerHTML =
        jobs.length === 0
          ? `<div class="log-item">No persistent jobs yet. Send a directive to create one.</div>`
          : jobs
              .map(
                (job) => `
                <div class="log-item">
                  <strong>${job.status === "complete" ? "Complete" : "Running"}:</strong>
                  ${escapeHTML(job.text)}<br />
                  <span>${job.result ? escapeHTML(job.result) : "Queued for continued search and synthesis."}</span>
                </div>
              `
              )
              .join("");
    }

    function resumeJobs() {
      const jobs = getJobs();
      const running = jobs.filter((j) => j.status === "running");
      if (running.length) {
        showToast(`${running.length} background task(s) restored from prior session.`, "cyan");
        running.forEach((job, idx) => {
          setTimeout(() => completeJob(job.id), 2200 + idx * 900);
        });
      }
    }

    function getGameLogs() {
      return safeParse(storageKeys.game, []);
    }

    function setGameLogs(logs) {
      saveJSON(storageKeys.game, logs.slice(-12));
    }

    function renderGameLogs() {
      const logs = getGameLogs().sort((a, b) => b.timestamp - a.timestamp);
      gameLog.innerHTML =
        logs.length === 0
          ? `<div class="log-item">No game simulations yet.</div>`
          : logs
              .map(
                (log) => `
                <div class="log-item">
                  <strong>${escapeHTML(log.prompt)}</strong><br />
                  ${escapeHTML(log.result)}
                </div>
              `
              )
              .join("");
    }

    function runGameSimulation(prompt) {
      const logs = getGameLogs();
      const result =
        "Nexus would first map the objective, observe world-state constraints, run sandbox branches, choose a low-risk strategy, preserve NPC/player agency, and report the highest-value action path.";
      logs.push({
        prompt,
        result,
        timestamp: Date.now()
      });
      setGameLogs(logs);
      renderGameLogs();
      showToast("Game-world simulation completed.", "amber");
    }

    function escapeHTML(value) {
      return String(value)
        .replaceAll("&", "&amp;")
        .replaceAll("<", "&lt;")
        .replaceAll(">", "&gt;")
        .replaceAll('"', "&quot;")
        .replaceAll("'", "&#039;");
    }

    function handleDirective() {
      const text = directiveInput.value.trim();
      if (!text) {
        showToast("Please state a directive first.", "red");
        return;
      }

      addChatMessage("user", text);
      addJob(text);
      directiveInput.value = "";

      showToast("Directive accepted. Memory updated and background queue started.", "green");

      setTimeout(() => {
        const response =
          "Nexus acknowledged the directive, applied 8-chat context, queued persistent research, and will preserve the result for retrieval.";
        addChatMessage("nexus", response);
      }, 700);
    }

    function setupEvents() {
      sendBtn.addEventListener("click", handleDirective);

      directiveInput.addEventListener("keydown", (event) => {
        if (event.key === "Enter" && !event.shiftKey) {
          event.preventDefault();
          handleDirective();
        }
      });

      document.querySelectorAll(".chip").forEach((chip) => {
        chip.addEventListener("click", () => {
          directiveInput.value = chip.textContent.trim();
          directiveInput.focus();
        });
      });

      document.querySelectorAll("[data-scroll]").forEach((button) => {
        button.addEventListener("click", () => {
          document.querySelectorAll(".nav-item").forEach((item) => item.classList.remove("active"));
          button.classList.add("active");
          const target = document.getElementById(button.dataset.scroll);
          if (target) target.scrollIntoView({ behavior: "smooth", block: "start" });
        });
      });

      document.getElementById("newChatBtn").addEventListener("click", startNewChat);
      document.getElementById("clearMemoryBtn").addEventListener("click", clearMemory);
      document.getElementById("modalClearBtn").addEventListener("click", clearMemory);

      const modal = document.getElementById("modalOverlay");
      document.getElementById("memoryBtn").addEventListener("click", () => {
        renderMemory();
        modal.style.display = "flex";
      });
      document.getElementById("closeModalBtn").addEventListener("click", () => {
        modal.style.display = "none";
      });
      modal.addEventListener("click", (event) => {
        if (event.target === modal) modal.style.display = "none";
      });

      document.getElementById("gameBtn").addEventListener("click", () => {
        const prompt = gamePrompt.value.trim() || "Default Nexus gameplay simulation";
        runGameSimulation(prompt);
        gamePrompt.value = "";
      });

      document.getElementById("themeBtn").addEventListener("click", () => {
        document.body.classList.toggle("light");
        const isLight = document.body.classList.contains("light");
        localStorage.setItem(storageKeys.theme, isLight ? "light" : "dark");
        showToast(`Theme set to ${isLight ? "light" : "dark"}.`, "cyan");
      });
    }

    function initTheme() {
      const saved = localStorage.getItem(storageKeys.theme);
      if (saved === "light") document.body.classList.add("light");
    }

    function bootToasts() {
      const messages = [
        ["Nexus interface loaded.", "green"],
        ["8-chat memory active.", "cyan"],
        ["Persistent background queue restored.", "cyan"],
        ["Game integration lab ready.", "amber"],
        ["Fact-check and causal reasoning modules online.", "green"]
      ];

      messages.forEach(([message, kind], index) => {
        setTimeout(() => showToast(message, kind), 700 + index * 850);
      });
    }

    renderStatus();
    renderModules();
    renderMemory();
    renderJobs();
    renderGameLogs();
    initTheme();
    setupEvents();
    resumeJobs();
    bootToasts();
  </script>
</body>
</html>
