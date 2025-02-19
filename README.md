<html lang="pt-BR">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>Calculadora de Coberturas</title>
  <style>
    body {
      font-family: Arial, sans-serif;
      margin: 20px;
      text-align: center;
    }
    h1 {
      color: #333;
    }
    .container {
      max-width: 600px;
      margin: 0 auto;
    }
    label {
      display: block;
      margin-top: 10px;
    }
    input, select, button {
      width: 100%;
      padding: 10px;
      margin-top: 5px;
      margin-bottom: 10px;
      border: 1px solid #ccc;
      border-radius: 5px;
    }
    button {
      background-color: #007BFF;
      color: white;
      cursor: pointer;
    }
    button:hover {
      background-color: #0056b3;
    }
    .resultado {
      margin-top: 20px;
      padding: 10px;
      background-color: #f9f9f9;
      border: 1px solid #ddd;
      border-radius: 5px;
      text-align: left;
    }
    .hidden {
      display: none;
    }
    img {
      max-width: 100%;
      height: auto;
      margin-top: 10px;
    }
    .logo {
      max-width: 450px;
      margin: 0 auto 20px; /* Centraliza o logotipo */
      display: block; /* Garante que a margem automática funcione */
    }
    .whatsapp-button {
      background-color: #25D366;
      color: white;
      padding: 10px 20px;
      border-radius: 5px;
      text-decoration: none;
      display: inline-block;
      margin-top: 20px; /* Aumenta a margem superior para posicionar abaixo do botão de PDF */
      animation: piscar 1.5s infinite;
    }
    @keyframes piscar {
      0%, 100% { opacity: 1; }
      50% { opacity: 0.7; }
    }
    .instagram-link {
      display: block;
      margin-top: 10px;
      color: #007BFF;
      text-decoration: none;
    }
  </style>
  <script src="https://cdnjs.cloudflare.com/ajax/libs/jspdf/2.5.1/jspdf.umd.min.js"></script>
</head>
<body>
  <div class="container">
    <!-- Logotipo da Empresa -->
    <img src="https://gabriellemoreira.com.br/wp-content/uploads/2025/02/braco-forte.jpeg" alt="Logotipo da Empresa" class="logo">

    <h1>Orçamento <p>Calculadora de Coberturas</p> </h1>
    <p><strong>EMPRESA DE COBERTURAS DE AÇOS DO KELVYN</strong></p>

    <!-- Filtro de Tipo de Cobertura -->
    <label for="tipoCobertura">Tipo de Cobertura:</label>
    <select id="tipoCobertura">
      <option value="umaInclinacao">Selecione o formato do seu telhado</option>
      <option value="umaInclinacao">Uma inclinação</option>
      <option value="duasAbasSimetricas">Duas abas simétricas</option>
      <option value="duasAbasAssimetricas">Duas abas assimétricas</option>
    </select>

    <!-- Imagem da Cobertura -->
    <img id="imagemCobertura" src="" alt="Imagem do tipo de cobertura" class="hidden">

    <!-- Filtro de Telhas -->
    <label for="tipoTelha">Selecione a Telha:</label>
    <select id="tipoTelha">
      <optgroup label="Telhas de Zinco Trapezoidais">
        <option value="1.8x0.8">Selecione o tipo de telha </option>

        <option value="1.8x0.8">Telhas de Zinco Trapezoidais 1 (1,8x0,8 cm)</option>
        <option value="2.0x0.8">Telhas de Zinco Trapezoidais 2 (2,0x0,80 cm)</option>
        <option value="3.0x0.8">Telhas de Zinco Trapezoidais 3 (3,0x0,80 cm)</option>
        <option value="5.0x0.8">Telhas de Zinco Trapezoidais 4 (5,0x0,80 cm)</option>
        <option value="6.0x0.8">Telhas de Zinco Trapezoidais 5 (6,0x0,80 cm)</option>
        <option value="8.0x0.8">Telhas de Zinco Trapezoidais 6 (8,0x0,80 cm)</option>
        <option value="10.0x0.8">Telhas de Zinco Trapezoidais 7 (10,0x0,80 cm)</option>
        <option value="12.0x0.8">Telhas de Zinco Trapezoidais 8 (12,0x0,80 cm)</option>
      </optgroup>
      <optgroup label="Telhas de Zinco Onduladas">

        <option value="1.8x0.8">Telhas de Zinco Onduladas 1 (1,8x0,80 cm)</option>
        <option value="2.0x0.8">Telhas de Zinco Onduladas 2 (2,0x0,80 cm)</option>
        <option value="3.0x0.8">Telhas de Zinco Onduladas 3 (3,0x0,80 cm)</option>
        <option value="5.0x0.8">Telhas de Zinco Onduladas 4 (5,0x0,80 cm)</option>
        <option value="6.0x0.8">Telhas de Zinco Onduladas 5 (6,0x0,80 cm)</option>
        <option value="8.0x0.8">Telhas de Zinco Onduladas 6 (8,0x0,80 cm)</option>
        <option value="10.0x0.8">Telhas de Zinco Onduladas 7 (10,0x0,80 cm)</option>
        <option value="12.0x0.8">Telhas de Zinco Onduladas 8 (12,0x0,80 cm)</option>
      </optgroup>
    </select>

    <!-- Imagem da Telha -->
    <img id="imagemTelha" src="" alt="Imagem da telha selecionada" class="hidden">

    <!-- Campos de Metragem -->
    <label for="metragemA">A (m):</label>
    <input type="number" id="metragemA" placeholder="Insira a metragem A">

    <label for="metragemB">B (m):</label>
    <input type="number" id="metragemB" placeholder="Insira a metragem B">

    <label for="metragemC" class="hidden">C (m):</label>
    <input type="number" id="metragemC" placeholder="Insira a metragem C" class="hidden">

    <!-- Botão de Calcular -->
    <button onclick="calcular()">Calcular</button>

    <!-- Resultado -->
    <div class="resultado">
      <p>A superfície do telhado é: <span id="areaTotal">0</span> m²</p>
      <p>Você precisa: <span id="quantidadeTelhas">0</span> telhas</p>
      <p>Valor total: R$ <span id="valorTotal">0,00</span></p>
      <p id="detalhesSobreposicao"></p>
      <button onclick="gerarPDF()">Clique para Imprimir seu Orçamento em PDF</button>
    </div>

    <!-- Botão do WhatsApp -->
    <a href="https://wa.me/5521981304519" class="whatsapp-button" target="_blank">Chame no WhatsApp</a>

    <!-- Link do Instagram -->
    <a href="https://www.instagram.com/bracofortecoberturas/" class="instagram-link" target="_blank">Siga-nos no Instagram</a>
  </div>

  <script>
    // URLs das imagens
    const imagensCobertura = {
      umaInclinacao: "https://gabriellemoreira.com.br/wp-content/uploads/2025/02/telhado-uma-inclinacao.png",
      duasAbasSimetricas: "https://gabriellemoreira.com.br/wp-content/uploads/2025/02/telhados-duas-abas-simetricas.png",
      duasAbasAssimetricas: "https://gabriellemoreira.com.br/wp-content/uploads/2025/02/Telhados-duas-abas-assimetricas.png"
    };

    const imagensTelhas = {
      trapezoidal: "https://gabriellemoreira.com.br/wp-content/uploads/2025/02/Captura-de-Tela-2025-02-19-as-01.02.31.png",
      ondulada: "https://gabriellemoreira.com.br/wp-content/uploads/2025/02/Captura-de-Tela-2025-02-19-as-01.11.18.png"
    };

    // Atualizar imagem ao selecionar o tipo de cobertura
    document.getElementById("tipoCobertura").addEventListener("change", function () {
      const tipo = this.value;
      const imgCobertura = document.getElementById("imagemCobertura");
      imgCobertura.src = imagensCobertura[tipo];
      imgCobertura.classList.remove("hidden");

      // Mostrar/ocultar campo C para "Duas abas assimétricas"
      if (tipo === "duasAbasAssimetricas") {
        document.getElementById("metragemC").classList.remove("hidden");
        document.querySelector('label[for="metragemC"]').classList.remove("hidden");
      } else {
        document.getElementById("metragemC").classList.add("hidden");
        document.querySelector('label[for="metragemC"]').classList.add("hidden");
      }
    });

    // Atualizar imagem ao selecionar o tipo de telha
    document.getElementById("tipoTelha").addEventListener("change", function () {
      const tipoTelha = this.options[this.selectedIndex].parentElement.label;
      const imgTelha = document.getElementById("imagemTelha");
      if (tipoTelha.includes("Trapezoidais")) {
        imgTelha.src = imagensTelhas.trapezoidal;
      } else if (tipoTelha.includes("Onduladas")) {
        imgTelha.src = imagensTelhas.ondulada;
      }
      imgTelha.classList.remove("hidden");
    });

    // Função para calcular área, quantidade de telhas e valor total
    function calcular() {
      const tipoCobertura = document.getElementById("tipoCobertura").value;
      const metragemA = parseFloat(document.getElementById("metragemA").value);
      const metragemB = parseFloat(document.getElementById("metragemB").value);
      const metragemC = parseFloat(document.getElementById("metragemC").value) || 0;

      // Calcular área do telhado
      let areaTelhado;
      if (tipoCobertura === "umaInclinacao" || tipoCobertura === "duasAbasSimetricas") {
        areaTelhado = metragemA * metragemB;
      } else if (tipoCobertura === "duasAbasAssimetricas") {
        areaTelhado = (metragemA * metragemB) + (metragemA * metragemC);
      }

      // Calcular área útil da telha (considerando sobreposições)
      const medidasTelha = document.getElementById("tipoTelha").value.split("x");
      const comprimentoTelha = parseFloat(medidasTelha[0]); // Em metros
      const larguraTelha = parseFloat(medidasTelha[1]); // Em metros

      // Sobreposições
      const sobreposicaoLateral = 0.1; // 10 cm
      const sobreposicaoLongitudinal = 0.2; // 20 cm

      const larguraUtil = larguraTelha - sobreposicaoLateral;
      const comprimentoUtil = comprimentoTelha - sobreposicaoLongitudinal;
      const areaUtilTelha = larguraUtil * comprimentoUtil;

      // Quantidade de telhas necessárias
      const quantidadeTelhas = Math.ceil(areaTelhado / areaUtilTelha);

      // Valor total (R$ 180,00 por telha)
      const valorTotal = quantidadeTelhas * 180;

      // Exibir resultados
      document.getElementById("areaTotal").textContent = areaTelhado.toFixed(2);
      document.getElementById("quantidadeTelhas").textContent = quantidadeTelhas;
      document.getElementById("valorTotal").textContent = valorTotal.toFixed(2);

      // Detalhes da sobreposição
      document.getElementById("detalhesSobreposicao").innerHTML = `
        <strong>Considerando as sobreposições:</strong><br>
        - Sobreposição lateral: ${sobreposicaoLateral * 100} cm (largura útil: ${larguraUtil.toFixed(2)} m)<br>
        - Sobreposição longitudinal: ${sobreposicaoLongitudinal * 100} cm (comprimento útil: ${comprimentoUtil.toFixed(2)} m)<br>
        - Área útil de cada telha: ${areaUtilTelha.toFixed(2)} m²<br>
        <em>Obs.: Caso sua largura ou comprimento estejam incorretos, me avise para refazer os cálculos! 😊</em>
      `;
    }

    // Função para gerar PDF
    function gerarPDF() {
      const { jsPDF } = window.jspdf;
      const doc = new jsPDF();

      // Adicionar logotipo
      const logoUrl = "https://gabriellemoreira.com.br/wp-content/uploads/2025/02/braco-forte.jpeg";
      const logoWidth = 50;
      const logoHeight = 20;
      doc.addImage(logoUrl, "JPEG", 10, 10, logoWidth, logoHeight);

      // Título
      doc.setFontSize(18);
      doc.text("Orçamento de Coberturas", 70, 20);

      // Informações da Empresa
      doc.setFontSize(12);
      doc.text("EMPRESA DE COBERTURAS DE AÇOS DO KELVYN", 10, 40);
      doc.text("Rua Doutor Lucio Machado 15, São João de Meriti", 10, 50);
      doc.text("Orçamentos: (21) 98130-4519 grátis!", 10, 60);
      doc.text("Instagram: @bracofortecoberturas", 10, 70);

      // Dados do Orçamento
      doc.setFontSize(14);
      doc.text("Detalhes do Orçamento:", 10, 90);
      doc.setFontSize(12);
      doc.text(`Área do telhado: ${document.getElementById("areaTotal").textContent} m²`, 10, 100);
      doc.text(`Quantidade de telhas: ${document.getElementById("quantidadeTelhas").textContent}`, 10, 110);
      doc.text(`Valor total: R$ ${document.getElementById("valorTotal").textContent}`, 10, 120);

      // Salvar o PDF e abrir em uma nova aba
      const pdfBlob = doc.output("blob");
      const pdfUrl = URL.createObjectURL(pdfBlob);
      const newWindow = window.open(pdfUrl, "_blank");
      if (!newWindow) {
        alert("Por favor, permita pop-ups para visualizar o PDF.");
      }
    }
  </script>
</body>
</html>
