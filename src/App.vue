<template>
  <div id="app">
    <div class="container mt-3">
      <h1>Vue.js tag input component</h1>
      <hr class="mb-4">

      <new-thread-form></new-thread-form>
    </div>
  </div>
</template>

<script>
  import NewThreadForm from './components/NewThreadForm.vue'

  export default {
    components: {
      newThreadForm: NewThreadForm
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
