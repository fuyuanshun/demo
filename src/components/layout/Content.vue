<template>
    <div class="content">
    </div>
</template>
<script setup lang='ts'>
import {ref} from 'vue'
defineOptions({
    name: 'Content'
})
</script>
<style scoped lang='scss'>
.content {
    width: calc(100% - var(--navigate_width) - 200px);
    height: 100%;
    background-color: rgb(255, 255, 255);
}
</style>