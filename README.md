<!DOCTYPE html>
<html lang="es">
<head>
  <meta charset="UTF-8">
  <title>Mapa Vivo de Participación Comunal</title>
  <style>
    /* Estilos modernos y vibrantes para la herramienta offline */
    body {
      font-family: 'Segoe UI', Tahoma, sans-serif;
      background: linear-gradient(135deg, #f2f7fc, #e9f1fa);
      margin: 0;
      padding: 0;
      color: #333;
    }
    .header {
      background-color: #0065b3;
      color: #ffffff;
      padding: 20px;
      text-align: center;
    }
    .container {
      max-width: 900px;
      margin: 20px auto;
      background-color: #ffffff;
      padding: 20px 30px;
      border-radius: 8px;
      box-shadow: 0 4px 10px rgba(0, 0, 0, 0.1);
    }
    .container h2 {
      color: #0065b3;
    }
    form label {
      display: block;
      margin-top: 12px;
      font-weight: 600;
    }
    input[type="text"], textarea, select {
      width: 100%;
      padding: 10px;
      margin-top: 4px;
      border: 1px solid #cccccc;
      border-radius: 4px;
      box-sizing: border-box;
    }
    button {
      display: inline-block;
      margin-top: 15px;
      padding: 12px 24px;
      background-color: #00a3e0;
      color: #ffffff;
      border: none;
      border-radius: 4px;
      font-size: 1rem;
      cursor: pointer;
      transition: background-color 0.3s ease;
    }
    button:hover {
      background-color: #0081b4;
    }
    table {
      border-collapse: collapse;
      width: 100%;
      margin-top: 20px;
    }
    th, td {
      padding: 10px;
      border: 1px solid #dddddd;
      text-align: left;
    }
    th {
      background-color: #0065b3;
      color: #ffffff;
    }
    tbody tr:nth-child(odd) {
      background-color: #f5faff;
    }
    tbody tr:nth-child(even) {
      background-color: #e9f2fb;
    }
    .footer {
      margin-top: 30px;
      font-size: 0.8rem;
      color: #555;
      text-align: center;
      background-color: #f2f7fc;
      padding: 10px 20px;
      border-radius: 0 0 8px 8px;
    }
    .footer strong {
      color: #0065b3;
    }
  </style>
</head>
<body>
  <div class="header">
    <h1>Mapa Vivo de Participación Comunal</h1>
  </div>
  <div class="container">
    <p>Registre su nivel de participación y describa las barreras y oportunidades en su comunidad. También puede proponer acciones para superar problemas específicos.</p>
    <form id="form">
      <label>Nivel de participación:
        <select id="level">
          <option value="No participo">No participo</option>
          <option value="Participo ocasionalmente">Participo ocasionalmente</option>
          <option value="Participo activamente">Participo activamente</option>
          <option value="Lidero procesos">Lidero procesos</option>
        </select>
      </label>
      <label>Barrera identificada:
        <input type="text" id="barrier" required>
      </label>
      <label>Oportunidad identificada:
        <input type="text" id="opportunity" required>
      </label>
      <label>Problema priorizado (opcional):
        <input type="text" id="problem">
      </label>
      <label>Causa del problema (opcional):
        <textarea id="cause" rows="2"></textarea>
      </label>
      <label>Acción propuesta (opcional):
        <textarea id="action" rows="2"></textarea>
      </label>
      <label>Actor responsable (opcional):
        <input type="text" id="actor">
      </label>
      <button type="button" onclick="addEntry()">Agregar entrada</button>
    </form>
    <h2>Entradas registradas</h2>
    <table id="entries">
      <thead>
        <tr>
          <th>Nivel</th>
          <th>Barrera</th>
          <th>Oportunidad</th>
          <th>Problema</th>
          <th>Causa</th>
          <th>Acción</th>
          <th>Actor</th>
        </tr>
      </thead>
      <tbody></tbody>
    </table>
    <div class="footer">
      <p><strong>Directiva de Derechos de Autor: Ana María Núñez H.</strong><br>
      © 2026 Ana María Núñez H. Todos los derechos reservados. Se autoriza el uso de esta herramienta únicamente con fines académicos y de investigación, conforme a las excepciones de derecho de cita e ilustración para la enseñanza previstas en la legislación aplicable:contentReference[oaicite:0]{index=0}:contentReference[oaicite:1]{index=1}. Debe mencionarse la fuente y no se permiten fines comerciales.</p>
    </div>
  </div>

  <script>
    function addEntry() {
      const level = document.getElementById('level').value;
      const barrier = document.getElementById('barrier').value.trim();
      const opportunity = document.getElementById('opportunity').value.trim();
      const problem = document.getElementById('problem').value.trim();
      const cause = document.getElementById('cause').value.trim();
      const action = document.getElementById('action').value.trim();
      const actor = document.getElementById('actor').value.trim();

      if (!barrier || !opportunity) {
        alert('Por favor complete al menos los campos de barrera y oportunidad.');
        return;
      }

      const tableBody = document.getElementById('entries').getElementsByTagName('tbody')[0];
      const newRow = tableBody.insertRow();
      newRow.insertCell(0).innerText = level;
      newRow.insertCell(1).innerText = barrier;
      newRow.insertCell(2).innerText = opportunity;
      newRow.insertCell(3).innerText = problem;
      newRow.insertCell(4).innerText = cause;
      newRow.insertCell(5).innerText = action;
      newRow.insertCell(6).innerText = actor;

      // Limpiar campos tras registrar
      document.getElementById('barrier').value = '';
      document.getElementById('opportunity').value = '';
      document.getElementById('problem').value = '';
      document.getElementById('cause').value = '';
      document.getElementById('action').value = '';
      document.getElementById('actor').value = '';
    }
  </script>
</body>
</html>
