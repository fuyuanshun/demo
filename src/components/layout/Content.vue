<template>
    <div class="content" :class="{isdragging:isDraggable}">
    </div>
</template>
<script setup lang='ts'>
    defineOptions({
        name: 'Content'
    })

    defineProps(['isDraggable'])

</script>
<style scoped lang='scss'>
    .content {
        width: calc(100% - var(--navigate_width) - 200px);
        height: 100%;
        background-color: rgb(255, 255, 255);
        margin: 0px 10px;
    }

    .isdragging{
        box-shadow: 1px 1px 10px rgb(100, 99, 99);
    }

</style>