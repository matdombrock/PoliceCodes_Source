<template>
  <div id="app">
    <!-- <img alt="Vue logo" class="logo" src="./assets/logo.png"> -->
    <Main/>
  </div>
</template>

<script>
import Main from './components/Main.vue'

export default {
  name: 'App',
  components: {
    Main
  }
}
</script>

<style>
:root{
  --background: black;  
  --color:white;

  --accent1: rgba(82, 82, 82, 0.75);
  --accent2:rgb(58, 58, 58, 0.75);
}
body{
  margin:0 auto;
  padding:0;
}
html{
  background: var(--background);
  background-image:url('assets/police-lights.jpg');
  background-size: cover;
  background-position:center;
  background-attachment: fixed;
  color:white;
}
.logo{
  height:15vh;
  max-height:125px;
  width:auto;
  filter:invert(1);
}
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  max-height:100vh;
  max-width:100vh;
  overflow:hidden;
  margin:0 auto;
}
@media only screen and (max-width: 800px) {
  body{
    margin:0 auto;
  }
}
</style>
