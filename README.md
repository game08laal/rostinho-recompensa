<!DOCTYPE html>
<html lang="pt-BR">
<head>
  <meta charset="UTF-8">
  <title>Robô de Recompensa</title>
  <style>
    body {
      background: #fff8dc;
      display: flex;
      justify-content: center;
      align-items: center;
      height: 100vh;
      margin: 0;
      overflow: hidden; /* para o confete não aparecer fora da tela */
    }

    .robo {
      width: 60vw;
      height: 70vh;
      background: linear-gradient(145deg, #FFD700, #FFC300);
      border-radius: 200px;
      position: relative;
      box-shadow: 0 8px 25px rgba(0,0,0,0.3), 0 0 40px rgba(255,215,0,0.6);
      animation: flutuar 2s ease-in-out infinite, concordar 2.5s ease-in-out infinite;
      z-index: 1;
    }

    @keyframes flutuar {
      0%, 100% { transform: translateY(0); }
      50% { transform: translateY(-5px); }
    }

    @keyframes concordar {
      0%, 5%   { transform: translateY(0); }
      10%      { transform: translateY(-15px); }
      15%      { transform: translateY(15px); }
      20%      { transform: translateY(-15px); }
      25%      { transform: translateY(0); }
      50%      { transform: translateY(0); }
      55%      { transform: translateY(-15px); }
      60%      { transform: translateY(15px); }
      65%      { transform: translateY(-15px); }
      70%      { transform: translateY(0); }
      100%     { transform: translateY(0); }
    }

    .olho {
      width: 22vh;
      height: 22vh;
      background: radial-gradient(circle at 30% 30%, #FFFFF0, #FFFACD);
      border-radius: 50%;
      position: absolute;
      top: 23%;
      box-shadow: 0 0 20px rgba(255, 255, 224, 0.8);
      animation: piscar 3s infinite, fecharOlhos 2.5s ease-in-out infinite;
      z-index: 2;
    }
    .olho.esq { left: 17%; }
    .olho.dir { right: 17%; }

    @keyframes piscar {
      0%, 90%, 100% { transform: scaleY(1); }
      95% { transform: scaleY(0.1); }
    }

    @keyframes fecharOlhos {
      0%, 5%   { transform: scaleY(1); }
      10%, 20% { transform: scaleY(0.6); }
      25%      { transform: scaleY(1); }
      55%, 65% { transform: scaleY(0.6); }
      70%      { transform: scaleY(1); }
      100%     { transform: scaleY(1); }
    }

    .boca {
      width: 200px;
      height: 100px;
      background: #FFFACD;
      border-radius: 0 0 150px 150px;
      position: absolute;
      bottom: 18%;
      left: 50%;
      transform: translateX(-50%);
      box-shadow: 0 0 20px rgba(255, 250, 205, 0.8);
      z-index: 2;
    }

    /* confete dourado */
    .confete {
      width: 8px;
      height: 14px;
      background: linear-gradient(45deg, #FFD700, #FFFACD);
      position: absolute;
      top: -20px;
      border-radius: 2px;
      opacity: 0.8;
      animation: cair linear infinite;
    }

    @keyframes cair {
      0% {
        transform: translateY(0) rotate(0deg);
        opacity: 1;
      }
      100% {
        transform: translateY(100vh) rotate(360deg);
        opacity: 0;
      }
    }

  </style>
</head>
<body>
  <div class="robo">
    <div class="olho esq"></div>
    <div class="olho dir"></div>
    <div class="boca"></div>
  </div>

  <!-- gerar múltiplos confetes -->
  <script>
    const numConfetes = 50;
    for (let i = 0; i < numConfetes; i++) {
      const confete = document.createElement('div');
      confete.classList.add('confete');
      confete.style.left = Math.random() * 100 + 'vw';
      confete.style.animationDuration = (2 + Math.random() * 3) + 's';
      confete.style.animationDelay = Math.random() * 5 + 's';
      confete.style.width = 5 + Math.random() * 10 + 'px';
      confete.style.height = 10 + Math.random() * 20 + 'px';
      document.body.appendChild(confete);
    }
  </script>
</body>
</html>

