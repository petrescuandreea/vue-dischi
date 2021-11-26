<template>
  <div id="app">
    <header>
      <!-- componente MyHeader  -->
      <MyHeader/>
    </header>
    <main>
      <!-- componente Albumlist  -->
    <Albumlist/>
    </main>
  </div>
</template>

<script>
import MyHeader from './components/MyHeader.vue';
import Albumlist from './components/Albumlist.vue'


export default {
  name: 'App',
  components: {
    MyHeader,
    Albumlist
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
