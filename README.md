<!DOCTYPE html>
<html lang="es">
<head>
  <meta charset="UTF-8" />
  <meta name="viewport" content="width=device-width, initial-scale=1.0"/>
  <title>Editor de Yape - ¡Yapeaste! | By AnthZz Berrocal</title>
  <link href="https://fonts.googleapis.com/css2?family=Roboto:wght@300;400;500;700&display=swap" rel="stylesheet">
  <script src="https://cdnjs.cloudflare.com/ajax/libs/html2canvas/1.4.1/html2canvas.min.js"></script>
  <script src="https://cdn.jsdelivr.net/npm/swiper@11/swiper-bundle.min.js"></script>
  <link rel="stylesheet" href="https://cdn.jsdelivr.net/npm/swiper@11/swiper-bundle.min.css">
  <style>
    * {
      margin: 0;
      padding: 0;
      box-sizing: border-box;
    }

    body {
      font-family: 'Roboto', sans-serif;
      background: #69009A;
      color: #fff;
      display: flex;
      justify-content: center;
      align-items: center;
      min-height: 100vh;
      padding: 20px;
    }

    .container {
      width: 100%;
      max-width: 400px;
      position: relative;
      overflow: hidden;
    }

    .header {
      text-align: left;
      margin-bottom: 20px;
    }

    .logo {
      width: 80px;
      height: 80px;
      display: inline-block;
    }

    .logo img {
      width: 100%;
      height: auto;
    }

    .close-btn {
      position: absolute;
      top: 30px;
      right: 30px;
      width: 60px;
      height: 60px;
      border-radius: 50%;
      background: rgba(255, 255, 255, 0.1);
      color: white;
      font-size: 28px;
      display: flex;
      justify-content: center;
      align-items: center;
      cursor: pointer;
      border: none;
    }

    .card {
      background: #F5F5F5;
      border-radius: 20px;
      padding: 24px;
      margin-bottom: 20px;
      box-shadow: 0 4px 10px rgba(0, 0, 0, 0.1);
    }

    .title {
      font-size: 22px;
      font-weight: 700;
      color: #69009A;
      margin-bottom: 12px;
    }

    .amount {
      font-size: 48px;
      font-weight: 700;
      color: #222;
      margin-bottom: 12px;
    }

    .name {
      font-size: 24px;
      font-weight: 500;
      color: #222;
      margin-bottom: 8px;
    }

    .date-time {
      font-size: 16px;
      color: #666;
      margin-bottom: 24px;
    }

    .security-code {
      display: flex;
      justify-content: space-between;
      margin-bottom: 24px;
      font-size: 14px;
      color: #666;
    }

    .security-code span {
      font-weight: 500;
    }

    .info-icon {
      color: #00C89A;
      font-size: 24px;
      cursor: pointer;
    }

    .code-digits {
      display: flex;
      gap: 10px;
    }

    .digit {
      width: 40px;
      height: 40px;
      background: #EAEAEA;
      border-radius: 8px;
      display: flex;
      justify-content: center;
      align-items: center;
      font-size: 18px;
      font-weight: 500;
      color: #222;
    }

    .transaction-data {
      margin-top: 20px;
      font-size: 14px;
      color: #666;
      text-transform: uppercase;
      letter-spacing: 0.5px;
    }

    .data-row {
      display: flex;
      justify-content: space-between;
      margin: 12px 0;
      font-size: 16px;
    }

    .data-row strong {
      color: #222;
    }

    .button {
      width: 100%;
      padding: 16px;
      background: #00C89A;
      color: white;
      border: none;
      border-radius: 12px;
      font-size: 18px;
      font-weight: 500;
      display: flex;
      justify-content: center;
      align-items: center;
      gap: 10px;
      margin: 20px 0;
      cursor: pointer;
    }

    .swiper-container {
      width: 100%;
      height: 200px;
      margin-top: 20px;
    }

    .swiper-slide {
      text-align: center;
      font-size: 18px;
      background: #F5F5F5;
      border-radius: 12px;
      overflow: hidden;
    }

    .swiper-slide img {
      width: 100%;
      height: 100%;
      object-fit: cover;
    }

    .controls {
      margin-top: 20px;
      padding: 20px;
      background: rgba(255, 255, 255, 0.1);
      border-radius: 12px;
      backdrop-filter: blur(10px);
    }

    .input-group {
      margin-bottom: 12px;
    }

    .input-group label {
      display: block;
      margin-bottom: 6px;
      font-size: 14px;
      color: #fff;
    }

    .input-group input {
      width: 100%;
      padding: 8px;
      border: 1px solid #ccc;
      border-radius: 8px;
      font-size: 14px;
      background: white;
      color: #000;
    }

    button.export {
      width: 100%;
      padding: 12px;
      background: #00C89A;
      color: white;
      border: none;
      border-radius: 8px;
      font-size: 16px;
      font-weight: 500;
      cursor: pointer;
      margin-top: 16px;
    }

    button.export:hover {
      background: #00B388;
    }

    .footer {
      text-align: center;
      margin-top: 20px;
      font-size: 12px;
      color: #ddd;
      opacity: 0.8;
    }

    /* AJUSTES */
    .settings {
      margin-top: 20px;
      padding: 20px;
      background: rgba(255, 255, 255, 0.1);
      border-radius: 12px;
      backdrop-filter: blur(10px);
    }

    .settings h3 {
      font-size: 18px;
      margin-bottom: 16px;
      color: #fff;
    }

    .app-info {
      text-align: center;
      margin-bottom: 16px;
    }

    .app-logo {
      width: 60px;
      height: 60px;
      border-radius: 50%;
      overflow: hidden;
      margin: 0 auto;
      box-shadow: 0 0 15px #FFD700, 0 0 30px #FFD700, inset 0 0 10px rgba(255, 215, 0, 0.5);
      border: 2px solid #FFD700;
    }

    .app-logo img {
      width: 100%;
      height: 100%;
      object-fit: cover;
    }

    .app-name {
      font-size: 16px;
      font-weight: 500;
      margin-top: 8px;
      color: #fff;
    }

    .app-version {
      font-size: 12px;
      color: #ddd;
    }

    .settings-list {
      list-style: none;
    }

    .settings-list li {
      padding: 12px 0;
      border-bottom: 1px solid rgba(255, 255, 255, 0.1);
      font-size: 14px;
      color: #ddd;
      cursor: pointer;
    }

    .settings-list li:hover {
      color: #fff;
    }

    .settings-list li:last-child {
      border-bottom: none;
    }
  </style>
</head>
<body>
  <div class="container">
    <!-- CABECERA -->
    <div class="header">
      <div class="logo">
        <img src="https://i.imgur.com/qWkOuKq.png" alt="Yape Logo">
      </div>
    </div>

    <!-- BOTÓN DE CERRAR -->
    <button class="close-btn">×</button>

    <!-- TARJETA DE TRANSACCIÓN -->
    <div class="card">
      <div class="title">¡Yapeaste!</div>
      <div class="amount">S/ <span id="displayAmount">2</span></div>
      <div class="name" id="displayName">Julia Maucaylle H.</div>
      <div class="date-time">
        <span>📅 23 ago. 2025</span> | <span>⏰ 06:59 p.m.</span>
      </div>

      <div class="security-code">
        <span>CÓDIGO DE SEGURIDAD</span>
        <span class="info-icon">ℹ️</span>
      </div>
      <div class="code-digits">
        <div class="digit" id="digit1">0</div>
        <div class="digit" id="digit2">3</div>
        <div class="digit" id="digit3">8</div>
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
    </div>

    <!-- BOTÓN NUEVO YAPEO -->
    <button class="button">
      <svg xmlns="http://www.w3.org/2000/svg" width="24" height="24" viewBox="0 0 24 24" fill="none" stroke="white" stroke-width="2" stroke-linecap="round" stroke-linejoin="round">
        <path d="M21 15v4a2 2 0 0 1-2 2H5a2 2 0 0 1-2-2v-4"></path>
        <polyline points="17 8 12 3 7 8"></polyline>
        <line x1="12" y1="3" x2="12" y2="15"></line>
      </svg>
      NUEVO YAPEO
    </button>

    <!-- SWIPER DE ANUNCIOS -->
    <div class="swiper-container">
      <div class="swiper-wrapper">
        <div class="swiper-slide">
          <img src="https://i.postimg.cc/Pfp6yX1b/1755961471955.jpg" alt="Anuncio 1">
        </div>
        <div class="swiper-slide">
          <img src="https://i.postimg.cc/5yCn2gfK/1755961504718.jpg" alt="Anuncio 2">
        </div>
        <div class="swiper-slide">
          <img src="https://i.imgur.com/wUjLxXp.jpg" alt="Anuncio 3">
        </div>
      </div>
    </div>

    <!-- CONTROLES DE EDICIÓN -->
    <div class="controls">
      <div class="input-group">
        <label>Monto (S/)</label>
        <input type="text" id="amountInput" value="2" oninput="updateAmount()">
      </div>
      <div class="input-group">
        <label>Nombre completo</label>
        <input type="text" id="nameInput" value="Julia Maucaylle H." oninput="updateName()">
      </div>
      <div class="input-group">
        <label>Fecha</label>
        <input type="text" id="dateInput" value="23 ago. 2025" oninput="updateDate()">
      </div>
      <div class="input-group">
        <label>Hora</label>
        <input type="text" id="timeInput" value="06:59 p.m." oninput="updateTime()">
      </div>
      <div class="input-group">
        <label>Código de seguridad</label>
        <input type="text" id="codeInput" value="038" oninput="updateCode()">
      </div>
      <div class="input-group">
        <label>Número de celular</label>
        <input type="text" id="cellInput" value="*** *** 832" oninput="updateCell()">
      </div>
      <div class="input-group">
        <label>Nro. de operación</label>
        <input type="text" id="opInput" value="18081038" oninput="updateOp()">
      </div>
      <button class="export" onclick="downloadImage()">📥 Descargar Imagen</button>
    </div>

    <!-- AJUSTES -->
    <div class="settings">
      <h3>⚙️ Ajustes</h3>
      <div class="app-info">
        <div class="app-logo">
          <img src="https://i.postimg.cc/sgkfBDPn/IMG-20250826-WA0338.jpg" alt="Logo App">
        </div>
        <div class="app-name">Editor de Yape</div>
        <div class="app-version">Versión 1.0.0</div>
      </div>
      <ul class="settings-list">
        <li>Editar Recibo</li>
        <li>Configuración de Notificaciones</li>
        <li>Acerca de la App</li>
        <li>Contacto</li>
        <li>Privacidad</li>
        <li>Terminos y Condiciones</li>
      </ul>
    </div>

    <!-- FOOTER -->
    <div class="footer">
      By AnthZz Berrocal | BerMatMods
    </div>
  </div>

  <script>
    function updateAmount() {
      document.getElementById('displayAmount').innerText = document.getElementById('amountInput').value;
    }

    function updateName() {
      document.getElementById('displayName').innerText = document.getElementById('nameInput').value;
    }

    function updateDate() {
      document.querySelector('.date-time span:nth-child(1)').innerText = `📅 ${document.getElementById('dateInput').value}`;
    }

    function updateTime() {
      document.querySelector('.date-time span:nth-child(3)').innerText = `⏰ ${document.getElementById('timeInput').value}`;
    }

    function updateCode() {
      const code = document.getElementById('codeInput').value;
      document.getElementById('digit1').innerText = code[0] || '0';
      document.getElementById('digit2').innerText = code[1] || '0';
      document.getElementById('digit3').innerText = code[2] || '0';
    }

    function updateCell() {
      document.getElementById('cellNumber').innerText = document.getElementById('cellInput').value;
    }

    function updateOp() {
      document.getElementById('operationId').innerText = document.getElementById('opInput').value;
    }

    function downloadImage() {
      const capture = document.querySelector('.container');
      html2canvas(capture, {
        backgroundColor: '#69009A',
        scale: 2,
        useCORS: true
      }).then(canvas => {
        const link = document.createElement('a');
        link.download = 'yape-recibo.png';
        link.href = canvas.toDataURL();
        link.click();
      });
    }

    // Inicializar Swiper
    const swiper = new Swiper('.swiper-container', {
      loop: true,
      autoplay: {
        delay: 3000,
        disableOnInteraction: false,
      },
      navigation: {
        nextEl: '.swiper-button-next',
        prevEl: '.swiper-button-prev',
      },
      pagination: {
        el: '.swiper-pagination',
        clickable: true,
      },
    });

    // Inicializar
    window.onload = () => {
      updateAmount();
      updateName();
      updateDate();
      updateTime();
      updateCode();
      updateCell();
      updateOp();
    };
  </script>
</body>
</html>
