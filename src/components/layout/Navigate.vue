<template>
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
</template>
<script setup lang='ts'>
import { ref } from 'vue'
defineOptions({
    name: 'Navigate'
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
</style>