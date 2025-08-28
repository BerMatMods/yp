<!DOCTYPE html>
<html lang="es">
<head>
  <meta charset="UTF-8" />
  <meta name="viewport" content="width=device-width, initial-scale=1.0"/>
  <title>Recibo de Yape Realista</title>
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
      width: 80px;
      height: 80px;
    }

    .logo img {
      width: 100%;
      height: auto;
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
      background: #F5F5F5;
      border-radius: 20px;
      padding: 24px;
      margin-bottom: 20px;
      box-shadow: 0 4px 10px rgba(0, 0, 0, 0.1);
    }

    .title {
      font-size: 22px;
      font-weight: 700;
      margin-bottom: 12px;
      color: #69009A;
    }

    .amount {
      font-size: 48px;
      font-weight: 700;
      color: #D32F2F;
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
      background: #F5F5F5;
      border-radius: 12px;
      overflow: hidden;
    }

    .swiper-slide img {
      width: 100%;
      height: 100%;
      object-fit: cover;
    }

    /* Menú desplegable */
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
    }

    .menu {
      background: #F5F5F5;
      width: 90%;
      max-width: 350px;
      border-radius: 16px;
      padding: 20px;
      box-shadow: 0 10px 30px rgba(0, 0, 0, 0.3);
    }

    .menu-header {
      text-align: center;
      margin-bottom: 20px;
      color: #69009A;
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

    .menu-list {
      list-style: none;
    }

    .menu-list li {
      padding: 12px 0;
      border-bottom: 1px solid #eee;
      font-size: 15px;
      color: #333;
      cursor: pointer;
    }

    .menu-list li:last-child {
      border-bottom: none;
    }

    .close-menu {
      text-align: center;
      margin-top: 16px;
      color: #00C89A;
      font-weight: 500;
      cursor: pointer;
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
  <!-- RECIBO REALISTA -->
  <div class="container" id="captureArea">
    <div class="header">
      <div class="logo">
        <img src="https://share.google/images/nivz3x5SlndAkGe3o" alt="Yape Logo">
      </div>
      <div class="menu-btn" onclick="openMenu()">☰</div>
    </div>

    <div class="card">
      <div class="title" id="operationTitle">¡Yapeaste!</div>
      <div class="amount" id="amountColor">S/ <span id="displayAmount">2</span></div>
      <div class="name" id="displayName">Julia Maucaylle H.</div>
      <div class="date-time">
        <span id="dateText">📅 23 ago. 2025</span> | <span id="timeText">⏰ 6:59 p.m.</span>
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
      <div class="data-row">
        <strong>Mensaje</strong>
        <span id="messageText">Gracias por el trabajo 😊</span>
      </div>
    </div>

    <button class="button">
      <svg xmlns="http://www.w3.org/2000/svg" width="24" height="24" viewBox="0 0 24 24" fill="none" stroke="white" stroke-width="2" stroke-linecap="round" stroke-linejoin="round">
        <path d="M21 15v4a2 2 0 0 1-2 2H5a2 2 0 0 1-2-2v-4"></path>
        <polyline points="17 8 12 3 7 8"></polyline>
        <line x1="12" y1="3" x2="12" y2="15"></line>
      </svg>
      NUEVO YAPEO
    </button>

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

    <div class="footer">
      By AnthZz Berrocal | BerMatMods
    </div>
  </div>

  <!-- MENÚ DE AJUSTES (3 RAYAS) -->
  <div class="menu-overlay" id="menuOverlay">
    <div class="menu">
      <div class="menu-header">Configuración del Editor</div>
      <div class="app-logo">
        <img src="https://i.postimg.cc/sgkfBDPn/IMG-20250826-WA0338.jpg" alt="Logo App">
      </div>
      <ul class="menu-list">
        <li onclick="changeType('sent')">Cambiar a: ¡Yapeaste!</li>
        <li onclick="changeType('received')">Cambiar a: ¡Te yapearon!</li>
        <li onclick="changeType('payment')">Pago realizado</li>
        <li onclick="changeType('topup')">Recarga exitosa</li>
        <li onclick="promptEdit('amount')">Editar monto</li>
        <li onclick="promptEdit('name')">Editar nombre</li>
        <li onclick="promptEdit('cell')">Editar número</li>
        <li onclick="promptEdit('op')">Editar operación</li>
        <li onclick="promptEdit('message')">Editar mensaje</li>
        <li onclick="downloadImage()">📥 Descargar como imagen</li>
      </ul>
      <div class="close-menu" onclick="closeMenu()">Cerrar menú</div>
    </div>
  </div>

  <script>
    // Abrir y cerrar menú
    function openMenu() {
      document.getElementById('menuOverlay').style.display = 'flex';
    }

    function closeMenu() {
      document.getElementById('menuOverlay').style.display = 'none';
    }

    // Cambiar tipo de operación
    function changeType(type) {
      const title = document.getElementById('operationTitle');
      const amount = document.getElementById('amountColor');

      switch(type) {
        case 'sent':
          title.innerText = '¡Yapeaste!';
          title.style.color = '#69009A';
          amount.style.color = '#D32F2F';
          break;
        case 'received':
          title.innerText = '¡Te yapearon!';
          title.style.color = '#00C89A';
          amount.style.color = '#00C89A';
          break;
        case 'payment':
          title.innerText = 'Pago realizado';
          title.style.color = '#69009A';
          amount.style.color = '#D32F2F';
          break;
        case 'topup':
          title.innerText = 'Recarga exitosa';
          title.style.color = '#00C89A';
          amount.style.color = '#00C89A';
          break;
      }
      closeMenu();
    }

    // Editar campos
    function promptEdit(field) {
      let value;
      switch(field) {
        case 'amount':
          value = prompt('Ingresa el monto:', document.getElementById('displayAmount').innerText);
          if (value) document.getElementById('displayAmount').innerText = value;
          break;
        case 'name':
          value = prompt('Nombre del contacto:', document.getElementById('displayName').innerText);
          if (value) document.getElementById('displayName').innerText = value;
          break;
        case 'cell':
          value = prompt('Número de celular:', document.getElementById('cellNumber').innerText);
          if (value) document.getElementById('cellNumber').innerText = value;
          break;
        case 'op':
          value = prompt('Número de operación:', document.getElementById('operationId').innerText);
          if (value) document.getElementById('operationId').innerText = value;
          break;
        case 'message':
          value = prompt('Mensaje:', document.getElementById('messageText').innerText);
          if (value) document.getElementById('messageText').innerText = value;
          break;
      }
    }

    // Actualizar fecha y hora (Perú)
    function updateDateTime() {
      const now = new Date();
      const options = { year: 'numeric', month: 'short', day: 'numeric' };
      const date = now.toLocaleDateString('es-PE', options).replace('ene', 'ene').replace('feb', 'feb').replace('mar', 'mar').replace('abr', 'abr').replace('may', 'may').replace('jun', 'jun').replace('jul', 'jul').replace('ago', 'ago').replace('sep', 'sep').replace('oct', 'oct').replace('nov', 'nov').replace('dic', 'dic');
      document.getElementById('dateText').innerText = `📅 ${date}`;

      const hour = now.getHours();
      const minute = now.getMinutes();
      const ampm = hour >= 12 ? 'p.m.' : 'a.m.';
      const formattedHour = hour % 12 || 12;
      const formattedMinute = minute.toString().padStart(2, '0');
      document.getElementById('timeText').innerText = `⏰ ${formattedHour}:${formattedMinute} ${ampm}`;
    }

    // Descargar como imagen
    function downloadImage() {
      const capture = document.getElementById('captureArea');
      html2canvas(capture, {
        backgroundColor: '#69009A',
        scale: 2,
        useCORS: true
      }).then(canvas => {
        const link = document.createElement('a');
        link.download = 'recibo-yape.png';
        link.href = canvas.toDataURL();
        link.click();
      });
      closeMenu();
    }

    // Inicializar Swiper
    const swiper = new Swiper('.swiper-container', {
      loop: true,
      autoplay: {
        delay: 3000,
        disableOnInteraction: false,
      },
      pagination: {
        el: '.swiper-pagination',
        clickable: true,
      },
    });

    // Inicializar
    window.onload = () => {
      updateDateTime();
    };

    // Actualizar cada minuto
    setInterval(updateDateTime, 60000);
  </script>
</body>
</html>
