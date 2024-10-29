<template>
    <div class="main_container">
        <Header></Header>
        <div class="content_container">
            <Navigate></Navigate>
            <Content></Content>
            <ComponentInfo></ComponentInfo>
        </div>

        <div v-if="state.isDragging" class="dragging-preview" :style="{ top: `${state.mouseY}px`, left: `${state.mouseX}px` }">
            <div class="top">
                {{ state.draggingLabel }}
            </div>
            <div class="content">

            </div>
        </div>
    </div>
</template>
<script setup lang='ts'>
import ComponentInfo from './layout/ComponentInfo.vue';
import Content from './layout/Content.vue';
import Header from './layout/Header.vue';
import Navigate from './layout/Navigate.vue';
import { ref, reactive, provide } from 'vue'

defineOptions({
    name: 'Layout'
})

const state = reactive({
    isDragging:false,
    draggingLabel:'',
    mouseX:0,
    mouseY:0
})
provide('state', state)

</script>
<style scoped lang='scss'>
.main_container {
    width: 100vw;
    height: 100vh;

    .content_container {
        display: flex;
        //减去padding
        width: calc(100% - 20px);
        height: calc(100vh - var(--header_height) - 20px);
        padding: 10px;
    }

    .cus_tree{
        background-color: rgb(249, 248, 250);
    }


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
}
</style>