<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <title>Harshana & Vishmi Wedding</title>
    <style>
        body {
            font-family: sans-serif;
            background-color: #87CEEB;
            text-align: center;
            padding: 50px;
        }

        .container {
            background-color: white;
            padding: 30px;
            border-radius: 10px;
            display: inline-block;
            box-shadow: 0 0 10px rgba(0, 0, 0, 0.1);
        }

        input {
            padding: 10px;
            font-size: 16px;
            margin: 10px 5px;
        }

        button {
            padding: 10px 15px;
            font-size: 16px;
            cursor: pointer;
            background-color: #007bff;
            color: white;
            border: none;
            border-radius: 5px;
        }

        button:hover {
            background-color: #0056b3;
        }

        #results {
            margin-top: 20px;
            font-size: 18px;
            color: #333;
        }
    </style>
</head>
<body>
    <div class="container">
        <h1>Harshana & Vishmi Wedding</h1>
        <input type="text" id="firstNameInput" placeholder="Enter your first name">
        <button id="findTableBtn">Table Number</button>
        <div id="results"></div>
    </div>

    <script>
        const guests = [
            { firstName: "Kumudu", lastName: "Hewapathirana", table: 1 },
            { firstName: "Akash", lastName: "Hewapathirana", table: 2 },
            { firstName: "Neetaha", lastName: "Jayakodi", table: 3 },
            { firstName: "Kalhari", lastName: "Fernando", table: 4 },
            { firstName: "Luxman", lastName: "Jeewantha", table: 3 },
            { firstName: "Uditha", lastName: "Sirithunga", table: 3 },
            { firstName: "Shiromi", lastName: "Sirithunga", table: 3 }
        ];

        document.addEventListener("DOMContentLoaded", function () {
            const button = document.getElementById("findTableBtn");
            button.addEventListener("click", function () {
                const input = document.getElementById("firstNameInput").value.trim().toLowerCase();
                const resultsDiv = document.getElementById("results");
                resultsDiv.innerHTML = "";

                if (!input) {
                    resultsDiv.textContent = "Please enter your first name.";
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
            });
        });
    </script>
</body>
</html>
