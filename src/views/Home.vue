<template>
  <div>
    <app-button :to="{name: 'signin'}" size="large"></app-button>
    <app-button :to="{name: 'signin'}" theme="danger"></app-button>
  </div>
</template>

<script>
import AppButton from '@/components/AppButton'
export default {
  name: 'home',
  components: {
    AppButton
  }
}
</script>
