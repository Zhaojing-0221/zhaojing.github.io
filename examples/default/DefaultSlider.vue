<template>
    <div class="chart-wapper">
        <Line :data="data" :axis="axis"></Line>
    </div>
</template>
<script setup>

const data = [];

// 生成模拟数据
for(let i = 0 ; i < 3000 ; i+=1){
    switch (true) {
        case i>=100 && i<1000:
        data.push({x:i.toString(),y:i}) 
        break;

        case i>=1000 && i<2000:
        data.push({x:i.toString(),y:i/5}) 
        break;

        case i>=2000 && i<3000:
        data.push({x:i.toString(),y:i/2}) 
        break;

        default:
        data.push({x:i.toString(),y:i*10}) 
        break;
    }
}

const axis = {
    xAxis:{
        slider:true
    }
}
</script>
<style></style>