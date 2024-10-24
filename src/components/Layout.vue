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
                <div class="search_div">
                    <input type="text" class="search" placeholder="请输入关键词搜索...">
                </div>
                <h4>数据表</h4>
                <div class="navigate_top">
                    <el-tree :data="dataTable" empty-text="暂无数据" class="cus_tree"></el-tree>
                </div>
                <h4>节点库</h4>
                <div class="navigate_bottom">
                    <el-tree :data="dataNode" empty-text="暂无数据" class="cus_tree"></el-tree>
                </div>
            </div>
            <div class="content">
            </div>
        </div>
    </div>
</template>
<script setup lang='ts'>
import SVG from '@/components/svg/SVG.vue'
import { ref } from 'vue'

defineOptions({
    name: 'Layout'
})

let dataTable = ref([
    {
        'label': '系统数据源',
        'children': [
            {
                'label': '表一'
            },
            {
                'label': '表二'
            }
        ],
    },
    {
        'label': '本地数据源',
        'children': [
        ],
    }
])
let dataNode = ref([
    {
        'label': '计算',
        children: [
            {
                'label': '加法',
            },
            {
                'label': '减法',
            },
            {
                'label': '乘法',
            },
            {
                'label': '除法',
            },
            {
                'label': '方差',
            },
            {
                'label': '公式',
            }
        ]
    },
    {
        'label': '数据处理',
        children: [
            {
                'label': '四舍五入'
            },
            {
                'label': '保留小数'
            },
            {
                'label': '拼接'
            },
            {
                'label': '拆分'
            },
            {
                'label': '去重'
            },
            {
                'label': '单位换算'
            }
        ]
    },
    {
        'label': '数据比较',
        children: [
            {
                'label': '等于'
            },
            {
                'label': '不等于'
            },
            {
                'label': '大于'
            },
            {
                'label': '小于'
            }
        ]
    },
    {
        'label': '排序',
        children: [
            {
                'label': '升序'
            },
            {
                'label': '降序'
            }
        ]
    },
    {
        'label': '规则关系',
        children: [
            {
                'label': '且'
            },
            {
                'label': '或'
            },
            {
                'label': '序列'
            },
            {
                'label': '分支'
            },
        ]
    },
    {
        'label': '个人组件',
        children: [
            {
                'label': '字段'
            },
            {
                'label': '表'
            }
        ]
    }
])
</script>
<style scoped lang='scss'>
.main_container {
    width: 100vw;
    height: 100vh;

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

    .content_container {
        display: flex;
        //减去padding
        width: calc(100% - 20px);
        height: calc(100vh - var(--header_height) - 20px);
        padding: 10px;

        .navigate_tab {
            display: flex;
            width: calc(var(--navigate_width) - 20px);
            height: calc(100% - 20px);
            padding: 10px;
            flex-direction: column;
            justify-content: space-between;
            background-color: rgb(249, 248, 250);

            .search {
                padding: 3px;
                width: calc(100% - 6px);
                height: 14px;
                transition: .3s all linear;
                background: url('@/assets/svgs/search.svg') no-repeat right center / 16px 16px;
                background-color: #FFFFFF;
                border: 1px solid gray;
            }

            .search:focus {
                outline: none;
            }

            h4 {
                color: white;
                width: 100%;
                background-color: rgb(31, 16, 60);
                text-align: center;
                margin-top: 10px;
            }
            .navigate_top:hover::-webkit-scrollbar-thumb{
                background-color: #E0E5EC;
            }

            .navigate_bottom:hover::-webkit-scrollbar-thumb{
                background-color: #E0E5EC;
            }

            .navigate_top {
                margin-top: 10px;
                width: 100%;
                height: 45%;
                overflow: auto;
            }

            .navigate_bottom {
                margin-bottom: 10px;
                width: 100%;
                height: 45%;
                overflow: auto;
            }
        }

        .content {
            width: calc(100% - var(--navigate_width));
            height: 100%;
            background-color: rgb(255, 255, 255);
        }
    }

    .cus_tree{
        background-color: rgb(249, 248, 250);
    }

}
</style>