<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>My Simple Website</title>
  <link rel="stylesheet" href="styles.css">
</head>
<body>
  <header>
    <h1>Welcome to My Simple Website</h1>
  </header>
  <main>
    <p>This is a basic website hosted on GitHub Pages. Feel free to explore!</p>
    <button id="clickMe">Click Me!</button>
    <p id="message"></p>
  </main>
  <footer>
    <p>&copy; 2025 My Simple Website</p>
  </footer>
  <script src="script.js"></script>
</body>
</html>
body {
  font-family: Arial, sans-serif;
  text-align: center;
  margin: 0;
  padding: 0;
  background-color: #f4f4f9;
  color: #333;
}

header {
  background-color: #6200ea;
  color: white;
  padding: 1rem 0;
}

main {
  padding: 2rem;
}

button {
  background-color: #6200ea;
  color: white;
  border: none;
  padding: 0.5rem 1rem;
  cursor: pointer;
  border-radius: 5px;
}

button:hover {
  background-color: #3700b3;
}

footer {
  margin-top: 2rem;
  font-size: 0.9rem;
}
document.getElementById("clickMe").addEventListener("click", function() {
  document.getElementById("message").textContent = "You clicked the button! 🎉";
});
