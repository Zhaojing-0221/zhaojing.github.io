<template>
    <div class="chart-wapper">
        <Area :data="dataMuti" seriesField="group" :annotation="annotation">
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
    regionFilter: [
        // 第一段上色区域的配置
        {   // 区域的颜色
            color: 'rgba(0, 0, 0, 0.2)',
            // 颜色是否在图表的最上层
            top: true,
            // 上色的开始位置
            start: ['min', 'min'],
            // 上色的结束位置 4-2为横坐标对应的数值
            end: ['4-2', 'max'],
        },
        // 第二段上色区域的配置
        {
            color: 'rgba(0, 0, 0, 0.2)',
            top: true,
             // 上色的开始位置 4-3为横坐标对应的数值
            start: ['4-3', 'max'],
            // 上色的结束位置 4-2为横坐标对应的数值
            end: ['max', 0],
        }
    ]
};
</script>