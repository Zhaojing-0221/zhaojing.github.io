<template>
    <div class="chart-wapper">
        <Line :data="dataPic" :annotation="annotation"></Line>
    </div>
</template>
<script setup>
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
    regionFilter: [
        {
            start: ['04:00', 'min'],
            end: ['12:00', 'max'],
            color: 'purple'
        },
        {
            start: ['20:00', 'min'],
            end: ['22:00', 'max'],
            color: 'red'
        }
    ],
};
</script>