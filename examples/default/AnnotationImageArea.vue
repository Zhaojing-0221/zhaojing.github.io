<template>
    <div class="chart-wapper">
        <Area :data="dataPic" seriesField="group" :legend="false" :annotation="annotation"></Area>
    </div>
</template>
<script setup>
import chartArrow from '../../public/chart-arrow.svg'
// 图表的数据
const dataPic = [
    { x: "00:00", y: 332, group: '综采一队' },
    { x: "04:00", y: 202, group: '综采一队' },
    { x: "08:00", y: 322, group: '综采一队' },
    { x: "12:00", y: 132, group: '综采一队' },
    { x: "16:00", y: 152, group: '综采一队' },
    { x: "20:00", y: 100, group: '综采一队' },
    { x: "22:00", y: 240, group: '综采一队' },
    { x: "24:00", y: 170, group: '综采一队' },
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