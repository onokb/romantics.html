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

        /* القلوب العائمة */
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

        /* البطاقة الرئيسية */
        .container {
            background: white;
            padding: 3rem;
            border-radius: 40px;
            box-shadow: 0 15px 40px rgba(251, 111, 146, 0.2);
            z-index: 10;
            max-width: 85%;
            width: 380px;
            position: relative;
        }

        .bear-container {
            font-size: 100px;
            margin-bottom: 20px;
            transition: transform 0.5s ease;
        }

        h1 {
            color: var(--dark-pink);
            font-size: 2.2rem;
            margin-bottom: 2rem;
        }

        .buttons {
            display: flex;
            justify-content: center;
            align-items: center;
            gap: 25px;
            height: 60px;
        }

        /* تصميم الأزرار */
        #yesBtn {
            background: linear-gradient(45deg, #ffafcc, #fb6f92);
            color: white; border: none;
            padding: 15px 40px; border-radius: 50px;
            font-size: 1.3rem; font-weight: bold;
            cursor: pointer;
            box-shadow: 0 5px 15px rgba(251, 111, 146, 0.4);
            transition: 0.3s;
        }

        #noBtn {
            background: transparent;
            color: var(--dark-pink);
            border: 2px solid var(--dark-pink);
            padding: 12px 35px; border-radius: 50px;
            font-size: 1.1rem; cursor: pointer;
            transition: 0.2s;
        }

        /* رسالة الحب */
        #message {
            display: none;
            color: var(--dark-pink);
            font-size: 1.8rem;
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
        <source src="https://files.catbox.moe/6f3v8r.mp3" type="audio/mpeg">
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

        // إنشاء القلوب
        function createHeart() {
            const heart = document.createElement('div');
            heart.classList.add('heart');
            heart.innerHTML = '❤️';
            heart.style.left = Math.random() * 100 + 'vw';
            heart.style.animationDuration = Math.random() * 2 + 3 + 's';
            heartBg.appendChild(heart);
            setTimeout(() => heart.remove(), 5000);
        }
        setInterval(createHeart, 400);

        // هروب زر "La"
        noBtn.addEventListener('mouseover', () => {
            const x = Math.random() * (window.innerWidth - noBtn.offsetWidth);
            const y = Math.random() * (window.innerHeight - noBtn.offsetHeight);
            noBtn.style.position = 'fixed';
            noBtn.style.left = x + 'px';
            noBtn.style.top = y + 'px';
        });

        // الضغط على "Ah"
        yesBtn.addEventListener('click', () => {
            // حذف السؤال والأزرار تماماً
            questionText.remove();
            btnGroup.remove();
            
            // إظهار الميساج وتغيير الأيقونة
            message.style.display = 'block';
            icon.innerHTML = '💍'; 
            icon.style.transform = 'scale(1.2)';
            
            // تشغيل أغنية Vechera
            music.play();

            // شلال كثيف من القلوب
            for(let i=0; i<50; i++) {
                setTimeout(createHeart, i * 50);
            }
        });
    </script>
</body>
</html>
