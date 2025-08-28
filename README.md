<!DOCTYPE html>
<html lang="es" id="html">
<head>
  <meta charset="UTF-8" />
  <meta name="viewport" content="width=device-width, initial-scale=1.0"/>
  <title>BerMatMods - Editor de Recibos</title>
  <link rel="manifest" href='data:application/json,{}' id="manifest">
  <link href="https://fonts.googleapis.com/css2?family=Roboto:wght@300;400;500;700&display=swap" rel="stylesheet">
  <script src="https://cdnjs.cloudflare.com/ajax/libs/html2canvas/1.4.1/html2canvas.min.js"></script>
  <script src="https://cdn.jsdelivr.net/npm/swiper@11/swiper-bundle.min.js"></script>
  <script src="https://cdnjs.cloudflare.com/ajax/libs/jspdf/2.5.1/jspdf.umd.min.js"></script>
  <link rel="stylesheet" href="https://cdn.jsdelivr.net/npm/swiper@11/swiper-bundle.min.css">
  <style>
    :root {
      --bg: #69009A;
      --title-color: #69009A;
      --card-bg: #F5F5F5;
      --text-dark: #222;
      --text-gray: #666;
      --border-light: #eee;
    }

    .dark-mode {
      --bg: #121212;
      --card-bg: #1e1e1e;
      --text-dark: #e0e0e0;
      --text-gray: #aaa;
      --border-light: #333;
    }

    body {
      font-family: 'Roboto', sans-serif;
      background: var(--bg);
      color: #fff;
      display: flex;
      justify-content: center;
      align-items: center;
      min-height: 100vh;
      padding: 20px;
      margin: 0;
      transition: background 0.3s;
    }

    .container {
      width: 100%;
      max-width: 380px;
      position: relative;
      overflow: hidden;
      border-radius: 20px;
      box-shadow: 0 15px 30px rgba(0, 0, 0, 0.3);
    }

    .header {
      display: flex;
      justify-content: space-between;
      align-items: center;
      padding: 16px 16px 0 16px;
    }

    .logo {
      width: 70px;
      height: 70px;
    }

    .logo img {
      width: 100%;
      height: auto;
      border-radius: 8px;
    }

    .menu-btn {
      width: 40px;
      height: 40px;
      background: rgba(255, 255, 255, 0.1);
      border-radius: 50%;
      display: flex;
      justify-content: center;
      align-items: center;
      cursor: pointer;
      font-size: 24px;
      color: white;
    }

    .card {
      background: var(--card-bg);
      border-radius: 20px;
      padding: 20px 16px;
      margin: 16px auto;
      width: 94%;
      max-width: 350px;
      box-shadow: 0 4px 10px rgba(0, 0, 0, 0.1);
    }

    .title {
      font-size: 20px;
      font-weight: 700;
      margin-bottom: 10px;
      color: var(--title-color);
    }

    .amount {
      font-size: 42px;
      font-weight: 700;
      color: var(--text-dark);
      margin-bottom: 10px;
    }

    .name {
      font-size: 20px;
      font-weight: 700;
      color: var(--text-dark);
      margin-bottom: 8px;
    }

    .date-time {
      font-size: 14px;
      color: var(--text-gray);
      margin-bottom: 16px;
    }

    .security-code-row {
      display: flex;
      align-items: center;
      justify-content: space-between;
      margin-bottom: 16px;
      font-size: 14px;
      color: var(--text-gray);
    }

    .security-code-label {
      font-weight: 500;
    }

    .security-code-digits {
      display: flex;
      gap: 6px;
    }

    .digit {
      width: 30px;
      height: 30px;
      background: #EAEAEA;
      border-radius: 6px;
      display: flex;
      justify-content: center;
      align-items: center;
      font-size: 16px;
      font-weight: 500;
      color: #000;
    }

    .transaction-data {
      margin-top: 16px;
      font-size: 13px;
      color: var(--text-gray);
      text-transform: uppercase;
      letter-spacing: 0.5px;
      font-weight: 500;
    }

    .data-row {
      display: flex;
      justify-content: space-between;
      margin: 10px 0;
      font-size: 15px;
    }

    .data-row strong {
      color: var(--text-dark);
      font-weight: 700;
    }

    .data-row span {
      color: var(--text-dark);
      font-weight: 400;
    }

    .swiper-container {
      width: 94%;
      max-width: 350px;
      height: 180px;
      margin: 16px auto;
      border-radius: 12px;
      overflow: hidden;
    }

    .swiper-slide img {
      width: 100%;
      height: 100%;
      object-fit: cover;
    }

    /* Menú */
    .menu-overlay {
      position: fixed;
      top: 0;
      left: 0;
      width: 100%;
      height: 100%;
      background: rgba(0, 0, 0, 0.5);
      z-index: 1000;
      display: none;
      justify-content: center;
      align-items: center;
      overflow-y: auto;
    }

    .menu {
      background: var(--card-bg);
      width: 90%;
      max-width: 380px;
      border-radius: 16px;
      padding: 20px;
      box-shadow: 0 10px 30px rgba(0, 0, 0, 0.3);
      max-height: 90vh;
      overflow-y: auto;
    }

    .menu-header {
      text-align: center;
      margin-bottom: 20px;
      color: var(--title-color);
      font-weight: 700;
      font-size: 18px;
    }

    .app-logo {
      width: 60px;
      height: 60px;
      border-radius: 50%;
      overflow: hidden;
      margin: 0 auto 10px;
      box-shadow: 0 0 15px #FFD700, 0 0 30px #FFD700;
      border: 2px solid #FFD700;
    }

    .app-logo img {
      width: 100%;
      height: 100%;
      object-fit: cover;
    }

    .menu-category {
      margin: 20px 0 10px;
      color: var(--title-color);
      font-weight: 500;
      font-size: 16px;
    }

    .menu-list {
      list-style: none;
    }

    .menu-list li {
      padding: 12px 0;
      border-bottom: 1px solid var(--border-light);
      font-size: 15px;
      color: var(--text-dark);
      cursor: pointer;
    }

    .menu-list li:last-child {
      border-bottom: none;
    }

    .switch-row {
      display: flex;
      justify-content: space-between;
      align-items: center;
    }

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
      left: 3px;
      bottom: 3px;
      background-color: white;
      transition: .4s;
      border-radius: 50%;
    }

    input:checked + .slider {
      background-color: #00C89A;
    }

    input:checked + .slider:before {
      transform: translateX(26px);
    }

    .footer {
      text-align: center;
      margin-top: 20px;
      font-size: 12px;
      color: #ddd;
      opacity: 0.8;
    }
  </style>
</head>
<body>
  <div class="container" id="captureArea">
    <div class="header">
      <div class="logo">
        <img id="appLogo" src="https://i.postimg.cc/9MZK0cXj/Icono-de-la-aplicaci-n-Yape-removebg-preview-1.png" alt="App Logo">
      </div>
      <div class="menu-btn" onclick="openMenu()">☰</div>
    </div>

    <div class="card">
      <div class="title" id="operationTitle">¡Yapeaste!</div>
      <div class="amount">S/ <span id="displayAmount">2</span></div>
      <div class="name" id="displayName">Julia Maucaylle H.</div>
      <div class="date-time">
        <span id="dateText">📅 23 ago. 2025</span> | <span id="timeText">⏰ 6:59 p.m.</span>
      </div>

      <div class="security-code-row">
        <span class="security-code-label" id="securityLabel">CÓDIGO DE SEGURIDAD</span>
        <div class="security-code-digits">
          <div class="digit" id="digit1">0</div>
          <div class="digit" id="digit2">3</div>
          <div class="digit" id="digit3">8</div>
        </div>
      </div>

      <div class="transaction-data">Datos de la transacción</div>
      <div class="data-row">
        <strong>Nro. de celular</strong>
        <span id="cellNumber">*** *** 832</span>
      </div>
      <div class="data-row">
        <strong>Destino</strong>
        <span id="destination">Yape</span>
      </div>
      <div class="data-row">
        <strong>Nro. de operación</strong>
        <span id="operationId">18081038</span>
      </div>
      <div class="data-row">
        <strong>Mensaje</strong>
        <span id="messageText">Gracias por el trabajo 😊</span>
      </div>
    </div>

    <div class="swiper-container">
      <div class="swiper-wrapper">
        <div class="swiper-slide">
          <img src="https://i.postimg.cc/Pfp6yX1b/1755961471955.jpg" alt="Anuncio 1">
        </div>
        <div class="swiper-slide">
          <img src="https://i.postimg.cc/5yCn2gfK/1755961504718.jpg" alt="Anuncio 2">
        </div>

    <div class="footer">
      By AnthZz Berrocal | BerMatMods
    </div>
  </div>

  <!-- MENÚ DE 3 RAYAS -->
  <div class="menu-overlay" id="menuOverlay">
    <div class="menu">
      <div class="app-logo">
        <img src="https://i.postimg.cc/sgkfBDPn/IMG-20250826-WA0338.jpg" alt="Logo App">
      </div>
      <div class="menu-header">BerMatMods Recibo Editor Pro</div>

      <!-- Apps -->
      <div class="menu-category">📱 Apps de Pago</div>
      <ul class="menu-list">
        <li onclick="switchApp('yape')">Yape</li>
        <li onclick="switchApp('plin')">Plin</li>
        <li onclick="switchApp('bim')">Bim</li>
        <li onclick="switchApp('tunki')">Tunki</li>
        <li onclick="switchApp('lucy')">Lucy</li>
      </ul>

      <!-- Bancos -->
      <div class="menu-category">🏦 Transferencias</div>
      <ul class="menu-list">
        <li onclick="switchApp('bcp')">BCP</li>
        <li onclick="switchApp('bbva')">BBVA</li>
        <li onclick="switchApp('interbank')">Interbank</li>
        <li onclick="switchApp('scotiabank')">Scotiabank</li>
        <li onclick="switchApp('banbif')">BanBif</li>
      </ul>

      <!-- Mensajería -->
      <div class="menu-category">💬 Mensajes</div>
      <ul class="menu-list">
        <li onclick="switchApp('whatsapp')">WhatsApp</li>
        <li onclick="switchApp('telegram')">Telegram</li>
      </ul>

      <!-- Edición -->
      <div class="menu-category">✏️ Edición</div>
      <ul class="menu-list">
        <li onclick="promptEdit('amount')">Editar monto</li>
        <li onclick="promptEdit('name')">Editar nombre</li>
        <li onclick="promptEdit('cell')">Editar número</li>
        <li onclick="promptEdit('op')">Editar operación</li>
        <li onclick="promptEdit('message')">Editar mensaje</li>
      </ul>

      <!-- Exportar -->
      <div class="menu-category">📤 Exportar</div>
      <ul class="menu-list">
        <li onclick="downloadImage()">Descargar PNG</li>
        <li onclick="downloadPDF()">Descargar PDF</li>
      </ul>

      <!-- Ajustes -->
      <div class="menu-category">⚙️ Ajustes</div>
      <ul class="menu-list">
        <li class="switch-row">
          Modo Oscuro
          <label class="switch">
            <input type="checkbox" id="darkModeToggle" onchange="toggleDarkMode()">
            <span class="slider"></span>
          </label>
        </li>
        <li class="switch-row">
          Idioma: <span id="langText">Español</span>
          <button onclick="toggleLang()" style="background:var(--title-color);color:white;border:none;padding:4px 8px;border-radius:8px;">Cambiar</button>
        </li>
      </ul>

      <!-- Más -->
      <div class="menu-category">ℹ️ Más</div>
      <ul class="menu-list">
        <li onclick="showInfo()">Acerca de BerMatMods</li>
        <li onclick="showHistory()">Historial de Ediciones</li>
        <li onclick="addShortcut()">Añadir a inicio (PWA)</li>
      </ul>

      <div class="close-menu" onclick="closeMenu()" style="text-align:center;margin-top:16px;color:var(--title-color);cursor:pointer;">Cerrar menú</div>
    </div>
  </div>

  <script>
    let currentApp = 'yape';
    let darkMode = false;
    let lang = 'es';
    const history = [];

    const apps = {
      yape: { logo: 'https://i.imgur.com/qWkOuKq.png', bg: '#69009A', titleColor: '#69009A', title: '¡Yapeaste!', security: 'CÓDIGO DE SEGURIDAD', destination: 'Yape' },
      plin: { logo: 'https://i.postimg.cc/63yX0LdC/plin-logo.png', bg: '#00A651', titleColor: '#00A651', title: '¡Plinaste!', security: 'CÓDIGO DE VERIFICACIÓN', destination: 'Plin' },
      bim: { logo: 'https://i.postimg.cc/SsV8LhXr/bim-logo.png', bg: '#1374F3', titleColor: '#1374F3', title: '¡Bimeaste!', security: 'CÓDIGO DE SEGURIDAD', destination: 'Bim' },
      tunki: { logo: 'https://i.postimg.cc/XYv5BkLg/tunki-logo.png', bg: '#FF6B00', titleColor: '#FF6B00', title: 'Transferencia exitosa', security: 'Código de operación', destination: 'Tunki' },
      lucy: { logo: 'https://i.postimg.cc/8cXJ0Z7v/lucy-logo.png', bg: '#9C27B0', titleColor: '#9C27B0', title: 'Pago realizado', security: 'Número de operación', destination: 'Lucy' },
      bcp: { logo: 'https://i.postimg.cc/9Q1d0W3k/bcp-logo.png', bg: '#E60012', titleColor: '#E60012', title: 'Transferencia exitosa', security: 'Código de operación', destination: 'BCP' },
      bbva: { logo: 'https://i.postimg.cc/7Z0K2VrN/bbva-logo.png', bg: '#F7931E', titleColor: '#F7931E', title: 'Pago realizado', security: 'Código de confirmación', destination: 'BBVA' },
      interbank: { logo: 'https://i.postimg.cc/25jDvq9Z/interbank-logo.png', bg: '#0039A6', titleColor: '#0039A6', title: 'Transferencia completada', security: 'Número de operación', destination: 'Interbank' },
      scotiabank: { logo: 'https://i.postimg.cc/441N1k8W/scotia-logo.png', bg: '#0062AC', titleColor: '#0062AC', title: 'Transferencia exitosa', security: 'Número de transacción', destination: 'Scotiabank' },
      banbif: { logo: 'https://i.postimg.cc/65VvqR2d/banbif-logo.png', bg: '#009640', titleColor: '#009640', title: 'Transferencia completada', security: 'Código de operación', destination: 'BanBif' },
      whatsapp: { logo: 'https://i.postimg.cc/441N1k8W/whatsapp-logo.png', bg: '#128C7E', titleColor: '#128C7E', title: 'Mensaje enviado', security: 'Hora', destination: 'WhatsApp' },
      telegram: { logo: 'https://i.postimg.cc/441N1k8W/telegram-logo.png', bg: '#0088cc', titleColor: '#0088cc', title: 'Mensaje enviado', security: 'Hora', destination: 'Telegram' }
    };

    function switchApp(app) {
      if (!apps[app]) return;
      currentApp = app;
      const data = apps[app];
      document.body.style.setProperty('--bg', data.bg);
      document.body.style.setProperty('--title-color', data.titleColor);
      document.getElementById('appLogo').src = data.logo;
      document.getElementById('operationTitle').innerText = data.title;
      document.getElementById('securityLabel').innerText = data.security;
      document.getElementById('destination').innerText = data.destination;
      closeMenu();
    }

    function openMenu() {
      document.getElementById('menuOverlay').style.display = 'flex';
    }

    function closeMenu() {
      document.getElementById('menuOverlay').style.display = 'none';
    }

    function promptEdit(field) {
      const labels = { amount: 'Monto', name: 'Nombre', cell: 'Número', op: 'Operación', message: 'Mensaje' };
      let value = prompt((lang === 'es' ? 'Editar ' : 'Edit ') + labels[field] + ':', document.getElementById({
        'amount': 'displayAmount',
        'name': 'displayName',
        'cell': 'cellNumber',
        'op': 'operationId',
        'message': 'messageText'
      }[field]).innerText);
      if (value) {
        document.getElementById({
          'amount': 'displayAmount',
          'name': 'displayName',
          'cell': 'cellNumber',
          'op': 'operationId',
          'message': 'messageText'
        }[field]).innerText = value;
        saveToHistory();
      }
      closeMenu();
    }

    function saveToHistory() {
      if (history.length >= 5) history.shift();
      history.push(document.getElementById('captureArea').innerHTML);
    }

    function showHistory() {
      alert((lang === 'es' ? 'Historial (últimos 5):' : 'History (last 5):') + '\n\n' + history.map((_, i) => `Recibo ${i+1}`).join('\n'));
    }

    function downloadImage() {
      html2canvas(document.getElementById('captureArea'), {
        backgroundColor: getComputedStyle(document.body).getPropertyValue('--bg'),
        scale: 2
      }).then(canvas => {
        const link = document.createElement('a');
        link.download = `recibo-${currentApp}.png`;
        link.href = canvas.toDataURL();
        link.click();
      });
      closeMenu();
    }

    function downloadPDF() {
      const { jsPDF } = window.jspdf;
      html2canvas(document.getElementById('captureArea'), { scale: 2 }).then(canvas => {
        const img = canvas.toDataURL("image/png");
        const pdf = new jsPDF('p', 'mm', 'a4');
        const width = pdf.internal.pageSize.getWidth();
        const height = (canvas.height * width) / canvas.width;
        pdf.addImage(img, 'PNG', 0, 0, width, height);
        pdf.save(`recibo-${currentApp}.pdf`);
      });
      closeMenu();
    }

    function toggleDarkMode() {
      darkMode = !darkMode;
      document.body.classList.toggle('dark-mode', darkMode);
    }

    function toggleLang() {
      lang = lang === 'es' ? 'en' : 'es';
      document.getElementById('langText').innerText = lang === 'es' ? 'Español' : 'English';
    }

    function showInfo() {
      alert("BerMatMods Recibo Editor Pro\nBy AnthZz Berrocal\nVersión 2.0\nSolo para fines educativos.");
    }

    function addShortcut() {
      if ('serviceWorker' in navigator) {
        navigator.serviceWorker.register('/sw.js').then(() => {
          alert('App lista para instalarse. Usa el botón "Añadir a inicio" de tu navegador.');
        });
      }
    }

    const swiper = new Swiper('.swiper-container', {
      loop: true,
      autoplay: { delay: 3000, disableOnInteraction: false },
      pagination: { el: '.swiper-pagination', clickable: true }
    });

    function updateDateTime() {
      const now = new Date();
      const options = { year: 'numeric', month: 'short', day: 'numeric' };
      let date = now.toLocaleDateString(lang, options);
      document.getElementById('dateText').innerText = (lang === 'es' ? '📅 ' : '📅 ') + date;

      const hour = now.getHours();
      const minute = now.getMinutes();
      const ampm = hour >= 12 ? (lang === 'es' ? 'p.m.' : 'PM') : (lang === 'es' ? 'a.m.' : 'AM');
      const formattedHour = hour % 12 || 12;
      const formattedMinute = minute.toString().padStart(2, '0');
      document.getElementById('timeText').innerText = `⏰ ${formattedHour}:${formattedMinute} ${ampm}`;
    }

    window.onload = () => {
      switchApp('yape');
      updateDateTime();
      saveToHistory();
    };

    setInterval(updateDateTime, 60000);
  </script>

  <!-- PWA Manifest -->
  <script>
    document.getElementById('manifest').href = 'data:application/json,' + encodeURIComponent(JSON.stringify({
      "name": "BerMatMods Recibo Editor",
      "short_name": "Recibo Editor",
      "start_url": ".",
      "display": "standalone",
      "background_color": "#69009A",
      "theme_color": "#69009A",
      "icons": [{ "src": "https://i.postimg.cc/sgkfBDPn/IMG-20250826-WA0338.jpg", "sizes": "192x192", "type": "image/jpg" }]
    }));
  </script>
</body>
</html>
