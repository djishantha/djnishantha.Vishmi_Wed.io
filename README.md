
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>My Wedding</title>
    <link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/6.4.0/css/all.min.css">
    <style>
        * {
            margin: 0;
            padding: 0;
            box-sizing: border-box;
            font-family: 'Segoe UI', Tahoma, Geneva, Verdana, sans-serif;
        }
        
        body {
            background: linear-gradient(135deg, #ffe8e8 0%, #ffd1dc 100%);
            color: #333;
            min-height: 100vh;
            padding: 20px;
        }
        
        .container {
            max-width: 1000px;
            margin: 0 auto;
            background-color: rgba(255, 255, 255, 0.9);
            border-radius: 15px;
            box-shadow: 0 10px 30px rgba(0, 0, 0, 0.1);
            padding: 30px;
            position: relative;
            overflow: hidden;
        }
        
        .header {
            text-align: center;
            margin-bottom: 40px;
            padding-bottom: 20px;
            border-bottom: 2px solid #ff7eb3;
        }
        
        h1 {
            font-size: 30px;
            text-transform: uppercase;
            color: #1e88e5;
            margin-bottom: 15px;
            text-shadow: 2px 2px 4px rgba(0, 0, 0, 0.1);
        }
        
        .subtitle {
            font-size: 18px;
            color: #ff4081;
            font-style: italic;
        }
        
        .couple-img {
            width: 200px;
            height: 200px;
            border-radius: 50%;
            object-fit: cover;
            border: 5px solid #ff9ab0;
            margin: 20px auto;
            display: block;
            box-shadow: 0 5px 15px rgba(0, 0, 0, 0.2);
        }
        
        .details {
            display: flex;
            justify-content: space-around;
            flex-wrap: wrap;
            margin: 30px 0;
        }
        
        .detail-card {
            background: linear-gradient(135deg, #a7d7f9 0%, #c9e6ff 100%);
            border-radius: 10px;
            padding: 20px;
            margin: 10px;
            flex: 1;
            min-width: 250px;
            text-align: center;
            box-shadow: 0 5px 15px rgba(0, 0, 0, 0.1);
        }
        
        .detail-card h3 {
            color: #1e88e5;
            margin-bottom: 10px;
        }
        
        .data-section {
            background: linear-gradient(135deg, #ffd1dc 0%, #ffe8e8 100%);
            padding: 25px;
            border-radius: 10px;
            margin: 30px 0;
            text-align: center;
        }
        
        .data-section h2 {
            color: #d81b60;
            margin-bottom: 20px;
        }
        
        .input-group {
            display: flex;
            justify-content: center;
            margin: 20px 0;
        }
        
        input[type="text"] {
            padding: 12px 15px;
            border: 2px solid #ff9ab0;
            border-radius: 5px 0 0 5px;
            width: 300px;
            font-size: 16px;
        }
        
        button {
            background: #1e88e5;
            color: white;
            border: none;
            padding: 12px 25px;
            border-radius: 0 5px 5px 0;
            cursor: pointer;
            font-size: 16px;
            font-weight: bold;
            transition: background 0.3s;
        }
        
        button:hover {
            background: #1565c0;
        }
        
        .instructions {
            background-color: #e3f2fd;
            padding: 15px;
            border-radius: 8px;
            margin-top: 20px;
            font-size: 14px;
        }
        
        .hearts {
            position: absolute;
            top: 0;
            left: 0;
            width: 100%;
            height: 100%;
            pointer-events: none;
            z-index: -1;
        }
        
        .heart {
            position: absolute;
            font-size: 20px;
            color: #ff9ab0;
            opacity: 0.6;
        }
        
        footer {
            text-align: center;
            margin-top: 40px;
            color: #777;
            font-size: 14px;
        }
        
        @media (max-width: 768px) {
            .input-group {
                flex-direction: column;
                align-items: center;
            }
            
            input[type="text"] {
                border-radius: 5px;
                margin-bottom: 10px;
                width: 100%;
                max-width: 300px;
            }
            
            button {
                border-radius: 5px;
                width: 100%;
                max-width: 300px;
            }
        }
    </style>
</head>
<body>
    <div class="container">
        <div class="header">
            <h1>My Wedding</h1>
            <p class="subtitle">Sarah & Michael - June 12, 2023</p>
        </div>
        
        <img src="https://images.unsplash.com/photo-1519225421980-715cb0215aed?ixlib=rb-1.2.1&auto=format&fit=crop&w=500&q=80" alt="Happy Couple" class="couple-img">
        
        <div class="details">
            <div class="detail-card">
                <h3><i class="fas fa-church"></i> Ceremony</h3>
                <p>St. Mary's Church</p>
                <p>3:00 PM</p>
            </div>
            
            <div class="detail-card">
                <h3><i class="fas fa-utensils"></i> Reception</h3>
                <p>Grand Hotel Ballroom</p>
                <p>6:00 PM</p>
            </div>
            
            <div class="detail-card">
                <h3><i class="fas fa-gift"></i> Registry</h3>
                <p>Bed Bath & Beyond</p>
                <p>Amazon Wedding Registry</p>
            </div>
        </div>
        
        <div class="data-section">
            <h2><i class="fas fa-spreadsheet"></i> Wedding Guest Information</h2>
            <p>Click the button below to retrieve the special cell value from our guest spreadsheet</p>
            
            <div class="input-group">
                <input type="text" id="cellValue" placeholder="Cell value will appear here" readonly>
                <button onclick="getCellValue()">
                    <i class="fas fa-mobile-alt"></i> MY CELL
                </button>
            </div>
            
            <div class="instructions">
                <p><strong>Note:</strong> This button retrieves data from our Google Sheets guest list. In a real implementation, it would fetch the value from cell A2 of the specified spreadsheet.</p>
            </div>
        </div>
        
        <footer>
            <p>Made with <i class="fas fa-heart" style="color: #ff4081;"></i> for our wedding</p>
        </footer>
        
        <div class="hearts" id="hearts"></div>
    </div>

    <script>
        // Function to create floating hearts
        function createHearts() {
            const heartsContainer = document.getElementById('hearts');
            const numberOfHearts = 25;
            
            for (let i = 0; i < numberOfHearts; i++) {
                const heart = document.createElement('div');
                heart.innerHTML = '<i class="fas fa-heart"></i>';
                heart.classList.add('heart');
                
                // Random position
                heart.style.left = Math.random() * 100 + '%';
                heart.style.top = Math.random() * 100 + '%';
                
                // Random animation
                const duration = Math.random() * 5 + 5;
                heart.style.animation = `float ${duration}s ease-in-out infinite`;
                
                heartsContainer.appendChild(heart);
            }
        }
        
        // Function to simulate getting cell value (for demonstration)
        function getCellValue() {
            const inputField = document.getElementById('cellValue');
            
            // Show loading state
            inputField.value = "Loading...";
            inputField.style.color = "#1e88e5";
            
            // In a real implementation, you would fetch data from Google Sheets here
            // For demonstration, we'll simulate a delay and show a sample value
            setTimeout(() => {
                // This is a simulation - in reality you would fetch from the Google Sheets API
                inputField.value = "Sarah's Cell: (555) 123-4567";
                inputField.style.color = "#d81b60";
                
                // Celebration effect
                confettiEffect();
            }, 1500);
        }
        
        // Simple celebration effect
        function confettiEffect() {
            const confettiColors = ['#ff9ab0', '#a7d7f9', '#c9e6ff', '#ffd1dc', '#1e88e5'];
            const container = document.querySelector('.container');
            
            for (let i = 0; i < 50; i++) {
                const confetti = document.createElement('div');
                confetti.style.position = 'absolute';
                confetti.style.width = '10px';
                confetti.style.height = '10px';
                confetti.style.backgroundColor = confettiColors[Math.floor(Math.random() * confettiColors.length)];
                confetti.style.borderRadius = '50%';
                confetti.style.left = Math.random() * 100 + '%';
                confetti.style.top = '-20px';
                confetti.style.zIndex = '9999';
                confetti.style.opacity = '0.8';
                
                container.appendChild(confetti);
                
                // Animate confetti
                const animation = confetti.animate([
                    { transform: 'translateY(0) rotate(0deg)', opacity: 0.8 },
                    { transform: `translateY(${window.innerHeight}px) rotate(${Math.random() * 360}deg)`, opacity: 0 }
                ], {
                    duration: Math.random() * 2000 + 2000,
                    easing: 'cubic-bezier(0.1, 0.8, 0.3, 1)'
                });
                
                // Remove confetti after animation completes
                animation.onfinish = () => {
                    confetti.remove();
                };
            }
        }
        
        // Initialize the page
        window.onload = function() {
            createHearts();
            
            // Add animation keyframes dynamically
            const style = document.createElement('style');
            style.textContent = `
                @keyframes float {
                    0%, 100% { transform: translate(0, 0) rotate(0deg); }
                    25% { transform: translate(5px, 5px) rotate(5deg); }
                    50% { transform: translate(10px, 0px) rotate(0deg); }
                    75% { transform: translate(5px, -5px) rotate(-5deg); }
                }
            `;
            document.head.appendChild(style);
        };
    </script>
</body>
</html>
