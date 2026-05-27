# BOTINACOPA
<!DOCTYPE html>
<html lang="pt-BR">
<head>
  <meta charset="UTF-8" />
  <meta name="viewport" content="width=device-width, initial-scale=1.0" />
  <title>Chuta e Ganha | Brinde Premiado</title>

  <style>
    * {
      margin: 0;
      padding: 0;
      box-sizing: border-box;
      font-family: Arial, Helvetica, sans-serif;
    }

    body {
      min-height: 100vh;
      background: radial-gradient(circle at top, #16a34a 0%, #065f46 45%, #022c22 100%);
      display: flex;
      justify-content: center;
      align-items: center;
      padding: 20px;
      color: #fff;
      overflow-x: hidden;
    }

    .app {
      width: 100%;
      max-width: 500px;
      background: rgba(255, 255, 255, 0.12);
      border: 1px solid rgba(255, 255, 255, 0.22);
      border-radius: 28px;
      padding: 22px;
      box-shadow: 0 25px 70px rgba(0, 0, 0, 0.35);
      backdrop-filter: blur(12px);
      text-align: center;
      position: relative;
      overflow: hidden;
    }

    .badge {
      display: inline-block;
      background: #fff;
      color: #047857;
      padding: 7px 14px;
      border-radius: 999px;
      font-size: 12px;
      font-weight: 800;
      letter-spacing: 0.5px;
      margin-bottom: 14px;
      text-transform: uppercase;
    }

    h1 {
      font-size: 34px;
      line-height: 1.02;
      margin-bottom: 10px;
      text-transform: uppercase;
      text-shadow: 0 4px 12px rgba(0, 0, 0, 0.28);
    }

    .subtitle {
      font-size: 15px;
      line-height: 1.45;
      opacity: 0.95;
      margin-bottom: 18px;
    }

    .gift-box {
      background: linear-gradient(135deg, #facc15, #f97316);
      color: #321200;
      border-radius: 22px;
      padding: 15px;
      margin-bottom: 20px;
      font-weight: 900;
      box-shadow: 0 12px 30px rgba(250, 204, 21, 0.22);
    }

    .gift-box small {
      display: block;
      font-size: 12px;
      text-transform: uppercase;
      letter-spacing: 0.5px;
      margin-bottom: 3px;
    }

    .gift-box span {
      display: block;
      font-size: 25px;
      line-height: 1.1;
    }

    .field-area {
      height: 330px;
      background: linear-gradient(180deg, #16a34a 0%, #15803d 100%);
      border-radius: 28px;
      position: relative;
      overflow: hidden;
      border: 3px solid rgba(255, 255, 255, 0.3);
      margin-bottom: 18px;
      touch-action: none;
    }

    .field-area::before {
      content: "";
      position: absolute;
      inset: 0;
      background-image:
        linear-gradient(rgba(255,255,255,0.12) 2px, transparent 2px),
        linear-gradient(90deg, rgba(255,255,255,0.12) 2px, transparent 2px);
      background-size: 44px 44px;
      opacity: 0.45;
    }

    .goal {
      position: absolute;
      top: 20px;
      left: 50%;
      transform: translateX(-50%);
      width: 230px;
      height: 115px;
      border: 8px solid #fff;
      border-bottom: none;
      border-radius: 12px 12px 0 0;
      z-index: 2;
    }

    .goal::after {
      content: "";
      position: absolute;
      inset: 0;
      background-image:
        linear-gradient(rgba(255,255,255,0.35) 1px, transparent 1px),
        linear-gradient(90deg, rgba(255,255,255,0.35) 1px, transparent 1px);
      background-size: 18px 18px;
    }

    .target-label {
      position: absolute;
      top: 133px;
      left: 50%;
      transform: translateX(-50%);
      font-size: 11px;
      font-weight: 800;
      background: rgba(255,255,255,0.18);
      padding: 6px 10px;
      border-radius: 999px;
      z-index: 4;
    }

    .target-rail {
      position: absolute;
      top: 162px;
      left: 14px;
      right: 14px;
      height: 2px;
      border-top: 2px dashed rgba(255,255,255,0.55);
      z-index: 3;
    }

    .target-marker {
      position: absolute;
      top: -10px;
      left: 50%;
      width: 22px;
      height: 22px;
      border-radius: 50%;
      background: #facc15;
      border: 3px solid #fff;
      box-shadow: 0 0 0 5px rgba(250, 204, 21, 0.25);
      transform: translateX(-50%);
      cursor: grab;
    }

    .keeper {
      position: absolute;
      top: 89px;
      left: 50%;
      transform: translateX(-50%);
      width: 54px;
      height: 54px;
      font-size: 48px;
      z-index: 5;
      user-select: none;
      pointer-events: none;
      filter: drop-shadow(0 8px 10px rgba(0,0,0,0.35));
      animation: gloveMove 1.15s linear infinite alternate;
    }

    @keyframes gloveMove {
      0% {
        left: calc(50% - 82px);
        transform: translateX(-50%) rotate(-10deg);
      }
      50% {
        transform: translateX(-50%) rotate(8deg);
      }
      100% {
        left: calc(50% + 82px);
        transform: translateX(-50%) rotate(10deg);
      }
    }

    .keeper.defense {
      animation: defensePulse 0.45s ease-in-out, gloveMove 1.15s linear infinite alternate;
    }

    @keyframes defensePulse {
      0% { transform: translateX(-50%) scale(1) rotate(0deg); }
      50% { transform: translateX(-50%) scale(1.25) rotate(-12deg); }
      100% { transform: translateX(-50%) scale(1) rotate(0deg); }
    }

    .ball {
      position: absolute;
      bottom: 24px;
      left: 50%;
      transform: translateX(-50%);
      width: 66px;
      height: 66px;
      border-radius: 50%;
      background: #fff;
      border: 3px solid #111827;
      z-index: 6;
      box-shadow: 0 12px 22px rgba(0,0,0,0.35);
      display: flex;
      justify-content: center;
      align-items: center;
      font-size: 38px;
      user-select: none;
      pointer-events: none;
    }

    .power-box {
      margin-bottom: 12px;
      text-align: left;
    }

    .power-label {
      display: flex;
      justify-content: space-between;
      font-size: 12px;
      font-weight: 800;
      margin-bottom: 6px;
      padding: 0 2px;
    }

    .power-bar {
      width: 100%;
      height: 16px;
      background: rgba(255,255,255,0.2);
      border-radius: 999px;
      overflow: hidden;
      border: 1px solid rgba(255,255,255,0.25);
    }

    .power-fill {
      height: 100%;
      width: 0%;
      background: linear-gradient(90deg, #22c55e, #facc15, #ef4444);
      border-radius: 999px;
      transition: width 0.05s linear;
    }

    .kick-btn {
      width: 100%;
      border: none;
      background: #facc15;
      color: #1f2937;
      padding: 16px;
      border-radius: 18px;
      font-size: 16px;
      font-weight: 900;
      cursor: pointer;
      margin-bottom: 12px;
      box-shadow: 0 12px 25px rgba(0,0,0,0.22);
      touch-action: none;
      user-select: none;
    }

    .kick-btn.disabled {
      opacity: 0.6;
      cursor: not-allowed;
    }

    .hint {
      font-size: 12px;
      line-height: 1.4;
      margin-bottom: 14px;
      opacity: 0.92;
    }

    .status {
      min-height: 44px;
      display: flex;
      align-items: center;
      justify-content: center;
      text-align: center;
      font-weight: 900;
      font-size: 15px;
      margin-bottom: 12px;
      padding: 0 10px;
    }

    .result-box {
      display: none;
      background: #fff;
      color: #111827;
      border-radius: 24px;
      padding: 20px;
      margin-top: 16px;
      text-align: center;
      animation: fadeUp 0.5s ease forwards;
    }

    @keyframes fadeUp {
      from { transform: translateY(20px); opacity: 0; }
      to { transform: translateY(0); opacity: 1; }
    }

    .result-box h2 {
      font-size: 26px;
      margin-bottom: 8px;
      color: #047857;
    }

    .result-box p {
      font-size: 15px;
      color: #374151;
      line-height: 1.45;
      margin-bottom: 14px;
    }

    .gift-name {
      background: #ecfdf5;
      border: 1px dashed #10b981;
      color: #065f46;
      border-radius: 16px;
      padding: 14px;
      font-weight: 900;
      font-size: 18px;
      margin-bottom: 12px;
    }

    .rules {
      font-size: 11px;
      color: #6b7280;
      margin-top: 12px;
      line-height: 1.35;
      text-align: center;
    }

    .confetti {
      position: fixed;
      top: -10px;
      width: 10px;
      height: 10px;
      animation: fall 2.6s linear forwards;
      z-index: 9999;
    }

    @keyframes fall {
      to {
        transform: translateY(110vh) rotate(720deg);
        opacity: 0;
      }
    }

    .footer-note {
      margin-top: 14px;
      font-size: 12px;
      opacity: 0.86;
      line-height: 1.4;
      position: relative;
      z-index: 2;
    }

    .logo-programa {
      position: absolute;
      right: 14px;
      top: 14px;
      opacity: 0.18;
      z-index: 1;
      pointer-events: none;
      font-size: 13px;
      font-weight: 900;
      letter-spacing: 1.4px;
      color: rgba(255, 255, 255, 0.9);
      text-transform: uppercase;
      text-shadow: 0 2px 8px rgba(0,0,0,0.35);
    }

    .created-by {
      position: absolute;
      left: 14px;
      bottom: 10px;
      opacity: 0.32;
      z-index: 1;
      pointer-events: none;
      font-size: 10px;
      font-weight: 700;
      letter-spacing: 0.4px;
      color: rgba(255, 255, 255, 0.92);
      text-shadow: 0 2px 8px rgba(0,0,0,0.35);
    }

    @media (max-width: 480px) {
      h1 {
        font-size: 29px;
      }

      .goal {
        width: 195px;
      }
    }
  </style>
</head>

<body>
  <main class="app">
    <div class="badge">Campanha exclusiva</div>
    <h1>Chuta<br />e Ganha</h1>
    <p class="subtitle">
      Mire no gol, segure para carregar a força e tente marcar. Cuidado: a luva se mexe!
    </p>

    <div class="gift-box">
      <small>GOL DA COPA</small>
      <span>Faça o gol<br />e ganhe um brinde</span>
    </div>

    <section class="field-area" id="fieldArea">
      <div class="goal" id="goal"></div>
      <div class="keeper" id="keeper">🧤</div>
      <div class="target-label">Arraste a mira</div>
      <div class="target-rail" id="targetRail">
        <div class="target-marker" id="targetMarker"></div>
      </div>
      <div class="ball" id="ball">⚽</div>
    </section>

    <div class="power-box">
      <div class="power-label">
        <span>Força do chute</span>
        <span id="powerText">0%</span>
      </div>
      <div class="power-bar">
        <div class="power-fill" id="powerFill"></div>
      </div>
    </div>

    <button class="kick-btn" id="kickBtn">Segure para carregar e solte para chutar</button>

    <div class="hint">
      1. Arraste a mira para escolher a direção.<br>
      2. Segure o botão para carregar a força.<br>
      3. Solte no momento certo e fuja da luva.
    </div>

    <div class="status" id="statusMessage">Você tem apenas 1 chance. Faça o gol para liberar seu brinde.</div>

    <section class="result-box" id="resultBox">
      <h2>GOOOOL! 🎉</h2>
      <p>Você ganhou um brinde!</p>
      <p>Mande esse print para seu supervisor para resgatar.</p>
      <div class="rules">
        Promoção sujeita à confirmação do pedido realizado. O nome do brinde pode ser alterado pela equipe responsável.
      </div>
    </section>

    <div class="footer-note">
      Atenção: cada acesso permite apenas 1 chute. Se errar, será necessário abrir o link novamente.
    </div>

    <div class="logo-programa">CP MR ALVES</div>
    <div class="created-by">Created by Pablo Kallyan Batista</div>
  </main>

  <script>
    const fieldArea = document.getElementById("fieldArea");
    const goal = document.getElementById("goal");
    const keeper = document.getElementById("keeper");
    const ball = document.getElementById("ball");
    const targetRail = document.getElementById("targetRail");
    const targetMarker = document.getElementById("targetMarker");
    const kickBtn = document.getElementById("kickBtn");
    const powerFill = document.getElementById("powerFill");
    const powerText = document.getElementById("powerText");
    const statusMessage = document.getElementById("statusMessage");
    const resultBox = document.getElementById("resultBox");

    let aiming = false;
    let charging = false;
    let shooting = false;
    let unlocked = false;
    let alreadyKicked = false;

    let power = 0;
    let powerDirection = 1;
    let chargeInterval = null;

    let keeperPos = 0;
    let keeperDirection = 1;
    let keeperPaused = false;
    let keeperSpeed = 2.4;

    function createConfetti() {
      for (let i = 0; i < 55; i++) {
        const confetti = document.createElement("div");
        confetti.classList.add("confetti");
        confetti.style.left = Math.random() * 100 + "vw";
        confetti.style.background = ["#facc15", "#22c55e", "#ffffff", "#fb7185", "#38bdf8"][Math.floor(Math.random() * 5)];
        confetti.style.animationDelay = Math.random() * 0.6 + "s";
        confetti.style.width = Math.random() * 8 + 6 + "px";
        confetti.style.height = Math.random() * 8 + 6 + "px";
        document.body.appendChild(confetti);
        setTimeout(() => confetti.remove(), 3000);
      }
    }

    function clamp(value, min, max) {
      return Math.max(min, Math.min(max, value));
    }

    function setTargetFromClientX(clientX) {
      const rect = targetRail.getBoundingClientRect();
      const x = clamp(clientX - rect.left, 0, rect.width);
      targetMarker.style.left = x + "px";
    }

    targetRail.addEventListener("pointerdown", (e) => {
      if (shooting || unlocked) return;
      aiming = true;
      setTargetFromClientX(e.clientX);
    });

    window.addEventListener("pointermove", (e) => {
      if (!aiming || shooting || unlocked) return;
      setTargetFromClientX(e.clientX);
    });

    window.addEventListener("pointerup", () => {
      aiming = false;
    });

    function moveKeeper() {
      // A movimentação da luva agora é feita por CSS para funcionar melhor no celular.
    }

    function initKeeper() {
      // Mantido apenas para compatibilidade com o restante do código.
    }

    function startCharge(e) {
      if (shooting || unlocked || alreadyKicked) return;
      e.preventDefault();

      charging = true;
      power = 0;
      powerDirection = 1;
      updatePowerUI();
      statusMessage.textContent = "Carregando força... solte para chutar!";
      kickBtn.classList.remove("disabled");

      chargeInterval = setInterval(() => {
        power += powerDirection * 4;

        if (power >= 100) {
          power = 100;
          powerDirection = -1;
        } else if (power <= 0) {
          power = 0;
          powerDirection = 1;
        }

        updatePowerUI();
      }, 40);
    }

    function endCharge(e) {
      if (!charging || shooting || unlocked) return;
      e.preventDefault();

      clearInterval(chargeInterval);
      charging = false;
      shootBall();
    }

    function updatePowerUI() {
      powerFill.style.width = power + "%";
      powerText.textContent = Math.round(power) + "%";
    }

    kickBtn.addEventListener("pointerdown", startCharge);
    kickBtn.addEventListener("pointerup", endCharge);
    kickBtn.addEventListener("pointerleave", (e) => {
      if (charging) endCharge(e);
    });
    kickBtn.addEventListener("pointercancel", (e) => {
      if (charging) endCharge(e);
    });

    function resetBall() {
      ball.style.left = "50%";
      ball.style.bottom = "24px";
      ball.style.transform = "translateX(-50%)";
    }

    function getTargetXInField() {
      return targetMarker.offsetLeft + (targetMarker.offsetWidth / 2);
    }

    function shootBall() {
      shooting = true;
      kickBtn.classList.add("disabled");
      statusMessage.textContent = "Chutando...";

      const fieldRect = fieldArea.getBoundingClientRect();
      const startX = fieldRect.width / 2;
      const startY = fieldRect.height - 55;
      const targetX = getTargetXInField();
      const targetY = 145;
      const duration = 650;
      const startTime = performance.now();

      function animate(now) {
        const elapsed = now - startTime;
        const t = Math.min(elapsed / duration, 1);

        const x = startX + (targetX - startX) * t;
        const yLinear = startY + (targetY - startY) * t;
        const arc = Math.sin(t * Math.PI) * (70 + power * 0.25);
        const y = yLinear - arc;

        ball.style.left = x + "px";
        ball.style.bottom = (fieldRect.height - y) + "px";
        ball.style.transform = `translateX(-50%) rotate(${t * 720}deg)`;

        if (t < 1) {
          requestAnimationFrame(animate);
        } else {
          finishShot(targetX);
        }
      }

      requestAnimationFrame(animate);
    }

    function finishShot(targetX) {
      alreadyKicked = true;
      const goalRect = goal.getBoundingClientRect();
      const fieldRect = fieldArea.getBoundingClientRect();

      const goalLeft = goalRect.left - fieldRect.left + 10;
      const goalRight = goalRect.right - fieldRect.left - 10;
      const keeperRect = keeper.getBoundingClientRect();
      const keeperCenter = keeperRect.left - fieldRect.left + keeperRect.width / 2;

      const insideGoal = targetX >= goalLeft && targetX <= goalRight;
      const enoughPower = power >= 30;
      const tooStrong = power > 92;
      const defended = Math.abs(targetX - keeperCenter) <= 36;
      const nearPostHarder = Math.abs(targetX - goalLeft) < 10 || Math.abs(targetX - goalRight) < 10;

      let result = "goal";

      if (!enoughPower) {
        result = "weak";
      } else if (tooStrong && Math.random() < 0.45) {
        result = "miss";
      } else if (!insideGoal) {
        result = "miss";
      } else if (defended) {
        result = "saved";
      } else if (nearPostHarder && power < 45) {
        result = "miss";
      }

      if (result === "goal") {
        unlocked = true;
        keeperPaused = true;
        statusMessage.textContent = "GOOOOL! Você ganhou um brinde 🎉";
        createConfetti();
        setTimeout(() => {
          resultBox.style.display = "block";
          resultBox.scrollIntoView({ behavior: "smooth", block: "start" });
        }, 700);
      } else {
        if (result === "weak") {
          statusMessage.textContent = "Chute fraco! Segure mais tempo para carregar.";
        } else if (result === "miss") {
          statusMessage.textContent = "Pra fora! Ajuste a mira e tente novamente.";
        } else if (result === "saved") {
          keeper.classList.add("defense");
          statusMessage.textContent = "A luva defendeu! Tente chutar no canto.";
          setTimeout(() => keeper.classList.remove("defense"), 500);
        }

        setTimeout(() => {
          power = 0;
          updatePowerUI();
          shooting = false;
          kickBtn.classList.add("disabled");
          kickBtn.textContent = "Chance usada. Abra o link novamente.";
          statusMessage.textContent += " Abra o link novamente para tentar outra vez.";
        }, 1000);

        return;
      }

      shooting = false;
      kickBtn.classList.add("disabled");
    }

    window.addEventListener("load", () => {
      resetBall();
    });

    window.addEventListener("resize", () => {
      initKeeper();
    });
  </script>
</body>
</html>
