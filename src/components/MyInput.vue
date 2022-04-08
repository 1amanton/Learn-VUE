<template>
  <input type="text" @input="$emit('input', $event.target.value)">
</template>

<script>
export default {
  name: "MyInput",

  model: {
    prop: "value",
    event: "input"
  }
}
</script>

<style scoped>

</style>