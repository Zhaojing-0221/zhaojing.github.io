<template>
    <div class="chart-wapper dark">
        <IntervalChart 
            :data="data" 
            seriesField="type" 
            :axis="axis"
            transpose="mirror"
            theme="blueDark.mirror"></IntervalChart>
    </div>
</template>
<script setup>
// 图表的数据
const data = [
    { x: '12-08', y: 10, type: '时间' },
    { x: '12-11', y: 2, type: '时间' },
    { x: '12-14', y: 8, type: '时间' },
    { x: '12-17', y: 30, type: '时间' },
    { x: '12-20', y: 10, type: '时间' },
    { x: '12-31', y: 15, type: '时间' },
    { x: '12-23', y: 18, type: '时间' },
    { x: '12-08', y: 15, type: '次数' },
    { x: '12-11', y: 15, type: '次数' },
    { x: '12-14', y: 1, type: '次数' },
    { x: '12-17', y: 6, type: '次数' },
    { x: '12-20', y: 9, type: '次数' },
    { x: '12-31', y: 0, type: '次数' },
    { x: '12-23', y: 11, type: '次数' },
];
const axis = {
    yAxis: {
        // 只需要调整position参数，而不需要传递其他的参数，其他的参数都在主题中
        unit: [
            {
                position: ['-4.5%', '-41%'],
            },
            {
                position: ['-4.5%', '140%'], // 调整文字位置
            },
        ]
    }
}
</script>