<template>
    <div>
        <label for="genre-select"> Seleziona genere:
        <!-- associo l'evento change  -->
            <select @change="$emit('filter', $event)">
                <option value="all">All</option>
                <option value="rock">Rock</option>
                <option value="pop">Pop</option>
                <option value="jazz">Jazz</option>
                <option value="metal">Metal</option>
            </select>
        </label>
    </div>
</template>

<script>
export default {
  name: 'FilterAlbum',
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped lang="scss">
    div {
        text-align: center;

        label {
            font-size: 20px;
            color: white;
        }
    }
    
</style>