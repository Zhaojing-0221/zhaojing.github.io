<template>
    <div class="chart-wapper">
        <DoubleYArea :data="data" :color="color" :view="view"></DoubleYArea>
    </div>
</template>
<script setup>
import {ref}from 'vue'

const data = ref([
    {
        x:'00:00',
        y1:50,
        y2:40
    },    
    {
        x:'02:00',
        y1:60,
        y2:50
    },
    {
        x:'04:00',
        y1:50,
        y2:60
    },
    {
        x:'06:00',
        y1:40,
        y2:50
    },
    {
        x:'08:00',
        y1:30,
        y2:40
    },
    {
        x:'10:00',
        y1:20,
        y2:45
    },
    {
        x:'12:00',
        y1:30,
        y2:50
    }
])

const color = '#26ff26'

const view = [
    {
        color:'#1890ff',
    }
]
</script>
<style></style>