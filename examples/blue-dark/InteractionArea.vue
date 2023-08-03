<template>
    <div class="chart-wapper dark large">
        <Area 
            :chartBasic="chartBasic"
            :data="dataMuti" 
            :tooltip="tooltip"
            :axis="axis"
            theme="blueDark.default">
        </Area>
    </div>
</template>

<script setup>
const chartBasic = {
    padding: [30, 0, 30, 50],
}
// 图表的数据
const dataMuti = [
    { x: '05-19', y: 2400,  t: '2023-05-19' },
    { x: '05-20',  y: 5000,   t: '2023-05-20' },
    { x: '05-21', y: 350,    t: '2023-05-21' },
    { x: '05-22',  y: 6700,    t: '2023-05-22' },
    { x: '05-23', y: 3950,    t: '2023-05-23' },
    { x: '05-24',  y: 6070,    t: '2023-05-24' },
    { x: '05-25', y: 1700,    t: '2023-05-25' },
    { x: '05-26',  y: 700,    t: '2023-05-26' },
    { x: '05-27', y: 6700,    t: '2023-05-27' },
    { x: '05-28',  y: 3700,    t: '2023-05-28' },
    { x: '05-29', y: 3050,    t: '2023-05-29' },
    { x: '05-30',  y: 9700,    t: '2023-05-30' },
    { x: '05-31', y: 1700,   t: '2023-05-31' },
    { x: '06-01',  y: 6700,   t: '2023-06-01' },
    { x: '06-02', y: 700,   t: '2023-06-02' },
    { x: '06-03',  y: 2700,   t: '2023-06-03' },
    { x: '06-04', y: 3050,   t: '2023-06-04' },
    { x: '06-05',  y: 1070,   t: '2023-06-05' },
    { x: '06-06',  y: 6700,   t: '2023-06-06' },
    { x: '06-07', y: 1000,   t: '2023-06-07' },
    { x: '06-08',  y: 2700,   t: '2023-06-08' },
    { x: '06-09', y: 3050,   t: '2023-06-09' },
    { x: '06-10',  y: 1700,   t: '2023-06-10' },
    { x: '06-11', y: 1070,   t: '2023-06-11' },
    { x: '06-12',  y: 2300,   t: '2023-06-12' },
    { x: '06-13', y: 3050,   t: '2023-06-13' },
    { x: '06-14',  y: 1000,   t: '2023-06-14' },
    { x: '06-15', y: 1000,   t: '2023-06-15' },
    { x: '06-16',  y: 2300,   t: '2023-06-16' },
    { x: '06-17', y: 3050,   t: '2023-06-17' },
    { x: '06-18',  y: 1700,   t: '2023-06-18' },
    { x: '06-19',  y: 1000,   t: '2023-06-19' },
    { x: '06-20',  y: 100,   t: '2023-06-20' },
];
// 对y轴的数据进行格式化：添加千分符
const toThousands = ( num, char = ',' , digit = 3) => {
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
    customItems: items => {
        items.forEach(item => {
            item.value = toThousands(item.data.y);
            item.name = "总产量";
        });
        return items;
    },
    itemTpl: `
    <li class="g2-tooltip-list-item">
        <span class="g2-tooltip-marker" style="background-color:{color} ;"></span>
        <span class="g2-tooltip-name">{name}</span>
        <span class="g2-tooltip-value">{value} 
            <span class="g2-tooltip-unit">吨</span>
        </span>
    </li>`,
}
</script>