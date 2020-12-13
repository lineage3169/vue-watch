<template>
    <div>
        
    </div>
</template>
<script>
export default {
    name: 'DeepWatch',
    props: ['propsData'],
    data() {
        return {
            ip: {
                a: 0,
                b: 0,
                c: 0,
                d: 0,
            }
        }
    },
    watch: {
        propsData: {
            handler: function (val, oldVal) { 
                // 深層監視
                // val => 新資料
                // oldVal => 前一筆資料
                console.log('new:',val)
                console.log('old:',oldVal)
            },
            deep: true
        },
        'ip.a': function (data,oldData) {
            // 針對object的某個key 做watch
            console.log(data,oldData)
        }
    }
}
</script>