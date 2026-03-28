<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Wach katbghini?</title>
    <style>
        :root {
            --soft-pink: #ffdae0;
            --deep-pink: #ff85a2;
            --white: #ffffff;
        }

        body {
            margin: 0;
            padding: 0;
            display: flex;
            justify-content: center;
            align-items: center;
            min-height: 100vh;
            background-color: var(--soft-pink);
            font-family: 'Segoe UI', Tahoma, Geneva, Verdana, sans-serif;
            overflow: hidden;
            text-align: center;
        }

        .container {
            background: rgba(255, 255, 255, 0.8);
            padding: 2rem;
            border-radius: 30px;
            box-shadow: 0 10px 30px rgba(255, 133, 162, 0.3);
            z-index: 10;
            max-width: 90%;
            width: 400px;
            transition: all 0.5s ease;
        }

        .bear-container {
            font-size: 80px;
            margin-bottom: 20px;
            animation: float 3s ease-in-out infinite;
        }

        @keyframes float {
            0%, 100% { transform: translateY(0); }
            50% { transform: translateY(-15px); }
        }

        h1 {
            color: var(--deep-pink);
            font-size: 2rem;
            margin-bottom: 30px;
        }

        .buttons {
            display: flex;
            justify-content: center;
            gap: 20px;
            position: relative;
            height: 50px;
        }

        .btn {
            padding: 12px 35px;
            font-size: 1.1rem;
            border-radius: 50px;
            cursor: pointer;
            border: none;
            transition: transform 0.2s, background 0.3s;
            font-weight: bold;
        }

        #yes-btn {
            background: linear-gradient(45deg, #ff85a2, #ffb3c1);
            color: white;
            box-shadow: 0 4px 15px rgba(255, 133, 162, 0.4);
        }

        #yes-btn:hover {
            transform: scale(1.1);
        }

        #no-btn {
            background: transparent;
            color: var(--deep-pink);
            border: 2px solid var(--deep-pink);
            position: absolute;
            left: 220px;
        }

        .heart {
            position: absolute;
            color: var(--deep-pink);
            font-size: 20px;
            user-select: none;
            pointer-events: none;
            animation: heartFloat 4s linear forwards;
        }

        @keyframes heartFloat {
            0% { transform: translateY(0) rotate(0deg); opacity: 1; }
            100% { transform: translateY(-100vh) rotate(360deg); opacity: 0; }
        }

        .success-msg {
            display: none;
            color: var(--deep-pink);
            font-size: 1.5rem;
            margin-top: 20px;
            font-weight: bold;
            animation: fadeIn 1s;
        }

        @keyframes fadeIn {
            from { opacity: 0; }
            to { opacity: 1; }
        }
    </style>
</head>
<body>

    <div class="container" id="main-card">
        <div class="bear-container">🧸</div>
        <h1 id="question">Wach katbghini?</h1>
        
        <div class="buttons" id="btn-group">
            <button class="btn" id="yes-btn" onclick="sayYes()">Ah</button>
            <button class="btn" id="no-btn" onmouseover="moveNo()">La</button>
        </div>
        
        <div class="success-msg" id="message">Ana tanbghik bzzaf❤️</div>
    </div>

    <script>
        // Create floating background hearts
        function createHeart() {
            const heart = document.createElement('div');
            heart.classList.add('heart');
            heart.innerHTML = '❤️';
            heart.style.left = Math.random() * 100 + 'vw';
            heart.style.animationDuration = Math.random() * 2 + 3 + 's';
            heart.style.fontSize = Math.random() * 20 + 10 + 'px';
            document.body.appendChild(heart);

            setTimeout(() => {
                heart.remove();
            }, 4000);
        }

        setInterval(createHeart, 300);

        // Dodge logic for the "No" button
        function moveNo() {
            const btn = document.getElementById('no-btn');
            const x = Math.random() * (window.innerWidth - btn.offsetWidth);
            const y = Math.random() * (window.innerHeight - btn.offsetHeight);
            
            btn.style.position = 'fixed';
            btn.style.left = x + 'px';
            btn.style.top = y + 'px';
        }

        // Click logic for "Yes"
        function sayYes() {
            document.getElementById('btn-group').style.display = 'none';
            document.getElementById('question').style.display = 'none';
            document.getElementById('message').style.display = 'block';
            
            // Extra heart burst
            for(let i=0; i<30; i++) {
                setTimeout(createHeart, i * 50);
            }
        }
    </script>
</body>
</html>
