<template>
  <div>
    <gl-header msg="GlWindow.vue This is a Gl-header">{{msg}}</gl-header>
    <gl-content msg="GlWindow.vue this is window content">{{msg}}</gl-content>
  </div>
</template>

<script>
  import GlHeader from "@/components/GlHeader";
  import GlContent from "@/components/gl-content"
  export default {
    name: 'GlWindow',
    //components: {GlHeader: () => import("@/components/GlHeader")},
    //components: {'gl-header': GlHeader},
    components: {
      GlHeader,
      GlContent,
    },
    //child:{GlHeader},
    props: {
      msg: String
    }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
  div {
    border: 1px solid red;
    margin: 1px;
    width: fit-content;
  }
h3 {
  margin: 40px 0 0;
}
ul {
  list-style-type: none;
  padding: 0;
}
li {
  display: inline-block;
  margin: 0 10px;
}
a {
  color: #42b983;
}
</style>
