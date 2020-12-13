<template>
    <div v-if="editData" class="edit-modal">
        <p>名稱</p>
        <input v-model="editData.name" type="text">
        <p>尺寸</p>
        <input v-model="editData.size" type="text">
        <p>價格</p>
        <input v-model="editData.price" type="text">
        <p>數量</p>
        <input v-model="editData.amount" type="text">
        <br>
        <br>
        <button @click="save()">儲存</button>
    </div>
</template>
<script>
export default {
    name: 'EditModal',
    props: ['propsData'],
    data() {
        return {
            editData: null,
        }
    },
    methods: {
        save() {
            // 子傳父
            this.$emit('onEdit',this.editData)
        }
    },
    watch: {
        propsData(data) {
            // 值被改變時觸發
            this.editData = data
        },
    },
}
</script>