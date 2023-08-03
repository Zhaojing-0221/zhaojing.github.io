<template>
    <div class="chart-wapper">
        <Pie :data="data" :color=color :animation="animation" :coordinate="coordinate"></Pie>
    </div>
</template>
<script setup>
// 图表的数据
const data = [
    {x: 1, y: 45},
    {x: 2, y: 60},
    {x: 3, y: 20},
];
// 图表的颜色
const color = ['rgb(110,147,243)', 'rgb(228,138,98)', 'rgb(255,153,195)'];
const animation = {
    'highLight':{ // highLight：动画名称
        // 高亮颜色
        color: ['#527FF3', '#E47949', '#FF73AC'],
        // 动画多少毫秒执行一次 1000ms => 1s
        time: 1000, 
    }
};
// 设置饼图半径
const coordinate = {
    innerRadius: 0.8,
    radius: 0.9
}
</script>