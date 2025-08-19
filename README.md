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
    <button onclick="loadExcel()">MY CELL</button>
    <input type="text" id="cellValue" readonly />
  </div>

  <!-- SheetJS library for reading XLSX files -->
  <script src="https://cdn.jsdelivr.net/npm/xlsx/dist/xlsx.full.min.js"></script>

  <script>
    async function loadExcel() {
      try {
        // Fetch the Excel file hosted on GitHub
        const response = await fetch('files/table.xlsx');
        const arrayBuffer = await response.arrayBuffer();

        const workbook = XLSX.read(arrayBuffer, { type: "array" });
        const sheet = workbook.Sheets["Sheet1"];
        const cellA2 = sheet["A2"] ? sheet["A2"].v : "Not Found";

        document.getElementById("cellValue").value = cellA2;
      } catch (error) {
        alert("Failed to load Excel file: " + error);
      }
    }
  </script>

</body>
</html>
