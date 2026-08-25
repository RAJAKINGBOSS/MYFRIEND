<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Will You Be My Girlfriend? 💖</title>
    <style>
        * {
            margin: 0;
            padding: 0;
            box-sizing: border-box;
        }

        body {
            font-family: 'Segoe UI', Tahoma, Geneva, Verdana, sans-serif;
            background: linear-gradient(135deg, #ffe4e1 0%, #fff0f5 50%, #ffe4f0 100%);
            min-height: 100vh;
            display: flex;
            justify-content: center;
            align-items: center;
            overflow: hidden;
            position: relative;
        }

        /* Floating hearts background */
        .heart {
            position: absolute;
            font-size: 2rem;
            opacity: 0.5;
            animation: float 8s infinite ease-in-out;
            pointer-events: none;
        }

        @keyframes float {
            0%, 100% {
                transform: translateY(0px) translateX(0px) rotate(0deg);
                opacity: 0.3;
            }
            25% {
                transform: translateY(-40px) translateX(15px) rotate(15deg);
                opacity: 0.6;
            }
            50% {
                transform: translateY(-80px) translateX(-20px) rotate(-10deg);
                opacity: 0.5;
            }
            75% {
                transform: translateY(-40px) translateX(25px) rotate(20deg);
                opacity: 0.6;
            }
        }

        /* Main card */
        .card {
            background: white;
            border-radius: 40px;
            padding: 50px 40px;
            box-shadow: 0 20px 60px rgba(255, 105, 180, 0.25);
            text-align: center;
            max-width: 550px;
            width: 90%;
            z-index: 10;
            position: relative;
            animation: slideIn 0.8s cubic-bezier(0.34, 1.56, 0.64, 1);
            transition: all 0.6s ease;
        }

        @keyframes slideIn {
            from {
                opacity: 0;
                transform: translateY(-40px) scale(0.9);
            }
            to {
                opacity: 1;
                transform: translateY(0) scale(1);
            }
        }

        /* Cute character/GIF area */
        .cute-character {
            font-size: 6rem;
            margin-bottom: 25px;
            animation: bounce 2.5s ease-in-out infinite;
            display: inline-block;
        }

        @keyframes bounce {
            0%, 100% {
                transform: translateY(0) scale(1);
            }
            50% {
                transform: translateY(-20px) scale(1.05);
            }
        }

        h1 {
            font-size: 2.2rem;
            color: #ff1493;
            margin-bottom: 15px;
            font-weight: 800;
            letter-spacing: 0.5px;
            background: linear-gradient(135deg, #ff1493, #ff69b4);
            -webkit-background-clip: text;
            -webkit-text-fill-color: transparent;
            background-clip: text;
        }

        .subtitle {
            color: #ff69b4;
            font-size: 1.15rem;
            margin-bottom: 35px;
            font-style: italic;
            font-weight: 500;
        }

        /* Buttons container */
        .buttons {
            display: flex;
            gap: 20px;
            justify-content: center;
            margin-top: 35px;
            flex-wrap: wrap;
            align-items: center;
        }

        button {
            padding: 16px 45px;
            font-size: 1.15rem;
            border: none;
            border-radius: 30px;
            cursor: pointer;
            transition: all 0.3s ease;
            font-weight: 700;
            box-shadow: 0 4px 15px rgba(0, 0, 0, 0.1);
            position: relative;
        }

        #yesBtn {
            background: linear-gradient(135deg, #ff69b4 0%, #ff1493 100%);
            color: white;
            box-shadow: 0 6px 25px rgba(255, 105, 180, 0.4);
            min-width: 140px;
        }

        #yesBtn:hover:not(.success) {
            transform: scale(1.08);
            box-shadow: 0 10px 35px rgba(255, 105, 180, 0.6);
        }

        #yesBtn:active:not(.success) {
            transform: scale(0.96);
        }

        #noBtn {
            background: linear-gradient(135deg, #e0e0e0 0%, #d0d0d0 100%);
            color: #888;
            box-shadow: 0 4px 15px rgba(0, 0, 0, 0.08);
            transition: position 0.1s ease;
            z-index: 5;
        }

        #noBtn:hover {
            background: linear-gradient(135deg, #d0d0d0 0%, #c0c0c0 100%);
            box-shadow: 0 6px 20px rgba(0, 0, 0, 0.12);
        }

        /* Success state */
        .card.success {
            background: linear-gradient(135deg, rgba(255, 182, 193, 0.3), rgba(255, 192, 203, 0.3));
            backdrop-filter: blur(10px);
        }

        .original-content {
            transition: opacity 0.4s ease;
        }

        .original-content.hidden {
            opacity: 0;
            pointer-events: none;
            display: none;
        }

        .success-message {
            opacity: 0;
            animation: successPop 0.6s cubic-bezier(0.34, 1.56, 0.64, 1) forwards;
        }

        @keyframes successPop {
            0% {
                opacity: 0;
                transform: scale(0.3);
            }
            100% {
                opacity: 1;
                transform: scale(1);
            }
        }

        .success-character {
            font-size: 7rem;
            margin-bottom: 25px;
            animation: successSpin 0.8s cubic-bezier(0.34, 1.56, 0.64, 1);
        }

        @keyframes successSpin {
            0% {
                transform: scale(0) rotateY(180deg);
            }
            100% {
                transform: scale(1) rotateY(0deg);
            }
        }

        .success-text {
            font-size: 2rem;
            color: #ff1493;
            margin-bottom: 15px;
            font-weight: 800;
            background: linear-gradient(135deg, #ff1493, #ff69b4);
            -webkit-background-clip: text;
            -webkit-text-fill-color: transparent;
            background-clip: text;
        }

        .success-subtext {
            font-size: 1.3rem;
            color: #ff69b4;
            font-style: italic;
            font-weight: 600;
        }

        /* Confetti */
        .confetti {
            position: fixed;
            pointer-events: none;
            z-index: 9999;
            font-size: 2rem;
        }

        /* Sparkles */
        .sparkle {
            position: absolute;
            pointer-events: none;
            animation: sparkleAnimation 1.5s ease-out forwards;
        }

        @keyframes sparkleAnimation {
            0% {
                opacity: 1;
                transform: scale(1) translate(0, 0);
            }
            100% {
                opacity: 0;
                transform: scale(0) translate(var(--tx), var(--ty));
            }
        }

        /* Mobile responsive */
        @media (max-width: 600px) {
            body {
                padding: 20px;
            }

            .card {
                padding: 35px 25px;
                border-radius: 30px;
            }

            h1 {
                font-size: 1.8rem;
            }

            .cute-character {
                font-size: 5rem;
            }

            .success-character {
                font-size: 6rem;
            }

            .subtitle {
                font-size: 1rem;
                margin-bottom: 25px;
            }

            button {
                padding: 14px 35px;
                font-size: 1rem;
                min-width: 120px;
            }

            .buttons {
                gap: 15px;
            }

            .heart {
                font-size: 1.5rem;
            }
        }
    </style>
</head>
<body>
    <div class="card" id="card">
        <div class="original-content">
            <div class="cute-character" id="character">🐱💕</div>
            <h1 id="heading">Will you be my girlfriend? 💖</h1>
            <p class="subtitle" id="subtitle">This is a very important question... 🥰</p>
            
            <div class="buttons">
                <button id="yesBtn">Yes! 💕</button>
                <button id="noBtn">No</button>
            </div>
        </div>

        <div class="success-message" id="successMessage">
            <div class="success-character">🎉💕🎉</div>
            <div class="success-text">Yaaay! Best decision ever! 🥰💍</div>
            <div class="success-subtext">You just made me the happiest! 💗</div>
        </div>
    </div>

    <script>
        const yesBtn = document.getElementById('yesBtn');
        const noBtn = document.getElementById('noBtn');
        const card = document.getElementById('card');
        const successMessage = document.getElementById('successMessage');
        const originalContent = document.querySelector('.original-content');
        const buttons = document.querySelector('.buttons');

        let yesBtnSize = 1;
        let noButtonMoved = false;

        // Function to get random position for No button (constrained within viewport)
        function moveNoButton() {
            const margin = 20;
            const maxX = window.innerWidth - noBtn.offsetWidth - margin;
            const maxY = window.innerHeight - noBtn.offsetHeight - margin;
            
            const randomX = Math.max(margin, Math.random() * maxX);
            const randomY = Math.max(margin, Math.random() * maxY);
            
            // Only set fixed positioning on first move
            if (!noButtonMoved) {
                noBtn.style.position = 'fixed';
                noButtonMoved = true;
            }
            
            noBtn.style.left = randomX + 'px';
            noBtn.style.top = randomY + 'px';
        }

        // Function to increase Yes button size
        function increaseYesButton() {
            yesBtnSize += 0.12;
            yesBtn.style.transform = `scale(${Math.min(yesBtnSize, 3)})`;
            
            // Create sparkles around the button
            createSparkles(yesBtn);
        }

        // Function to create sparkles
        function createSparkles(element) {
            const rect = element.getBoundingClientRect();
            const centerX = rect.left + rect.width / 2;
            const centerY = rect.top + rect.height / 2;
            
            for (let i = 0; i < 8; i++) {
                const sparkle = document.createElement('div');
                sparkle.className = 'sparkle';
                sparkle.textContent = '✨';
                
                const angle = (i / 8) * Math.PI * 2;
                const distance = 60;
                const tx = Math.cos(angle) * distance;
                const ty = Math.sin(angle) * distance;
                
                sparkle.style.left = centerX + 'px';
                sparkle.style.top = centerY + 'px';
                sparkle.style.setProperty('--tx', tx + 'px');
                sparkle.style.setProperty('--ty', ty + 'px');
                
                document.body.appendChild(sparkle);
                
                setTimeout(() => sparkle.remove(), 1500);
            }
        }

        // No button hover (desktop)
        noBtn.addEventListener('mouseenter', () => {
            moveNoButton();
            increaseYesButton();
        });

        // No button click
        noBtn.addEventListener('click', (e) => {
            e.preventDefault();
            moveNoButton();
            increaseYesButton();
        });

        // No button touch for mobile
        noBtn.addEventListener('touchstart', (e) => {
            e.preventDefault();
            moveNoButton();
            increaseYesButton();
        });

        // Create confetti
        function createConfetti() {
            const confettiPieces = 60;
            const symbols = ['🎉', '💖', '✨', '💕', '🎊', '💗', '🌹', '💝'];
            
            for (let i = 0; i < confettiPieces; i++) {
                const confetti = document.createElement('div');
                confetti.className = 'confetti';
                confetti.textContent = symbols[Math.floor(Math.random() * symbols.length)];
                confetti.style.left = Math.random() * window.innerWidth + 'px';
                confetti.style.top = '-30px';
                confetti.style.opacity = '1';
                confetti.style.fontSize = (Math.random() * 35 + 25) + 'px';
                
                document.body.appendChild(confetti);
                
                // Animate confetti falling with physics
                let yPos = -30;
                let xPos = parseFloat(confetti.style.left);
                const speed = Math.random() * 4 + 2;
                const drift = (Math.random() - 0.5) * 6;
                const rotation = Math.random() * 360;
                let rotationSpeed = Math.random() * 10 - 5;
                
                const animateConfetti = () => {
                    yPos += speed;
                    xPos += drift;
                    rotation += rotationSpeed;
                    
                    confetti.style.transform = `rotate(${rotation}deg)`;
                    confetti.style.left = xPos + 'px';
                    confetti.style.top = yPos + 'px';
                    
                    // Fade out near the bottom
                    if (yPos > window.innerHeight - 100) {
                        const fadeStart = window.innerHeight - 100;
                        const alpha = 1 - (yPos - fadeStart) / 100;
                        confetti.style.opacity = Math.max(0, alpha);
                    }
                    
                    if (yPos < window.innerHeight) {
                        requestAnimationFrame(animateConfetti);
                    } else {
                        confetti.remove();
                    }
                };
                
                animateConfetti();
            }
        }

        // Yes button click
        yesBtn.addEventListener('click', () => {
            yesBtn.classList.add('success');
            
            // Hide original content
            originalContent.classList.add('hidden');
            
            // Show success message
            card.classList.add('success');
            successMessage.style.display = 'block';
            
            // Create multiple confetti bursts
            createConfetti();
            setTimeout(() => createConfetti(), 200);
            setTimeout(() => createConfetti(), 400);
            setTimeout(() => createConfetti(), 600);
        });

        // Create floating hearts in background
        function createFloatingHearts() {
            const heartCount = 20;
            const hearts = ['💗', '💖', '💕', '💓', '❤️', '🌹', '💝'];
            
            for (let i = 0; i < heartCount; i++) {
                const heart = document.createElement('div');
                heart.className = 'heart';
                heart.textContent = hearts[Math.floor(Math.random() * hearts.length)];
                heart.style.left = Math.random() * 100 + '%';
                heart.style.top = Math.random() * 100 + '%';
                heart.style.animationDelay = Math.random() * 8 + 's';
                heart.style.fontSize = (Math.random() * 35 + 15) + 'px';
                heart.style.opacity = Math.random() * 0.4 + 0.2;
                document.body.appendChild(heart);
            }
        }

        // Initialize
        createFloatingHearts();
    </script>
</body>
</html>
