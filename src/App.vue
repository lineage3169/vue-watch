<template>
  <div id="app">
    <table border>
      <thead>
        <tr>
          <th>名稱</th>
          <th>動作</th>
        </tr>
      </thead>
      <tbody>
        <tr v-for="(item,index) in product" :key="index">
          <td>{{item.name}}</td>
          <td>
            <button @click.stop="edit(item)">編輯</button>
          </td>
        </tr>
      </tbody>
    </table>
    <EditModal :propsData="selectedItem" @onEdit="saveEditData"/>
    <DeepWatch :propsData="demoObj"/>
    <button @click="changeData()">
      Change Data Value
    </button>
  </div>
</template>

<script>
import EditModal from '@/components/edit-modal';
import DeepWatch from '@/components/deep-watch'
export default {
  name: 'App',
  components: {
    EditModal,DeepWatch
  },
  data() {
    return {
      str: 'demo',
      product: [
        {
          id: 0,
          name: '鬼滅之刃-T',
          size: 'L',
          price: 799,
          amount: 10
        },
        {
          id: 1,
          name: '鋼彈UC-T',
          size: 'M',
          price: 419,
          amount: 10
        },
        {
          id: 2,
          name: '咒術迴戰-T',
          size: 'XS',
          price: 999,
          amount: 5
        }
      ],
      selectedItem: null,
      demoObj: {
        a: 1,
        b: 2
      }
    }
  },
  methods: {
    deepCopy(data) {
      return JSON.parse(JSON.stringify(data))
    },
    edit(data) {
      this.selectedItem = this.deepCopy(data)
    },
    saveEditData(data) {
      // 接子傳父的值
      this.product = this.product.map(item => {
        if(item.id === data.id)
          return data
        return item
      })
    },
    changeData() {
      this.demoObj.b = 456
    }
  },
}
</script>