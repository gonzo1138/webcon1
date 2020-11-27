<template>
    <div>{{msg}}</div>
</template>

<script>
    export default {
        name: "GlHeader",
        props: {
            msg: String
        }
    }
</script>

<style scoped>
  div {
      border: 1px solid indigo;
      width: inherit;
      margin: 1px;
  }
</style>