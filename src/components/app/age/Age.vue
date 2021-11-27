<template>
  <button type="button" @click="onUpdateAge">Update Age:</button>
  <button type="button" @click="updateAgeFn(3)">Update Age CB:</button>
  <p>This user is {{ age }} years old!</p>
</template>

<script>
  export default {
    name: "Age",
    props: {
      age: { 
        type: Number, 
        required: true,
        // default: 20
        // validator(value)
        //   return value < 130
        // }
      },
      updateAgeFn: Function
    },
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