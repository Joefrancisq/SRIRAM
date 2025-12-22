# SRIRAM

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
          <span class="meta-pill"></span>
          <span class="meta-pill">Password IN </span>
          <span class="meta-pill">Environment: Production</span>
        </div>

        <div class="preview">
          <div>
            <div class="preview-title">Password pattern</div>
            <p>
              Let's Guess out the pattern
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
              placeholder="Enter Password"
            />
          </div>
          <div class="hint">
            Hi Sriram
          </div>
        </div>

        <div id="error" class="error"></div>
        <div id="success" class="success"></div>

        <button type="submit">Authenticate</button>

        <div id="dashboardLink" class="dashboard-link">
          Login successful.  
          <a href="Dashboard.html">
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

