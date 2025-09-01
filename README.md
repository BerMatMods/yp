
<html lang="es">
<head>
  <meta charset="utf-8" />
  <meta name="viewport" content="width=device-width, initial-scale=1, maximum-scale=1, user-scalable=no" />
  <title>Para Briyidth 💖</title>

  <!-- Google Fonts -->
  <link href="https://fonts.googleapis.com/css2?family=Dancing+Script:wght@700&family=Montserrat:wght@500&display=swap" rel="stylesheet">
  <!-- Font Awesome -->
  <script src="https://kit.fontawesome.com/a2b5d5e9b5.js" crossorigin="anonymous"></script>

  <style>
    /* ====== RESET Y ESTILOS BASE ====== */
    * {
      margin: 0;
      padding: 0;
      box-sizing: border-box;
    }

    :root {
      --bg: #000;
      --neon-pink: #ff2bd6;
      --neon-purple: #a84dff;
      --neon-cyan: #27e0ff;
      --menu-bg: linear-gradient(135deg, #1e0030, #3a1a5a, #2a0040);
      --text-light: #fff;
    }

    html, body {
      height: 100%;
      margin: 0;
      background: var(--bg);
      overflow: hidden;
      color: var(--text-light);
      font-family: 'Montserrat', sans-serif;
      position: relative;
    }

    /* ====== BOTÓN DEL MENÚ (3 RAYAS BLANCAS Y GRANDES) ====== */
    .menu-toggle {
      position: fixed;
      top: 20px;
      left: 20px;
      width: 60px;
      height: 60px;
      background: rgba(0, 0, 0, 0.5);
      border-radius: 50%;
      display: flex;
      flex-direction: column;
      align-items: center;
      justify-content: center;
      z-index: 1000;
      cursor: pointer;
      backdrop-filter: blur(10px);
      border: 2px solid rgba(255, 255, 255, 0.3);
      box-shadow: 
        0 0 20px rgba(255, 255, 255, 0.2),
        0 0 30px rgba(255, 255, 255, 0.1);
      transition: all 0.3s ease;
    }

    .menu-toggle:hover {
      transform: scale(1.1);
      box-shadow: 
        0 0 25px rgba(255, 255, 255, 0.4),
        0 0 40px rgba(255, 255, 255, 0.2);
    }

    /* Líneas blancas, gruesas y bien espaciadas */
    .menu-line {
      width: 28px;
      height: 3.5px;
      background: #ffffff;
      border-radius: 2px;
      margin: 4px 0;
      transition: background 0.3s;
      box-shadow: 0 0 8px rgba(255, 255, 255, 0.8);
    }

    .menu-toggle:hover .menu-line {
      background: #ffffff;
      box-shadow: 0 0 10px rgba(255, 255, 255, 1);
    }

    /* ====== PANEL DEL MENÚ ====== */
    .menu-panel {
      position: fixed;
      top: 0;
      left: -320px;
      width: 300px;
      height: 100%;
      background: var(--menu-bg);
      backdrop-filter: blur(12px);
      border-right: 2px solid var(--neon-purple);
      padding: 80px 20px 40px;
      z-index: 999;
      transition: left 0.4s cubic-bezier(0.68, -0.55, 0.265, 1.55);
      display: flex;
      flex-direction: column;
      align-items: center;
      font-family: 'Montserrat', sans-serif;
      box-shadow: -10px 0 30px rgba(0, 0, 0, 0.5);
    }

    .menu-panel.open {
      left: 0;
    }

    /* Título del menú */
    .menu-panel h3 {
      color: #ff8ed4;
      font-size: 18px;
      margin-bottom: 25px;
      text-align: center;
      font-weight: 600;
      letter-spacing: 0.5px;
      text-shadow: 0 0 10px rgba(255, 43, 214, 0.4);
    }

    /* Botón de WhatsApp */
    .menu-panel a {
      display: flex;
      align-items: center;
      justify-content: center;
      gap: 12px;
      color: #d0a0ff;
      text-decoration: none;
      font-size: 16px;
      font-weight: 500;
      margin: 15px 0;
      padding: 14px 20px;
      border-radius: 14px;
      background: rgba(168, 77, 255, 0.15);
      width: 90%;
      max-width: 260px;
      text-align: center;
      transition: all 0.3s ease;
      border: 1px solid rgba(168, 77, 255, 0.3);
      box-shadow: 0 0 15px rgba(168, 77, 255, 0.1);
    }

    .menu-panel a:hover {
      background: rgba(168, 77, 255, 0.25);
      transform: scale(1.05);
      box-shadow: 0 0 20px rgba(168, 77, 255, 0.3);
      color: var(--neon-pink);
    }

    .menu-panel a i {
      color: #25D366;
      font-size: 18px;
    }

    /* Botón de cerrar */
    .close-btn {
      position: absolute;
      top: 20px;
      right: 20px;
      background: none;
      border: none;
      font-size: 28px;
      color: #fff;
      cursor: pointer;
      opacity: 0.9;
      transition: all 0.3s;
    }

    .close-btn:hover {
      opacity: 1;
      transform: rotate(90deg);
      color: #ff2bd6;
      text-shadow: 0 0 10px rgba(255, 43, 214, 0.8);
    }

    /* ====== TEXTO DENTRO DEL CORAZÓN ====== */
    .heart-inside-text {
      position: fixed;
      top: 50%;
      left: 50%;
      transform: translate(-50%, -50%);
      font-family: 'Dancing Script', cursive;
      font-size: clamp(16px, 3.5vw, 28px);
      color: #ff8ed4;
      text-shadow: 
        0 0 10px rgba(255, 43, 214, 0.8),
        0 0 20px rgba(168, 77, 255, 0.5);
      pointer-events: none;
      z-index: 10;
      text-align: center;
      max-width: 80%;
      white-space: normal;
      line-height: 1.4;
      opacity: 0;
      transition: opacity 0.5s ease;
    }

    /* ====== FIRMA ABAJO ====== */
    .footer {
      position: fixed;
      bottom: 15px;
      left: 50%;
      transform: translateX(-50%);
      font-size: 13px;
      color: #a84dff;
      z-index: 10;
      letter-spacing: 1px;
      text-align: center;
    }

    .footer a {
      color: #a0ffa0;
      text-decoration: none;
    }

    .footer a i {
      color: #25D366;
    }

    canvas {
      display: block;
      width: 100vw;
      height: 100vh;
    }
  </style>
</head>
<body>

  <canvas id="c"></canvas>

  <!-- Texto dentro del corazón -->
  <div class="heart-inside-text" id="heartText"></div>

  <!-- Botón del menú: 3 rayas BLANCAS, GRANDES y VISIBLES -->
  <div class="menu-toggle" id="menuToggle">
    <span class="menu-line"></span>
    <span class="menu-line"></span>
    <span class="menu-line"></span>
  </div>

  <!-- Panel del menú -->
  <div class="menu-panel" id="menuPanel">
    <button class="close-btn" id="closeMenu">&times;</button>
    <h3>¿Quieres un proyecto personalizado?</h3>
    <a href="https://wa.me/51937556459" target="_blank">
      <i class="fab fa-whatsapp"></i>
      <span>Escríbeme al WhatsApp</span>
    </a>
  </div>

  <!-- Firma -->
  <div class="footer">
    by AnthZz Berrocal BerMatMods
  </div>

  <script>
    /* ===========================================================
       ANIMACIÓN DEL CORAZÓN + MENÚ + TEXTO DINÁMICO
       (Código original, optimizado y funcional)
       =========================================================== */
    (() => {
      const canvas = document.getElementById('c');
      const ctx = canvas.getContext('2d');
      const textEl = document.getElementById('heartText');
      const menuToggle = document.getElementById('menuToggle');
      const menuPanel = document.getElementById('menuPanel');
      const closeMenu = document.getElementById('closeMenu');

      // Resize canvas (Hi-DPI)
      const resize = () => {
        const dpr = Math.max(1, Math.min(2, window.devicePixelRatio || 1));
        canvas.width = Math.floor(innerWidth * dpr);
        canvas.height = Math.floor(innerHeight * dpr);
        ctx.setTransform(dpr, 0, 0, dpr, 0, 0);
      };
      window.addEventListener('resize', resize);
      resize();

      // Ecuación del corazón
      const heartPoint = (t, scale = 12) => {
        const x = 16 * Math.sin(t) ** 3;
        const y = 13 * Math.cos(t) - 5 * Math.cos(2 * t) - 2 * Math.cos(3 * t) - Math.cos(4 * t);
        return { x: x * scale, y: -y * scale };
      };

      const outline = [];
      const OUTLINE_STEPS = 800;
      for (let i = 0; i <= OUTLINE_STEPS; i++) {
        const t = (i / OUTLINE_STEPS) * Math.PI * 2;
        outline.push(heartPoint(t));
      }

      // Corazón pequeño (60%)
      const outlineSmall = outline.map(p => ({
        x: p.x * 0.6,
        y: p.y * 0.6
      }));

      // Partículas
      const particles = [];
      const MAX_PARTICLES = 900;

      function spawnParticle(x, y, scale = 1) {
        const vx = x;
        const vy = y;
        const mag = Math.hypot(vx, vy) || 1;
        const speed = 0.015 + Math.random() * 0.035;
        const life = 700 + Math.random() * 900;

        particles.push({
          x, y,
          vx: (vx / mag) * (speed * (40 + Math.random() * 40)) * scale,
          vy: (vy / mag) * (speed * (40 + Math.random() * 40)) * scale,
          r: 2 + Math.random() * 2.5,
          born: performance.now(),
          life,
          huePick: Math.random()
        });
        if (particles.length > MAX_PARTICLES) particles.shift();
      }

      // Dibujar corazón neón
      function drawNeonHeart(cx, cy, outlinePoints, offsetX = 0, offsetY = 0, scaleOutline = 1) {
        ctx.save();
        ctx.translate(cx + offsetX, cy + offsetY);
        ctx.beginPath();
        for (let i = 0; i < outlinePoints.length; i++) {
          const p = outlinePoints[i];
          if (i === 0) ctx.moveTo(p.x * scaleOutline, p.y * scaleOutline);
          else ctx.lineTo(p.x * scaleOutline, p.y * scaleOutline);
        }
        ctx.closePath();

        const grad = ctx.createLinearGradient(-200, -200, 200, 200);
        grad.addColorStop(0, getNeon(0.0));
        grad.addColorStop(0.5, getNeon(0.5));
        grad.addColorStop(1, getNeon(1.0));

        ctx.strokeStyle = grad;
        ctx.lineWidth = 3;
        ctx.shadowColor = grad;
        ctx.shadowBlur = 25;
        ctx.stroke();

        ctx.shadowBlur = 0;
        ctx.lineWidth = 1.2;
        ctx.globalAlpha = 0.75;
        ctx.stroke();

        ctx.restore();
      }

      // Gradientes de color
      function getNeon(t) {
        if (t < 0.5) {
          const m = t / 0.5;
          return mix('#ff2bd6', '#a84dff', m);
        } else {
          const m = (t - 0.5) / 0.5;
          return mix('#a84dff', '#27e0ff', m);
        }
      }

      function mix(a, b, t) {
        const pa = hexToRgb(a), pb = hexToRgb(b);
        const r = Math.round(pa.r + (pb.r - pa.r) * t);
        const g = Math.round(pa.g + (pb.g - pa.g) * t);
        const b2 = Math.round(pa.b + (pb.b - pa.b) * t);
        return `rgb(${r},${g},${b2})`;
      }

      function hexToRgb(hex) {
        const v = parseInt(hex.replace('#', ''), 16);
        return { r: (v >> 16) & 255, g: (v >> 8) & 255, b: v & 255 };
      }

      // === ANIMACIÓN DE TEXTO DENTRO DEL CORAZÓN ===
      const lovePhrases = [
        "Para usted mi Amor Yorchi 💖",
        "Tu mirada es mi hogar 🌙",
        "Contigo, todo es amor ✨",
        "Eres mi niña hermosa 🌹",
        "Mi corazón late por ti 💓",
        "Eres mi paz y mi locura 💫",
        "Nada es más hermosa que tú 💎",
        "Eres mi eterno sueño 💭",
        "Te amo muchísimo más cada día 🌻",
        "Eres mi universo entero 🌌"
      ];

      let currentPhraseIndex = 0;
      let charIndex = 0;
      let isDeleting = false;
      const textSpeed = 100;
      const deleteSpeed = 50;
      const pauseTime = 1500;

      function typeWriter() {
        const currentPhrase = lovePhrases[currentPhraseIndex];
        if (isDeleting) {
          textEl.textContent = currentPhrase.substring(0, charIndex - 1);
          charIndex--;
        } else {
          textEl.textContent = currentPhrase.substring(0, charIndex + 1);
          charIndex++;
        }

        if (!isDeleting && charIndex === currentPhrase.length) {
          isDeleting = true;
          setTimeout(typeWriter, pauseTime);
          return;
        } else if (isDeleting && charIndex === 0) {
          isDeleting = false;
          currentPhraseIndex = (currentPhraseIndex + 1) % lovePhrases.length;
        }

        const speed = isDeleting ? deleteSpeed : textSpeed;
        setTimeout(typeWriter, speed);
      }

      // Mostrar texto con fade-in
      setTimeout(() => {
        textEl.style.opacity = 1;
        typeWriter();
      }, 1000);

      // Animación principal
      let last = performance.now();
      function tick(now) {
        const dt = now - last; last = now;

        ctx.fillStyle = 'rgba(0,0,0,0.20)';
        ctx.fillRect(0, 0, canvas.width, canvas.height);

        const cx = innerWidth / 2;
        const cy = innerHeight / 2;

        drawNeonHeart(cx, cy, outline, 0, 0, 1);
        drawNeonHeart(cx, cy, outlineSmall, 180, 120, 1);

        const spawnCount = 6;
        for (let i = 0; i < spawnCount; i++) {
          const p = outline[(Math.random() * outline.length) | 0];
          spawnParticle(p.x, p.y, 1);

          if (Math.random() > 0.6) {
            const pSmall = outlineSmall[(Math.random() * outlineSmall.length) | 0];
            spawnParticle(pSmall.x, pSmall.y, 0.6);
          }
        }

        for (let i = particles.length - 1; i >= 0; i--) {
          const p = particles[i];
          const age = now - p.born;
          if (age > p.life) {
            particles.splice(i, 1);
            continue;
          }

          const fade = 1 - age / p.life;
          p.x += p.vx * dt * 0.016;
          p.y += p.vy * dt * 0.016;

          ctx.save();
          ctx.translate(cx, cy);

          const neon = p.huePick < 0.33 ? '#ff2bd6' :
                      p.huePick < 0.66 ? '#a84dff' : '#27e0ff';

          ctx.fillStyle = neon;
          ctx.globalAlpha = Math.max(0, fade);
          ctx.shadowColor = neon;
          ctx.shadowBlur = 18;

          ctx.beginPath();
          ctx.arc(p.x, p.y, p.r * (0.5 + fade), 0, Math.PI * 2);
          ctx.fill();

          ctx.globalAlpha = Math.max(0, fade * 0.6);
          ctx.shadowBlur = 0;
          ctx.strokeStyle = neon;
          ctx.lineWidth = 1;
          ctx.beginPath();
          ctx.moveTo(p.x - p.vx * 0.08, p.y - p.vy * 0.08);
          ctx.lineTo(p.x, p.y);
          ctx.stroke();

          ctx.restore();
        }

        requestAnimationFrame(tick);
      }
      requestAnimationFrame(tick);

      // Interacción: clic → partículas
      const boom = (mx, my) => {
        mx -= innerWidth / 2;
        my -= innerHeight / 2;

        for (let i = 0; i < 120; i++) {
          particles.push({
            x: mx, y: my,
            vx: (Math.random() - 0.5) * 9,
            vy: (Math.random() - 0.5) * 9,
            r: 1.5 + Math.random() * 2,
            born: performance.now(),
            life: 500 + Math.random() * 600,
            huePick: Math.random()
          });
        }

        const smallX = mx + 180;
        const smallY = my + 120;
        for (let i = 0; i < 60; i++) {
          particles.push({
            x: smallX, y: smallY,
            vx: (Math.random() - 0.5) * 7,
            vy: (Math.random() - 0.5) * 7,
            r: 1 + Math.random() * 1.5,
            born: performance.now(),
            life: 400 + Math.random() * 500,
            huePick: Math.random()
          });
        }
      };

      canvas.addEventListener('click', e => boom(e.clientX, e.clientY));
      canvas.addEventListener('touchstart', e => {
        const t = e.touches[0];
        boom(t.clientX, t.clientY);
      }, { passive: true });

      // === MENÚ INTERACTIVO ===
      menuToggle.addEventListener('click', () => {
        menuPanel.classList.add('open');
      });

      closeMenu.addEventListener('click', () => {
        menuPanel.classList.remove('open');
      });

      document.addEventListener('click', (e) => {
        if (!menuPanel.contains(e.target) && !menuToggle.contains(e.target)) {
          menuPanel.classList.remove('open');
        }
      });

    })();
  </script>
</body>
</html>
