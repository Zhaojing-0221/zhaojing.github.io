<template>
    <div class="chart-wapper ai-dark">
        <Area 
            :chart-basic="chartCfg.chartBasic"
            :data="chartCfg.data"
            :tooltip="chartCfg.tooltip"
            :axis="chartCfg.axis"
            :theme="chartCfg.theme"></Area>
    </div>
</template>
<script setup>  
// 图表的数据
const chartCfg ={
    chartBasic: {
        padding: [30, 10, 30, 40], // 图表容器padding 可能会有四个值
    },
    data: [
        {x: '03-24', y: 44, 't': '2023-03-24'},
        {x: '03-25', y: 30, 't': '2023-03-25'},
        {x: '03-26', y: 43, 't': '2023-03-26'},
        {x: '03-27', y: 30, 't': '2023-03-27'},
        {x: '03-28', y: 0, 't': '2023-03-28'},
        {x: '03-29', y: 10, 't': '2023-03-29'},
        {x: '03-30', y: 30, 't': '2023-03-30'},
    ],
    tooltip: {
        title: (title, datum) => datum.t, // 提示信信息的标题要使用数据中的那个字段做显示
        itemTpl: `
            <li class="g2-tooltip-list-item">
                <span class="g2-tooltip-name">报警数量</span>
                <span class="g2-tooltip-value">
                    {value} <span class="g2-tooltip-unit">次</span>
                </span>
            </li>`,
    },
    theme: 'aiBlue.default',
    axis: {
        yAxis: {
            unit: {
                content: '次',
                position: ['-4%', '-15%']
            }
        }
    }
};

</script>