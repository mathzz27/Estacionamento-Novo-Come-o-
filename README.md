<!DOCTYPE html>
<html lang="pt-BR">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>Estacionamento Novo Começo</title>
  <style>
    /* Estilo Global */
    body {
      font-family: 'Roboto', sans-serif;
      margin: 0;
      padding: 0;
      background: linear-gradient(to bottom, #f5f5f5, #ffffff);
      color: #333;
    }

    /* Cabeçalho */
    header {
      background: linear-gradient(to right, #1e1e2f, #3a3a5f);
      color: #f4f4f8;
      text-align: center;
      padding: 30px;
      box-shadow: 0 8px 15px rgba(0, 0, 0, 0.2);
    }

    header h1 {
      margin: 0;
      font-size: 3rem;
      font-weight: 600;
      letter-spacing: 2px;
    }

    header p {
      margin: 5px 0 0;
      font-size: 1.2rem;
      font-style: italic;
      opacity: 0.8;
    }

    /* Container principal */
    .container {
      max-width: 900px;
      margin: 40px auto;
      padding: 20px;
      background: #ffffff;
      border-radius: 15px;
      box-shadow: 0 10px 30px rgba(0, 0, 0, 0.1);
    }

    /* Botões */
    .button {
      display: block;
      width: 100%;
      padding: 15px;
      margin: 10px 0;
      background: linear-gradient(to right, #6a11cb, #2575fc);
      color: white;
      text-align: center;
      font-size: 1.3rem;
      font-weight: 600;
      text-transform: uppercase;
      border: none;
      border-radius: 8px;
      cursor: pointer;
      transition: transform 0.3s, background-color 0.3s;
    }

    .button:hover {
      background: linear-gradient(to right, #5b0eb2, #1d65e8);
      transform: translateY(-3px);
      box-shadow: 0 8px 20px rgba(0, 0, 0, 0.15);
    }

    /* Seções ocultas */
    .hidden {
      display: none;
    }

    .section {
      margin: 20px 0;
      padding: 20px;
      background: #f9f9f9;
      border-radius: 10px;
      box-shadow: 0 4px 15px rgba(0, 0, 0, 0.1);
    }

    .section h2 {
      margin-bottom: 15px;
      color: #6a11cb;
      font-size: 2rem;
    }

    .section p, .section ul {
      font-size: 1.2rem;
      line-height: 1.8;
    }

    .section ul {
      padding-left: 20px;
    }

    .section ul li {
      margin-bottom: 10px;
    }

    /* QR Code */
    .qr-container {
      text-align: center;
      margin: 40px 0;
    }

    .qr-container h2 {
      color: #6a11cb;
      font-size: 1.8rem;
    }

    .qr-container img {
      max-width: 200px;
      margin-top: 15px;
    }

    /* Rodapé */
    footer {
      text-align: center;
      margin: 30px 0;
      font-size: 1rem;
      color: #777;
    }

    footer p {
      margin: 0;
    }
  </style>
  <script src="https://cdnjs.cloudflare.com/ajax/libs/qrcodejs/1.0.0/qrcode.min.js"></script>
</head>
<body>

<header>
  <h1>Estacionamento Novo Começo</h1>
  <p>Institito Pro Ser</p>
</header>

<div class="container">
  <button class="button" onclick="showSection('precos')">Preços</button>
  <button class="button" onclick="showSection('convenios')">Convênios</button>
  <button class="button" onclick="showSection('lavajato')">Lava-Jato</button>
  <button class="button" onclick="showSection('carvao')">Carvão</button>

  <div id="precos" class="section hidden">
    <h2>Preços</h2>
    <p><strong>Diária:</strong> R$ 30,00</p>
    <p><strong>Por Hora:</strong> R$ 7,00</p>
    <p><strong>Fração:</strong> R$ 4,00</p>
  </div>

  <div id="convenios" class="section hidden">
    <h2>Convênios</h2>
    <p><strong>Taberna Alpina:</strong> Consumo mínimo de R$ 150,00 para estacionamento grátis.</p>
    <p><strong>Cadel:</strong> 1h30 de estacionamento grátis.</p>
    <p><strong>Osvaldo & Luci:</strong> Estacionamento grátis para clientes do restaurante.</p>
    <p><strong>Estrela:</strong> 1h grátis para compras acima de R$ 50,00.</p>
  </div>

  <div id="lavajato" class="section hidden">
    <h2>Lava-Jato</h2>
    <p><strong>Ducha Simples:</strong> R$ 15,00</p>
    <p><strong>Ducha c/ Secagem:</strong></p>
    <ul>
      <li>Carro Pequeno/Médio: R$ 25,00</li>
      <li>Carro Grande: R$ 40,00</li>
    </ul>
    <p><strong>Aspiração Geral:</strong> R$ 35,00</p>
    <p><strong>Geral c/ Cera:</strong></p>
    <ul>
      <li>Carro Pequeno/Médio: R$ 65,00</li>
      <li>Carro Grande: R$ 120,00</li>
    </ul>
  </div>

  <div id="carvao" class="section hidden">
    <h2>Carvão</h2>
    <p><strong>Preço:</strong> R$ 14,00 por saco.</p>
  </div>

  <div class="qr-container">
    <h2>Baixe nosso aplicativo</h2>
    <div id="qrcode"></div>
  </div>
</div>

<footer>
  <p>© 2025 Estacionamento Novo Começo. Exclusividade e sofisticação para você.</p>
</footer>

<script>
  function showSection(sectionId) {
    document.querySelectorAll('.section').forEach(section => {
      section.classList.add('hidden');
    });
    document.getElementById(sectionId).classList.remove('hidden');
  }

  function generateQRCode() {
    const url = window.location.href;
    const qrCodeContainer = document.getElementById('qrcode');
    new QRCode(qrCodeContainer, {
      text: url,
      width: 200,
      height: 200,
      colorDark: "#1e1e2f",
      colorLight: "#ffffff",
      correctLevel: QRCode.CorrectLevel.H
    });
  }

  generateQRCode();
</script>

</body>
</html>
