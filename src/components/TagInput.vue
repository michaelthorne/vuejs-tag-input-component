<script>
  export default {
    render () {
      return this.$scopedSlots.default({
        tags: this.tags,
        removeTag: this.removeTag,
        inputBindings: {
          value: this.newTag
        },
        inputEventHandlers: {
          input: (e) => { this.newTag = e.target.value },
          keydown: (e) => {
            if (e.keyCode === 8) {
              this.handleTagBackspace()
            }
            if (e.keyCode === 13) {
              e.preventDefault()
              this.addTag()
            }
          }
        }
      })
    },
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
