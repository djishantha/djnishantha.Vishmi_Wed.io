<!DOCTYPE html>
<html>
<head>
  <title>My Wedding</title>
  <style>
    body {
      background-color: #ffe4e1; /* rose color */
      text-align: center;
      font-family: Arial, sans-serif;
      padding-top: 50px;
    }

    h1 {
      font-size: 30px;
      text-transform: uppercase;
      color: blue;
    }

    .cell-container {
      margin-top: 40px;
    }

    input[type="text"] {
      padding: 8px;
      font-size: 16px;
      width: 200px;
    }

    button {
      padding: 10px 20px;
      font-size: 16px;
      margin-right: 10px;
      cursor: pointer;
    }
  </style>
</head>
<body>

  <h1>My Wedding</h1>

  <div class="cell-container">
    <button onclick="loadCell()">MY CELL</button>
    <input type="text" id="cellValue" readonly />
  </div>

  <!-- Load Google Charts library -->
  <script type="text/javascript" src="https://www.gstatic.com/charts/loader.js"></script>

  <script>
    function loadCell() {
      // Query only column A from the sheet
      const query = encodeURIComponent("SELECT A");
      const sheetURL = `https://docs.google.com/spreadsheets/d/e/2PACX-1vSzV0tWqebYZW81ZwYVlyNui2pIuZvFYgLdBOrSzq58mfDHbDY8l5YX43kNPoXqWA5_qjGW-LzbGGoI/gviz/tq?gid=0&tq=${query}`;

      fetch(sheetURL)
        .then(res => res.text())
        .then(text => {
          const json = JSON.parse(text.substring(47).slice(0, -2)); // Trim padding
          const value = json.table.rows[1]?.c[0]?.v || "Not Found"; // Cell A2
          document.getElementById("cellValue").value = value;
        })
        .catch(err => {
          console.error("Failed to load sheet:", err);
          alert("Unable to load cell data.");
        });
    }
  </script>

</body>
</html>
