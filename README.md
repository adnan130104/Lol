<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <title>League Points Table</title>
  <style>
    body {
      font-family: Arial, sans-serif;
      background: #f9f9f9;
    }
    h2 {
      text-align: center;
      margin-top: 20px;
    }
    table {
      width: 90%;
      margin: 20px auto;
      border-collapse: collapse;
      background: white;
      box-shadow: 0 0 10px rgba(0,0,0,0.1);
    }
    th, td {
      border: 1px solid #ddd;
      padding: 10px;
      text-align: center;
    }
    th {
      background-color: #4CAF50;
      color: white;
    }
    input[type="number"] {
      width: 50px;
      text-align: center;
    }
    button {
      display: block;
      margin: 20px auto;
      padding: 10px 20px;
      font-size: 16px;
      background-color: #4CAF50;
      color: white;
      border: none;
      cursor: pointer;
      border-radius: 5px;
    }
    button:hover {
      background-color: #45a049;
    }
  </style>
</head>
<body>

<h2>League Points Table</h2>

<table id="pointsTable">
  <thead>
    <tr>
      <th>Team</th>
      <th>Played</th>
      <th>Wins</th>
      <th>Draws</th>
      <th>Losses</th>
      <th>Points</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td>Team A</td>
      <td><input type="number" class="played" value="0"></td>
      <td><input type="number" class="wins" value="0"></td>
      <td><input type="number" class="draws" value="0"></td>
      <td><input type="number" class="losses" value="0"></td>
      <td class="points">0</td>
    </tr>
    <tr>
      <td>Team B</td>
      <td><input type="number" class="played" value="0"></td>
      <td><input type="number" class="wins" value="0"></td>
      <td><input type="number" class="draws" value="0"></td>
      <td><input type="number" class="losses" value="0"></td>
      <td class="points">0</td>
    </tr>
    <tr>
      <td>Team C</td>
      <td><input type="number" class="played" value="0"></td>
      <td><input type="number" class="wins" value="0"></td>
      <td><input type="number" class="draws" value="0"></td>
      <td><input type="number" class="losses" value="0"></td>
      <td class="points">0</td>
    </tr>
  </tbody>
</table>

<button onclick="updatePoints()">Update and Sort</button>

<script>
function updatePoints() {
  const table = document.getElementById("pointsTable").getElementsByTagName('tbody')[0];
  const rows = Array.from(table.rows);

  rows.forEach(row => {
    const played = parseInt(row.querySelector(".played").value) || 0;
    const wins = parseInt(row.querySelector(".wins").value) || 0;
    const draws = parseInt(row.querySelector(".draws").value) || 0;
    const losses = parseInt(row.querySelector(".losses").value) || 0;

    // Calculate points
    const points = (wins * 3) + (draws * 1);

    // Update points cell
    row.querySelector(".points").innerText = points;
  });

  // Sort the rows based on points (high to low)
  rows.sort((a, b) => {
    const pointsA = parseInt(a.querySelector(".points").innerText);
    const pointsB = parseInt(b.querySelector(".points").innerText);
    return pointsB - pointsA;
  });

  // Reattach sorted rows to the table
  rows.forEach(row => table.appendChild(row));
}
</script>

</body>
</html>
