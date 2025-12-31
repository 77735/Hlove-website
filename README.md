[index.html](https://github.com/user-attachments/files/24389740/index.html)
<!DOCTYPE html>
<html lang="zh-CN">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>何政的爱心网站</title>
    <style>
        * {
            margin: 0;
            padding: 0;
            box-sizing: border-box;
        }
        
        body {
            font-family: 'Arial', sans-serif;
            background: linear-gradient(135deg, #ff9a9e 0%, #fecfef 100%);
            overflow: hidden;
            height: 100vh;
            display: flex;
            justify-content: center;
            align-items: center;
        }
        
        /* 背景容器 */
        .background-container {
            position: fixed;
            top: 0;
            left: 0;
            width: 100%;
            height: 100%;
            pointer-events: none;
            z-index: 1;
        }
        
        /* 爱心样式 */
        .heart {
            position: absolute;
            width: 30px;
            height: 30px;
            background-color: #ff6b6b;
            transform: rotate(-45deg);
            animation: floatHeart 8s ease-in-out infinite;
            opacity: 0.6;
        }
        
        .heart:before,
        .heart:after {
            content: '';
            position: absolute;
            width: 30px;
            height: 30px;
            background-color: #ff6b6b;
            border-radius: 50%;
        }
        
        .heart:before {
            top: -15px;
            left: 0;
        }
        
        .heart:after {
            left: 15px;
            top: 0;
        }
        
        @keyframes floatHeart {
            0%, 100% {
                transform: translateY(0) rotate(-45deg);
            }
            50% {
                transform: translateY(-30px) rotate(-45deg);
            }
        }
        
        /* 气球样式 */
        .balloon {
            position: absolute;
            width: 40px;
            height: 50px;
            background-color: #ffd700;
            border-radius: 50% 50% 50% 50% / 40% 40% 60% 60%;
            animation: floatBalloon 10s ease-in-out infinite;
            opacity: 0.7;
        }
        
        .balloon:before {
            content: '';
            position: absolute;
            bottom: -20px;
            left: 50%;
            transform: translateX(-50%);
            width: 2px;
            height: 20px;
            background-color: #ffd700;
        }
        
        @keyframes floatBalloon {
            0%, 100% {
                transform: translateY(0) rotate(-5deg);
            }
            50% {
                transform: translateY(-50px) rotate(5deg);
            }
        }
        
        /* 主内容区域 */
        .main-container {
            position: relative;
            z-index: 2;
            background-color: rgba(255, 255, 255, 0.95);
            padding: 40px;
            border-radius: 20px;
            box-shadow: 0 15px 40px rgba(0, 0, 0, 0.2);
            text-align: center;
            max-width: 500px;
            width: 90%;
        }
        
        h1 {
            color: #ff6b6b;
            margin-bottom: 30px;
            font-size: 28px;
            text-shadow: 2px 2px 4px rgba(0, 0, 0, 0.1);
        }
        
        .input-container {
            display: flex;
            flex-direction: column;
            gap: 20px;
        }
        
        textarea {
            width: 100%;
            height: 120px;
            padding: 20px;
            border: 3px solid #ff6b6b;
            border-radius: 15px;
            font-size: 18px;
            resize: none;
            font-family: 'Arial', sans-serif;
            transition: all 0.3s ease;
        }
        
        textarea:focus {
            outline: none;
            border-color: #ff8787;
            box-shadow: 0 0 20px rgba(255, 107, 107, 0.4);
        }
        
        button {
            padding: 15px 30px;
            background-color: #ff6b6b;
            color: white;
            border: none;
            border-radius: 15px;
            font-size: 18px;
            cursor: pointer;
            transition: all 0.3s ease;
            font-weight: bold;
        }
        
        button:hover {
            background-color: #ff5252;
            transform: translateY(-3px);
            box-shadow: 0 8px 20px rgba(255, 107, 107, 0.4);
        }
        
        button:active {
            transform: translateY(0);
        }
        
        /* 模态窗口通用样式 */
        .modal {
            display: none;
            position: fixed;
            z-index: 1000;
            left: 0;
            top: 0;
            width: 100%;
            height: 100%;
            background-color: rgba(0, 0, 0, 0.6);
            backdrop-filter: blur(8px);
            overflow: hidden;
        }
        
        .modal-content {
            position: relative;
            background-color: rgba(255, 255, 255, 0.98);
            margin: 10% auto;
            padding: 40px;
            border-radius: 25px;
            width: 80%;
            max-width: 500px;
            text-align: center;
            box-shadow: 0 25px 50px rgba(0, 0, 0, 0.3);
            animation: modalSlideIn 0.6s ease;
            z-index: 1001;
        }
        
        @keyframes modalSlideIn {
            from {
                opacity: 0;
                transform: translateY(-60px) scale(0.85);
            }
            to {
                opacity: 1;
                transform: translateY(0) scale(1);
            }
        }
        
        /* 钻戒和爱心容器 */
        .rings-hearts-container {
            position: fixed;
            top: 0;
            left: 0;
            width: 100%;
            height: 100%;
            pointer-events: none;
            z-index: 999;
        }
        
        /* 钻戒样式 */
        .ring {
            position: absolute;
            width: 35px;
            height: 35px;
            border: 4px solid #ffd700;
            border-radius: 50%;
            opacity: 0.9;
            animation: floatRing 6s ease-in-out infinite;
        }
        
        .ring:before {
            content: '';
            position: absolute;
            top: 50%;
            left: 50%;
            transform: translate(-50%, -50%);
            width: 12px;
            height: 12px;
            background-color: #fff;
            border-radius: 50%;
            box-shadow: 0 0 15px #ffd700;
        }
        
        @keyframes floatRing {
            0%, 100% {
                transform: translateY(0) rotate(0deg);
            }
            25% {
                transform: translateY(-25px) rotate(90deg);
            }
            50% {
                transform: translateY(15px) rotate(180deg);
            }
            75% {
                transform: translateY(-15px) rotate(270deg);
            }
        }
        
        /* 浅绿色爱心样式 */
        .green-heart {
            position: absolute;
            width: 25px;
            height: 25px;
            background-color: #90ee90;
            transform: rotate(-45deg);
            animation: floatGreenHeart 7s ease-in-out infinite;
            opacity: 0.8;
        }
        
        .green-heart:before,
        .green-heart:after {
            content: '';
            position: absolute;
            width: 25px;
            height: 25px;
            background-color: #90ee90;
            border-radius: 50%;
        }
        
        .green-heart:before {
            top: -12.5px;
            left: 0;
        }
        
        .green-heart:after {
            left: 12.5px;
            top: 0;
        }
        
        @keyframes floatGreenHeart {
            0%, 100% {
                transform: translateY(0) rotate(-45deg);
            }
            50% {
                transform: translateY(-35px) rotate(-45deg);
            }
        }
        
        /* 烟花容器 */
        .fireworks-container {
            position: fixed;
            top: 0;
            left: 0;
            width: 100%;
            height: 100%;
            pointer-events: none;
            z-index: 999;
        }
        
        /* 烟花粒子样式 */
        .firework-particle {
            position: absolute;
            width: 6px;
            height: 6px;
            border-radius: 50%;
            animation: explode 2s ease-out forwards;
        }
        
        @keyframes explode {
            0% {
                transform: translate(0, 0) scale(1);
                opacity: 1;
            }
            100% {
                transform: translate(var(--tx), var(--ty)) scale(0);
                opacity: 0;
            }
        }
        
        /* 答案文本样式 */
        .answer-text {
            font-size: 32px;
            font-weight: bold;
            color: #333;
            margin-bottom: 30px;
            padding: 20px;
            background: linear-gradient(135deg, rgba(255, 215, 0, 0.2), rgba(144, 238, 144, 0.2));
            border-radius: 15px;
            animation: pulse 2s ease-in-out infinite;
        }
        
        @keyframes pulse {
            0%, 100% {
                transform: scale(1);
            }
            50% {
                transform: scale(1.05);
            }
        }
        
        .close-btn {
            background-color: #ffd700;
            color: #333;
            font-weight: bold;
            font-size: 16px;
        }
        
        .close-btn:hover {
            background-color: #ffed4e;
        }
    </style>
</head>
<body>
    <!-- 背景容器 -->
    <div class="background-container"></div>
    
    <!-- 主内容区域 -->
    <div class="main-container">
        <h1>何政的爱心网站</h1>
        <div class="input-container">
            <textarea id="question" placeholder="请输入内容..."></textarea>
            <button id="submit-btn">提交</button>
        </div>
    </div>
    
    <!-- 钻戒和爱心模态窗口 -->
    <div id="ring-heart-modal" class="modal">
        <div class="rings-hearts-container"></div>
        <div class="modal-content">
            <h2 style="color: #ffd700; margin-bottom: 20px; font-size: 26px;">💍 答案 💍</h2>
            <p id="ring-heart-answer" class="answer-text"></p>
            <button id="ring-heart-close-btn" class="close-btn">关闭</button>
        </div>
    </div>
    
    <!-- 烟花模态窗口 -->
    <div id="fireworks-modal" class="modal">
        <div class="fireworks-container"></div>
        <div class="modal-content">
            <h2 style="color: #ff6b6b; margin-bottom: 20px; font-size: 26px;">🎆 答案 🎆</h2>
            <p id="fireworks-answer" class="answer-text"></p>
            <button id="fireworks-close-btn" class="close-btn">关闭</button>
        </div>
    </div>
    
    <script>
        // 生成背景爱心和气球
        function createBackgroundElements() {
            const container = document.querySelector('.background-container');
            
            // 生成爱心
            for (let i = 0; i < 30; i++) {
                const heart = document.createElement('div');
                heart.classList.add('heart');
                heart.style.left = Math.random() * 100 + '%';
                heart.style.top = Math.random() * 100 + '%';
                heart.style.animationDelay = Math.random() * 5 + 's';
                heart.style.animationDuration = Math.random() * 3 + 5 + 's';
                
                const size = Math.random() * 20 + 20;
                heart.style.width = size + 'px';
                heart.style.height = size + 'px';
                
                container.appendChild(heart);
            }
            
            // 生成气球
            for (let i = 0; i < 20; i++) {
                const balloon = document.createElement('div');
                balloon.classList.add('balloon');
                balloon.style.left = Math.random() * 100 + '%';
                balloon.style.top = Math.random() * 100 + '%';
                balloon.style.animationDelay = Math.random() * 6 + 's';
                balloon.style.animationDuration = Math.random() * 4 + 6 + 's';
                
                const size = Math.random() * 15 + 35;
                balloon.style.width = size + 'px';
                balloon.style.height = size * 1.25 + 'px';
                
                container.appendChild(balloon);
            }
        }
        
        // 生成钻戒
        function createRing() {
            const container = document.querySelector('.rings-hearts-container');
            const ring = document.createElement('div');
            ring.classList.add('ring');
            
            ring.style.left = Math.random() * 100 + '%';
            ring.style.top = Math.random() * 100 + '%';
            
            const size = Math.random() * 20 + 25;
            ring.style.width = size + 'px';
            ring.style.height = size + 'px';
            
            ring.style.animationDelay = Math.random() * 4 + 's';
            ring.style.animationDuration = Math.random() * 3 + 3 + 's';
            
            const colors = ['#ffd700', '#ffed4e', '#fff9c4', '#ffe082'];
            ring.style.borderColor = colors[Math.floor(Math.random() * colors.length)];
            
            container.appendChild(ring);
            
            setTimeout(() => {
                ring.remove();
            }, 6000);
        }
        
        // 生成浅绿色爱心
        function createGreenHeart() {
            const container = document.querySelector('.rings-hearts-container');
            const heart = document.createElement('div');
            heart.classList.add('green-heart');
            
            heart.style.left = Math.random() * 100 + '%';
            heart.style.top = Math.random() * 100 + '%';
            
            const size = Math.random() * 15 + 20;
            heart.style.width = size + 'px';
            heart.style.height = size + 'px';
            
            heart.style.animationDelay = Math.random() * 3 + 's';
            heart.style.animationDuration = Math.random() * 2 + 4 + 's';
            
            container.appendChild(heart);
            
            setTimeout(() => {
                heart.remove();
            }, 7000);
        }
        
        // 生成烟花
        function createFirework(x, y) {
            const container = document.querySelector('.fireworks-container');
            const colors = ['#ff6b6b', '#ffd700', '#90ee90', '#87ceeb', '#dda0dd', '#ff8c00'];
            
            for (let i = 0; i < 30; i++) {
                const particle = document.createElement('div');
                particle.classList.add('firework-particle');
                
                particle.style.left = x + 'px';
                particle.style.top = y + 'px';
                particle.style.backgroundColor = colors[Math.floor(Math.random() * colors.length)];
                
                const angle = (i / 30) * Math.PI * 2;
                const distance = Math.random() * 200 + 100;
                const tx = Math.cos(angle) * distance;
                const ty = Math.sin(angle) * distance;
                
                particle.style.setProperty('--tx', tx + 'px');
                particle.style.setProperty('--ty', ty + 'px');
                
                container.appendChild(particle);
                
                setTimeout(() => {
                    particle.remove();
                }, 2000);
            }
        }
        
        // 显示钻戒和爱心模态窗口
        function showRingHeartModal(answer) {
            const modal = document.getElementById('ring-heart-modal');
            const answerText = document.getElementById('ring-heart-answer');
            const container = document.querySelector('.rings-hearts-container');
            
            answerText.textContent = answer;
            container.innerHTML = '';
            
            modal.style.display = 'flex';
            
            // 生成钻戒和爱心
            for (let i = 0; i < 20; i++) {
                setTimeout(createRing, i * 100);
                setTimeout(createGreenHeart, i * 150);
            }
        }
        
        // 显示烟花模态窗口
        function showFireworksModal(answer) {
            const modal = document.getElementById('fireworks-modal');
            const answerText = document.getElementById('fireworks-answer');
            const container = document.querySelector('.fireworks-container');
            
            answerText.textContent = answer;
            container.innerHTML = '';
            
            modal.style.display = 'flex';
            
            // 持续生成烟花
            const fireworkInterval = setInterval(() => {
                const x = Math.random() * window.innerWidth;
                const y = Math.random() * window.innerHeight * 0.6 + window.innerHeight * 0.2;
                createFirework(x, y);
            }, 500);
            
            modal.dataset.fireworkInterval = fireworkInterval;
        }
        
        // 关闭模态窗口
        function closeModal(modalId) {
            const modal = document.getElementById(modalId);
            modal.style.display = 'none';
            
            if (modalId === 'ring-heart-modal') {
                document.querySelector('.rings-hearts-container').innerHTML = '';
            } else if (modalId === 'fireworks-modal') {
                clearInterval(modal.dataset.fireworkInterval);
                document.querySelector('.fireworks-container').innerHTML = '';
            }
        }
        
        // 提交按钮事件
        document.getElementById('submit-btn').addEventListener('click', function() {
            const question = document.getElementById('question').value.trim();
            const lowerQuestion = question.toLowerCase();
            
            if (lowerQuestion.includes('全世界最美丽的女孩')) {
                showRingHeartModal('陈瑞瑞❤');
            } else if (lowerQuestion.includes('陈瑞瑞')) {
                showFireworksModal('Happy New Year');
            } else if (question) {
                alert('抱歉，我还不知道这个问题的答案呢！');
            } else {
                alert('请输入内容！');
            }
        });
        
        // Enter键提交
        document.getElementById('question').addEventListener('keypress', function(e) {
            if (e.key === 'Enter' && !e.shiftKey) {
                e.preventDefault();
                document.getElementById('submit-btn').click();
            }
        });
        
        // 关闭按钮事件
        document.getElementById('ring-heart-close-btn').addEventListener('click', function() {
            closeModal('ring-heart-modal');
        });
        
        document.getElementById('fireworks-close-btn').addEventListener('click', function() {
            closeModal('fireworks-modal');
        });
        
        // 点击模态窗口外部关闭
        window.addEventListener('click', function(e) {
            if (e.target.id === 'ring-heart-modal') {
                closeModal('ring-heart-modal');
            } else if (e.target.id === 'fireworks-modal') {
                closeModal('fireworks-modal');
            }
        });
        
        // 初始化背景元素
        createBackgroundElements();
    </script>
</body>
</html>
