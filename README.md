<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Wait... I have a question!</title>
    <style>
        body {
            font-family: 'Poppins', sans-serif;
            background-color: #fff0f3;
            display: flex;
            flex-direction: column;
            align-items: center;
            justify-content: center;
            height: 100vh;
            margin: 0;
            overflow: hidden; /* Prevents scrollbars when Yes gets huge */
            text-align: center;
        }

        .container {
            position: relative;
            z-index: 2;
        }

        img {
            width: 250px;
            border-radius: 20px;
            box-shadow: 0 10px 20px rgba(0,0,0,0.1);
            margin-bottom: 20px;
        }

        h1 {
            color: #ff4d6d;
            font-size: 2rem;
            margin-bottom: 30px;
        }

        .btn-group {
            display: flex;
            gap: 20px;
            justify-content: center;
            align-items: center;
        }

        #yesBtn {
            background-color: #ff4d6d;
            color: white;
            border: none;
            padding: 15px 30px;
            font-size: 1.2rem;
            font-weight: bold;
            border-radius: 50px;
            cursor: pointer;
            box-shadow: 0 5px 15px rgba(255, 77, 109, 0.4);
            transition: transform 0.2s ease-out; /* Smooth growth */
        }

        #noBtn {
            background-color: #ced4da;
            color: #495057;
            border: none;
            padding: 15px 30px;
            font-size: 1.2rem;
            border-radius: 50px;
            cursor: pointer;
        }

        #celebration {
            display: none;
        }
    </style>
</head>
<body>

    <div id="main-content" class="container">
        <img src="https://media.giphy.com/media/v1.Y2lkPTc5MGI3NjExOHpueG5xZ3R6Z3R6Z3R6Z3R6Z3R6Z3R6Z3R6Z3R6Z3R6Z3R6JmVwPXYxX2ludGVybmFsX2dpZl9ieV9pZCZjdD1n/c76IJLufpN762clOW7/giphy.gif" alt="Valentine Cartoon">
        
        <h1 id="questionText">Will you be my Valentine? 🌹</h1>

        <div class="btn-group">
            <button id="yesBtn" onclick="accept()">Yes</button>
            <button id="noBtn" onclick="growYes()">No</button>
        </div>
    </div>

    <div id="celebration" class="container">
        <h1>Yay! I knew you'd say yes! ❤️</h1>
        <img src="https://media.giphy.com/media/v1.Y2lkPTc5MGI3NjExOHpueG5xZ3R6Z3R6Z3R6Z3R6Z3R6Z3R6Z3R6Z3R6Z3R6JmVwPXYxX2ludGVybmFsX2dpZl9ieV9pZCZjdD1n/lTQF0ODLLJHzaOBCfy/giphy.gif" alt="Celebration">
    </div>

    <script>
        let currentScale = 1;
        const noMessages = ["Are you sure?", "Think again!", "Wait, look at the Yes button!", "It's getting bigger...", "You have no choice now!", "Resistance is futile!"];
        let msgIndex = 0;

        function growYes() {
            const yesBtn = document.getElementById('yesBtn');
            const noBtn = document.getElementById('noBtn');
            
            // The logic: Increase scale significantly (20x total over a few clicks)
            currentScale += 3.5; 
            yesBtn.style.transform = `scale(${currentScale})`;
            
            // Move the No button slightly to make it harder to click
            const x = Math.random() * 50 - 25;
            const y = Math.random() * 50 - 25;
            noBtn.style.transform = `translate(${x}px, ${y}px)`;

            // Cycle through funny messages
            noBtn.innerText = noMessages[msgIndex];
            msgIndex = (msgIndex + 1) % noMessages.length;
        }

        function accept() {
            document.getElementById('main-content').style.display = 'none';
            document.getElementById('celebration').style.display = 'block';
            document.body.style.backgroundColor = '#ffccd5';
        }
    </script>
</body>
</html>
