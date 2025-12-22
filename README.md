# SRIRAM
<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8" />
  <title>Operations Analytics Login</title>
  <meta name="viewport" content="width=device-width, initial-scale=1" />

  <style>
    :root {
      --bg: #0f172a;
      --card-bg: #0b1120;
      --accent: #22c55e;
      --accent-soft: rgba(34,197,94,0.12);
      --border: #1e293b;
      --text-main: #e5e7eb;
      --text-muted: #9ca3af;
      --error: #f97373;
    }

    * { box-sizing: border-box; margin: 0; padding: 0; }

    body {
      min-height: 100vh;
      font-family: system-ui, -apple-system, BlinkMacSystemFont, "Segoe UI", sans-serif;
      background:
        radial-gradient(circle at 0 0, #1f2937 0, #020617 45%, #000000 100%);
      color: var(--text-main);
      display: flex;
      align-items: center;
      justify-content: center;
      padding: 24px;
    }

    .shell {
      max-width: 960px;
      width: 100%;
      display: grid;
      gap: 32px;
      grid-template-columns: minmax(0, 1.1fr) minmax(0, 1fr);
      align-items: stretch;
    }

    @media (max-width: 800px) {
      .shell { grid-template-columns: minmax(0, 1fr); }
    }

    .panel-left {
      padding: 32px 28px;
      border-radius: 18px;
      background:
        radial-gradient(circle at 0 0, rgba(56,189,248,0.2), transparent 55%),
        radial-gradient(circle at 100% 100%, rgba(34,197,94,0.22), transparent 55%),
        linear-gradient(135deg, rgba(15,23,42,0.96), rgba(15,23,42,0.96));
      border: 1px solid rgba(148,163,184,0.35);
      box-shadow: 0 25px 80px rgba(15,23,42,0.85);
      position: relative;
      overflow: hidden;
    }

    .panel-left::after {
      content: "";
      position: absolute;
      inset: 0;
      opacity: 0.3;
      background-image: linear-gradient(120deg, rgba(148,163,184,0.22) 1px, transparent 1px),
                       linear-gradient(210deg, rgba(51,65,85,0.25) 1px, transparent 1px);
      background-size: 110px 110px;
      mix-blend-mode: soft-light;
      pointer-events: none;
    }

    .panel-left-inner {
      position: relative;
      z-index: 1;
    }

    .badge {
      display: inline-flex;
      align-items: center;
      gap: 8px;
      padding: 4px 10px;
      border-radius: 999px;
      border: 1px solid rgba(148,163,184,0.4);
      background: rgba(15,23,42,0.85);
      font-size: 11px;
      color: var(--text-muted);
      margin-bottom: 14px;
    }

    .badge-dot {
      width: 8px;
      height: 8px;
      border-radius: 999px;
      background: #22c55e;
      box-shadow: 0 0 0 4px rgba(34,197,94,0.4);
    }

    .headline {
      font-size: 26px;
      line-height: 1.3;
      letter-spacing: 0.03em;
      margin-bottom: 10px;
    }

    .subhead {
      font-size: 14px;
      color: var(--text-muted);
      max-width: 420px;
      margin-bottom: 24px;
    }

    .meta-row {
      display: flex;
      flex-wrap: wrap;
      gap: 10px;
      margin-bottom: 26px;
    }

    .meta-pill {
      font-size: 11px;
      padding: 4px 10px;
      border-radius: 999px;
      border: 1px solid rgba(148,163,184,0.4);
      color: var(--text-muted);
      background: rgba(15,23,42,0.85);
    }

    .preview {
      margin-top: 10px;
      border-radius: 16px;
      border: 1px solid rgba(55,65,81,0.85);
      background: radial-gradient(circle at 0 0,#1e293b 0,#020617 75%);
      padding: 14px 16px 12px;
      display: grid;
      grid-template-columns: minmax(0,1.4fr) minmax(0,1fr);
      gap: 14px;
      font-size: 11px;
      color: var(--text-muted);
    }

    @media (max-width: 800px) {
      .preview { grid-template-columns: minmax(0,1fr); }
    }

    .preview-title {
      font-size: 13px;
      margin-bottom: 4px;
      color: var(--text-main);
      font-weight: 600;
    }

    .preview-chip {
      display: inline-flex;
      align-items: center;
      gap: 6px;
      padding: 3px 8px;
      border-radius: 999px;
      font-size: 10px;
      border: 1px solid rgba(74,222,128,0.4);
      background: rgba(22,163,74,0.12);
      color: #bbf7d0;
      margin-top: 6px;
    }

    .preview-chip-dot {
      width: 7px;
      height: 7px;
      border-radius: 999px;
      background: #4ade80;
    }

    .panel-right {
      padding: 26px 24px 24px;
      border-radius: 18px;
      background: var(--card-bg);
      border: 1px solid var(--border);
      box-shadow: 0 22px 60px rgba(15,23,42,0.7);
      display: flex;
      flex-direction: column;
      justify-content: center;
    }

    .form-title {
      font-size: 18px;
      margin-bottom: 4px;
    }

    .form-subtitle {
      font-size: 12px;
      color: var(--text-muted);
      margin-bottom: 18px;
    }

    .field {
      margin-bottom: 14px;
    }

    label {
      display: block;
      font-size: 12px;
      margin-bottom: 6px;
      color: var(--text-muted);
    }

    .input-wrap {
      position: relative;
    }

    input[type="text"],
    input[type="password"] {
      width: 100%;
      padding: 10px 12px;
      border-radius: 10px;
      border: 1px solid #1f2937;
      background: #020617;
      color: var(--text-main);
      font-size: 13px;
      transition: border-color 0.16s ease, box-shadow 0.16s ease, background 0.16s ease;
    }

    input::placeholder { color: #6b7280; }

    input:focus {
      outline: none;
      border-color: var(--accent);
      box-shadow: 0 0 0 1px rgba(34,197,94,0.6);
      background: #020617;
    }

    .hint {
      font-size: 10px;
      color: var(--text-muted);
      margin-top: 4px;
    }

    .error {
      margin-top: 8px;
      font-size: 11px;
      color: var(--error);
      min-height: 16px;
    }

    .success {
      margin-top: 8px;
      font-size: 11px;
      color: #4ade80;
      min-height: 16px;
    }

    button {
      margin-top: 8px;
      width: 100%;
      border: none;
      border-radius: 999px;
      padding: 10px 14px;
      background: linear-gradient(135deg,#22c55e,#16a34a);
      color: #f9fafb;
      font-size: 13px;
      font-weight: 600;
      letter-spacing: 0.04em;
      text-transform: uppercase;
      cursor: pointer;
      box-shadow: 0 14px 40px rgba(22,163,74,0.6);
      transition: transform 0.14s ease, box-shadow 0.14s ease, filter 0.14s ease;
    }

    button:hover {
      transform: translateY(-1px);
      filter: brightness(1.02);
      box-shadow: 0 18px 55px rgba(22,163,74,0.75);
    }

    button:active {
      transform: translateY(0);
      box-shadow: 0 10px 30px rgba(22,163,74,0.55);
    }

    .footer-row {
      margin-top: 18px;
      display: flex;
      justify-content: space-between;
      font-size: 10px;
      color: var(--text-muted);
    }

    .link {
      color: var(--accent);
      text-decoration: none;
    }

    .link:hover { text-decoration: underline; }

    .dashboard-link {
      margin-top: 12px;
      display: none;
      font-size: 12px;
    }

    .dashboard-link a {
      color: var(--accent);
      text-decoration: none;
      font-weight: 500;
    }

    .dashboard-link a:hover {
      text-decoration: underline;
    }
  </style>
</head>
<body>
  <div class="shell">
    <!-- Left info panel -->
    <section class="panel-left">
      <div class="panel-left-inner">
        <div class="badge">
          <span class="badge-dot"></span>
          Operations Analytics · Secure Access
        </div>
        <h1 class="headline">Welcome, Sriram</h1>
        <p class="subhead">
          Use your single‑user credential to launch the Operations Analytics Hub.
          Access is restricted and every login is tied to the current date for traceability.
        </p>

        <div class="meta-row">
          <span class="meta-pill">User: Sriram</span>
          <span class="meta-pill">Password suffix: today’s date (YYYYMMDD)</span>
          <span class="meta-pill">Environment: Production</span>
        </div>

        <div class="preview">
          <div>
            <div class="preview-title">Password pattern</div>
            <p>
              The password is built as:
              <strong>Sriram + today’s date in YYYYMMDD format</strong>.  
              Example: if today is 2025‑12‑22, password becomes
              <strong>Sriram20251222</strong>.
            </p>
            <div class="preview-chip">
              <span class="preview-chip-dot"></span>
              Generated dynamically on login
            </div>
          </div>
          <div>
            <div class="preview-title">Hint</div>
            <p>
              Make sure your device date and time are correct, otherwise the
              expected suffix will not match and authentication will fail.
            </p>
          </div>
        </div>
      </div>
    </section>

    <!-- Right login panel -->
    <section class="panel-right">
      <h2 class="form-title">Sign in to continue</h2>
      <p class="form-subtitle">
        Enter your credentials. Password changes every day based on the date suffix.
      </p>

      <form id="loginForm" autocomplete="off">
        <div class="field">
          <label for="username">User name</label>
          <div class="input-wrap">
            <input
              id="username"
              name="username"
              type="text"
              placeholder="Enter user name"
            />
          </div>
        </div>

        <div class="field">
          <label for="password">Password</label>
          <div class="input-wrap">
            <input
              id="password"
              name="password"
              type="password"
              placeholder="SriramYYYYMMDD"
            />
          </div>
          <div class="hint">
            Format: Sriram + today’s date (YYYYMMDD), e.g. Sriram20251222.
          </div>
        </div>

        <div id="error" class="error"></div>
        <div id="success" class="success"></div>

        <button type="submit">Authenticate</button>

        <div id="dashboardLink" class="dashboard-link">
          Login successful.  
          <a href="index.html" target="_blank" rel="noopener noreferrer">
            Open Operations Analytics Hub
          </a>
        </div>

        <div class="footer-row">
          <span>© <span id="year"></span> Operations Analytics</span>
          <span>Secured login · Sriram only</span>
        </div>
      </form>
    </section>
  </div>

  <script>
    function formatTodayYYYYMMDD() {
      const d = new Date();
      const y = d.getFullYear();
      const m = String(d.getMonth() + 1).padStart(2, "0");
      const day = String(d.getDate()).padStart(2, "0");
      return `${y}${m}${day}`;
    }

    document.getElementById("year").textContent = new Date().getFullYear();

    const form = document.getElementById("loginForm");
    const errorEl = document.getElementById("error");
    const successEl = document.getElementById("success");
    const dashboardLink = document.getElementById("dashboardLink");

    form.addEventListener("submit", function (e) {
      e.preventDefault();
      errorEl.textContent = "";
      successEl.textContent = "";
      dashboardLink.style.display = "none";

      const username = document.getElementById("username").value.trim();
      const password = document.getElementById("password").value.trim();

      const todaySuffix = formatTodayYYYYMMDD();
      const expectedUser = "Sriram";
      const expectedPassword = expectedUser + todaySuffix;

      if (username !== expectedUser) {
        errorEl.textContent = "Invalid user name. Only Sriram is allowed.";
        return;
      }

      if (password !== expectedPassword) {
        errorEl.textContent =
          "Invalid password. Use Sriram followed by today’s date in YYYYMMDD format.";
        return;
      }

      successEl.textContent = "Authentication successful.";
      dashboardLink.style.display = "block";
    });
  </script>
</body>
</html>

<html lang="en">
<head>
    <meta charset="UTF-8">
    <title>Operations Analytics Hub</title>
    <meta name="viewport" content="width=device-width, initial-scale=1">

    <!-- Simple, reliable, responsive layout -->
    <style>
        :root {
            --bg: #f5f7fb;
            --card-bg: #ffffff;
            --primary: #2563eb;
            --primary-soft: #e0ecff;
            --text-main: #111827;
            --text-muted: #6b7280;
            --border: #e5e7eb;
            --shadow-soft: 0 10px 25px rgba(15, 23, 42, 0.06);
            --radius-lg: 14px;
            --radius-sm: 8px;
        }

        * {
            box-sizing: border-box;
            margin: 0;
            padding: 0;
        }

        body {
            font-family: system-ui, -apple-system, BlinkMacSystemFont, "Segoe UI", sans-serif;
            background: radial-gradient(circle at top left,#eef2ff 0,#f5f7fb 42%,#f9fafb 100%);
            color: var(--text-main);
            min-height: 100vh;
            display: flex;
            flex-direction: column;
        }

        /* Top navigation */
        .nav {
            display: flex;
            align-items: center;
            justify-content: space-between;
            padding: 16px 32px;
            border-bottom: 1px solid rgba(148,163,184,.35);
            backdrop-filter: blur(20px);
            background: linear-gradient(to right,rgba(248,250,252,.9),rgba(239,246,255,.9));
            position: sticky;
            top: 0;
            z-index: 20;
        }

        .nav-left {
            display: flex;
            align-items: center;
            gap: 10px;
        }

        .nav-logo {
            width: 32px;
            height: 32px;
            border-radius: 10px;
            background: radial-gradient(circle at 20% 0,#4f46e5,#2563eb);
            display: flex;
            align-items: center;
            justify-content: center;
            color: white;
            font-weight: 700;
            font-size: 18px;
            box-shadow: 0 6px 16px rgba(37,99,235,.6);
        }

        .nav-title {
            font-weight: 600;
            letter-spacing: 0.03em;
            font-size: 18px;
        }

        .nav-sub {
            font-size: 11px;
            color: var(--text-muted);
        }

        .nav-right {
            display: flex;
            align-items: center;
            gap: 16px;
            font-size: 13px;
            color: var(--text-muted);
        }

        .nav-pill {
            padding: 6px 12px;
            border-radius: 9999px;
            background: var(--primary-soft);
            color: var(--primary);
            font-weight: 500;
        }

        .nav-avatar {
            width: 32px;
            height: 32px;
            border-radius: 9999px;
            background: linear-gradient(135deg,#22c55e,#16a3e5);
            display: flex;
            align-items: center;
            justify-content: center;
            color: white;
            font-size: 14px;
            font-weight: 600;
            box-shadow: 0 6px 16px rgba(15,118,110,.4);
        }

        /* Main wrapper */
        .wrapper {
            max-width: 1200px;
            margin: 24px auto 40px;
            padding: 0 24px 48px;
            width: 100%;
        }

        .page-header {
            display: flex;
            flex-wrap: wrap;
            align-items: flex-end;
            justify-content: space-between;
            gap: 16px;
            margin-bottom: 24px;
        }

        .page-header-text h1 {
            font-size: 26px;
            letter-spacing: 0.01em;
        }

        .page-header-text p {
            margin-top: 6px;
            color: var(--text-muted);
            font-size: 14px;
        }

        .tag-row {
            display: flex;
            align-items: center;
            gap: 8px;
            flex-wrap: wrap;
            margin-top: 10px;
        }

        .tag {
            padding: 4px 10px;
            border-radius: 9999px;
            border: 1px solid rgba(148,163,184,.6);
            background: rgba(255,255,255,.8);
            font-size: 11px;
            color: var(--text-muted);
        }

        .status-pill {
            padding: 5px 12px;
            border-radius: 9999px;
            background: rgba(22,163,74,.08);
            color: #15803d;
            font-size: 12px;
            font-weight: 500;
            border: 1px solid rgba(22,163,74,.3);
        }

        /* Cards grid */
        .card-grid {
            display: grid;
            grid-template-columns: repeat(3, minmax(0,1fr));
            gap: 18px;
        }

        @media (max-width: 960px) {
            .card-grid {
                grid-template-columns: repeat(2, minmax(0,1fr));
            }
        }

        @media (max-width: 640px) {
            .nav { padding: 12px 16px; }
            .wrapper { padding: 0 16px 32px; }
            .card-grid {
                grid-template-columns: minmax(0,1fr);
            }
        }

        .card {
            background: var(--card-bg);
            border-radius: var(--radius-lg);
            border: 1px solid var(--border);
            box-shadow: var(--shadow-soft);
            overflow: hidden;
            display: flex;
            flex-direction: column;
            transition: transform .18s ease, box-shadow .18s ease, border-color .18s ease;
            position: relative;
        }

        .card::before {
            content: "";
            position: absolute;
            inset: 0;
            border-radius: inherit;
            border: 1px solid transparent;
            background: linear-gradient(135deg,rgba(129,140,248,.45),rgba(59,130,246,.1),rgba(236,72,153,.25));
            opacity: 0;
            transition: opacity .22s ease;
            pointer-events: none;
        }

        .card:hover {
            transform: translateY(-4px);
            box-shadow: 0 18px 45px rgba(15,23,42,.18);
            border-color: rgba(59,130,246,.45);
        }

        .card:hover::before {
            opacity: 0.85;
        }

        .card-inner {
            position: relative;
            z-index: 1;
            display: flex;
            flex-direction: column;
            height: 100%;
        }

        .card-figure {
            position: relative;
            overflow: hidden;
        }

        .card-figure img {
            width: 100%;
            height: 160px;
            object-fit: cover;
            display: block;
            transition: transform .22s ease;
        }

        .card:hover .card-figure img {
            transform: scale(1.04);
        }

        .chip {
            position: absolute;
            left: 10px;
            bottom: 10px;
            padding: 4px 10px;
            border-radius: 9999px;
            font-size: 10px;
            background: rgba(15,23,42,.78);
            color: rgba(249,250,251,.95);
            display: inline-flex;
            align-items: center;
            gap: 4px;
        }

        .chip-dot {
            width: 7px;
            height: 7px;
            border-radius: 9999px;
            background: #22c55e;
            box-shadow: 0 0 0 3px rgba(34,197,94,.45);
        }

        .card-body {
            padding: 14px 14px 12px;
            display: flex;
            flex-direction: column;
            gap: 6px;
        }

        .card-title {
            font-size: 15px;
            font-weight: 600;
            letter-spacing: 0.01em;
        }

        .card-desc {
            font-size: 12px;
            color: var(--text-muted);
        }

        .card-meta {
            display: flex;
            justify-content: space-between;
            align-items: center;
            margin-top: 6px;
            font-size: 11px;
            color: var(--text-muted);
        }

        .card-meta span {
            display: inline-flex;
            align-items: center;
            gap: 5px;
        }

        .pill-small {
            padding: 3px 8px;
            border-radius: 9999px;
            border: 1px solid rgba(148,163,184,.6);
            background: rgba(248,250,252,.9);
        }

        .card-link {
            display: inline-flex;
            align-items: center;
            gap: 4px;
            color: var(--primary);
            font-weight: 500;
            text-decoration: none;
        }

        .card-link svg {
            width: 12px;
            height: 12px;
        }

        a.card-block {
            text-decoration: none;
            color: inherit;
        }

        footer {
            margin-top: auto;
            padding: 16px 24px 20px;
            font-size: 11px;
            color: var(--text-muted);
            text-align: center;
        }
    </style>
</head>
<body>

    <!-- Top bar -->
    <header class="nav">
        <div class="nav-left">
            <div class="nav-logo">OA</div>
            <div>
                <div class="nav-title">Operations Analytics</div>
                <div class="nav-sub">Internal performance dashboards</div>
            </div>
        </div>
        <div class="nav-right">
            <span class="nav-pill">Production · Live</span>
            <div class="nav-avatar">RK</div>
        </div>
    </header>

    <!-- Main content -->
    <main class="wrapper">
        <section class="page-header">
            <div class="page-header-text">
                <h1>Quick access to key reports</h1>
                <p>Launch Zoho Analytics dashboards from a single, reliable hub page.</p>
                <div class="tag-row">
                    <span class="tag">Zoho Analytics</span>
                    <span class="tag">Supply‑chain</span>
                    <span class="tag">Finance &amp; Billing</span>
                </div>
            </div>
            <span class="status-pill">SLA: 99.9% availability</span>
        </section>

        <!-- Cards grid -->
        <section class="card-grid">

            <!-- 1. Consumable Priority Action -->
            <a class="card card-block"
               href="https://analytics.zoho.com/workspace/3051221000000052001/view/3051221000000067031"
               target="_blank" rel="noopener noreferrer">
                <div class="card-inner">
                    <figure class="card-figure">
  <div
    style="
      width: 100%;
      height: 170px;
      display: flex;
      align-items: center;
      justify-content: center;
      text-align: center;
      padding: 0 16px;

      border-radius: 16px;
      background:
        radial-gradient(circle at 10% 0, #eef2ff 0, #dbeafe 40%, #bfdbfe 100%);
      box-shadow: 0 16px 40px rgba(15, 23, 42, 0.18);

      color: #0f172a;
      font-weight: 600;
      font-size: 18px;
      letter-spacing: 0.02em;
    "
  >
    Consumable Priority Action
  </div>

  <div class="chip">
    <span class="chip-dot"></span>
    Inventory focus
  </div>
</figure>


                    
                    <div class="card-body">
                        <div class="card-title">Consumable Priority Action</div>
                        <div class="card-desc">Identify critical consumable stock actions that need immediate attention.</div>
                        <div class="card-meta">
                            <span><span class="pill-small">Operations</span></span>
                            <span class="card-link">
                                Open report
                                <svg viewBox="0 0 20 20" fill="none">
                                    <path d="M6 14L14 6M9 6H14V11" stroke="currentColor" stroke-width="1.4" stroke-linecap="round" stroke-linejoin="round"/>
                                </svg>
                            </span>
                        </div>
                    </div>
                </div>
            </a>

            <!-- 2. Warehouse Material Movement -->
            <a class="card card-block"
               href="https://analytics.zoho.com/workspace/3051221000000052001/view/3051221000000309043"
               target="_blank" rel="noopener noreferrer">
                <div class="card-inner">
                    <figure class="card-figure">
  <div
    style="
      width: 100%;
      height: 170px;
      display: flex;
      align-items: center;
      justify-content: center;
      text-align: center;
      padding: 0 20px;

      border-radius: 16px;
      background:
        radial-gradient(circle at 10% 0, #eef2ff 0, #dbeafe 40%, #bfdbfe 100%);
      box-shadow: 0 16px 40px rgba(15, 23, 42, 0.18);

      color: #0f172a;
      font-weight: 600;
      font-size: 17px;
      line-height: 1.4;
      letter-spacing: 0.04em;
      text-transform: uppercase;
    "
  >
    Warehouse Material Movement Dashboard
  </div>

  <div class="chip">
    <span class="chip-dot"></span>
    Logistics &amp; Stock Flow
  </div>
</figure>

                    <div class="card-body">
                        <div class="card-title">Warehouse Material Movement</div>
                        <div class="card-desc">Monitor inbound and outbound material flows across warehouses.</div>
                        <div class="card-meta">
                            <span><span class="pill-small">Warehouse</span></span>
                            <span class="card-link">
                                Open report
                                <svg viewBox="0 0 20 20" fill="none">
                                    <path d="M6 14L14 6M9 6H14V11" stroke="currentColor" stroke-width="1.4" stroke-linecap="round" stroke-linejoin="round"/>
                                </svg>
                            </span>
                        </div>
                    </div>
                </div>
            </a>

            <!-- 3. Overdue Orders As On Date -->
            <a class="card card-block"
               href="https://analytics.zoho.com/workspace/3051221000000037359/view/3051221000000037396"
               target="_blank" rel="noopener noreferrer">
                <div class="card-inner">
                   <figure class="card-figure">
  <div
    style="
      width: 100%;
      height: 170px;
      display: flex;
      align-items: center;
      justify-content: center;
      text-align: center;
      padding: 0 20px;

      border-radius: 16px;
      background:
        radial-gradient(circle at 10% 0, #eef2ff 0, #dbeafe 40%, #bfdbfe 100%);
      box-shadow: 0 16px 40px rgba(15, 23, 42, 0.18);

      color: #0f172a;
      font-weight: 600;
      font-size: 17px;
      line-height: 1.4;
      letter-spacing: 0.04em;
      text-transform: uppercase;
    "
  >
    Overdue Orders As On Date
  </div>

  <div class="chip">
    <span class="chip-dot"></span>
    Risk Watch 
  </div>
</figure>
                    <div class="card-body">
                        <div class="card-title">Overdue Orders As On Date</div>
                        <div class="card-desc">Track customer orders that are past the promised delivery date.</div>
                        <div class="card-meta">
                            <span><span class="pill-small">Customer orders</span></span>
                            <span class="card-link">
                                Open report
                                <svg viewBox="0 0 20 20" fill="none">
                                    <path d="M6 14L14 6M9 6H14V11" stroke="currentColor" stroke-width="1.4" stroke-linecap="round" stroke-linejoin="round"/>
                                </svg>
                            </span>
                        </div>
                    </div>
                </div>
            </a>

            <!-- 4. OVL‑Purchases Snapshot YTD -->
            <a class="card card-block"
               href="https://analytics.zoho.com/workspace/3051221000000035001/view/3051221000000148047"
               target="_blank" rel="noopener noreferrer">
                <div class="card-inner">
                    <figure class="card-figure">
  <div
    style="
      width: 100%;
      height: 170px;
      display: flex;
      align-items: center;
      justify-content: center;
      text-align: center;
      padding: 0 20px;

      border-radius: 16px;
      background:
        radial-gradient(circle at 10% 0, #eef2ff 0, #dbeafe 40%, #bfdbfe 100%);
      box-shadow: 0 16px 40px rgba(15, 23, 42, 0.18);

      color: #0f172a;
      font-weight: 600;
      font-size: 17px;
      line-height: 1.4;
      letter-spacing: 0.04em;
      text-transform: uppercase;
    "
  >
   Overall Purchase Report
  </div>

  <div class="chip">
    <span class="chip-dot"></span>
   Spend View
  </div>
</figure>

                    <div class="card-body">
                        <div class="card-title">OVL‑Purchases Snapshot YTD</div>
                        <div class="card-desc">Year‑to‑date purchase trends and supplier performance at a glance.</div>
                        <div class="card-meta">
                            <span><span class="pill-small">Purchasing</span></span>
                            <span class="card-link">
                                Open report
                                <svg viewBox="0 0 20 20" fill="none">
                                    <path d="M6 14L14 6M9 6H14V11" stroke="currentColor" stroke-width="1.4" stroke-linecap="round" stroke-linejoin="round"/>
                                </svg>
                            </span>
                        </div>
                    </div>
                </div>
            </a>

            <!-- 5. Invoicing Status -->
            <a class="card card-block"
               href="https://analytics.zoho.com/workspace/3051221000000035463/view/3051221000000035510"
               target="_blank" rel="noopener noreferrer">
                <div class="card-inner">
                   <figure class="card-figure">
  <div
    style="
      width: 100%;
      height: 170px;
      display: flex;
      align-items: center;
      justify-content: center;
      text-align: center;
      padding: 0 20px;

      border-radius: 16px;
      background:
        radial-gradient(circle at 10% 0, #eef2ff 0, #dbeafe 40%, #bfdbfe 100%);
      box-shadow: 0 16px 40px rgba(15, 23, 42, 0.18);

      color: #0f172a;
      font-weight: 600;
      font-size: 17px;
      line-height: 1.4;
      letter-spacing: 0.04em;
      text-transform: uppercase;
    "
  >
    Invoicing Status
  </div>

  <div class="chip">
    <span class="chip-dot"></span>
   Billing Cycle
  </div>
</figure>
                    <div class="card-body">
                        <div class="card-title">Invoicing Status</div>
                        <div class="card-desc">Visualize pending, processed and disputed invoices in real time.</div>
                        <div class="card-meta">
                            <span><span class="pill-small">Finance</span></span>
                            <span class="card-link">
                                Open report
                                <svg viewBox="0 0 20 20" fill="none">
                                    <path d="M6 14L14 6M9 6H14V11" stroke="currentColor" stroke-width="1.4" stroke-linecap="round" stroke-linejoin="round"/>
                                </svg>
                            </span>
                        </div>
                    </div>
                </div>
            </a>

            <!-- 6. 1 Rupee JO YTD -->
            <a class="card card-block"
               href="https://analytics.zoho.com/workspace/3051221000000035001/view/3051221000000274050"
               target="_blank" rel="noopener noreferrer">
                <div class="card-inner">
                   <figure class="card-figure">
  <div
    style="
      width: 100%;
      height: 170px;
      display: flex;
      align-items: center;
      justify-content: center;
      text-align: center;
      padding: 0 20px;

      border-radius: 16px;
      background:
        radial-gradient(circle at 10% 0, #eef2ff 0, #dbeafe 40%, #bfdbfe 100%);
      box-shadow: 0 16px 40px rgba(15, 23, 42, 0.18);

      color: #0f172a;
      font-weight: 600;
      font-size: 17px;
      line-height: 1.4;
      letter-spacing: 0.04em;
      text-transform: uppercase;
    "
  >
   1 Rupee JO Report
  </div>

  <div class="chip">
    <span class="chip-dot"></span>
   Exception View
  </div>
</figure>

                    <div class="card-body">
                        <div class="card-title">1 Rupee JO YTD</div>
                        <div class="card-desc">Review 1‑rupee job orders and exceptions across the current year.</div>
                        <div class="card-meta">
                            <span><span class="pill-small">Audit</span></span>
                            <span class="card-link">
                                Open report
                                <svg viewBox="0 0 20 20" fill="none">
                                    <path d="M6 14L14 6M9 6H14V11" stroke="currentColor" stroke-width="1.4" stroke-linecap="round" stroke-linejoin="round"/>
                                </svg>
                            </span>
                        </div>
                    </div>
                </div>
            </a>

        </section>
    </main>

    <footer>
        &copy; <span id="year"></span> Operations Analytics · Internal use only
    </footer>

    <script>
        // Keep footer year current
        document.getElementById('year').textContent = new Date().getFullYear();
    </script>
</body>
</html>
