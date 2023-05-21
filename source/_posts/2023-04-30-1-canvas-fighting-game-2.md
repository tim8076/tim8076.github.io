---
title: canvas fingting game (2) 移動角色
date: 2023-04-30 11:53:29
tags: canvas
description: '建立事件監聽來移動角色'
---

[原始碼參考](https://github.com/tim8076/canvas-fighting-game/tree/2-move-character)

## 建立鍵盤事件監聽

為了移動角色，需要監聽鍵盤的 keydown 事件，當玩家按下鍵盤後移動角色；並同時監聽 keyup事件，當玩家放開鍵盤後停止角色移動。

另外我們會另外建立一個 keys 的物件，用來記錄按鍵是否為按下的狀態，再來利用這些狀態，在animate函式中操作人物的移動。因為直接在 window.addEventListener中操作角色移動會不夠靈敏，在animate函式操作更為靈活。

``` js
const keys = {
  a: {
    pressd: false,
  },
  d: {
    pressd: false,
  },
  w: {
    pressd: false,
  },
  ArrowRight: {
    pressd: false,
  },
  ArrowLeft: {
    pressd: false,
  }
}
```

``` js
window.addEventListener('keydown', (e) => {
  switch(e.key) {
    case 'd':
      keys.d.pressd = true;
      player.lastKey = 'd';
      break;
    case 'a':
      keys.a.pressd = true;
      player.lastKey = 'a';
      break;
    case 'w':
      player.velocity.y = -20;
      break;
    case 'ArrowRight':
      keys.ArrowRight.pressd = true;
      enemy.lastKey = 'ArrowRight';
      break;
    case 'ArrowLeft':
      keys.ArrowLeft.pressd = true;
      enemy.lastKey = 'ArrowLeft';
      break;
    case 'ArrowUp':
      enemy.velocity.y = -20;
      break;
  }
});

window.addEventListener('keyup', (e) => {
  switch (e.key) {
    case 'd':
      keys.d.pressd = false;
      break;
    case 'a':
      keys.a.pressd = false;
      break;
  }
  
  // enemy keys
  switch (e.key) {
    case 'ArrowRight':
      keys.ArrowRight.pressd = false;
      break;
    case 'ArrowLeft':
      keys.ArrowLeft.pressd = false;
      break;
  }
})
```

## 移動角色

有了 keys 的物件，用來記錄按鍵是否為按下的狀態，可以利用這些狀態，在animate函式中操作人物的移動。

``` js

function animate() {
  window.requestAnimationFrame(animate);
  c.fillStyle = 'black';
  c.fillRect(0, 0, canvas.width, canvas.height);
  player.update();
  enemy.update();
  
  // 每次移動前都先停止角色，防止角色無限移動
  player.velocity.x = 0;
  enemy.velocity.x = 0;
  
  // player movement
  if (keys.a.pressd && player.lastKey === 'a') {
    player.velocity.x = -5;
  } else if (keys.d.pressd && player.lastKey === 'd') {
    player.velocity.x = 5;
  }

  // enemy movement
  if (keys.ArrowLeft.pressd && enemy.lastKey === 'ArrowLeft') {
    enemy.velocity.x = -5;
  } else if (keys.ArrowRight.pressd && enemy.lastKey === 'ArrowRight') {
    enemy.velocity.x = 5;
  }
}
```