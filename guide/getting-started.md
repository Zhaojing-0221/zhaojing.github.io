---
# 取二三级标题生成目录
outline: 'deep'
---

# :rocket: 快速开始

### 准备工作

要使用图表组件库，你的项目必须安装对应版本的`Vue`和`antv g2`：
```javascript
yarn add vue@3.2.37
yarn add @antv/g2@4.2.10
```

### 如何使用

在项目中创建对应的`chartlib`目录并放入打包后的组件库文件`chart-component-base.js`：
```javascript
项目根目录:
├─src
│  └─chartlib
│      └─chart-component-base.js
```

::: tip
组件库代码文件放置的目录文件和位置可以根据项目本身的目录规划自行决定，后面全局注册组件时注意引入目录即可。
:::

在`main.js`中全局注册组件：
```javascript{24,32}
// 引入 vue 组件
import { createApp } from 'vue';
import vuex from '@/store';
import router from '@/router';
import App from './App.vue';

// 引入三方组件
import ElementPlus from 'element-plus';

// 引入自定组件
import utils from '@/utils';
import api from '@/api';
import components from '@/components';
import i18n from '@/assets/i18n';

// 初始化app
let app = createApp(App);

// 配置全局函数
app.config.globalProperties.$utils = utils;
app.config.globalProperties.$api = api;

// 引入组件
import chartComponentBase from '@/chartlib/chart-component-base';

// 全局加载自定义组件
for (let i in components) app.component(i, components[i]);
app.use(ElementPlus); // elementui
app.use(router);
app.use(vuex);
app.use(i18n);
app.use(chartComponentBase);
app.mount('#app');

```

在模板中使用：

```html
<!-- 饼图使用 -->
<Pie :data=data><Pie/>
<!-- 折线图使用 -->
<Line :data=data></Line>
```

### 图表使用参数简单说明
:::tip
使用图表组件时，需要给图表组件传入参数，这里对参数做一些简单的说明，详细的参数见：图表参数。
:::
#### data
- `type`: `Array`
- `default`: `[]`

图表的数据，必选参数，如果没有该参数，则图表无法显示。

目前只支持一种数据结构：

```javascript
const data = [
  { genre: 'Sports', sold: 275, age: 10, team: 'team1' },
  { genre: 'Strategy', sold: 115, age: 20, team: 'team1' },
  { genre: 'Action', sold: 120, age: 20, team: 'team2' },
  { genre: 'Shooter', sold: 350, age: 10, team: 'team2' },
  { genre: 'Other', sold: 150, , age: 10, team: 'team3' },
];
```

#### chartBasic
- `type`: `Object `

图表对象的一些基础配置，比如图表宽（`width`）高（`height`）、内边距(`padding`)以及图表的渲染引擎(`renderer`)等。如果没有`width`和`height`参数，图表容器的宽高会自适应父组件`DOM`元素的宽高，且渲染方式为`canvas`。

#### xField
- `type`: `String`  
- `default`: `'x'`

`x`轴字段。

以那个字段作为`x`轴的数据(默认以`data`数据中的`x`字段)：

```javascript
xField = 'genre'
```

#### yField
- `type`: `String` 
- `required`: `True`  

`y`轴字段。

以那个字段作为`y`轴的数据(默认以`data`数据中的`y`字段)：
```javascript
yField = 'sold'
```

#### seriesField
- `type`: `String` 
- `default`: `'undefined'`
- `required`: `False`   

多条图形的分组字段。

当有多条图形：多条折线图，多条面积图，通过那个数据字段对数据进行分组：

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

#### tooltip
- `type`: `Boolean | Object`
- `default`: `true`  

提示信息，其中包括提示的标题、内容、样式、辅助线等

![An image](../public/tooltip.png)

`tooltip`默认是打开的，内容样式为`g2`图表默认的内容和样式。

关闭`tooltip`的显示，将该项置为`false`即可：

```javascript
tooltip: false
```

#### axis
坐标轴的相关配置：坐标轴标题、坐标轴轴线、坐标轴刻度线、坐标轴刻度值、网格线、缩略轴、最标轴的文本标记。

![An image](../public/axis.png)

坐标轴默认显示，可以通过设置`false`将坐标轴关闭。

统一关闭`x`、`y`轴：
```javascript
axis: false 
```
可通过配置单独关闭`x`或者`y`：
```javascript
axis: {
    xAxis: false,
    yAxis: false
}
```

#### legend
图例的相关配置。

图例默认是显示的，可通过传入`false`关闭图例：
```javascript
legend: false

```

#### line
- `type`: `Object`

线条相关的内容：线条是否平滑、线条上的点。


#### annotation

对图表做一些标注，比如在图表上添加一些辅助图片、辅助线（可带文本）、辅助文本、辅助框（框选一段图表区域）、图表数据点标注等。

#### color

图表的一组色值，如果不单独设置该参数，则采用g2默认的色板值。


#### fillColor

面积图的填充色。


