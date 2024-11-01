<template>
    <div>
        <el-tree :data="treeData" empty-text="暂无数据" class="cus_tree">
            <template #default="{node, data}">
                <VueDraggableNext :list="data.children" :key="data.label"
                @drag="m"
                @start="startDraggable(data.label)" @end="endDraggable" :disabled="data.parent">
                    <div style="position:relative;" :class="{cloned:data.isCloned}">
                        {{ data.label }}
                    </div>    
                </VueDraggableNext>
            </template>
        </el-tree>
    </div>
</template>
<script setup lang='ts'>
    import { VueDraggableNext } from 'vue-draggable-next'
    import { ref, inject } from 'vue'
    import type State from '../types/State.ts'

    defineOptions({
        name: 'CusTree'
    })
    defineProps({
        treeData:Array
    })

    let isDragging = ref(false);
    let draggingLabel = ref('');
    let state : State = inject('state')!

    const updateState = ()=> {
        state.isDragging = isDragging.value;
        state.draggingLabel = draggingLabel.value;
    }

    function startDraggable(data:string){
        isDragging.value = true;
        draggingLabel.value = data
        updateState();
    }

    function endDraggable(){
        isDragging.value = false;
        updateState()

        state.copy(state.mouseX, state.mouseY, state.draggingLabel)
    }

    function m(e:DragEvent){
        if(e.clientX == 0 && e.clientY == 0){
            return;
        }
        state.mouseX = e.clientX
        state.mouseY = e.clientY
    }
</script>
<style scoped lang='scss'>
    .cloned{
        color:transparent
    }
</style>