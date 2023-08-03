---
outline: "deep"
---

# axis

坐标轴的相关配置：坐标轴标题(`title`)、坐标轴轴线（`line`）、坐标轴刻度线（`tickLine`）、坐标轴刻度值（`label`）、网格线（`grid`）、缩略轴（`slider`）、度量（`scale`）、坐标轴的文本标记（`unit`）。

![An image](../public/axis.png)

坐标轴默认显示，可以通过设置`false`将坐标轴关闭。

统一关闭`x`、`y`轴：

```javascript
axis: false;
```

可通过配置单独关闭`x`或者`y`：

```javascript
axis: {
    xAxis: false,
    yAxis: false
}
```

#### axis.title

- `type`: `Boolean | Object`

坐标轴标题。

坐标轴标题默认不显示，可通过配置设置坐标轴标题：

```javascript
//开启x坐标轴显示
axis = {
  xAxis: {
    title: true,
  },
};
```

自定义坐标轴标题内容或者样式：

```javascript
// 配置x坐标轴标题
axis = {
  xAxis: {
    title: {
      // 标题文本
      text: "我是坐标轴的标题文本内容",
      // 标题的位置
      position: "left",
      // ......
    },
  },
};
```

#### axis.line

- `type`: `Boolean | ShapeAttrs `
  坐标轴轴线。

坐标轴轴线默认显示，可通过设置`false`关闭坐标轴轴线的显示。

```javascript
axis = {
  xAxis: {
    line: false, // 关闭坐标轴线
  },
};
```

详细配置坐标轴的轴线样式：

```javascript
axis = {
  xAxis: {
    line: {
      // 设置x轴线的样式
      style: {
        stroke: "#cccccc30",
      },
    },
  },
};
```

#### axis.tickLine

- `type`: `Boolean | Object`

坐标轴刻度线。

坐标轴刻度线默认显示，可通过设置`false`关闭坐标轴刻度线：

```javascript
// 关闭x轴坐标轴刻度线
axis = {
  xAxis: {
    tickLine: false,
  },
};
```

配置坐标轴刻度线的样式：

```javascript
axis =  {
  	xAxis: {
        tickLine: {
            length： 10, // 刻度线长度
            // ...
        },
    }
}

```

#### axis.label

- `type`: `Boolean | Object `

坐标轴刻度值。

坐标轴刻度值默认显示，可通过设置`false`关闭坐标轴刻度值的文本显示：

```javascript
// 关闭x轴坐标轴刻度线
axis = {
  xAxis: {
    label: false,
  },
};
// 配置x轴刻度值文本
axis = {
  xAxis: {
    label: {
      // 刻度值文本旋转角度
      rotate: 30,
      // 刻度值文本格式化
      formatter: (text, item, index) => any,
      // ...
    },
  },
};
// 配置y轴刻度值文本
axis = {
  yAxis: {
    label: {
      // 刻度值文本的样式
      style: {
        fill: "#A2A9B4", // 文字颜色
        fontSize: 11, // 字体大小
      },
      offsetX: -3, // 刻度值在X轴方向上的偏移量
      offsetY: -3, // 刻度值在Y轴方向上的偏移量
    },
  },
};
```

##### axis.label.formatter

```javascript
/*
 * text: String   表示每一项的数据
 * item: DataItem 整个chart图表的数据
 * index: Number  当前项数据的下标
 */
formatter: (text, item, index) => {};
```

#### axis.grid

- `type`: `Boolean | Object `

坐标轴网格线。

坐标轴网格线默认显示，可通过设置`false`关闭坐标轴刻度值的文本显示：

```javascript
// 关闭x轴坐标轴刻度线
axis = {
  xAxis: {
    grid: false,
  },
};
```

详细配置 `y` 轴网格线：

```javascript
axis = {
    yAxis: {
        grid: {
            line: {
                // 网格线的样式
                style: {
                    // 设置线的虚线样式，可以指定一个数组。一组描述交替绘制线段和间距（坐标空间单位）长度的数字。
                    lineDash: [4, 2],
                    // 描边色、渐变或纹理，默认值为空；
                    stroke: 'red',
                    // 设置图形和图片透明度的属性，默认值是 1。 数值的范围从 0.0 （完全透明）到 1.0 （完全不透明）。
                    opacity: 0.5,
                },
            },
        },
    }
},
```

#### axis.slider

- `type`: `Boolean | Object`

坐标轴的缩略轴。

坐标轴缩略轴默认不显示，可通过设置`true`或者`{}`开启缩略轴：

```javascript
// 开启缩略轴
axis = {
  slider: true | {},
};
```

配置缩略轴高度：

```javascript
axis = {
  slider: {
    height: 20, //组件高度
  },
};
```

##### axis.slider.padding

缩略轴图表内边距.
- `type`: `number[]`

```javascript
axis = {
  slider: {
    padding: [5,5,5,5],
  },
};
```


##### axis.slider.backgroundStyle

滑块背景样式

- `type`: `ShapeAttrs`


##### axis.slider.foregroundStyle

滑块前景样式

- `type`: `ShapeAttrs`

##### axis.slider.foregroundStyle

handlerStyle

- `type`: `ShapeAttrs`

滑块背景趋势图配置。`trendCfg` 配置如下：

| 参数名          |   类型   | 是否必选 | 默认值 | 描述   |
| :-------------- | :------: | :------: | :----: | :----- |
| data            | number[] |    否    |   -    | 趋势图数据，组件会默认根据图表数据填充，无需配置 |
| smooth          | boolean  |    否    | false  | 趋势图曲线是否圆滑                               |
| isArea          | boolean  |    否    | false  | 趋势图是否使用面积图                             |
| backgroundStyle | 样式属性 |    否    |   -    | 背景样式                                         |
| lineStyle       | 样式属性 |          |   否   | -                                                | 折线图样式 |
| areaStyle       | 样式属性 |          |   否   | -                                                | 面积图样式 |

##### axis.slider.messData
当图表数据量过大时,开启大量数据缩略轴.


- `type`: `Boolean`|`(data,areaData,extraction)=>object[]`
  
* 传入true开启大量数据缩略轴,使用默认数据提取方法.
* 传入回调函数可以自定义数据提取函数.


``` Vue
<template>
    <Line :data="data" :axis="axis"></Line>
</template>
<script>
const axis = {
    xAxis:{
        slider:{
            // 开启大量数据缩略轴
            // data全部数据
            // areaData滑块选取的数据区间(0-1之前) 例:[0,1]
            // extraction默认提取的数据数量
            massData:(data,areaData,extraction=1000)=> data
        }
    }
}
</script>
 ```

#### axis.unit

- `type`: `Object `

坐标轴单位文本配置，默认不配置则不显示，可自定义在 `x` 轴或 `y` 轴显示。

```javascript
// 配置y轴单位文本
axis = {
  yAxis: {
    unit: {
      content: "吨", // 显示的文本内容
      style: {
        fill: "#bbb", // 文本颜色
      },
      position: ["-3%", "-6%"], // 文本位置
    },
  },
};
```

#### axis.scale

度量（Scale）用于定义数据的类型和展示方式，可选择定义 x 轴的数据或者 y 轴的数据。

##### axis.scale.nice

- `type`: `boolean `

自动调整坐标轴上显示数据的 min、max。

```javascript
// 自动调整y轴数据显示的min、max
axis = {
  yAxis: {
    scale: {
      nice: true,
    },
  },
};
```

##### axis.scale.tickCount

- `type`: `number `

`tick` 个数。

```javascript
// 调整y轴tick个数为5
axis = {
  yAxis: {
    scale: {
      tickCount: 5,
    },
  },
};
```

##### axis.scale.tickInterval

- `type`: `number `

`tick` 间隔，只对分类型和时间型适用，优先级高于 `tickCount`。

```javascript
// 自动调整y轴数据的间隔
axis = {
  yAxis: {
    scale: {
      tickInterval: 5,
    },
  },
};
```

##### axis.scale.range

- `type`: `[number, number] `
- `default`: `[0, 1]`

输出域、值域，表示在绘图范围内可用于绘制的范围。

配置前：
![An image](/before-scale.png)

配置后：

```javascript
// 调整x轴绘图范围从0.03开始到0.98结束，
axis = {
  xAxis: {
    scale: {
      range: [0.03, 0.98],
    },
  },
};
```

![An image](/after-scale.png)
