<template>
  <div id="app">
    <h1>WUSSUP</h1>
    <MyComponent/>
    <UserCard/>
  </div>
</template>

<script>
import MyComponent from "@/components/MyComponent";
import UserCard from "@/components/User.Card";

export default {
  name: 'App',

  components: {
    UserCard,
    MyComponent
  }
}
</script>

<style>
* {
  margin: 0;
  padding: 0;
  box-sizing: border-box;
  font-size: 16px;
}

#app {
}
</style>
