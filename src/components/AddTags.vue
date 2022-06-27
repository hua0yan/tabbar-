<template>
  <div>
    <button
      class="btn btn-primary btn-sm"
      v-if="AddTags"
      @click="AddTags = false"
    >
      +Tag
    </button>
    <input
      type="text"
      v-else
      @blur="AddTagsitem"
      v-focus
      style="width: 50px"
      v-model="tags"
      @keydown.enter="AddTagsitem"
    />
  </div>
</template>

<script>
export default {
  data () {
    return {
      AddTags: true,
      tags: ''
    }
  },
  directives: {
    focus: {
      inserted (el) {
        el.focus()
      }
    }
  },
  methods: {
    AddTagsitem () {
      this.AddTags = true
      if (this.tags.trim() !== '') {
        this.$emit('Add-tags', this.tags)
      }
      this.tags = ''
    }
  }
}
</script>

<style></style>
