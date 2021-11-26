<template>
  <section>
      <div id="album-wrapper">
         <Album 
         v-for="album, i in albumArray" 
         :key="i" 
         :details="album"/>
      </div>

  </section>
</template>

<script>
import axios from 'axios';
import Album from '@/components/Album.vue'

export default {
  name: 'Albumlist',
  components: {
      Album
  },
  data() {
      return {
        //   variabile che mi salva l'endpoint dell'API 
          apiUrl: "https://flynn.boolean.careers/exercises/api/array/music",
          albumArray: [],
      }
  },
  created() {
      this.getAlbumList();
  },
  methods: {
      getAlbumList() {
          axios
          .get(this.apiUrl)
          .then((result) => {
              this.albumArray = result.data.response;
          })
      }
  }
  
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped lang="scss">
    section {
        background-color: rgba(30,45,59,255);

        #album-wrapper {
            width: 75%;
            margin: 15px auto;
            display: flex;
            flex-wrap: wrap;
            justify-content: space-between;
        }
    }
</style>
