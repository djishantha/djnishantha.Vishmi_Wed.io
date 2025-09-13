<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <h1 class="main-welcome">WELCOME !</h1>
    <h2>Harshana & Vishmi Wedding</h2>
<h3 class="hotel-name">JETWING BLUE - NEGOMBO</h3>
    <style>
        body {
    font-family: sans-serif;
    background-color: #87CEEB;
    text-align: center;
    padding: 0;
    margin: 0;
    box-sizing: border-box;
        }
.main-welcome {
    font-size: 64px; /* Double typical title (e.g. if original was ~32px) */
    color: blue;
    font-family: 'Cursive', 'Brush Script MT', sans-serif;
    margin-bottom: 10px;
}

h2 {
    font-size: 32px;
    margin: 10px 0;
}
.hotel-name {
    font-size: 16px; /* Half of h2 */
    color: green;
    font-family: 'Georgia', 'Times New Roman', serif;
    margin-top: 5px;
}
        .container {
    background-color: white;
    padding: 30px;
    border-radius: 10px;
    margin: 0 auto;
    max-width: 500px;
    width: 90%;
    box-sizing: border-box;
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
        #findCarParkBtn {
    margin-top: 20px;
    padding: 10px 15px;
    font-size: 16px;
    cursor: pointer;
    background-color: #28a745;
    color: white;
    border: none;
    border-radius: 5px;
}

#findCarParkBtn:hover {
    background-color: #1e7e34;
}

        #results {
            margin-top: 20px;
            font-size: 18px;
            color: #333;
        }
        .table-plan {
    margin-top: 30px;
    max-width: 100%;
    height: auto;
    border: 2px solid #ccc;
    border-radius: 8px;
    box-shadow: 0 0 10px rgba(0,0,0,0.1);
}
    </style>
</head>
<body>
    <div class="container">
        <h1>Find Your Table</h1>
        <input type="text" id="firstNameInput" placeholder="Enter your first name">
        <button id="findTableBtn">Table Number</button>
        <div id="results"></div>
        <img src="table-plan.jpg" alt="Wedding Table Plan" class="table-plan">
        <button id="findCarParkBtn">Find Your Car Park</button>
    </div>

    <script>
        const guests = [
            { firstName: "Kumudu", lastName: "Hewapathirana", table: 1 },
            { firstName: "Uditha", lastName: "Sirithunga", table: 1 },
            { firstName: "Shiromi", lastName: "Sirithunga", table: 1 },
            { firstName: "Milani", lastName: "Sirithunga", table: 1 },
            { firstName: "Latha", lastName: "Galappaththi", table: 1 },
             { firstName: "Shanthi", lastName: "Galappaththi", table: 1 },
            { firstName: "Thilani", lastName: "Dias", table: 1 },
            { firstName: "Ajith", lastName: "Dias", table: 1 },
            { firstName: "Rekha", lastName: "De Silva", table: 1 },
            { firstName: "Prabath", lastName: "Kasthuriarachchi", table: 1 },
            { firstName: "Akash", lastName: "Hewapathirana", table: 2 },
            { firstName: "Kanaki", lastName: "Hewapathirana", table: 2 },
            { firstName: "Dulshani", lastName: "Rajapakse", table: 2 },
            { firstName: "Kavisha", lastName: "Sirithunga", table: 2 },
            { firstName: "Wagisha", lastName: "Sirithunga", table: 2 },
            { firstName: "Sadew", lastName: "Dias", table: 2 },
            { firstName: "Yashith", lastName: "Dias", table: 2},
            { firstName: "Kisara", lastName: "Kasthuriarachchi", table: 2 },
            { firstName: "Gangi", lastName: "Galappaththi", table: 2 },
            { firstName: "Gangi", lastName: "Husband", table: 2 },
            { firstName: "Neetaha", lastName: "Jayakodi", table: 3 },
            { firstName: "Kalhari", lastName: "Fernando", table: 3 },
            { firstName: "Luxman", lastName: "Jeewantha", table: 3 },
            { firstName: "Indrananda", lastName: "Weerasena", table: 3 },
            { firstName: "Chandrika", lastName: "Welivita", table: 3 },
            { firstName: "Peshaka", lastName: "Ranganath", table: 3 },
         { firstName: "Peshaka", lastName: "Wife", table: 3 },
         { firstName: "Lakmali", lastName: "Rangani", table: 3 },
         { firstName: "Nayanagith", lastName: "Dhananjaya", table: 3 },
            { firstName: "Nayanajith", lastName: "Wife", table: 3 },
         { firstName: "Saranapala", lastName: "Saranapala", table: 3 },
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
    <script>
    document.getElementById("findCarParkBtn").addEventListener("click", function () {
        // Replace this URL with the actual car park location link
        window.open("https://maps.app.goo.gl/rW5yMQzisJt6ZzSM8", "_blank");
    });
</script>
</body>
</html>
