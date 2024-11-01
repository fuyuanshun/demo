<template>
    <div class="main_container" ref="container">
        <Header></Header>
        <div class="content_container">
            <Navigate></Navigate>
            <Content></Content>
            <ComponentInfo></ComponentInfo>
        </div>
<!-- 
        <div ref="originDiv" v-if="state.isDragging" class="dragging-preview" :style="{ top: `${state.mouseY}px`, left: `${state.mouseX}px` }">
            <div class="top">
                {{ state.draggingLabel }}
            </div>
            <div class="content">
                <ul>
                    <li>温度</li>
                    <li>湿度</li>
                    <li>噪音</li>
                </ul>
            </div>
        </div> -->
        <component v-for="comp in comps" :is="LabelInfoDiv" ref="originDiv" :mouseX="comp.x" :mouseY="comp.y" :label="comp.content">
            <template #default="">
                <div>
                    
                </div>
            </template>
        </component>
    </div>
</template>
<script setup lang='ts'>
import ComponentInfo from './layout/ComponentInfo.vue';
import Content from './layout/Content.vue';
import Header from './layout/Header.vue';
import Navigate from './layout/Navigate.vue';
import { ref, reactive, provide } from 'vue'
<<<<<<< Updated upstream
import State from '../types/State.ts'
=======
import type State from '../types/State.ts'
import LabelInfoDiv from './LabelInfoDiv.vue';
>>>>>>> Stashed changes

defineOptions({
    name: 'Layout'
})

const state:State = reactive({
    isDragging:false,
    draggingLabel:'',
    mouseX:0,
    mouseY:0,
    copy:copy
})

const comps : any = ref([])

provide('state', state)

const originDiv = ref()
const container = ref();

<<<<<<< Updated upstream
function copy(){
    if (originDiv.value) {
        const clone = originDiv.value.cloneNode(true); // 克隆原始 div
        container.value.appendChild(clone); // 将克隆的元素添加到目标容器
=======
function copy(x:number, y:number, draggingLabel:string){
    // if (originDiv.value && x > 170 && y > 40) {
    //     const clone = originDiv.value.cloneNode(true); // 克隆原始 div
    //     container.value.appendChild(clone); // 将克隆的元素添加到目标容器
    // }
    const newComponent = {
        content:draggingLabel,
        x:x,
        y:y
>>>>>>> Stashed changes
    }
    comps.value.push(newComponent)
}

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
}
</style>