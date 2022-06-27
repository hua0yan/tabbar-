<template>
  <div>
    <table class="table table-bordered table-stripped">
      <!-- 表格标题区域 -->
      <thead>
        <tr>
          <slot name="header"></slot>
        </tr>
      </thead>
      <!-- 表格主体区域 -->
      <tbody>
        <tr v-for="item in goosList" :key="item.id">
         <slot name="body" :item="item"></slot>
        </tr>
      </tbody>
    </table>
  </div>
</template>

<script>
export default {
  props: {
    goosList: {
      type: Array,
      required: true
    }
  }
}
</script>

<style>
</style>
