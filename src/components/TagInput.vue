<template>
  <div class="tag-input form-control">
    <span v-for="tag in tags" class="tag-input-tag">
      <span>{{ tag }}</span>
      <button type="button" class="tag-input-remove" @click="removeTag(tag)">×</button>
    </span>

    <input class="tag-input-text" type="text" id="tags" placeholder="Add a tag…"
           @keydown.backspace="handleTagBackspace"
           @keydown.enter.prevent="addTag"
           v-model="newTag">
  </div>
</template>

<script>
  export default {
    model: {
      prop: 'tags',
      event: 'update'
    },
    props: ['tags'],
    data () {
      return {
        newTag: ''
      }
    },
    methods: {
      addTag () {
        // Prevent adding empty or duplicate tags
        if (this.newTag.length === 0 || this.tags.includes(this.newTag)) {
          return
        }

        // Add the new tag to the list of tags
        this.$emit('update', [...this.tags, this.newTag]) // Spread syntax: https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Operators/Spread_syntax
        this.newTag = ''
      },
      removeTag (tag) {
        // Remove the selected tag from the list
        this.$emit('update', this.tags.filter(t => t !== tag)) // arr.filter(callback[, thisArg])
        // this.$emit('update', this.tags.filter(function (t) {
        //   return t !== tag
        // }))
      },
      handleTagBackspace (e) {
        if (this.newTag.length === 0) {
          // Remove the last tag from the list
          this.$emit('update', this.tags.slice(0, -1)) // arr.slice([begin[, end]])
        }
      }
    }
  }
</script>

<style lang="scss" scoped>
  .tag-input {
    display: flex;
    flex-wrap: wrap;
    padding-bottom: 0.125em;
    padding-top: 0.625em;
  }

  .tag-input-tag {
    align-items: center;
    background-color: #7fdbff;
    border-radius: 0.25em;
    color: #001f3f;
    display: inline-flex;
    line-height: 1;
    margin-bottom: 0.5em;
    margin-right: 0.75em;
    padding: 0.375em 0.5em;
    user-select: none;
  }

  .tag-input-remove {
    background-color: transparent;
    border: 0;
    color: #0074d9;
    cursor: pointer;
    margin-left: 0.25em;
    outline: 0;
    padding: 0;
  }

  .tag-input-text {
    border: 0;
    flex: 1;
    margin-bottom: 0.5em;
    min-width: 10em;
    outline: 0;
    padding-bottom: 0.125em;
    padding-top: 0.125em;
  }
</style>
