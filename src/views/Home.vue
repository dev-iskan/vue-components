<template>
  <div>
    <!-- <app-button @click.prevent="clicked" title="Sign up for an account">
      Create an account
    </app-button> -->
    <!-- <app-button :to="{name: 'signin'}" theme="danger" size="large" disabled></app-button> -->

    <!-- <app-label for="email">E-mail</app-label>
    <app-input name="email" type="email" v-model="form.email" placeholder="text@text.com" required></app-input> -->
    <!-- <app-textarea name="bio" v-model="form.bio" placeholder="Hello world"></app-textarea> -->


    <!-- Modals -->
    <!-- <app-sign-in-modal name="Alex"></app-sign-in-modal>

    <a href="#" @click.prevent="openModal">Open modal</a> -->

    <!-- Tabs -->
    <app-tabs>
      <app-tab
        name="Tab one"
      >Tab content 1
      </app-tab>
      <app-tab
        name="Tab two"
      >Tab content 2
      </app-tab>
    </app-tabs>
  </div>
</template>

<script>
// import AppButton from '@/components/AppButton'
// import AppInput from '@/components/AppInput'
// import AppLabel from '@/components/AppLabel'
// import AppSignInModal from '@/components/modals/AppSignInModal'
import AppTabs from '@/components/tabs/AppTabs'
import AppTab from '@/components/tabs/AppTab'
export default {
  name: 'home',
  components: {
    // AppButton,
    // AppInput,
    // AppLabel,
    // AppTextarea,
    // AppSignInModal,
    AppTabs,
    AppTab
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
    },
    openModal () {
      this.$modal.show('signin', {name: 'Alex'})

      // setTimeout(() => {
      //   this.$modal.hide('signin')
      // }, 2000)
    }
  }
}
</script>
