<!DOCTYPE html>
<html>
<head>
    <meta name="viewport" content="width=device-width, initial-scale=1.0, maximum-scale=1.0, user-scalable=no">
    <title>和好</title>
    <style>
        body {
            margin: 0;
            padding: 0;
            background: rgba(0,0,0,0.5);
            height: 100vh;
            display: flex;
            justify-content: center;
            align-items: center;
            touch-action: none;
            -webkit-touch-callout: none;
        }
        .dialog {
            background: #ffe6f2;
            width: 80%;
            padding: 30px;
            border-radius: 20px;
            box-shadow: 0 0 20px rgba(0,0,0,0.2);
            text-align: center;
            position: relative;
        }
        h1 {
            color: #ff69b4;
            margin-bottom: 30px;
            font-size: 24px;
        }
        .btn-group {
            display: flex;
            justify-content: center;
            gap: 15px;
        }
        .btn {
            border: none;
            padding: 15px 30px;
            border-radius: 30px;
            font-size: 18px;
            font-weight: bold;
            cursor: pointer;
            transition: all 0.3s;
            flex-shrink: 0;
        }
        .yes-btn {
            background: #ff69b4;
            color: white;
        }
        .no-btn {
            background: #ff1493;
            color: white;
        }
    </style>
</head>
<body>
    <div class="dialog">
        <h1>要不要跟我和好？🌸</h1>
        <div class="btn-group">
            <button class="btn yes-btn">要！！！</button>
            <button class="btn no-btn">不要</button>
        </div>
    </div>

    <script>
        const yesBtn = document.querySelector('.yes-btn');
        const noBtn = document.querySelector('.no-btn');
        let noScale = 1;
        let offset = 0;

        // 点击"要"按钮
        yesBtn.addEventListener('click', () => {
            noBtn.style.display = 'none';
            yesBtn.textContent = '就知道你会选我～😘';
            yesBtn.style.fontSize = '20px';
            yesBtn.disabled = true;
        });

        // 点击"不要"按钮
        noBtn.addEventListener('click', function() {
            // 放大要按钮
            yesBtn.style.transform = `scale(${1 + offset*0.2})`;
            
            // 缩小和移动不要按钮
            noScale *= 0.8;
            offset += 30;
            this.style.transform = `translateX(${offset}px) scale(${noScale})`;
            
            // 移出屏幕后隐藏
            if (offset > 200) {
                this.style.display = 'none';
                yesBtn.textContent = '不许不要！😭';
                yesBtn.style.fontSize = '24px';
            }
        });

        // 禁止触摸滚动
        document.addEventListener('touchmove', (e) => {
            e.preventDefault();
        }, { passive: false });
    </script>
</body>
</html>
