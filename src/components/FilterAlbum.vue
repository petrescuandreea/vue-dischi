<template>
    <!-- associo l'evento change  -->
    <label> Seleziona genere
        <select @change="$emit('filter', $event)">
            <option value="all">All</option>
            <option value="rock">Rock</option>
            <option value="pop">Pop</option>
            <option value="jazz">Jazz</option>
            <option value="metal">Metal</option>
        </select>
    </label>
</template>

<script>
export default {
  name: 'FilterAlbum',
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped lang="scss">

    
</style>