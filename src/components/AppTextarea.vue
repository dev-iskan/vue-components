<template>
  <textarea
      v-bind="$attrs"
      :name="name" 
      :id="name" 
      class="form-control"
      :value="value"
      :rows="rows"
      @input="$emit('input', $event.target.value)"
    >
  </textarea>

</template>

<script>
  export default {
    props: {
      name: {
        required: true,
        type: String
      },
      value: {
        required: false,
        type: String,
        default: ''
      }
    },
    computed: {
      rows () {
        return Math.max(5, this.value.split('\n').length)
      }
    }
  }
</script>

<style scoped>

</style>