<!DOCTYPE html>
<html lang="pt-BR">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>Chá Julino Rafaela e Rafael</title>
  <style>
    body {
      margin: 0;
      padding: 0;
      font-family: 'Segoe UI', sans-serif;
      background-color: #171a4a;
      color: #fff;
      overflow-x: hidden;
    }
    header {
      text-align: center;
      padding: 30px 20px;
      position: relative;
    }
    header img {
      width: 120px;
      height: auto;
    }
    h1 {
      font-size: 2.5rem;
      color: #ffd700;
      margin: 10px 0 0 0;
    }
    .glow {
      position: absolute;
      top: 0;
      left: 0;
      width: 100%;
      height: 100%;
      background: radial-gradient(circle, rgba(255,215,0,0.15) 1px, transparent 1px);
      background-size: 50px 50px;
      pointer-events: none;
      z-index: 0;
    }
    main {
      padding: 20px;
      max-width: 700px;
      margin: 0 auto;
    }
    h2 {
      color: #ffe066;
      border-bottom: 2px solid #ffd700;
      padding-bottom: 5px;
    }
    ul {
      list-style: none;
      padding: 0;
    }
    li {
      background-color: #1b1f4a;
      border: 1px solid #ffd70055;
      margin-bottom: 10px;
      padding: 12px;
      border-radius: 8px;
      display: flex;
      justify-content: space-between;
      align-items: center;
      box-shadow: 0 0 10px #ffd70033;
    }
    button {
      background-color: #ffd700;
      color: #171a4a;
      border: none;
      padding: 8px 12px;
      border-radius: 5px;
      font-weight: bold;
      cursor: pointer;
    }
    button:disabled {
      background-color: #888;
      color: #ccc;
      cursor: not-allowed;
    }
    .cadastro {
      margin-bottom: 30px;
      background-color: #1b1f4a;
      padding: 20px;
      border-radius: 10px;
      box-shadow: 0 0 15px #ffd70044;
    }
    .cadastro label {
      display: block;
      margin: 10px 0 5px;
      font-weight: bold;
    }
    .cadastro input {
      width: 100%;
      padding: 8px;
      border-radius: 5px;
      border: 1px solid #ccc;
    }
  </style>
</head>
<body>
  <div class="glow"></div>
  <header>
    <img src="WhatsApp%20Image%202025-06-16%20at%2020.34.09.jpeg" alt="Logo RR">
    <h1>Chá Julino Rafaela e Rafael</h1>
  </header>

  <main>
    <div class="cadastro">
      <h2>Identifique-se para escolher um presente 🎁</h2>
      <label for="nome">Nome:</label>
      <input type="text" id="nome">
      <label for="email">Email:</label>
      <input type="email" id="email">
      <label for="celular">Celular:</label>
      <input type="tel" id="celular">
      <br><br>
      <button onclick="liberarEscolhas()">Confirmar</button>
    </div>

    <h2>Cozinha</h2>
    <ul id="cozinha"></ul>

    <h2>Banheiro</h2>
    <ul id="banheiro"></ul>

    <h2>Sala</h2>
    <ul id="sala"></ul>
  </main>

  <script>
    const listaPresentes = {
      cozinha: [
        "Kit utensilios de cozinha silicone",
        "Conjunto de panelas",
        "Porta tempero",
        "Ralador de queijo",
        "Jogo de sobremesa",
        "Escorredor de louça",
        "Porta detergente e bucha",
        "Toalha de mesa",
        "Forma de bolo",
        "Forma",
        "Mesa de jantar",
        "Kit facas",
        "Puxa saco",
        "Porta papel filme, papel alumínio e papel toalha",
        "Kit churrasco",
        "Açucareiro",
        "Saleiro",
      ],
      banheiro: [
        "Cesto de lixo",
        "Tapete de banheiro",
        "Jogo de toalhas",
        "Porta sabão líquido",
        "Porta escova de dente",
      ],
      sala: [
        "Banquetas",
        "Almofadas",
        "Cadeira",
        "Rede",
        "Quadro decorativo",
      ]
    };

    function renderList(categoria, containerId) {
      const ul = document.getElementById(containerId);
      listaPresentes[categoria].forEach((item) => {
        const li = document.createElement("li");
        const btn = document.createElement("button");
        btn.textContent = "Escolher";
        btn.disabled = true;
        btn.onclick = function () {
          btn.textContent = "Escolhido";
          btn.disabled = true;
        };
        li.innerHTML = `<span>${item}</span>`;
        li.appendChild(btn);
        ul.appendChild(li);
      });
    }

    function liberarEscolhas() {
      const nome = document.getElementById('nome').value.trim();
      const email = document.getElementById('email').value.trim();
      const celular = document.getElementById('celular').value.trim();

      if (nome && email && celular) {
        document.querySelectorAll('button').forEach(btn => {
          if (btn.textContent === 'Escolher') {
            btn.disabled = false;
          }
        });
        alert('Cadastro realizado com sucesso! Agora você pode escolher um presente.');
      } else {
        alert('Por favor, preencha todos os campos para continuar.');
      }
    }

    renderList("cozinha", "cozinha");
    renderList("banheiro", "banheiro");
    renderList("sala", "sala");
  </script>
</body>
</html>
