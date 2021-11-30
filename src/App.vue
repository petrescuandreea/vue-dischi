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
    <Albumlist :selectedGen="selectedGenre" @genreReady="getGenresList"/>
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
      selectedGenre:"",
    }
  },
  methods: {
    getGenresList(allGenres) {
      this.genresList = allGenres;
    },

    // tengo traccia della selezione fatta dall'utente 
    selectGenre(genreToSearch) {
        this.selectedGenre = genreToSearch;
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

  header {
    height: 80px;
    background-color: rgba(46,58,70,255);
    display: flex;
    justify-content: space-between;
    align-items: center;
  }

  main {
    min-height: calc(100vh - 80px);
    background-color: rgba(30,45,59,255);
  }
}
</style>
