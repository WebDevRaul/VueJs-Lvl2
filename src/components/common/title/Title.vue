<template>
  <h1>{{ title }}</h1>
</template>

<script>
  export default {
    name: 'Title',
    props: ["title"]
  }
</script>

<style scoped lang="scss">
  $red: red;
  h1 {
    color: $red;
  }
</style>