<template>
    <div class="chart-wapper dark large">
        <Area :chartBasic="chartBasic" :data="dataMuti" seriesField="s" :tooltip="tooltip" :axis="axis"
            theme="blueDark.default" :annotation="annotation"></Area>
    </div>
</template>
<script setup>
const chartBasic = {
    padding: [30, 0, 30, 70],
}
const dataMuti = [
    { x: '05-19', y: 20000, s: '总产量', t: '2023-05-19' },
    { x: '05-20', y: 45000, s: '总产量', t: '2023-05-20' },
    { x: '05-21', y: 30050, s: '总产量', t: '2023-05-21' },
    { x: '05-22', y: 60700, s: '总产量', t: '2023-05-22' },
    { x: '05-23', y: 32950, s: '总产量', t: '2023-05-23' },
    { x: '05-24', y: 60700, s: '总产量', t: '2023-05-24' },


    { x: '05-19', y: 10700, s: '综采一队', t: '2023-05-19' },
    { x: '05-20', y: 700, s: '综采一队', t: '2023-05-20' },
    { x: '05-21', y: 56700, s: '综采一队', t: '2023-05-21' },
    { x: '05-22', y: 37700, s: '综采一队', t: '2023-05-22' },
    { x: '05-23', y: 38050, s: '综采一队', t: '2023-05-23' },
    { x: '05-24', y: 90700, s: '综采一队', t: '2023-05-24' },


    { x: '05-19', y: 19700, s: '综采二队', t: '2023-05-19' },
    { x: '05-20', y: 6700, s: '综采二队', t: '2023-05-20' },
    { x: '05-21', y: 10700, s: '综采二队', t: '2023-05-21' },
    { x: '05-22', y: 23700, s: '综采二队', t: '2023-05-22' },
    { x: '05-23', y: 30050, s: '综采二队', t: '2023-05-23' },
    { x: '05-24', y: 10700, s: '综采二队', t: '2023-05-24' },
];
// 对y轴的数据进行格式化：添加千分符
const toThousands = (num, char = ',', digit = 3) => {
    let re = new RegExp('(\\d)(?=(?:\\d{' + digit + '})+$)', 'g');
    return num.toString().replace(/\d+/, function (n) {
        return n.replace(re, '$1' + char);
    });
};
const axis = {
    yAxis: {
        scale: {
            formatter: (val, k) => toThousands(val),
        },
        unit: {
            content: '吨',
            position: ['-5%', '-8%']
        }
    }
}
const tooltip = {
    title: (title, datum) => datum.t, // 提升信息的标题要使用数据中的那个自动做显示
    itemTpl: `
    <li class="g2-tooltip-list-item">
        <span class="g2-tooltip-marker" style="background-color:{color} ;"></span>
        <span class="g2-tooltip-name">{name}</span>
        <span class="g2-tooltip-value">{value} 
            <span class="g2-tooltip-unit">吨</span>
        </span>
    </li>`,
}

const annotation = {
    line: [
        {
            start: ['05-21', 0],
            end: ['05-21', 'max'],
        },
        {
            start: ['05-23', 0],
            end: ['05-23', 'max'],
        }
    ],
    regionFilter: [
        // 第一段上色区域的配置
        {   // 区域的颜色
            // 上色的开始位置
            start: ['min', 'min'],
            // 上色的结束位置 4-2为横坐标对应的数值
            end: ['05-21', 'max'],
        },
        // 第二段上色区域的配置
        {
            // 上色的开始位置 4-3为横坐标对应的数值
            start: ['05-23', 'max'],
            // 上色的结束位置 4-2为横坐标对应的数值
            end: ['max', 0],
        }
    ]
}
</script>