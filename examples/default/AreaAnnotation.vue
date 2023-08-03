<template>
    <div class="chart-wapper dark">
        <Area :data="data" :annotation="annotation" theme="blueDark.default"></Area>
    </div>
</template>
<script setup>

const data = [
      
        {x:'2001',y:60},
        {x:'2002',y:40},
        {x:'2003',y:20},
        {x:'2004',y:70},
        {x:'2005',y:60},
        {x:'2006',y:70},
        {x:'2007',y:40},
        {x:'2008',y:50},
        {x:'2010',y:70},
        {x:'2011',y:90},
        {x:'2012',y:60},
        {x:'2013',y:40},
        {x:'2014',y:30},
        {x:'2018',y:20},
    
    ]

const annotation = {
    regionFilter:[
        // 左边区域变暗
        {
            start: ['min', 0],
            end: ['2002', 'max']
        },
        // 右边区域变暗
        {
            start: ['2007', 0],
            end: ['max', 'max']
        }, 
    ],
    // 线段标注
    line:[
        {
            start: ['2002', 0],
            end: ['2002', 'max'],
        },
        {
            start: ['2007', 0],
            end: ['2007', 'max'],
        }
    ]
}

</script>
<style></style>