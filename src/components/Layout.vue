<template>
    <div class="main_container" ref="container">
        <Header></Header>
        <div class="content_container">
            <Navigate></Navigate>
            <Content :isDraggable="state.isDragging"></Content>
            <ComponentInfo></ComponentInfo>
        </div>
        <!-- 用于拖拽过程中的展示 -->
        <component v-if="state.isDragging" :is="LabelInfoDiv" 
        :mouseX="state.mouseX" :mouseY="state.mouseY" :label="state.draggingLabel"
        :titleColor="state.titleColor">
            <template #default>
                <ul>
                    <li>温度</li>
                    <li>湿度</li>
                    <li>噪音</li>
                </ul>
            </template>
        </component>

        <!-- 用于拖拽完成后展示 -->
        <component v-for="comp in comps" :is="LabelInfoDiv" ref="originDiv" :mouseX="comp.x" :mouseY="comp.y" :label="comp.content" :titleColor="comp.titleColor">
            <template #default>
                <ul>
                    <li>温度</li>
                    <li>湿度</li>
                    <li>噪音</li>
                </ul>
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
import type State from '../types/State.ts'
import LabelInfoDiv from './LabelInfoDiv.vue';

defineOptions({
    name: 'Layout'
})

const state:State = reactive({
    isDragging:false,
    draggingLabel:'',
    mouseX:0,
    mouseY:0,
    copy:copy,
    titleColor:''
})

const comps : any = ref([])

provide('state', state)

const originDiv = ref()
const container = ref();

function copy(x:number, y:number, draggingLabel:string, titleColor:String){
    const newComponent = {
        content:draggingLabel,
        x:x,
        y:y,
        titleColor:titleColor
    }
    if (x > 170 && y > 40) {
        comps.value.push(newComponent)
    }
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