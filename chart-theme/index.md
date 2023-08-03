# 图表主题切换

图表组件现提供了两种内置主题:`blueDark`和`lightOrange`，不同的主题配置了不同的样式属性：`axis`、`tooltip`、`color`、`fillColor`等等。

### 主题的设计理念

主题的设计之初主要是将图表中的样式进行统一配置，组件内部通过读取主题中的样式对图表样式进行设置，从而使得`业务组件`在使用时图表组件时，只关注数据，而不需要传递过多的样式属性。


### blueDark主题

`blueDark`称为蓝黑色主题，主要是为了精益项目中的蓝黑色图表样式而设计，该主题基于实际的业务需求，又拆分了六个小的主题，分别如下：

- `blueDark.default`
- `blueDark.circular`
- `blueDark.dataExtract`
- `blueDark.mirror`
- `blueDark.arrowMain`
- `blueDark.arrowSecond`

### lightOrange主题

`lightOrange`称为亮橙色主题，主要是为了精益项目中的亮色图表而设计，同样`lightOrange`也拆分了六个小的主题，分别如下：

- `lightOrange.default`
- `lightOrange.circular`
- `lightOrange.dataExtract`
- `lightOrange.mirror`
- `lightOrange.arrowMain`
- `lightOrange.arrowSecond`

### 使用主题

主题使用时只需要将主题参数传递给对应的图表组件即可：

```javascript
<!-- 折线图：使用blueDark.default主题 -->
<Line theme="blueDark.default"></Line>


<!-- 镜像图：使用blueDark.mirror -->
<IntervalChart theme="blueDark.mirror"></IntervalChart>


<!-- 饼图：使用lightOrigin.default主题 -->
<Pie theme="lightOrange.default"></Pie>
```

之后，组件会通过传递的`theme`参数读取改主题对应的样式配置，渲染图表。