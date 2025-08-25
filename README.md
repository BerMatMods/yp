
<html lang="es">
<head>
  <meta charset="UTF-8" />
  <meta name="viewport" content="width=device-width, initial-scale=1.0" />
  <title>NeonX Proxy</title>
  <link rel="preconnect" href="https://fonts.googleapis.com" />
  <link rel="preconnect" href="https://fonts.gstatic.com" crossorigin />
  <link href="https://fonts.googleapis.com/css2?family=Orbitron:wght@400;500;700&family=Exo+2&family=Rajdhani:wght@500&display=swap" rel="stylesheet" />
  <style>
    /* Variables */
    :root {
      --bg: #0f172a;
      --text: #e2e8f0;
      --primary: #0ea5e9;
      --secondary: #8b5cf6;
      --accent: #10b981;
      --card: #1e293b;
      --border: #334155;
      --font-main: 'Orbitron', sans-serif;
      --glow: 0 0 10px rgba(14, 165, 233, 0.6);
    }

    .light-mode {
      --bg: #f8fafc;
      --text: #1e293b;
      --card: #ffffff;
      --border: #e2e8f0;
      --glow: 0 0 10px rgba(14, 165, 233, 0.4);
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
      transition: background 0.5s ease, color 0.5s ease;
      min-height: 100vh;
      position: relative;
      overflow-x: hidden;
    }

    /* Fondo animado con partículas */
    .bg-animation {
      position: fixed;
      top: 0;
      left: 0;
      width: 100%;
      height: 100%;
      background: linear-gradient(125deg, #0f172a, #1e1b4b, #1e293b);
      z-index: -2;
      opacity: 0.3;
    }

    .bg-animation::before {
      content: '';
      position: absolute;
      top: -50%;
      left: -50%;
      width: 200%;
      height: 200%;
      background: radial-gradient(circle, transparent 20%, var(--bg) 20%, var(--bg) 80%, transparent 80%, transparent), 
                  radial-gradient(circle, transparent 20%, var(--bg) 20%, var(--bg) 80%, transparent 80%, transparent) 50px 50px,
                  linear-gradient(var(--primary) 1px, transparent 1px) 0 -1px,
                  linear-gradient(90deg, var(--primary) 1px, var(--bg) 1px);
      background-size: 100px 100px, 100px 100px, 50px 50px, 50px 50px;
      background-position: 0 0, 25px 25px;
      animation: pan 10s linear infinite;
      z-index: -1;
      opacity: 0.1;
    }

    @keyframes pan {
      0% { transform: translateY(0) translateX(0); }
      100% { transform: translateY(50px) translateX(50px); }
    }

    /* Header */
    .header {
      display: flex;
      justify-content: space-between;
      align-items: center;
      padding: 1rem 1.5rem;
      background: rgba(15, 23, 42, 0.8);
      backdrop-filter: blur(10px);
      position: sticky;
      top: 0;
      z-index: 10;
      border-bottom: 1px solid var(--border);
    }

    .logo {
      font-size: 1.5rem;
      font-weight: 700;
    }

    .neon-text {
      color: var(--primary);
      text-shadow: var(--glow);
    }

    .version {
      font-size: 0.8rem;
      opacity: 0.7;
    }

    .btn-icon {
      background: none;
      border: none;
      font-size: 1.5rem;
      cursor: pointer;
      color: var(--text);
    }

    /* Sidebar */
    .sidebar {
      position: fixed;
      top: 0;
      left: -280px;
      width: 280px;
      height: 100%;
      background: var(--card);
      box-shadow: 5px 0 15px rgba(0,0,0,0.3);
      transition: left 0.4s ease;
      z-index: 100;
      padding: 3rem 1rem 1rem;
      border-right: 1px solid var(--border);
    }

    .sidebar.open {
      left: 0;
    }

    .sidebar ul {
      list-style: none;
    }

    .sidebar li {
      margin: 1rem 0;
    }

    .sidebar a {
      display: flex;
      align-items: center;
      gap: 0.8rem;
      color: var(--text);
      text-decoration: none;
      padding: 0.8rem 1rem;
      border-radius: 8px;
      transition: background 0.3s;
    }

    .sidebar a:hover, .sidebar a.active {
      background: var(--primary);
      color: white;
    }

    /* Main */
    .main-content {
      padding: 1rem;
      max-width: 800px;
      margin: 0 auto;
    }

    .section {
      display: none;
      padding: 1.5rem;
      background: var(--card);
      border-radius: 12px;
      margin-bottom: 1rem;
      box-shadow: 0 4px 10px rgba(0,0,0,0.1);
      animation: fadeIn 0.5s ease;
    }

    .section.active {
      display: block;
    }

    @keyframes fadeIn {
      from { opacity: 0; transform: translateY(10px); }
      to { opacity: 1; transform: translateY(0); }
    }

    h1, h2 {
      margin-bottom: 1rem;
      color: var(--primary);
    }

    .form-group {
      margin-bottom: 1rem;
    }

    label {
      display: block;
      margin-bottom: 0.5rem;
      font-weight: 500;
    }

    input, select, textarea {
      width: 100%;
      padding: 0.8rem;
      border: 1px solid var(--border);
      background: var(--bg);
      color: var(--text);
      border-radius: 8px;
      font-family: var(--font-main);
    }

    input:focus, select:focus, textarea:focus {
      outline: none;
      border-color: var(--primary);
      box-shadow: var(--glow);
    }

    .btn-primary {
      background: var(--primary);
      color: white;
      border: none;
      padding: 0.8rem 1.5rem;
      border-radius: 8px;
      cursor: pointer;
      font-weight: 600;
      transition: transform 0.2s;
    }

    .btn-primary:hover {
      transform: translateY(-2px);
      box-shadow: var(--glow);
    }

    .btn-secondary {
      background: var(--secondary);
      color: white;
      border: none;
      padding: 0.8rem 1.5rem;
      border-radius: 8px;
      cursor: pointer;
      margin-right: 0.5rem;
    }

    .btn-danger {
      background: #ef4444;
    }

    /* Switch toggle */
    .switch {
      position: relative;
      display: inline-block;
      width: 50px;
      height: 24px;
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
      border-radius: 24px;
    }

    .slider:before {
      position: absolute;
      content: "";
      height: 18px;
      width: 18px;
      left: 4px;
      bottom: 3px;
      background-color: white;
      transition: .4s;
      border-radius: 50%;
    }

    input:checked + .slider {
      background-color: var(--accent);
    }

    input:checked + .slider:before {
      transform: translateX(26px);
    }

    /* Perfiles */
    .profile-list {
      margin: 1rem 0;
    }

    .profile-item {
      display: flex;
      justify-content: space-between;
      background: var(--bg);
      padding: 0.8rem;
      border-radius: 8px;
      margin-bottom: 0.5rem;
    }

    /* Responsive */
    @media (max-width: 600px) {
      .header {
        padding: 1rem;
      }
      .main-content {
        padding: 0.5rem;
      }
      .section {
        padding: 1rem;
      }
    }

    /* RGB Glow dinámico */
    .rgb-glow {
      animation: rgbPulse 2.5s ease infinite;
    }

    @keyframes rgbPulse {
      0% { box-shadow: 0 0 10px #0ea5e9; }
      25% { box-shadow: 0 0 10px #8b5cf6; }
      50% { box-shadow: 0 0 10px #10b981; }
      75% { box-shadow: 0 0 10px #f59e0b; }
      100% { box-shadow: 0 0 10px #ef4444; }
    }
  </style>
</head>
<body class="dark-mode">

  <!-- Fondo animado -->
  <div class="bg-animation"></div>

  <!-- Header -->
  <header class="header">
    <div class="logo">
      <span class="neon-text">NeonX</span> <span class="version">v2.1</span>
    </div>
    <button id="theme-toggle" class="btn-icon">🌙</button>
    <button id="menu-toggle" class="btn-icon">☰</button>
  </header>

  <!-- Menú lateral -->
  <nav id="sidebar" class="sidebar">
    <ul>
      <li><a href="#home" class="active"><i>🏠</i> Inicio</a></li>
      <li><a href="#tunnel"><i>⚡</i> Túnel HTTP</a></li>
      <li><a href="#socks"><i>🔐</i> SOCKS5</a></li>
      <li><a href="#pac"><i>🌐</i> PAC & DNS</a></li>
      <li><a href="#profiles"><i>💾</i> Perfiles</a></li>
      <li><a href="#settings"><i>⚙️</i> Ajustes</a></li>
      <li><a href="#about"><i>ℹ️</i> Acerca de</a></li>
    </ul>
  </nav>

  <!-- Contenido principal -->
  <main class="main-content">

    <!-- Inicio -->
    <section id="home" class="section active">
      <h1>Bienvenido a <span class="neon-text">NeonX</span></h1>
      <p>Configura túneles HTTP y SOCKS con estilo futurista. Compatible con móviles y GitHub Pages.</p>
      <button class="btn-primary rgb-glow">Iniciar Conexión</button>
    </section>

    <!-- Túnel HTTP -->
    <section id="tunnel" class="section">
      <h2>Túnel HTTP Personalizado</h2>
      <div class="form-group">
        <label>Host (Proxy)</label>
        <input type="text" id="http-host" placeholder="ej: 103.10.23.10" />
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
        </select>
      </div>
      <div class="form-group">
        <label>Header Extra (opcional)</label>
        <input type="text" id="http-header" placeholder="X-Online-Host: google.com" />
      </div>
      <button class="btn-primary" onclick="saveHttpConfig()">Guardar Config</button>
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
      <div class="toggle-group">
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
      <button class="btn-primary" onclick="saveSocksConfig()">Conectar</button>
    </section>

    <!-- PAC & DNS -->
    <section id="pac" class="section">
      <h2>PAC & DNS Personalizado</h2>
      <div class="form-group">
        <label>DNS Personalizado</label>
        <input type="text" id="custom-dns" placeholder="8.8.8.8, 1.1.1.1" />
      </div>
      <div class="form-group">
        <label>URL del PAC (Proxy Auto-Config)</label>
        <input type="url" id="pac-url" placeholder="http://ejemplo.com/proxy.pac" />
      </div>
      <button class="btn-primary" onclick="savePacConfig()">Guardar</button>
    </section>

    <!-- Perfiles -->
    <section id="profiles" class="section">
      <h2>Perfiles Guardados</h2>
      <div class="profile-list" id="profile-list">
        <!-- Perfiles generados dinámicamente -->
      </div>
      <button class="btn-secondary" onclick="exportProfiles()">Exportar (.json)</button>
      <label class="btn-primary" style="display:inline-block;">
        Importar
        <input type="file" id="import-file" accept=".json" onchange="importProfiles()" style="display:none;" />
      </label>
    </section>

    <!-- Ajustes -->
    <section id="settings" class="section">
      <h2>Ajustes Avanzados</h2>
      <div class="setting-item">
        <label>Modo Oscuro</label>
        <label class="switch">
          <input type="checkbox" id="dark-mode-toggle" checked />
          <span class="slider"></span>
        </label>
      </div>
      <div class="setting-item">
        <label>Efectos RGB</label>
        <label class="switch">
          <input type="checkbox" id="rgb-toggle" checked />
          <span class="slider"></span>
        </label>
      </div>
      <div class="setting-item">
        <label>Fuente</label>
        <select id="font-select">
          <option value="Orbitron">Orbitron</option>
          <option value="Exo 2">Exo 2</option>
          <option value="Rajdhani">Rajdhani</option>
        </select>
      </div>
      <button class="btn-danger btn-primary" onclick="resetApp()">Restablecer Todo</button>
    </section>

    <!-- Acerca de -->
    <section id="about" class="section">
      <h2>Acerca de NeonX</h2>
      <p>Desarrollado por <strong>AnthZz Berrocal - BerMatMods</strong></p>
      <p>Versión: 2.1.0</p>
      <p>✅ Compatible con GitHub Pages</p>
      <p>🔧 Sin backend, 100% frontend</p>
    </section>

  </main>

  <script>
    // Datos de configuración
    let profiles = JSON.parse(localStorage.getItem('neonx-profiles')) || [];

    // Cargar preferencias
    function loadPreferences() {
      const darkMode = localStorage.getItem('darkMode') !== 'false';
      const rgbEnabled = localStorage.getItem('rgbEnabled') !== 'false';
      const font = localStorage.getItem('font') || 'Orbitron';

      if (!darkMode) document.body.classList.remove('dark-mode');
      document.getElementById('theme-toggle').textContent = darkMode ? '🌙' : '☀️';
      document.getElementById('dark-mode-toggle').checked = darkMode;
      document.getElementById('rgb-toggle').checked = rgbEnabled;
      document.getElementById('font-select').value = font;
      document.body.style.setProperty('--font-main', `${font}, sans-serif`);
      if (rgbEnabled) document.body.classList.add('rgb-glow');

      loadProfiles();
    }

    // Alternar tema
    function toggleTheme() {
      const isDark = !document.body.classList.contains('dark-mode');
      document.body.classList.toggle('dark-mode', isDark);
      document.getElementById('theme-toggle').textContent = isDark ? '🌙' : '☀️';
      document.getElementById('dark-mode-toggle').checked = isDark;
      localStorage.setItem('darkMode', isDark);
    }

    // Menú
    document.getElementById('theme-toggle').addEventListener('click', toggleTheme);
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
      if (this.checked) {
        document.body.classList.add('rgb-glow');
      } else {
        document.body.classList.remove('rgb-glow');
      }
      localStorage.setItem('rgbEnabled', this.checked);
    });

    // Fuente
    document.getElementById('font-select').addEventListener('change', function () {
      document.body.style.setProperty('--font-main', `${this.value}, sans-serif`);
      localStorage.setItem('font', this.value);
    });

    // SOCKS autenticación
    document.getElementById('socks-auth').addEventListener('change', function () {
      document.getElementById('socks-auth-fields').style.display = this.checked ? 'block' : 'none';
    });

    // Guardar configuraciones
    function saveHttpConfig() {
      const config = {
        type: 'http',
        host: document.getElementById('http-host').value,
        port: document.getElementById('http-port').value,
        method: document.getElementById('http-method').value,
        header: document.getElementById('http-header').value,
        date: new Date().toLocaleString()
      };
      profiles.push(config);
      saveProfiles();
      alert('Config HTTP guardada!');
    }

    function saveSocksConfig() {
      const auth = document.getElementById('socks-auth').checked;
      const config = {
        type: 'socks5',
        ip: document.getElementById('socks-ip').value,
        port: document.getElementById('socks-port').value,
        auth: auth,
        user: auth ? document.getElementById('socks-user').value : '',
        pass: auth ? document.getElementById('socks-pass').value : '',
        date: new Date().toLocaleString()
      };
      profiles.push(config);
      saveProfiles();
      alert('Config SOCKS guardada!');
    }

    function savePacConfig() {
      const config = {
        type: 'pac-dns',
        dns: document.getElementById('custom-dns').value,
        pac: document.getElementById('pac-url').value,
        date: new Date().toLocaleString()
      };
      profiles.push(config);
      saveProfiles();
      alert('PAC/DNS guardado!');
    }

    // Perfiles
    function saveProfiles() {
      localStorage.setItem('neonx-profiles', JSON.stringify(profiles));
      loadProfiles();
    }

    function loadProfiles() {
      const list = document.getElementById('profile-list');
      list.innerHTML = '';
      profiles.forEach((p, i) => {
        const item = document.createElement('div');
        item.className = 'profile-item';
        item.innerHTML = `
          <div>
            <strong>${p.type.toUpperCase()}</strong><br>
            <small>${p.date}</small>
          </div>
          <button class="btn-danger btn-primary" onclick="deleteProfile(${i})">🗑️</button>
        `;
        list.appendChild(item);
      });
    }

    function deleteProfile(index) {
      profiles.splice(index, 1);
      saveProfiles();
    }

    // Importar/Exportar
    function exportProfiles() {
      const dataStr = "data:text/json;charset=utf-8," + encodeURIComponent(JSON.stringify(profiles, null, 2));
      const dlAnchor = document.createElement('a');
      dlAnchor.setAttribute("href", dataStr);
      dlAnchor.setAttribute("download", "neonx_profiles.json");
      document.body.appendChild(dlAnchor);
      dlAnchor.click();
      document.body.removeChild(dlAnchor);
    }

    function importProfiles() {
      const file = document.getElementById('import-file').files[0];
      if (!file) return;
      const reader = new FileReader();
      reader.onload = function(e) {
        try {
          const imported = JSON.parse(e.target.result);
          profiles = profiles.concat(imported);
          saveProfiles();
          alert('Perfiles importados!');
        } catch (err) {
          alert('Error al importar JSON.');
        }
      };
      reader.readAsText(file);
    }

    // Restablecer
    function resetApp() {
      if (confirm('¿Restablecer toda la app?')) {
        localStorage.clear();
        profiles = [];
        loadProfiles();
        location.reload();
      }
    }

    // Inicializar
    loadPreferences();
    showSection('home');
  </script>
</body>
</html>
