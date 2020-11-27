<template>
  <div id="app">
    <gl-window></gl-window>
  </div>
</template>

<script>
//import HelloWorld from './components/HelloWorld.vue'
//import GlWindow from '@/components/GlWindow'
//import GlHeader from "@/components/GlHeader";
//import GlHeader from "@/components/GlHeader";
//import GlHeader from "@/components/GlHeader";
//import GlHeader from "@/components/GlHeader"

//const app = createApp({
//  root instance definition
//});

//import GlShell from 'vue-shell'
import GlWindow from "@/components/GlWindow";
export default {
  name: 'App',

  components: {
    GlWindow,
    //GlShell,
    //GlWindow,
  },
  //child: GlHeader
}
</script>

<style>
  body {
    background-color: black;
    margin: 1px;
  }
</style>

<style scoped>
#app {
  border: 2px solid grey;
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  background-color: bisque;
  margin: 1px;
  width: fit-content;
}

</style>
