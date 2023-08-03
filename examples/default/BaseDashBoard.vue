<template>
    <div class="chart-wapper">
        <dash-board :data="data" :axis="axis" :coordinate="coordinate" :scale="scale"></dash-board>
    </div>
</template>
<script setup>
// 图表的数据
const data = 6

// 配置坐标系
const coordinate = {
        startAngle: (-9 / 8) * Math.PI,
        endAngle: (1 / 8) * Math.PI,
        radius: 0.87,
}

// 度量
const scale = {
        min: 0,
        max: 10,
        tickInterval: 1
}

// 坐标轴
const axis = {
        lineWidth: 12,
        label: {
            offset: -26,
            style: {
                fontSize: 14,
                textAlign: 'center',
                textBaseline: 'middle',
            },
        },
        subTickLine: {
            count: 4,
            length: -10,
        },
        tickLine: {
            length: -14,
        },
}
</script>