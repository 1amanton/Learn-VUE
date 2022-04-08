<template>
  <div id="app">
    <MySetter/>
    <SupsList/>
    <h1>WUSSUP</h1>
    <MyComponent/>
    <UserCard/>
    <SearchComponent/>
    <ChangeClasses/>

  </div>
</template>

<script>
import MySetter from "@/components/MySetter";
import SupsList from "@/components/SupsList";
import MyComponent from "@/components/MyComponent";
import UserCard from "@/components/UserCard";
import SearchComponent from "@/components/SearchComponent";
import ChangeClasses from "@/components/ChangeClasses"

export default {
  name: 'App',

  components: {
    MySetter,
    SupsList,
    ChangeClasses,
    SearchComponent,
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
