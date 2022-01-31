<template>
  <div id="app">
    <header-app/>
    <!-- eseguo l'applicazione solo quando loadingAPI sarà true -->
    <main-container v-if="loadingAPI" :dischi="dischi" />
    <loader-app v-else/>
  </div>
</template>

<script>
import axios from 'axios'
import HeaderApp from './components/HeaderApp.vue'
import MainContainer from './components/MainContainer.vue'
import LoaderApp from './components/LoaderApp.vue'

export default {
  name: 'App',
  components: {
    HeaderApp,
    MainContainer,
    LoaderApp
  },

  data() {
    return {
      dischi: [],
       
      loadingAPI: false
    }
  },

// dopo 1 secondo chiama la funzione ed esegue le istruzioni
// loader-app diventerà falso e quindi sparirà dal codice

  mounted() {
    axios.get('https://flynn.boolean.careers/exercises/api/array/music').then((element) => {
      this.dischi = element.data.response;
      setTimeout(() => {
      // assegno il valore di 'success' presente nei dati e lo assegno a loadingAPI
      this.loadingAPI = element.data.success;
      }, 2000)
      })
  }
}
  

</script>

<style lang="scss">
@import '../style/main.scss';
</style>
