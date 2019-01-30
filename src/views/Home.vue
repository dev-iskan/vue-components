<template>
  <div>
    <app-button @click.prevent="clicked" title="Sign up for an account">
      Create an account
    </app-button>
    <!-- <app-button :to="{name: 'signin'}" theme="danger" size="large" disabled></app-button> -->
  </div>
</template>

<script>
import AppButton from '@/components/AppButton'
export default {
  name: 'home',
  components: {
    AppButton
  },
  methods: {
    clicked() {
      console.log('clicked')
    }
  }
}
</script>
