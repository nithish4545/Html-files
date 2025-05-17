<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <title>Quality Control - Manufacturing</title>
  <style>
    body {
      font-family: Arial, sans-serif;
      margin: 40px;
    }
    label, input, textarea {
      display: block;
      margin-bottom: 10px;
      width: 300px;
    }
    table {
      margin-top: 20px;
      border-collapse: collapse;
      width: 80%;
    }
    th, td {
      padding: 8px 12px;
      border: 1px solid #ccc;
    }
    th {
      background-color: #f4f4f4;
    }
    .success {
      color: green;
    }
  </style>
</head>
<body>

  <h1>Quality Control Log</h1>

  <form id="qcForm">
    <label>Product ID:
      <input type="text" id="productId" required>
    </label>
    <label>Inspector Name:
      <input type="text" id="inspector" required>
    </label>
    <label>Defect Description:
      <textarea id="defect" required></textarea>
    </label>
    <button type="submit">Log Defect</button>
  </form>

  <p class="success" id="successMsg"></p>

  <table id="defectTable">
    <thead>
      <tr>
        <th>Timestamp</th>
        <th>Product ID</th>
        <th>Inspector</th>
        <th>Defect</th>
      </tr>
    </thead>
    <tbody></tbody>
  </table>

  <script>
    const form = document.getElementById('qcForm');
    const tableBody = document.querySelector('#defectTable tbody');
    const successMsg = document.getElementById('successMsg');

    form.addEventListener('submit', function (e) {
      e.preventDefault();
      const productId = document.getElementById('productId').value.trim();
      const inspector = document.getElementById('inspector').value.trim();
      const defect = document.getElementById('defect').value.trim();

      if (!productId || !inspector || !defect) return;

      const now = new Date().toLocaleString();
      const row = tableBody.insertRow();
      row.insertCell(0).textContent = now;
      row.insertCell(1).textContent = productId;
      row.insertCell(2).textContent = inspector;
      row.insertCell(3).textContent = defect;

      successMsg.textContent = "Defect logged successfully.";

      form.reset();
      setTimeout(() => successMsg.textContent = '', 3000);
    });
  </script>

</body>
</html>