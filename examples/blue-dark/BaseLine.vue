<template>
    <div class="chart-wapper  dark">
        <Line 
            :data="data" 
            :axis="axis"
            :chartBasic="chartBasic"
            :tooltip="tooltip"
            theme="blueDark.default">
        </Line>
    </div>
</template>
<script setup>
// 图表的数据
const data = [
    { x: '00:00', y: 174, s: '05-19', t: '2023-05-19' },
    { x: '01:00', y: 78, s: '05-20', t: '2023-05-20' },
    { x: '06:00',  y: 15, s: '05-22',   t: '2023-05-22' },
    { x: '08:00',  y: 8, s: '05-24',   t: '2023-05-24' },
    { x: '12:00', y: 12,  s: '05-25',  t: '2023-05-25' },
    { x: '15:00', y: 178, s: '05-27',   t: '2023-05-27' },
    { x: '16:00', y: 10, s: '05-28',   t: '2023-05-28' },
    { x: '20:00',  y: 56, s: '05-29',  t: '2023-05-29' },
    { x: '24:00', y: 100,  s: '05-30',  t: '2023-05-30' },
];

const chartBasic = {
    padding: [35, 0, 30, 35]
};

const tooltip = {
    title: (title, datum) => datum.s + ' ' + datum.x, // 提升信息的标题要使用数据中的那个自动做显示
    customItems: items => {
        return items.map(it => {
            const res = { ...it };
            res.name = '支架位置';
            return { ...res };
        });
    },
}

// 煤机轨迹要求显示数据的最大值
const num = data.map(it => it.y);
const min = Math.min(...num) ? Math.min(...num) : 0;
const max = Math.max(...num) ? Math.max(...num) : 0;

const axis = {
    xAxis: {
        scale: {
            ticks: ['00:00', '06:00', '12:00', '18:00', '24:00'],
        },
    },
    yAxis: {
        unit: { 
            content: '架', 
            position: ['-5%', '-17%'],
        },
        // 横坐标固定显示 5个labe值
        scale: {
            min: min,
            ticks: [min, Math.trunc(((max - min) * 25) / 100) + min, Math.trunc(((max - min) * 50) / 100) + min, Math.trunc(((max - min) * 75) / 100) + min, max],
        },
    },
}
</script>