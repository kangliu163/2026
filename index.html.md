<!DOCTYPE html>  
<html lang="zh-CN">  
<head>  
    <meta charset="UTF-8">  
    <meta name="viewport" content="width=device-width, initial-scale=1.0">  
    <title>2026 **致我的宝宝**</title>  
    <style>  
        * {  
            margin: 0;  
            padding: 0;  
            box-sizing: border-box;  
            font-family: "Microsoft YaHei", sans-serif;  
        }  
  
        body {  
            background-color: #0a0a16;  
            height: 100vh;  
            overflow: hidden;  
            display: flex;  
            justify-content: center;  
            align-items: center;  
        }  
  
        .slider {  
            width: 100vw;  
            height: 100vh;  
            display: flex;  
            transition: transform 0.8s cubic-bezier(0.4, 0, 0.2, 1);  
            position: relative;  
        }  
  
        .page {  
            min-width: 100vw;  
            height: 100vh;  
            display: flex;  
            flex-direction: column;  
            justify-content: center;  
            align-items: center;  
            position: relative;  
            overflow: hidden;  
            opacity: 0;  
            animation: fadeIn 1s ease forwards;  
        }  
        /* **文字渐入动画** */  
        @keyframes fadeIn {  
            to {  
                opacity: 1;  
            }  
        }  
        /* **错开各页面动画时间** */  
        .page1 { animation-delay: 0.2s; }  
        .page2 { animation-delay: 0.4s; }  
        .page3 { animation-delay: 0.6s; }  
  
        /* **雪花特效** - **挂载到**slider**上，让雪花覆盖所有页面** */  
        .snowflake {  
            position: absolute;  
            top: -10px;  
            color: #fff;  
            opacity: 0.7;  
            font-size: 12px;  
            pointer-events: none;  
            animation: fall linear infinite;  
            z-index: 10;  
        }  
  
        @keyframes fall {  
            to {  
                transform: translateY(105vh);  
                opacity: 0;  
            }  
        }  
  
        /* **页面**1**样式** */  
        .page1 {  
            background: linear-gradient(120deg, #1a1a2e, #16213e);  
        }  
        .page1 h1 {  
            color: #fff;  
            font-size: 3.5rem;  
            margin-bottom: 1rem;  
            text-shadow: 0 0 15px #4cc9f0;  
        }  
        .page1 p {  
            color: #c7c7ff;  
            font-size: 1.5rem;  
        }  
        .page1 .year {  
            color: #ffd166;  
            font-size: 5rem;  
            margin-top: 2rem;  
            text-shadow: 0 0 20px #ffd166;  
        }  
  
        /* **页面**2**样式** */  
        .page2 {  
            background: linear-gradient(120deg, #0f3460, #1a1a2e);  
        }  
        .page2 .game-card {  
            background: rgba(255, 255, 255, 0.1);  
            padding: 3rem;  
            border-radius: 20px;  
            backdrop-filter: blur(10px);  
            border: 1px solid rgba(255, 255, 255, 0.2);  
            text-align: center;  
        }  
        .page2 h2 {  
            color: #4cc9f0;  
            font-size: 2.2rem;  
            margin-bottom: 1.5rem;  
        }  
        .page2 p {  
            color: #fff;  
            font-size: 1.3rem;  
            line-height: 1.8;  
        }  
        /* **昵称爱心高亮** */  
        .page2 .nickname {  
            color: #ff758f;  
            font-weight: bold;  
            text-shadow: 0 0 8px #ff758f;  
            position: relative;  
        }  
        .page2 .nickname::before {  
            content: "❤️";  
            position: absolute;  
            left: -20px;  
            top: -2px;  
            animation: bounce 1s ease infinite;  
        }  
        @keyframes bounce {  
            0%,100% { transform: scale(1); }  
            50% { transform: scale(1.2); }  
        }  
  
        /* **页面**3**样式** */  
        .page3 {  
            background: linear-gradient(120deg, #16213e, #0f3460);  
        }  
        .page3 .blessing {  
            background: rgba(255, 255, 255, 0.1);  
            padding: 3rem 4rem;  
            border-radius: 20px;  
            backdrop-filter: blur(10px);  
            border: 1px solid rgba(255, 255, 255, 0.2);  
            text-align: center;  
        }  
        .page3 h2 {  
            color: #ffd166;  
            font-size: 2.5rem;  
            margin-bottom: 2rem;  
        }  
        .page3 p {  
            color: #fff;  
            font-size: 1.4rem;  
            line-height: 2;  
        }  
        .page3 .highlight {  
            color: #ff758f;  
            font-weight: bold;  
            text-shadow: 0 0 8px #ff758f;  
            position: relative;  
        }  
        .page3 .highlight::before {  
            content: "❤️";  
            position: absolute;  
            left: -20px;  
            top: -2px;  
            animation: bounce 1s ease infinite;  
        }  
        .page3 .btn {  
            margin-top: 2.5rem;  
            padding: 1rem 3rem;  
            background: linear-gradient(90deg, #ff758f, #ff7eb3);  
            border: none;  
            border-radius: 50px;  
            color: white;  
            font-size: 1.2rem;  
            cursor: pointer;  
            transition: all 0.3s ease;  
        }  
        .page3 .btn:hover {  
            transform: scale(1.05);  
            box-shadow: 0 0 20px #ff758f;  
        }  
        .page3 .tip {  
            color: #c7c7ff;  
            margin-top: 1rem;  
            font-size: 1rem;  
            opacity: 0;  
            transition: opacity 0.3s ease;  
        }  
  
        /* **滑动提示** - **箭头闪烁** */  
        .slide-tip {  
            position: fixed;  
            bottom: 30px;  
            color: #fff;  
            font-size: 1rem;  
            opacity: 0.7;  
            animation: flash 2s ease infinite;  
            z-index: 20;  
        }  
        @keyframes flash {  
            0%,100% { opacity: 0.7; }  
            50% { opacity: 1; }  
        }  
  
        @media (max-width: 768px) {  
            .page1 h1 {  
                font-size: 2.2rem;  
            }  
            .page1 .year {  
                font-size: 3.5rem;  
            }  
            .page2 .game-card {  
                padding: 2rem;  
            }  
            .page2 h2 {  
                font-size: 1.8rem;  
            }  
            .page3 .blessing {  
                padding: 2rem;  
            }  
            .page3 h2 {  
                font-size: 2rem;  
            }  
            .page3 p {  
                font-size: 1.2rem;  
            }  
        }  
    </style>  
</head>  
<body>  
    <div class="slider" id="slider">  
        <!-- **页面**1**：**2026**跨年开场** -->  
        <div class="page page1">  
            <h1>2026 **我们的新年**</h1>  
            <p>**跨越山海** **奔赴彼此**</p>  
            <div class="year">2026</div>  
        </div>  
  
        <!-- **页面**2**：游戏相识回忆** - **文案修改** -->  
        <div class="page page2">  
            <div class="game-card">  
                <h2>**和平精英的相遇**</h2>  
                <p>**还记得在海岛的枪声里**<br>**我遇见了我的** <span class="nickname">**宝宝**</span><br>**从相识到相伴** **期间我们非常开心**<br>**阿玉哥哥希望陪宝宝走的更远**</p>  
            </div>  
        </div>  
  
        <!-- **页面**3**：新年祝福** - **文案修改** -->  
        <div class="page page3">  
            <div class="blessing">  
                <h2>**致我的宝贝**</h2>  
                <p>2026**年的雪落满枝头**<br>**愿我的** <span class="highlight">**宝宝**</span> **岁岁无忧**<br>**平安喜乐** **万事顺意**<br>**新的一年** **阿玉哥哥继续陪着宝宝**<br>**无论开心快乐** **烦恼忧愁**<br>**一起闹一起笑**<br>**还有一个最最最最重要的**<br>**要一起狂打木乃伊！！！！！**<br>**当然** **想要和宝宝做的还有很多很多**……</p>  
                <button class="btn" onclick="copyBlessing()">**复制新年祝福**</button>  
                <p class="tip" id="tip">**祝福复制成功啦**~</p>  
            </div>  
        </div>  
    </div>  
  
    <div class="slide-tip">← **左右滑动切换页面** →</div>  
  
    <!-- **背景音乐** -->  
    <audio src="https://music.163.com/song/media/outer/url?id=1864711050.mp3" loop autoplay muted id="bgm">  
    <button style="position:fixed;top:20px;right:20px;padding:0.5rem 1rem;border-radius:20px;border:none;background:rgba(255,255,255,0.2);color:#fff;cursor:pointer;" onclick="toggleBgm()">**开启音乐**</button>  
  
    <script>  
        // **雪花生成函数**  
        function createSnow() {  
            const slider = document.getElementById('slider');  
            const snow = document.createElement('div');  
            snow.className = 'snowflake';  
            snow.innerText = '❄️';  
              
            // **随机位置和动画时长**  
            const left = Math.random() * 100;  
            const duration = Math.random() * 10 + 5;  
            const size = Math.random() * 8 + 4;  
  
            snow.style.left = `${left}vw`;  
            snow.style.fontSize = `${size}px`;  
            snow.style.animationDuration = `${duration}s`;  
  
            slider.appendChild(snow);  
  
            // **移除雪花**  
            setTimeout(() => {  
                snow.remove();  
            }, duration * 1000);  
        }  
  
        // **持续生成雪花**  
        setInterval(createSnow, 200);  
  
        // **滑动切换页面**  
        let currentPage = 0;  
        const slider = document.getElementById('slider');  
        const pageCount = document.querySelectorAll('.page').length;  
  
        // **鼠标拖拽滑动**  
        let startX = 0;  
        let isDragging = false;  
  
        document.addEventListener('mousedown', (e) => {  
            isDragging = true;  
            startX = e.clientX;  
        });  
  
        document.addEventListener('mousemove', (e) => {  
            if (!isDragging) return;  
            const moveX = e.clientX - startX;  
            slider.style.transform = `translateX(${-currentPage * 100 + moveX / 10}vw)`;  
        });  
  
        document.addEventListener('mouseup', (e) => {  
            if (!isDragging) return;  
            isDragging = false;  
            const moveX = e.clientX - startX;  
              
            if (moveX < -50 && currentPage < pageCount - 1) {  
                currentPage++;  
            } else if (moveX > 50 && currentPage > 0) {  
                currentPage--;  
            }  
  
            slider.style.transform = `translateX(${-currentPage * 100}vw)`;  
        });  
  
        // **移动端触摸滑动**  
        document.addEventListener('touchstart', (e) => {  
            startX = e.touches**[**0**]**.clientX;  
        });  
  
        document.addEventListener('touchmove', (e) => {  
            const moveX = e.touches**[**0**]**.clientX - startX;  
            slider.style.transform = `translateX(${-currentPage * 100 + moveX / 10}vw)`;  
        });  
  
        document.addEventListener('touchend', (e) => {  
            const moveX = e.changedTouches**[**0**]**.clientX - startX;  
              
            if (moveX < -50 && currentPage < pageCount - 1) {  
                currentPage++;  
            } else if (moveX > 50 && currentPage > 0) {  
                currentPage--;  
            }  
  
            slider.style.transform = `translateX(${-currentPage * 100}vw)`;  
        });  
  
        // **复制祝福语功能**  
        function copyBlessing() {  
            const text = document.querySelector('.blessing p').innerText;  
            navigator.clipboard.writeText(text).then(() => {  
                const tip = document.getElementById('tip');  
                tip.style.opacity = 1;  
                setTimeout(() => tip.style.opacity = 0, 2000);  
            });  
        }  
  
        // **背景音乐开关**  
        function toggleBgm() {  
            const bgm = document.getElementById('bgm');  
            if (bgm.muted) {  
                bgm.muted = false;  
                document.querySelector('button**[**onclick="toggleBgm()"**]**').innerText = '**关闭音乐**';  
            } else {  
                bgm.muted = true;  
                document.querySelector('button**[**onclick="toggleBgm()"**]**').innerText = '**开启音乐**';  
            }  
        }  
    </script>  
</body>  
</html>  
