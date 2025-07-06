<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0, maximum-scale=1.0, user-scalable=no">
    <title>NISHIKA Birthday Hacked! - From K0CH1M4N4</title>
    <style>
        body {
            background-color: #000;
            color: #0F0;
            font-family: 'Courier New', monospace;
            margin: 0;
            padding: 10px;
            overflow: hidden;
            height: 100vh;
        }
        
        #fireworks-canvas {
            position: fixed; /* Position fixed to cover the entire viewport */
            top: 0;
            left: 0;
            width: 100%;
            height: 100%;
            z-index: 0; /* Ensure it's behind the terminal */
        }

        #terminal {
            background-color: rgba(0, 0, 0, 0.7);
            border-radius: 5px;
            padding: 15px;
            height: calc(100vh - 40px);
            overflow-y: auto;
            position: relative;
            z-index: 1; /* Ensure terminal is above fireworks */
        }
        
        .command {
            margin-bottom: 10px;
        }
        
        .prompt {
            color: #0F0;
            display: inline-block;
            margin-right: 10px;
        }
        
        .input-line {
            display: flex;
            align-items: center;
            margin-bottom: 10px;
        }
        
        #cursor {
            display: inline-block;
            width: 10px;
            height: 20px;
            background-color: #0F0;
            animation: blink 1s infinite;
            margin-left: 5px;
            vertical-align: middle;
        }
        
        @keyframes blink {
            0% { opacity: 1; }
            50% { opacity: 0; }
            100% { opacity: 1; }
        }
        
        .typing {
            border-right: 2px solid #0F0;
            white-space: nowrap;
            overflow: hidden;
            animation: typing 3s steps(40) forwards, blink-caret 0.75s step-end infinite;
        }
        
        @keyframes typing {
            from { width: 0 }
            to { width: 100% }
        }
        
        @keyframes blink-caret {
            from, to { border-color: transparent }
            50% { border-color: #0F0 }
        }
        
        .success {
            color: #0F0;
        }
        
        .error {
            color: #F00;
        }
        
        .warning {
            color: #FF0;
        }
        
        .critical {
            color: #F0F;
            font-weight: bold;
        }
        
        #birthday-message {
            display: none;
            font-size: 1.5em;
            text-align: center;
            margin-top: 20px;
            animation: rainbow 5s infinite;
        }
        
        @keyframes rainbow {
            0% { color: #FF0000; }
            16% { color: #FF8000; }
            32% { color: #FFFF00; }
            48% { color: #00FF00; }
            64% { color: #0000FF; }
            80% { color: #8000FF; }
            100% { color: #FF0080; }
        }
        
        .progress-bar {
            width: 100%;
            background-color: #222;
            padding: 3px;
            border-radius: 3px;
            margin-top: 10px;
            overflow: hidden;
        }
        
        .progress {
            height: 20px;
            background-color: #0F0;
            width: 0%;
            transition: width 0.5s;
        }
    </style>
</head>
<body>
    <canvas id="fireworks-canvas"></canvas>

    <!-- Added Audio Element -->
    <audio id="birthday-song" src="happy_birthday.mp3" preload="auto"></audio> 

    <div id="terminal">
        <div class="command">Initializing hacking sequence...</div>
        <div class="command">Establishing secure connection to birthday_db...</div>
        <div class="command">Today is 2nd October!</div>
        <div class="command success">Connected! Gathering birthday info...</div>
        <div class="command">Decrypting target's name: N I S H I K A</div>
        <div class="progress-bar"><div class="progress" style="width: 25%"></div></div>
        <div id="commands-container"></div>
        <div id="birthday-message"></div>
        <div class="input-line">
            <span class="prompt">K0CH1M4N4@NISHIKA_BDAY:~#</span>
            <span id="typed-cmd"></span>
            <span id="cursor"></span>
        </div>
    </div>

    <script>
        // --- Fireworks Script Start ---
        const canvas = document.getElementById('fireworks-canvas');
        const ctx = canvas.getContext('2d');
        let particles = [];
        let fireworks = [];
        const colors = ['#FF0000', '#00FF00', '#0000FF', '#FFFF00', '#FF00FF', '#00FFFF', '#FFFFFF'];

        // Resize canvas to fill window
        function resizeCanvas() {
            canvas.width = window.innerWidth;
            canvas.height = window.innerHeight;
        }
        window.addEventListener('resize', resizeCanvas);
        resizeCanvas(); // Initial resize

        class Particle {
            constructor(x, y, color, velocity) {
                this.x = x;
                this.y = y;
                this.color = color;
                this.velocity = velocity;
                this.alpha = 1;
                this.friction = 0.99;
                this.gravity = 0.05;
            }

            draw() {
                ctx.save();
                ctx.globalAlpha = this.alpha;
                ctx.beginPath();
                ctx.arc(this.x, this.y, 2, 0, Math.PI * 2);
                ctx.fillStyle = this.color;
                ctx.fill();
                ctx.restore();
            }

            update() {
                this.velocity.x *= this.friction;
                this.velocity.y *= this.friction;
                this.velocity.y += this.gravity;
                this.x += this.velocity.x;
                this.y += this.velocity.y;
                this.alpha -= 0.008; // Fade out
            }
        }

        class Firework {
            constructor(x, y, targetX, targetY, color) {
                this.x = x;
                this.y = y;
                this.targetX = targetX;
                this.targetY = targetY;
                this.color = color;
                this.velocity = {
                    x: (targetX - x) / 60, // Adjust speed
                    y: (targetY - y) / 60
                };
                this.alpha = 1;
                this.exploded = false;
            }

            draw() {
                ctx.save();
                ctx.globalAlpha = this.alpha;
                ctx.beginPath();
                ctx.arc(this.x, this.y, 3, 0, Math.PI * 2);
                ctx.fillStyle = this.color;
                ctx.fill();
                ctx.restore();
            }

            update() {
                if (!this.exploded) {
                    this.x += this.velocity.x;
                    this.y += this.velocity.y;

                    // Check if reached target
                    if (Math.abs(this.x - this.targetX) < Math.abs(this.velocity.x) &&
                        Math.abs(this.y - this.targetY) < Math.abs(this.velocity.y)) {
                        this.explode();
                        this.exploded = true;
                    }
                }
            }

            explode() {
                const particleCount = 100; // Number of particles in explosion
                for (let i = 0; i < particleCount; i++) {
                    const angle = Math.random() * Math.PI * 2;
                    const speed = Math.random() * 5 + 1; // Random speed for particles
                    const velocity = {
                        x: Math.cos(angle) * speed,
                        y: Math.sin(angle) * speed
                    };
                    particles.push(new Particle(this.x, this.y, this.color, velocity));
                }
            }
        }

        function animateFireworks() {
            requestAnimationFrame(animateFireworks);
            ctx.fillStyle = 'rgba(0, 0, 0, 0.05)'; // Trail effect
            ctx.fillRect(0, 0, canvas.width, canvas.height);

            // Update and draw particles
            for (let i = particles.length - 1; i >= 0; i--) {
                const particle = particles[i];
                particle.update();
                particle.draw();
                if (particle.alpha <= 0.05) {
                    particles.splice(i, 1);
                }
            }

            // Update and draw fireworks (rockets)
            for (let i = fireworks.length - 1; i >= 0; i--) {
                const firework = fireworks[i];
                firework.update();
                firework.draw();
                if (firework.exploded) {
                    fireworks.splice(i, 1);
                }
            }

            // Launch new fireworks periodically
            if (Math.random() < 0.03) { // Adjust frequency
                const startX = canvas.width / 2;
                const startY = canvas.height;
                const targetX = Math.random() * canvas.width;
                const targetY = Math.random() * (canvas.height / 2); // Explode in upper half
                const color = colors[Math.floor(Math.random() * colors.length)];
                fireworks.push(new Firework(startX, startY, targetX, targetY, color));
            }
        }

        animateFireworks();
        // --- Fireworks Script End ---


        const commands = [
            {text: "Bypassing firewall...", delay: 1000, class: ""},
            {text: "Accessing NISHIKA_birthday_db...", delay: 800, class: ""},
            {text: "Locating target record...", delay: 1200, class: "warning"},
            {text: "Target identified...", delay: 1500, class: "success"},
            {text: "ERROR: Security protocols detected!", delay: 2000, class: "error"},
            {text: "Injecting bypass code...", delay: 1000, class: ""},
            {text: "Brute forcing birthday wishes...", delay: 2500, class: ""},
            {text: "Decryption in progress...", delay: 3000, class: ""},
            {text: "CRITICAL: Birthday protocol detected!", delay: 1000, class: "critical"},
            
            {
                text: "SUCCESS: Birthday wish extracted!", 
                delay: 2000, 
                class: "success",
                callback: function() {
                    updateProgress(100);
                    setTimeout(showBirthdayMessage, 1500);
                }
            }
        ];
        
        const birthdayMessages = [
            "Happy Birthday to my amazing girlfriend NISHIKA!",
            "Your system has been hacked by K0CH1M4N4 with love and birthday wishes!",
            "May your year be filled with joy and love, just like you bring to my life!",
            "Access granted to infinite happiness, my love!",
            "Kernel Panic - Happy Birthday to the one who makes my heart race!"
        ];
        
        const container = document.getElementById('commands-container');
        const typedCmd = document.getElementById('typed-cmd');
        const progressBar = document.querySelector('.progress');
        const birthdayMessage = document.getElementById('birthday-message');
        
        let i = 0;
        let progress = 25;
        
        function updateProgress(newProgress) {
            progress = newProgress;
            progressBar.style.width = `${newProgress}%`; // Corrected to use newProgress
        }
        
        // Get the audio element
        const birthdaySong = document.getElementById('birthday-song');

        function showBirthdayMessage() {
            container.style.display = 'none';
            const randomMessage = birthdayMessages[Math.floor(Math.random() * birthdayMessages.length)];
            birthdayMessage.textContent = randomMessage;
            birthdayMessage.style.display = 'block';
            
            // Play the birthday song
            birthdaySong.play().catch(error => {
                console.error("Error playing audio:", error);
                // This catch block handles potential "NotAllowedError" if autoplay is blocked
                // You might want to add a user interaction prompt here if it's crucial.
            });

            // Add confetti effect
            setTimeout(() => {
                birthdayMessage.classList.add('typing');
                addConfetti();
            }, 500);
        }
        
        function addConfetti() {
            const confettiCount = 100;
            const confettiColors = ['#f00', '#0f0', '#00f', '#ff0', '#f0f'];
            
            for (let i = 0; i < confettiCount; i++) {
                const confetti = document.createElement('div');
                confetti.style.position = 'absolute';
                confetti.style.left = Math.random() * 100 + 'vw';
                confetti.style.top = '-10px';
                confetti.style.width = Math.random() * 10 + 5 + 'px';
                confetti.style.height = Math.random() * 10 + 5 + 'px';
                confetti.style.backgroundColor = confettiColors[Math.floor(Math.random() * confettiColors.length)];
                confetti.style.zIndex = '1000';
                
                const animationDuration = Math.random() * 3 + 2;
                confetti.style.animation = `fall ${animationDuration}s linear forwards`;
                
                document.body.appendChild(confetti);
                
                // Remove after animation
                setTimeout(() => {
                    confetti.remove();
                }, animationDuration * 1000);
            }
            
            // Add confetti animation
            const style = document.createElement('style');
            style.innerHTML = `
                @keyframes fall {
                    to {
                        transform: translateY(100vh) rotate(360deg);
                        opacity: 0;
                    }
                }
            `;
            document.head.appendChild(style);
        }
        
        function simulateTyping(text, callback) {
            typedCmd.textContent = '';
            let j = 0;
            const interval = setInterval(() => {
                if (j <= text.length) {
                    typedCmd.textContent = text.substring(0, j);
                    j++;
                } else {
                    clearInterval(interval);
                    setTimeout(callback, 500);
                }
            }, 100);
        }
        
        function addCommand(text, className = '') {
            const div = document.createElement('div');
            div.className = `command ${className}`;
            div.textContent = text;
            container.appendChild(div);
            container.scrollTop = container.scrollHeight;
            
            updateProgress(progress + (70 / commands.length));
        }
        
        function processCommands() {
            if (i < commands.length) {
                const command = commands[i];
                
                simulateTyping(command.text, () => {
                    addCommand(command.text, command.class);
                    
                    if (command.callback) {
                        command.callback();
                    }
                    
                    i++;
                    setTimeout(processCommands, command.delay);
                });
            }
        }
        
        // Start the sequence
        setTimeout(processCommands, 2000);
    </script>
</body>
</html>
