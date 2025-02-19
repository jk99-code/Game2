<!DOCTYPE html>
<html>
<head>
    <title>Pong Game</title>
    <style>
        canvas {
            background: black;
            display: block;
            margin: auto;
        }
    </style>
</head>
<body>
    <canvas id="gameCanvas" width="800" height="400"></canvas>
    <script>
        const canvas = document.getElementById("gameCanvas");
        const ctx = canvas.getContext("2d");

        const paddleWidth = 10, paddleHeight = 60;
        let player1Y = canvas.height / 2 - paddleHeight / 2;
        let player2Y = canvas.height / 2 - paddleHeight / 2;
        let player1Speed = 0, player2Speed = 0;
        const ballSize = 10;
        let ballX = canvas.width / 2, ballY = canvas.height / 2;
        let ballSpeedX = 4, ballSpeedY = 4;

        function drawRect(x, y, width, height, color) {
            ctx.fillStyle = color;
            ctx.fillRect(x, y, width, height);
        }

        function drawCircle(x, y, radius, color) {
            ctx.fillStyle = color;
            ctx.beginPath();
            ctx.arc(x, y, radius, 0, Math.PI * 2, false);
            ctx.fill();
        }

        function update() {
            player1Y += player1Speed;
            player2Y += player2Speed;
            player1Y = Math.max(0, Math.min(canvas.height - paddleHeight, player1Y));
            player2Y = Math.max(0, Math.min(canvas.height - paddleHeight, player2Y));
            
            ballX += ballSpeedX;
            ballY += ballSpeedY;

            if (ballY <= 0 || ballY >= canvas.height - ballSize) ballSpeedY *= -1;
            
            if (
                (ballX <= 20 && ballY >= player1Y && ballY <= player1Y + paddleHeight) ||
                (ballX >= canvas.width - 20 - ballSize && ballY >= player2Y && ballY <= player2Y + paddleHeight)
            ) {
                ballSpeedX *= -1;
            }

            if (ballX < 0 || ballX > canvas.width) {
                ballX = canvas.width / 2;
                ballY = canvas.height / 2;
                ballSpeedX = 4;
                ballSpeedY = 4;
            }
        }

        function draw() {
            drawRect(0, 0, canvas.width, canvas.height, "black");
            drawRect(10, player1Y, paddleWidth, paddleHeight, "white");
            drawRect(canvas.width - 20, player2Y, paddleWidth, paddleHeight, "white");
            drawCircle(ballX, ballY, ballSize, "white");
        }

        function gameLoop() {
            update();
            draw();
            requestAnimationFrame(gameLoop);
        }

        window.addEventListener("keydown", (event) => {
            if (event.key === "w") player1Speed = -6;
            if (event.key === "s") player1Speed = 6;
            if (event.key === "ArrowUp") player2Speed = -6;
            if (event.key === "ArrowDown") player2Speed = 6;
        });

        window.addEventListener("keyup", (event) => {
            if (event.key === "w" || event.key === "s") player1Speed = 0;
            if (event.key === "ArrowUp" || event.key === "ArrowDown") player2Speed = 0;
        });

        gameLoop();
    </script>
</body>
</html>
