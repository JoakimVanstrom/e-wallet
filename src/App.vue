<template>
  <div id="app">
  <Home> </Home>
  <CreateCardPage> </CreateCardPage>
  </div>
</template>


<script>
import Home from './views/Home.vue'
import CreateCardPage from './views/CreateCardPage.vue'

export default {
  components:{Home, CreateCardPage}
}
</script>

<style lang="scss">
@import url('https://fonts.googleapis.com/css2?family=PT+Mono&family=Source+Sans+Pro&display=swap');

body{
  display: grid;
  place-items: center;
}

// font-family: 'PT Mono', monospace;
// font-family: 'Source Sans Pro', sans-serif;
</style>