<template>
    <animation-pie :data="data"></animation-pie>
</template>

<script setup lang="ts">
import { ref } from 'vue';


const data = ref([
    { gbx: '机电设备故障', encodey: 12 },
    { gbx: '材料供应超时', encodey: 15 },
    { gbx: '大块矸石堵仓', encodey: 12 },
    { gbx: '提升系统停机', encodey: 15 },
    { gbx: '个人违章违纪', encodey: 16 },
]);

const testTheme = ref('blueDark.circular');
</script>
<style scoped lang="scss"></style>
