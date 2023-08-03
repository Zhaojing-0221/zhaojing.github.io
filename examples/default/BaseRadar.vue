<template>
    <div class="chart-wapper">
        <RadarChart :data="data"></RadarChart>
    </div>
</template>
<script setup>
// 图表的数据
const data = [
    { x: 'Design', y: 30 },
    { x: 'Development',  y: 60 },
    { x: 'Marketing',  y: 20 },
    { x: 'Users', y: 40 },
    { x: 'Test',  y: 50 },
    { x: 'Language',  y: 50 },
    { x: 'Technology', y: 28 },
];
</script>