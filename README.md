<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Wach Katbghini? 💕</title>
    <style>
        * {
            margin: 0;
            padding: 0;
            box-sizing: border-box;
        }

        body {
            font-family: 'Poppins', sans-serif;
            background: linear-gradient(135deg, #ff9a9e 0%, #fecfef 50%, #fecfef 100%);
            min-height: 100vh;
            overflow-x: hidden;
            position: relative;
        }

        .container {
            display: flex;
            flex-direction: column;
            align-items: center;
            justify-content: center;
            min-height: 100vh;
            padding: 20px;
            position: relative;
            z-index: 10;
        }

        .hearts-bg {
            position: fixed;
            top: 0;
            left: 0;
            width: 100%;
            height: 100%;
            pointer-events: none;
            z-index: 1;
        }

        .heart {
            position: absolute;
            color: rgba(255, 105, 180, 0.6);
            font-size: 20px;
            animation: float 6s infinite linear;
        }

        @keyframes float {
            0% {
                transform: translateY(100vh) rotate(0deg);
                opacity: 1;
            }
            100% {
                transform: translateY(-100px) rotate(360deg);
                opacity: 0;
            }
        }

        .teddy-container {
            text-align: center;
            margin-bottom: 30px;
            transition: all 0.5s cubic-bezier(0.68, -0.55, 0.265, 1.55);
            transform-origin: center;
        }

        .teddy {
            width: 200px;
            height: 200px;
            background: 
                radial-gradient(circle at 40% 40%, #ff6b9d 20%, transparent 20%),
                radial-gradient(circle at 60% 40%, #ff8fab 20%, transparent 20%),
                radial-gradient(circle at 50% 70%, #ff4d94 25%, transparent 25%),
                radial-gradient(circle at 30% 60%, #ffb3d1 15%, transparent 15%),
                radial-gradient(circle at 70% 60%, #ffb3d1 15%, transparent 15%),
                linear-gradient(45deg, #ff6b9d 0%, #ff8fab 100%);
            border-radius: 50% 50% 40% 40%;
            position: relative;
            margin: 0 auto 20px;
            box-shadow: 
                0 20px 40px rgba(255, 107, 157, 0.3),
                inset 0 -10px 20px rgba(255, 255, 255, 0.2);
            animation: bounce 2s infinite;
        }

        @keyframes bounce {
            0%, 20%, 50%, 80%, 100% { transform: translateY(0); }
            40% { transform: translateY(-10px); }
            60% { transform: translateY(-5px); }
        }

        .teddy::before {
            content: '🐻';
            position: absolute;
            top: 20%;
            left: 50%;
            transform: translate(-50%, -50%);
            font-size: 60px;
            z-index: 2;
        }

        .teddy::after {
            content: '';
            position: absolute;
            bottom: -20px;
            left: 50%;
            transform: translateX(-50%);
            width: 0;
            height: 0;
            border-left: 25px solid transparent;
            border-right: 25px solid transparent;
            border-top: 25px solid #ff6b9d;
            animation: tailWag 2s infinite;
        }

        @keyframes tailWag {
            0%, 100% { transform: translateX(-50%) rotate(-10deg); }
            50% { transform: translateX(-50%) rotate(10deg); }
        }

        .main-text {
            font-size: clamp(24px, 5vw, 36px);
            font-weight: 600;
            color: #ff4d6d;
            margin-bottom: 40px;
            text-shadow: 0 2px 10px rgba(255, 77, 109, 0.3);
            animation: glow 2s ease-in-out infinite alternate;
        }

        @keyframes glow {
            from { text-shadow: 0 2px 10px rgba(255, 77, 109, 0.3); }
            to { text-shadow: 0 2px 20px rgba(255, 77, 109, 0.6), 0 0 30px rgba(255, 107, 157, 0.4); }
        }

        .buttons {
            display: flex;
            gap: 20px;
            flex-wrap: wrap;
            justify-content: center;
        }

        .btn {
            padding: 15px 30px;
            font-size: 18px;
            font-weight: 600;
            border: none;
            border-radius: 50px;
            cursor: pointer;
            transition: all 0.3s ease;
            text-transform: uppercase;
            letter-spacing: 1px;
            position: relative;
            overflow: hidden;
            min-width: 120px;
        }

        .btn-ah {
            background: linear-gradient(45deg, #ff6b9d, #ff8fab, #ff9a9e);
            color: white;
            box-shadow: 0 10px 30px rgba(255, 107, 157, 0.4);
        }

        .btn-ah:hover {
            transform: translateY(-5px) scale(1.05);
            box-shadow: 0 15px 40px rgba(255, 107, 157, 0.6);
        }

        .btn-la {
            background: transparent;
            color: #ff6b9d;
            border: 3px solid #ff6b9d;
            backdrop-filter: blur(10px);
        }

        .btn-la:hover {
            background: rgba(255, 107, 157, 0.1);
            transform: scale(1.1);
        }

        .response {
            position: fixed;
            top: 50%;
            left: 50%;
            transform: translate(-50%, -50%);
            font-size: clamp(28px, 6vw, 42px);
            font-weight: 700;
            color: #ff4d6d;
            text-align: center;
            opacity: 0;
            transform: translate(-50%, -50%) scale(0.5);
            z-index: 20;
            text-shadow: 0 2px 20px rgba(255, 77, 109, 0.5);
            animation: responseAnim 0.8s ease-out forwards;
            max-width: 90vw;
        }

        @keyframes responseAnim {
            0% { opacity: 0; transform: translate(-50%, -50%) scale(0.5); }
            50% { opacity: 1; transform: translate(-50%, -50%) scale(1.1); }
            100% { opacity: 1; transform: translate(-50%, -50%) scale(1); }
        }

        .move-away {
            animation: moveAway 1s ease-out forwards;
        }

        @keyframes moveAway {
            0% { transform: translateY(0) scale(1); }
            100% { transform: translateX(100vw) translateY(-50px) scale(0.5) rotate(30deg); opacity: 0; }
        }

        @media (max-width: 768px) {
            .buttons { flex-direction: column; align-items: center; }
            .btn { width: 200px; }
            .teddy { width: 150px; height: 150px; }
            .teddy::before { font-size: 45px; }
        }

        .hearts-explosion {
            position: fixed;
            top: 50%;
            left: 50%;
            pointer-events: none;
            z-index: 30;
            transform: translate(-50%, -50%);
        }

        .heart-explosion {
            position: absolute;
            font-size: 24px;
            color: #ff69b4;
            animation: explode 1s ease-out forwards;
        }

        @keyframes explode {
            0% {
                transform: translate(0, 0) scale(0) rotate(0deg);
                opacity: 1;
            }
            100% {
                transform: translate(var(--dx), var(--dy)) scale(1) rotate(720deg);
                opacity: 0;
            }
        }
    </style>
</head>
<body>
    <div class="hearts-bg" id="heartsBg"></div>
    
    <div class="container">
        <div class="teddy-container" id="teddyContainer">
            <div class="teddy"></div>
            <div class="main-text">Wach katbghini? 💕</div>
        </div>
        
        <div class="buttons">
            <button class="btn btn-ah" onclick="handleAh()">Ah 😍</button>
            <button class="btn btn-la" id="laBtn" onmouseover="handleLaHover(true)" onmouseout="handleLaHover(false)">La 🙄</button>
        </div>
    </div>

    <div class="response" id="response"></div>
    <div class="hearts-explosion" id="heartsExplosion"></div>

    <script>
        // Floating hearts background
        function createFloatingHeart() {
            const heart = document.createElement('div');
            heart.className = 'heart';
            heart.innerHTML = '💕';
            heart.style.left = Math.random() * 100 + '%';
            heart.style.animationDuration = (Math.random() * 3 + 4) + 's';
            heart.style.animationDelay = Math.random() * 2 + 's';
            document.getElementById('heartsBg').appendChild(heart);

            setTimeout(() => {
                heart.remove();
            }, 7000);
        }

        // Create hearts continuously
        setInterval(createFloatingHeart, 300);

        // Ah button handler
        function handleAh() {
            document.getElementById('response').innerHTML = 'Ana tanbghik bzzaf ❤️💕';
            document.getElementById('response').style.opacity = '1';
            
            // Create hearts explosion
            createHeartsExplosion();
            
            // Hide buttons and teddy bounces more
            document.querySelector('.buttons').style.opacity = '0';
            document.querySelector('.buttons').style.transform = 'scale(0.8)';
            document.getElementById('teddyContainer').style.transform = 'scale(1.2)';
        }

        // La button hover handlers
        function handleLaHover(hovering) {
            const teddy = document.getElementById('teddyContainer');
            const laBtn = document.getElementById('laBtn');
            
            if (hovering) {
                teddy.style.transform = 'translateX(50px) rotate(10deg)';
                laBtn.style.transform = 'scale(1.2)';
            } else {
                teddy.style.transform = 'translateX(0) rotate(0deg)';
                laBtn.style.transform = 'scale(1)';
            }
        }

        // Hearts explosion effect
        function createHeartsExplosion() {
            const explosion = document.getElementById('heartsExplosion');
            for (let i = 0; i < 12; i++) {
                const heart = document.createElement('div');
                heart.className = 'heart-explosion';
                heart.innerHTML = ['💖', '💕', '💗', '💓', '✨'][Math.floor(Math.random() * 5)];
                heart.style.setProperty('--dx', (Math.random() - 0.5) * 200 + 'px');
                heart.style.setProperty('--dy', (Math.random() - 0.5) * 200 + 'px');
                heart.style.animationDelay = Math.random() * 0.3 + 's';
                explosion.appendChild(heart);

                setTimeout(() => heart.remove(), 1000);
            }
        }

        // Add Google Fonts
        const link = document.createElement('link');
        link.href = 'https://fonts.googleapis.com/css2?family=Poppins:wght@400;600;700&display=swap';
        link.rel = 'stylesheet';
        document.head.appendChild(link);
    </script>
</body>
</html>
