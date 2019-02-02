<template>
  <app-modal name="signin" @before-open="loadCourses">
    <template slot="body" slot-scope="{ params }">
      <!-- <p>Sign In</p>
      <a href="#" @click.prevent="signIn">Submit</a> -->

      {{courses}}
    </template>
  </app-modal>
</template>

<script>
  import axios from 'axios'
  import AppModal from '../AppModal';
  export default {
    data () {
      return {
        courses: []
      }
    },

    components: {
      AppModal
    },

    methods: {
      signIn () {
        this.$modal.hide('signin')
      },
      async loadCourses (done) {
        const response = await axios.get('https://api.codecourse.com/api/courses')
        this.courses = response.data
        done()
      }
    }
  }
</script>

<style scoped>

</style>