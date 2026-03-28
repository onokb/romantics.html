<!DOCTYPE html>
<html lang="ar" dir="rtl">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Wach Katbghini? ❤️</title>
    <style>
        :root {
            --primary-pink: #ffb6c1; /* Soft pink */
            --dark-pink: #ff8fa3;
            --heart-color: #ff6b81;
            --text-color: #555;
            --bg-color: #fff0f5; /* Lavender blush for contrast */
        }

        * {
            box-sizing: border-box;
            margin: 0;
            padding: 0;
            font-family: 'Segoe UI', Tahoma, Geneva, Verdana, sans-serif;
        }

        body {
            background-color: var(--bg-color);
            overflow: hidden; /* Prevent scrollbars due to floating hearts */
            display: flex;
            justify-content: center;
            align-items: center;
            min-height: 100vh;
            color: var(--text-color);
        }

        /* Floating Hearts Container */
        #heart-container {
            position: fixed;
            top: 0;
            left: 0;
            width: 100%;
            height: 100%;
            pointer-events: none; /* Let clicks pass through */
            z-index: 1;
        }

        .heart {
            position: absolute;
            background-color: var(--heart-color);
            display: inline-block;
            width: 20px;
            height: 20px;
            opacity: 0.8;
            transform: rotate(-45deg);
            animation: float 10s infinite linear;
        }

        .heart::before,
        .heart::after {
            content: "";
            position: absolute;
            width: 20px;
            height: 20px;
            background-color: var(--heart-color);
            border-radius: 50%;
        }

        .heart::before {
            top: -10px;
            left: 0;
        }

        .heart::after {
            top: 0;
            left: 10px;
        }

        @keyframes float {
            0% {
                transform: translateY(100vh) rotate(-45deg) scale(0);
                opacity: 0;
            }
            10% {
                opacity: 0.8;
                transform: translateY(90vh) rotate(-45deg) scale(1);
            }
            100% {
                transform: translateY(-20vh) rotate(-45deg) scale(1);
                opacity: 0;
            }
        }

        /* Main Content Container */
        .main-container {
            position: relative;
            z-index: 10;
            background-color: rgba(255, 255, 255, 0.9);
            padding: 40px;
            border-radius: 30px;
            box-shadow: 0 10px 30px rgba(0, 0, 0, 0.05);
            text-align: center;
            width: 90%;
            max-width: 500px;
            transition: all 0.5s ease;
        }

        /* Teddy Bear Container */
        .teddy-box {
            margin-bottom: 25px;
        }

        .teddy-bear {
            width: 150px;
            height: 150px;
            transition: transform 0.3s ease;
        }

        .main-container:hover .teddy-bear {
            transform: scale(1.05);
        }

        /* Text Style */
        .question {
            font-size: 2.5rem;
            color: var(--dark-pink);
            margin-bottom: 30px;
            font-weight: bold;
        }

        .response-text {
            display: none; /* Hidden by default */
            font-size: 2rem;
            color: #d81b60; /* Darker pink for the surprise */
            margin-top: 20px;
            opacity: 0;
            transition: opacity 0.5s ease;
        }

        .response-text.show {
            display: block;
            opacity: 1;
        }

        /* Buttons Container */
        .button-box {
            display: flex;
            justify-content: space-around;
            gap: 20px;
            margin-top: 20px;
            position: relative; /* For "La" movement */
            height: 60px; /* Base height for button space */
        }

        /* Common Button Styles */
        .btn {
            padding: 12px 35px;
            font-size: 1.2rem;
            cursor: pointer;
            border: none;
            border-radius: 50px;
            transition: all 0.3s ease;
            box-shadow: 0 4px 10px rgba(0, 0, 0, 0.05);
            width: 120px; /* Fixed width for consistency */
        }

        .btn:focus {
            outline: none;
        }

        /* "Ah" Button Style */
        #btn-ah {
            background: linear-gradient(45deg, #ff9a9e 0%, var(--primary-pink) 100%);
            color: white;
        }

        #btn-ah:hover {
            background: linear-gradient(45deg, #f783ac 0%, #ff9a9e 100%);
            transform: translateY(-3px);
            box-shadow: 0 6px 15px rgba(255, 107, 129, 0.3);
        }

        /* "La" Button Style */
        #btn-la {
            background: transparent;
            color: var(--dark-pink);
            border: 2px solid var(--dark-pink);
            position: relative; /* For movement */
            transition: transform 0.2s ease;
        }

        /* Responsive Design */
        @media (max-width: 600px) {
            .main-container {
                padding: 30px 20px;
            }

            .teddy-bear {
                width: 120px;
                height: 120px;
            }

            .question {
                font-size: 1.8rem;
            }

            .response-text {
                font-size: 1.5rem;
            }

            .button-box {
                flex-direction: column;
                gap: 15px;
                height: 140px; /* Higher container to accommodate column layout */
            }

            .btn {
                width: 100%;
                max-width: 180px;
                margin: 0 auto;
            }
        }
    </style>
</head>
<body>

    <div id="heart-container"></div>

    <div class="main-container" id="interaction-card">
        <div class="teddy-box">
            <svg class="teddy-bear" viewBox="0 0 100 100" xmlns="http://www.w3.org/2000/svg">
                <ellipse cx="50" cy="65" rx="30" ry="25" fill="#a16c5a" />
                <ellipse cx="50" cy="65" rx="20" ry="18" fill="#eacba0" /> <circle cx="50" cy="35" r="22" fill="#b9806a" />
                
                <circle cx="28" cy="22" r="8" fill="#a16c5a" />
                <circle cx="28" cy="22" r="5" fill="#eacba0" />
                <circle cx="72" cy="22" r="8" fill="#a16c5a" />
                <circle cx="72" cy="22" r="5" fill="#eacba0" />
                
                <circle cx="43" cy="32" r="2.5" fill="#333" />
                <circle cx="57" cy="32" r="2.5" fill="#333" />
                
                <ellipse cx="50" cy="40" rx="8" ry="6" fill="#eacba0" />
                <polygon points="48,39 52,39 50,42" fill="#333" />
                
                <path d="M50 63 C48 60, 45 61, 45 64 C45 68, 50 71, 50 71 C50 71, 55 68, 55 64 C55 61, 52 60, 50 63 Z" fill="#ff6b81"/>
            </svg>
        </div>

        <h1 class="question" id="question-text">wach katbghini?</h1>
        
        <p class="response-text" id="response-text">Ana tanbghik bzzaf❤️</p>

        <div class="button-box" id="button-container">
            <button class="btn" id="btn-ah">ah</button>
            <button class="btn" id="btn-la">La</button>
        </div>
    </div>

    <script>
        // 1. Floating Hearts Logic
        const heartContainer = document.getElementById('heart-container');
        function createHeart() {
            const heart = document.createElement('div');
            heart.classList.add('heart');
            
            // Randomize position and size
            heart.style.left = Math.random() * 100 + 'vw';
            const size = Math.random() * 15 + 10;
            heart.style.width = size + 'px';
            heart.style.height = size + 'px';
            
            // Randomize animation duration
            const duration = Math.random() * 5 + 7; // 7s to 12s
            heart.style.animationDuration = duration + 's';
            
            heartContainer.appendChild(heart);

            // Clean up old hearts
            setTimeout(() => {
                heart.remove();
            }, duration * 1000);
        }

        // Create initial hearts
        for (let i = 0; i < 15; i++) {
            createHeart();
        }
        
        // Keep creating hearts
        setInterval(createHeart, 800);

        // 2. Interaction Logic
        const btnAh = document.getElementById('btn-ah');
        const btnLa = document.getElementById('btn-la');
        const questionText = document.getElementById('question-text');
        const responseText = document.getElementById('response-text');
        const buttonContainer = document.getElementById('button-container');

        // Ah Interaction
        btnAh.addEventListener('click', () => {
            // Hide the question and buttons
            questionText.style.display = 'none';
            buttonContainer.style.display = 'none';
            
            // Show the loving response with animation
            responseText.classList.add('show');
            
            // Increase heart frequency for a short time
            const intenseHeartInterval = setInterval(createHeart, 200);
            setTimeout(() => {
                clearInterval(intenseHeartInterval);
            }, 3000);
        });

        // La Interaction (Moves away on hover)
        // This requires careful responsive handling
        btnLa.addEventListener('mouseover', moveButton);
        btnLa.addEventListener('touchstart', moveButton); // For mobile tap-and-hover

        function moveButton(e) {
            // Get dimensions of the card and button
            const card = document.getElementById('interaction-card');
            const cardRect = card.getBoundingClientRect();
            const btnRect = btnLa.getBoundingClientRect();
            
            // Available space within the card padding
            const padding = 20;
            const availableWidth = cardRect.width - btnRect.width - (padding * 2);
            const availableHeight = cardRect.height - btnRect.height - (padding * 2);

            // Generate new random positions relative to the card's top-left corner
            const newLeft = Math.random() * availableWidth + padding;
            const newTop = Math.random() * availableHeight + padding;

            // In mobile column layout, we primarily move it horizontally to avoid breaking the layout, 
            // but we add a slight vertical variance for fun.
            const isMobile = window.innerWidth <= 600;
            
            if (isMobile) {
                // For mobile: focus more on horizontal movement, slight vertical offset
                btnLa.style.position = 'absolute';
                btnLa.style.left = newLeft + 'px';
                // Slight offset from its original vertical spot
                btnLa.style.top = (Math.random() * 40 - 20) + 'px';
            } else {
                // For desktop: full movement within button container area
                btnLa.style.position = 'absolute';
                // Adjust position relative to the container itself
                const containerRect = buttonContainer.getBoundingClientRect();
                const relativeX = e.clientX - containerRect.left;
                
                // Move in the opposite direction of the mouse slightly to feel more reactive
                let offsetX = (relativeX < containerRect.width/2) ? 100 : -100;
                let finalLeft = newLeft;

                // Simple 'move away' without complex math for reliability
                if(btnLa.style.left === '20px') {
                   finalLeft = availableWidth + padding;
                } else {
                   finalLeft = padding;
                }
                
                btnLa.style.left = finalLeft + 'px';
                btnLa.style.top = (availableHeight/2) + 'px'; // Keep vertically centered in the container area
            }
        }
        
        // Also prevent click on "La" (it should be impossible anyway)
        btnLa.addEventListener('click', (e) => {
            e.preventDefault();
        });

    </script>
</body>
</html>
