<template>
    <div class="main_container">
        <div class="header">

        </div>
        <div class="content_container">
            <div class="navigate_tab">
                
            </div>
            <div class="content">

            </div>
        </div>
        <div class="footer">

        </div>
    </div>
</template>
<script setup lang='ts'>
    defineOptions({
        name: 'Layout'
    })
</script>
<style scoped lang='scss'>
    .main_container{
        width: 100vw;
        height: 100vh;

        .header {
            height: var(--header_height);
            background-color: rgb(34, 15, 63);
        }

        .content_container {
            display: flex;
            width: 100%;
            height: calc(100vh - var(--header_height));

            .navigate_tab{
                width: var(--navigate_height);
                height: 100%;
                background-color: rgb(249, 248, 250);
            }
            .content{
                width: calc(100% - var(--navigate_height));
                height: 100%;
                background-color: rgb(255, 255, 255);
            }
        }

    }
    
</style>