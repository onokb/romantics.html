<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Wach Katbghini?</title>
    <style>
        :root {
            --primary-pink: #ffafcc;
            --dark-pink: #fb6f92;
            --bg-soft: #fff0f3;
        }

        body {
            margin: 0;
            padding: 0;
            display: flex;
            justify-content: center;
            align-items: center;
            min-height: 100vh;
            background-color: var(--bg-soft);
            font-family: 'Segoe UI', Tahoma, Geneva, Verdana, sans-serif;
            overflow: hidden;
            text-align: center;
        }

        /* Floating Hearts Background */
        .heart-bg {
            position: absolute;
            top: 0;
            left: 0;
            width: 100%;
            height: 100%;
            pointer-events: none;
            z-index: 0;
        }

        .heart {
            position: absolute;
            color: var(--primary-pink);
            font-size: 20px;
            animation: float 6s linear infinite;
            opacity: 0;
        }

        @keyframes float {
            0% { transform: translateY(100vh) rotate(0deg); opacity: 1; }
            100% { transform: translateY(-10vh) rotate(360deg); opacity: 0; }
        }

        /* Main Card */
        .container {
            background: white;
            padding: 2rem;
            border-radius: 30px;
            box-shadow: 0 10px 30px rgba(251, 111, 146, 0.2);
            z-index: 10;
            max-width: 90%;
            width: 400px;
            transition: all 0.5s ease;
        }

        .bear-container {
            font-size: 80px;
            margin-bottom: 1rem;
        }

        h1 {
            color: var(--dark-pink);
            font-size: 2rem;
            margin-bottom: 2rem;
        }

        .buttons {
            display: flex;
            justify-content: center;
            align-items: center;
            gap: 20px;
            height: 60px;
        }

        /* Button Styling */
        #yesBtn {
            background: linear-gradient(45deg, #ffafcc, #fb6f92);
            color: white;
            border: none;
            padding: 12px 35px;
            border-radius: 50px;
            font-size: 1.2rem;
            font-weight: bold;
            cursor: pointer;
            box-shadow: 0 4px 15px rgba(251, 111, 146, 0.4);
            transition: transform 0.2s;
        }

        #yesBtn:hover {
            transform: scale(1.1);
        }

        #noBtn {
            background: transparent;
            color: var(--dark-pink);
            border: 2px solid var(--dark-pink);
            padding: 10px 30px;
            border-radius: 50px;
            font-size: 1.1rem;
            cursor: pointer;
            position: relative;
            transition: all 0.2s ease;
        }

        /* Success Message */
        #message {
            display: none;
            color: var(--dark-pink);
            font-size: 1.5rem;
            font-weight: bold;
            margin-top: 20px;
            animation: fadeIn 1s;
        }

        @keyframes fadeIn {
            from { opacity: 0; transform: translateY(10px); }
            to { opacity: 1; transform: translateY(0); }
        }
    </style>
</head>
<body>

    <div class="heart-bg" id="heartBg"></div>

    <div class="container" id="mainContainer">
        <div class="bear-container">🧸</div>
        <h1 id="question">Wach katbghini?</h1>
        
        <div class="buttons" id="btnGroup">
            <button id="yesBtn">Ah</button>
            <button id="noBtn">La</button>
        </div>

        <div id="message">Ana tanbghik bzzaf ❤️</div>
    </div>

    <script>
        const noBtn = document.getElementById('noBtn');
        const yesBtn = document.getElementById('yesBtn');
        const message = document.getElementById('message');
        const question = document.getElementById('question');
        const btnGroup = document.getElementById('btnGroup');
        const heartBg = document.getElementById('heartBg');

        // Function to create floating hearts
        function createHeart() {
            const heart = document.createElement('div');
            heart.classList.add('heart');
            heart.innerHTML = '❤️';
            heart.style.left = Math.random() * 100 + 'vw';
            heart.style.animationDuration = Math.random() * 3 + 3 + 's';
            heartBg.appendChild(heart);

            setTimeout(() => {
                heart.remove();
            }, 6000);
        }
        setInterval(createHeart, 400);

        // "La" button dodging logic
        noBtn.addEventListener('mouseover', () => {
            const x = Math.random() * (window.innerWidth - noBtn.offsetWidth);
            const y = Math.random() * (window.innerHeight - noBtn.offsetHeight);
            
            noBtn.style.position = 'absolute';
            noBtn.style.left = x + 'px';
            noBtn.style.top = y + 'px';
        });

        // "Ah" button click logic
        yesBtn.addEventListener('click', () => {
            question.style.display = 'none';
            btnGroup.style.display = 'none';
            message.style.display = 'block';
            
            // Shower of hearts effect
            for(let i=0; i<20; i++) {
                setTimeout(createHeart, i * 100);
            }
        });
    </script>
</body>
</html>
