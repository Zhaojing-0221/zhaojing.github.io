<template>
    <div class="chart-wapper  dark">
        <Line :data="dataMuti" seriesField="group" theme="blueDark.default"></Line>
    </div>
</template>
<script setup>
const dataMuti = [
    {x: 1, y: 332, group: '综采一队'},
    {x: 2, y: 202, group: '综采一队'},
    {x: 3, y: 322, group: '综采一队'},
    {x: 4, y: 132, group: '综采一队'},
    {x: 1, y: 152, group: '综采二队'},
    {x: 2, y: 100, group: '综采二队'},
    {x: 3, y: 240, group: '综采二队'},
    {x: 4, y: 170, group: '综采二队'},
    {x: 1, y: 318, group: '综采三队'},
    {x: 2, y: 108, group: '综采三队'},
    {x: 3, y: 318, group: '综采三队'},
    {x: 4, y: 189, group: '综采三队'}
];
</script>