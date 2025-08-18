<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>My Wedding</title>
    <link rel="stylesheet" href="styles.css">
</head>
<body>
    <div class="container">
        <h1>Welcome to My Wedding</h1>
        <p>Enter your first name:</p>
        <input type="text" id="firstNameInput" placeholder="First Name" oninput="searchNames()">
        <div id="results" class="results"></div>
    </div>

    <script src="script.js"></script>
</body>
</html>

body {
    font-family: Arial, sans-serif;
    background-color: #f4f4f4;
    margin: 0;
    padding: 0;
}

.container {
    max-width: 800px;
    margin: 50px auto;
    text-align: center;
    background-color: white;
    padding: 30px;
    box-shadow: 0 0 10px rgba(0, 0, 0, 0.1);
}

input {
    padding: 10px;
    font-size: 16px;
    width: 70%;
    margin-top: 10px;
}

h1 {
    color: #333;
}

.results {
    margin-top: 20px;
    display: grid;
    grid-template-columns: repeat(3, 1fr);
    gap: 15px;
    padding: 10px;
}

.result-item {
    background-color: #eaeaea;
    padding: 10px;
    border-radius: 5px;
}

.result-item p {
    margin: 5px 0;
}

const namesData = [
    { firstName: "John", lastName: "Doe", table: 1 },
    { firstName: "Jane", lastName: "Smith", table: 2 },
    // Add 300 names here, similar to the example
];

function searchNames() {
    const firstNameInput = document.getElementById('firstNameInput').value.toLowerCase();
    const resultsDiv = document.getElementById('results');
    
    // Clear previous results
    resultsDiv.innerHTML = '';

    // Filter names based on the input
    const filteredNames = namesData.filter(name =>
        name.firstName.toLowerCase().includes(firstNameInput)
    );

    // If no names match
    if (filteredNames.length === 0) {
        resultsDiv.innerHTML = '<p>No results found.</p>';
        return;
    }

    // Display the filtered results in 3 columns
    filteredNames.forEach(name => {
        const resultDiv = document.createElement('div');
        resultDiv.classList.add('result-item');
        resultDiv.innerHTML = `
            <p><strong>First Name:</strong> ${name.firstName}</p>
            <p><strong>Last Name:</strong> ${name.lastName}</p>
            <p><strong>Table Number:</strong> ${name.table}</p>
        `;
        resultsDiv.appendChild(resultDiv);
    });
}
