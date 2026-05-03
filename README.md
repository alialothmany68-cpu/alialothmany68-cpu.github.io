<html lang="ar" dir="rtl">
<head>
    <meta charset="UTF-8">
    <title>لعبة صيد الأهداف</title>
    <style>
        body {
            text-align: center;
            font-family: Arial, sans-serif;
            background-color: #f0f0f0;
            overflow: hidden;
        }
        #game-container {
            width: 100%;
            height: 80vh;
            position: relative;
            background-color: white;
            border: 2px solid #333;
            margin-top: 20px;
            cursor: crosshair;
        }
        #target {
            width: 50px;
            height: 50px;
            background-color: #ff4757;
            position: absolute;
            border-radius: 8px;
            display: none;
            cursor: pointer;
            transition: 0.1s;
        }
        .score-board {
            font-size: 24px;
            margin: 10px;
        }
    </style>
</head>
<body>

    <h1>لعبة التحدي السريع 🎮</h1>
    <div class="score-board">النقاط: <span id="score">0</span></div>
    <button onclick="startGame()">ابدأ اللعبة</button>

    <div id="game-container">
        <div id="target" onclick="hitTarget()"></div>
    </div>

    <script>
        let score = 0;
        const target = document.getElementById('target');
        const scoreDisplay = document.getElementById('score');
        const container = document.getElementById('game-container');

        function startGame() {
            score = 0;
            scoreDisplay.innerText = score;
            moveTarget();
        }

        function moveTarget() {
            // تحديد مكان عشوائي داخل الحاوية
            const maxX = container.clientWidth - 50;
            const maxY = container.clientHeight - 50;
            
            const randomX = Math.floor(Math.random() * maxX);
            const randomY = Math.floor(Math.random() * maxY);

            target.style.left = randomX + 'px';
            target.style.top = randomY + 'px';
            target.style.display = 'block';
        }

        function hitTarget() {
            score++;
            scoreDisplay.innerText = score;
            target.style.display = 'none';
            // تحريكه لمكان جديد بعد الضغط
            setTimeout(moveTarget, 200);
        }
    </script>
</body>
</html>

