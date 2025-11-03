<!DOCTYPE html>
<html lang="es">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>Integración de Páginas Web</title>
  <style>
    body {
      font-family: Arial, sans-serif;
      text-align: center;
      margin: 0;
      padding: 0;
    }

    h1 {
      background-color: #ff80aa;
      color: white;
      margin: 0;
      padding: 20px;
    }

    .button-container {
      margin-top: 20px;
    }

    button {
      margin: 10px;
      padding: 10px 20px;
      font-size: 16px;
      cursor: pointer;
      border: none;
      background-color: #ff4d94;
      color: white;
      border-radius: 8px;
      transition: background 0.3s;
    }

    button:hover {
      background-color: #e60073;
    }

    iframe {
      width: 90%;
      height: 600px;
      margin-top: 20px;
      border: 2px solid #ccc;
      border-radius: 10px;
    }

    footer {
      margin-top: 30px;
      background-color: #f2f2f2;
      padding: 12px;
      font-size: 15px;
      color: #333;
      font-weight: bold;
    }
  </style>
</head>
<body>

  <h1>🌸 Explora nuestras páginas 🌸</h1>

  <div class="button-container">
    <button onclick="cargarPagina('formulario.html')">📝 Formulario</button>
    <button onclick="cargarPagina('juego.html')">🎮 Juego</button>
    <button onclick="cargarPagina('principal.html')">🏠 Página Principal</button>
  </div>

  <iframe id="visor" src="" title="Visor de páginas"></iframe>

  <footer>
    <p>Elaborado por: <strong>Maria Jose Duque y Manuela Florez</strong></p>
  </footer>

  <script>
    function cargarPagina(url) {
      document.getElementById('visor').src = url;
    }
  </script>

</body>
</html>
