<template>
  <div>
    <router-link 
      class="btn" 
      :to="to"
      :class="[
        themes[theme],
        sizes[size]
      ]"
    >
      Sign In
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
    }
  }
</script>

<style scoped>

</style>