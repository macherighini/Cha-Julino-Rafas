<!DOCTYPE html>
<html lang="pt-BR">
<head>
  <meta charset="UTF-8" />
  <meta name="viewport" content="width=device-width, initial-scale=1.0" />
  <title>Chá Julino Rafaela e Rafael</title>
  <style>
    body {
      font-family: 'Segoe UI', sans-serif;
      background-color: #171a4a;
      color: #f1f1f1;
      margin: 0;
      padding: 20px;
      background-image: radial-gradient(#ffd70033 1px, transparent 1px);
      background-size: 40px 40px;
    }
    header {
      text-align: center;
      margin-bottom: 30px;
    }
    header img {
      width: 150px;
      margin-bottom: 10px;
    }
    h1 {
      color: #ffd700;
      font-size: 2.5rem;
    }
    h2 {
      margin-top: 30px;
      border-bottom: 2px solid #ffd700;
      padding-bottom: 5px;
      color: #ffe066;
    }
    ul {
      list-style: none;
      padding-left: 0;
    }
    li {
      background-color: #1b263b;
      border: 1px solid #415a77;
      margin: 8px 0;
      padding: 12px;
      border-radius: 10px;
      display: flex;
      justify-content: space-between;
      align-items: center;
      box-shadow: 0 0 10px #ffd70033;
    }
    button {
      background-color: #ffd700;
      color: #0d1b2a;
      font-weight: bold;
      border: none;
      padding: 6px 12px;
      border-radius: 5px;
      cursor: pointer;
      transition: background-color 0.3s;
    }
    button:hover:not(:disabled) {
      background-color: #ffcc00;
    }
    button:disabled {
      background-color: #888;
      color: #ccc;
      cursor: not-allowed;
    }
    .cadastro {
      margin: 30px auto;
      max-width: 400px;
      padding: 20px;
      background-color: #1b263b;
      border-radius: 10px;
      box-shadow: 0 0 15px #ffd70055;
    }
    .cadastro h2 {
      text-align: center;
    }
    .cadastro input {
      width: 100%;
      padding: 10px;
      margin: 10px 0;
      border-radius: 5px;
      border: none;
      font-size: 1rem;
    }
    .cadastro button {
      width: 100%;
      margin-top: 10px;
    }
    .disabled {
      pointer-events: none;
      opacity: 0.5;
    }
  </style>
</head>
<body>
  <header>
    <img src="/mnt/data/0357efe5-6fa7-4f9d-9fa7-30e3c5f1847c.jpeg" alt="Logo R&R">
    <h1>Chá Julino Rafaela e Rafael</h1>
  </header>

  <div class="cadastro">
    <h2>Faça seu cadastro</h2>
    <input type="text" id="nome" placeholder="Nome completo" />
    <input type="email" id="email" placeholder="Email" />
    <input type="tel" id="telefone" placeholder="Celular" />
    <button onclick="registrarUsuario()">Cadastrar</button>
  </div>

  <div id="listas" class="disabled">
    <h2>Cozinha</h2>
    <ul id="cozinha"></ul>

    <h2>Banheiro</h2>
    <ul id="banheiro"></ul>

    <h2>Sala</h2>
    <ul id="sala"></ul>
  </div>

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
      ],
    };

    function renderList(categoria, containerId) {
      const ul = document.getElementById(containerId);
      listaPresentes[categoria].forEach((item) => {
        const li = document.createElement("li");
        const button = document.createElement("button");
        button.textContent = "Escolher";
        button.onclick = () => {
          button.disabled = true;
          button.textContent = "Escolhido";
        };
        li.innerHTML = `<span>${item}</span>`;
        li.appendChild(button);
        ul.appendChild(li);
      });
    }

    function registrarUsuario() {
      const nome = document.getElementById("nome").value.trim();
      const email = document.getElementById("email").value.trim();
      const telefone = document.getElementById("telefone").value.trim();

      if (nome && email && telefone) {
        document.querySelector(".cadastro").classList.add("disabled");
        document.getElementById("listas").classList.remove("disabled");
        renderList("cozinha", "cozinha");
        renderList("banheiro", "banheiro");
        renderList("sala", "sala");
      } else {
        alert("Por favor, preencha todos os campos para continuar.");
      }
    }
  </script>
</body>
</html>
