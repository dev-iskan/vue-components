<template>
<div>
  <input
      v-bind="$attrs"
      :type="inputType" 
      :name="name" 
      :id="name" 
      class="form-control"
      :value="value"
      @input="$emit('input', $event.target.value)"
    >
    <a v-if="type=='password'" href="" @click.prevent="passwordRevealed = !passwordRevealed">
      {{passwordRevealed ? 'Hide' : 'Reveal'}} password</a>
</div>
  
</template>

<script>
  export default {
    data () {
      return {
        passwordRevealed: false
      }
    },
    props: {
      name: {
        required: true,
        type: String
      },
      value: {
        required: false,
        type: String,
        default: ''
      },
      type: {
        required: false,
        type: String,
        default: 'text'
      }
    },
    computed: {
      inputType  () {
        return this.passwordRevealed ? 'text' : this.type
      }
    },
    methods: {
      toggleVisibility () {
        this.inputType = this.inputType === 'password' ? 'text' : 'password'
      }
    }
  }
</script>

<style scoped>

</style>