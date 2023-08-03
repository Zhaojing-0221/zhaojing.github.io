<template>
    <div class="chart-wapper dark">
        <IntervalChart :data="data" theme="blueDark.arrowMain"></IntervalChart>
    </div>
</template>
<script setup>
// 图表的数据
const data = [
    { x: '我这里', y: 801 },
    { x: '汽运混煤', y: 100 },
    { x: '原煤', y: 819 },
    { x: '洗中块', y: 678 },
    { x: '洗混小块', y: 823 },
    { x: '超过8条就滚动条', y: 819 },
    { x: '再多一条', y: 678 },
    { x: '测试测试', y: 823 },
    { x: '3', y: 823 },
];
</script>