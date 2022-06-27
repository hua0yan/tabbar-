<template>
  <MyTags :goosList="goosList">
    <template #header>
      <th>#</th>
      <th>商品名称</th>
      <th>价格</th>
      <th>标签</th>
      <th>操作</th>
    </template>
    <template #body="{ item }">
      <td>{{ item.id }}</td>
      <td>{{ item.goods_name }}</td>
      <td>{{ item.goods_price }}</td>
      <td>
        <AddTags @Add-tags="Addtags($event, item.tags)" />
        <span
          class="badge bg-warning text-dark"
          v-for="(i, index) in item.tags"
          :key="index"
          style="margin-right: 5px"
          >{{ i }}</span
        >
      </td>
      <td>
        <button class="btn btn-danger btn-sm" @click="delGoods(item)">
          删除
        </button>
      </td>
    </template>
  </MyTags>
</template>

<script>
import axios from '../utils/request.js'
import MyTags from '../components/MyTags.vue'
import AddTags from '../components/AddTags.vue'
export default {
  components: { MyTags, AddTags },
  data () {
    return {
      goosList: []
    }
  },
  name: 'MyTable',
  created () {
    this.getGoodsList()
  },
  methods: {
    async getGoodsList () {
      const { data } = await axios({ url: '/api/goods' })
      console.log(data)
      this.goosList = data.data
    },
    Addtags (tagName, tags) {
      tags.push(tagName)
    },
    delGoods (i) {
      this.goosList = this.goosList.filter((item) => item !== i)
    }
  }
}
</script>

<style scoped lang="less">
.my-goods-list {
  .badge {
    margin-right: 5px;
  }
}
</style>
