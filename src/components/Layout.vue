<template>
    <div class="main_container" @mousemove="changeMouse">
        <Header></Header>
        <div class="content_container">
            <Navigate></Navigate>
            <Content></Content>
            <ComponentInfo></ComponentInfo>
        </div>
    </div>
</template>
<script setup lang='ts'>
import ComponentInfo from './layout/ComponentInfo.vue';
import Content from './layout/Content.vue';
import Header from './layout/Header.vue';
import Navigate from './layout/Navigate.vue';
import { ref } from 'vue'

defineOptions({
    name: 'Layout'
})

const mouseX = ref(0)
const mouseY = ref(0)

function changeMouse(e:MouseEvent){
    // mouseX.value = e.clientX;
    // mouseY.value = e.clientY;
    // console.log(mouseX.value)
    // console.log(mouseY.value)
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