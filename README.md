<!DOCTYPE html>
<html lang="ar">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Valentine Letter</title>
    <style>
        /* تنسيق الخلفية العامة */
        body {
            background-color: #fce4ec; /* لون وردي فاتح جداً */
            display: flex;
            justify-content: center;
            align-items: center;
            height: 100vh;
            margin: 0;
            font-family: 'Courier New', Courier, monospace; /* خط يشبه لغة البرمجة أو البيكسل */
        }

        /* نافذة الرسالة */
        .card {
            background-color: #ffcdd2; /* وردي أغمق قليلاً */
            border: 4px solid #f06292;
            border-radius: 10px;
            padding: 20px;
            text-align: center;
            box-shadow: 10px 10px 0px #f06292;
            width: 350px;
            position: relative;
        }

        /* القلوب الصغيرة في الخلفية (اختياري) */
        .card::before {
            content: "❤❤❤";
            display: block;
            color: #f06292;
            margin-bottom: 10px;
            font-size: 20px;
        }

        h1 {
            color: #d81b60;
            font-size: 24px;
        }

        /* صورة القطة أو الإيموجي */
        .gif-container img {
            width: 150px;
            margin: 20px 0;
        }

        /* تنسيق الأزرار */
        .btn-group {
            display: flex;
            justify-content: center;
            gap: 20px;
            margin-top: 20px;
            position: relative;
        }

        button {
            padding: 10px 25px;
            font-size: 18px;
            border: 2px solid #d81b60;
            border-radius: 5px;
            cursor: pointer;
            transition: 0.3s;
            font-family: inherit;
        }

        #yesBtn {
            background-color: #f06292;
            color: white;
        }

        #yesBtn:hover {
            background-color: #d81b60;
            transform: scale(1.1);
        }

        #noBtn {
            background-color: white;
            color: #d81b60;
            position: absolute; /* ضروري لجعله يتحرك */
            left: 190px;
        }
    </style>
</head>
<body>

    <div class="card">
        <h1>Will you be my Valentine?</h1>
        
        <div class="gif-container">
            <img src="https://media.giphy.com/media/v1.Y2lkPTc5MGI3NjExNHJndnZueXp3Y3V6amZ3bmZ3bmZ3bmZ3bmZ3bmZ3bmZ3bmZ3JmVwPXYxX2ludGVybmFsX2dpZl9ieV9pZCZjdD1z/KBy0Y7YvW8Y3R1sY9j/giphy.gif" alt="Cute Cat">
        </div>

        <div class="btn-group">
            <button id="yesBtn" onclick="celebrate()">YES</button>
            <button id="noBtn" onmouseover="moveButton()">NO</button>
        </div>
    </div>

    <script>
        function moveButton() {
            const noBtn = document.getElementById('noBtn');
            
            // حساب أماكن عشوائية لزر "لا" حتى لا يستطيع أحد الضغط عليه
            const x = Math.random() * (window.innerWidth - noBtn.offsetWidth);
            const y = Math.random() * (window.innerHeight - noBtn.offsetHeight);
            
            noBtn.style.position = 'fixed';
            noBtn.style.left = x + 'px';
            noBtn.style.top = y + 'px';
        }

        function celebrate() {
            alert("I knew it! ❤️ Happy Valentine's Day!");
            // يمكنك توجيه المستخدم لصفحة أخرى أو تغيير المحتوى هنا
            document.querySelector('.card').innerHTML = "<h1>Yaaaay! ❤️🥰</h1><img src='https://media.giphy.com/media/v1.Y2lkPTc5MGI3NjExMm56bmZ3bmZ3bmZ3bmZ3bmZ3bmZ3bmZ3bmZ3bmZ3JmVwPXYxX2ludGVybmFsX2dpZl9ieV9pZCZjdD1z/MDJ9NmI8VliL3S8fW4/giphy.gif' width='200'>";
        }
    </script>

</body>
</html>
