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

    .button-container {
      margin-top: 50px;
    }

    button {
      padding: 10px 20px;
      margin: 10px;
      font-size: 16px;
      cursor: pointer;
    }
  </style>
</head>
<body>
  <h1>My Wedding</h1>

  <img src="images/rose.jpg" alt="Rose Flower" />

  <div class="button-container">
    <button onclick="window.location.href='bride.html'">Bride Guest</button>
    <button onclick="alert('Groom page not yet implemented')">Groom Guest</button>
  </div>
</body>
</html>
