<!DOCTYPE html>
<html lang="pt-BR">
<head>
  <meta charset="UTF-8">
  <title>Pergunta Sim ou Não</title>
  <style>
    body {
      display: flex;
      flex-direction: column;
      align-items: center;
      justify-content: center;
      height: 100vh;
      font-family: sans-serif;
      background-color: #f0f0f0;
    }
    h1 {
      margin-bottom: 130px;
    }
    .btn-container {
      position: relative;
      width: 200px;
      height: 1000px;
    }
    button {
      width: 100px;
      height: 100px;
      margin: 0 100px;
      font-size: 1rem;
      cursor: pointer;
      position: absolute;
      top: 50%;
      transform: translateY(-50%);
      transition: all 0.2s ease;
    }
    #yes {
      left: 0;
    }
    #no {
      right: 0;
    }
  </style>
</head>
<body>

  <h1>Você me ama?</h1>
  <div class="btn-container">
    <button id="yes">Sim meu melhor funcionário</button>
    <button id="no">Não</button>
  </div>

  <script>
    const noBtn = document.getElementById('no');
    const container = document.querySelector('.btn-container');

    container.addEventListener('mousemove', (e) => {
      const rect = noBtn.getBoundingClientRect();
      const mouseX = e.clientX;
      const mouseY = e.clientY;

      const dx = mouseX - (rect.left + rect.width / 2);
      const dy = mouseY - (rect.top + rect.height / 2);
      const distance = Math.hypot(dx, dy);

      if (distance < 80) {
        const angle = Math.atan2(dy, dx);
        const moveX = Math.cos(angle) * 100;
        const moveY = Math.sin(angle) * 130;
        const newLeft = Math.min(
          container.clientWidth - rect.width,
          Math.max(0, rect.left - container.getBoundingClientRect().left - moveX)
        );
        const newTop = Math.min(
          container.clientHeight - rect.height,
          Math.max(0, rect.top - container.getBoundingClientRect().top - moveY)
        );
        noBtn.style.left = `${newLeft}px`;
        noBtn.style.top = `${newTop}px`;
      }
    });

    noBtn.addEventListener('click', () => {
      alert('Nem chega perto!');
    });

    document.getElementById('yes').addEventListener('click', () => {
      alert('melhorias
            trabalho em equipe +32%
        produtividade +40%
        conversinhas -23%');
    });
  </script>

</body>
</html>
