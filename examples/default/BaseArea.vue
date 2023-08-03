<template>
    <div class="chart-wapper">
        <Area :data="data"></Area>
    </div>
</template>
<script setup>
// 图表的数据
const data = [
    { x: 1, y: 45 },
    { x: 2, y: 60 },
    { x: 3, y: 20 },
    { x: 4, y: 10 },
    { x: 5, y: 18 }
];
</script>