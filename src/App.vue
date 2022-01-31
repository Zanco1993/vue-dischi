<template>
  <div id="app">
    <header-app/>
    <main-container :dischi="dischi" />
  </div>
</template>

<script>
import axios from 'axios'
import HeaderApp from './components/HeaderApp.vue'
import MainContainer from './components/MainContainer.vue'

export default {
  name: 'App',
  components: {
    HeaderApp,
    MainContainer
  },

  data() {
    return {
      dischi: []
       
    }
  },

  mounted() {
    axios.get('https://flynn.boolean.careers/exercises/api/array/music').then((element) => {
      console.log(element.data)
      this.dischi = element.data.response
    })
  }
}
</script>

<style lang="scss">
@import '../style/main.scss';
</style>
