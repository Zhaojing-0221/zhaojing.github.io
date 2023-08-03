---
outline: "deep"
---

# 面积图参数

### chartBasic(非必传属性)

`chartBasic`表示图表对象的一些基础配置，比如图表宽（`width`）高（`height`）、内边距(`padding`)等。
如果不配置该属性，则图表默认跟随父盒子宽高，自动撑开。

##### chartBasic.width

- `type`: `Number `
- `default`: `undefined`

图表的宽度。

##### chartBasic.heigth

- `type`: `Number `
- `default`: `'undefined'`

图表的高度。

> `width`和`height`可以省略，图表的宽高默认自适应父元素的宽高。

##### chartBasic.padding

- `type`: `'auto' | Number | Number[]`
- `default`: `'auto'`

图表的内边距。

### data(必传)

- `type`: `Array`
- `default`: `[]`

图表的数据。

目前只支持一种数据结构：

```javascript
const data = [
  { year: "1991", value: 15468 },
  { year: "1992", value: 16100 },
  { year: "1993", value: 15900 },
  { year: "1994", value: 17409 },
  { year: "1995", value: 17000 },
];
或者：
const data = [
  { x: 1, y: 332, group: "综采一队" },
  { x: 2, y: 202, group: "综采一队" },
  { x: 3, y: 322, group: "综采一队" },
  { x: 1, y: 152, group: "综采二队" },
  { x: 2, y: 100, group: "综采二队" },
  { x: 3, y: 240, group: "综采二队" },
  { x: 1, y: 318, group: "综采三队" },
  { x: 2, y: 108, group: "综采三队" },
  { x: 3, y: 318, group: "综采三队" },
];
```

### xField

- `type`: `String`
- `default`: `'x'`
- `required`: `false`

`x`轴字段。

以哪个字段作为`x`轴的数据(默认以`data`数据中的`x`字段)：

```javascript
xField = "genre"; // 以"genre"字段的值作为x轴的数据
```

### yField

- `type`: `String`
- `default`: `'y'`
- `required`: `false`

`y`轴字段。

以哪个字段作为`y`轴的数据(默认以`data`数据中的`y`字段)：

```javascript
yField = "sold"; //以"sold"字段的值作为y轴的数据
```

### seriesField

- `type`: `String`
- `default`: `'undefined'`
- `required`: `False`

多组图形的分组字段。

当有多组图形：多条面积图或多条折线图，通过这个数据字段对数据进行分组：

```javascript
const data = [
    { genre: 'Sports', sold: 275, age: 10, team: 'team1' },
    { genre: 'Strategy', sold: 115, age: 20, team: 'team1' },
    { genre: 'Sports', sold: 120, age: 20, team: 'team2' },
    { genre: 'Strategy', sold: 350, age: 10, team: 'team2' },
    { genre: 'Sports', sold: 150, , age: 10, team: 'team3' },
    { genre: 'Strategy', sold: 150, , age: 10, team: 'team3' },
];
seriesField = 'team'
```

以上的`data`和`seriesField`配置最终会将数据分为三组，展示三条线段：

```javascript
const data1 = [
    { genre: 'Sports', sold: 275, age: 10, team: 'team1' },
    { genre: 'Strategy', sold: 115, age: 20, team: 'team1' },
];

const data2 = [
    { genre: 'Sports', sold: 120, age: 20, team: 'team2' },
    { genre: 'Strategy', sold: 350, age: 10, team: 'team2' },
]

const data3 = {
    { genre: 'Sports', sold: 150, , age: 10, team: 'team3' },
    { genre: 'Strategy', sold: 150, , age: 10, team: 'team3' },
}
```

### adjust

- `type`: `String`
- `required`: `False`

设置数据调整方式，如面积图可使用此属性来设置堆叠面积图。

可选值：`'stack' | 'dodge' | 'jitter' | 'symmetric'`

`'stack'`:层叠，将同一个分类的数据值累加起来。以层叠的柱状图为例，x 轴方向的同一个分类下面的数据，按照顺序，将 y 轴对应的值累加，最终将数据调整的不再重叠。

`'dodge'`:分组散开，将同一个分类的数据进行分组在一个范围内均匀分布，例如分组柱状图。

`'jitter'`:扰动散开，将数据的位置轻微的调整，使得映射后的图形位置不再重叠。仅适用于分类数据，将分类数据转换成索引值，在索引值 [ -0.5 ,0.5 ] 的范围内进行随机分布。

`'symmetric'`:数据对称，使得生成的图形居中对齐，例如河流图、漏斗图。

```javascript
adjust = "stack"; // 使面积图变成堆叠面积图
```

![An image](../public/stack-area.png)

### tooltip

- `type`: `Boolean | Object`
- `default`: `true`

提示信息，其中包括提示的标题、内容、样式、辅助线等

![An image](../public/tooltip.png)

`tooltip`默认是打开的，内容样式为`g2`图表默认的内容和样式。

关闭`tooltip`的显示，将该项置为`false`即可：

```javascript
tooltip: false;
```

#### tooltip.crosshairs

- `type`: `Boolean | Object`,
- `default`: `true`

`tooltip`的辅助线默认是开启的，样式为`g2`图表提供的默认样式。如果需要关闭辅助线，可以设置`crosshairs`为`false`,或者直接配置某条坐标轴上的`crosshairs`相关属性。

```javascript
tooltip = {
  crosshairs: false,
};

tooltip = {
  crosshairs: {
    type: "x", // 设置x坐标轴上的辅助线属性
    line: {
      // 设置线条样式
      style: {
        stroke: "l(90) 0:rgba(54, 110, 174,0.1)  1:rgba(129, 170, 212,0.8)", // 描边色
        lineWidth: 1.5, // 线条宽度
        shadowBlur: 20, // 模糊程度
        shadowColor: "rgb(238, 244, 255)", // 阴影颜色
      },
    },
  },
};
```

如果需要配置辅助线的样式，传入相关的样式配置即可。

```javascript
tooltip = {
  crosshairs: {
    // x: x轴上的辅助线 y:y轴的辅助线 default: x(垂直辅助线)
    type: "x | y | xy",
    line: {
      // 线条样式配置
      style: {
        stroke: "l(90) 0:rgba(54, 110, 174,0.1)  1:rgba(129, 170, 212,0.8)", // 填充色
        lineWidth: 1.5, // 线条宽度
        shadowBlur: 20, //模糊程度
        shadowColor: "rgb(238, 244, 255)", // 阴影颜色
      },
    },
  },
};
```

#### tooltip.marker

- `type`: `Boolean | Object`

辅助线和图形交汇处的标记点,默认开启。

![An image](../public/tooltip-marker.png)

配置`marker`的样式：

```javascript
tooltip = {
  marker: {
    fill: "#fff", // 填充色
    stroke: "#397DF9", // 描边色
  },
};
```

#### tooltip.domStyles

- `type`: ` Object`

`TooltipDomStyles` 是以 dom 节点的 class 为 key 的对象，`CSSProperties` 为 value 的对象,可以通过该属性修改 `tooltip` 提示框样式.

dom 结构以及修改样式示例如下：

```javascript
// dom结构名称
interface TooltipDomStyles {
  "g2-tooltip"?: CSSProperties;
  "g2-tooltip-title"?: CSSProperties;
  "g2-tooltip-list"?: CSSProperties;
  "g2-tooltip-list-item"?: CSSProperties;
  "g2-tooltip-marker"?: CSSProperties;
  "g2-tooltip-value"?: CSSProperties;
  "g2-tooltip-name"?: CSSProperties;
}

// 修改样式示例
tooltip = {
  domStyles: {
        'g2-tooltip': { // 提示框大盒子
            backgroundColor: 'rgba(159, 177, 245, 0.5)',
            color: '#fff',
            boxShadow: '0,0,0',
            borderRadius: '6px',
            padding: '18px 30px 16px 30px',
            textAlign: 'left',
        },
        'g2-tooltip-marker': { // 文本前图标
            display: 'none',
        },

        'g2-tooltip-name': {  // 文本
            color: 'rgba(255, 255, 255, 0.7)',
            fontSize: '8px',
        },
        'g2-tooltip-value': { // 数据
            color: 'rgba(255, 255, 255, 0.9)',
            fontSize: '10px',
        },
        'g2-tooltip-list': {
            textAlign: 'left',
        },
        'g2-tooltip-list-item': {
            margin: '10px 0'
        },
        'g2-tooltip-title': {
            margin: '6px 0'
        }
}
}；
```

#### tooltip.itemTpl

- `type`: ` string`

用于指定图例容器的模板，自定义模板时必须包含各个 dom 节点的 class,可通过该属性修改`tooltip`默认显示内容。

例如`tooltip` 自带冒号，但通过如下代码可去除自带的冒号。

```javascript
tooltip = {
  itemTpl: `
             <li class="g2-tooltip-list-item">
                <span class="g2-tooltip-marker"></span>
                <span class="g2-tooltip-name">{name}</span><span class="g2-tooltip-value">{value} </span>
            </li>`,
};
```

#### tooltip.customItems

-`type`：`(items) => any`

在渲染`tooltip` 之前，对 G2 的 tooltip items 列表项目进行用户自定义处理，默认不做任何处理。可以用来对 `tooltip` 列表进行过滤、排序、格式化等操作,

```javascript
tooltip = {
  customItems: (items) => {
    items.forEach((item) => {
      item.value = `${item.data.y} 吨`; // 为每个y轴的数据添加“吨”后缀单位
      item.name = `${item.data.t}`; // 使提示框内左侧标题内容变为data中的t字段内容
    });
    return items;
  },
};
```

![An image](../public/tooltip-custom.png)

### axis

坐标轴的相关配置：坐标轴标题、坐标轴轴线、坐标轴刻度线、坐标轴刻度值、网格线、缩略轴、度量、坐标轴的文本标记。

![An image](/axis.png)

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
// 配置y轴刻度值样式
axis = {
  yAxis: {
    label: {
      style: {
        fill: "#A2A9B4", // 文字颜色
        fontSize: 11, // 字体大小
      },
      offsetY: -3,
    },
  },
};
// 配置x轴刻度值样式以及文本格式化
axis = {
  xAxis: {
    label: {
      // 刻度值文本旋转角度
      rotate: 30,
      // 刻度值文本格式化
      formatter: (text: string, item: ListItem, index: number) => any,
      // ...
    },
  },
};
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

详细配置 y 轴网格线：

```javascript
axis = {
  yAxis: {
    grid: {
      line: {
           style: {
                lineDash: [4, 2], // 设置线的虚线样式，可以指定一个数组。一组描述交替绘制线段和间距（坐标空间单位）长度的数字。
                stroke: 'red', // 描边色、渐变或纹理，默认值为空；
                opacity: 0.5, // 设置图形和图片透明度的属性，默认值是 1。 数值的范围从 0.0 （完全透明）到 1.0 （完全不透明）。
            },
        },
      },
    },
  },

```

#### axis.unit

- `type`: `Object `

坐标轴单位文字配置，默认不配置则不显示，可自定义在 x 轴或 y 轴显示

```javascript
// 配置y轴单位文字
axis = {
  yAxis: {
    unit: {
      content: "吨", // 显示的文本
      style: {
        fill: "#bbb", // 填充色
      },
      position: ["-3%", "-6%"], // 显示位置
    },
  },
};
```

### legend

- `type`: `Boolean | Object `

图例的相关配置。

图例默认是显示的，可通过传入`false`关闭图例：

```javascript
legend: false;
```

### line

- `type`: `Object`

线条相关的内容：线条是否平滑、线条上的点(主要在折线图上使用)

#### line.smooth

- `type`: `Boolean`

线条是否平滑，默认不平滑，可通过传入`true`设置线段为平滑曲线。

```javascript
line: {
    smooth: true, // 平滑
}
```

线条为平滑时效果如下图。
![An image](../public/line-smooth.png)

### color

- `type`: `string | Array;`

线条颜色，可使用单个字符串或者数组以及回调形式。
多组颜色建议使用数组形式，单个颜色使用字符串即可。

```javascript
color = ["#934EEC", "#1E91F5", "#8DB3DF"];
color = "#FFF";
```

### fillColor

- `type`: `string | Array;`

  填充颜色，主要为面积图使用。
  多组颜色建议使用数组形式，单个颜色使用字符串即可。

```javascript
const fillColor = [
  "l(270) 0:#26324B30 0.3:#26314A 1:#934EEC",
  "l(270) 0:#26324B 0.3:#26314A 1:#1E91F5",
  "l(270) 0:#26324B 0.2:#26314A 1:#8DB3DF",
];

const fillColor = "#FFF";
```

### annotation

图形标注，Annotation，作为 G2 图表的辅助元素，主要用于在图表上标识额外的标记注解。

#### annotation.regionFilter

- `type`: `Array[Object]`

  区域着色，将图表中位于矩形选区中的图形元素提取出来，重新着色。
  下图中 `regionFilter `为`贸易赤字`和`贸易盈余`两个区域。

  示例图如下:
  ![An image](/regionFliter.png)

```javascript
const annotation = {
  regionFilter: [
    {
      // 第一组区域
      top: true, // 指定 annotation 是否绘制在 canvas 最上层，默认为 false, 即绘制在最下层,这里改为绘制在最上层
      start: [1700, "min"], // 从1700年最低点开始
      end: [1753, "max"], // 在1753年最高点结束
      color: "#F5222D", // 重新着色的颜色
      apply: ["area"], // 设定 regionFilter 只对特定 geometry 类型起作用，如此处只对面积图起作用
    },
    {
      // 第二组区域
      top: true, // 指定 annotation 是否绘制在 canvas 最上层，默认为 false, 即绘制在最下层,这里改为绘制在最上层
      start: [1753, "min"], // 从1753年最低点开始
      end: [1780, "max"], // 在1780年最高点结束
      color: "#FAAD14", // 重新着色的颜色
      apply: ["area"], // 设定 regionFilter 只对特定 geometry 类型起作用，如此处只对面积图起作用
    },
  ],
};
```

#### annotation.line

- `type`: `Array[Object]`

  辅助线（可带文本），例如表示平均值或者预期分布的直线，
  可以自定义样式。

注意：开始位置与结束位置的值需与 x 轴 或 y 轴数值对应，否则无法渲染到正确位置。
![An image](/annotation-line.png)

```javascript
const annotation = {
  line: [
    {
      start: ["4-2", 0], // 从"4-2"数据最低点开始绘制
      end: ["4-2", "max"], // 在"4-2"数据最高点结束
      style: {
        // 可根据需要自定义样式
        lineDash: [8, 4, 4, 2], // 线条虚线设置
        stroke: "#9E98DC", // 描边色
        lineWidth: 1.5, // 线条宽度
      },
    },
    {
      start: ["4-5", 0], // 从"4-5"数据最低点开始绘制
      end: ["4-5", "max"], // 在"4-5"数据最高点结束
      style: {
        lineDash: [8, 4, 4, 2], // 线条虚线设置
        stroke: "#9E98DC", // 描边色
        lineWidth: 1.5, // 线条宽度
      },
    },
    {
      start: ["4-7", 0], // 从"4-7"数据最低点开始绘制
      end: ["4-7", "max"], // 在"4-7"数据最高点结束
      style: {
        lineDash: [8, 4, 4, 2], // 线条虚线设置
        stroke: "#9E98DC", // 描边色
        lineWidth: 1.5, // 线条宽度
      },
    },
  ],
};
```

#### annotation.image

- `type`: `Array[Object]`

  辅助图片，在图表上添加辅助图片，可以添加多个图片标注。

  注意：开始位置与结束位置的值需与 x 轴 或 y 轴数值对应，否则无法渲染到正确位置。
  ![An image](../public/image-annotation.png)

  ```javascript
  const annotation = {
    image: [
      {
        src: chartArrow, // 图片需要先引入，如import方式等
        start: ["00:00", "min"], // 从"00:00"开始
        end: ["00:00", "min"], // 在"00:00"结束
        offsetX: -6, // x方向偏离值
        offsetY: -10, // y方向偏离值
      },
      {
        src: chartArrow, // 图片需要先引入，如import方式等
        start: ["08:00", "min"], // 从"08:00"开始
        end: ["08:00", "min"], // 从"08:00"开始
        offsetX: -6, // x方向偏离值
        offsetY: -10, // y方向偏离值
      },
    ],
  };

  const dataPic = [
    { x: "00:00", y: 332, group: "综采一队" },
    { x: "04:00", y: 202, group: "综采一队" },
    { x: "08:00", y: 322, group: "综采一队" },
    { x: "12:00", y: 132, group: "综采一队" },
    { x: "16:00", y: 152, group: "综采一队" },
    { x: "20:00", y: 100, group: "综采一队" },
    { x: "22:00", y: 240, group: "综采一队" },
    { x: "24:00", y: 170, group: "综采一队" },
  ];
  ```

### theme

- `type`: `string`

主题配置，填写对应的主题配置名称可读取默认主题配置,自动填充内置样式，如有个别属性仍需调整或自定义，可根据上方文档配置传值。

```javascript
const theme = "LightOrange";
const theme = "blueDark";
```
