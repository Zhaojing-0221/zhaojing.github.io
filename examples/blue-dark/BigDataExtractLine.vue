<template>
    <div class="chart-wapper dark large">
        <Line :chartBasic="chartBasic" :data="data" theme="blueDark.dataExtract" :axis="axis" :annotation="annotation">
        </Line>
    </div>
</template>
<script setup>
import response from './response.json'

const chartBasic = {
    padding: [40, 35, 40, 50],
}
// 图表的数据
const data = response.data.data.map(it => ({
    x: it[0],
    y: it[2],
}));

// 紫色的标注线
const annotation = {
    regionFilter: [
        {
            start: [1684631678000, 'min'],
            end: [1684673309000, 'max'],
        },
    ],
};
const axis = {
    yAxis: {
        unit: {
            content: '吨',
        }
    }
}
</script>