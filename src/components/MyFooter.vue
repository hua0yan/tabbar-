<template>
  <div class="my-tab-bar">
    <div
      :class="['tab-item', { current: changeIndex === index }]"
      v-for="(item, index) in tabList"
      :key="index"
      @click="changeComponent(item.componentName, index)"
    >
      <!-- 图标 -->
      <span :class="`iconfont ${item.iconText}`" class="text"></span>
      <!-- 文字 -->
      <span>{{ item.text }}</span>
    </div>
  </div>
</template>

<script>
import '../assets/fonts/iconfont.css'
export default {
  props: {
    tabList: {
      type: Array,
      required: true
    }
  },
  data () {
    return {
      changeIndex: 0
    }
  },
  methods: {
    changeComponent (componentName, index) {
      this.changeIndex = index
      this.$emit('change-Components', componentName)
    }
  }
}
</script>

<style lang="less" scoped>
.my-tab-bar {
  position: fixed;
  left: 0;
  bottom: 0;
  width: 100%;
  height: 50px;
  border-top: 1px solid #ccc;
  display: flex;
  justify-content: space-around;
  align-items: center;
  background-color: white;
  .tab-item {
    display: flex;
    flex-direction: column;
    align-items: center;
  }
}

.current {
  color: #1d7bff;
  .text {
    color: #1d7bff;
  }
}
</style>
