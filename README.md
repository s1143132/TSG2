# 賽車遊戲 (Racing Game)

一個使用 HTML5 Canvas 製作的賽車遊戲。

## 遊戲特色

- **操作方式**：使用方向鍵或 WASD 控制
- **遊戲目標**：躲避障礙物，獲得高分
- **視覺效果**：霓虹風格賽車遊戲

## 控制說明

| 按鍵 | 功能 |
|------|------|
| ← → / A D | 左右移動 |
| ↑ ↓ / W S | 加速減速 |

## 遊戲機制

1. **分數計算**：速度越快，分數越高
2. **障礙物**：隨機生成不同顏色的障礙物
3. **速度系統**：最高速度為 15

## 程式碼結構

### HTML 部分

```html
<!DOCTYPE html>
<html lang="zh-TW">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>賽車遊戲</title>
    <!-- ... -->
</head>
<body>
    <h1>🏎️ 賽車遊戲</h1>
    <div id="gameContainer">
        <canvas id="gameCanvas" width="400" height="600"></canvas>
        <!-- UI 元素 -->
    </div>
</body>
</html>
```

### CSS 樣式

- 霓虹綠色主題 (`#00ff88`)
- 漸變背景效果
- 發光按鈕與邊框

### JavaScript 功能

#### 初始化
```javascript
const player = {
    x: 175,
    y: 480,
    width: 50,
    height: 80,
    color: '#ff6b6b'
};
```

#### 遊戲循環

```javascript
function gameLoop() {
    if (!gameRunning) return;
    ctx.clearRect(0, 0, canvas.width, canvas.height);
    drawRoad();
    drawObstacles();
    drawPlayer();
    update();
    requestAnimationFrame(gameLoop);
}
```

#### 碰撞檢測

```javascript
if (player.x < obs.x + obs.width &&
    player.x + player.width > obs.x &&
    player.y < obs.y + obs.height &&
    player.y + player.height > obs.y) {
    gameOver();
}
```

## 檔案資訊

- **檔案類型**：HTML5 遊戲
- **依賴**：無 (原生 JavaScript)
- **瀏覽器支援**：所有現代瀏覽器