<template>
    <div class="chart-wapper">
        <Line :data="data" :axis="axis" theme="blueDark.dataExtract"></Line>
    </div>
</template>
<script setup>
import response from './response.json'
import { DateTime } from 'luxon';

// 图表的数据
const data = response.data.data.map(it => ({
    x: it[0],
    y: it[2],
}));

const axis = {
    xAxis: {
        slider: {
            massData: handlerData
        },
        scale: {
            tickMethod: cfg => {
                const res = [];
                const group = cfg.values.length / 6;
                for (let i = 0; i < 6; i++) {
                    res.push(cfg.values[Math.floor(group * i)]);
                }
                res.push(cfg.values[cfg.values.length - 1]);
                return res;
            },
            range: [0.02, 0.98],
        }
    },
    yAxis:{}
}

/**
 * 提取数据
 */
function extractionData(option, datum, second, color) {
    /** 间隔的时间戳 */
    const timeStamp = second * 1000;
    /** 起始位置时间戳 */
    let startStamp = datum[0].x;
    /** 结束位置时间戳 */
    const endStamp = datum[datum.length - 1].x;
    /** 处理后的data */
    const handlerRes = [];

    /** 处理后的时间戳数组 */
    const handlerStamp = [];

    while (startStamp <= endStamp) {
        const item = datum.find(it => {
            return it.x >= startStamp && it.x <= endStamp;
        });
        handlerRes.push({
            x: startStamp,
            y: item?.y,
            s: item?.s,
        });
        handlerStamp.push(startStamp);
        startStamp += timeStamp;
    }

    const timeinterval = datum[datum.length - 1].x - datum[0].x;

    // 将时间戳处理成字符串格式
    if (timeinterval <= 420000) {
        return {
            data: handlerRes.map(it => ({
                x: DateTime.fromJSDate(new Date(it.x)).toFormat('HH:mm:ss'),
                y: it.y,
                s: it.s,
            })),
        };
    } else {
        return {
            data: handlerRes.map(it => ({
                x: DateTime.fromJSDate(new Date(it.x)).toFormat('HH:mm'),
                y: it.y,
                s: it.s,
            })),
        };
    }
}

function handlerData(option, areaData, color) {
    if (option.data.length < 2) {
        return option;
    }

    /** 起始位置索引 */
    const startIndex = Math.floor((option.data.length - 1) * areaData[0]);

    /**  截取时间区间 */
    const timeArea = 86400000 * (areaData[1] - areaData[0]);
    const sliceData = [];
    option.data.forEach((item, index) => {
        if (startIndex <= index && item.x <= option.data[startIndex].x + timeArea) {
            sliceData.push(item);
        }
    });

    /** 第一条数据和最后一条数据时间戳的差 */
    const timeStampArea = sliceData[sliceData.length - 1].x - sliceData[0].x;
    /** 结果 */
    let result = {
        data: [],
        regionFilter: [],
    };

    switch (true) {
        case timeStampArea >= 1000 * 60 * 60 * 12:
            result = extractionData(option, sliceData, 600, color);
            break;
        case timeStampArea < 1000 * 60 * 60 * 12 && timeStampArea >= 1000 * 60 * 60 * 6:
            result = extractionData(option, sliceData, 300, color);
            break;
        case timeStampArea < 1000 * 60 * 60 * 6 && timeStampArea >= 1000 * 60 * 60 * 3:
            result = extractionData(option, sliceData, 180, color);
            break;
        case timeStampArea < 1000 * 60 * 60 * 3 && timeStampArea >= 1000 * 60 * 60:
            result = extractionData(option, sliceData, 60, color);
            break;
        case timeStampArea < 1000 * 60 * 60 && timeStampArea >= 1000 * 60 * 30:
            result = extractionData(option, sliceData, 30, color);
            break;
        case timeStampArea < 1000 * 60 * 30 && timeStampArea >= 1000 * 60 * 10:
            result = extractionData(option, sliceData, 15, color);
            break;
        case timeStampArea < 1000 * 60 * 10 && timeStampArea >= 1000 * 60 * 5:
            result = extractionData(option, sliceData, 10, color);
            break;
        case timeStampArea < 1000 * 60 * 5 && timeStampArea >= 1000 * 60:
            result = extractionData(option, sliceData, 5, color);
            break;
        default:
            result = extractionData(option, sliceData, 3, color);
            break;
    }

    const arr = option.data.map(it => it.y);
    const min = Math.min(...arr);
    const max = Math.max(...arr);
    const differ = max - min;
    const ticks = [min];
    for (let index = 1; index < 6; index += 1) {
        ticks[index] = Math.round((differ * index) / 5 + min);
    }
    // 计算yScale
    option.axis.yAxis.scale = {
        min,
        ticks,
    };

    // 最后一项添加24:00
    if (areaData[1] === 1) {
        result.data.push({
            x: '24:00',
            y: null,
            s: result.data[0].s,
        });
    }
    option.data = result.data;
    return option;
}



</script>