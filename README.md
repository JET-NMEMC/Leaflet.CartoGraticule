# Leaflet.CartoGraticule

Leaflet.CartoGraticule 是一个轻量级的 Leaflet 插件，旨在为地图添加“制图模式”。开启该模式后，插件会自动调整地图容器的大小，并在地图周围绘制经纬度网格、刻度和标签，非常适合用于生成标准的地图截图或打印输出。

## 特性 (Features)

*   **一键切换**: 提供一个简单的按钮，用于在普通地图模式和制图模式之间快速切换。
*   **自动布局**: 进入制图模式时，自动调整地图容器的边距，为坐标标签留出空间。
*   **高度可定制**: 支持自定义字体大小、刻度方向（向内/向外）等。
*   **智能网格**: 根据当前的缩放级别和地图范围，自动计算合适的经纬度网格间隔（支持度、分、秒格式）。
*   **无缝集成**: 作为一个标准的 Leaflet Control 存在，易于集成到任何 Leaflet 项目中。

## 安装与使用 (Usage)

1.  **引入文件**

    在你的 HTML 文件中引入 `Leaflet.CartoGraticule.css` 和 `Leaflet.CartoGraticule.js`：

    ```html
    <!-- 引入 Leaflet (必须) -->
    <link rel="stylesheet" href="https://unpkg.com/leaflet/dist/leaflet.css" />
    <script src="https://unpkg.com/leaflet/dist/leaflet.js"></script>

    <!-- 引入 Leaflet.CartoGraticule -->
    <link rel="stylesheet" href="path/to/Leaflet.CartoGraticule.css">
    <script src="path/to/Leaflet.CartoGraticule.js"></script>
    ```

2.  **初始化插件**

    在地图初始化之后，添加 `L.control.cartoGraticule` 控件：

    ```javascript
    var map = L.map('map').setView([36.0671, 120.3826], 13);

    // 添加底图...
    L.tileLayer('...').addTo(map);

    // 添加 CartoGraticule 插件
    L.control.cartoGraticule({
        position: 'topleft',        // 控件按钮位置
        fontSize: 14,               // 坐标标签字体大小
        tickDirection: 'out',       // 刻度方向: 'in' (向内) 或 'out' (向外)
        showZoomControl: true       // 制图模式下是否保留缩放控件
    }).addTo(map);
    ```

## 配置选项 (Options)

| 选项名 | 类型 | 默认值 | 描述 |
| :--- | :--- | :--- | :--- |
| `position` | String | `'topleft'` | 控件按钮在地图上的位置 (e.g., `'topleft'`, `'topright'`)。 |
| `mapStyle` | Object | `{ top: '40px', bottom: '40px', left: '50px', right: '50px' }` | 制图模式下地图容器的边距设置，用于留出绘制坐标的空间。 |
| `fontSize` | Number | `14` | 坐标标签的字体大小 (像素)。 |
| `tickDirection` | String | `'out'` | 刻度线的方向。可选值: `'in'` (指向地图内部), `'out'` (指向地图外部)。 |
| `showZoomControl`| Boolean | `true` | 进入制图模式时，是否显示 Leaflet 默认的缩放控件。 |
| `targetN` | Object | `{ lng: 3, lat: 2 }` | 控制经纬度网格密度的因子。数值越大，网格越密。 |

## 示例 (Example)

查看 `index.html` 获取完整的运行示例。

```javascript
L.control.cartoGraticule({
    position: 'topleft',
    fontSize: 15,
    tickDirection: 'out',
    showZoomControl: false,
    // 自定义经纬度网格密度
    targetN: {
        lng: 3, // 期望的经度标签数量（近似值）
        lat: 2  // 期望的纬度标签数量（近似值）
    },
    // 自定义制图模式边距
    mapStyle: {
        top: '40px',
        bottom: '40px',
        left: '50px',
        right: '50px'
    }
}).addTo(map);
```

## License

MIT
