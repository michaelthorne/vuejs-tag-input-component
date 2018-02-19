<template>
  <div id="app">
    <div class="container mt-3">
      <h1>Vue.js tag input component</h1>
      <hr class="mb-4">

      <form>
        <fieldset class="form-group">
          <legend>Start a new discussion</legend>
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
                  <option value="">Please select…</option>
                  <option value="1">Finance</option>
                  <option value="2">Politics</option>
                  <option value="3">Sport</option>
                  <option value="4">Weather</option>
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
                <tag-input></tag-input>
              </div>
            </div>
          </div>

          <div class="row">
            <div class="col-md">
              <div class="form-group">
                <button type="submit" class="btn btn-primary btn-lg">Start discussion</button>
              </div>
            </div>
          </div>
        </fieldset>
      </form>
    </div>
  </div>
</template>

<script>
  import TagInput from './components/TagInput.vue'

  export default {
    components: {
      tagInput: TagInput
    },
    data () {
      return {}
    }
  }
</script>

<style lang="scss" scoped>
  .container {
    max-width: 45em; /* 720 / 16 */
  }
</style>
