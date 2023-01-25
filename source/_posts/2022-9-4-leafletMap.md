---
title: leaflet + OpenStreetMap 地圖應用教學
date: 2022-09-04 21:10:18
tags:
---

## 地圖框架與圖資

### 地圖框架

指的是地圖應用的js框架，可以載入地圖資源並標記標示點等功能。

常見的如 [leaflet](https://leafletjs.com/index.html)。

### 圖資

指的是地圖資源的提供者，常見的有

- Google Map (要收費)

- [OpenStreetMap](https://www.openstreetmap.org/#map=14/25.0066/121.4954) (免費開源)

本文會講解如何使用 leaflet + OpenStreetMap 來開發地圖應用程式。

## 載入地圖

首先在專案裡用cdn的方式引入 leaflet 的 css 和 js

``` html
 <link rel="stylesheet" href="https://unpkg.com/leaflet@1.8.0/dist/leaflet.css"
   integrity="sha512-hoalWLoI8r4UszCkZ5kL8vayOGVae1oxXe/2A4AO6J9+580uKHDO3JdHb7NzwwzK5xr/Fs0W40kiNHxM9vyTtQ=="
   crossorigin=""/>
```

``` html
<!-- Make sure you put this AFTER Leaflet's CSS -->
 <script src="https://unpkg.com/leaflet@1.8.0/dist/leaflet.js"
   integrity="sha512-BB3hKbKWOc9Ez/TAwyWxNXeoV9c1v6FIeYiBieIWkpLjauysF18NzgR1MBNBXf8/KABdlkX68nAhlwcDFLGPCQ=="
   crossorigin=""></script>
```

準備一個放置地圖的元素，並設置高度

``` html
<div id="map"></div>
```

``` css
#map { height: 180px; }
```

在 js 裡載入框架

``` js
const map = L.map('map').setView([51.505, -0.09], 13);
```

- L: 框架的縮寫

- map('map'): 指定放地圖的元素

- setView: 第一個參數指定地圖顯示的經緯度，第二參數表示地圖縮放的級距。


再來要載入圖資

``` js
L.tileLayer('https://tile.openstreetmap.org/{z}/{x}/{y}.png', {
    maxZoom: 19,
    attribution: '© OpenStreetMap'
}).addTo(map);
```

tileLayer的第一個參數指定使用圖資的來源，第二個參數是物件，maxZoom代表最大縮放級距，attribution則標示圖資所有權。

最後用 addTo(map)，將圖資載入map變數裡。

到這邊已經成功將地圖服務載入囉，[範例程式碼](https://codepen.io/liao/pen/gOpOgzg)。

## 地圖加入標示

圖資其實是一層一層的圖層疊起來呈現的

![](https://fs.npstatic.com/userfiles/4774964/image/google-maps-layers-w810h462.jpg)

在最底層的地圖圖上，我們可以在加上標示的圖層。

``` js
const marker = L.marker([51.5, -0.09]).addTo(map);
```

使用marker方法加入標示，第一個參數帶入標示的經緯度，在加入map變數裡。

要在marker再加入標示說明，可用popup語法。

``` js
marker.bindPopup("<b>Hello world!</b><br>I am a popup.").openPopup();
```

- bindPopup: 加入標示的說明文字的html。
- openPopup: 讓標示預設是打開的。

要一次加入多個 marker ，可以跑迴圈加入

``` js
var data = [
  {'name':'軟體園區',lat:22.604799,lng:120.2976256},
  {'name':'ikea',lat:22.6066728,lng:120.3015429}
]
for(var i =0;data.length>i;i++){
  L.marker([data[i].lat,data[i].lng], {icon: greenIcon}).addTo(map)
    .bindPopup('<h1>'+ data[i].name +'</h1>')
}
```

要更改marker的icon的話，也有提供方法使用，主要將 iconUrl 替換成自己的icon圖片:

``` js
var myIcon = L.icon({
    iconUrl: 'my-icon.png',
    iconSize: [38, 95],
    iconAnchor: [22, 94],
    popupAnchor: [-3, -76],
    shadowUrl: 'my-icon-shadow.png',
    shadowSize: [68, 95],
    shadowAnchor: [22, 94]
});

L.marker([50.505, 30.57], {icon: myIcon}).addTo(map);
```

## 效能處理

當今天資料很多時，為了避免依次顯示太多標示在地圖上，我們可以使用插件 [Leaflet.markercluster](https://github.com/Leaflet/Leaflet.markercluster)。

這個插件可以依據縮放的級距顯示相對數量標示，避免顯示太多效能變差。

使用方法也很簡單，在原有的tileLayer圖層上再加上一層MarkerCluster圖層。

``` js
var markers = new L.MarkerClusterGroup().addTo(map);;
```

[範例code](https://codepen.io/tim-chou/pen/mdLyObY)








