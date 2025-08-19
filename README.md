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

  <!-- Google Visualization API -->
  <script type="text/javascript" src="https://www.gstatic.com/charts/loader.js"></script>

  <script>
    function loadCell() {
      const queryString = encodeURIComponent("SELECT A");
      const sheetID = "1-FtZ-6aXhbLoSqkEdQvJrZFiVwnme9wTpQlLpYTTDf4";
      const gid = "0"; // GID of the first sheet
      const url = `https://docs.google.com/spreadsheets/d/${sheetID}/gviz/tq?gid=${gid}&tq=${queryString}`;

      fetch(url)
        .then(res => res.text())
        .then(data => {
          // Clean JSON response
          const json = JSON.parse(data.substring(47).slice(0, -2));
          const cellA2 = json.table.rows[1]?.c[0]?.v || "Not found";
          document.getElementById("cellValue").value = cellA2;
        })
        .catch(err => {
          alert("Failed to load data from Google Sheet.");
          console.error(err);
        });
    }
  </script>

</body>
</html>
