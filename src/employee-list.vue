<template>
    <div class="tree-menu">
        <ul v-for="item in data">
            <c-employee-item :data="item"></c-employee-item>
        </ul>
    </div>
</template>
 
<script>


import cEmployeeItem from './employee-item'
export default {
    props: {
        data: {
            type: [Object, Array],
            required: true
        }
    },
    components: {
        cEmployeeItem
    }
}
</script>