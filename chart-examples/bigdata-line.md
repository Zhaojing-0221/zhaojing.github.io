# 大数据量的折线图

### G2原生slider缩略轴

可以让用户在数据量较大的情况下一次只关注局部的数据。

 <preview path="../examples/default/DefaultSlider.vue" title="较大数据量slider缩略轴" description=""></preview>

### 大量数据slider缩略轴

当数据量过大时,使用G2原生slider缩略轴滑动会严重卡顿。开启massData会使用默认数据提取方法，在大量数据中提取数据趋势点渲染图表。同时也支持自定义数据提取方式。

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

<preview path="../examples/blue-dark/BigDataExtractLine.vue" title="大量数据slider缩略轴" description=""></preview>

### 精益项目亮橙色主题大数据量缩略轴

<preview path="../examples/light-orange/BigDataExtractLine.vue" title="大量数据slider缩略轴" description=""></preview>
