<template>
    <div>
        <el-tree :data="treeData" empty-text="暂无数据" class="cus_tree">
            <template #default="{node, data}">
                <VueDraggableNext :list="data.children" :key="data.label"
                @drag="m"
                @start="startDraggable(data.label, data.type)" @end="endDraggable(data.type)" :disabled="data.parent">
                    <div style="position:relative;" :class="{isdragging:state.isDragging, cursor_move:!data.parent}">
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
    let titleColor = ref('')
    let state : State = inject('state')!

    const updateState = ()=> {
        state.isDragging = isDragging.value;
        state.draggingLabel = draggingLabel.value;
        state.titleColor =  titleColor.value
    }

    function startDraggable(data:string, type:number){
        isDragging.value = true;
        draggingLabel.value = data

        titleColor.value = type == 2 ? 'yellow' : 'aquamarine';
        updateState();
    }

    function endDraggable(type:number){
        isDragging.value = false;
        updateState()

        titleColor.value = type == 2 ? 'yellow' : 'aquamarine';
        state.copy(state.mouseX, state.mouseY, state.draggingLabel, titleColor.value)
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
    .cursor_move{
        cursor: move;
    }
</style>