<template>
  <div id="app">
    <header-app />
    <search-app
      v-if="loadingAPI === true"
      @searchGenre="selectGenre"
      @searchArtist="selectArtist"
      @reset="reset"
      :listGenre="listGenre()"
      :listAuthor="listAuthor()"
    />
    <!-- eseguo l'applicazione solo quando loadingAPI sarà true -->
    <main-container v-if="loadingAPI" :dischi="dischiFilter" />
    <loader-app v-else />
  </div>
</template>

<script>
import axios from "axios";
import HeaderApp from "./components/HeaderApp.vue";
import MainContainer from "./components/MainContainer.vue";
import LoaderApp from "./components/LoaderApp.vue";
import SearchApp from "./components/SearchApp.vue";

export default {
  name: "App",
  components: {
    HeaderApp,
    MainContainer,
    LoaderApp,
    SearchApp,
  },

  data() {
    return {
      dischi: [],
      dischiFilter: [],
      loadingAPI: false,
    };
  },

  // dopo 1 secondo chiama la funzione ed esegue le istruzioni
  // loader-app diventerà falso e quindi sparirà dal codice

  mounted() {
    axios
      .get("https://flynn.boolean.careers/exercises/api/array/music")
      .then((element) => {
        this.dischi = element.data.response;
        this.dischiFilter = element.data.response;

        setTimeout(() => {
          // assegno il valore di 'success' presente nei dati e lo assegno a loadingAPI
          this.loadingAPI = element.data.success;
        }, 1000);
      });
  },

  methods: {
    listGenre() {
      let genre = [];
      this.dischi.forEach((element) => {
        if (!genre.includes(element.genre.toLowerCase())) {
          genre.push(element.genre.toLowerCase());
        }
      });
      return genre;
    },
    listAuthor() {
      let author = [];
      this.dischi.forEach((element) => {
        if (!author.includes(element.author.toLowerCase())) {
          author.push(element.author.toLowerCase());
        }
      });
      return author;
    },

    selectGenre(input) {
      // console.log("prova");
      // popolo l'array di dischiFilter con il genere musicale
      this.dischiFilter = this.dischi.filter((genere) => {
        return genere.genre.toLowerCase().includes(input.toLowerCase());
      });
      // se clicco All, l'array torno come quello originale
      if (input === "All") {
        this.dischiFilter = this.dischi;
      }
    },
    selectArtist(input) {
      // console.log("prova");
      // popolo l'array di dischiFilter con l'autore
      this.dischiFilter = this.dischi.filter((artista) => {
        return artista.author.toLowerCase().includes(input.toLowerCase());
      });
      if (input === "All") {
        this.dischiFilter = this.dischi;
      }
    },

    reset() {
      this.dischiFilter = this.dischi;
    },
  },
};
</script>

<style lang="scss">
@import "../style/main.scss";
</style>
