<template>
  <div class="search">
    <hr>
    <label for="search"> Search
      <input
          @input="searchLine = $event.target.value"
          type="text" name="" id="search">
    </label>
    <span>Search line : {{ searchLine }}</span>

    <span>Всего имён : {{ nameList.length }}</span>
    <span>Совпадений : {{ filteredList.length }}</span>

    <span
        v-for="(name, index) in filteredList"
        :key="index"
    >
      {{ name }}
    </span>
    <hr>
  </div>
</template>

<script>
export default {
  name: "SearchComponent",

  data() {
    return {
      searchLine: "",
      nameList: ["Steve", "Ivan", "Jack", "Molly", "Ihor"],
    }
  },

  methods: {
  },

  computed: {
    filteredList() {
      let regExp = new RegExp(this.searchLine, "i")
      return this.nameList.filter(el => regExp.test(el))
    }
  }
}
</script>

<style scoped>
.search {
  display: flex;
  flex-direction: column;
  padding: 0 2rem;
}

</style>