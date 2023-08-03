<template>
    <div class="chart-wapper ai-dark">
        <Line
            :theme="chartCfg.theme"
            :data="chartCfg.data"
            :seriesField="chartCfg.seriesField"
            :chartBasic="chartCfg.chartBasic"
            :tooltip="chartCfg.tooltip"
            :axis="chartCfg.axis" />
    </div>
</template>
<script setup>  
// 图表的配置
const chartCfg = {
    chartBasic: {
        padding: [60, 10, 40, 50], // 图表容器padding 可能会有四个值
    },
    seriesField: 's',
    data: [
        {x: '03-24', y: 33, s: '重大', t: '2023-03-24'},
        {x: '03-25', y: 30, s: '重大', t: '2023-03-25'},
        {x: '03-26', y: 39, s: '重大', t: '2023-03-26'},
        {x: '03-27', y: 38, s: '重大', t: '2023-03-27'},
        {x: '03-28', y: 34, s: '重大', t: '2023-03-28'},
        {x: '03-29', y: 33, s: '重大', t: '2023-03-29'},
        {x: '03-30', y: 30, s: '重大', t: '2023-03-30'},
        {x: '03-24', y: 20, s: '较大', t: '2023-03-24'},
        {x: '03-25', y: 20, s: '较大', t: '2023-03-25'},
        {x: '03-26', y: 20, s: '较大', t: '2023-03-26'},
        {x: '03-27', y: 20, s: '较大', t: '2023-03-27'},
        {x: '03-28', y: 24, s: '较大', t: '2023-03-28'},
        {x: '03-29', y: 25, s: '较大', t: '2023-03-29'},
        {x: '03-30', y: 22, s: '较大', t: '2023-03-30'},
        {x: '03-24', y: 16, s: '一般', t: '2023-03-24'},
        {x: '03-25', y: 18, s: '一般', t: '2023-03-25'},
        {x: '03-26', y: 20, s: '一般', t: '2023-03-26'},
        {x: '03-27', y: 17, s: '一般', t: '2023-03-27'},
        {x: '03-28', y: 15, s: '一般', t: '2023-03-28'},
        {x: '03-29', y: 10, s: '一般', t: '2023-03-29'},
        {x: '03-30', y: 11, s: '一般', t: '2023-03-30'},
        {x: '03-24', y: 8, s: '低', t: '2023-03-24'},
        {x: '03-25', y: 4, s: '低', t: '2023-03-25'},
        {x: '03-26', y: 1, s: '低', t: '2023-03-26'},
        {x: '03-27', y: 2, s: '低', t: '2023-03-27'},
        {x: '03-28', y: 3, s: '低', t: '2023-03-28'},
        {x: '03-29', y: 5, s: '低', t: '2023-03-29'},
        {x: '03-30', y: 0, s: '低', t: '2023-03-30'},
    ],
    tooltip: {
        title: (title, datum) => datum.t, // 提升信息的标题要使用数据中的那个自动做显示
        itemTpl: `
            <li class="g2-tooltip-list-item">
                <span class="g2-tooltip-marker" style="background-color:{color}"></span>
                <span class="g2-tooltip-name">{name}</span>
                <span class="g2-tooltip-value">{value} 
                    <span class="g2-tooltip-unit">吨</span>
                </span>
            </li>`,
    },
    theme: 'aiBlue.default',
    axis: {
        yAxis: {
            unit: {
                content: '次',
                position: ['-4.5%', '-18%']
            }
        }
    }
};

</script>
<style lang="scss">
.g2-tooltip{
    .g2-tooltip-list{
        .g2-tooltip-marker{
            width: 8px !important; 
            height: 8px !important;
        }
    }
}

</style>