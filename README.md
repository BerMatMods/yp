
<html lang="es">
<head>
  <meta charset="UTF-8" />
  <meta name="viewport" content="width=device-width, initial-scale=1.0" />
  <meta name="description" content="NeonX Pro - App de Proxy Avanzada con Diseño 3D y Efectos RGB">
  <title>HttpX Pro v3.0 | BerMatMods</title>

  <!-- Google Fonts -->
  <link rel="preconnect" href="https://fonts.googleapis.com" />
  <link rel="preconnect" href="https://fonts.gstatic.com" crossorigin />
  <link href="https://fonts.googleapis.com/css2?family=Orbitron:wght@400;500;700&family=Exo+2:wght@400;500;600&family=Rajdhani:wght@500&family=Press+Start+2P&display=swap" rel="stylesheet" />

  <style>
    /* Variables Globales */
    :root {
      --bg: #0a0e17;
      --bg-card: #111827;
      --bg-deep: #0f172a;
      --text: #e0e7ff;
      --text-light: #94a3b8;
      --primary: #3b82f6;
      --primary-glow: #60a5fa;
      --secondary: #8b5cf6;
      --success: #10b981;
      --warning: #f59e0b;
      --danger: #ef4444;
      --accent: #06b6d4;
      --border: #334155;
      --font-main: 'Orbitron', sans-serif;
      --font-code: 'Exo 2', monospace;
      --font-title: 'Press Start 2P', cursive;
      --glow-primary: 0 0 15px rgba(59, 130, 246, 0.7);
      --glow-accent: 0 0 15px rgba(6, 182, 212, 0.7);
      --shadow-card: 0 10px 25px rgba(0, 0, 0, 0.3);
      --radius: 16px;
      --transition: all 0.4s cubic-bezier(0.25, 0.8, 0.25, 1);
    }

    .light-mode {
      --bg: #f1f5f9;
      --bg-card: #ffffff;
      --bg-deep: #e2e8f0;
      --text: #1e293b;
      --text-light: #64748b;
      --border: #cbd5e1;
      --glow-primary: 0 0 10px rgba(59, 130, 246, 0.4);
      --shadow-card: 0 5px 15px rgba(0, 0, 0, 0.1);
    }

    * {
      margin: 0;
      padding: 0;
      box-sizing: border-box;
    }

    body {
      font-family: var(--font-main);
      background: var(--bg);
      color: var(--text);
      transition: var(--transition);
      min-height: 100vh;
      overflow-x: hidden;
      perspective: 1000px;
    }

    /* Fondo con partículas animadas */
    .bg-particles {
      position: fixed;
      top: 0;
      left: 0;
      width: 100%;
      height: 100%;
      z-index: -3;
      overflow: hidden;
    }

    .particle {
      position: absolute;
      border-radius: 50%;
      opacity: 0.5;
      pointer-events: none;
      animation: float 15s infinite linear;
    }

    @keyframes float {
      0% { transform: translateY(0) rotate(0deg); opacity: 0; }
      10% { opacity: 0.7; }
      90% { opacity: 0.7; }
      100% { transform: translateY(-1000px) rotate(720deg); opacity: 0; }
    }

    /* Grid 3D fondo */
    .bg-grid {
      position: fixed;
      top: 0;
      left: 0;
      width: 100%;
      height: 100%;
      background: 
        linear-gradient(rgba(59, 130, 246, 0.05) 1px, transparent 1px),
        linear-gradient(90deg, rgba(59, 130, 246, 0.05) 1px, transparent 1px);
      background-size: 50px 50px;
      z-index: -2;
      transform: rotateX(60deg);
      pointer-events: none;
      opacity: 0.1;
    }

    /* Header con efecto 3D */
    .header {
      position: sticky;
      top: 0;
      display: flex;
      justify-content: space-between;
      align-items: center;
      padding: 1.2rem 1.5rem;
      background: rgba(15, 23, 42, 0.85);
      backdrop-filter: blur(12px);
      border-bottom: 1px solid var(--border);
      z-index: 10;
      transform: translateZ(50px);
      box-shadow: var(--shadow-card);
    }

    .logo {
      font-family: var(--font-title);
      font-size: 1.4rem;
      letter-spacing: 1px;
    }

    .neon-text {
      color: var(--primary);
      text-shadow: var(--glow-primary);
      animation: pulse 2s infinite alternate;
    }

    @keyframes pulse {
      0% { text-shadow: 0 0 5px #3b82f6; }
      100% { text-shadow: 0 0 20px #3b82f6, 0 0 30px #60a5fa; }
    }

    .version {
      font-size: 0.7rem;
      opacity: 0.7;
    }

    .btn-icon {
      background: none;
      border: none;
      font-size: 1.5rem;
      cursor: pointer;
      color: var(--text);
      transition: var(--transition);
    }

    .btn-icon:hover {
      transform: scale(1.1);
      color: var(--primary);
    }

    /* Sidebar 3D */
    .sidebar {
      position: fixed;
      top: 0;
      left: -300px;
      width: 280px;
      height: 100%;
      background: var(--bg-deep);
      border-right: 1px solid var(--border);
      z-index: 100;
      padding: 5rem 1rem 2rem;
      transform: translateZ(30px);
      box-shadow: 5px 0 20px rgba(0, 0, 0, 0.4);
      transition: left 0.5s cubic-bezier(0.68, -0.55, 0.26, 1.55);
    }

    .sidebar.open {
      left: 0;
    }

    .sidebar ul {
      list-style: none;
    }

    .sidebar li {
      margin: 1.2rem 0;
      transform: translateZ(20px);
    }

    .sidebar a {
      display: flex;
      align-items: center;
      gap: 0.8rem;
      color: var(--text);
      text-decoration: none;
      padding: 0.9rem 1.2rem;
      border-radius: var(--radius);
      transition: var(--transition);
      position: relative;
      overflow: hidden;
    }

    .sidebar a::before {
      content: '';
      position: absolute;
      top: 0;
      left: -100%;
      width: 100%;
      height: 100%;
      background: linear-gradient(90deg, transparent, rgba(59, 130, 246, 0.2), transparent);
      transition: 0.5s;
    }

    .sidebar a:hover::before {
      left: 100%;
    }

    .sidebar a:hover {
      background: var(--primary);
      color: white;
      transform: translateX(10px) scale(1.02);
    }

    .sidebar a.active {
      background: var(--primary);
      color: white;
      box-shadow: var(--glow-primary);
    }

    /* Main */
    .main-content {
      padding: 1.5rem;
      max-width: 900px;
      margin: 0 auto;
      transform: translateZ(20px);
    }

    .section {
      display: none;
      padding: 2rem;
      background: var(--bg-card);
      border-radius: var(--radius);
      margin-bottom: 1.5rem;
      box-shadow: var(--shadow-card);
      border: 1px solid var(--border);
      animation: slideUp 0.6s ease;
      transform: translateY(20px);
      opacity: 0;
    }

    .section.active {
      display: block;
      opacity: 1;
      transform: translateY(0);
    }

    @keyframes slideUp {
      from { opacity: 0; transform: translateY(20px); }
      to { opacity: 1; transform: translateY(0); }
    }

    h1, h2 {
      margin-bottom: 1.5rem;
      color: var(--primary);
      text-shadow: var(--glow-primary);
      font-weight: 600;
    }

    .form-group {
      margin-bottom: 1.2rem;
    }

    label {
      display: block;
      margin-bottom: 0.6rem;
      font-weight: 500;
      color: var(--text-light);
    }

    input, select, textarea {
      width: 100%;
      padding: 0.9rem;
      border: 1px solid var(--border);
      background: rgba(30, 41, 59, 0.5);
      color: var(--text);
      border-radius: 10px;
      font-family: var(--font-code);
      transition: var(--transition);
    }

    input:focus, select:focus, textarea:focus {
      outline: none;
      border-color: var(--primary);
      box-shadow: var(--glow-primary);
      background: rgba(30, 41, 59, 0.8);
    }

    /* Botones */
    .btn {
      padding: 0.8rem 1.5rem;
      border: none;
      border-radius: 10px;
      cursor: pointer;
      font-weight: 600;
      transition: var(--transition);
      margin-right: 0.5rem;
      margin-bottom: 0.5rem;
    }

    .btn-primary {
      background: var(--primary);
      color: white;
    }

    .btn-secondary {
      background: var(--secondary);
      color: white;
    }

    .btn-success {
      background: var(--success);
      color: white;
    }

    .btn-danger {
      background: var(--danger);
      color: white;
    }

    .btn:hover {
      transform: translateY(-3px);
      box-shadow: 0 5px 15px rgba(0, 0, 0, 0.2);
    }

    .btn:active {
      transform: translateY(0);
    }

    /* Switch */
    .switch {
      position: relative;
      display: inline-block;
      width: 60px;
      height: 30px;
    }

    .switch input {
      opacity: 0;
      width: 0;
      height: 0;
    }

    .slider {
      position: absolute;
      cursor: pointer;
      top: 0;
      left: 0;
      right: 0;
      bottom: 0;
      background-color: #ccc;
      transition: .4s;
      border-radius: 30px;
    }

    .slider:before {
      position: absolute;
      content: "";
      height: 24px;
      width: 24px;
      left: 4px;
      bottom: 3px;
      background-color: white;
      transition: .4s;
      border-radius: 50%;
    }

    input:checked + .slider {
      background: linear-gradient(90deg, #10b981, #06b6d4);
    }

    input:checked + .slider:before {
      transform: translateX(30px);
    }

    /* Cards de estado */
    .status-card {
      background: rgba(15, 23, 42, 0.5);
      border: 1px solid var(--border);
      border-radius: var(--radius);
      padding: 1.2rem;
      margin-bottom: 1rem;
      text-align: center;
      box-shadow: 0 5px 15px rgba(0, 0, 0, 0.2);
    }

    .status-value {
      font-size: 1.8rem;
      font-weight: 700;
      color: var(--accent);
      text-shadow: var(--glow-accent);
    }

    /* Gráfico de red */
    .network-graph {
      width: 100%;
      height: 120px;
      background: rgba(15, 23, 42, 0.4);
      border-radius: 10px;
      margin: 1rem 0;
      position: relative;
      overflow: hidden;
    }

    .graph-line {
      position: absolute;
      bottom: 50%;
      left: 0;
      width: 100%;
      height: 2px;
      background: var(--text-light);
    }

    .graph-pulse {
      position: absolute;
      width: 4px;
      height: 4px;
      background: var(--success);
      border-radius: 50%;
      animation: pulseGraph 2s infinite;
    }

    @keyframes pulseGraph {
      0% { transform: scaleY(1); opacity: 0.5; }
      50% { transform: scaleY(5); opacity: 1; }
      100% { transform: scaleY(1); opacity: 0.5; }
    }

    /* Perfiles */
    .profile-item {
      background: rgba(30, 41, 59, 0.6);
      padding: 1rem;
      border-radius: 12px;
      margin-bottom: 0.8rem;
      border-left: 4px solid var(--primary);
      display: flex;
      justify-content: space-between;
      align-items: center;
      transition: var(--transition);
    }

    .profile-item:hover {
      transform: scale(1.02);
      background: rgba(59, 130, 246, 0.1);
    }

    /* Responsive */
    @media (max-width: 600px) {
      .header { padding: 1rem; }
      .main-content { padding: 1rem; }
      .section { padding: 1.2rem; }
      h1, h2 { font-size: 1.4rem; }
    }

    /* Animaciones RGB */
    .rgb-glow {
      animation: rgbPulse 3s ease infinite;
    }

    @keyframes rgbPulse {
      0% { box-shadow: 0 0 15px #3b82f6; }
      25% { box-shadow: 0 0 15px #8b5cf6; }
      50% { box-shadow: 0 0 15px #06b6d4; }
      75% { box-shadow: 0 0 15px #10b981; }
      100% { box-shadow: 0 0 15px #ef4444; }
    }

    /* Iconos SVG animados */
    .animated-icon {
      transition: transform 0.3s;
    }

    .animated-icon:hover {
      transform: rotate(180deg) scale(1.2);
    }
  </style>
</head>
<body class="dark-mode">

  <!-- Fondo de partículas -->
  <div class="bg-particles" id="particles"></div>
  <div class="bg-grid"></div>

  <!-- Header -->
  <header class="header">
    <div class="logo">
      <span class="neon-text">NEONX</span> <span class="version">PRO v3.0</span>
    </div>
    <button id="theme-toggle" class="btn-icon">🌙</button>
    <button id="menu-toggle" class="btn-icon">☰</button>
  </header>

  <!-- Sidebar -->
  <nav id="sidebar" class="sidebar">
    <ul>
      <li><a href="#home" class="active"><i class="animated-icon">🏠</i> Inicio</a></li>
      <li><a href="#tunnel"><i class="animated-icon">⚡</i> Túnel HTTP</a></li>
      <li><a href="#socks"><i class="animated-icon">🔐</i> SOCKS5</a></li>
      <li><a href="#pac"><i class="animated-icon">🌐</i> PAC & DNS</a></li>
      <li><a href="#profiles"><i class="animated-icon">💾</i> Perfiles</a></li>
      <li><a href="#logs"><i class="animated-icon">📜</i> Logs</a></li>
      <li><a href="#settings"><i class="animated-icon">⚙️</i> Ajustes</a></li>
      <li><a href="#about"><i class="animated-icon">ℹ️</i> Acerca de</a></li>
    </ul>
  </nav>

  <!-- Contenido -->
  <main class="main-content">

    <!-- Inicio -->
    <section id="home" class="section active">
      <h1>Bienvenido a <span class="neon-text">NeonX Pro</span></h1>
      <p>La app de proxy más avanzada con diseño futurista 3D, efectos RGB y soporte total para móviles.</p>
      
      <div class="status-card">
        <div>Estado de Conexión</div>
        <div class="status-value">✅ Conectado</div>
      </div>

      <div class="status-card">
        <div>Velocidad</div>
        <div class="status-value">12.4 Mbps</div>
      </div>

      <div class="network-graph">
        <div class="graph-line"></div>
        <div class="graph-pulse" style="left: 10%; animation-delay: 0s;"></div>
        <div class="graph-pulse" style="left: 30%; animation-delay: 0.5s;"></div>
        <div class="graph-pulse" style="left: 60%; animation-delay: 1s;"></div>
        <div class="graph-pulse" style="left: 80%; animation-delay: 1.5s;"></div>
      </div>

      <button class="btn btn-primary rgb-glow">Iniciar Conexión</button>
    </section>

    <!-- Túnel HTTP -->
    <section id="tunnel" class="section">
      <h2>Túnel HTTP Avanzado</h2>
      <div class="form-group">
        <label>Host (Proxy)</label>
        <input type="text" id="http-host" placeholder="103.10.23.10" />
      </div>
      <div class="form-group">
        <label>Puerto</label>
        <input type="number" id="http-port" placeholder="8080" />
      </div>
      <div class="form-group">
        <label>Método de Inyección</label>
        <select id="http-method">
          <option>GET / HTTP/1.1</option>
          <option>CONNECT</option>
          <option>POST</option>
          <option>PROXY</option>
        </select>
      </div>
      <div class="form-group">
        <label>Host Header</label>
        <input type="text" id="http-header" placeholder="X-Online-Host: google.com" />
      </div>
      <div class="form-group">
        <label>Extra Headers (uno por línea)</label>
        <textarea id="extra-headers" rows="3" placeholder="User-Agent: Mozilla/5.0...&#10;Connection: keep-alive"></textarea>
      </div>
      <button class="btn btn-primary" onclick="saveHttpConfig()">Guardar</button>
    </section>

    <!-- SOCKS5 -->
    <section id="socks" class="section">
      <h2>Configuración SOCKS5</h2>
      <div class="form-group">
        <label>IP del Servidor</label>
        <input type="text" id="socks-ip" placeholder="192.168.1.1" />
      </div>
      <div class="form-group">
        <label>Puerto</label>
        <input type="number" id="socks-port" placeholder="1080" />
      </div>
      <div class="form-group">
        <label>Autenticación</label>
        <label class="switch">
          <input type="checkbox" id="socks-auth" />
          <span class="slider"></span>
        </label>
      </div>
      <div class="form-group" id="socks-auth-fields" style="display:none;">
        <input type="text" id="socks-user" placeholder="Usuario" />
        <input type="password" id="socks-pass" placeholder="Contraseña" />
      </div>
      <button class="btn btn-primary" onclick="saveSocksConfig()">Conectar</button>
    </section>

    <!-- PAC & DNS -->
    <section id="pac" class="section">
      <h2>PAC & DNS Personalizado</h2>
      <div class="form-group">
        <label>DNS (separados por coma)</label>
        <input type="text" id="custom-dns" placeholder="8.8.8.8, 1.1.1.1, 9.9.9.9" />
      </div>
      <div class="form-group">
        <label>URL del PAC</label>
        <input type="url" id="pac-url" placeholder="http://tudominio.com/proxy.pac" />
      </div>
      <div class="form-group">
        <label>Reglas de Exclusión (ej: *.local)</label>
        <input type="text" id="pac-exclude" placeholder="*.local, 192.168.*" />
      </div>
      <button class="btn btn-primary" onclick="savePacConfig()">Guardar</button>
    </section>

    <!-- Perfiles -->
    <section id="profiles" class="section">
      <h2>Perfiles Guardados</h2>
      <div class="profile-list" id="profile-list"></div>
      <button class="btn btn-secondary" onclick="exportProfiles()">📤 Exportar</button>
      <label class="btn btn-primary">
        📥 Importar
        <input type="file" id="import-file" accept=".json" onchange="importProfiles()" style="display:none;">
      </label>
    </section>

    <!-- Logs -->
    <section id="logs" class="section">
      <h2>Logs de Conexión</h2>
      <div class="form-group">
        <textarea id="logs-output" rows="8" readonly placeholder="Iniciando..."></textarea>
      </div>
      <button class="btn btn-success" onclick="simulateLog()">Generar Log</button>
      <button class="btn btn-danger" onclick="clearLogs()">Limpiar</button>
    </section>

    <!-- Ajustes -->
    <section id="settings" class="section">
      <h2>Ajustes Avanzados</h2>
      <div class="form-group">
        <label>Modo Oscuro</label>
        <label class="switch">
          <input type="checkbox" id="dark-mode-toggle" checked>
          <span class="slider"></span>
        </label>
      </div>
      <div class="form-group">
        <label>Efectos RGB</label>
        <label class="switch">
          <input type="checkbox" id="rgb-toggle" checked>
          <span class="slider"></span>
        </label>
      </div>
      <div class="form-group">
        <label>Fuente</label>
        <select id="font-select">
          <option value="Orbitron">Orbitron</option>
          <option value="Exo 2">Exo 2</option>
          <option value="Rajdhani">Rajdhani</option>
        </select>
      </div>
      <div class="form-group">
        <label>Animaciones</label>
        <label class="switch">
          <input type="checkbox" id="anim-toggle" checked>
          <span class="slider"></span>
        </label>
      </div>
      <button class="btn btn-danger" onclick="resetApp()">Restablecer Todo</button>
    </section>

    <!-- Acerca de -->
    <section id="about" class="section">
      <h2>Acerca de NeonX Pro</h2>
      <p><strong>Desarrollado por:</strong> AnthZz Berrocal - BerMatMods</p>
      <p><strong>Versión:</strong> 3.0.0</p>
      <p><strong>Plataforma:</strong> Web (móvil-first)</p>
      <p><strong>Compatibilidad:</strong> 100% con GitHub Pages</p>
      <p><strong>Licencia:</strong> Open Source (MIT)</p>
      <p style="margin-top: 1rem; font-size: 0.9rem; opacity: 0.8;">
        Esta app es solo frontend. No almacena datos sensibles.
      </p>
    </section>

  </main>

  <script>
    // Variables
    let profiles = JSON.parse(localStorage.getItem('neonx-profiles')) || [];
    let logCounter = 0;

    // Generar partículas
    function createParticles() {
      const container = document.getElementById('particles');
      for (let i = 0; i < 50; i++) {
        const p = document.createElement('div');
        p.classList.add('particle');
        p.style.width = Math.random() * 10 + 'px';
        p.style.height = p.style.width;
        p.style.backgroundColor = ['#3b82f6', '#8b5cf6', '#06b6d4', '#10b981'][Math.floor(Math.random() * 4)];
        p.style.left = Math.random() * 100 + 'vw';
        p.style.top = Math.random() * 100 + 'vh';
        p.style.animationDuration = Math.random() * 20 + 10 + 's';
        p.style.animationDelay = Math.random() * 5 + 's';
        container.appendChild(p);
      }
    }

    // Cargar preferencias
    function loadPreferences() {
      const darkMode = localStorage.getItem('darkMode') !== 'false';
      const rgbEnabled = localStorage.getItem('rgbEnabled') !== 'false';
      const font = localStorage.getItem('font') || 'Orbitron';
      const animEnabled = localStorage.getItem('animEnabled') !== 'false';

      document.body.classList.toggle('dark-mode', darkMode);
      document.getElementById('theme-toggle').textContent = darkMode ? '🌙' : '☀️';
      document.getElementById('dark-mode-toggle').checked = darkMode;
      document.getElementById('rgb-toggle').checked = rgbEnabled;
      document.getElementById('anim-toggle').checked = animEnabled;
      document.getElementById('font-select').value = font;
      document.body.style.setProperty('--font-main', `${font}, sans-serif`);
      if (rgbEnabled) document.body.classList.add('rgb-glow');

      loadProfiles();
      createParticles();
    }

    // Toggle theme
    document.getElementById('theme-toggle').addEventListener('click', toggleTheme);
    function toggleTheme() {
      const isDark = !document.body.classList.contains('dark-mode');
      document.body.classList.toggle('dark-mode', isDark);
      document.getElementById('theme-toggle').textContent = isDark ? '🌙' : '☀️';
      document.getElementById('dark-mode-toggle').checked = isDark;
      localStorage.setItem('darkMode', isDark);
    }

    // Menú
    document.getElementById('menu-toggle').addEventListener('click', () => {
      document.getElementById('sidebar').classList.toggle('open');
    });

    // Navegación
    document.querySelectorAll('.sidebar a').forEach(link => {
      link.addEventListener('click', (e) => {
        e.preventDefault();
        const target = link.getAttribute('href').slice(1);
        showSection(target);
        document.getElementById('sidebar').classList.remove('open');
      });
    });

    function showSection(id) {
      document.querySelectorAll('.section').forEach(s => s.classList.remove('active'));
      document.getElementById(id).classList.add('active');
      document.querySelectorAll('.sidebar a').forEach(a => a.classList.remove('active'));
      document.querySelector(`.sidebar a[href="#${id}"]`).classList.add('active');
    }

    // Efectos RGB
    document.getElementById('rgb-toggle').addEventListener('change', function () {
      document.body.classList.toggle('rgb-glow', this.checked);
      localStorage.setItem('rgbEnabled', this.checked);
    });

    // Fuente
    document.getElementById('font-select').addEventListener('change', function () {
      document.body.style.setProperty('--font-main', `${this.value}, sans-serif`);
      localStorage.setItem('font', this.value);
    });

    // Animaciones
    document.getElementById('anim-toggle').addEventListener('change', function () {
      document.body.style.setProperty('--transition', this.checked ? 'all 0.4s cubic-bezier(0.25, 0.8, 0.25, 1)' : 'none');
      localStorage.setItem('animEnabled', this.checked);
    });

    // SOCKS auth
    document.getElementById('socks-auth').addEventListener('change', function () {
      document.getElementById('socks-auth-fields').style.display = this.checked ? 'block' : 'none';
    });

    // Guardar configs
    function saveHttpConfig() {
      const config = {
        type: 'HTTP', host: i('http-host'), port: i('http-port'),
        method: i('http-method'), header: i('http-header'), date: timestamp()
      };
      profiles.push(config);
      saveProfiles();
      alert('✅ Config HTTP guardada');
    }

    function saveSocksConfig() {
      const auth = document.getElementById('socks-auth').checked;
      const config = {
        type: 'SOCKS5', ip: i('socks-ip'), port: i('socks-port'), auth,
        user: auth ? i('socks-user') : '', pass: auth ? i('socks-pass') : '',
        date: timestamp()
      };
      profiles.push(config);
      saveProfiles();
      alert('✅ SOCKS guardado');
    }

    function savePacConfig() {
      const config = {
        type: 'PAC/DNS', dns: i('custom-dns'), pac: i('pac-url'),
        exclude: i('pac-exclude'), date: timestamp()
      };
      profiles.push(config);
      saveProfiles();
      alert('✅ PAC/DNS guardado');
    }

    function i(id) { return document.getElementById(id).value; }
    function timestamp() { return new Date().toLocaleString(); }

    // Perfiles
    function saveProfiles() {
      localStorage.setItem('neonx-profiles', JSON.stringify(profiles));
      loadProfiles();
    }

    function loadProfiles() {
      const list = document.getElementById('profile-list');
      list.innerHTML = '';
      profiles.slice(-10).reverse().forEach((p, i) => {
        const item = document.createElement('div');
        item.className = 'profile-item';
        item.innerHTML = `
          <div>
            <strong>${p.type}</strong> | ${p.date}
            <div style="font-size:0.8rem; opacity:0.7;">${shortConfig(p)}</div>
          </div>
          <button class="btn btn-danger" onclick="deleteProfile(${profiles.length - 1 - i})">🗑️</button>
        `;
        list.appendChild(item);
      });
    }

    function shortConfig(p) {
      if (p.type === 'HTTP') return `${p.host}:${p.port} | ${p.method}`;
      if (p.type === 'SOCKS5') return `${p.ip}:${p.port}`;
      return p.dns || 'PAC';
    }

    function deleteProfile(index) {
      profiles.splice(index, 1);
      saveProfiles();
    }

    // Logs
    function simulateLog() {
      const logs = document.getElementById('logs-output');
      const entries = [
        `[${timestamp()}] Conexión iniciada...`,
        `[${timestamp()}] Resolviendo DNS... OK`,
        `[${timestamp()}] Conectado al proxy: ${Math.random().toFixed(3) * 100}ms`,
        `[${timestamp()}] Tráfico encriptado activado`,
        `[${timestamp()}] Navegación segura`
      ];
      logs.value += entries.join('\n') + '\n';
      logs.scrollTop = logs.scrollHeight;
    }

    function clearLogs() {
      document.getElementById('logs-output').value = '';
    }

    // Importar/Exportar
    function exportProfiles() {
      const dataStr = "data:text/json;charset=utf-8," + encodeURIComponent(JSON.stringify(profiles, null, 2));
      const a = document.createElement('a');
      a.href = dataStr;
      a.download = "neonx_profiles.json";
      document.body.appendChild(a);
      a.click();
      document.body.removeChild(a);
    }

    function importProfiles() {
      const file = document.getElementById('import-file').files[0];
      if (!file) return;
      const r = new FileReader();
      r.onload = e => {
        try {
          const imported = JSON.parse(e.target.result);
          profiles = profiles.concat(imported);
          saveProfiles();
          alert('✅ Perfiles importados');
        } catch (err) {
          alert('❌ Error al importar');
        }
      };
      r.readAsText(file);
    }

    // Reset
    function resetApp() {
      if (confirm('¿Restablecer toda la app?')) {
        localStorage.clear();
        profiles = [];
        location.reload();
      }
    }

    // Inicializar
    loadPreferences();
    showSection('home');
  </script>
</body>
</html>
