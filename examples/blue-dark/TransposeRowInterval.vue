<template>
    <div class="chart-wapper dark">
        <IntervalChart :data="data" theme="blueDark.default" transpose='horizontal' :chartBasic="chartBasic">
        </IntervalChart>
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
];

const chartBasic = {
    padding: [30, 50, 10, 80]
}
</script>