<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <title>My Wedding</title>
    <link rel="stylesheet" href="style.css">
</head>
<body>
    <div class="container">
        <h1>Welcome to Our Wedding!</h1>
        <p>Enter your first name to find your table number:</p>
        <input type="text" id="firstNameInput" placeholder="First Name">
        <button onclick="findTable()">Table Number</button>
        <div id="results"></div>
    </div>

    <script src="script.js"></script>
</body>
</html>
body {
    font-family: Arial, sans-serif;
    background-color: #f0f4f8;
    text-align: center;
    padding: 50px;
}

.container {
    background: white;
    padding: 30px;
    border-radius: 10px;
    display: inline-block;
    box-shadow: 0 0 10px rgba(0,0,0,0.1);
}

input {
    padding: 10px;
    font-size: 16px;
    margin-right: 10px;
}

button {
    padding: 10px 20px;
    font-size: 16px;
    background-color: #6a5acd;
    color: white;
    border: none;
    border-radius: 5px;
    cursor: pointer;
}

button:hover {
    background-color: #5a4bbd;
}

#results {
    margin-top: 20px;
    font-size: 18px;
}
// Guest list stored in JavaScript
const guests = [
    { firstName: "John", lastName: "Doe", table: 3 },
    { firstName: "Jane", lastName: "Smith", table: 5 },
    { firstName: "John", lastName: "Smith", table: 1 },
    { firstName: "Alice", lastName: "Johnson", table: 2 },
    { firstName: "Michael", lastName: "Brown", table: 4 }
];

function findTable() {
    const input = document.getElementById("firstNameInput").value.trim().toLowerCase();
    const resultsDiv = document.getElementById("results");
    resultsDiv.innerHTML = "";

    if (!input) {
        resultsDiv.textContent = "Please enter a first name.";
        return;
    }

    const matches = guests.filter(guest => guest.firstName.toLowerCase() === input);

    if (matches.length === 0) {
        resultsDiv.textContent = "No guest found with that first name.";
    } else {
        const list = document.createElement("ul");
        matches.forEach(guest => {
            const item = document.createElement("li");
            item.textContent = `${guest.firstName} ${guest.lastName} - Table ${guest.table}`;
            list.appendChild(item);
        });
        resultsDiv.appendChild(list);
    }
}
