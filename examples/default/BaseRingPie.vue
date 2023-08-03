<template>
    <div class="chart-wapper">
        <Pie 
            :data="dataBase" 
            :coordinate="coordinate">
        </Pie>
    </div>
</template>
<script setup>
// 图表的数据
const dataBase = [
    {x: 1, y: 45},
    {x: 2, y: 60},
    {x: 3, y: 20},
    {x: 4, y: 10},
    {x: 5, y: 18}
];
const coordinate = {
    interval: 0.02,
    radius: 0.8,
    innerRadius: 0.85,
};

</script>
