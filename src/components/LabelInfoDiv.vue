<template>
    <div class="dragging-preview" :style="{ top: `${mouseY}px`, left: `${mouseX}px` }">
        <div class="top" :class="titleColor">
            {{ label }}
        </div>
        <div class="content">
            <slot></slot>
        </div>
    </div>
</template>
<script setup lang='ts'>
    defineOptions({
        name: 'LabelInfoDiv'
    })

    defineProps(['mouseX', 'mouseY', 'label', 'titleColor'])
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
            // background-color: aquamarine;
            text-align: center;
        }

        .content{
            width: 100%;
            height: calc(100% - 10px);
            background-color: #FFFFFF;
            display: flex;
            align-items: center;
            justify-content: center;
        }
    }

    .aquamarine{
        background-color: aquamarine;
    }

    .yellow{
        background-color: rgb(252,223,184)
    }
</style>