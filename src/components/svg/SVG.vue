<template>
    <svg :width="width||'12px'" :height="height||'12px'">
        <use :xlink:href="'#icon-' + iconName" :width="width||'12px'" :height="height||'12px'" :fill="fillColor"></use>
    </svg>
</template>
<script setup lang='ts'>
    defineProps({
        width:String,
        height:String,
        iconName:String,
        fillColor:String
    })
</script>
<style scoped lang='scss'>
    
</style>