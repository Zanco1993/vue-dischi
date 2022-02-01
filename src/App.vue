<template>
  <div id="app">
    <header-app/>
    <!-- <search-app v-if="loadingAPI === true" @search="selectGenre"/> -->
    <search-app v-if="loadingAPI === true" />
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
import SearchApp from './components/SearchApp.vue'

export default {
  name: 'App',
  components: {
    HeaderApp,
    MainContainer,
    LoaderApp,
    SearchApp
  },

  data() {
    return {
      dischi: [],
      dischiGenre: [],
      loadingAPI: false
    }
  },

// dopo 1 secondo chiama la funzione ed esegue le istruzioni
// loader-app diventerà falso e quindi sparirà dal codice

  mounted() {
    axios.get('https://flynn.boolean.careers/exercises/api/array/music').then((element) => {
      this.dischi = element.data.response;
      // this.dischiGenre = element.data.response
      
      setTimeout(() => {
      // assegno il valore di 'success' presente nei dati e lo assegno a loadingAPI
      this.loadingAPI = element.data.success;
      }, 1000)
      })
  },

  // mothods: {
  //   selectGenre(select) {
  //     this.dischiGenre = this.dischi.filter((genere) => {
  //       return genere.response.genre.includes(select)
  //     })
  //   }
  // }
}
  

</script>

<style lang="scss">
@import '../style/main.scss';
</style>
