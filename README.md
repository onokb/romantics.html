<!DOCTYPE html>
<html lang="ar">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Wach Katbghini? ❤️</title>
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
            top: 0; left: 0; width: 100%; height: 100%;
            pointer-events: none; z-index: 0;
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
            padding: 2.5rem;
            border-radius: 35px;
            box-shadow: 0 15px 35px rgba(251, 111, 146, 0.2);
            z-index: 10;
            max-width: 85%;
            width: 380px;
            transition: all 0.6s cubic-bezier(0.175, 0.885, 0.32, 1.275);
        }

        .bear-container {
            font-size: 90px;
            margin-bottom: 15px;
            display: block;
        }

        h1 {
            color: var(--dark-pink);
            font-size: 1.8rem;
            margin-bottom: 2rem;
            transition: opacity 0.3s;
        }

        .buttons {
            display: flex;
            justify-content: center;
            align-items: center;
            gap: 20px;
            height: 60px;
            position: relative;
        }

        /* Buttons */
        #yesBtn {
            background: linear-gradient(45deg, #ffafcc, #fb6f92);
            color: white; border: none;
            padding: 12px 35px; border-radius: 50px;
            font-size: 1.2rem; font-weight: bold;
            cursor: pointer;
            box-shadow: 0 4px 15px rgba(251, 111, 146, 0.4);
            transition: transform 0.2s;
        }

        #noBtn {
            background: transparent;
            color: var(--dark-pink);
            border: 2px solid var(--dark-pink);
            padding: 10px 30px; border-radius: 50px;
            font-size: 1.1rem; cursor: pointer;
            transition: all 0.2s ease;
        }

        /* Result View */
        #message {
            display: none;
            color: var(--dark-pink);
            font-size: 1.6rem;
            font-weight: bold;
            animation: popIn 0.8s cubic-bezier(0.175, 0.885, 0.32, 1.275);
        }

        @keyframes popIn {
            0% { transform: scale(0.5); opacity: 0; }
            100% { transform: scale(1); opacity: 1; }
        }
    </style>
</head>
<body>

    <audio id="bgMusic" loop>
        <source src="https://www.chosic.com/wp-content/uploads/2021/07/Rainy-Day-Background-Music.mp3" type="audio/mpeg">
    </audio>

    <div class="heart-bg" id="heartBg"></div>

    <div class="container" id="mainContainer">
        <div class="bear-container" id="icon">🧸</div>
        <h1 id="questionText">Wach katbghini?</h1>
        
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
        const questionText = document.getElementById('questionText');
        const btnGroup = document.getElementById('btnGroup');
        const heartBg = document.getElementById('heartBg');
        const music = document.getElementById('bgMusic');
        const icon = document.getElementById('icon');

        // إنشاء قلوب عشوائية
        function createHeart() {
            const heart = document.createElement('div');
            heart.classList.add('heart');
            heart.innerHTML = '❤️';
            heart.style.left = Math.random() * 100 + 'vw';
            heart.style.animationDuration = Math.random() * 3 + 3 + 's';
            heartBg.appendChild(heart);
            setTimeout(() => heart.remove(), 6000);
        }
        setInterval(createHeart, 500);

        // هروب زر "لا"
        noBtn.addEventListener('mouseover', () => {
            const x = Math.random() * (window.innerWidth - noBtn.offsetWidth);
            const y = Math.random() * (window.innerHeight - noBtn.offsetHeight);
            noBtn.style.position = 'fixed';
            noBtn.style.left = x + 'px';
            noBtn.style.top = y + 'px';
        });

        // الضغط على "نعم"
        yesBtn.addEventListener('click', () => {
            // محو السؤال والبطونات
            questionText.style.display = 'none';
            btnGroup.style.display = 'none';
            
            // إظهار الميساج وتغيير الأيقونة
            message.style.display = 'block';
            icon.innerHTML = '💖';
            
            // تشغيل الموسيقى (كتحتاج تفاعل من المستخدم باش تخدم)
            music.play();

            // شلال ديال القلوب
            for(let i=0; i<40; i++) {
                setTimeout(createHeart, i * 60);
            }
        });
    </script>
</body>
</html>
