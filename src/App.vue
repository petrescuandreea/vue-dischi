<template>
  <div id="app">
    <header>
      <!-- componente MyHeader  -->
      <!-- catturo l'evento lanciato dal figlio FilterAlbum  => emit -->
      <FilterAlbum :genres="genresList"  @filter="selectGenre"/>
    </header>
    <main>
      <!-- componente Albumlist  -->
      <!-- invio il dato ricevuto dal figlio FilterAlbum al fratello Albumlist => props -->
    <Albumlist :selectedGenre="genreToSearch" @genreReady="getGenresList"/>
    </main>
  </div>
</template>

<script>
// import MyHeader from './components/MyHeader.vue';
import FilterAlbum from '@/components/FilterAlbum.vue';
import Albumlist from './components/Albumlist.vue';


export default {
  name: 'App',
  components: {
    FilterAlbum,
    // MyHeader,
    Albumlist
  },
  data() {
    return {
      genresList: [],

      // proprietà che mi salva il dato ricevuto dal componente figlio 
      genreToSearch:"",
    }
  },
  methods: {
    getGenresList(allGenres) {
      this.genresList = allGenres;
    },

    // tengo traccia della selezione fatta dall'utente 
    selectGenre(genreToSearch) {
        this.selectedGenre = genreToSearch.target.value;
        console.log(this.selectedGenre);
    },
  }
}
</script>

<style lang="scss">
* {
  margin: 0;
  padding: 0;
  box-sizing: border-box;
}
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
}
</style>
