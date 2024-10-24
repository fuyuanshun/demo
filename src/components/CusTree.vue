<template>
    <div>
        <el-tree :data="treeData" empty-text="暂无数据" class="cus_tree">
            <template #default="{node, data}">
                <VueDraggableNext :list="data.children" :key="data.label"
                @move="cg"
                @start="startDraggable(data.label)" @end="endDraggable" :disabled="data.parent">
                    <div style="position:relative">
                        {{ data.label }}
                    </div>
                </VueDraggableNext>
            </template>
        </el-tree>
        <div v-if="isDragging" class="dragging-preview" :style="{ top: `${mouseY}px`, left: `${mouseX}px` }">
            <div class="top">
                {{ draggingLabel }}
            </div>
            <div class="content">

            </div>
        </div>
    </div>
</template>
<script setup lang='ts'>
    import { VueDraggableNext } from 'vue-draggable-next'
    import { ref } from 'vue'
    defineOptions({
        name: 'CusTree'
    })
    defineProps({
        treeData:Array
    })

    let isDragging = ref(false);
    let mouseX = ref(10)
    let mouseY = ref(10)
    let draggingLabel = ref('');

    function startDraggable(data:string){
        isDragging.value = true;
        draggingLabel.value = data
    }

    function endDraggable(){
        isDragging.value = false;
        console.log(mouseX.value, mouseY.value)
    }

    function cg(){
        console.log("....")
    }
</script>
<style scoped lang='scss'>
    .dragging-preview {
        position: absolute;
        width:120px;
        height:100px;
        pointer-events: none; /* 使其不干扰鼠标事件 */
        display: flex;
        flex-direction: column;
        box-shadow: 1px 1px 3px gray;
        border-radius: 10px;
        overflow: hidden;

        .top{
            width: 100%;
            height: 20px;
            background-color: aquamarine;
            text-align: center;
        }

        .content{
            width: 100%;
            height: calc(100% - 10px);
            background-color: #FFFFFF;
        }
    }
</style>