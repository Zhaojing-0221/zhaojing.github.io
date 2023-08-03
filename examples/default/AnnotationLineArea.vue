<template>
    <div class="chart-wapper">
        <Area 
            :data="dataMuti" 
            seriesField="group" 
            :annotation="annotation">
        </Area>
    </div>
</template>
<script setup>
// 图表的数据
const dataMuti = [
    { x: '4-1', y: 332, group: '综采一队' },
    { x: '4-2', y: 202, group: '综采一队' },
    { x: '4-3', y: 322, group: '综采一队' },
    { x: '4-4', y: 132, group: '综采一队' },
    { x: '4-1', y: 152, group: '综采二队' },
    { x: '4-2', y: 100, group: '综采二队' },
    { x: '4-3', y: 240, group: '综采二队' },
    { x: '4-4', y: 170, group: '综采二队' },
    { x: '4-1', y: 318, group: '综采三队' },
    { x: '4-2', y: 108, group: '综采三队' },
    { x: '4-3', y: 318, group: '综采三队' },
    { x: '4-4', y: 189, group: '综采三队' }
];

const annotation = {
    line: [
        {
            start: ['4-2', 100],
            end: ['4-2', 'max'],
            style: {
                lineDash: [8, 4, 4, 2],
                stroke: '#A2A0ED',
                lineWidth: 2
            }
        },
        {
            start: ['4-3', 100],
            end: ['4-3', 'max'],
            style: {
                lineDash: [8, 4, 4, 2],
                stroke: '#A2A0ED',
                lineWidth: 2
            }
        }
    ]

};
</script>