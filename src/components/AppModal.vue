<template>
<transition name="modal">
  <div v-if="visible" >
    <div class="app-modal" @click.prevent="$modal.hide(name)"></div>

    <div class="app-modal-inner">
      <a href="#" @click.prevent="$modal.hide(name)">Close</a>
      <slot name="body" :params="params"/>
    </div>
  </div>
</transition>

 
</template>

<script>
  export default {
    props: {
      name: {
        required: true,
        type: String
      }
    },
    data () {
      return {
        visible: false,
        params: {}
      }
    },
    methods: {
      setVisible (value) {
        this.visible = value
      }
    },

    beforeMount () {
      this.$modal.$event.$on('show', (modal, params) => {
        if (this.name !== modal) {
          return
        }
          this.params = params

          if (!this.$listeners['before-open']) {
            this.setVisible(true)
            return
          }

          this.$emit('before-open', () => {
            this.setVisible(true)
          })
      })
      this.$modal.$event.$on('hide', (modal) => {
        if (this.name === modal) {
         this.setVisible(false)
        }
      })
    },

    mounted () {
      document.addEventListener('keydown', e => {
        if(this.visible && e.keyCode === 27) {
          this.setVisible(false)
        }
        
      })
    }
  }
</script>

<style scoped>
  .app-modal  {
    background-color: #141420;
    position: fixed;
    width: 100%;
    height: 100%;
    top: 0;
    left: 0;
    z-index: 9999;
  }

  .app-modal-inner {
    position: fixed;
    top: 50%;
    left: 50%;
    transform: translate(-50%, -50%);
    background-color: #fff;
    padding: 30px;
    width: 90%;
    max-width: 500px;
    z-index: 9999;
  }

  .modal-enter-active, .modal-leave-active {
    transition: all 250ms;
  }
  .modal-enter, .modal-leave-to {
    opacity: 0;
  }
</style>