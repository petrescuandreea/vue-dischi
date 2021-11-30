<template>
    <div id="header">
        <i class="fab fa-spotify"></i>

        <div id="select">
            <label for="genre-select"> Seleziona genere:
            <!-- lancio l'evento filter e gli passo il parametro genreFilter per inviare i dati
            associo all'evento change l'evento lanciato -->
                <select @change="$emit('filter', genreFilter)" v-model="genreFilter">
                    <option value="" selected disabled>-- --</option>
                    <option value="tutti">Tutti</option>
                    <option value="rock">Rock</option>
                    <option value="pop">Pop</option>
                    <option value="jazz">Jazz</option>
                    <option value="metal">Metal</option>
                </select>
            </label>
        </div>
    </div>
</template>

<script>
export default {
  name: 'FilterAlbum',
  props: {
      genres: Array,
  },
  data() {
      return {
          genreFilter: "",
      }
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped lang="scss">
     #header {
         width: 100vw;
         display: flex;
         justify-content: space-between;
         align-items: center;
         padding: 10px 20px;

         i {
             color: rgba(30,215,96,255);
             font-size: 50px;
         }

         #select {
             label {
                 color: white;
             }
         }
         
  }
    
</style>