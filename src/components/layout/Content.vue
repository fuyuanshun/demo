<template>
    <div class="content">
        <!-- <VueDraggableNext :list="items" item-key="id">
            <div class="draggable-item" v-drag>
            xx
            </div>
        </VueDraggableNext> -->
    </div>
</template>
<script setup lang='ts'>
import { VueDraggableNext } from 'vue-draggable-next'
import { ref } from 'vue'
defineOptions({
    name: 'Content'
})

const items = ref([])


</script>
<style scoped lang='scss'>
.content {
    width: calc(100% - var(--navigate_width) - 200px);
    height: 100%;
    background-color: rgb(255, 255, 255);

    // .draggable-item {
    //     padding: 10px;
    //     margin: 5px;
    //     background-color: #f0f0f0;
    //     border: 1px solid #ccc;
    //     cursor: move; /* 设置鼠标指针为移动 */
    // }
}

</style>