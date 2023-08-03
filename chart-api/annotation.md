---
outline: "deep"
---

# annotation
图形标注，`Annotation`，作为图表的辅助元素，主要用于在图表上标识额外的标记注解。


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

![An image](/annotation-line.png)

```javascript
// 配置两组辅助线标记
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
  ],
};
```

::: tip
`start`和`end`属性值的第一个元素的值需与 `x` 轴 或 `y` 轴数值对应，否则辅助线无法渲染到正确位置。
:::

#### annotation.image

- `type`: `Array[Object]`

  辅助图片，在图表上添加辅助图片，可以添加多个图片标注。

  ![An image](../public/image-annotation.png)

```javascript
// 配置三个图片标记
import chartArrow from '../../public/chart-arrow.svg'
const annotation = {
    image: [
      {
        src: chartArrow, // 图片需要先引入，如import方式等
        start: ["00:00", "min"], // 从"00:00"开始
        end: ["00:00", "min"], // 在"00:00"结束
        offsetX: -6, // x方向偏移量
        offsetY: -10, // y方向偏移量
      },
      {
        src: chartArrow, // 图片需要先引入，如import方式等
        start: ["08:00", "min"], // 从"08:00"开始
        end: ["08:00", "min"], // 从"08:00"开始
        offsetX: -6, // x方向偏移量
        offsetY: -10, // y方向偏移量
      },
       {
        src: chartArrow, // 图片需要先引入，如import方式等
        start: ["16:00", "min"], // 从"08:00"开始
        end: ["16:00", "min"], // 从"08:00"开始
        offsetX: -6, // x方向偏移量
        offsetY: -10, // y方向偏移量
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

::: tip
`start`和`end`属性值的第一个元素的值需与 `x` 轴 或 `y` 轴数值对应，否则无法渲染到正确位置。
:::
