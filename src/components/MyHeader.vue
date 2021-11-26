<template>
   <div id="header">
     <i class="fab fa-spotify"></i>
   </div>
</template>

<script>
export default {
  name: 'MyHeader',
  
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped lang="scss">
  #header {
    background-color: rgba(46,58,70,255);
    padding: 10px 20px;
    
    i {
      color: rgba(30,215,96,255);
      font-size: 50px;
    }
  }
    
</style>