<template>
  <div>
    <!-- <app-button @click.prevent="clicked" title="Sign up for an account">
      Create an account
    </app-button> -->
    <!-- <app-button :to="{name: 'signin'}" theme="danger" size="large" disabled></app-button> -->

    <!-- <app-label for="email">E-mail</app-label>
    <app-input name="email" type="email" v-model="form.email" placeholder="text@text.com" required></app-input> -->
    <app-textarea name="bio" v-model="form.bio" placeholder="Hello world"></app-textarea>
  </div>
</template>

<script>
// import AppButton from '@/components/AppButton'
// import AppInput from '@/components/AppInput'
// import AppLabel from '@/components/AppLabel'
import AppTextarea from '@/components/AppTextarea'
export default {
  name: 'home',
  components: {
    // AppButton,
    // AppInput,
    // AppLabel,
    AppTextarea
  },
  data () {
    return {
      form: {
        email: '',
        bio: ''
      }
    }
  },
  methods: {
    clicked() {
      console.log('clicked')
    }
  }
}
</script>
