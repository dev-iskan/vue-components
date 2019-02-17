<template>
<div>
 <ul class="app-tabs">
    <li v-for="(tab, index) in tabs" :key="index">
      <a 
        href="#" 
        class="app-tab" 
        @click.prevent="switchTab(tab.hash)"
        :class="{'active': tab.active}"
        >
        {{tab.name}}
      </a>
    </li>
  </ul> 
  <slot />
</div>
</template>

<script>
  export default {
    data () {
      return {
        tabs: []
      }
    },
    created () {
      // this.$children shows components which are children of current component
     this.tabs = this.$children
    },
    mounted () {
      this.switchTab(this.tabs[0].hash, false)
      if(this.$route.hash) {
        this.switchTab(this.$route.hash, false)
      }
    },
    methods: {
      switchTab(hash, switchHash = true) {
        // to select to show content of exact tab
        const clickedTab = this.findTab(hash)

        //in case there is no such tab
        if (typeof clickedTab === 'undefined') {
          return
        }
        //switch active property of component AppTab we loop through all and set false to other than clicked tabs
        this.tabs.forEach(tab => {
          tab.active = (tab.hash === clickedTab.hash)
        })

        if (switchHash) {
          //add hash to url, we use replace as we don't need to save to history clicked tab
          this.$router.replace({
            hash: clickedTab.hash         
          })
        }
        
      },
      findTab (hash) {
        // find either by plain id or with # itself
        return this.tabs.find(tab=>tab.hash === hash || `#${tab.hash}` === hash)
      }
    }
  }
</script>

<style scoped>
  .app-tabs {
    display: flex;
    align-items: flex-end;
    border-bottom: 1px solid #eee;
    list-style-type: none;
    padding: 0;
    margin: 0;
  }

  .app-tab {
    display: block;
    padding: 20px;
    font-weight: bold;
    border-bottom: 3px solid transparent;
    transform: translateY(3px)
  }

  .app-tab:hover, .app-tab.active {
    border-bottom-color: #03a6ff;
    text-decoration: none;
  }
</style>