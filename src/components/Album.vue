<template>
    <div class="album">
        <img :src="details.poster" :alt="details.author">
        <h1>{{ details.title }}</h1>
        <span>{{ details.author }}</span>
        <span>{{ details.year }}</span>
    </div>
</template>

<script>
export default {
  name: 'Album',
  props: {
      details: Object
  }
  
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped lang="scss">
    .album {
        text-align: center;
        width: calc(100% / 5 - 20px);
        min-height: 300px;
        padding: 10px;
        background-color: rgba(46,58,70,255);
        margin: 0 20px 20px 0 ;
        // margin-right: 20px;
        // margin-bottom: 20px ;


        h1 {
            color: white;
            font-size: 25px;
            text-transform: uppercase;
            margin: 15px 0;
        }

        img {
            max-width: 100%;
        }

        span {
            display: block;
            color: rgba(127,126,118,255);
        }
    }
    
</style>