---
title: canvas fingting game (1) 創建遊戲主角與敵人
date: 2023-04-29 14:59:30
tags: canvas
description: '建立專案基礎設定與主角'
---

## 專案建立

建立一個新資料夾，並建立index.html 與 index.js檔案。在 index.html裡，加入canvas元素，並在index.js中選取它設定相關的值。

``` html
  <!-- html -->
  <canvas></canvas>
  <script src="index.js"></script>
```

``` js
// 設定 canvas 的畫布大小，並繪製到畫面上
const canvas = document.querySelector('canvas');
const c = canvas.getContext('2d');

canvas.width = 1024;
canvas.height = 576;

c.fillRect(0, 0, canvas.width, canvas.height);
```

## 創建主角與敵人物件藍圖(class)

``` js
const gravity = .2;
class Sprite {
  constructor({ position, velocity }) {
    this.position = position;
    this.velocity = velocity;
    this.height = 150;
    this.width = 50;
  };

  draw() {
    c.fillStyle = 'red';
    c.fillRect(this.position.x, this.position.y, this.width, this.height);
  };

  update() {
    this.draw();
    this.position.y += this.velocity.y;

    // 當物件的底部碰到畫布的底部時，停止移動。
    if (this.position.y + this.height + this.velocity.y >= canvas.height) {
      this.velocity.y = 0;
    } else {
      this.velocity.y += gravity;
    }
  };
}
```

首先建立一個 class 叫做 sprite ，我們會用這個 sprite class 分別來生成主角與敵人的物件。
在 sprite 裡會傳入一個物件當作參數，物件裡包含 position 和 velocity 物件。

- posotion : 包含x和y值，用來決定物件的位置。
- velocity:  包含x和y值，用來決定物件的移動值。

sprite 裡也包含兩個函式:

- draw: 繪製物件。
- update: 更新物件的值。


## 建立實體

有了 sprite class後，我們可以依據class建立主角和敵人實體。

``` js
const player = new Sprite({
  position: {
    x: 0,
    y: 0,
  },
  velocity: {
    x: 0,
    y: 10,
  },
});

const enemy = new Sprite({
  position: {
    x: 400,
    y: 100,
  },
  velocity: {
    x: 0,
    y: 0,
  },
});
```

## 持續更新畫面

為了持續更新畫面，我們需要一個 loop function，在函式裡我們用到 `requestAnimationFrame` 來持續更新畫面。

``` js
function animate() {
  window.requestAnimationFrame(animate);

  // 重設畫布
  c.fillStyle = 'black';
  c.fillRect(0, 0, canvas.width, canvas.height);

  // 更新並繪製人物
  player.update();
  enemy.update();
}

animate();
```