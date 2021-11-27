<template>
  <ul>
    <li>This is not a slot</li>
    <slot name="1"></slot>
    <li>This is not a slot</li>
    <slot name="2"></slot>
    <li>This is not a slot</li>
    <slot name="3"></slot>
  </ul>
</template>

<script>
  export default {
    name: "Slot"
  }
</script>

<style scoped>

</style>