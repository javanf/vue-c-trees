## 前言
Vue开发一个简洁树形结构组件，组件递归组件自身，生成dom。

## 预览图

![web秀](http://cdn.javanx.cn/wp-content/themes/lensnews2.2/images/post/20181122171310.gif)

## 代码预览
### tree-item
通过`computed`计算`hasChild`属性，判断当前级别是否还有`children`，有继续循环组件，依次执行下去，直到没有找到`children`结束。点击每个item时，也判断是否还有`children`，有则展开。
```html
<template>
    <li>
        <span @click="toggle">
            <em v-if="hasChild" class="icon">{{open ? '-' : '+'}}</em>
            <em v-if="!hasChild" class="icon file-text"></em>
            {{ data.name }}
        </span>
        <ul v-show="open" v-if="hasChild">
            <tree-item v-for="(item, index) in data.children" :data="item" :key="index"></tree-item>
        </ul>
    </li>
</template>
 
<script>
export default {
    name: 'TreeItem',
    props: {
        data: {
            type: [Object, Array],
            required: true
        }
    },
    data() {
        return {
            open: false
        }
    },
    computed: {
        hasChild() {
            return this.data.children && this.data.children.length
        }
    },
    methods: {
        toggle() {
            if(this.hasChild) {
                this.open = !this.open
            }
        }
    }
}
</script>
 
<style>
ul {
    list-style: none;
    margin: 10px 0;
}
li {
    padding: 3px 0;
}
li > span {
    cursor: pointer;
    font-size: 14px;
    line-height: 20px;
}
li > span:visited{
    background: #fff;
}
em.icon {
    display: inline-block;
    width: 20px;
    height: 20px;
    margin-right: 5px;
    background-repeat: no-repeat;
    vertical-align: middle;
}
.tree-menu li {
    line-height: 1.5;
}
</style>
```

### tree
```html
<template>
    <div class="tree-menu">
        <ul v-for="item in data">
            <c-tree-item :data="item"></c-tree-item>
        </ul>
    </div>
</template>
 
<script>


import cTreeItem from './tree-item'
export default {
    props: {
        data: {
            type: [Object, Array],
            required: true
        }
    },
    components: {
        cTreeItem
    }
}
</script>
```
## 快速开始

``` bash
# 安装
npm install vue-c-tree -S
```


```javascript
// 引入模块
import cTree from 'vue-c-tree'
 
Vue.use(cTree)
```

## 模拟数据
```json
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
```

```html
<template>
   <cTree :data="myData"></cTree>
</template>
```

> 切记：你的数据必须要有结尾，不能无限循环下去，会导致内存泄漏。


## 源码地址
github地址： [vue-h5-trees](https://github.com/javanf/vue-c-trees)
