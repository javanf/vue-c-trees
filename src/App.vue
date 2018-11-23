<template>
    <div class="tree-menu">
        <cTree :data="data"></cTree>
    </div>
</template>
 
<script>
var myData = [
    {
        'name': 'Web秀',
        'children': [{
            'name': 'web前端',
            'children': [{
                'name': 'CSS'
            }, {
                'name': 'JavaScript'
            }, {
                'name': 'Vue'
            }, {
                'name': '小程序'
            }, {
                'name': 'Three.js'
            }]
        }, {
            'name': '服务器'
        }, {
            'name': '工具类'
        }]
    }, {
        'name': '今日头条',
        'children': [{
            'name': '图片'
        }, {
            'name': '新闻',
            'children': []
        }]
    }, {
        'name': 'Angular'
    }
];

 
import cTree from './tree'
export default {
    components: {
        cTree
    },
    data() {
        return {
            data: myData
        }
    }
}
</script>