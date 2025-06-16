<!DOCTYPE html>
<html lang="pt-BR">
<head>
  <meta charset="UTF-8" />
  <meta name="viewport" content="width=device-width, initial-scale=1" />
  <title>Chá Julino Rafaela e Rafael</title>
  <style>
    /* Fonte */
    @import url('https://fonts.googleapis.com/css2?family=Great+Vibes&family=Montserrat&display=swap');

    body {
      margin: 0;
      padding: 20px;
      font-family: 'Montserrat', sans-serif;
      background-color: #0b2342; /* azul marinho */
      color: #f9f1d1; /* amarelo claro */
      background-image:
        radial-gradient(circle, #ffd70066 1px, transparent 1px),
        linear-gradient(45deg, #0b2342 25%, #0d2c57 25%, #0d2c57 50%, #0b2342 50%, #0b2342 75%, #0d2c57 75%, #0d2c57 100%);
      background-size: 40px 40px, 80px 80px;
      min-height: 100vh;
    }

    header {
      text-align: center;
      margin-bottom: 40px;
      position: relative;
    }

    header img {
      width: 160px;
      height: 160px;
      border-radius: 50%;
      border: 4px solid #ffd700;
      background-color: #0b2342;
      box-shadow:
        0 0 15px 5px #ffd700aa,
        0 0 30px 15px #ffd70055;
      margin-bottom: 10px;
    }

    header h1 {
      font-family: 'Great Vibes', cursive;
      font-size: 3.8rem;
      color: #ffd700;
      letter-spacing: 3px;
      text-shadow: 0 0 10px #ffd700cc;
      margin: 0;
    }

    h2 {
      font-family: 'Montserrat', sans-serif;
      font-weight: 600;
      font-size: 1.8rem;
      margin-top: 50px;
      margin-bottom: 15px;
      border-bottom: 3px solid #ffd700;
      padding-bottom: 6px;
      color: #ffe066;
      text-shadow: 0 0 5px #ffd700aa;
    }

    ul {
      list-style: none;
      padding-left: 0;
      max-width: 480px;
      margin: 0 auto;
    }

    li {
      background-color: #123158;
      border: 1.5px solid #ffd700cc;
      margin: 10px 0;
      padding: 12px 18px;
      border-radius: 12px;
      display: flex;
      justify-content: space-between;
      align-items: center;
      box-shadow: 0 0 10px #ffd70099;
      font-size: 1.1rem;
    }

    button {
      background-color: #ffd700;
      color: #0b2342;
      font-weight: 700;
      border: none;
      border-radius: 8px;
      padding: 7px 15px;
      cursor: pointer;
      box-shadow: 0 0 7px #ffd700cc;
      transition: background-color 0.25s ease;
    }

    button:hover:not(:disabled) {
      background-color: #ffdb4d;
    }

    button:disabled {
      background-color: #7a6f0a;
      color: #d7c954;
      cursor: default;
      box-shadow: none;
    }

    /* Recados */
    .recados {
      max-width: 480px;
      margin: 50px auto 0;
      text-align: center;
    }

    .recados textarea {
      width: 100%;
      height: 120px;
      border-radius: 10px;
      border: 1.8px solid #ffd700cc;
      background-color: #123158;
      color: #f9f1d1;
      font-size: 1.1rem;
      font-family: 'Montserrat', sans-serif;
      padding: 15px;
      resize: none;
      box-shadow: 0 0 10px #ffd70099 inset;
      outline: none;
      transition: border-color 0.3s;
    }

    .recados textarea:focus {
      border-color: #ffea00;
      box-shadow: 0 0 15px #ffd700cc inset;
    }

    .recados button {
      margin-top: 12px;
      width: 100%;
      font-size: 1.2rem;
      padding: 10px 0;
    }

    .mensagens {
      margin-top: 25px;
      max-height: 250px;
      overflow-y: auto;
      background-color: #123158;
      padding: 15px;
      border-radius: 10px;
      box-shadow: 0 0 15px #ffd700aa inset;
    }

    .mensagem {
      background-color: #0b2342;
      border-left: 4px solid #ffd700;
      margin-bottom: 12px;
      padding: 10px 15px;
      border-radius: 8px;
      font-size: 1rem;
      text-align: left;
      word-wrap: break-word;
      box-shadow: 0 0 8px #ffd700bb;
    }

    /* Scrollbar estilizado */
    .mensagens::-webkit-scrollbar {
      width: 8px;
    }
    .mensagens::-webkit-scrollbar-thumb {
      background: #ffd700cc;
      border-radius: 4px;
    }
    .mensagens::-webkit-scrollbar-track {
      background: #0b2342;
    }

    /* Música fixa no canto inferior direito */
    .audio-player {
      position: fixed;
      bottom: 15px;
      right: 15px;
      background-color: #123158cc;
      border-radius: 12px;
      box-shadow: 0 0 15px #ffd700aa;
      padding: 10px 15px;
      display: flex;
      align-items: center;
      gap: 10px;
      color: #ffd700;
      font-weight: 700;
      font-family: 'Montserrat', sans-serif;
      user-select: none;
    }

    .audio-player audio {
      outline: none;
      width: 180px;
    }
  </style>
</head>
<body>
  <header>
    <img src="https://via.placeholder.com/150/0b2342/ffd700?text=R%26R" alt="Logo R & R" />
    <h1>Chá Julino Rafaela & Rafael</h1>
  </header>

  <h2>Cozinha</h2>
  <ul id="cozinha"></ul>

  <h2>Banheiro</h2>
  <ul id="banheiro"></ul>

  <h2>Sala</h2>
  <ul id="sala"></ul>

  <section class="recados">
    <h2>Deixe seu recado para os noivos 💌</h2>
    <textarea id="mensagem" placeholder="Escreva aqui sua mensagem..."></textarea>
    <button onclick="enviarMensagem()">Enviar</button>
    <div class="mensagens" id="mensagens"></div>
  </section>

  <div class="audio-player" title="Música: Perfect - Ed Sheeran">
    <audio id="audio" controls loop>
      <source src="https://www.dropbox.com/scl/fi/j1f0dj6d4g0z5t0e7n04x/Ed-Sheeran-Perfect.mp3?rlkey=kgvd2l8coyzk4s7ru1wv56uzd&dl=1" type="audio/mpeg" />
      Seu navegador não suporta áudio.
    </audio>
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
      ul.innerHTML = ''; // limpa para não duplicar
      listaPresentes[categoria].forEach((item) => {
        const li = document.createElement("li");
        li.innerHTML = `
          <span>${item}</span>
          <button onclick="marcarEscolhido(this)">Escolher</button>
        `;
        ul.appendChild(li);
      });
    }

    function marcarEscolhido(button) {
      button.disabled = true;
      button.textContent = "Escolhido";
    }

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

    renderList("cozinha", "cozinha");
    renderList("banheiro", "banheiro");
    renderList("sala", "sala");
  </script>
</body>
</html>
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
