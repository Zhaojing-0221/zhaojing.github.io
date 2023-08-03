<template>
    <div class="chart-wapper dark">
        <Line :data="dataPic" :annotation="annotation" theme="blueDark.default"></Line>
    </div>
</template>
<script setup>
import chartArrow from '../../public/chart-arrow.svg'
// 图表的数据
const dataPic = [
    { x: "00:00", y: 332 },
    { x: "04:00", y: 202 },
    { x: "08:00", y: 322 },
    { x: "12:00", y: 132 },
    { x: "16:00", y: 152 },
    { x: "20:00", y: 100 },
    { x: "22:00", y: 240 },
    { x: "24:00", y: 170 },
]

const annotation = {
    image: [
        {
            src: chartArrow,
            start: ['00:00', 'min'],
            end: ['00:00', 'min'],
            offsetX: -7,
            offsetY: -2,
        },
        {
            src: chartArrow,
            start: ['08:00', 'min'],
            end: ['08:00', 'min'],
            offsetX: -7,
            offsetY: -2,
        },
        {
            src: chartArrow,
            start: ['16:00', 'min'],
            end: ['16:00', 'min'],
            offsetX: -7,
            offsetY: -2,
        },
    ],

};
</script>