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

 <img src="https://upload.wikimedia.org/wikipedia/commons/thumb/f/fb/Rose_red_1.jpg/320px-Rose_red_1.jpg" alt="Rose Flower" />

  <div class="button-container">
    <button onclick="window.location.href='guest.html'">Bride Guest</button>
    <button onclick="window.location.href='guest.html'">Groom Guest</button>
  </div>
</body>
</html>
<!DOCTYPE html>
<html>
<head>
  <title>Wedding Guest</title>
  <style>
    body {
      background-color: #ffe4e1;
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

    .form-container {
      margin-top: 50px;
    }

    label {
      font-size: 18px;
      margin-right: 10px;
    }

    input[type="text"] {
      padding: 8px;
      font-size: 16px;
    }

    button {
      padding: 8px 15px;
      font-size: 16px;
      margin-left: 10px;
      cursor: pointer;
    }
  </style>
</head>
<body>
  <h1>My Wedding</h1>

  <img src="images/rose.jpg" alt="Rose Flower" />

  <div class="form-container">
    <label for="fname">Enter your first name</label>
    <input type="text" id="fname" name="fname" />
    <button onclick="alert('Welcome ' + document.getElementById('fname').value + '!')">GO</button>
  </div>
</body>
</html>

