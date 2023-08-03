<template>
    <div class="chart-wapper dark">
        <Area :data="data" seriesField="s" :color="color" theme="blueDark.default"/>
    </div>
</template>
<script setup>

const data = [
    {x:'1-1',y:50,s:'A'},
    {x:'1-2',y:60,s:'A'},
    {x:'1-3',y:70,s:'A'},
    {x:'1-4',y:60,s:'A'},
    {x:'1-5',y:40,s:'A'},
    {x:'1-6',y:50,s:'A'},
    {x:'1-7',y:90,s:'A'},    
    {x:'1-1',y:20,s:'B'},
    {x:'1-2',y:30,s:'B'},
    {x:'1-3',y:40,s:'B'},
    {x:'1-4',y:30,s:'B'},
    {x:'1-5',y:20,s:'B'},
    {x:'1-6',y:10,s:'B'},
    {x:'1-7',y:30,s:'B'},

    {x:'1-1',y:60,s:'C'},
    {x:'1-2',y:70,s:'C'},
    {x:'1-3',y:80,s:'C'},
    {x:'1-4',y:100,s:'C'},
    {x:'1-5',y:70,s:'C'},
    {x:'1-6',y:90,s:'C'},
    {x:'1-7',y:40,s:'C'},
    
]

// field是传入的seriesFields字段用于对数据进行分组
const color = {
    'A': 1,
    'B': 2,
    'C': 3,
}

</script>
<style></style>