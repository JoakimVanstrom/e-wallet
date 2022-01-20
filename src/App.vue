<template>
  <div id="app">
  <Home v-if="currentView === 'home'"> </Home>
  <CreateCardPage v-else-if="currentView === 'createCardPage'"> </CreateCardPage>
  <button @click="currentView = 'createCardPage'">Create Card</button>
  </div>
</template>


<script>
import Home from './views/Home.vue'
import CreateCardPage from './views/CreateCardPage.vue'

export default {
  components:{Home, CreateCardPage},
  name: 'App',
  data(){return{
    currentView: 'home',
  }}
}
</script>

<style lang="scss">
@import url('https://fonts.googleapis.com/css2?family=PT+Mono&family=Source+Sans+Pro&display=swap');

body{
  display: grid;
  place-items: center
}

// button {
//     margin-top: 4rem;
//     height: 72px;
//     font-size: 1.5rem;
//     font-weight: bolder;
//     color: white;
//     background-color: black;
//     border-radius: 10px;
// }

// font-family: 'PT Mono', monospace;
// font-family: 'Source Sans Pro', sans-serif;
</style>