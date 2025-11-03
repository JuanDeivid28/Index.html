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
<!DOCTYPE html>
<html lang="es">
<head>
  <meta charset="UTF-8" />
  <meta name="viewport" content="width=device-width, initial-scale=1.0" />
  <title>Sopa de Letras - Brillo Mágico</title>
  <style>
    body {
      font-family: 'Poppins', sans-serif;
      background: #fff0f5;
      text-align: center;
      color: #333;
      margin: 0;
      padding: 0;
    }

    h1 {
      margin-top: 30px;
      color: #e60073;
    }

    #grid {
      display: grid;
      grid-template-columns: repeat(6, 40px);
      justify-content: center;
      gap: 5px;
      margin-top: 30px;
    }

    .cell {
      width: 40px;
      height: 40px;
      background: white;
      border: 1px solid #ff99cc;
      display: flex;
      align-items: center;
      justify-content: center;
      font-weight: bold;
      cursor: pointer;
      user-select: none;
      border-radius: 6px;
      transition: background 0.2s;
    }

    .selected {
      background: #ffb3d9;
    }

    .found {
      background: #ff4d94;
      color: white;
    }

    button {
      background-color: #ff4d94;
      color: white;
      border: none;
      padding: 10px 20px;
      border-radius: 10px;
      cursor: pointer;
      margin-top: 20px;
    }

    button:hover {
      background-color: #e60073;
    }

    p {
      font-size: 18px;
    }
  </style>
</head>
<body>
  <h1>🎯 Sopa de Letras de Maquillaje</h1>
  <p>Encuentra las palabras: <strong>labial, base, rubor, sombra, brocha</strong></p>

  <div id="grid"></div>

  <button onclick="window.location.href='index.html'">🏠 Volver al inicio</button>

  <script>
    const palabras = ["LABIAL", "BASE", "RUBOR", "SOMBRA", "BROCHA"];
    const letras = [
      ["L","A","B","I","A","L"],
      ["R","U","B","O","R","A"],
      ["S","O","M","B","R","A"],
      ["B","A","S","E","X","Y"],
      ["B","R","O","C","H","A"]
    ];

    const grid = document.getElementById("grid");
    let seleccionadas = [];
    let encontradas = [];

    letras.forEach((fila, y) => {
      fila.forEach((letra, x) => {
        const cell = document.createElement("div");
        cell.classList.add("cell");
        cell.textContent = letra;
        cell.dataset.x = x;
        cell.dataset.y = y;
        cell.addEventListener("click", () => seleccionar(cell));
        grid.appendChild(cell);
      });
    });

    function seleccionar(cell) {
      const id = `${cell.dataset.x},${cell.dataset.y}`;
      if (seleccionadas.includes(id)) {
        cell.classList.remove("selected");
        seleccionadas = seleccionadas.filter(s => s !== id);
      } else {
        cell.classList.add("selected");
        seleccionadas.push(id);
      }
      comprobarPalabra();
    }

    function comprobarPalabra() {
      const letrasSeleccionadas = seleccionadas.map(id => {
        const [x, y] = id.split(",").map(Number);
        return letras[y][x];
      }).join("");

      for (let palabra of palabras) {
        if (letrasSeleccionadas.includes(palabra)) {
          marcarEncontrada(palabra);
        }
      }
    }

    function marcarEncontrada(palabra) {
      if (encontradas.includes(palabra)) return;
      encontradas.push(palabra);
      document.querySelectorAll(".selected").forEach(cell => {
        cell.classList.remove("selected");
        cell.classList.add("found");
      });
      seleccionadas = [];

      if (encontradas.length === palabras.length) {
        setTimeout(() => alert("🎉 ¡Has encontrado todas las palabras!"), 200);
      }
    }
  </script>
</body>
</html>
<!DOCTYPE html>
<html lang="es">
<head>
  <meta charset="UTF-8" />
  <meta name="viewport" content="width=device-width, initial-scale=1.0" />
  <title>Formulario de Contacto - Brillo Mágico</title>
  <style>
    body {
      font-family: 'Poppins', sans-serif;
      background: #ffe6f2;
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

    form {
      background: white;
      display: inline-block;
      margin-top: 40px;
      padding: 25px;
      border-radius: 15px;
      box-shadow: 0 0 10px #ffb6c1;
      width: 300px;
    }

    input, textarea {
      width: 90%;
      margin: 10px auto;
      padding: 10px;
      border-radius: 8px;
      border: 1px solid #ccc;
      font-family: 'Poppins', sans-serif;
    }

    textarea {
      height: 80px;
      resize: none;
    }

    button {
      background-color: #ff4d94;
      color: white;
      border: none;
      padding: 10px 20px;
      border-radius: 10px;
      cursor: pointer;
      margin-top: 10px;
    }

    button:hover {
      background-color: #e60073;
    }

    footer {
      margin-top: 40px;
      background-color: #f2f2f2;
      padding: 12px;
      font-size: 15px;
      color: #333;
      font-weight: bold;
    }
  </style>
</head>
<body>
  <h1>💌 Contáctanos</h1>

  <form onsubmit="event.preventDefault(); alert('¡Gracias por contactarte con Brillo Mágico! 💄');">
    <input type="text" placeholder="Nombre completo" required />
    <input type="email" placeholder="Correo electrónico" required />
    <textarea placeholder="Tu mensaje..." required></textarea>
    <button type="submit">Enviar</button>
  </form>

  <br>
  <button onclick="window.location.href='index.html'">🏠 Volver al inicio</button>

  <footer>
    <p>Brillo Mágico - 2025 💋</p>
  </footer>
</body>
<button onclick="cargarPagina('formulario.html')">📝 Formulario</button>
<button onclick="cargarPagina('juego.html')">🎮 Juego</button>
<button onclick="cargarPagina('principal.html')">🏠 Página Principal</button>

</html>
