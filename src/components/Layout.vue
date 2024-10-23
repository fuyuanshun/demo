<template>
    <div class="main_container">
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
        <div class="content_container">
            <div class="navigate_tab">
                <div class="navigate_top">
                    <h4>数据表</h4>
                    <ul>
                        <li></li>
                        <li></li>
                        <li></li>
                    </ul>
                </div>
                <div class="navigate_bottom">
                    <h4>节点库</h4>
                    <ul>
                        <li></li>
                        <li></li>
                        <li></li>
                    </ul>
                </div>
            </div>
            <div class="content">
            </div>
        </div>
    </div>
</template>
<script setup lang='ts'>
    import SVG from '@/components/svg/SVG.vue'

    defineOptions({
        name: 'Layout'
    })
</script>
<style scoped lang='scss'>
    .main_container{
        width: 100vw;
        height: 100vh;

        .header {
            display: flex;
            height: var(--header_height);
            color: white;
            background-color: rgb(34, 15, 63);
            justify-content: space-between;

            .hand:hover{
                cursor: pointer;
            }

            .header_left {
                display: flex;
                width: 120px;
                height: 100%;
                align-items: center;
                justify-content: space-evenly;

                .go_back{
                    margin-right:10px;
                }
                
                .select_source{
                    // margin-left:5px;
                }
            }

            .header_right{
                display: flex;
                width: 235px;
                height: 100%;
                align-items: center;
                justify-content: space-evenly;

                .btn {
                    color:white;
                    width:55px;
                    height:23px;
                    border-radius: 5px;
                    border:none;
                    background-color: rgb(81, 153, 246);
                    transition: all .3s linear;
                }
                .btn:hover {
                    cursor: pointer;
                    background-color: rgb(45, 105, 184);;
                }
            }
        }

        .content_container {
            display: flex;
            width: 100%;
            height: calc(100vh - var(--header_height));

            .navigate_tab{
                display: flex;
                width: var(--navigate_width);
                height: 100%;
                flex-direction: column;
                justify-content: space-between;
                background-color: rgb(249, 248, 250);
                padding-left: 10px;
                padding-right: 10px;

                h4{
                    color: white;
                    width:100%;
                    background-color: rgb(31, 16, 60);
                    text-align: center;
                }

                .navigate_top {
                    margin-top: 10px;
                    width:100%;
                    height: 45%;
                }

                .navigate_bottom{
                    margin-bottom: 10px;
                    width:100%;
                    height: 45%;
                }
            }
            .content{
                width: calc(100% - var(--navigate_width));
                height: 100%;
                background-color: rgb(255, 255, 255);
            }
        }

    }
    
</style>