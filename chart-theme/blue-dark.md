---
outline: 'deep'
---

# blueDark

`blueDark`称为蓝黑色主题，主要是为了精益项目中的蓝黑色图表样式而设计。

::: tip

主题的主要目的在于将图表中的样式进行统一配置，组件侧通过读取主题中的固定样式对图表样式进行设置，从而使得`业务组件`在使用时图表组件时可以不需要传递过多的样式属性。不过，需要注意的时，主题仅仅包含样式的配置，数据驱动的内容，还是需要业务组件去设置，比如：希望固定`x/y`轴显示多少个`label`值、对`x/y`轴的数据进行格式化等。

:::

`blueDark`主题在设计之初，只有一种默认的图表主题：`blueDark.default`，但是后续因为这套默认的图表主题样式并不能满足该项目中所有的图表，因此又拆分出来五个主题样式，分别是：`blueDark.circular`、`blueDark.dataExtract`、`blueDark.mirror`、`blueDark.arrowMain`、`blueDark.arrowSecond`。


### blueDark.default

该主题适用于项目中的大部分图表：

- `单日`
    - `总产量趋势分析图`
    - `煤机运行轨迹图`
    - `煤机运行轨迹详情页面`
- `周期`
    - `总产量趋势图`
    - `生产误时原因分析`
    - `生产误时趋势分析`
- `周期弹窗`
    - `有效生产`  
        - `有效生产时间分析图`
        - `功效分析图`
    - `检修时间`
        - `检修时间分析图`

以下是简单的使用示例：

<preview path="../examples/blue-dark/MutiArea.vue" title="多组面积图" description=""></preview>

<preview path="../examples/blue-dark/InteractionArea.vue" title="带横向滚动的面积图" description=""></preview>

<preview path="../examples/blue-dark/BaseLine.vue" title="折线图" description=""></preview>

### blueDark.circular

该主题适用于以下环形图：
- `单日`
    - `总产量环形图`
    - `检修时间-弹窗-双环形图`

- `周期`
    - `总产量环形图`

<preview path="../examples/blue-dark/BasePie.vue" title="单环形图" description=""></preview>

<preview path="../examples/blue-dark/RingPie.vue" title="双环形图" description=""></preview>

<preview path="../examples/blue-dark/AutoLightCircular.vue" title="双环高亮环形图" description=""></preview>
<preview path="../examples/blue-dark/AutoLightTextMarkerCircular.vue" title="带文本高亮环形图" description=""></preview>

###  blueDark.dataExtract

<preview path="../examples/blue-dark/BigDataExtractLine.vue" title="大数据量提取的折线图" description=""></preview>

### blueDark.mirror

该主题适用的图表：

- `周期弹窗`
    - `有效生产`  
        - `生产辅助系统异常分析图`
    - `生产误时`
        - `生产误时统计分析`


<preview path="../examples/blue-dark/MirrorInterval.vue" title="镜像图" description=""></preview>


<preview path="../examples/blue-dark/ScrollBarMirrorInterval.vue" title="带滚动的镜像图" description=""></preview>

### blueDark.arrowMain

该主题适用的图表：

- `生产误时`
    - `生产误事详细原因分析（主要原因）`

示例：
<preview path="../examples/blue-dark/ArrowMainInterval.vue" title="横向顶部箭头(主要原因)" description=""></preview>

<preview path="../examples/blue-dark/ArrowMainScrollbarInterval.vue" title="带滚动的横向顶部箭头(主要原因)" description=""></preview>

该主题适用的图表：

### blueDark.arrowSecond

- `生产误时`
    - `生产误事详细原因分析（次要原因）`

示例：
<preview path="../examples/blue-dark/ArrowSecondInterval.vue" title="横向顶部箭头(次要原因)" description=""></preview>

<preview path="../examples/blue-dark/ArrowSecondScrollbarInterval.vue" title="带滚动的横向顶部箭头(次要原因)" description=""></preview>



