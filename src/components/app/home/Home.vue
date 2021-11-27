<template>
  <h1>
    Home component
  </h1>
</template>

<script>
  export default {
    name: "Home",
    activated() {
      console.log('activated')
    },
    deactivated() {
      console.log('deactivated')
    }
  }
</script>

<style scoped>

</style>