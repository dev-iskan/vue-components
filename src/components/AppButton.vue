<template>
  <div>
    <router-link 
      class="btn"
      @click.native="clicked"
      :disabled="disabled"
      :to="to"
      :class="[
        themes[theme],
        sizes[size],
        {
          'disabled' : disabled
        }
      ]"
    >
      <slot/>
    </router-link>
  </div>
</template>

<script>
  export default {
    data () {
        return {
          themes: {
            primary: 'btn-primary',
            danger: 'btn-danger'
          },
          sizes: {
            normal: '',
            large: 'btn-lg'
          }
        }
      },
    props: {
      disabled:{
        required: false,
        type: Boolean,
        default: false
      },
      theme: {
        required: false,
        type: String,
        default: 'primary'
      },
      size: {
        required: false,
        type: String,
        default: 'normal'
      },
      to: {
        required: false,
        default () {
          return {
            name: 'home'
          }
        }
      }
    },
    methods: {
      clicked (e) {
        // if (this.disabled) {
        //   return
        // }
        this.$emit('click', e)
      }
    }
  }
</script>

<style scoped>

</style>

// In case you want to output text on button we 
// use <slot/> which allows to make component with openning and closing tags
// no need to pass default html props such as "title" for example