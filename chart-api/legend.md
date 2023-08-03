---
outline: "deep"
---

# legend

- `type`: `Boolean | Object `

图例的相关配置。

图例默认是关闭的。

### legend.position
- `type`: `String`

图例的位置，可选的值：`"top" | "top-left" | "top-right" | "right" | "right-top" | "right-bottom" | "left" | "left-top" | "left-bottom" | "bottom" | "bottom-left" | "bottom-right" `。

### legend.marker

图例形状的相关配置。

##### legend.marker.symbol

图例 `marker` 的形状，可选的值有：`"circle" | "square" | "line" | "diamond" | "triangle" | "triangle-down" | "hexagon" | "bowtie" | "cross" | "tick" | "plus" | "hyphen"`。

`circle`:

 ![circle](../public/api/legend-marker-symbol/circle.png)

 `square`:

 ![square](../public/api/legend-marker-symbol/square.png)


 `line`:

 ![line](../public/api/legend-marker-symbol/line.png)

  `diamond`:

 ![diamond](../public/api/legend-marker-symbol/diamond.png)

  `triangle`:

 ![triangle](../public/api/legend-marker-symbol/triangle.png)

   `hexagon`:

 ![hexagon](../public/api/legend-marker-symbol/hexagon.png)

`bowtie`:

 ![bowtie](../public/api/legend-marker-symbol/bowtie.png)

`hyphen`:

 ![circle](../public/api/legend-marker-symbol/hyphen.png)

#### legend.marker.spacing

图例项`marker`同后面文本的间距

### legend.itemName

图例项文本配置。

##### legend.itemName.style

图例项文本样式。

```javascript

legend = {
    position: 'top',
    marker: {
        symbol: 'circle',
    },
    // 图例项文本配置
    itemName:{
        style: {
            fill: 'rgba(255, 255, 255, 0.7)'  // 文本颜色
        }
    }
};

```


##### legend.itemName.formatter

- `type`: `function`

图例项文本格式化函数。


### legend.offsetX
-`type`: `number`

图例 (`marker`和文本整体)在 `x` 方向的偏移。

### legend.offsetY
-`type`: `number`

图例(`marker`和文本整体)在 `y` 方向的偏移。