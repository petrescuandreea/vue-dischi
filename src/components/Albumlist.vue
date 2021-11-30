<template>
  <section>
    <!-- catturo l'evento filter e gli passo la funzione selectGenre  -->
    <!-- <FilterAlbum @filter="selectGenre"/>  -->
    <Loader  v-if="albumArray.length === 0"/>

    <div v-else id="album-wrapper">
        <Album 
        v-for="album, i in filteredAlbumArray" 
        :key="i" 
        :details="album"/>
    </div>
  </section>
</template>

<script>
import axios from 'axios';
import Album from '@/components/Album.vue';
import Loader from '@/components/Loader.vue';
// import FilterAlbum from '@/components/FilterAlbum.vue';

export default {
  name: 'Albumlist',
  components: {
      Album,
      Loader,
      // FilterAlbum
  },

  props: {
    // dichiaro la prop per poter ricevere le info inviate dal componente padre 
    selectedGen: String,
  },

  data() {
      return {
        //   variabile che mi salva l'endpoint dell'API 
          apiUrl: "https://flynn.boolean.careers/exercises/api/array/music",
          albumArray: [],

          // array generi 
          genres: [],
      }
  },

//   lancia il prima possibile la chiama Ajax 
  created() {
      this.getAlbumList();
  },

  computed: {
    // creo una copia dell'array utilizzata per filtrare i dischi in base al genere 
    filteredAlbumArray() { 
      // se l'utente seleziona la voce 'all' compare l'array di partenza
      if (this.selectedGen === 'all') {
        return this.albumArray;
      }

      // altrimenti compare l'array filtrato in base a quello che l'utente ha selezionato
      return this.albumArray.filter((item) => {
        return item.genre.toLowerCase().includes(this.selectedGen.toLowerCase());
      })
      
    }
  },

  methods: {
      getAlbumList() {
        //   chiamata axios 
          axios
        //   richiamo l'endpoint 
          .get(this.apiUrl)
          .then((result) => {
              this.albumArray = result.data.response;

              this.albumArray.forEach(album => {
                if(!this.genres.includes(album.genre)) {
                  this.genres.push(album.genre);
                  console.log(this.genres);
                }
              })
          });

          // lancio l'evento genreReady e gli passo il parametro genres per inviare i dati
          this.$emit("genreReady", this.genres);
      },

      // tengo traccia della selezione fatta dall'utente 
      // selectGenre(event) {
      //     this.selectedGenre = event.target.value;
      //     console.log(this.selectedGenre);
      // },
  }
  
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped lang="scss">
    section {
        background-color: rgba(30,45,59,255);
        padding: 30px 0;

        #album-wrapper {
            width: 70%;
            margin: 0 auto;
            padding: 20px 0;
            display: flex;
            flex-wrap: wrap;
            justify-content: space-between;
        }
    }
</style>
