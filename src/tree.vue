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