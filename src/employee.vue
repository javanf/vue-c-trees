<template>
    <div class="tree-menu">
        <employee-list :data="data"></employee-list>
    </div>
</template>
 
<script>
var myData = [
    {
        'name': '研发部',
        'children': [{
          id: 100,
          name: 'James'
        },{
            'name': 'Web前端',
            'children': [{
                id: 101,
                name: 'Javanx'
            }, {
                id: 102,
                name: 'Mark'
            }, {
                id: 103,
                name: 'Rool'
            }]
        }, {
            name: '测试',
            'children': [{
              id: 104,
              name: 'Finny'
            }, {
              id: 105,
              name: 'Jesse'
            }]
        }, {
            name: '后台',
            'children': [{
                name: 'Java后台',
                'children': [{
                  id: 106,
                  name: 'Owen'
                }, {
                  id: 107,
                  name: 'Carry'
                }]
            }, {
                name: '运维',
                'children': [{
                  id: 108,
                  name: 'Kim'
                }]
            }]
        }]
    }, {
        name: '综合管理部',
        'children': [{
          id: 109,
          name: 'Amiee'
        },{
            name: '财务',
            'children': [{
              id: 110,
              name: 'Firse'
            },{
              id: 111,
              name: 'Jake'
            }]
        }, {
            name: '人事',
            'children': [{
              id: 112,
              name: 'Firse'
            },{
              id: 113,
              name: 'Jake'
            }]
        }]
    }
];

 
import employeeList from './employee-list'
export default {
    components: {
        employeeList
    },
    data() {
        return {
            data: myData
        }
    }
}
</script>
