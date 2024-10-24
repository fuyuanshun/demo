<template>
    <div class="header">
        <div class="header_left">
            <div class="hand go_back">
                <SVG width="18px" height="18px" iconName="back"></SVG>
            </div>
            <div class="select_source">数据源</div>
        </div>
        <div class="header_right">
            <div class="hand left_arrow">
                <SVG width="18px" height="18px" iconName="left"></SVG>
            </div>
            <div class="hand right">
                <SVG width="18px" height="18px" iconName="right"></SVG>
            </div>
            <div class="hand download">
                <SVG width="18px" height="18px" iconName="download" fillColor="#FFFFFF"></SVG>
            </div>
            <div class="save">
                <button class="btn">保存</button>
            </div>
            <div class="save_as">
                <button class="btn">另存为</button>
            </div>
        </div>
    </div>
</template>
<script setup lang='ts'>
import SVG from '@/components/svg/SVG.vue'
defineOptions({
    name: 'Header'
})
</script>
<style scoped lang='scss'>
.header {
    display: flex;
    height: var(--header_height);
    color: white;
    background-color: rgb(34, 15, 63);
    justify-content: space-between;

    .hand:hover {
        cursor: pointer;
    }

    .header_left {
        display: flex;
        width: 120px;
        height: 100%;
        align-items: center;
        justify-content: space-evenly;

        .go_back {
            margin-right: 10px;
        }

        .select_source::after {
            content: ""
        }
    }

    .header_right {
        display: flex;
        width: 235px;
        height: 100%;
        align-items: center;
        justify-content: space-evenly;

        .btn {
            color: white;
            width: 55px;
            height: 23px;
            border-radius: 5px;
            border: none;
            background-color: rgb(81, 153, 246);
            transition: all .3s linear;
        }

        .btn:hover {
            cursor: pointer;
            background-color: rgb(45, 105, 184);
            ;
        }
    }
}
</style>