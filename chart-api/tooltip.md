---
outline: 'deep'
---
# tooltip

- `type`: `Boolean | Object`

提示信息，其中包括提示的标题、内容、样式、辅助线等

![An image](../public/tooltip.png)

`tooltip`默认是打开的，内容样式为`g2`图表默认的内容和样式。

关闭`tooltip`的显示，将该项置为`false`即可：

```javascript
tooltip: false;
```

#### tooltip.crosshairs

- `type`: `Boolean | Object`,
- `default`: `false`

`tooltip`的辅助线开启，样式为`g2`图表提供的样式。如果需要关闭辅助线，设置`crosshairs`为`fasle`。

关闭`tooltip`的辅助线：
```javascript
tooltip = {
  crosshairs: false,
};

```

##### tooltip.crosshairs.type
- `type`: `String`
- `default`: `'x'`

辅助线的类型：`x`表示`x`轴上的辅助线（垂直辅助线），`y`表示`y`轴上的辅助线（水平辅助线）, `xy`表示同时显示`x`和`y`轴上的辅助线（水平辅助线）。

```javascript
tooltip = {
	crosshairs: {
		type: "x | y | xy",
	},
};
```

##### tooltip.crosshairs.line

如果需要配置辅助线的样式，传入相关的样式配置即可。

```javascript
tooltip = {
	crosshairs: {
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

`domStyles` 是以 `dom` 节点的 `class` 为 `key` 、`CSSProperties` 为 `value` 的对象，可以通过该属性修改 `tooltip` 提示框样式.

dom 结构以及设置`tooltip`样式示例如下：

```javascript
// dom结构
<div class="g2-tooltip">
  <div class="g2-tooltip-title">Language</div>
  <ul class="g2-tooltip-list">
    <li class="g2-tooltip-list-item">
      <span class="g2-tooltip-marker"></span>
      <span class="g2-tooltip-name">a</span>:<span class="g2-tooltip-value">70</span>
    </li>
    <li class="g2-tooltip-list-item">
      <span class="g2-tooltip-marker"></span>
      <span class="g2-tooltip-name">b</span>:<span class="g2-tooltip-value">50</span>
    </li>
  </ul>
</div>
```


设置`tooltip`样式：

```javascript
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
用于指定图例容器的模板，自定义模板时必须包含各个 `dom` 节点的 `class`,可通过该属性修改 `tooltip` 默认显示内容。

例如 `tooltip` 自带冒号，但通过如下代码可去除自带的冒号：

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

在渲染 `toolti`p 之前，对 `G2` 的 `tooltip items` 列表项目进行用户自定义处理，默认不做任何处理。可以用来对 `tooltip` 列表进行过滤、排序、格式化等操作,

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