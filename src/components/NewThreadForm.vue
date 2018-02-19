<template>
  <div class="card">
    <h5 class="card-header">Start a new discussion</h5>
    <div class="card-body">
      <form @submit="submit">
        <div class="row">
          <div class="col-md">
            <div class="form-group">
              <label for="title">Title</label>
              <input type="text" class="form-control" id="title">
            </div>
          </div>

          <div class="col-md-4">
            <div class="form-group">
              <label for="category">Category</label>
              <select class="form-control" id="category">
                <option v-for="category in categories" :value="category.value">{{ category.label }}</option>
              </select>
            </div>
          </div>
        </div>

        <div class="row">
          <div class="col-md">
            <div class="form-group">
              <label for="message">Message</label>
              <textarea class="form-control" id="message" rows="3"></textarea>
            </div>
          </div>
        </div>

        <div class="row">
          <div class="col-md">
            <div class="form-group">
              <label for="tags">Tags</label>
              <tag-input v-model="tags"></tag-input>
            </div>
          </div>
        </div>

        <div class="row">
          <div class="col-md">
            <div class="form-group mb-0">
              <button type="submit" class="btn btn-primary btn-lg">Start discussion</button>
            </div>
          </div>
        </div>
      </form>
    </div>
  </div>
</template>

<script>
  import TagInput from '../components/TagInput.vue'

  export default {
    components: {
      tagInput: TagInput
    },
    data () {
      return {
        categories: [
          {
            label: 'Please select…',
            value: ''
          },
          {
            label: 'Entertainment',
            value: '1'
          },
          {
            label: 'Finance',
            value: '2'
          },
          {
            label: 'News',
            value: '3'
          },
          {
            label: 'Sport',
            value: '4'
          }
        ],
        tags: [
          'archive',
          'history',
          'interesting fact'
        ]
      }
    },
    methods: {
      submit () {}
    }
  }
</script>

<style lang="scss" scoped>
  .card-body {
    padding: 1em;
  }
</style>
