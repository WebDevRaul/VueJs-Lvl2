<template>
  <button type="button" @click="onUpdateAge">Update Age:</button>
  <p>This user is {{ age }} years old!</p>
</template>

<script>
  export default {
    name: "Age",
    props: ["age"],
    emits: ['onUpdateAge'],
    methods: {
      onUpdateAge() {
        this.$emit('onUpdateAge', 3)
      }
    }
  }
</script>

<style scoped>

</style>