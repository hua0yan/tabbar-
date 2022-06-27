<template>
  <div id="app">
    <MyHeader title="tabbar案例" />
    <component :is="componentchange"></component>
    <MyFooter
      :tabList="tabList"
      @change-Components="changeComponent($event)"
    ></MyFooter>
  </div>
</template>

<script>
import MyFooter from './components/MyFooter.vue'
import MyHeader from './components/MyHeader.vue'
import MyGoodsList from './views/MyGoodsList.vue'
import MyGoodsSearch from './views/MyGoodsSearch.vue'
import MyUserInfo from './views/MyUserInfo.vue'
export default {
  components: {
    MyHeader,
    MyFooter,
    MyGoodsList,
    MyGoodsSearch,
    MyUserInfo
  },
  data () {
    return {
      tabList: [
        {
          iconText: 'icon-shangpinliebiao',
          text: '商品列表',
          componentName: 'MyGoodsList'
        },
        {
          iconText: 'icon-sousuo',
          text: '商品搜索',
          componentName: 'MyGoodsSearch'
        },
        {
          iconText: 'icon-user',
          text: '我的信息',
          componentName: 'MyUserInfo'
        }
      ],
      componentchange: 'MyGoodsList'
    }
  },
  methods: {
    changeComponent (componentName) {
      this.componentchange = componentName
    }
  }
}
</script>

<style>
#app{
  margin: 50px 0;
}
</style>
