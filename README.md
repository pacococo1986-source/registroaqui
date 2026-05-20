<!DOCTYPE html>
<html lang="es">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>Formulario Cliente</title>

  <style>
    body {
      font-family: Arial, sans-serif;
      background: #f4f4f4;
      display: flex;
      justify-content: center;
      align-items: center;
      height: 100vh;
      margin: 0;
    }

    .container {
      background: white;
      padding: 30px;
      border-radius: 12px;
      box-shadow: 0 4px 12px rgba(0,0,0,0.1);
      width: 320px;
    }

    h2 {
      text-align: center;
      margin-bottom: 20px;
    }

    input {
      width: 100%;
      padding: 12px;
      margin-bottom: 15px;
      border: 1px solid #ccc;
      border-radius: 8px;
      font-size: 16px;
      box-sizing: border-box;
    }

    button {
      width: 100%;
      padding: 12px;
      border: none;
      border-radius: 8px;
      background: #007bff;
      color: white;
      font-size: 16px;
      cursor: pointer;
    }

    button:hover {
      background: #0056b3;
    }

    .mensaje {
      text-align: center;
      margin-top: 15px;
      color: green;
    }
  </style>
</head>
<body>

  <div class="container">
    <h2>Formulario</h2>

    <form id="formulario">
      <input type="text" id="nombre" placeholder="Nombre" required>

      <input type="text" id="apellidos" placeholder="Apellidos" required>

      <button type="submit">Enviar</button>
    </form>

    <div class="mensaje" id="mensaje"></div>
  </div>

  <script>
    const formulario = document.getElementById('formulario');

    formulario.addEventListener('submit', async (e) => {
      e.preventDefault();

      const nombre = document.getElementById('nombre').value;
      const apellidos = document.getElementById('apellidos').value;

      const datos = {
        nombre,
        apellidos
      };

      try {
        const respuesta = await fetch('PEGA_AQUI_TU_URL_DE_APPS_SCRIPT', {
          method: 'POST',
          headers: {
            'Content-Type': 'application/json'
          },
          body: JSON.stringify(datos)
        });

        const resultado = await respuesta.text();

        document.getElementById('mensaje').innerText = 'Formulario enviado correctamente';

        formulario.reset();

      } catch (error) {
        document.getElementById('mensaje').innerText = 'Error al enviar';
        console.error(error);
      }
    });
  </script>

</body>
</html>