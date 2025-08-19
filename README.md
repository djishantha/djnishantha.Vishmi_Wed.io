<!DOCTYPE html>
<html>
<head>
  <title>My Wedding</title>
  <style>
    body {
      background-color: #ffe4e1; /* rose color */
      text-align: center;
      font-family: Arial, sans-serif;
    }

    h1 {
      font-size: 30px;
      text-transform: uppercase;
      color: blue;
      margin-top: 50px;
    }

    img {
      margin-top: 30px;
      width: 150px;
      height: auto;
    }

    .button-container, .form-container {
      margin-top: 40px;
    }

    button {
      padding: 10px 20px;
      margin: 10px;
      font-size: 16px;
      cursor: pointer;
    }

    .form-container {
      display: none;
    }

    label {
      font-size: 18px;
      margin-right: 10px;
    }

    input[type="text"] {
      padding: 8px;
      font-size: 16px;
    }
  </style>
</head>
<body>

  <h1>My Wedding</h1>
  <img src="images/rose.jpg" alt="Rose Flower" />

  <div class="button-container">
    <button onclick="showBrideForm()">Bride Guest</button>
    <button onclick="alert('Groom section coming soon')">Groom Guest</button>
  </div>

  <div class="form-container" id="brideForm">
    <label for="fname">Enter your first name</label>
    <input type="text" id="fname" name="fname" />
    <button onclick="goToExcel()">GO</button>
  </div>

  <script>
    function showBrideForm() {
      document.getElementById('brideForm').style.display = 'block';
    }

    function goToExcel() {
      const name = document.getElementById('fname').value.trim();
      if (name === '') {
        alert('Please enter your name.');
        return;
      }
      // Redirect to Excel file hosted on GitHub
      window.location.href = 'files/table.xlsx';
    }
  </script>

</body>
</html>
