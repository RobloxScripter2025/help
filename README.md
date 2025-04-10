<html>
<head>
    <link rel="stylesheet" href="https://fonts.googleapis.com/css?family=Nunito:400,700|Titan+One|Creepster|Satisfy|Eczar:700">
    <link rel="icon" href="https://cdn.glitch.global/50648a61-8fe9-4ce0-a01c-baff9438bbf2/bblogo.png">
    <meta name="description" content="Blooket Bot Join Game">
    <title>Join Game</title>
    <style>
        body {
            font-family: Nunito, sans-serif;
            background-color: #009449;
            display: flex;
            justify-content: center;
            align-items: center;
            height: 100vh;
            margin: 0;
        }
        .container {
            background-color: #fff;
            padding: 20px;
            border-radius: 8px;
            box-shadow: 0 4px 10px rgba(0, 0, 0, 0.1);
            width: 400px;
        }
        .normtext {
            font-size: 24px;
            color: #333;
            text-align: center;
        }
        .input-container {
            width: 100%;
            margin-bottom: 20px;
        }
        .input-field {
            width: 100%;
            padding: 10px;
            font-size: 20px;
            border-radius: 6px;
            border: 1px solid #ccc;
            margin-bottom: 10px;
            box-sizing: border-box;
        }
        .join-button {
            width: 100%;
            padding: 15px;
            background-color: #009449;
            color: white;
            font-size: 18px;
            border: none;
            border-radius: 6px;
            cursor: pointer;
            transition: transform 0.2s ease;
        }
        .join-button:hover {
            transform: scale(1.05);
        }
    </style>
</head>

<body>
    <div class="container">
        <div class="normtext">Join Game</div>
        <div class="input-container">
            <input id="gcode" class="input-field" placeholder="Enter Game ID" />
        </div>
        <div class="input-container">
            <input id="gname" class="input-field" placeholder="Enter Nickname" />
        </div>
        <div class="join-button" onclick="join()">Join</div>
        <div id="status" class="normtext" style="margin-top: 20px;">Status: Ready</div>
    </div>

    <script>
        function join() {
            var gameCode = document.getElementById("gcode").value;
            var nickname = document.getElementById("gname").value;
            
            if (gameCode && nickname) {
                document.getElementById("status").innerText = "Attempting to join...";
                
                // Simulate the join game request
                fetch(`https://blooket.com/join/${gameCode}`, {
                    method: 'POST',
                    headers: {
                        'Content-Type': 'application/json'
                    },
                    body: JSON.stringify({
                        nickname: nickname
                    })
                })
                .then(response => response.json())
                .then(data => {
                    // Assuming we get some kind of success or failure response
                    if (data.success) {
                        document.getElementById("status").innerText = "Successfully joined the game!";
                    } else {
                        document.getElementById("status").innerText = "Failed to join the game. Try again!";
                    }
                })
                .catch(error => {
                    console.error("Error:", error);
                    document.getElementById("status").innerText = "An error occurred. Please try again.";
                });
            } else {
                document.getElementById("status").innerText = "Please fill in both fields!";
            }
        }
    </script>
</body>
</html>
