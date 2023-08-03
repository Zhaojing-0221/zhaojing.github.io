---
outline: 'deep'
---

# lightOrange

`lightOrange`称为亮橙色主题，主要是为了精益项目中的亮色图表而设计。

`lightOrange`主题和`blueDark`主题是一一对应的，分别有：`light-orange.default`，`light-orange.circular`、`light-orange.dataExtract`、`light-orange.mirror`、`light-orange.arrowMain`、`light-orange.arrowSecond`。




### lightOrange.default

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


<preview path="../examples/light-orange/MutiArea.vue" title="多组面积图" description=""></preview>

<preview path="../examples/light-orange/InteractionArea.vue" title="带横向滚动的面积图" description=""></preview>

<preview path="../examples/light-orange/BaseLine.vue" title="折线图" description=""></preview>



### lightOrange.circular

该主题适用于以下环形图：
- `单日`
    - `总产量环形图`
    - `检修时间-弹窗-双环形图`

- `周期`
    - `总产量环形图`

<preview path="../examples/light-orange/BasePie.vue" title="单环形图" description=""></preview>

<preview path="../examples/light-orange/RingPie.vue" title="双环形图" description=""></preview>

<preview path="../examples/light-orange/AutoLightCircular.vue" title="双环高亮环形图" description=""></preview>
<preview path="../examples/light-orange/AutoLightTextMarkerCircular.vue" title="带文本高亮环形图" description=""></preview>



###  blueDark.dataExtract

<preview path="../examples/light-orange/BigDataExtractLine.vue" title="大数据量提取的折线图" description=""></preview>

### lightOrange.mirror

该主题适用的图表：

- `周期弹窗`
    - `有效生产`  
        - `生产辅助系统异常分析图`
    - `生产误时`
        - `生产误时统计分析`


<preview path="../examples/light-orange/MirrorInterval.vue" title="镜像图" description=""></preview>


<preview path="../examples/light-orange/ScrollBarMirrorInterval.vue" title="带滚动的镜像图" description=""></preview>

### lightOrange.arrowMain

该主题适用的图表：

- `生产误时`
    - `生产误事详细原因分析（主要原因）`

示例：
<preview path="../examples/light-orange/ArrowMainInterval.vue" title="镜像图" description=""></preview>

该主题适用的图表：

### lightOrange.arrowSecond

- `生产误时`
    - `生产误事详细原因分析（次要原因）`

示例：
<preview path="../examples/light-orange/ArrowSecondInterval.vue" title="镜像图" description=""></preview>




