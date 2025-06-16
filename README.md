
    /* Luzes douradas estilo Enrolados (animação suave) */
    body::before {
      content: "";
      position: fixed;
      top: 0; left: 0; right: 0; bottom: 0;
      background: radial-gradient(circle at 20% 30%, #ffd70088 8px, transparent 10px),
                  radial-gradient(circle at 50% 50%, #ffd70066 6px, transparent 8px),
                  radial-gradient(circle at 80% 70%, #ffd700aa 7px, transparent 9px);
      background-repeat: repeat;
      background-size: 100px 100px;
      animation: twinkle 5s infinite alternate;
      pointer-events: none;
      z-index: 0;
    }

    @keyframes twinkle {
      0% { filter: brightness(1); }
      100% { filter: brightness(1.5); }
    }

    /* Container principal por cima das luzes */
    main {
      position: relative;
      z-index: 1;
      max-width: 700px;
      margin: 0 auto;
      background-color: #12233fdd; /* azul marinho semitransparente */
      padding: 30px;
      border-radius: 15px;
      box-shadow: 0 0 30px #ffd700aa;
    }

    header {
      text-align: center;
      margin-bottom: 30px;
    }

    header img {
      width: 150px;
      margin-bottom: 10px;
    }

    /* Título com fonte cursiva e sombra dourada */
    h1 {
      font-family: 'Great Vibes', cursive;
      font-size: 3.5rem;
      color: #ffd700;
      text-shadow: 0 0 10px #ffd700cc;
      margin-bottom: 10px;
    }

    h2 {
      margin-top: 30px;
      border-bottom: 2px solid #ffd700;
      padding-bottom: 5px;
      color: #ffe066;
      font-weight: 600;
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
      font-weight: 500;
    }

    button {
      background-color: #ffd700;
      color: #0d1b2a;
      font-weight: bold;
      border: none;
      padding: 6px 14px;
      border-radius: 5px;
      cursor: pointer;
      transition: background-color 0.3s;
      user-select: none;
    }

    button:hover:not(:disabled) {
      background-color: #ffcc00;
    }

    button:disabled {
      background-color: #888;
      color: #ccc;
      cursor: not-allowed;
    }

    .recados {
      margin-top: 40px;
    }

    textarea {
      width: 100%;
      height: 100px;
      padding: 10px;
      border-radius: 8px;
      border: 1px solid #ccc;
      resize: none;
      font-family: inherit;
      font-size: 1rem;
    }

    .mensagens {
      margin-top: 20px;
      max-height: 200px;
      overflow-y: auto;
    }

    .mensagem {
      background-color: #1b263b;
      border-left: 4px solid #ffd700;
      padding: 10px;
      margin-bottom: 10px;
      border-radius: 6px;
      font-size: 1rem;
      color: #f1f1f1;
    }
  </style>
</head>
<body>
  <audio autoplay loop>
    <source src="https://www.dropbox.com/scl/fi/j1f0dj6d4g0z5t0e7n04x/Ed-Sheeran-Perfect.mp3?rlkey=kgvd2l8coyzk4s7ru1wv56uzd&dl=1" type="audio/mpeg" />
    Seu navegador não suporta áudio.
  </audio>

  <main>
    <header>
      <img src="https://via.placeholder.com/150x150/0d1b2a/ffd700?text=R%26R" alt="Logo R&R" />
      <h1>Chá Julino Rafaela e Rafael</h1>
    </header>

    <h2>Cozinha</h2>
    <ul id="cozinha"></ul>

    <h2>Banheiro</h2>
    <ul id="banheiro"></ul>

    <h2>Sala</h2>
    <ul id="sala"></ul>

    <section class="recados">
      <h2>Deixe seu recado para os noivos 💌</h2>
      <textarea id="mensagem" placeholder="Escreva aqui sua mensagem..."></textarea><br />
      <button onclick="enviarMensagem()">Enviar</button>
      <div class="mensagens" id="mensagens"></div>
    </section>
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
      ],
    };

    // Renderiza os presentes com botões
    function renderList(categoria, containerId) {
      const ul = document.getElementById(containerId);
      listaPresentes[categoria].forEach((item) => {
        const li = document.createElement("li");
        li.innerHTML = `
          <span>${item}</span>
          <button onclick="marcarEscolhido(this)">Escolher</button>
        `;
        ul.appendChild(li);
      });
    }

    // Marca o presente como escolhido (botão desabilitado e texto trocado)
    function marcarEscolhido(button) {
      button.disabled = true;
      button.textContent = "Escolhido";
    }

    // Envia recado, adiciona na lista e limpa textarea
    function enviarMensagem() {
      const textarea = document.getElementById("mensagem");
      const mensagem = textarea.value.trim();
      if (mensagem) {
        const div = document.createElement("div");
        div.className = "mensagem";
        div.textContent = mensagem;
        document.getElementById("mensagens").appendChild(div);
        textarea.value = "";
      }
    }

    // Renderiza as listas na tela
    renderList("cozinha", "cozinha");
    renderList("banheiro", "banheiro");
    renderList("sala", "sala");
  </script>
</body>
</html>
