<template>
  <div v-show="active" :id="hash">
    <slot/>
  </div>
</template>

<script>
  export default {
    data () {
      return {
        active: false
      }
    },
    computed: {
      // to select exact tab
      hash () {
        return `${this.name.toLowerCase().replace(/ /g, '-')}` // customize to show hash
      }
    },
    props: {
      name: {
        required: true,
        type: String
      }
    }
  }
</script>

<style scoped>

</style>