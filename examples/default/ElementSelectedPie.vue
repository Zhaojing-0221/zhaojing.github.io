<template>
    <div class="chart-wapper">
        <Pie :data="data" :coordinate="coordinate" :animation="animation" :annotation="annotation"></Pie>
    </div>
</template>
<script setup>
import { ref } from 'vue'

const data = [
    {x: '机电设备故障', y: 12},
    {x: '材料供应超时', y: 15},
    {x: '大块矸石堵仓', y: 12},
    {x: '提升系统停机', y: 15},
    {x: '个人违章违纪', y: 16},
];

const coordinate = {
    innerRadius: 0.8,
    radius: 0.9
}

const annotation = ref({
    text:{
        content: '18%',
        position: ['50%','50%'],
        offsetX: -15,
        style:{
            fontSize:18
        }
    }
})

const animation = ref({
    /** 饼图区域放大配置 */
    elementSelected: 0
});

const count = data.map(it=>it.y).reduce((total, num)=>total + num)

setInterval(()=>{
    animation.value.elementSelected += 1
    if(animation.value.elementSelected > 4){
        animation.value.elementSelected = 0
    }
    annotation.value.text.content = `${Math.round(data[animation.value.elementSelected].y/count*100)}%`
},1000)
</script>
<style></style>