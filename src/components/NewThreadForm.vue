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

              <tag-input v-model="tags">
                <div class="form-control tag-input" slot-scope="{ tags, removeTag, inputBindings, inputEventHandlers }">
                  <span class="tag-input-tag" v-for="tag in tags">
                    <span>{{ tag }}</span>
                    <button type="button" class="tag-input-remove" @click="removeTag(tag)">×</button>
                  </span>

                  <input class="tag-input-text" type="text"
                         id="tags"
                         placeholder="Add a tag…"
                         v-on="inputEventHandlers"
                         v-bind="inputBindings">
                </div>
              </tag-input>
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
