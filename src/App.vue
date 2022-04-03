<template>
  <div id="app">
    <h1>WUSSUP</h1>
    <MyComponent/>
  </div>
</template>

<script>
import MyComponent from "@/components/MyComponent";

export default {
  name: 'App',

  components: {
    MyComponent
  }
}
</script>

<style>
#app {
  margin: 0;
  padding: 0;
  box-sizing: border-box;
  font-size: 16px;
}
</style>
