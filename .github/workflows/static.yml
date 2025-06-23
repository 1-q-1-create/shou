<!DOCTYPE html>
<html lang="zh-CN">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>哪吒2之魔童闹海 - 拼音匹配游戏</title>
    <style>
        * {
            margin: 0;
            padding: 0;
            box-sizing: border-box;
        }
        
        body {
            font-family: 'Microsoft YaHei', sans-serif;
            background: linear-gradient(135deg, #1a237e 0%, #0d47a1 100%);
            color: #fff;
            min-height: 100vh;
            display: flex;
            flex-direction: column;
            align-items: center;
            padding: 20px;
            overflow-x: hidden;
        }
        
        header {
            text-align: center;
            margin: 20px 0;
            padding: 15px;
            width: 100%;
            max-width: 900px;
            position: relative;
        }
        
        h1 {
            font-size: 2.8rem;
            text-shadow: 0 0 10px #ff5722, 0 0 20px #ff5722;
            margin-bottom: 10px;
            letter-spacing: 3px;
            background: linear-gradient(to right, #ff9800, #ff5722);
            -webkit-background-clip: text;
            -webkit-text-fill-color: transparent;
        }
        
        .subtitle {
            font-size: 1.4rem;
            margin-bottom: 20px;
            color: #ffeb3b;
        }
        
        .game-container {
            background: rgba(0, 20, 40, 0.7);
            border: 3px solid #4fc3f7;
            border-radius: 15px;
            padding: 25px;
            width: 100%;
            max-width: 900px;
            box-shadow: 0 0 30px rgba(0, 150, 255, 0.5);
            margin-bottom: 30px;
            position: relative;
            overflow: hidden;
        }
        
        .game-container::before {
            content: "";
            position: absolute;
            top: 0;
            left: 0;
            width: 100%;
            height: 100%;
            background: url('data:image/svg+xml;utf8,<svg xmlns="http://www.w3.org/2000/svg" viewBox="0 0 100 100"><path d="M0,0 L100,100" stroke="rgba(79, 195, 247, 0.1)" stroke-width="1"/></svg>');
            background-size: 20px 20px;
            pointer-events: none;
        }
        
        .rules {
            background: rgba(255, 152, 0, 0.15);
            border: 2px solid #ff9800;
            border-radius: 10px;
            padding: 15px;
            margin-bottom: 30px;
            font-size: 1.1rem;
            line-height: 1.6;
        }
        
        .rules h2 {
            color: #ffeb3b;
            margin-bottom: 10px;
            text-align: center;
        }
        
        .rules ul {
            padding-left: 25px;
        }
        
        .rules li {
            margin-bottom: 8px;
        }
        
        .score-container {
            display: flex;
            justify-content: center;
            margin: 20px 0;
            font-size: 1.4rem;
            color: #ffeb3b;
        }
        
        .score {
            font-weight: bold;
            font-size: 2rem;
            margin-left: 15px;
            color: #4caf50;
        }
        
        .monsters-row {
            display: flex;
            justify-content: space-around;
            margin: 30px 0;
            padding: 15px;
            border: 2px dashed #4fc3f7;
            border-radius: 10px;
            background: rgba(0, 40, 80, 0.4);
        }
        
        .monster-item {
            display: flex;
            flex-direction: column;
            align-items: center;
            width: 120px;
            padding: 10px;
            border-radius: 10px;
            transition: all 0.3s;
        }
        
        .monster-item.drag-over {
            background: rgba(255, 152, 0, 0.3);
            transform: scale(1.05);
        }
        
        .monster-img {
            width: 80px;
            height: 80px;
            background: #fff;
            border-radius: 50%;
            display: flex;
            align-items: center;
            justify-content: center;
            font-size: 2.5rem;
            margin-bottom: 10px;
            border: 3px solid #ff5722;
            box-shadow: 0 0 15px rgba(255, 87, 34, 0.5);
        }
        
        .pinyin-row {
            display: flex;
            justify-content: space-around;
            margin: 30px 0;
            padding: 15px;
            border: 2px dashed #ff9800;
            border-radius: 10px;
            background: rgba(80, 0, 40, 0.4);
        }
        
        .pinyin-item {
            width: 120px;
            padding: 15px 10px;
            background: #ff9800;
            color: #1a237e;
            border-radius: 8px;
            text-align: center;
            font-size: 1.4rem;
            font-weight: bold;
            cursor: grab;
            transition: all 0.3s;
            box-shadow: 0 4px 8px rgba(0, 0, 0, 0.3);
        }
        
        .pinyin-item.dragging {
            opacity: 0.7;
            transform: scale(0.95);
            box-shadow: 0 0 20px #ffeb3b;
        }
        
        .controls {
            display: flex;
            justify-content: center;
            gap: 20px;
            margin-top: 20px;
        }
        
        button {
            padding: 12px 30px;
            font-size: 1.2rem;
            background: linear-gradient(45deg, #ff5722, #ff9800);
            color: white;
            border: none;
            border-radius: 50px;
            cursor: pointer;
            transition: all 0.3s;
            font-weight: bold;
            letter-spacing: 1px;
            box-shadow: 0 5px 15px rgba(255, 87, 34, 0.4);
        }
        
        button:hover {
            transform: translateY(-3px);
            box-shadow: 0 8px 20px rgba(255, 87, 34, 0.6);
        }
        
        button:active {
            transform: translateY(1px);
        }
        
        #resetBtn {
            background: linear-gradient(45deg, #2196f3, #03a9f4);
        }
        
        .nezhua {
            position: absolute;
            top: 20px;
            right: 20px;
            font-size: 5rem;
            transform: rotate(15deg);
            text-shadow: 0 0 10px #ff5722;
            z-index: 10;
        }
        
        .result {
            position: fixed;
            top: 0;
            left: 0;
            width: 100%;
            height: 100%;
            background: rgba(0, 0, 0, 0.8);
            display: flex;
            flex-direction: column;
            align-items: center;
            justify-content: center;
            z-index: 100;
            opacity: 0;
            pointer-events: none;
            transition: opacity 0.5s;
        }
        
        .result.show {
            opacity: 1;
            pointer-events: all;
        }
        
        .result-content {
            background: linear-gradient(135deg, #1a237e 0%, #0d47a1 100%);
            padding: 40px;
            border-radius: 20px;
            text-align: center;
            max-width: 500px;
            width: 90%;
            border: 3px solid #ff5722;
            box-shadow: 0 0 40px rgba(255, 87, 34, 0.7);
        }
        
        .result h2 {
            font-size: 2.5rem;
            margin-bottom: 20px;
            color: #ffeb3b;
        }
        
        .final-score {
            font-size: 4rem;
            font-weight: bold;
            margin: 20px 0;
            color: #4caf50;
            text-shadow: 0 0 10px rgba(76, 175, 80, 0.8);
        }
        
        .message {
            font-size: 1.6rem;
            margin: 20px 0;
            color: #ff9800;
        }
        
        .firework {
            position: absolute;
            width: 10px;
            height: 10px;
            border-radius: 50%;
            pointer-events: none;
        }
        
        @media (max-width: 768px) {
            h1 { font-size: 2rem; }
            .subtitle { font-size: 1.1rem; }
            .monster-item, .pinyin-item { width: 90px; }
            .monster-img { width: 60px; height: 60px; font-size: 2rem; }
            .pinyin-item { font-size: 1.1rem; padding: 10px 5px; }
        }
        
        @media (max-width: 480px) {
            h1 { font-size: 1.6rem; }
            .monster-item, .pinyin-item { width: 70px; }
            .monster-img { width: 50px; height: 50px; font-size: 1.5rem; }
            .pinyin-item { font-size: 0.9rem; }
            button { padding: 10px 20px; font-size: 1rem; }
        }
    </style>
</head>
<body>
    <header>
        <h1>哪吒2之魔童闹海</h1>
        <div class="subtitle">降妖除魔 · 拼音匹配挑战</div>
        <div class="nezhua">👦🔥</div>
    </header>
    
    <div class="game-container">
        <div class="rules">
            <h2>游戏规则</h2>
            <ul>
                <li>上方是妖怪图片（龙、豹、鼠、虎、牛）</li>
                <li>下方是妖怪拼音（long, bao, shu, hu, niu）</li>
                <li>拖拽拼音到对应图片下方完成匹配</li>
                <li>初始分数：10分，每错一个扣2分</li>
                <li>完成所有匹配后点击"提交"查看得分</li>
            </ul>
        </div>
        
        <div class="score-container">
            当前得分: <span class="score" id="score">10</span> / 10
        </div>
        
        <div class="monsters-row" id="monstersRow">
            <!-- 妖怪图片将通过JS动态生成 -->
        </div>
        
        <div class="pinyin-row" id="pinyinRow">
            <!-- 拼音将通过JS动态生成 -->
        </div>
        
        <div class="controls">
            <button id="submitBtn">提交答案</button>
            <button id="resetBtn">重新开始</button>
        </div>
    </div>
    
    <div class="result" id="result">
        <div class="result-content">
            <h2>降妖除魔完成!</h2>
            <div class="message" id="resultMessage"></div>
            <div class="final-score" id="finalScore">0分</div>
            <button id="playAgainBtn">再战一场</button>
        </div>
    </div>

    <script>
        document.addEventListener('DOMContentLoaded', () => {
            // 游戏数据
            const monsters = [
                { name: '龙', pinyin: 'long', emoji: '🐉' },
                { name: '豹', pinyin: 'bao', emoji: '🐆' },
                { name: '鼠', pinyin: 'shu', emoji: '🐭' },
                { name: '虎', pinyin: 'hu', emoji: '🐯' },
                { name: '牛', pinyin: 'niu', emoji: '🐮' }
            ];
            
            // 游戏状态
            let currentScore = 10;
            let matchedPairs = 0;
            let gameCompleted = false;
            
            // DOM元素
            const monstersRow = document.getElementById('monstersRow');
            const pinyinRow = document.getElementById('pinyinRow');
            const scoreElement = document.getElementById('score');
            const submitBtn = document.getElementById('submitBtn');
            const resetBtn = document.getElementById('resetBtn');
            const resultElement = document.getElementById('result');
            const finalScoreElement = document.getElementById('finalScore');
            const resultMessageElement = document.getElementById('resultMessage');
            const playAgainBtn = document.getElementById('playAgainBtn');
            
            // 初始化游戏
            function initGame() {
                // 重置状态
                currentScore = 10;
                matchedPairs = 0;
                gameCompleted = false;
                scoreElement.textContent = currentScore;
                
                // 清空容器
                monstersRow.innerHTML = '';
                pinyinRow.innerHTML = '';
                
                // 创建随机顺序的怪物
                const shuffledMonsters = [...monsters].sort(() => Math.random() - 0.5);
                
                // 添加怪物到界面
                shuffledMonsters.forEach(monster => {
                    const monsterItem = document.createElement('div');
                    monsterItem.className = 'monster-item';
                    monsterItem.dataset.name = monster.name;
                    
                    monsterItem.innerHTML = `
                        <div class="monster-img">${monster.emoji}</div>
                        <div>${monster.name}</div>
                    `;
                    
                    monstersRow.appendChild(monsterItem);
                });
                
                // 创建随机顺序的拼音
                const shuffledPinyin = [...monsters]
                    .map(m => m.pinyin)
                    .sort(() => Math.random() - 0.5);
                
                // 添加拼音到界面
                shuffledPinyin.forEach(pinyin => {
                    const pinyinItem = document.createElement('div');
                    pinyinItem.className = 'pinyin-item';
                    pinyinItem.textContent = pinyin;
                    pinyinItem.draggable = true;
                    pinyinItem.dataset.pinyin = pinyin;
                    
                    // 拖拽事件处理
                    pinyinItem.addEventListener('dragstart', handleDragStart);
                    pinyinItem.addEventListener('dragend', handleDragEnd);
                    
                    pinyinRow.appendChild(pinyinItem);
                });
                
                // 设置怪物区域的拖拽事件
                const monsterItems = document.querySelectorAll('.monster-item');
                monsterItems.forEach(item => {
                    item.addEventListener('dragover', handleDragOver);
                    item.addEventListener('dragenter', handleDragEnter);
                    item.addEventListener('dragleave', handleDragLeave);
                    item.addEventListener('drop', handleDrop);
                });
            }
            
            // 拖拽处理函数
            let draggedItem = null;
            
            function handleDragStart(e) {
                draggedItem = this;
                this.classList.add('dragging');
                e.dataTransfer.effectAllowed = 'move';
            }
            
            function handleDragEnd() {
                this.classList.remove('dragging');
            }
            
            function handleDragOver(e) {
                e.preventDefault();
                return false;
            }
            
            function handleDragEnter(e) {
                this.classList.add('drag-over');
            }
            
            function handleDragLeave() {
                this.classList.remove('drag-over');
            }
            
            function handleDrop(e) {
                e.preventDefault();
                this.classList.remove('drag-over');
                
                // 检查是否已经匹配过
                if (this.querySelector('.matched')) {
                    return;
                }
                
                // 获取怪物名称
                const monsterName = this.dataset.name;
                
                // 查找对应的拼音
                const correctPinyin = monsters.find(m => m.name === monsterName).pinyin;
                
                // 检查匹配是否正确
                const isCorrect = draggedItem.dataset.pinyin === correctPinyin;
                
                if (isCorrect) {
                    // 创建匹配标记
                    const checkMark = document.createElement('div');
                    checkMark.textContent = '✓';
                    checkMark.style.color = '#4caf50';
                    checkMark.style.fontSize = '2rem';
                    checkMark.style.position = 'absolute';
                    checkMark.style.top = '10px';
                    checkMark.style.right = '10px';
                    
                    // 添加到怪物项
                    this.appendChild(checkMark);
                    this.classList.add('matched');
                    
                    // 禁用拼音项
                    draggedItem.style.opacity = '0.5';
                    draggedItem.style.cursor = 'default';
                    draggedItem.draggable = false;
                    
                    // 更新匹配计数
                    matchedPairs++;
                    
                    // 检查游戏是否完成
                    if (matchedPairs === monsters.length) {
                        gameCompleted = true;
                    }
                } else {
                    // 扣分处理
                    currentScore = Math.max(0, currentScore - 2);
                    scoreElement.textContent = currentScore;
                    
                    // 显示错误动画
                    draggedItem.style.animation = 'shake 0.5s';
                    setTimeout(() => {
                        draggedItem.style.animation = '';
                    }, 500);
                }
                
                return false;
            }
            
            // 提交答案
            submitBtn.addEventListener('click', () => {
                if (!gameCompleted) {
                    alert('请完成所有匹配后再提交！');
                    return;
                }
                
                // 显示结果
                finalScoreElement.textContent = `${currentScore}分`;
                
                // 设置结果消息
                let message = '';
                if (currentScore === 10) {
                    message = '完美！你成功降服了所有妖怪！';
                    createFireworks();
                } else if (currentScore >= 8) {
                    message = '干得漂亮！妖怪们都被你制服了！';
                } else if (currentScore >= 6) {
                    message = '不错！但还可以做得更好！';
                } else {
                    message = '再接再厉！哪吒相信你能做得更好！';
                }
                
                resultMessageElement.textContent = message;
                resultElement.classList.add('show');
            });
            
            // 重新开始游戏
            resetBtn.addEventListener('click', initGame);
            playAgainBtn.addEventListener('click', () => {
                resultElement.classList.remove('show');
                initGame();
            });
            
            // 烟花效果
            function createFireworks() {
                const colors = ['#ff5722', '#ffeb3b', '#4caf50', '#2196f3', '#9c27b0'];
                
                for (let i = 0; i < 50; i++) {
                    setTimeout(() => {
                        const firework = document.createElement('div');
                        firework.className = 'firework';
                        
                        // 随机位置
                        const posX = Math.random() * window.innerWidth;
                        const posY = Math.random() * window.innerHeight;
                        
                        // 随机颜色
                        const color = colors[Math.floor(Math.random() * colors.length)];
                        
                        // 随机大小
                        const size = 2 + Math.random() * 8;
                        
                        firework.style.left = `${posX}px`;
                        firework.style.top = `${posY}px`;
                        firework.style.width = `${size}px`;
                        firework.style.height = `${size}px`;
                        firework.style.backgroundColor = color;
                        firework.style.boxShadow = `0 0 ${size * 2}px ${size}px ${color}`;
                        
                        document.body.appendChild(firework);
                        
                        // 移除烟花
                        setTimeout(() => {
                            firework.remove();
                        }, 1000);
                    }, i * 100);
                }
            }
            
            // 开始游戏
            initGame();
        });
    </script>
</body>
</html>
